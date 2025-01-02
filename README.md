# Network-Scanning-with-Nmap

Objective
---
To explore and demonstrate the use of Nmap for network scanning, identifying open ports, services, and vulnerabilities, and analyzing TCP header responses to understand network configurations and security.

Project Overview
---
Network scanning is a fundamental step in penetration testing and vulnerability assessment. Nmap, a powerful network scanner, uses TCP/IP packet analysis to determine port states and identify services running on target systems. This project highlights various Nmap scanning techniques and explains how Nmap interprets port states, such as Open, Closed, Filtered, Unfiltered, Open|Filtered, and Closed|Filtered.

Steps to Perform
---
**1. Understanding the TCP Header**
   
The TCP header contains critical fields that Nmap leverages to assess port states:

**- Source Port and Destination Port:** Identify communication endpoints.

**- Sequence Number and Acknowledgment Number:** Manage reliable data delivery.

**- Flags (e.g., SYN, ACK, FIN, RST):** Define connection behavior and port states.

**- Checksum:** Ensures data integrity.

**Key Flags in Scanning:**

**- SYN**: Initiates a connection.

**- ACK**: Acknowledges receipt of data.

**- RST**: Resets a connection.

**- FIN**: Gracefully closes a connection.

**2. Setting Up the Environment**

- Installed Nmap on a Linux system (e.g., Kali Linux or Ubuntu).

- Used a controlled lab environment with virtual machines as targets.

**3. Performing Scans**

**Nmap Commands:**
**Basic Scan:**

``` nmap <target_IP> ```

**SYN Scan (Stealth Scan):**

``` nmap -sS <target_IP> ```

**TCP Connect Scan:**

``` nmap -sT <target_IP> ```

**UDP Scan:**
``` nmap -sU <target_IP> ```

**ACK Scan:**
```nmap -sA <target_IP> ```

**Service Version Detection:**
```nmap -sV <target_IP> ```

**Exporting Results:**
``` nmap -oN nmap_scan_report.txt <target_IP> 
nmap -oX nmap_scan_report.xml <target_IP>
```

**4.Interpreting Port States**
   
Nmap categorizes ports into six states based on responses:

**- Open:** A service is actively listening.

**- Closed:** No service is listening, but the port is reachable.

**- Filtered:**Nmap cannot determine the state; packets are blocked by a firewall.

**- Unfiltered:** Nmap cannot determine the state, but the port is reachable.

**- Open|Filtered:** The port is either open or filtered; Nmap cannot decide.

**- Closed|Filtered:** The port is either closed or filtered; Nmap cannot decide.

**5. Analyzing Results**
   
**Example Scan Output:**

| PORT    | STATE   | SERVICE   |
|---------|---------|-----------|
| 22/tcp  |  open   |  ssh      |
| 80/tcp  |filtered |  http     |
| 443/tcp | closed  | https     |

**Explanation:**

- Port 22 (SSH): Service is actively accepting connections.

- Port 80 (HTTP): Filtered by a firewall.

- Port 443 (HTTPS): No service is running, but the port is reachable.

**6.Generating Reports**
   
Saved results in human-readable and XML formats:

Normal format:

``` nmap -oN nmap_scan_report.txt <target_IP> ```

XML format:

``` nmap -oX nmap_scan_report.xml <target_IP> ```

Commands Used
---

|Command | Description |
|---------|---------------|
|nmap <target_IP> | Basic scan to detect open ports.|
| nmap -sS <target_IP> | SYN Scan to detect open ports.|
| nmap -sT <target_IP> | Full TCP Connect scan.|
| nmap -sU <target_IP> | UDP Scan to identify open UDP ports.|
| nmap -sA <target_IP> | ACK Scan to determine firewall rules.|
| nmap -sV <target_IP> | Detect service versions.|
| nmap -oN report.txt | Save results in normal text format.|
| nmap -oX report.xml | Save results in XML format.|

Report
---

**Target System Details**

- IP Address: <target_IP> 
- Operating System: <target_OS>

**Port States**

|Port | State |Service |Explanation|
|-----|-------|--------|-----------|
|22/tcp | Open | SSH | Actively accepting connections.|
|80/tcp | Filtered | HTTP | Blocked by a firewall, no response received.|
|443/tcp | Closed | HTTPS | No service running, but port is reachable.|


Conclusion
---
This project demonstrates the importance of network scanning in cybersecurity. By leveraging Nmap’s capabilities, we can identify open ports, services, and potential vulnerabilities in a network. Understanding port states and TCP header behavior enables security professionals to assess and mitigate risks effectively.


