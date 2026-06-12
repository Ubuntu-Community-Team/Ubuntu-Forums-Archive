---
title: "Setting up RAID"
date: 2009-11-04
forum: Server Platforms
---

### Post by infecticide on 2009-11-04
I have a question I think I know the answer to ;P

Is it possible to build a RAID 1 across 2 drives without reinstalling the OS or restoring from backup?

I have a backup but if its possible to do without, that would be nice :)

---

### Post by buntunoob on 2009-11-05
This would be nice to know, I have a date this weekend redooing the server if not.

---

### Post by Lars Noodén on 2009-11-05
You'd have to juggle the partitions to get the two empty partitions needed for RAID 1, one on each disk.  They will be erased on the way to getting them ready for set up with mdadm

Look around for tips on re-partitioning.

Back up first.

---

