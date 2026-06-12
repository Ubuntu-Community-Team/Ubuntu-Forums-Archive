---
title: "Server setup (LVM, what does it get you)"
date: 2008-10-17
forum: Server Platforms
---

### Post by TheGameAh on 2008-10-17
Hey guys.

I'm a big fan of software raid.  With today prices, I just use RAID 10 for pretty much everything.  

But I've never taken it beyond that.  I just partition (usually /boot, /var, /, swap, and the remainder going to a partition I call /netdata), and off I go.

I know LVM let's you resize partitions on the fly, but what are the other benefits?  I always stayed away from LVM because it just seemed like another layer of complexity.  What are the benefits I'm missing?

Also:

How are you software raid gurus setting up your systems?  I normally RAID 10 everything (root, /boot).  But I hear of others just RAIDing their data partitions, and leaving everything else to run on a non RAID drive.  Wouldn't you want your boot system to be raided too?

---

### Post by Robstarusa on 2008-10-17
LVM also lets you do snapshots.  That is what I use it for.  You can then do backups while things are running on the snapshot volume.

I raid1 my boot disk, and use a fileserver for everything else.

---

