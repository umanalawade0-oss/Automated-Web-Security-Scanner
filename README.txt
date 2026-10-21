# Automated Web Security Header Scanner

A beginner-friendly defensive cybersecurity project that checks a website's HTTP response for common security headers and reports which ones are present or missing.

## Features
- Accepts a domain or full HTTP/HTTPS URL.
- Follows redirects and reports the final URL and HTTP status.
- Checks six headers: HSTS, Content-Security-Policy, X-Content-Type-Options, X-Frame-Options, Referrer-Policy, and Permissions-Policy.
- Prints a readable summary and can save JSON output.
- Uses a timeout and handles common request errors.

## Ethical use
Run this tool only against websites you own or have explicit permission to assess. It performs a simple HTTP GET request; it is not a penetration-testing tool. Missing headers do not automatically mean a site is vulnerable.

## Requirements
- Python 3.9 or later
- Internet connection
- Packages in `requirements.txt`

## Installation
```bash
python -m venv .venv
```
Activate the environment:
- Windows: `.venv\\Scripts\\activate`
- macOS/Linux: `source .venv/bin/activate`

Then install dependencies:
```bash
python -m pip install -r requirements.txt
```

## Run
```bash
python scanner.py https://example.com
```
Save results to JSON:
```bash
python scanner.py https://example.com --json scan_report.json
```
If you do not specify a scheme, the scanner tries HTTPS first:
```bash
python scanner.py example.com
```

## Example output
```text
Automated Web Security Header Scan
URL: https://example.com/
HTTP status: 200
HTTPS: Yes

[REVIEW] strict-transport-security
...
```
Actual output depends on the target website and may differ.

## Project structure
```text
automated_web_scanner/
├── scanner.py
├── requirements.txt
├── README.md
└── .gitignore
```

## Limitations
- Checks response headers only; it does not crawl pages or test for exploitable vulnerabilities.
- Does not verify whether each header's policy is strong or correctly configured.
- Results may differ by path, redirect, CDN, or server configuration.
- Always validate findings manually and obtain authorization.

## Future improvements
- Export HTML/PDF reports.
- Add a user interface.
- Add tests and configurable header checks.
- Compare values against a locally maintained policy checklist.