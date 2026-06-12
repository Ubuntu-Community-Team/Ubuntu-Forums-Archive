---
title: "Empty or adding space"
date: 2009-12-30
forum: The Cafe
---

### Post by esemkay on 2009-12-30
Hi all,

I am new to forum n Ubuntu to...
I have installed Ubuntu with Dual boot.
I have kept 35 gb empty drive and 37gb free space also.
at the time of installation i opted disk partition automatically.
After installation it showing like root has 59.2 mb space free..
and the 35 gb empty drive extended to 68.3gb.
When i am trying to update, it is showing "no enough space".
How do i make space to install updates (450mb) or can add
space to it ? Help me.

---

### Post by Psumi on 2009-12-30
Reinstall ubuntu and partition the entire drive to have ubuntu, never leave un-partitioned space, you can't use it anyway.

I have to be honest as well: I never partition a drive to have more than one partition unless I need to, because I've been taught it causes the drive to work more and will end up dead faster.

Also, the drive that houses ubuntu is the one that should have more space (IE: If you have a 2 GB harddrive and a 30 GB harddrive, put ubuntu on the 30 GB harddrive,)

---

### Post by murderslastcrow on 2009-12-30
I would use the LiveCD and go to System/Administration/GParted, and use the partition editor to extend it to fill up the remaining space, rather than install it from scratch. You should look up how to use GParted if it's unfamiliar or confusing to you.

---

### Post by Psumi on 2009-12-30
> **murderslastcrow said:**
> I would use the LiveCD and go to System/Administration/GParted, and use the partition editor to extend it to fill up the remaining space, rather than install it from scratch. You should look up how to use GParted if it's unfamiliar or confusing to you.

I only suggested reinstalling ubuntu because doing so will not have the user deal with the swap partition, which the user may accidentally delete.

This is also why the swap should be a file, and NOT a partition.

---

