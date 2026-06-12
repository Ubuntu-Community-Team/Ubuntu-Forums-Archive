---
title: "UFW allow apache full but port are closed"
date: 2017-12-18
forum: Server Platforms
---

### Post by mauro_ita on 2017-12-18
Dear all,

I'm spending days trying to figure out what is wrong and where on my Ubuntu 16.04 server where I run Apache as web server.

I can't manage to get the port 80 and 443 open

```

root@server:/var/www# ufw status
Status: active

To                         Action      From
--                         ------      ----
Apache Full                ALLOW       Anywhere                  
OpenSSH                    ALLOW       Anywhere                  
10000/tcp                  ALLOW       Anywhere                  
80/tcp                     ALLOW       Anywhere                  
Apache Full (v6)           ALLOW       Anywhere (v6)             
OpenSSH (v6)               ALLOW       Anywhere (v6)             
10000/tcp (v6)             ALLOW       Anywhere (v6)             
80/tcp (v6)                ALLOW       Anywhere (v6)

```

but when I run nmap to the server ip...
```

root@mauro-C700:~# nmap -p80,443 10.0.0.200

Starting Nmap 7.01 ( https://nmap.org ) at 2017-12-18 10:05 CET
Nmap scan report for 10.0.0.200
Host is up (0.00056s latency).
PORT    STATE  SERVICE
80/tcp  closed http
443/tcp closed https
MAC Address: 00:22:19:30:BF:6A (Dell)

Nmap done: 1 IP address (1 host up) scanned in 0.52 seconds
```

I've no idea from where I should start investigare before thinking on reinstalling :frown::frown::frown:

cheers

---

### Post by howefield on 2017-12-18
Thread moved to the "*Server Platforms*" forum.

---

### Post by darkod on 2017-12-18
Have you tried using iptables instead of ufw? I find ufw to be too messy and without any need. It just complicates things as frontend for iptables...

It looks you have the rules set up correctly. Are you performing the testing from the same LAN, there are no routers in between that would have firewall enabled and block the ports?

---

### Post by LHammonds on 2017-12-18
If I were you, I'd specify ports directly rather than using shortcut names so you know exactly what is going on.

Here is an example firewall script for my Apache web server.

enable-firewall.sh
```

#!/bin/bash #############################################
## Name          : enable-firewall.sh
## Version       : 1.1
## Date          : 2017-04-13
## Author        : LHammonds
## Compatibility : Ubuntu Server 14.04-16.04 LTS
## Requirements  : Run as root
## Purpose       : Restore and enable firewall.
## Run Frequency : As needed
## Exit Codes    : None
################ CHANGE LOG #################
## DATE       WHO  WHAT WAS CHANGED
## ---------- ---- ----------------------------
## 2015-08-28 LTH  Created script.
## 2017-04-13 LTH  Added comments in rules.
#############################################

## Requirement Check: Script must run as root user.
if [ "$(id -u)" != "0" ]; then
  ## FATAL ERROR DETECTED: Document problem and terminate script.
  echo -e "\nERROR: Root user required to run this script.\n"
  echo -e "Type 'sudo su' to temporarily become root user.\n"
  exit
fi

clear
echo ""
echo "Resetting Firewall to factory default"
echo y | ufw reset 1>/dev/null 2>&1
ufw default deny incoming 1>/dev/null 2>&1
ufw default allow outgoing 1>/dev/null 2>&1
echo "Allowing SSH from only LAN connections"
ufw allow from 192.168.1.0/24 to any port 22 comment 'SSH via LAN' 1>/dev/null 2>&1
echo "Adding Application-specific rules"
echo "Allowing Samba file sharing connections"
ufw allow proto tcp to any port 135,139,445 comment 'Samba Share' 1>/dev/null 2>&1
ufw allow proto udp to any port 137,138 comment 'Samba Share' 1>/dev/null 2>&1
echo "Adding MySQL/MariaDB rules"
ufw allow from 192.168.107.0/24 proto tcp to any port 3306 comment 'MariaDB via LAN' 1>/dev/null 2>&1
ufw allow from 192.168.2.0/24 proto tcp to any port 3306 comment 'MariaDB via LAN' 1>/dev/null 2>&1
echo "Adding Web Server rules"
ufw allow proto tcp to any port 80 comment 'Web Service' 1>/dev/null 2>&1
ufw allow proto tcp to any port 8080 comment 'Web Service Alt' 1>/dev/null 2>&1
ufw allow proto tcp to any port 443 comment 'Web Service SSL' 1>/dev/null 2>&1
echo "Enabling firewall"
echo y | ufw enable 1>/dev/null 2>&1
echo "Firewall enabled and all rules have been configured."

```

---

### Post by darkod on 2017-12-19
I would stop using ufw completely. It makes troubleshooting complicated too. For example if you list your rules now with 'iptables -L -n -v' you will see bunch of info, chains, etc, while when using only iptables directly that info is much clearer and to the point.

It's up to you what you use, I also used ufw for a project few years back when I didn't feel comfortable with iptables and soon realised I would be much better off by using iptables instead of ufw frontend.

---

### Post by mauro_ita on 2017-12-21
Thanks for your helps.

After uninstalling UFW, flat the router settings and other crazy approaches to the problem I'm considering that the ISP has blocked the ports after some tries I made on setting certificates for https thinking of sorts of attack to the IP....

I'm now trying to get in touch with the ISP and double check.

Keep u posted and in the meanwhile check your suggestions about using iptables rather than UFW

merry Xmas

---

### Post by QIII on 2017-12-21
Hello!

If you are trying to run a web server on a residential connection, virtually all ISPs block ports 80 and 443.  They will only allow them for commercial accounts.

Cheers!

---

### Post by LHammonds on 2017-12-22
In the Apache config file, change the website port from 80 to 81 (or other numbers), reload the config and see if it goes though.  If so, you will know the ISP is blocking 80.

My residential ISP doesn't seem to block ports but then again, it really doesn't matter.  I have a 4 meg download, 0.1 upload.

---

### Post by mauro_ita on 2017-12-29
> **QIII said:**
> Hello!

If you are trying to run a web server on a residential connection, virtually all ISPs block ports 80 and 443.  They will only allow them for commercial accounts.

Cheers!

Thanks.

the crazy thing is that I've been able to run the webserver for months when all of a sudden I couldn't anymore.

I phone the ISP but explain to check IP ports to a phone center and not to a technician is out of control. At the end the ISP said all ports are open... (reliable answer? big question mark but worth try asking)

cheers and best wishes for the 2018

---

### Post by The Cog on 2017-12-29
Are you sure they're still open on the webserver? what's the output of this (run it on the webserver)? ```
netstat -lnt
```
P.S. 
A firewall will normally just drop packets on blocked ports, and nmap would show those as **filtered**. If nmap says **closed** that means it has received a reply, which probably means the server is not listening for incoming connections on that port. [https://nmap.org/book/man.html](https://nmap.org/book/man.html)

---

