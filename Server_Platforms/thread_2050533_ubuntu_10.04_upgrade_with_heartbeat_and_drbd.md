---
title: "ubuntu 10.04 upgrade with heartbeat and drbd"
date: 2012-08-31
forum: Server Platforms
---

### Post by Mordachai on 2012-08-31
I have a dual ubuntu 10.04 server setup with heartbeat and drbd. I want those two servers to upgrade to 12.04. Can i just do a release upgrade on the passive server and then switch over and do the release on the other server? Will heartbeat and drbd keep working after the upgrade?

---

### Post by capnjack on 2013-01-05
I did exactly that a while ago and I'm having issues.  Everything appears to go fine after stopping ldirectord and heartbeat on the primary...all the resources transfer to the secondary...but then the secondary declares itself dead.  Please let me know if you get/got anywhere with this.

> IPaddr2[9226]:  2013/01/05_12:06:00 INFO:  Success
mach_down[7665]:        2013/01/05_12:06:00 info: /usr/share/heartbeat/mach_down: nice_failback: foreign resources acquired
mach_down[7665]:        2013/01/05_12:06:00 info: mach_down takeover complete for node prodlb01.
Jan 05 12:06:00 prodlb02 heartbeat: [1643]: info: mach_down takeover complete.
Jan 05 12:06:07 prodlb02 heartbeat: [1643]: info: Link prodlb01:eth0 dead.
Jan 05 12:06:07 prodlb02 ipfail: [1698]: info: Link Status update: Link prodlb01/eth0 now has status dead
Jan 05 12:06:08 prodlb02 ipfail: [1698]: info: We are dead. :<
Jan 05 12:06:08 prodlb02 ipfail: [1698]: info: Asking other side for ping node count.
Jan 05 12:06:27 prodlb02 heartbeat: [1643]: WARN: node prodlb01: is dead
Jan 05 12:06:27 prodlb02 heartbeat: [1643]: info: Dead node prodlb01 gave up resources.
Jan 05 12:06:27 prodlb02 ipfail: [1698]: info: Status update: Node prodlb01 now has status dead
Jan 05 12:06:28 prodlb02 ipfail: [1698]: info: NS: We are dead. :<

Thanks,
Chaz

---

