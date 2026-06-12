---
title: "URGENT : An Error occured while mounting"
date: 2016-01-01
forum: Server Platforms
---

### Post by soamz on 2016-01-01
Hi, I have a Dell Server 2950 and I have like 5x2TB disks in it, which is done as 6TB RAID0 and 4TB RAID0 to make it total 10TB space. 

I have 2 mount points mnt/disk1 and mnt/disk2. 

Just 15 minutes before, one of my website stopped opening. 
I restarted the server and it shows, "An error occured while trying to mount mnt/disk1"

I clicked on skip s and now the ubuntu server started, but that folder shows blank. 
I guess, its not mounted. 

What to do ?
How do I put it back ?

What went wrong ?


Output of cat /etc/fstab is this : 

> 

root@www:~# cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda1 during installation
UUID=73c8013f-f94c-4de6-92d2-9c574e11bb58 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=1ee0a798-8234-4d9f-b4a3-0ad95d8bc2e6 none            swap    sw              0       0
/dev/sdb1 /mnt/disk1 ext3 defaults 0 0
/dev/sdc1 /mnt/disk2 ext4 defaults 0 0
/dev/sdc2 /home ext4 defaults 0 0
root@www:~#


---

### Post by nerdtron on 2016-01-01
> **soamz said:**
> Hi, I have a Dell Server 2950 and I have like 5x2TB disks in it, which is done as **6TB RAID0** and **4TB RAID0** to make it total 10TB space. 



Urgent answer: Probably a failed hard drive. In RAID0, a single drive failure will cause the whole array to lose data. 

So why did you ever use a RAID0 configuration on a production server? I mean, shouldn't the minimum config like RAID5 or RAID10?

---

### Post by soamz on 2016-01-01
I remounted the disk and it worked. 

You mean, we should not use RAID0 ?
But I read RAID0 gives the best performance.

---

### Post by darkod on 2016-01-01
Is this HW raid using the Dell controller? In such case, are there any hdds with amber/warning lights? Go into the RAID config and check the arrays status.

We discussed the raid0 when you were setting up the server and we all told you not to use it. But you did it anyway... Now if a disk has failed and that array is gone, there is nothing more to do...

---

### Post by nerdtron on 2016-01-01
> **soamz said:**
> I remounted the disk and it worked. 

You mean, we should not use RAID0 ?
But I read RAID0 gives the best performance.

You should look into predictive failures on the Sever Management console (DRAC?) just to see if the drives are healthy. When a hard drive fails once, don't trust it again on with any critical data. 
Yes, RAID0 is fast but RAID0 doesn't offer any redundancy for hard drive failures. That's why RAID10 is invented - has the speed performance of RAID0 and the redundancy of RAID1. Only caveat is that storage capacity will be halved. But at least, better to have half capacity than **lose it all** (when one hard drive fails).

---

### Post by darkod on 2016-01-01
> But I read RAID0 gives the best performance.

No, it does not. And depending what you consider performance. Only the speed?

Open wikipedia and read more about varios raid levels (there are plenty of other pages on the same subject on the internet too). Raid0 is a specific type of array which splits the data among 2 or more disks, which in a way can offer better read/write speeds, but the BIG downside of raid0 is that splitting the data over varios disks makes you lose ALL data if only one disk fails. There is no redundancy with raid0.

This is a risk that you shouldn't accept even for a basic home server, let alone a serious production server. You should stay away from any setup that makes you lose all data after losing a single disk.

---

### Post by volkswagner on 2016-01-01
There are good reasons for using RAID0, but storage on a server is not one of them. Some people like to use RAID0 for a scratch disk when they
need high I/O performance, but don't want to sacrifice size.

For a server, if you want benefits of striping, but want redundancy and data integrity, take a look at RAID10. The sacrifice with RAID10 is reduced
total storage size. Just get larger disks to compensate ;)

PS: either way, RAID is not a backup solution. Whether you have RAID0, RAID5, RAID10, etc... you still NEED a backup solution in place.

---

