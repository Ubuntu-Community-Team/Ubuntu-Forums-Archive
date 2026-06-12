---
title: "EXT4 to XFS and Partitions"
date: 2012-01-07
forum: Server Platforms
---

### Post by Phixion on 2012-01-07
Hey guys,

I have a server running Ubuntu 11.10 with an EXT4 Filesystem. The server has RAID0 and is on a dedicated Gbit connection. I'd like to switch to XFS Filesystem as I've heard it's very good with fast connections.

The problem is my host doesn't have an option to install an XFS filesystem.

My current partition setup is as follows:

2x512MB /boot
2x512MB /swap
Remainer /

I've read that you don't need a /swap partition if you have a certain amount of memory, my server has 4GB, should I be using /swap? If so how big? My server host doesn't let me reinstall without a /swap partition.

Any help appreciated!

Regards,

Phixion

---

### Post by hawkmage on 2012-01-08
In some cases you can get away without swap space but it is not recommended.  

Linux will use memory for caching device I/O and it will try to use as much memory as possable.  If it can't swap idle pages out of memory you will degrade performance.  

Also it can help a system from memory starvation if you have an application with a memory leak.  Leaked memory will almost always be idle so it will be swapped out freeing real memory.

---

### Post by rubylaser on 2012-01-09
Just a little word of warning about XFS.  I used it a few times in the past for large datastores and experienced filesystem corruption in almost all cases.  I've used ext3/4 since then, and have never had that problem since then.

Also, if your disks are fast enough, ext4 should be able to saturate a gigabit connection just like XFS.

And, you'll want to leave the swap space intact.  It's not like 512MB is a massive amount of storage space being used up.

---

### Post by SeijiSensei on 2012-01-09
> **rubylaser said:**
> Just a little word of warning about XFS.  I used it a few times in the past for large datastores and experienced filesystem corruption in almost all cases.  I've used ext3/4 since then, and have never had that problem since then.

I had a similar experience with XFS when I used it on an external drive.  Since the drive contained mostly video files, I gave XFS a spin since it was designed to handle large files well.

The XFS filesystem on this device *never* survived a power loss without a substantial loss of data.  Like rubylaser I've returned to the ext4 fold.  XFS might work well on internal drives in a stable environment like a rack server, but I won't ever use it again on a machine at home.

---

