---
title: "Hardware or Software Issue?"
date: 2018-10-19
forum: Server Platforms
---

### Post by mhumm2 on 2018-10-19
I have US 18.04.1 installed on a Supermicro X9SCM mobo.  I've been configuring the server for a NAS and samba, and SSH.  Today, all of a sudden, I am unable to ssh into the server.  I troubleshot the problem to one of my LAN ports being offline.  In other words, no winky-blinky lights on that port nor on my switch (the other side).  This mobo has an IPMI, LAN1 and LAN2 ports. When I boot the server, all ports are active, then 1 and 2 go out, and back on again.  Then, when the OS is finished loading, LAN2 goes dark.  Now here's the weird symptom:

ifconfig displays no active ports, only lo, loopback.  So why doesn't ifconfig display LAN1 and IPMI ports?  The fact that the port is active during bootup and inactive after bootup tells me this is a software, US 18.04.1 issue and not hardware.  Please advise.

mhumm2

---

