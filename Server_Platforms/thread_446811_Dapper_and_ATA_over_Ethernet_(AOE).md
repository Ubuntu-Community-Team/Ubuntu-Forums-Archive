---
title: "Dapper and ATA over Ethernet (AOE)"
date: 2007-05-17
forum: Server Platforms
---

### Post by qhartman on 2007-05-17
I just wanted to post my findings using ATA over Ethernet devices with Dapper. When I was doing my research, I had a hard time finding information, so maybe this will help someone else.

Specifically I'm using a Coraid 1521 AOE shelf which is populated by 4 500GB Seagate ES drives in a RAID 5 array. I'd imagine my findings would be similar when using other devices.

Out of the box, Dapper gets solidly modiocre performance with AOE. Using the "ddt" tools that Coraid built, I got about 25-28MB/sec reading and writing with 30-40% CPU utilization.

Upgrading the aoe kernel module and aoe tools to the latest ones provided by Coraid and upping the MTU on the interface being used to connect to the AOE device boosted performance substantially. Writes are now happening at a respectable 76MB /sec, and reads are happening at 40MB /sec.

I honestly expected these numbers to be higher, but the machines I am testing with right now are pretty old, dual processor P-III, one at 700Mhz, the other at 500. I'd wager they are just about saturated with that much data moving through them.

I'm hoping to start testing with more modern equipment soon and I'll post my findings.

---

