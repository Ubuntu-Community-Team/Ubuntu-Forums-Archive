---
title: "live rezise mdadm RAID1, possible?"
date: 2010-01-18
forum: Server Platforms
---

### Post by SergeiFranco on 2010-01-18
Hello,
I am having a difficulty to resizing RAID1 array (mdadm) to use up all free space on the partition it lives on.

Here is background:
kernel 2.6.28-15-generic (64bit), Ubuntu 9.04
two disks, partitioned 100Mb md0 RAID1 (/boot/ ext2), and rest of space md1 RAID1 (LVM).
I had 250Gb disks in there until 1 failed. Luckily they were hot swappable so I did the following:
got 2 500Gb disks.
Pulled out failed drive.
Inserted new 500Gb drive.
Created partitions (100MB and 499.9GB as Linux Raid).
Added to RAID1 arrays.
Installed grub.
After Re-sync I have replaced second 250GB (fail and remove it from array) with another new 500GB.
Copied partition table.
Added to array.
Re-sync finished successfully.
All was done on live system without reboots.
So here was optimistically trying to resize array to take up free space on the partitions:

    mdadm --grow /dev/md1/ size=max

Only for it to silently fail, and leaving this in dmesg:

    md1: unknown partition table

What can I do for it to resize? Preferably without reboot.

Thanks.

---

