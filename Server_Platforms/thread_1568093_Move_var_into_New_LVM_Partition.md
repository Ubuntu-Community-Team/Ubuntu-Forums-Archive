---
title: "Move var into New LVM Partition"
date: 2010-09-04
forum: Server Platforms
---

### Post by RS_Brooks on 2010-09-04
During install of Ubuntu 10.04 I did an auto partitioning using LVM. I ended up with a boot and logical group containing root and a swap volume. I decided I wanted to split off tmp, var, and usr into their own partitions. I created a couple of new logical volumes, booted off a live CD to prepare moving data...and BRAIN FREEZE. At this point, I'm slightly lost as I'm not real keen on LVM yet. Nor have I had much experience moving around mount points. I stumbled upon the rsync command, which seems to simplify many of the things I had originally intended to step through. I was slightly concerned I might be missing a few other key points. Can anyone give me a hand with a documentation or walk through url of this process? Would be greatly appreciated!

---

### Post by RS_Brooks on 2010-09-04
Hmm, can't decide if my questions on here are extremely stupid or if the Ubuntu forums just aren't crazy hopping on a three day weekend. :P Anyways, if someone stumbles across my tags looking for the same answers...
 
[https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)
 
That post is fairly straight forward, hits on the rsync vs other copy methods, and appears to be fairly up to date.

---

