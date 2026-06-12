---
title: "Replace IP adress for existing domain"
date: 2013-06-04
forum: Server Platforms
---

### Post by e-San on 2013-06-04
Hi!

I have one device that tries to connect to one server for upgrade.
It works fine but it is at least slow. I want to connect it to PC that runs DNS and DHCP by a PC-to-PC ethernet cable (no routers or so).
How to setup my DNS to redirect all adreses to my local PC or at least concrete adresses?

Regards!

---

### Post by SeijiSensei on 2013-06-05
1)  You need a special type of cable to this, a "crossover" Ethernet cable.  Regular cables will only work if you connect them to a router.

2)  DNS/DHCP are unneccessary.  Just assign each device a static address in the same subnet, e.g., 10.10.10.10 and 10.10.10.11.

3)  Use /etc/hosts on the client to point hostnames to the other machine's address.  Alternatively just use its IP address for transfers rather than a hostname.

---

### Post by Shrek01 on 2013-06-05
Before you buy a crossover cable or adapter, try a regular cable since many network cards support Auto-MDIX (it will crossover automatically).

[http://en.wikipedia.org/wiki/Auto-MDIX](http://en.wikipedia.org/wiki/Auto-MDIX)

---

