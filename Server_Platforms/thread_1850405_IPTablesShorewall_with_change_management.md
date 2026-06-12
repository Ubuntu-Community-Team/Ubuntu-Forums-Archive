---
title: "IPTables/Shorewall with change management"
date: 2011-09-26
forum: Server Platforms
---

### Post by syncmasterpt on 2011-09-26
Hi folks:

 I'm using Ubuntu server in production as a firewall machine, using Iptables/shorewall and the webmin module for configuration.

Everything works fine, but I need help in knowing if it's possible to have the following functionality, namely change request/management.

What I need is that every time a change is made on the firewall configuration through webmin, or not, , a log of what was changed and at what date is made is written.

 Any ideas?

TIA

---

### Post by elico on 2011-09-26
i have an idea for you but it wont work just with webmin...
before each time you are going to make a change do a backup of the iptables to a directory such as 
/var/fwhistory/date_time

and then you will have a list of files that each one of them has the whole firewall rules and on case you want to check something just use the diff command between two files..

---

### Post by syncmasterpt on 2011-09-27
> **elico said:**
> i have an idea for you but it wont work just with webmin...
before each time you are going to make a change do a backup of the iptables to a directory such as 
/var/fwhistory/date_time

and then you will have a list of files that each one of them has the whole firewall rules and on case you want to check something just use the diff command between two files..

Thanks, it's a nice ideia anyway.

---

