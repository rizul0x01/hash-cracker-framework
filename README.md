# Advanced Hash Cracker Framework

This is an advanced hash cracking framework designed to identify hash types and crack them using various methods, including dictionary attacks.

## Installation

To set up the project, follow these steps:

1.  **Extract the archive:**
    ```bash
    tar -xzf hash-cracker-framework.tar.gz
    ```

2.  **Navigate to the extracted directory:**
    ```bash
    cd hash-cracker-framework
    ```

2.  **Install dependencies:**
    It is highly recommended to use a Python virtual environment to avoid conflicts with your system's Python packages.

    ```bash
    # Create a virtual environment
    python3 -m venv hash_myvenv

    # Activate the virtual environment
    source hash_myvenv/bin/activate

    # Install required packages
    pip install -r hash_cracker/requirements.txt

    # Install the project in editable mode
    pip install -e hash_cracker
    ```

    If you encounter issues with `crypt` module, ensure you have `python3-dev` and `libcrypt-dev` installed on your system (for Debian/Ubuntu-based systems):
    ```bash
    sudo apt update
    sudo apt install python3-dev libcrypt-dev
    ```

## Usage

There are two primary ways to use the hash cracker:

### 1. Interactive Mode (Recommended for quick use)

Navigate into the `hash_cracker` subdirectory and run `main.py` directly. The program will prompt you for the necessary inputs.

```bash
python3 -m hash_cracker.main
```

Follow the prompts:

*   **Enter hash value:** Paste the hash you want to crack.
*   **Enter wordlist path (Optional):** Provide the path to your wordlist file (e.g., `wordlist.txt`). If left blank, it will attempt to use a default wordlist.

### 2. Command-Line Arguments Mode

You can also provide arguments directly when running the `main.py` script from the `hash_cracker_latest` directory (after installing in editable mode).

```bash
python3 -m hash_cracker.main --hash <YOUR_HASH> --wordlist <PATH_TO_WORDLIST>
```

**Example:**

```bash
python3 -m hash_cracker.main --hash 5f4dcc3b5aa765d61d8327deb882cf99 --wordlist hash_cracker/wordlist.txt
```

**Available Arguments:**

*   `--hash <HASH_VALUE>`: Specify a single hash value to crack.
*   `--hash-file <PATH_TO_FILE>`: Specify a file containing hash values (one hash per line).
*   `--wordlist <PATH_TO_WORDLIST>`: Specify the path to a wordlist file for dictionary attacks.
*   `--bruteforce`: Enable bruteforce attack mode.
*   `--charset <CHARSET>`: Specify the character set for bruteforce (e.g., `?l?d` for lowercase letters and digits).
*   `--min-len <LENGTH>`: Minimum length for bruteforce passwords.
*   `--max-len <LENGTH>`: Maximum length for bruteforce passwords.
*   `--output <PATH_TO_FILE>`: Save cracked hashes to a specified file.
*   `--format <FORMAT>`: Specify the hash format if known (e.g., `MD5`, `SHA1`).
*   `--resume`: Resume a previous cracking session.
*   `--threads <NUMBER>`: Number of threads to use for cracking (default: 4).
*   `--verbose`: Enable verbose output.
*   `--quiet`: Suppress most output.

## Troubleshooting

*   **`ModuleNotFoundError: No module named 'hash_cracker'`**: Ensure you have installed the project in editable mode (`pip install -e hash_cracker`) from the `hash_cracker_latest` directory, and that your virtual environment is activated.
*   **`ModuleNotFoundError: No module named 'crypt'`**: On Debian/Ubuntu, install `python3-dev` and `libcrypt-dev` using `sudo apt install python3-dev libcrypt-dev`.
*   **`ModuleNotFoundError: No module named 'passlib'`**: Ensure `passlib` is included in your `requirements.txt` and installed via `pip install -r hash_cracker/requirements.txt`.
*   **`Wordlist exhausted, password not found.`**: This means the password was not found in the provided wordlist. Try a larger or different wordlist, or consider a bruteforce attack if applicable.

If you encounter any other issues, please refer to the project's `setup.py` and `requirements.txt` files for dependency information.
