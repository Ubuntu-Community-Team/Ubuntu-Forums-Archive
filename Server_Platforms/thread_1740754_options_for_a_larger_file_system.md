---
title: "options for a larger file system"
date: 2011-04-27
forum: Server Platforms
---

### Post by Vegan on 2011-04-27
I have considered a range of choices, but at the end of the day the choice I make can quite easily put into a situation that requires even more thinking.

The idea is to have an enormous file system for SAMBA that can scale from terabytes to petabytes. Such as a single directory with say 4 million MP3s in my iTunes collection. iTunes cannot use multiple drives easily.

There are lots of vendors that have offerings galore, I wanted to see what can be done with a roll your own approach.

---

### Post by arrrghhh on 2011-04-27
I've seen a lot of options.  Some seem more viable than others.

There's always LVM - which seems to be the most stable offering.

I've heard of some others - creating pools similar to how WHS used to be.  I will need to do some research to dig those up...

Edit - Ah, just found an article that has almost all the ones I've heard of before.

[How-to Geek Article](http://www.howtogeek.com/howto/36458/9-alternatives-for-windows-home-servers-drive-extender/)

Enjoy!

---

### Post by Usa_Tony_Cuba on 2011-04-27
> **arrrghhh said:**
> ...There's always LVM - which seems to be the most stable offering....

+1 .. LVM will do it

---

### Post by dtfinch on 2011-04-27
When you say 4 million files in a directory, do you mean directly in the directory or divided into many subdirectories?

We have a couple million files on ext4 on lvm on md raid 1. But no very large folders. The largest I'm aware of is we have some with around 36k files each.

The kernel wiki says ext4 supports unlimited files in a directory now, while ext3 supported 32k, but wikipedia says ext4 needs the dir_nlink option to go past 64k.

As for Samba, it can slow down doing case-insensitive lookups in very large directories when serving from a case-sensitive filesystem, because if it can't find an exact match it has to check every file in the directory, though it does cache results. XFS supports case insensitivity, if you [specify it at creation](http://manpages.ubuntu.com/manpages/lucid/man8/mkfs.xfs.8.html).

---

### Post by Usa_Tony_Cuba on 2011-04-27
> **dtfinch said:**
> We have a couple million files on ext4 on lvm on md raid 1. But no very large folders. The largest I'm aware of is we have some with around 36k files each.[InstallationRAID1+LVM]("https://help.ubuntu.com/community/Installation/RAID1%2BLVM") *..."No program "pvcreate" found for your current version of LVM". Thankfully, someone over on the Ubuntu forums worked out how to fix it* =D>

> That's the RAID 1 bit of the setup taken care of - so this is the point at which we get LVM to create a nice big partition out of the first two disks. But there's a problem - the pvcreate command is a little broken. We need to run the command:


```
pvcreate /dev/md0 /dev/md1
```

But running that gives the following error: "No program "pvcreate" found for your current version of LVM". Thankfully, someone over on the Ubuntu forums worked out how to fix it. It's quite simple, too. Run this:
```
cp -r /lib/lvm-200/ /lib/lvm-0
```
Now run pvcreate again:
```
pvcreate /dev/md0 /dev/md1
```
Success! On to the next step.


```
vgcreate datavg /dev/md0 /dev/md1
```
You can call "datavg" anything you want - it's just a name for the "volume group". "datavg" is what I used - simple and descriptive. Onwards:


```
lvcreate --name datalv --size 931.51G datavg
```
Again, "datalv" (notice the difference to the above name) can be whatever you like, but this is fine for me. If you didn't use "datavg" as the name in the previous line, make sure you replace the "datavg" in this line with whatever you used. The value given after "--size" is the total size of the new partition - the sum of the combined partitions. My two 500 GB (465 GiB) drives make 1 TB (931 GiB), so that's how much I put.

Assuming that all went well (you can check with the lvdisplay command), you'll now have a large partition with no usuable (to you) format. Time to change that. I'm going to be using Ext3, but you can use Ext2, ReiserFS, or whatever you want.


```
mkfs.ext3 -m 0 -T largefile /dev/datavg/datalv
```
The "-m 0" tells it to reserve zero percent of the disk for the super user (root). If I didn't set that and used the default value, it would eat 60 GiB of my partition! If the system were going to be using it for the OS, then leaving some for root would be important (possibly) - but this is to be a pure data drive, so we don't need it.

"-T largefile" is used because the files created for my recordings are large wave files, so using this is better than using a system optimized for small files. If you're going to use your system for small files (pictures, text files, etc), you can omit this option.

Creating the file system may take a while - it took few minutes on my system. Once it's done, you'll have a nice large Ext3 (or whatever format you chose) partition ready to be mounted. Let's give it a spin. Create a mount point then mount it:


```
mkdir /mnt/data
mount /dev/mapper/datavg-datalv /mnt/data/
chmod 777 /mnt/data/
```
Notice the device used. If you didn't use the names "datavg" and "datalv" as per the above examples, your device will be named differently. It should be trivial to work out. 

Do a "df -h" and look on with a smile:


```
/dev/mapper/datavg-datalv 932G 200M 932G 1% /mnt/data
```
That's it! You now have the first two disks working under LVM - as if they were using RAID 0 - and they're mirrored with RAID 1. Easy, wasn't it? 
How many drives/disk-size you want to go for..? ... I have not tried, but in my opinion, even on Ubuntu Server 10.10, should be almost the same process ...IMHO

---

### Post by Vegan on 2011-04-28
I am looking at maybe 16x 4TB disks using a RAID6 controller. Maybe 10x such machines or so.

---

