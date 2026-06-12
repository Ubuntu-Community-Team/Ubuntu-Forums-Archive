---
title: "storage/media server"
date: 2011-07-22
forum: Server Platforms
---

### Post by parisv on 2011-07-22
I'm going to build an ubuntu 11.04 server. It's the first time I've set one up so don't have much experience. 

At the mo I'm testing it in a vm. It has 1 virtual disk for os and 4 virtual disks for software raid

I want it to be able to store data/video/music  on 3+ hdd's and if one disk goes for it to be safe because of having a spare (4th) disk

But I want it to work a bit like windows drive extender where you can add any size drive to data disks.

Also I want windows and osx clients to be able to access the data on it.

I've found flexraid but not having much luck with it and their forums don't seem to be used much. Is there any other solution I can use? I've read about LVM but it is possible to use a spare hdd (like parity on raid) From googling it looks like I can't but maybe I am wrong.

---

### Post by rubylaser on 2011-07-22
mdadm is what you would use for software RAID on Linux.  It would allow you to add a disk of any size, but the array size would be calculated based on the smallest disk.  If you want parity (the ability to have a drive fail and not lose everything) and you want the ability to throw in a drive of any size, you might want to look at [Unraid]("http://lime-technology.com/").

Personally, I've always just planned out my storage array basing it on the biggest disks available at that time (I'd use 3TB disks today), and then just add 3TB disks going forward.  I've just never really had the need / want to use a bunch of 250/320/500 GB drives in my storage server, so mdadm has served me very well.

---

### Post by parisv on 2011-07-22
yeah I had a look at unraid but I like the thought of having an ubuntu server so i can mess around with other things.

Is there a tutorial on setting mdam up as I've searched around on it and not finding much?

---

### Post by rubylaser on 2011-07-22
This is from the wiki.  [https://raid.wiki.kernel.org/index.php/RAID_setup]("https://raid.wiki.kernel.org/index.php/RAID_setup")

It contains the basic commands to get a RAID5 array setup with mdadm.  It's literally only a few steps.  I partition the disks first, then...

```
apt-get install mdadm
```
```
mdadm --create /dev/md0 --metadata 1.2 --level=5 --raid-devices=4 /dev/sd[bcde]1
```
Wait for it to sync...
```
watch cat /proc/mdstat
```
Then, add a filesystem
```
mkfs.ext4 /dev/md0
```
Then add a line to /etc/fstab to mount it
```
/dev/md0        /storage           ext4    defaults        0       2
```
Mount it.
```
mount -a
```

That's the basic jist of setting up an array.  You'll still need to setup email alerts, and smart monitoring for your disks.

---

### Post by parisv on 2011-07-23
ok first of all I setup the disks in fdisk by doing:

sudo fdisk /dev/sdb
Command (m for help): n
Command action
   e   extended
   p   primary partition (1-4)
p
Partition number (1-4): 1
First cylinder (1-652, default 1): 1
Last cylinder, +cylinders or +size{K,M,G} (1-652, default 652): 652

Command (m for help): w
The partition table has been altered!


then I did sudo mkfs -t ext4 /dev/sdb1

I did this for sdb/sdc/sdd/sde

then I wrote the mdadm command (i wanted it to use 3 disks and maybe setup 1 for parity, not sure if this is correct?)


$ sudo mdadm --create /dev/md0 --metadata 1.2 --level=5 --raid-devices=3 /dev/sd[bcd]1
mdadm: /dev/sdb1 appears to contain an ext2fs file system
    size=5237156K  mtime=Thu Jan  1 01:00:00 1970
mdadm: /dev/sdc1 appears to contain an ext2fs file system
    size=5237156K  mtime=Thu Jan  1 01:00:00 1970
mdadm: /dev/sdd1 appears to contain an ext2fs file system
    size=5237156K  mtime=Thu Jan  1 01:00:00 1970
Continue creating array? y
mdadm: ADD_NEW_DISK for /dev/sdc1 failed: Device or resource busy



not sure why it failed? this is the output from when I changed sdc1 to ext 4:

sudo mkfs -t ext4 /dev/sdc1
mke2fs 1.41.14 (22-Dec-2010)
Filesystem label=
OS type: Linux
Block size=4096 (log=2)
Fragment size=4096 (log=2)
Stride=0 blocks, Stripe width=0 blocks
327680 inodes, 1309289 blocks
65464 blocks (5.00%) reserved for the super user
First data block=0
Maximum filesystem blocks=1342177280
40 block groups
32768 blocks per group, 32768 fragments per group
8192 inodes per group
Superblock backups stored on blocks: 
	32768, 98304, 163840, 229376, 294912, 819200, 884736

Writing inode tables: done                            
Creating journal (32768 blocks): done
Writing superblocks and filesystem accounting information: done

This filesystem will be automatically checked every 31 mounts or
180 days, whichever comes first.  Use tune2fs -c or -i to override.


as it's a vm I might roll back and reboot after the partition creation and try again. maybe reboot after they have been created.

---

### Post by parisv on 2011-07-23
ah the reboots in between the partition creation seem to of helped.

mdadm: array /dev/md0 started   :)

---

### Post by rubylaser on 2011-07-23
You don't need to make a filesystem on each individual disk like you did...
>  then I did sudo mkfs -t ext4 /dev/sdb1

I did this for sdb/sdc/sdd/sde


You'd do that for the array /dev/md0. Although, you're array is working now, I would reformat the disks to remove the filesystems on them so that you don't have problems in the future.

---

