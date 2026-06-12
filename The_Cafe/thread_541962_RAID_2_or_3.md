---
title: "RAID 2 or 3"
date: 2007-09-03
forum: The Cafe
---

### Post by Arwen on 2007-09-03
Hello everyone!
I've recently read some stuff about RAID(my cousin wants to organise the hds in his work in RAID for safety) but we're both wondering 
what's the need of RAID2 which corrects only one error in a disc and it needs more discs to do it while RAID3 corrects errors in 1 bit by using only 1 parity disc.Is there any particular feature of RAID2 which makes it better than RAID3?

---

### Post by starcraft.man on 2007-09-03
> **Arwen said:**
> Hello everyone!
I've recently read some stuff about RAID(my cousin wants to organise the hds in his work in RAID for safety) but we're both wondering 
what's the need of RAID2 which corrects only one error in a disc and it needs more discs to do it while RAID3 corrects errors in 1 bit by using only 1 parity disc.Is there any particular feature of RAID2 which makes it better than RAID3?

I'd advise reading up more on the different levels of RAID. [Here]("http://en.wikipedia.org/wiki/RAID") and [here.]("http://en.wikipedia.org/wiki/Standard_RAID_levels#RAID_2") Then you should be able to decide for yourself. Lot's of people I know use RAID 5.

---

### Post by jpkotta on 2007-09-03
I believe levels 2 and 3 are legacy, and not really used at all.  You want just about any level besides 0.  You probably want level 5 (2 data + 1 parity, with parity and data scattered over all 3 disks).

---

### Post by Arwen on 2007-09-03
Thank you all for the links and advice,we now have to choose between RAID 1 and 5,but it's a decision that depends on cost and efficiency and it's not up to me to make now.I think 5 is the best solution,though it may be harder to setup than a RAID 1.
Thanks again :-)

---

### Post by beefcurry on 2007-09-03
I use Raid5, maybe more expensive and slower to set up then RAID1 but dispite having a lower write speed its got more storage avaliable with redundency percentage wise.

---

