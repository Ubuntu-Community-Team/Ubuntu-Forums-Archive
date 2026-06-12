---
title: "NIC card"
date: 2009-07-06
forum: Server Platforms
---

### Post by torque154 on 2009-07-06
I upgraded to a new server without reinstalling.  everything works except the network card. settings from the old server are in place all I need to do is get it running. I am running 8.04 terminal server.  how would i get it to reconise it?

---

### Post by peepingtom on 2009-07-06
First you should post the results of ```
lspci |grep Ethernet
``` so the community can determine the chipset of your NIC.

---

### Post by torque154 on 2009-07-06
that command couldn't filter out the ethernet card, but I found it.


```
01:08.0 Ethernet controller : Intel Corporation 82562EZ 10/100 Ethernet Controller (rev 02)


00:1f.1 Ethernet controller: ADMtek NC100 Network Everywhere Fast Ethernet 10/100 (rev 11)


```

---

