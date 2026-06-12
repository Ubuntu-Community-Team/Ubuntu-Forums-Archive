---
title: "can't connect to MSN with Pidgin while using FireStarter and ICMP Filtering"
date: 2008-12-08
forum: Security
---

### Post by pooppoop on 2008-12-08
just as the title says.
the log looks like this:
port   Source         Protocol   Service
 80    <localhost>     ICMP        HTTP

is there something i can do to fix it?
It seems that by setting the ICMP Filtering, no other rule can open it.

---

### Post by cdenley on 2008-12-08
> **pooppoop said:**
> just as the title says.
the log looks like this:
port   Source         Protocol   Service
 80    <localhost>     ICMP        HTTP

is there something i can do to fix it?
It seems that by setting the ICMP Filtering, no other rule can open it.

Some things require ICMP. It does not surprise me that filtering all ICMP packets would cause something to break. It is allowed by default for a reason.

---

### Post by Sarmacid on 2008-12-09
You could try creating a couple of rules in iptables, one to allow all outgoing ICMP packages and one allowing only incoming established ICMP packages.

---

### Post by pooppoop on 2008-12-09
The thing is that aMSN works while pidgin does not.
and the only icmp i want to be allowed is the ones required by pidgin, how
can i find what they are, and add them manualy to the iptables?

---

### Post by kevdog on 2008-12-09
You could run wireshark to sniff the packets -- grab one of the packets and then choose the option to follow the stream.  Usually that helps me figure out a lot of things.

Whats the deal with denying icmp anyways?  Despite what others may feel, I dont think leaving your machine open to just pings is a security risk.

---

### Post by pooppoop on 2008-12-12
Solved,
i just used a fork of the original msn plugin provided by pidgin.
sudo apt-get install msn-pecan
to get it.
Homepage:
[http://code.google.com/p/msn-pecan/](http://code.google.com/p/msn-pecan/)

---

