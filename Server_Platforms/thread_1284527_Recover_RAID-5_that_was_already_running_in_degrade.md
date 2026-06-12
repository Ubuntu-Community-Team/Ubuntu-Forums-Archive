---
title: "Recover RAID-5 that was already running in degraded mode"
date: 2009-10-06
forum: Server Platforms
---

### Post by OfficeLinebacker on 2009-10-06
Hi guys, this is silly, this has happened before and I figured out how to fix it and it was fine.

I'm running 4 500GB SATA drives in a RAID-5 on 7.20 server.  One of the disks failed (actually I think it's one of the connectors in the hot-swap cage) and it's been running off of three disks while I find a replacement HDD or further diagnose the problem.

Now, before you read any further, NO I do not have backups and the information is not super important, just nice to have.  

Anyway once before, I had some kind of HW hiccup, maybe the power went out or something, and I had problems recovering the array.  It wasn't that one of the disks failed, it was something else.  

I was able to simply add back in the second "failed" disk and in a few minutes, I was back up and running.  Maybe I had to run some kind of filesystem check, I don't know.

I spent hours, if not days, figuring out how to do it last time and have since forgotten.

The crux of the issue is that if I run a mdadm --examine on sdb, sdc, and sdd, sdd thinks it's still part of the array but on the superblock info of sdb and sdc, it lists sdd as removed.

sda is the disk that failed long before, it's listed correctly in all of them as faulty removed.

TIA.  The server in question is not on the internet so it's not possible to C&P the output of various commands on to the forum.

I know, by now a lot of you probably think I'm a nitwit, or worse.  However I do recollect that once I figured out the series of commands to run, it was a fairly straightforward procedure and it worked great.

---

