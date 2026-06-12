---
title: "growing a raid-5 xfs"
date: 2010-10-14
forum: Server Platforms
---

### Post by morilibus on 2010-10-14
Hello,

New to forum, but have found many answers here.  Also fairly new to Ubuntu (under a year) so my knowledge and familiarity is fairy low(pretty much google everything i need to do)

I built a Ubuntu 9.10 computer to house a bunch of hard drives(3 at the time in raid-5) to use as a media server.
I have a seperate hard drive for the os, so the Raid-5 array is just for the media.

I used mdadm, and I followed a tutorial I had found when building the array( and for some reason didn't bookmark) and had successfully set up the raid-5 running xfs with 3 devices.

Now my drives are getting full and I bought a new drive and have added it to the array and its finally synced up, but I'm not sure how to go about growing the filesystem.  I don't remember using LVM and i'm pretty sure i didn't as its not installed (pretty good theory eh?)  

So I'm not sure what my plan was in expanding( and I thought I had one) I currently don't have this data backed up anywhere but trying to find some good esata externals to backup in case I messed up and have to wipe the whole thing. (any recommendations? locally available in Canada preferred)

Is there a way to grow the xfs file system without loosing data?

If you need any additional info let me know( along with terminal commands to provide said information :) )

Thanks

in the mean time I shall continue to google for that original tutorial I used in hopes of determining how I set this up.

(edit) here's fdisk -l

> Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0000f29c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        6079    48829536   83  Linux
/dev/sda2            6080       30394   195310237+  83  Linux
/dev/sda3           30395       31123     5855692+  82  Linux swap / Solaris

Disk /dev/sdc: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000ae9f1

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1      121601   976760001   83  Linux

Disk /dev/sde: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xb37a5648

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1               1      121601   976760001   fd  Linux raid autodetect

Disk /dev/sdd: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00047b1b

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1      121601   976760001   83  Linux

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00011468

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1      121601   976760001   83  Linux

Disk /dev/md0: 3000.6 GB, 3000606523392 bytes
2 heads, 4 sectors/track, 732569952 cylinders
Units = cylinders of 8 * 512 = 4096 bytes
Disk identifier: 0x00000000

Disk /dev/md0 doesn't contain a valid partition tableok so I'm thinking I need to us xfs_growfs

and using the man pages I think I understand what I need to do.

for example my /dev/md0 is mounted to /media/storage

so I think all I need to do is:

$ xfs_growfs /media/storage

and it will start growing the filesystem.  I'd just like to be sure before I go ahead and that I'm not going to loose my data.  or I can wait till I get some external backup setup. 

on a side note: Any recommendations on how to backup 2TB + of data.  Was planning on getting a couple 2tb esata externals but not sure how to set that up mirror the content on the raid array.  This data won't be accessed just stored, not sure how to handle spreading data across 2 mediums, other then manually doing it.  

Thx

---

