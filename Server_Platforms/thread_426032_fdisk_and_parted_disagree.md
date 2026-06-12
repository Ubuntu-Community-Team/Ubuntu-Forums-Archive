---
title: "fdisk and parted disagree"
date: 2007-04-28
forum: Server Platforms
---

### Post by Bubba Ho-Tep on 2007-04-28
I'm trying to add a disk as a hot spare to a RAID 5 array.

The disk had 'stuff' on it on a ext3 filesystem.

My RAID array is using xfs so I deleted the partition on my disk using cfdisk and gave it a Type FD (raid)

If I query the disk with cfdisk or fdisk they both say it has one partition (the one which I created) and it is of type FD.

However if I query the disk with parted it says it has an ext3 filesystem on it ie the operations I did using cfdisk are being ignored by parted...WTF?

And mdadm is (i think) agreeing with parted cos when i do

sudo mdadm --add /dev/md0 /dev/sda1 

it complains there is no space left on the disk (which makes sense if it has the old ext3 FS still there)

So why are c/fdisk and parted disagreeing?

EDIT: I should have said - when I delete the sda1 partion in parted and try to create another it asks me what filesytem do I want on it. The man page lists a bunch of filesytems  - but I don't want to put a filesystem on it (yet) cos I am using LVM. I just want to format the disk!!!

---

### Post by MJN on 2007-04-28
Have you rebooted since adding/changing the partitions with (c)fdisk? I seem to recall that the last edit I made it rewrote the partition table yet still warned me that a reboot was required for the changes to _properly_ take effect.

Mathew

---

### Post by Bubba Ho-Tep on 2007-04-28
yeah did a reboot (just in case).

Interestingly parted is now reporting that the disk has a raid flag.

---

