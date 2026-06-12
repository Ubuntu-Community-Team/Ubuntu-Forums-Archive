---
title: "syslog"
date: 2005-10-20
forum: Server Platforms
---

### Post by ciscokid on 2005-10-20
Doese anyone know how should I make syslog server, who is going to monitor my logs, from web server!?:confused:

---

### Post by LordHunter317 on 2005-10-20
[QUOTE=ciscokid]Doese anyone know how should I make syslog server, who is going to monitor my logs, from web server!?:confused:[/QUOTE]Whatda mean?  Apache does its own logging by default.

---

### Post by ciscokid on 2005-10-21
Yes, but I would like to monitor different logs, on different terminals... ex. one for web server logs, one for pix firewall logs, and one for ISA server logs!?

---

### Post by gandonov on 2005-10-21
Syslog server is running by default. 
You can setup **different** logfiles for **different** applications.
Example: 
[i]   Routers -> /var/log/routers.log
   Web Server -> /var/log/web.log
   App X -> /var/log/app_X.log [/i]

To setup remote logging: 
**1.** Edit */etc/syslog.conf*. Add this line to */etc/syslog.conf*
*local3.*                        /var/log/cisco.log*
**2.** On router: Configure **syslog** server: _Your_IP_addess_
Note: **local3** is default facility for Cisco routers.

About **Monitoring**:
In the terminal start **tail -f _logfile_**

---

