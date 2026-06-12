---
title: "Can't install GRUB on GPT, raid and LVM"
date: 2014-10-14
forum: Server Platforms
---

### Post by harveyd on 2014-10-14
Hi, trying to install ubuntu server 14.04 on two 3TB hard drives, I have created a 1MB partition and selected the "Reserved Bios boot area" option on both drives e.g. /dev/sda1 and /dev/sdb1. Then created a big partition filling the rest of the disks and selecting them for use as raid. Then create the raid on the two partitions e.g. /dev/sda2 and /dev/sdb2 and then LVM on top of the raid with LV's for swap, root and data, set formats and mount points etc. Installation goes through but grub fails to install on /dev/sda "This is a fatal error". Any ideas?

I followed this guide but added LVM on top of the Raid:-

[http://stackful-dev.com/raid-install-ubuntu-server-on-a-large-hard-drive.html](http://stackful-dev.com/raid-install-ubuntu-server-on-a-large-hard-drive.html)

---

### Post by harveyd on 2014-10-14
Ok, so solved this, I did the following:-

2M "Reserved Bios boot area" partition, 550M partition RAID , Remaining disk RAID on each drive. Created two raids, one on the 550M (md0) and one on the Remaining (md1). Mounted md0 raid at /boot and created LVM on md1 and created root, swap and data as LV's etc.

---

