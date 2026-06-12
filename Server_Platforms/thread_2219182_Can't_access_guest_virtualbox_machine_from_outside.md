---
title: "Can't access guest virtualbox machine from outside world"
date: 2014-04-23
forum: Server Platforms
---

### Post by sharkey77 on 2014-04-23
I have a headless server (12.04) running a headless virtual machine (12.04).

The Host is assinged a local IP address.

The guest is assinged a WAN IP address on Eth0 using a bridged connection.  It is accessable by domain name or WAN IP on the local network. There are no firewalls running.

Attempting to access any host by domain name or WAN IP off of the internal network results in a blank page.

There are no external IP's in the webserver access log.

Thoughts?

This is a NMAP scan from outside the network:

~$ nmap -v **.**.**.*2/29
```

Starting Nmap 6.40 ( http://nmap.org ) at 2014-04-23 03:19 MST
Initiating Ping Scan at 03:19
Scanning 8 hosts [2 ports/host]
Completed Ping Scan at 03:19, 2.28s elapsed (8 total hosts)
Initiating Parallel DNS resolution of 8 hosts. at 03:19
Completed Parallel DNS resolution of 8 hosts. at 03:19, 0.01s elapsed
Initiating Connect Scan at 03:19
Scanning 8 hosts [1000 ports/host]
Discovered open port 80/tcp on **.**.**.*5
Discovered open port 80/tcp on **.**.**.*4
Discovered open port 80/tcp on **.**.**.*3
Discovered open port 80/tcp on **.**.**.*8
Discovered open port 80/tcp on **.**.**.*7
Discovered open port 80/tcp on **.**.**.*9
Discovered open port 80/tcp on **.**.**.*2
Discovered open port 80/tcp on **.**.**.*6
Discovered open port 4567/tcp on **.**.**.*8
Completed Connect Scan against **.**.**.*3 in 33.82s (7 hosts left)
Completed Connect Scan against **.**.**.*5 in 33.85s (6 hosts left)
Completed Connect Scan against **.**.**.*6 in 34.08s (5 hosts left)
Completed Connect Scan against **.**.**.*7 in 34.20s (4 hosts left)
Completed Connect Scan against **.**.**.*8 in 34.48s (3 hosts left)
Completed Connect Scan against **.**.**.*2 in 34.58s (2 hosts left)
Completed Connect Scan against **.**.**.*4 in 34.59s (1 host left)
Completed Connect Scan at 03:20, 34.63s elapsed (8000 total ports)
Nmap scan report for **.**.**.*2
Host is up (0.12s latency).
Not shown: 999 filtered ports
PORT   STATE SERVICE
80/tcp open  http

Nmap scan report for **.**.**.*3
Host is up (0.095s latency).
Not shown: 999 filtered ports
PORT   STATE SERVICE
80/tcp open  http

Nmap scan report for **********.com (**.**.**.*4)
Host is up (0.13s latency).
Not shown: 999 filtered ports
PORT   STATE SERVICE
80/tcp open  http

Nmap scan report for **.**.**.*5
Host is up (0.12s latency).
Not shown: 999 filtered ports
PORT   STATE SERVICE
80/tcp open  http

Nmap scan report for **********.com (**.**.**.*6)
Host is up (0.11s latency).
Not shown: 999 filtered ports
PORT   STATE SERVICE
80/tcp open  http

Nmap scan report for **.**.**.*7
Host is up (0.11s latency).
Not shown: 999 filtered ports
PORT   STATE SERVICE
80/tcp open  http

Nmap scan report for **.**.**.*8
Host is up (0.11s latency).
Not shown: 998 filtered ports
PORT     STATE SERVICE
80/tcp   open  http
4567/tcp open  tram

Nmap scan report for **.**.**.*9
Host is up (0.11s latency).
Not shown: 999 filtered ports
PORT   STATE SERVICE
80/tcp open  http

Read data files from: /usr/bin/../share/nmap
Nmap done: 8 IP addresses (8 hosts up) scanned in 36.97 seconds


```

---

