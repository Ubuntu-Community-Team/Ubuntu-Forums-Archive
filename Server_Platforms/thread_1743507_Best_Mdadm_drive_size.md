---
title: "Best Mdadm drive size?"
date: 2011-04-29
forum: Server Platforms
---

### Post by u-slayer on 2011-04-29
I want to make my new RAID-5 array future proof so that when I expand it in the future I can get drives at the the best $/TB ratio. 

Can I combine some of my smaller drives like this:

RAID 1: 1+1+1=3T
JBOD  : 2+1  =3T
Normal:    3 =3T

to make 3T units in a RAID-5 array? Or would there be a performance penalty for having layers of raid on top of each other like this. Would there be any drawback to going even bigger, such as 4T units?

---

### Post by rubylaser on 2011-04-30
If you want to do this the right way, you won't want to mix and match a bunch of different disk sizes, and aggregation on top of mdadm.  That could be a recipe for disaster.  To do this the right way that you're asking, what you're trying to do is RAID50.
[http://wiki.linuxquestions.org/wiki/RAID#RAID_50:_Striping_across_RAID_5_sets]("http://wiki.linuxquestions.org/wiki/RAID#RAID_50:_Striping_across_RAID_5_sets")

You'd need to create a new RAID5 array (wait for the parity calculation to complete), then add it to the md array to the RAID50 array stripe. You'd need 6 disks at a minimum to set this up. It would look something like this...

```
mdadm --create /dev/md1 -v --raid-devices=3 --level=5 /dev/sdb1 /dev/sdc1 /dev/sdd1 
mdadm --create /dev/md2 -v --raid-devices=3 --level=5 /dev/sde1 /dev/sdf1 /dev/sdg1 
mdadm --create /dev/md0 -v --raid-devices=2 --level=0 /dev/md1 /dev/md2
```

This would give you a RAID50.  In the future, if you wanted to expand, you'd need to add another 3 disks to grow the array. Here's what that would look like...
```
mdadm --create /dev/md3 -v --raid-devices=3 --level=5 /dev/sdh1 /dev/sdi1 /dev/sdj1
mdadm --manage /dev/md0 --add /dev/md3
mdadm --grow /dev/md0 --raid-devices=3
```
Then, you'll need to grow your filesystem to take advantage of the new space.  If you're not very comfortable with mdadm, I'd probably tell you to avoid this setup.


I've never tried RAID50 with mdadm, so I can't speak to performance penalties.  I can see where managing this could be tricky in the case of a disk failure.  What I would do is start with bigger disks than 1TB.  2TB disks seem to be the best value for the money right now, so if you started with 6 2TB disks in RAID6, you'd have 8TB of usable space, and be protected from 2 disk failures. You could do this with 3TB disks too if you want to. You'd just be paying more per gig of storage.

Just make sure if you purchase Advanced Format drives that you align the partitions on each drive to prevent a performance penalty.  Hope that helps.

---

### Post by u-slayer on 2011-04-30
Actually I'm trying to create a RAID 05 not a RAID 50.

That's a bunch of RAID 0 units tied together under a RAID5.

Is there anything wrong with that?

---

### Post by rubylaser on 2011-05-01
> Is there anything wrong with that?
RAID50 would provide more fault tolerance than RAID05.  This article explains the difference between the two in terms of fault tolerance.
[http://www.pcguide.com/ref/hdd/perf/raid/levels/multLevel05-c.html]("http://www.pcguide.com/ref/hdd/perf/raid/levels/multLevel05-c.html")

The other time is each time you wanted to add a new 3TB set, you'd need to recalculate parity for all of the disks in the array.  You might as well just do RAID6 and just the disks one at a time to grow the array.  It would be much more manageable and you'd only need to purchase 1 disk at a time.

---

