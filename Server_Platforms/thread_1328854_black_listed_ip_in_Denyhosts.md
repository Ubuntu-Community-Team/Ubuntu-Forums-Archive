---
title: "black listed ip in Denyhosts"
date: 2009-11-16
forum: Server Platforms
---

### Post by BlackSwordD2 on 2009-11-16
my ip was blacklisted when using denyhosts on an openssh server and when it is removed from the blacklist it reappears soon after. cant seem to get the purge flag to work and in desperate need of help

---

### Post by cariboo on 2009-11-17
There are several files in /var/lib/denyhosts that you have to remove your ip address from. You should also add your ip address to /etc/hosts.allow.

---

