---
title: "mdadm adding a disk to a root RAID5 issues"
date: 2012-10-14
forum: Server Platforms
---

### Post by talung on 2012-10-14
Hi All,

I am going to be building a NAS/Mini server box soon using Ubuntu Server.  In the meantime I have been practicing the raid setup on virtual-box machines.  I am using 20GB drives to test it.

The issue is that I have 6x 2TB drives.  However, on the initial setup, I will only be able to use 4 Drives and then add the extra 2 drives later.  I have decided to go with RAID5.

Building the 4 drive setup on the virtual box is no problem.  Machine boots up and works without issue.  I am setting the raid up during the installation.  Giving last 4gb on raid as swap and rest as root. I am getting approximately 60GB of space as expected.

Now, adding drives is not much of an issue using the 
```
sudo mdadm --add /dev/md0 /dev/sde1
```
then 
```
sudo mdadm --grow /dev/md0 --raid-devices=5
```

And I have setup the partition etc.

First problem is that you cannot run
```
e2fsck -f /dev/md0
```
or 
```
resize2fs /dev/md0
```

while the system is mounted, so I am booting up in rescue mode on the CD is doing the commands through there.  I am also doing 1 drive at a time.

Everything seems to work and I am able to reboot.

```
 sudo mdadm -D /dev/md0
/dev/md0:
        Version : 1.2
  Creation Time : Fri Oct 12 22:43:40 2012
     Raid Level : raid5
     Array Size : 83810304 (79.93 GiB 85.82 GB)
  Used Dev Size : 20952576 (19.98 GiB 21.46 GB)
   Raid Devices : 5
  Total Devices : 5
    Persistence : Superblock is persistent

    Update Time : Sun Oct 14 16:01:52 2012
          State : clean
 Active Devices : 5
Working Devices : 5
 Failed Devices : 0
  Spare Devices : 0

         Layout : left-symmetric
     Chunk Size : 512K

           Name : nas5:0  (local to host nas5)
           UUID : 4bdf2e76:61cb41f4:de11b54a:377ec82a
         Events : 100

    Number   Major   Minor   RaidDevice State
       0       8        1        0      active sync   /dev/sda1
       1       8       17        1      active sync   /dev/sdb1
       2       8       33        2      active sync   /dev/sdc1
       3       8       49        3      active sync   /dev/sdd1
       4       8       65        4      active sync   /dev/sde1


```

Shows that it seems to have added the extra drive properly, however the df command does not show this extra space.

```
df -h
Filesystem      Size  Used Avail Use% Mounted on
/dev/md0p1       56G  1.8G   51G   4% /
udev            2.0G  4.0K  2.0G   1% /dev
tmpfs           791M  484K  791M   1% /run
none            5.0M     0  5.0M   0% /run/lock
none            2.0G     0  2.0G   0% /run/shm
```

Anybody have any ideas?  I have tried the setup putting the root system on a non-raid device and was able to expand without an issue.

I have already done tons of searching and about 7 or 8 virtual machines, but just cannot get past this issue.  Some posts seem to refer to a similiar thing, but are always solved by the resize2fs which doesn't really help me at all.

Thanks for any input anybody has on this.

---

### Post by darkod on 2012-10-14
If I'm not mistaken, the partition /dev/md0p1 has it's size set during the initial install, and that can't be automatically expanded after you grow the array (raid device).

Likewise, resize2fs serves to resize the filesystem on a specific partition (not raid device like /dev/md0) but until you expand the partition itself resize2fs has nowhere to grow.

Have you tried Gparted from live mode or similar to resize /dev/md0p1 after you grew the raid device?

PS. If you prefer to use parted and the CLI, I think it has an option to expand partitions too. But I guess you will have to do that from live mode again.

---

### Post by talung on 2012-10-14
> **darkod said:**
> If I'm not mistaken, the partition /dev/md0p1 has it's size set during the initial install, and that can't be automatically expanded after you grow the array (raid device).

Likewise, resize2fs serves to resize the filesystem on a specific partition (not raid device like /dev/md0) but until you expand the partition itself resize2fs has nowhere to grow.

Have you tried Gparted from live mode or similar to resize /dev/md0p1 after you grew the raid device?

PS. If you prefer to use parted and the CLI, I think it has an option to expand partitions too. But I guess you will have to do that from live mode again.

Hi There,

I think you have it the nail right on the head.  I tried running gparted from the running system, and can see that extra 20GB at the end of the disk with the swap sitting in the middle.  Now the issue is trying to get gparted running from a live cd and being able to recognise the RAID.  I just tried the desktop live CD and it doesn't have it.

The Server live CD does have parted, but I am unsure of the way to do it that as there are three devices md127, md127p1 and md127p2.

But at least now I have a direction on which to go. 

Thanks

---

### Post by talung on 2012-10-14
This issue is solved now.

The issue was exactly as stated in the previous post.  The SWAP space was preventing the raid from expanding.

Using PartedMagic ISO
[http://partedmagic.com/doku.php]("http://partedmagic.com/doku.php")

I was able to boot up with it, and move the partitions and expand them using gparted.  It worked well with the RAID setup.

Thanks for your help.

---

### Post by darkod on 2012-10-14
The desktop cd doesn't include mdadm. You need to install the package and tell it to assemble the array (in case it isn't):
```
sudo apt-get install mdadm
sudo mdadm --assemble --scan
```

That should do it. After that you should be able to manipulate md0.

---

### Post by talung on 2012-10-14
> **darkod said:**
> The desktop cd doesn't include mdadm. You need to install the package and tell it to assemble the array (in case it isn't):
```
sudo apt-get install mdadm
sudo mdadm --assemble --scan
```

That should do it. After that you should be able to manipulate md0.

Thanks for that Darkod.  It never even occured to me to install stuff on the ram disk from the CD.  This would have helped me a ton in the past.

Amazing how some things you just don't see even when you staring at them directly.

So that's 2 methods now to fix the issue.

---

