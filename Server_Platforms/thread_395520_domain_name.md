---
title: "domain name"
date: 2007-03-28
forum: Server Platforms
---

### Post by aeby on 2007-03-28
hi 
can anyone please tell me how to set the domain name on ubuntu. i know to set the domainname via the network-admin comamnd but i want to know which file gets edited and what command can be used to view the domain name. i want to set up a mail server.

thanks in advance

---

### Post by Aberrix on 2007-03-28
are you talking about a web domain? ie: google.com

or just the hostname of the machine?

web domain, use BIND9

---

### Post by aeby on 2007-03-29
i want to know how to set the domain name like xyz.com, this has nothing to do with DNS

---

### Post by astrogazer on 2007-03-29
You need to edit two files:
/etc/hostname
/etc/hosts

In there you should define your hostname and domain name.

---

