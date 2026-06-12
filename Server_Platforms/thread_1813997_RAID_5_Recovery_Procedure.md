---
title: "RAID 5 Recovery Procedure"
date: 2011-07-28
forum: Server Platforms
---

### Post by masterkoppa on 2011-07-28
Ok first of all all of this is an assumption so I know what to expect when a RAID 5 Array that I have actually degrades and I have to recover it and I don't have to spend countless hours desperately looking for answers, so here it goes.

Assuming I have a 3 Disk RAID 5 Array set up, what would the correct procedure to recover from 1 disk failing and the array getting degraded?

So far this is what I understand from a couple hours of research:
1. Fail the drive from the array and remove it using mdadm.
2. Then insert the spare
3. ???
4. Add it to the array

The middle part gets a big ambiguous, do I need to do anything with the spare drive at hand, any formating or special commands that I need to run on it.

Like I said I want to have a clear picture before this actually happens and I start to go insane looking for answers.

Thanks in advance!

BTW. This would all be on a Ubuntu Server 11.04 Install, the RAID was set up with the installer and there is no LVM on the RAID, just formated with ext4 on top.

---

### Post by rubylaser on 2011-07-28
I normally use fdisk or parted to add a partition to the disk (I like to use disk partitions for mdadm rather than raw disks, but that's not a requirement).  

Also, you don't even have to fail the disk from mdadm.  Often the disk has completely died, so you power off the box, put in the replacement, partition it, and add it to the array.  mdadm will automatically resync after that.

---

### Post by masterkoppa on 2011-07-30
Thanks,

So basically just partition it with ect4 and plug it in?

Sounds easy enough thanks for your help.

Sorry about the late response.

---

### Post by rubylaser on 2011-07-30
> **masterkoppa said:**
> Thanks,

So basically just partition it with ect4 and plug it in?

Sounds easy enough thanks for your help.

Sorry about the late response.

I'm not sure what you mean by ect4, but I assume you mean ext4.  That would be putting a filesystem on the disk, and you don't want to do that before you add it to the array.  You just use fdisk or parted and create a partition that takes up the disk, and set it as a Linux partition (83 in fdisk).  Then, add it to the array.

---

### Post by bakegoodz on 2011-08-01
I agree, the steps would be:
1. Identify failed drive.
2. Shutdown and replace failed drive
3. Properly partition new drive and reboot
4. Confirm RAID rebuilding (cat /proc/mdstat)
extra step: If possible wipe drive, and run manufacturers diagnostic tool.
drive maybe still usable if it just had a few bad sectors and passes test. If so you can keep it as spare or re-purpose it. If not RMA or recycle it about $0.15 worth of Aluminum in a hard drive.


I have experience with mdadm. I guess it might allow for regular partition type or even no partition, but chances are the installer setup used Raid partition Type or Type df, instead of standard Linux partition or type 83. So look at the other drives partitions and match how they are setup, except /dev/sda probably has an extra /boot partition.

---

### Post by masterkoppa on 2011-08-02
Perfect, thank you both for your responses. Ill try to contribute to the wiki to make things clearer as there is no part on rebuilding a array of any kind.

---

### Post by TheR on 2011-08-02
It works perfectly good with computer turned on. I had my disk failed and replaced after 5 days (praying that another disk won't fail in between) on live iscsi SAN server. 

After new disk came, I inserted it into server (Supermicro storage server) and:
fdisk -l # to determine which device is assigned to new disk 
fdisk /dev/sdg # to create partition for raid
mdadm /dev/md1 -a /dev/sdg1 # to add new drive to array /dev/md1
cat  /proc/mdstat # to see how array rebuilding is progressing

by
TheR

---

### Post by zx1986 on 2012-10-08
>> 3. Properly partition new drive and reboot

sorry, how could I properly partition a new drive ?

I am running Ubuntu 12.04 server on HP DL380 G7,
a disk of my RAID 5 had broken, I replace a new one
(on the fly, just like what I did on RHEL)

but it didn't auto rebuild the new one to disk array, even I reboot my server.
how come ?

---

### Post by rubylaser on 2012-10-09
You need to partition the new disk like the old disks where.  What's the output of this command?

```
fdisk -l
```
after doing that, you need to add the new disk to your array to get mdadm to use it.  In this example, I'll add /dev/sdb1 to my existing array.
```
mdadm --manage /dev/md0 --add /dev/sdb1
```
This will cause mdadm to resync, and add the new disk to the existing array.

---

