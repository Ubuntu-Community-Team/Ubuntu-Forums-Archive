---
title: "software raid or LVM"
date: 2012-10-31
forum: Server Platforms
---

### Post by rgotten on 2012-10-31
On 2008 i installed ubuntu and then i place this question on ubuntu: [http://ubuntuforums.org/showthread.php?t=788493](http://ubuntuforums.org/showthread.php?t=788493) after having the server working for 4 years, last week, i had one hard drive failing (which i had during the 4 years and replace with no problem) but when i try to replace it i have a power outrage and it screw up my complete server. So now i am about to reinstall and even though have being 4 years, i still consider myself very new and would like some advise...So this are my questions:
since I have to do everything again I would like to know what has change and I have to do it the same way or differently.

1)I had install ubuntu server 8.04, it was raid 1 (100mb) for /boot, raid 1 (2gb) for swap, Raid 5 (10gb) for / (system) and raid 5 (980 gb) for /home. this was done using 3 500 GB hard drive. My question here is if should i do the sama or do something different; ie: ext4 instead of ext3. LVM on top of the raids, or anyhting different that you will be suggest


rgotten

---

### Post by sandyd on 2012-10-31
Unfortunately, 8.04 is no longer a supported distribution and has reached EOL. The latest LTS release is 12.04.

A LVM setup is useful when you need to adjust partition sizes, mainly by adding new disks to increase storage capacity.

A few thoughts for the filesystem
XFS is good for storing large files. Since you have RAID5, XFS is fine because it can sometimes be intollerant of disk issues
JFS is good for storing small files, and has an extremely fast fsck, and will recover most damaged files.

Generally, the EXTx filesystem types are just 'general' filesystem types that work in both desktops and servers.

---

### Post by rocker2344 on 2012-10-31
I am lucky to sign in been searching on info for raid/lvm and wanting to move to it.
i have a 12.04 install with static mounts (/dev/sda1 /) 
i want to move to an LVM setup with out a format
Currently i have a 16 ssd (sda) as my root i don't mind resizing it and adding a boot partition.
and a 1tb HDD (sdb) as /home i want to add another hard drive but would like the power of LVM how would i do this? 
the file systems are ext4

P.S. wow apparently i can't edit some of my settings for having less than 25 posts, looks like i will be stuck with 11.04 as my os for a while XD

---

### Post by LHammonds on 2012-11-01
I run my servers in a virtual environment now (IBM BladeCenter + DS3400 storage shelves).  The storage units run a mixture of RAID5 and RAID10 and is managed at the storage level.  It simply presents a LUN storage for my vmware server as just free space available for use.

When I build my servers (which get the automatic benefit of hardware RAID+hotspares without worrying about failed drives), I use LVM for everything except /boot.  I use ext2 for /boot and ext4 for everything else.  I also separate the various system folders into their own volumes for increased security and isolated management of storage space.  I configure my partitions so that there is free space at the volume group level (for online snapshots) and free space on each volume (for automatic space increase).  The design allows for very flexible use over time with a fairly hands-off approach to daily maintenance.

To see how I do it, take a look at my sig for step-by-step guides.

LHammonds

---

