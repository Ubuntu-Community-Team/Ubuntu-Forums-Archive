---
title: "Software RAID 5"
date: 2007-12-10
forum: Server Platforms
---

### Post by defaulk on 2007-12-10
I'm thinking of setting up a RAID 5.  If I do this, I want to be able to upgrade the drive space.

For example, suppose I have a 250GB, a 400 GB and a 500GB drive in a raid-5.  That would give me (3 - 1) * 250 = 500GB of storage.

What if I then want to replace that 250GB with a 750GB.  Would I be able to have the raid somehow rebuilt to be (3-1) * 400 = 800GB, since the 400GB drive would now be the smallest drive?

---

### Post by insane_alien on 2007-12-10
if you use lvm maybe. its also a bit of a waste to be using three different sized drives. you're losing 400GB worth of drive right there. buy a couple of 500GB drives and take a terayte of storage.

---

### Post by doogy2004 on 2007-12-10
here is a calculator for different size drives: [http://www.z-a-recovery.com/art-raid-estimator.htm](http://www.z-a-recovery.com/art-raid-estimator.htm)

here are instructions and a how-to: [http://www.gagme.com/greg/linux/raid-lvm.php](http://www.gagme.com/greg/linux/raid-lvm.php)

---

### Post by rsw686 on 2007-12-12
This is possible to do with LVM on top of RAID. Take a look at the ReadyNAS device. It does exactly what you are talking about behind the scenes. Although starting out with 3 different drive sizes isn't ideal as you can only use the size of the smallest drive.

I recommend you purchase 2 drives of the size you want to go with and set them up in RAID 1. You can then add a 3rd drive and migrate from RAID 1 to RAID 5 without loosing data. None of this requires LVM, just knowledge of mdadm and resize2fs.

If you are set on starting out with your 250GB RAID 5 you would create the array and setup LVM ontop. Once you bought your new 750GB drives you would need to swap out the drives one by one using mdam to reconstruct the array. This is time consuming. Once you swap in the last 750GB drive you would create a new RAID 5 array using the 500GB of free space on each drive. Then you add this to the LVM volume group with pvcreate. Now you can extend your existing logical volume and resize the filesystem.

---

### Post by sciurus on 2007-12-12
[http://www.gagme.com/greg/linux/raid-lvm.php](http://www.gagme.com/greg/linux/raid-lvm.php)
[http://scotgate.org/?p=107](http://scotgate.org/?p=107)

---

