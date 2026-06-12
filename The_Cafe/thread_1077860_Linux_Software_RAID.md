---
title: "Linux Software RAID?"
date: 2009-02-22
forum: The Cafe
---

### Post by kevin11951 on 2009-02-22
If i am running a RAID 5 setup with three 250GB discs, and one dies while the server is running, and i take out the drive and replace it, again while the server is on, will it start to copy the files back and go on with its life like nothing happened?  just trying to understand how software raid works.

---

### Post by Biochem on 2009-02-22
I never had to do it yet (crossing fingers and toes).

But, I think you have to mark the new drive as a spare. Then it will automatically be pickup and used to fix the array.

---

### Post by kevin11951 on 2009-02-22
> **Biochem said:**
> I never had to do it yet (crossing fingers and toes).

But, I think you have to mark the new drive as a spare. Then it will automatically be pickup and used to fix the array.

how do you mark the drive as a "spare"?

---

### Post by Biochem on 2009-03-02
I usually use evms in ncurse of gui mode for that kind of things.
But be careful there is a bug in evms that prevent booting in some configuration. I always remove it after use

---

### Post by ssam on 2009-03-02
[http://linux-raid.osdl.org/index.php/Reconstruction](http://linux-raid.osdl.org/index.php/Reconstruction)

you need to tell mdadm that the new disk is the replacement. also you may need to shutdown (unless you have hot swappable hardware).

there are some people who think raid 5 is a bad thing, as it can't recover from 2 failed drives. as you put more drives in a raid5 array you raise the risk of having multiple failures at once. also as disks get bigger the rebuild time gets longer, and the window for a second failure gets bigger.
[http://www.baarf.com/](http://www.baarf.com/)
[http://blogs.zdnet.com/storage/?p=162](http://blogs.zdnet.com/storage/?p=162)

---

