---
title: "disk detection order"
date: 2011-03-02
forum: Server Platforms
---

### Post by zaq.hack on 2011-03-02
I've run into quite a puzzle and I'm not sure where to go with it (hence, here I am).

The machine in question is meant to be a cheap, large video archive. It has one 40GB IDE drive (/dev/sde) and six 2TB drives in a RAID 5 (sda, sdb, sdc, sdd, sdf, sdg). I used Ubuntu Server 10.10, set up a software raid with mdadm, and all was peachy.

A few boots later, now the system drive is /dev/sda ... and my RAID assembly fails. Is there a way to nail down the drive order such that this doesn't keep flipping around?

I understand there are UUIDs for "regular" file systems to help make this process more graceful. Is there a similar process for mdadm? Or am I just at the mercy of whichever PCI device decides to muscle in line first (the IDE or the SATA controller)?

---

