---
title: "Create a raid from a single drive"
date: 2009-01-18
forum: Server Platforms
---

### Post by ElJefeRocks on 2009-01-18
Hello everybody,

(hopefully this is in a decent place, and if its not somebody will put it there)

I just started a new home media server build and got most of the hardware for it (AMD quad, 790GX mobo, 32gb SSD) and I was looking to get the other hard drives for it, 1.5tb, but the economy sucks so I can only get one.  Is it possible to use this drive and then expand the data from it onto a raid 5 using MDADM, including the 1 existing drive and not losing any data?  I'd probably move up to a 4 or 5 disk array when the time comes.  Is this possible to do or does the drive have to be in a raid array to begin with?

And I am planning on using 8.04 LTS server 64-bit

Thanks for your ideas/concerns

---

### Post by cariboo on 2009-01-18
You do realize that raid stands for redundant **array** of inexpensive disks. Check the array part. :) You can't create an array unless you have more disks. You can create a jbod (just a bunch of disks) array by adding more drives, but if you want to stripe or mirror, you're going to need at least 2 drives of the same size, and preferably the same manufacturer.

Jim

---

### Post by ElJefeRocks on 2009-01-20
Yes, I do understand what raid means, I was hoping with the new kernel and new implimentations to MDADM that it could be done.  I know that you can now 'add' and 'grow' to raid 5 (with great success, though it takes a little time), which I was hoping to use.

---

### Post by windependence on 2009-01-20
He can certainly do it, but I don't have any idea why except maybe because it's "cool"?

Yes, you can create a RAID array on one disk using different partitions but what would be the point? Disks are very cheap right now. I don't see them getting much cheaper to be honest.

-Tim

---

### Post by y@w on 2009-01-20
I think what he wants to do is build a RAID in a "degraded" mode to start with so it can be expanded without repartitioning, etc. later on when more disks can be afforded. I'm not quite sure how you'd pull that off.. It's definitely possible, but probably going to take more time than its worth. I would guess it is going to be easiest just to setup the RAID after you buy more disks.

---

### Post by fjgaude on 2009-01-20
Sure you can make a raid5 with two equal partitions of the same drive, and as you acquire more drives expand the array. But, it'll take effort to get past the size of the original partition. To start do this:

```
sudo mdadm --create /dev/md0 --level=5 --raid-devices=3 /dev/sd[n]1 /dev/sd[n]2 missing
```

Then make a filesystem for it, mount it, and you have it.

Study up on what it'll take to add more capacity:

[http://cobraftp.serveftp.com/pub/raid.pdf](http://cobraftp.serveftp.com/pub/raid.pdf)

Have fun!

---

