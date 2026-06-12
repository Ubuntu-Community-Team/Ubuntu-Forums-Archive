---
title: "LVM snapshots"
date: 2008-12-13
forum: Server Platforms
---

### Post by rkleemann on 2008-12-13
Hi, I'm running Ubuntu Server 8.04.

I have multiple filesystems under LVM-over-raid.

I've started playing around with snapshots, and so far no problem.

My question is, does LVM2 have a limit on the number of snapshots kept around?

I was hoping to be able to keep one week's worth of snapshots around, in a circular manner. Each night I take a snapshot and basically keep it for 7 days. Essentially that means 7 snapshots for one filesystem.

Is it way too much overhead to do that? Specially if I do it for 2 or 3 filesystems?

Will data get corrupted?

---

