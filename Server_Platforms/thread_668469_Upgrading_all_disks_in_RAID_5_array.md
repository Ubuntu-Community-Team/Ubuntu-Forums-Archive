---
title: "Upgrading all disks in RAID 5 array"
date: 2008-01-15
forum: Server Platforms
---

### Post by aboutblank on 2008-01-15
Hello all. I'd like to upgrade all disks in my raid5 array and move from ext3 to XFS without losing data. I believe this is possible.

My current set up is 3 x 250 GB drives in software RAID5. Each disk has a partition flagged for software raid, and mdadm makes the logical device out of these partitions. I formatted the logical device as ext3. I'm not using LVM

First, I will backup all critical data. I don't have enough storage for all non-critical data, but I would prefer not to lose it.

Second, I physically get the three new drives (500 GB) into the system.

[LIST]
[*]Replace a 250 GB drive with 500 GB
[*]Allow for rebuild
[*]fsck
[*]Repeat until all three drives in
[/LIST]

I believe at this point, the partitions flagged as software raid will only be 250GB on each disk. 

[LIST]
[*]Make new partitions on each new drive as Linux raid
[*]Use mdadm to create md3, a new raid 5 array using the newly created partitions
[*]Set up LVM on md3
[*]Make XFS filesystem on the lvm device (/dev/lvm-raid/lvm0)
[/LIST]

Am I correct in assuming it's necessary to form a new array, or would resizing and conversion to XFS be possible? Can someone briefly explain in laymens terms why I want to do LVM? I believe I understand but humor me...

[LIST]
[*]Mount new XFS filesystem
[*]Transfer all data to new filesystem
[*]Unmount
[/LIST]

[LIST]
[*]Delete mdadm array md2
[*]Delete all md2 (old ext3) partitions
[*]Grow new data partitions on each drive
[*]Grow mdadm array md3 (might be done automagically?)
[*]Grow XFS filesystem using xfs_grow
[*]Eat cake
[/LIST]

Am I correct in that I can grow the whole system like this?

Thank you for your time!!

---

### Post by aboutblank on 2008-01-20
Bump... Anyone have any thoughts?

---

### Post by chrisdeckard on 2008-01-21
I would probably do the following, provided you have enough slots for your drives.

1)  Install your new drives
2)  Create a new md device using your new three drives.
3)  Create an LVM volume group on your new md.
4)  Create an LVM logical volume.
5)  Copy all your data from the old md to the new.
6)  Destroy the old md.
7)  Create a new md on the old drives.
8)  Use lvm to add it to your new logical volume.

Now you're using your old and new drives to have one nice big storage.  Of course, you have to have the power and drive connections to do it.  No sense in letting 500GB of potential storage go to waste.

-Chris

---

### Post by smileypaul on 2008-01-21
Any particular reason to use xfs? 

I find ext3 to be very reliable.. but, its onyl downfall is the 2TB limit.. i did some research a while back between xfs and reiserfs .. i ended up using reiserfs for a 3tb raid5 system.. but i can't remember why..

do some research!

good luck

---

