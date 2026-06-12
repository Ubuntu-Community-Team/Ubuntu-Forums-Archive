---
title: "clean, degraded disk statuses after boot-repair (raid 1)"
date: 2012-02-28
forum: Server Platforms
---

### Post by Peter222 on 2012-02-28
I repaired grub with boot-repair after power lost (can't started system, reboot before grub).
System start now and everything looks OK but I have clean, degraded statuses on disks partitions.

fdisk, mdadm --details:
[http://pastebin.com/ycZ06SiJ](http://pastebin.com/ycZ06SiJ)

Dysk /dev/md0 nie zawiera poprawnej tablicy partycji (ENG: no correct partition table)

What can I do?

ubuntu 10.04

---

