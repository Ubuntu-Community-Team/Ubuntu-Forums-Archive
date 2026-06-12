---
title: "Copy HD to HD no eth0 now."
date: 2011-08-30
forum: Server Platforms
---

### Post by Raymond Day on 2011-08-30
The old Ubuntu server 10.10 was on a 100 watt system 160GB drive and I used True Image to copy it to a 25 Watt 500GB system. I had to run "Boot repair Disk" on it then. This other system don't have the same Ethernet. If I lest them they show eth1 in red.

I put in 3 other Ethernet cards in it and still it did not work with any of them.

I downloaded a 11.04 upgread CD. I hope that will fix it.

Any one else know what I could do?

This new system is on a 2 core Atom CPU a Intel Mini-ITX.

The old one has been set up for about a year. So don't want to start new but want to save power. It uses about 1/4 the power of the old system.

-Raymond Day

---

### Post by rubylaser on 2011-08-30
Have you made entries in your /etc/network/interfaces for the new network cards, and have you removed your old NIC from the /etc/udev/rules.d/70-persistent-net.rules file and rebooted?  That should solve all issues.

---

