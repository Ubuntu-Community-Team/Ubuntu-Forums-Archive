---
title: "GRUB rescue prompt"
date: 2011-01-07
forum: Server Platforms
---

### Post by ma0101 on 2011-01-07
After restart my ubuntu server 10.10 got GRUB Rescue promt.
3 HDD (same size) in RAID5 + LVM, GRUB2
md0 - linux
md1 - private files mounted into /home

In rescue mode only knows ls, set and insmod commands.
ls can see drives and LVM partitions.
I set it the prefix and root to
set prefix=(linux-root)/boot/grub
set root=(md0)
or 
set root=(linux-root)
but ls / returned unknown folder.
So I can not go further
I used this doc [https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

Under Ubuntu 10.10 desktop can see the RAID but can not start it.
cat /proc/mdstat
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10]
md0 : inactive sde2[0](S) - missing the others
48828352 blocks

md1 : inactive sde3[0](S) sdg3[2](S) sdf3[1](S) - not starting
5714051904 blocks

unused devices:

I don't know if I can play to add missing devices to RAID or stop and start it causing any bigger damage?
mdadm --add
mdadm -S /dev/md0
mdadm -R /dev/md0

mdadm --query --detail /dev/md0
mdadam --examine /dev/sde2,sde3
same result as cat /proc mdstat


Is there any way to start the server or the RAID partitions to copy my files?

Please help me.
thanks in advance

---

