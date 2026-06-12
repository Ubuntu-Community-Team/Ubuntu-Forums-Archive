---
title: "IP aliases centralization?"
date: 2009-03-06
forum: Server Platforms
---

### Post by khantastic on 2009-03-06
Hello.

Is there an easy and flexible way to share hosts-file information for different subnets, i.e. IP aliases in a centralized localization? 

In a development platform we have 5 different subnets. Each subnet consists of servers and dedicated hardware units. If we access the different units from the same computer, only the local /etc/hosts-file needs to store IP aliases.

However, the different units will be accessed from more than one computer, thus each PC needs to maintain their hosts-file. Changing IP for one of the units or simply adding a new unit, all PCs have to update their hosts-file. This results too often in inconsistency in hosts-files.

One of the servers, Ubuntu 8.04, have 5 network cards installed and are able to access every unit in the test environment. Is there a way to share this hosts-file to other computers in an automated way?

Any suggestions on how to solve this? Thanks.

---

### Post by netztier on 2009-03-07
> **khantastic said:**
> Is there a way to share this hosts-file to other computers in an automated way?


That's what DNS was invented for. BIND is probably the popular implementations of DNS.

[http://langfeldt.net/DNS-HOWTO/BIND-9/DNS-HOWTO-1.html](http://langfeldt.net/DNS-HOWTO/BIND-9/DNS-HOWTO-1.html)

and for our beloved Ubuntu:
[https://help.ubuntu.com/community/BIND9ServerHowto](https://help.ubuntu.com/community/BIND9ServerHowto)


regards

Marc

---

### Post by koenn on 2009-03-07
> **netztier said:**
> That's what DNS was invented for. BIND is probably the popular implementations of DNS.
so true.
but for a simple, easy implementation, dnsmasq is also an excellent choice.
it's in the repo's, and the comments in the config file are enough the help you set it up.

---

