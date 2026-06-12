---
title: "LVM partition"
date: 2011-09-27
forum: Server Platforms
---

### Post by Pyraxic on 2011-09-27
Hello everyone,

I created a new LVM partition using the following method:

virt01:/# fdisk -l

Disk /dev/sda: 598.9 GB, 598997614080 bytes
255 heads, 63 sectors/track, 72823 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          66      524288   83  Linux
Partition 1 does not end on cylinder boundary.
/dev/sda2              66       72823   584426427   8e  Linux LVM

Disk /dev/sdb: 2994.9 GB, 2994998807552 bytes
255 heads, 63 sectors/track, 364121 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x50a056d7

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1      267349  2147480811   8e  Linux LVM


/dev/sdb is about 3.0T hard-drive but when I create a new partition using fdisk /dev/sdb it only created 2.0TB partition.

virt01:/# pvdisplay
  --- Physical volume ---
  PV Name               /dev/drbd0
  VG Name               drbdvg
  PV Size               2.00 TB / not usable 1.00 MB
  Allocatable           yes
  PE Size (KByte)       4096
  Total PE              524271
  Free PE               524271
  Allocated PE          0
  PV UUID               IhSAau-p4Mo-IoWQ-0yMC-ws0G-iNWC-U2UVMk

I would like to know how can I make it utilize the entire hard-drive instead of wasting 1TB of space. I would really appreciate any help.

Thanks!

---

### Post by ajgreeny on 2011-09-27
See this post which explains all.
[http://ubuntuforums.org/showthread.php?t=901368](http://ubuntuforums.org/showthread.php?t=901368)

---

### Post by YesWeCan on 2011-09-27
The MBR partition table system is limited to 2TiB drives. fdisk only works with MBR.

Use Disk Utility to reformat the drive as GPT (GUID Partition Table). Then create a 3GB partition.

Then create your LVM layer
[COLOR="DarkSlateBlue"]sudo pvcreate /dev/sdb1
sudo vgcreate drbdvg /dev/sdb1
sudo lvcreate ...[/COLOR]

---

