---
title: "BIND9 Problems"
date: 2005-03-01
forum: Server Platforms
---

### Post by Klunk on 2005-03-01
Hi,

I have installed a base BIND9 and made some minor modifications found in the named.conf man page relating to dynamic updates. My problem is that I have a domain (sjwcc.com) which is hosted externally and I want to use home.sjwcc.com for my home domain. Whenever I **dig home.sjwcc.com** it goes to the external name server and not my local one.

Am I attempting the impossible or should I able to do the above some way ? If anyone has done just this can they assist, my next step is to get the dhcp server talking to dns when a client takes a lease.

---

### Post by alastair on 2005-03-01
Is this just a /etc/resolv.conf issue?

Try :

dig @localhost home.sjwcc.com

---

### Post by Klunk on 2005-03-01
NI, I seem to have got this working now, although I am still experiencing a problem with dynamic updates from dhcp3d

I get a not authorized message.

---

