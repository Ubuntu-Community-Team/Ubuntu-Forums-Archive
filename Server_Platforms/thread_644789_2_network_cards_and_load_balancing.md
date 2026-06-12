---
title: "2 network cards and load balancing"
date: 2007-12-19
forum: Server Platforms
---

### Post by keiffee30 on 2007-12-19
Hi all, i am setting up a server that has got 2 Nic's in. The server is going to be a 

DNS
Samba
LAMP (intranet)
File 
Database

The 2 Nic's are both Gb and i would like to know if i can get both the nics to share the network load. The spec of the server is not that big. its only

1.88Ghz Zxon x2
2Gb Ram
1066 Bus
16Mb Video
73GB HDD
1Gb NIC x 2

Im using 7.10 server 64Bit and have put a GUI interface on. If this can not be done, i will just plug them both into a Gb switch. 

Any comments

---

### Post by HermanAB on 2007-12-19
Yes, it can be done, but it is not as simple as one would hope.  See the Advanced Routing Howto on tldp.org.

The trouble is that many protocols, such as HTTP is not stateful, yet they get confused when one transaction happens on one interface while the next happens on the other interface.  Therefore, the load balancing software has to ensure that once a specific machine connected to the server over a specific interface, it will from then on always use that same interface.

Cheers,

Herman

---

### Post by keiffee30 on 2007-12-19
ok thanks for the input into this. i think i will stay with just the 2 Gb cards in the switch. 


Many thanks

---

