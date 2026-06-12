---
title: "HA with drbd failover not work"
date: 2015-03-16
forum: Server Platforms
---

### Post by nuke2 on 2015-03-16
hi all.
I did the solution in
[https://help.ubuntu.com/community/HighlyAvailableiSCSITarget](https://help.ubuntu.com/community/HighlyAvailableiSCSITarget)

Everything is ok, but failover not work.
I tested replicated image, it works well. But when server 1 is dead, client shows BSOD(windows 7 image).
I used M$ windows 7 SP1 image on ubuntu 14.04 LTS server, and iso image is in zfs subvolume.
Sorry for my poor English, please someone help me.

---

### Post by nuke2 on 2015-03-19
Anyone?
Please show me even just where to ask it about.

---

### Post by Thirtysixway on 2015-03-19
Are you using the iSCSI virtual IP address as the target from your windows system?

Does it crash regardless of which node goes down?

---

