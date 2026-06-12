---
title: "Ubuntu 10.04 - SSH problem"
date: 2011-06-09
forum: Server Platforms
---

### Post by Mark M. on 2011-06-09
OS: Ubuntu 10.04 LTS
Problem Child: OpenSSH Server

Symptom(s): Unable to connect via PuTTY from Windows PC on LAN.

Troubleshooting Performed: 

Followed the troubleshooting guidelines from the following link:
[https://help.ubuntu.com/community/SSH/OpenSSH/Configuring#Troubleshooting](https://help.ubuntu.com/community/SSH/OpenSSH/Configuring#Troubleshooting)
Able to connect via localhost.

Ubuntu Server can ping Windows PC and vice-versa.

PuTTY client on Windows PC errors upon attempted SSH connection with "Network error: Connection timed out"
*edited to add: *Also discovered that I am unable to browse to the webmin control panel on port 10000 from another PC.

ufw has not been enabled.



So, what am I overlooking?             ](*,)

---

### Post by Mark M. on 2011-06-09
**Solution**:  Turn off the ******* N0rt0n firewall on the Windows PC.   [B][I]Oy vey!




[/I][/B]

---

