---
title: "Dell Perc 6/i"
date: 2008-04-03
forum: Server Platforms
---

### Post by broth420 on 2008-04-03
I am having trouble creating my partitions on a Dell PE2900 using the Perc 6/i RAID controller.  I have 8 750GB drives running RAID5.  I am trying to make 4 partitions
8GB swap
64GB / (ext3)
16GB Var (ext3)
and I would like to use the rest of the space for one large partition (XFS).  
Each time I create the last partition using all space, it gets downsized to 708GB (leaving exactly 4TB unusable).
What am I missing?  I left a post on something similar to this, but no answers.
Can anyone direct me to instructions fo dealing with large partitions if there are any tricks?  Is this a hardware problem, a bug?  I am running out of ideas.  Most of what I find is old, and isn't dealing with the size I am.  I also tried to create the partitions with Gparted .3.4.11 and had the same problem.

---

