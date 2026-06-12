---
title: "Partitioning Problem"
date: 2010-07-13
forum: Server Platforms
---

### Post by LepeKaname on 2010-07-13
I'm trying to set a server with the following settings:

```
Mount [size] file_system
------------------------
/boot [1GB]  ext2
swap  [12GB] swap
/     [50GB] JFS
/var  [437GB] ReiserFS
```

All 4 partitions are primary and placed in that order in the disk.

The installation ends without any problem. But after rebooting it displays an error that it can't find the disk. 
I tried the same setup in VirtualBox and produces a serie of errors too after rebooting, in this case it shows:

> init: ureadahead main process (307) terminated with status 5
init: ureadahead-other main process (638 ) terminated with status 4
modprobe: FATAL : Error inserting padlock_sha (/lib/modules/..../padlock-sha.ko) No such device

At the very beginning I tried that configuration in a Raid1 setup but was displaying this error after rebooting:
> ALERT! /dev/disk/by-uuid/xxxxxxxx-xxxx-xxxx-xx$ does not exist

I tried to apply many of the suggestions but now I think it is not related to the RAID setup but for the partitioning (as my last try was on single disk without RAID), so I tried with the "normal" settings like this:

```
Mount [size] file_system
------------------------
swap  [10GB] swap
/     [490GB] ext4
```

and it worked without problems. 

Is there any restriction of where to put the /boot partition or the / partition in a disk?
Could it be possible that the order in which I add the partitions matters? it occurs to me that maybe /boot is not accessible as "/" is set later...
I don't think it is related to the File Systems... but I could be wrong.

**UPDATE 1:**

I tried setting the partitions in different order to rule out that possibility. This is what I tried:
```
Mount [size] file_system
------------------------
swap  [12GB] swap ##RAID1
/     [50GB] JFS ##RAID1
/boot [1GB]  ext2 ##RAID1
/var  [437GB] ReiserFS ##RAID1
```

Unfortunately I got the same "ALERT! /dev/disk/by-uuid" error... 

**UPDATE 2:**

Then I tried to make it simple:

```
Mount [size] file_system
------------------------
swap  [10GB] swap  ###RAID1
/     [490GB] ReiserFS ###RAID1

```

To my surprise I got this new error: 

> missing /sbin/init  Kernel Panic!

I entered from the recover option using the installation CD and /sbin/init was there. :S

**Update 3:**

Now I'm trying to change the file system from ReiserFS to ext4 to rule out that.
No luck... we can discard that.

---

### Post by LepeKaname on 2010-07-14
Somehow I solve the problem with this setup:

```
Mount [size] file_system
------------------------
/boot [1GB]  ext2 ##RAID1 
/     [50GB] ext4 ##RAID1
FREE  450GB
```

I didn't set swap (for now) and I disabled networking during the installation. I'm not sure what the problem was but at least it works.

I will customize the FREE space later.

---

### Post by LepeKaname on 2010-07-15
I tried to reinstalled again but this time I wanted to set LVM in the free space. However it seems that the only way it works is if it is FREE. I guess the problem might be related with the use of custom mount points (maybe?).

BTW. this time I tried with the network connected and it worked, so it was not necessary to disconnect it.

---

