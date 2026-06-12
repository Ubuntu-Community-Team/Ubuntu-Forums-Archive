---
title: "raid without partitioning drives"
date: 2012-01-24
forum: Server Platforms
---

### Post by southerngeek on 2012-01-24
Ok...I have a working server system with 10.10 on it. Had it running for several years now with no issues. I recently had one of my six 1TB drives fail in my raid 5 array. no biggie, just ordered a new one and popped it in, so far so good. I partitioned it as the other five were, with a raid autodetect partition. Went to add it in mdadm and got an error about the partition being too small (which it is...just by a few MB though) So I says forget this and just added the whole drive, sda, to the array. after rebuilding for a few hours everything seems to be back up and running like normal. My question is, will this make any difference at all, having the whole drive without a partition in the array? I have looked and looked all over the interwebs and have not really found a satisfactory answer. It seems to be working, just want to make sure I don't get any surprises down the road..

---

### Post by rubylaser on 2012-01-24
It won't cause a problem, other than showing up differently in fdisk -l.  The only situation that it could cause a problem is dependent on your mdadm version.  Metadata version 1.0 stores the superblock at the end of the device.  If you have varying sizes, that could potentially be a problem.  Metadata version 1.1 stores it at the beginning of the device and 1.2 stores it 4K from the start of the device.

I like to make my partitions a little smaller than the whole device to prevent situations like this where one manufacturer has a disk that's slightly smaller than another.

---

### Post by southerngeek on 2012-01-24
I did a mdadm -D and it said at the top version 00.90. Is that the metadata version?

---

### Post by rubylaser on 2012-01-24
Yes it is and that should be fine.

---

### Post by southerngeek on 2012-01-24
good deal. thanks a lot.

---

