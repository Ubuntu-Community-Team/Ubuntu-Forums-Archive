---
title: "[SOLVED] WD5000AAKS Raid Drive Replacement"
date: 2008-12-05
forum: Server Platforms
---

### Post by littlegreiger on 2008-12-05
I currently have a RAID 5 setup with mdadm on ubuntu server 7.10 with one failed drive, a western digital WD5000AAKS and I'm wondering if I can replace it with a seagate ST3500320AS, they're both 500gb and their sites both say they have the same number of sectors but I'm not sure if it's going to work or if it's just going to cause me problems. 
The only reason I ask is because it's becoming harder to find the WD5000AAKS because it is an older drive now and the new seagate drive is also cheaper. 

FYI, this is just a home server, not mission critical or anything.

Anyone have any ideas?

---

### Post by hyper_ch on 2008-12-05
should be fine to do so...

---

### Post by CrucifiedEgo on 2008-12-05
In software raid, i don't believe it makes much of a difference.  Even in newer hardware raid, i've seen it handle different drives well (though i've heard you get higher performance with identical drives, i can't source or verify that).  In your case, there's no reason that wouldn't work.

---

### Post by littlegreiger on 2008-12-05
Thanks for the quick replies, I'm gonna order the seagate drive and see how things go

---

