---
title: "[SOLVED] Another port 80 problem"
date: 2008-11-08
forum: Server Platforms
---

### Post by R.Bucky on 2008-11-08
Hey all - yes, this is another port 80 problem. I am working with a fresh Ubuntu 7.10 LAMP install. I am unable to access my web site outside my network. I have allowed port 80 and tried allowing other ports using UPnP on my router. I am using canyouseeme.org to verify any open ports, but it is a no-go for 80. My ISP is not blocking this port. I have had a successful server not more than a few days ago. I can ping buckyspalace.net and localhost, netstat -ntlp shows port 80 listening, and I used Firestarter to modify iptables to allow port 80. The firewall is currently disabled. Ports.conf is configured properly to Listen 80. 

Killn' me here. Help!?

---

### Post by R.Bucky on 2008-11-08
Ok, I hate it when I figure it out ahead of time. The solution: I changed modems (I neglected to mention that to the post), which apparently change my 192.168.1.1 to 192.168.1.101. Who would have thunk it. The solution was to visit the UPnP and alter the last digits of the address. Simple as pie.
SOLVED!!!

---

