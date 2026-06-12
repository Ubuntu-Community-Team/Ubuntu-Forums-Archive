---
title: "strange port specific scans"
date: 2007-03-29
forum: Server Platforms
---

### Post by dmizer on 2007-03-29
i've had a headless ubuntu dapper server online now for about a year and a half.  since it's been online, i've learned a huge amount about security and system configuration.  however, i'm anything but an expert.  

due to needs which are unrelated to my issue here, the server has a direct connection to the internet, and currently (due to my complete inability to configure iptables via cli) i'm running firestarter as my iptables frontend.  my desktop gui is icewm, but the dm is disabled on boot.

i've installed sysv-rc-conf and disabled as many services as possible in an effort to minimize my profile.  as near as i can see, the only ports that should be open are http, webcache, and ftp (which i've moved to an alternative port).  i am however (as indicated previously) something of a newcommer to server level security, so i defer to more experienced help.

it's entirely possible i'm wrong, but it would seem that i have a script kiddie after me, and my firewall traffic has trippled.  the following port numbers appear to be the foccus of the script:
19595 (udp and tcp)
10421 (udp)
10426 (udp)

i've done some searching for information on these ports but i can't seem to land anything.  so:
1) are (or how do i determine if) these actual attacks/scans?
2) if so, how would someone use these ports to their advantage?
3) how do i determine if i'm vulnerable to these ports?
4) and if vulnerable, how do i prevent myself from being compromised?

thanks for your input.

---

### Post by amohanty on 2007-03-30
For port information a good place to start is:
[http://isc.sans.org/port.html](http://isc.sans.org/port.html)
Just look for ports in the search box in the top right corner.

> due to needs which are unrelated to my issue here, the server has a direct connection to the internet, and currently (due to my complete inability to configure iptables via cli) i'm running firestarter as my iptables frontend. my desktop gui is icewm, but the dm is disabled on boot.


The easier option is to shell out some bucks and buy a SOHO hardware firewall. You can then have the ease of use of a web based gui and all the advantages of a real firewall, especially if you have the server open on the internet.

Install nmap and run the following and post the output.
sudo nmap -vv -sS -p 1-65535 your_ip_here

HTH
AM

---

### Post by huygens on 2007-03-30
> **amohanty said:**
> sudo nmap -vv -sS -p 1-65535 your_ip_here

Hum as it seems that the scan is on the UDP port (and one TCP), -sS is maybe not the better check. You could anyway launch it (might be pretty slow to scan all ports!), but you should also check it in UDP using -sU, so:
```
sudo nmap -v -sU -p- your_ip_here
```N.B.: -p- is equivalent to -p1-65535

Or you can mix the two and scan only the ports you have reported + you can scan after "standard" nmap ports:
```
sudo nmap -v -sU -sS -p U:10421,10426,19595,T:19595 your_ip_here
sudo nmap -v -sU -sS your_ip_here
```As for the port themselves, it seems that Dell uses 10421 and 10426 for "singleclick discovery or icc" which I have no clue what their purpose are. However, this is only under Windows. If you're using Linux, no worries.  No clue about 19595, but if it is coming from the same host, I would guess it is trying to discover other vendor services from a Windows based host.

---

### Post by Mr. C. on 2007-03-30
You are going to see all sorts of port scans, connection attempts, etc.  It's all part of the territory.

The key is to *knowing* that your firewall is configured correctly.  If you do not have confidence in your ability to configure iptables securely, I'd suggest, like the other poster, a cheap commodity hardware firewall with easy interface.  You can maintain your current IP tables for a double layer of security, and feel secure while you you learn.

Don't fool yourself with a belief that moving FTP to another port makes it more secure - its simply blunts the brute force attacks.

MrC

---

### Post by amohanty on 2007-03-30
> Hum as it seems that the scan is on the UDP port (and one TCP), -sS is maybe not the better check.

Oops! Sorry about the typo.  Thanks.
AM

---

