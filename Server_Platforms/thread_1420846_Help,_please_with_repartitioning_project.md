---
title: "Help, please with repartitioning project"
date: 2010-03-03
forum: Server Platforms
---

### Post by Donny Bahama on 2010-03-03
I have an 8.04 server with a 1.5TB external drive. The drive came formatted as one big NTFS partition. I want to create a LVG with multiple LVMs (one each for backup, user1, user2, music, video, pictures and software.) These are the top-level directories used in the ntfs partition, and once the LVMs are created, I intend to move all the files from ntfs/dir to /lvg/lvm then delete the ntfs partition and create nfs and samba shares for each of the LVMs. Hope I made that clear...

Anyway, I ran ntfsresize (tested it first with -n which completed successfully) and everything went fine...
```
Successfully resized NTFS on device '/dev/sdb1'.
```

But then it said all of this (which confused the heck out of me!)...
```
You can go on to shrink the device for example with Linux fdisk.
IMPORTANT: When recreating the partition, make sure that you
  1)  create it at the same disk sector (use sector as the unit!)
  2)  create it with the same partition type (usually 7, HPFS/NTFS)
  3)  do not make it smaller than the new NTFS filesystem size
  4)  set the bootable flag for the partition if it existed before
Otherwise you won't be able to access NTFS or can't boot from the disk!
If you make a mistake and don't have a partition table backup then you
can recover the partition table by TestDisk or Parted's rescue mode.

```
Am I to understand that although the partition was resized, it's still taking up just as much of the drive (until I use fdisk to shrink it)? That makes no sense to me.

I read the man page for fdisk but I didn't see anything specifically related to shrinking - and I really don't want to screw this up.

Can someone please give me some guidance as to how to proceed?

---

### Post by samosamo on 2010-03-03
Why are you doing it the hard way?  You'll be sorry when you lose all your data.  I hope you have a backup.  Just copy the data over to another physical device.

---

### Post by Donny Bahama on 2010-03-04
> **samosamo said:**
> Why are you doing it the hard way?Because I'm a noob and I don't know any better?!> You'll be sorry when you lose all your data.  I hope you have a backup.  Just copy the data over to another physical device.You're right, I'll be very sorry if I lose all my data! But I don't have another physical drive that's large enough to hold everything on this drive, so I'd have to use more than one physical drive.

Unfortunately, while waiting for a reply on this thread, I did some digging and found a procedure for this. That procedure wanted me to delete the partition, then create a new one (using fdisk) with the same starting cylinder and the correct (resized) number of sectors. With great trepidation, I deleted the parttion, but when I went to create the new one, it won't let me. I enter the proper starting cylinder, but when I try to specify the size, it says the number needs to be between X and Y (where Y is too small for the resized data.)

---

### Post by KiLaHuRtZ on 2010-03-04
[http://www.newegg.com/Product/Product.aspx?Item=N82E16822148412](http://www.newegg.com/Product/Product.aspx?Item=N82E16822148412)

---

### Post by Donny Bahama on 2010-03-04
Gee, thanks. That would be really helpful if I had an extra $100 laying around.

---

