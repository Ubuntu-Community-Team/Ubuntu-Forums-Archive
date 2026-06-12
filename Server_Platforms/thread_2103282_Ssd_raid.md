---
title: "Ssd raid"
date: 2013-01-09
forum: Server Platforms
---

### Post by Vegan on 2013-01-09
how good is Linux on an SSD array, anybody had much experience with performance bottlenecks?

---

### Post by rubylaser on 2013-01-09
That's pretty vague, there are a bunch of questions to properly answer that. Here are a few:
1. What type of SSDs and number of drives? 
2. Hardware RAID (which controller) or software RAID(mdadm, ZFS, etc)? 
3. What raid level? 
4. Are they installed in a chassis with a backplane that supports SATA III?

---

### Post by spynappels on 2013-01-11
In researching SSDs for my laptop, I found there were massive differences in performance between different manufacturers, and even between different models from the same manufacturer. This makes a difference when using a single SSD, I presume it would also make a difference when you are combining them in an array.

---

### Post by Grenage on 2013-01-11
Does TRIM even work on Linux RAID arrays?

---

