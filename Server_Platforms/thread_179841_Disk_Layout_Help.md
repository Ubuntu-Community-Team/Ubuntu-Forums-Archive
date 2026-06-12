---
title: "Disk Layout Help"
date: 2006-05-20
forum: Server Platforms
---

### Post by oboontoo on 2006-05-20
I was told to post in here after having posted in Absolute Beginner (which I am)

I'm trying to set up my first linux server with Dapper Drake and I'm unsure how to best layout the disks
I currently have 4 Raptors on 74Gb and 4Gb of memory.
I want to have the best performance and a bit of fail safe to go with that.
I don't care about if one of of the harddrives crashes and I have to reinstall the OS, so the OS and any programs can be on raid 0, but my data needs to be on raid5.

How would you guys put the disks to good use?

Martin

---

### Post by Glut on 2006-05-22
Unless you have hardware raid, you will want to use software raid level 5. Raid 5 will give you 99% of the performance of Raid 0 for most operations. Without the joy of having one drive failiure drop your entire system. 
The Ubuntu installer makes the configuration easy, setup identical partitions on each drive of the type 'software raid' and then select the software raid setup and go from there. 
From personal preference, I would create 2 smaller partitions one for boot and one for swap in RAID one with 1 active, 3 spare. No doubt someone will disagree, though.

---

