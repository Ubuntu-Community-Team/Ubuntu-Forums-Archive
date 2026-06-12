---
title: "Suspected device on my Wireless network"
date: 2014-08-17
forum: Security
---

### Post by valery5 on 2014-08-17
Hello everybody. I have a concern. Using the program ***SoftPerfect WiFi Guard*** I have discovered a **suspected device**. Only me and my mother use this wireless connection. *SoftPerfect WiFi Guard *detects our computers and the router plus this suspected device. At first, I thought it could be the cordless but I am not sure a cordless has a MAC ADDRESS... Has it?

However, I have made a scan with*** Nmap*** and this is the feedback: 139/tcp open  netbios-ssn Samba smbd (workgroup: WORKGROUP) ; 515/tcp open  printer

Checking the internet you can see there are a lot of exploitations related to printer open ports and netbios open port (however, I don't have any printer. Now, I am using Ubuntu but when I was using Windows already I noticed that I had printer enabled and I could not switch off it).

I have just scanned my laptop with Nmap and it says that all doors are closed. However, concern remain about this unknown device and its open ports. Can be the cordless?

---

### Post by TheFu on 2014-08-17
Please post the entire **nmap -sT** output.
Does it have a unique IP address?
Can you ping it?
Could the router have a USB port and act as a print server?

---

### Post by bashiergui on 2014-08-17
Yes please post the nmap -sT output. Also consider trying to fingerprint it with```
nmap -sV -O -v 192.168.x.x
``` where obviously you'd use the ip of the rogue device you found.

---

