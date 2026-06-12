---
title: "Truecrypt taking forever!!!"
date: 2012-07-07
forum: Security
---

### Post by Tetrohedron on 2012-07-07
Problem solved.

The problem:  I tried several times over a period of several days to create a 20 gig truecrypt volume.  The volume was taking an absurdly long period of time to create.  I tried making smaller volumes that were only a few gigabytes big.  Truecrypt would originally estimate 30 minutes but as it encrypted the volume it would process less and less data per minute until the 30 minute prediction turned into hours.

Solution:  I increased my partition size.

Explanation: When I first became frustrated with truecrypt I had a 100 gigabyte partition for Ubuntu.  On that partition I did install a 20 gig truecrypt volume but it took me nearly 24 hours to do it.  Recently, I reformatted my hard drive and this time around, as you can see from subsequent posts, I partitioned 320 gigabytes for Ubuntu.  Having done that I tried truecrypt again several times and appeared to encounter the same problem.  After several days I posted here to see if I could find a solution that didn't require me quarantining my computer for a day.  After posting I decided I would just let truecrypt run and give up my computer for a day but it turned out that despite predicting an ever increasingly distant ETA at the beginning of the encrypting, the speed picked up again and it worked.  The problem, I think, was that I didn't give tc enough time and I perceived the problem to still exist when in fact if  I would have allowed the encrypting to continue it would have become apparent that increasing the partition size had worked.

---

### Post by tubbygweilo on 2012-07-08
Can you let us know the specifications of your machine and the size of containers you wish to create? It all has an impact on the speed of creation but I would not have thought it would be a tardy as you suggest.

PS What version of Ubuntu and what version of Truecrypt?

---

### Post by Tetrohedron on 2012-07-08
Sure.  I am running a windows 7 /linux dual boot.  I have a 100 gig hard drive.  I partitioned 320 gigs for Ubuntu.  Of that, 27.5 gigs are used.  I would like to create a 20 gig volume.

Free -m returned

                     total       used       free     shared    buffers     cached
Mem:          8068       1328       6739          0           148           728
-/+ buffers/cache:     451       7616
Swap:         8182             0        8182

---

### Post by Tetrohedron on 2012-07-09
> **tubbygweilo said:**
> Can you let us know the specifications of your machine and the size of containers you wish to create? It all has an impact on the speed of creation but I would not have thought it would be a tardy as you suggest.

PS What version of Ubuntu and what version of Truecrypt?


problem solved.

---

### Post by tubbygweilo on 2012-07-09
Tetrohedron, so glad you fixed the problem and marked it solved.

Any chance of restating the problem and your solution so that others may learn from your work?

---

