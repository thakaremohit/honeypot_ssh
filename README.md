# 🛡️ Modular Honeypot for SSH & HTTP

This project is a modular, graphic-based honeypot designed to capture **IP addresses, usernames, passwords, and commands** from unauthorized login attempts on **SSH and HTTP services**. The honeypot is written in **Python** and allows easy deployment to **trap and analyze attackers** targeting vulnerable systems.

## 📌 Features

✅ **SSH Honeypot**  
- Emulates an SSH server using **Paramiko**.  
- Captures and logs **login credentials** (usernames & passwords).  
- Records **executed commands** from attackers.  
- Mimics a real Linux shell environment with limited responses.  

✅ **HTTP (WordPress) Honeypot**  
- Simulates a **WordPress login page** for capturing credentials.  
- Logs **IP addresses, usernames, and passwords** of intruders.  
- Redirects successful login attempts to an external URL.  

✅ **Logging & Monitoring**  
- All activity is logged in separate **audit files** for analysis.  
- Uses **Rotating Log Files** to manage storage efficiently.  
- Runs in a **modular** way, allowing either SSH or HTTP honeypot mode.  

## 🛠️ Installation & Setup

### Prerequisites
Make sure you have Python installed (>=3.8) and install dependencies:

```bash
pip install flask paramiko
```

### Running the Honeypot

**1️⃣ SSH Honeypot Mode**  
Start an SSH honeypot on port **2223** with a custom username & password:

```bash
python honeypy.py -a 0.0.0.0 -p 2223 -s -u admin -w password123
```

**2️⃣ HTTP Honeypot Mode**  
Run the WordPress-style HTTP honeypot on port **8080**:

```bash
python honeypy.py -a 0.0.0.0 -p 8080 -wh -u admin -w secretpass
```

If no username/password is provided, it defaults to `admin:deeboodah`.

## 📜 Logs & Analysis

Captured credentials and commands are stored in log files:
- **SSH Credentials & Commands** → `audits.log`, `cmd_audits.log`  
- **HTTP Login Attempts** → `http_audits.log`  

You can analyze these logs to study **attacker behavior and trends**.

## ⚠️ Disclaimer

**This project is for educational and research purposes only.** Deploying a honeypot without proper authorization in a production network may lead to legal consequences. Use responsibly.
