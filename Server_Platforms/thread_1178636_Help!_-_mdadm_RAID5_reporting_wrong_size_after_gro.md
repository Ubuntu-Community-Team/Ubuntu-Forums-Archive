---
title: "Help! - mdadm RAID5 reporting wrong size after grow"
date: 2009-06-04
forum: Server Platforms
---

### Post by plonka2000 on 2009-06-04
Hi all,

I seem to be having an oddity with my software mdadm RAID5 which I seem unable to work out.

I gre my array following the instructions on [this page]("http://scotgate.org/2006/07/03/growing-a-raid5-array-mdadm/") (which I did once before and worked without a hitch) from 6 drive to 7 drive RAID5 on XFS.

```
mdadm --add /dev/md0 /dev/sdi1
mdadm --grow /dev/md0 --raid-devices=7

xfs_growfs /dev/md0
```

All seemed to go fine until I relised after the entire process that I gre it onto the wrong drive. basically, my RAID5 is made up of 500GB drives and I grew it onto a 1TB drive which I had spare and plugged in as a live backup (Had nothing on it at the time).

No problem I thought, I'll mark the drive faulty and just 'add' the intended drive as the replacement which will then rebuild onto it... Which it did, andit seemewd to work. I got some advice from [this page]("http://g4u0419c.houston.hp.com/en/5991-7402/ch21s04.html") on how to do so.

The problem I have now is my RAID array is not registering properly as over 3TB, even though it appears to have grown the XFS File System just fine.

Does anyone have any idea how I can investigate this?
I have grown this array twice before from 5 to 5 drives then 5 to 6 drives without a hitch.

Anyone?

---

### Post by plonka2000 on 2009-06-05
Can anyone provide any help?
I am not sure what to do...

Even my Windows workstation reports the SMB share as 2.72GB when it should be well over 3GB.

Here is the output of my mdadm -D /dev/md0:

```
root@soundwave:~# mdadm -D /dev/md0
/dev/md0:
        Version : 00.90.03
  Creation Time : Sat Sep 27 17:03:40 2008
     Raid Level : raid5
     Array Size : 2930303616 (2794.56 GiB 3000.63 GB)
  Used Dev Size : 488383936 (465.76 GiB 500.11 GB)
   Raid Devices : 7
  Total Devices : 7
Preferred Minor : 0
    Persistence : Superblock is persistent

    Update Time : Fri Jun  5 09:34:33 2009
          State : clean
 Active Devices : 7
Working Devices : 7
 Failed Devices : 0
  Spare Devices : 0

         Layout : left-symmetric
     Chunk Size : 64K

           UUID : ee5127e0:277cbf0f:c81a20e0:547e7663
         Events : 0.974550

    Number   Major   Minor   RaidDevice State
       0       8        1        0      active sync   /dev/sda1
       1       8       17        1      active sync   /dev/sdb1
       2       8       33        2      active sync   /dev/sdc1
       3       8       49        3      active sync   /dev/sdd1
       4       8       65        4      active sync   /dev/sde1
       5       8       81        5      active sync   /dev/sdf1
       6       8      113        6      active sync   /dev/sdh1

```

Can anyone help?

---

### Post by fjgaude on 2009-06-06
I don't know but 465 GiB times six equals 2.79GB... you are not off that much. You think you are missing a drive size?

---

### Post by plonka2000 on 2009-06-08
> **fjgaude said:**
> I don't know but 465 GiB times six equals 2.79GB... you are not off that much. You think you are missing a drive size?

Actually, I have the feeling that I fixed it just before I posted this. I was getting strange sizes and now its reporting as normal.

According to my calculations, SEVEN 500GB drives should add up to 3.5GB minus parity (Parity is 1 drive capacity in RAID5 = 500GB in this instance) is 3GB but formatted is 2.79.

At one point it even registered as 2.56GB if I remember correctly.

Problem was it wasnt showing that before... And I was getting very worried about it. I've since been checking and rechecking it and it seems to be working. It just unfortunate that I created this thread after I apparently fixed it...

---

### Post by wheniwork on 2010-06-12
plonka2000, so how did you fix it? 

I'm having a similar problem. I grew my raid device and mdadm reports the size correctly, but df reports it wrong. See this post where I put my output.

[http://ubuntuforums.org/showthread.php?p=9450233#post9450233](http://ubuntuforums.org/showthread.php?p=9450233#post9450233)

Any ideas on why the size reporting is funky? Also, the device icon on the GDM desktop reprots the size right, but I don't think it's recognizing the usable free space right.

---

### Post by Xianath on 2010-06-12
You;re getting your units mixed up. Drive sizes are reported by vendors in Gigabytes (10^9 bytes) but you're typically looking at them in Gibibytes (2^30, or 1073741824, bytes). A "500G" disk is (about) 500 000 000 bytes = 0.465661287 GiB. Six times that is 2.79396772 GiB, which is exactly what you're seeing.

The difference between decimal/metric (powers of 10) and binary (powers of 2) adds up with drive size. A 1TB disk is actually 921GiB, or 8% less than you'd expect. 12 disks 1TB each in RAID6 add up to 9.21TiB, or 800GiB less than 10TB. That's almost the size of another disk! Just make sure you don't mix apples and oranges and you'll be fine.

---

### Post by wheniwork on 2010-06-12
Take a closer look at my setup. I have 7 1TB drives in the array.  Running df says the raid5 device is less than 4 TB. That's not right.

---

### Post by Xianath on 2010-06-12
Your original post mentioned 500G disks. mdadm -D shows this:

 Active Devices : 7
 Raid Level : raid5
 Array Size : 2930303616 (2794.56 GiB 3000.63 GB)

RAID5 with 7 500GB disks means 6 times 500GB = 3TB or 3000GB
3000GB * (10^9 / 2^30) = 2794GiB

It still looks right to me.

---

### Post by wheniwork on 2010-06-12
But I have 7 1TB drives, not 500GB. The issue is that "df" says the size of the raid device is the same as it was before I added 2 more TB drives. So something is not right.

```

root@kiwi:~# df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/mapper/system_mirror-ubuntu_system
                      391G  5.8G  385G   2% /
tmpfs                 2.0G     0  2.0G   0% /lib/init/rw
varrun                2.0G  372K  2.0G   1% /var/run
varlock               2.0G     0  2.0G   0% /var/lock
udev                  2.0G  3.0M  2.0G   1% /dev
tmpfs                 2.0G  104K  2.0G   1% /dev/shm
lrm                   2.0G  2.2M  2.0G   1% /lib/modules/2.6.27-17-server/volatile
/dev/md1              3.7T  2.5T  1.2T  69% /media/storage

```


```
root@kiwi:~# mdadm -D /dev/md1
/dev/md1:
        Version : 00.90
  Creation Time : Thu Mar 26 20:02:07 2009
     Raid Level : raid5
     Array Size : 5860559616 (5589.07 GiB 6001.21 GB)
  Used Dev Size : 976759936 (931.51 GiB 1000.20 GB)
   Raid Devices : 7
  Total Devices : 8
Preferred Minor : 1
    Persistence : Superblock is persistent

    Update Time : Sat Jun 12 18:17:05 2010
          State : clean
 Active Devices : 7
Working Devices : 8
 Failed Devices : 0
  Spare Devices : 1

         Layout : left-symmetric
     Chunk Size : 64K

           UUID : 93ae091b:b4aa0eb1:8e7c4951:0f0ba6be
         Events : 0.1324996

    Number   Major   Minor   RaidDevice State
       0       8       65        0      active sync   /dev/sde1
       1       8       81        1      active sync   /dev/sdf1
       2       8       97        2      active sync   /dev/sdg1
       3       8      113        3      active sync   /dev/sdh1
       4       8      129        4      active sync   /dev/sdi1
       5       8      145        5      active sync   /dev/sdj1
       6       8       33        6      active sync   /dev/sdc1

       7       8       49        -      spare   /dev/sdd1

```


See these to values comparing df and mdadm

```
/dev/md1              3.7T  2.5T  1.2T  69% /media/storage
```

```
     Array Size : 5860559616 (5589.07 GiB 6001.21 GB)
```

---

### Post by Xianath on 2010-06-13
This array looks very different from the one you showed before! This one has 8 disks, 7 active 1 spare, 1TB each. The previous one had 7 disks, all active, 500GB each. df output looked right before, now it doesn't. With all this contradictory information I can only conclude that you did xfs_growfs *before* you got your array straightened up. All you need to do now is xfs_growfs again.

---

### Post by wheniwork on 2010-06-13
I'll take a look at xfs_growfs, but I think you're getting me mixed up with someone else earlier in this thread. I've never had 500GB drives in my array.

I jumped onto this thread after plonka2000 fixed his 500GB array issue.

---

### Post by Xianath on 2010-06-13
D'oh! Different folks! Shoulda figured that out myself. I usually pay attention to STDOUT, not people :)

Anyway, **your** array seems fine to me, you just need to grow the FS. It takes just a few seconds, and xfs_growfs needs the filesystem to be mounted so it's an online operation, no downtime.

---

### Post by wheniwork on 2010-06-13
np. Ok cool so I just need to run this command?

xfs_growfs

Any arguments or parameter need to go with that?

---

### Post by wheniwork on 2010-06-13
> **wheniwork said:**
> np. Ok cool so I just need to run this command?

xfs_growfs

Any arguments or parameter need to go with that?

I don't think I have xfs_growfs installed. Once its installed I just run it then? I've never used it.

---

### Post by Xianath on 2010-06-15
Your RAID array needs to be mounted for xfs_growfs to work. Then just run it on the mount point, such as:

sudo xfs_growfs /mnt/data

xfs_growfs comes in the xfsprogs package so you'll need to install that first.

---

### Post by wheniwork on 2010-06-23
I'm getting this when trying to run that.

```
xfs_growfs: /media/storage is not a mounted XFS filesystem

```

Is this XFS thing the thing to use for mdadm raid arrays?

---

### Post by Xianath on 2010-06-25
xfs_growfs grows an XFS filesystem. Not an array, not a partition, and not a logical volume -- these are all block devices. xfs_growfs works on the actual filesystem contained within whatever block device you're using. It (the FS) needs to be mounted in order to be grown. So, just mount it under /media/storage and run xfs_growfs on it. Of course it needs to have been formatted with XFS in the first place :)

---

### Post by critter.be on 2010-06-25
What filetype is on your RAID volume? ext[234], xfs, something else?

resize ext[234] fs: resize2fs <device>
resize xfs: xfs_growfs <device>

---

### Post by wheniwork on 2010-06-27
My RAID5 array is a resizerfs

---

### Post by wheniwork on 2010-07-03
Since my raid device is resizerfs how do I make the OS recognize the added size I've done to the array? It doesn't seem that the xfs_growfs thing will work, right?

Check out my post 9 to see what I mean how the size of the array is conflicting when comparing the array size and what the OS sees.

[http://ubuntuforums.org/showpost.php?p=9452111&postcount=9](http://ubuntuforums.org/showpost.php?p=9452111&postcount=9)

---

### Post by wheniwork on 2010-08-01
> **wheniwork said:**
> Since my raid device is resizerfs how do I make the OS recognize the added size I've done to the array? It doesn't seem that the xfs_growfs thing will work, right?

Check out my post 9 to see what I mean how the size of the array is conflicting when comparing the array size and what the OS sees.

[http://ubuntuforums.org/showpost.php?p=9452111&postcount=9](http://ubuntuforums.org/showpost.php?p=9452111&postcount=9)

*Bump* :)

---

### Post by rubylaser on 2010-08-02
You need to run
```
resize_reiserfs
```

With your RAID array unmounted
```
sudo umount /media/storage
```

Resize
```
sudo resize_reiserfs /dev/md1
```

Remount your mdadm array
```
sudo mount -a
```
Hope that helps.

---

### Post by wheniwork on 2010-08-06
I get this when trying to resize

```
root@kiwi:~# sudo resize_reiserfs /dev/md1
resize_reiserfs 3.6.21 (2009 www.namesys.com)



resize_reiserfs: run reiserfsck --check first

```

---

### Post by wheniwork on 2010-09-16
Any ideas? See my output above. Thanks!

---

### Post by schworak on 2012-08-29
I know it has been a while since this thread has seen any action. I am  only posting because this keeps coming up high in my Google searches and  I found a simple solution.

I resized my RAID6 array by adding three new drives but DF kept showing the old size.

After some research I found that I simply needed to tell the OS to  resize the partition to its maximum size. It took a while but it did it  LIVE without unmounting the array and no data loss. As a matter of fact I  was even able to write to the disk while it was being resized. I  wouldn't try rebooting because that sounds down right dangerous.

It took about 3 hours (+/-) to expand my array from 3T to 6T using this command:

```
sudo resize2fs /dev/md9
```By not specifying the size you are resizing to, the entire available space is used which is exactly what I wanted.

[CENTER][EANdata.com]("http://eandata.com") | [Schworak.com]("http://schworak.com") | [ArtFromTheTribe.com]("http://artfromthetribe.com")[/CENTER]

---

### Post by rubylaser on 2012-08-29
> **schworak said:**
> I know it has been a while since this thread has seen any action. I am  only posting because this keeps coming up high in my Google searches and  I found a simple solution.

I resized my RAID6 array by adding three new drives but DF kept showing the old size.

After some research I found that I simply needed to tell the OS to  resize the partition to its maximum size. It took a while but it did it  LIVE without unmounting the array and no data loss. As a matter of fact I  was even able to write to the disk while it was being resized. I  wouldn't try rebooting because that sounds down right dangerous.

It took about 3 hours (+/-) to expand my array from 3T to 6T using this command:

```
sudo resize2fs /dev/md9
```By not specifying the size you are resizing to, the entire available space is used which is exactly what I wanted.

[CENTER][EANdata.com]("http://eandata.com") | [Schworak.com]("http://schworak.com") | [ArtFromTheTribe.com]("http://artfromthetribe.com")[/CENTER]

That works well, but is for ext2/3/4, and will not work resizerfs as was asked.  

Also, it really is a much better practice to umount your array, run an fsck on it, and then resize so you can reduce the risk of corruption.

---

