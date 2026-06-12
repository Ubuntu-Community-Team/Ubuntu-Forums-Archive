---
title: "Windows 7 won't install to a partition"
date: 2009-11-11
forum: The Cafe
---

### Post by blueshiftoverwatch on 2009-11-11
I freed up 95GB of space on my hard drive to install Windows 7 onto but I can't get it to install onto a partition.

After using System Rescue CD to partition the space I loaded up the installation DVD. But when I go to the part where it asked me where I wanted to install it I couldn't use the unallocated space because "*Setup was unable to create a new system partition or locate an existing system partition. See the setup log for more information*".

So I've tried various ways to get it to work and so far nothing is working: 

&#8226; Tried clicking on the advanced options link at the bottom of the Windows partition selector and installing to an new partition created out of the unallocated space and it wouldn't work.

&#8226; Tried changing the unallocated space to "unformatted" space in System Rescue CD. It wouldn't work.

&#8226; Tried formatting the new partition and it wouldn't work.

&#8226; I got an error message at one point saying that the partition was of an unrecognised type and that I needed to be NTFS. So I went into System Rescue CD and formatted it to NTFS. It didn't work.

For giggles I selected all of my partitions (both Ext3's, XFS, and FAT32) to see if the "next" button would allow me to continue. But Windows 7 didn't deem any of them worthy of installing it's self onto either.

Anyone else run into similar problems or know what's going on?

---

### Post by CharlesA on 2009-11-11
How many partitions do you have on your drive? The max is 4 primary partions on a basic disk.

Also: What does the setup log say?

---

### Post by natedawg on 2009-11-11
Yeah sounds like you have too many partitions. I had Ubuntu installed and then just installed Windows in the unused free space. You do know that Windows 7 needs a special system boot partition as well as its install partition right? 

If all else fails I would just wipe the whole drive and install Windows 7 first.

---

### Post by MasterNetra on 2009-11-11
> **natedawg said:**
> Yeah sounds like you have too many partitions. I had Ubuntu installed and then just installed Windows in the unused free space. You do know that Windows 7 needs a special system boot partition as well as its install partition right? 

If all else fails I would just wipe the whole drive and install Windows 7 first.

+1

Windows 7 creates a "recovery" partition which is about 100MB's in size. It will take the 100MB's out of the space/patition your installing it into. So most likely it sounds like you have 3+ partitions. Ftw Swap I believe is counted as a Partition.

---

### Post by wilee-nilee on 2009-11-12
If this is a upgrade version of W7 your key will not work with a fresh install. But you can call MS W7 tech team and they will get your key verified. There are some cracks on the net for the upgrade key on a fresh install that work and are easy to implement, but then your install with a cracked key is not considered valid technically to MS although the updates will not notice. MS tracks computers so a cracked key install sooner or later has the chance of being shutdown. The keys for retail and upgrades are specific to the type of purchase, the upgrade OS and retail are basically the same OS.

---

### Post by blueshiftoverwatch on 2009-11-12
> **CharlesA said:**
> How many partitions do you have on your drive? The max is 4 primary partions on a basic disk.
As long as I install Windows 7 first I can add as many partitions as I want later on, right? Because in addition to the 2 partitions that Windows 7 takes up I plan on adding about 5 more when I install Linux.
> **natedawg said:**
> You do know that Windows 7 needs a special system boot partition as well as its install partition right?
I do now.
> **natedawg said:**
> If all else fails I would just wipe the whole drive and install Windows 7 first.
That's what I ended up doing. Why does Windows care how many partitions I have though?

---

