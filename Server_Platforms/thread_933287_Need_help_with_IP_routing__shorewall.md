---
title: "Need help with IP routing / shorewall"
date: 2008-09-29
forum: Server Platforms
---

### Post by jlounds on 2008-09-29
Hello everyone!

I am running Hardy 2.6.24-19-server and have installed shorewall and have it (mostly) working.

The problem is, I cannot access the external IP when inside the network, but I can get to other IP addresses in the sub net just fine.

eth0 - external IP - 210.x.55.41

eth1 - internal IP - 192.168.168.1

I have masq working in Shorewall and from my laptop (192.168.168.99) can access the 'net, and a traceroute to 210.x.55.42 shows it is being routed very nicely:

traceroute to 210.x.55.42, 64 hops max, 40 byte packets
 1  192.168.168.1 (192.168.168.1)  2.732 ms  3.519 ms  2.009 ms
 2  210.x.55.42 (69.41.11.37)  9.548 ms  2.135 ms  1.960 ms

BUT, I cannot ping or traceroute or anything to

210.x.55.41

I did get it working (sort of) using a rule in shorewall of DNAT, but that makes a mess when I try and use resources on the server.

I KNOW it cannot be that difficult -- any ideas would be greatly appreciated!

Jeremy

---

### Post by alastair on 2008-09-29
Maybe post some of your shorewall config e.g.

policy
rules
masq
interfaces
zones

---

