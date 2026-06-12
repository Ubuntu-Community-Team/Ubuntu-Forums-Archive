---
title: "Nut with snmp support not working"
date: 2008-06-11
forum: Server Platforms
---

### Post by luccom on 2008-06-11
I have installed nut on my hardy server:
sudo apt-get install nut nut-snmp

when I try to start nut with /etc/init.d/nut start I get this message in syslog:
Jun 11 10:55:20 Hobbit upsd[4617]: Can't chdir to /var/run/nut: Permission denied

The permission for /var/run/nut are:
drwxrwx---  2 root nut     40 2008-06-11 10:42 nut

Any idea what I should check next ?

---

### Post by luccom on 2008-06-11
If I change the rights to 777 for /var/run/nut and /etc/nut/* the it work. I think it could be a user or group problem.

---

