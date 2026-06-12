---
title: "RAID 5 Silent Data Corruption.  How to track down?"
date: 2009-01-11
forum: Server Platforms
---

### Post by whatever69 on 2009-01-11
Hi guys,

I have a RAID 5 array.  Running:

```
$sudo mdadm --detail /dev/md0
```

returns:
> 
/dev/md0:
        Version : 00.90
  Creation Time : Mon Mar 27 18:21:42 2006
     Raid Level : raid5
     Array Size : 879100608 (838.38 GiB 900.20 GB)
  Used Dev Size : 293033536 (279.46 GiB 300.07 GB)
   Raid Devices : 4
  Total Devices : 4
Preferred Minor : 0
    Persistence : Superblock is persistent

    Update Time : Sun Jan 11 22:58:11 2009
          State : clean
 Active Devices : 4
Working Devices : 4
 Failed Devices : 0
  Spare Devices : 0

         Layout : left-symmetric
     Chunk Size : 64K

           UUID : 63a537ab:40b4da90:253ad282:433c621f
         Events : 0.6759228

    Number   Major   Minor   RaidDevice State
       0       8       17        0      active sync   /dev/sdb1
       1       8        1        1      active sync   /dev/sda1
       2       8       33        2      active sync   /dev/sdc1
       3       8       49        3      active sync   /dev/sdd1

I downloaded a 700 MB video file.  I watched it.  Then I tried copying it over to my Windows Box over Samba, and I got a 

```
"The request cannot be performed because of an I/O device error"
```

I was also getting "fsck died with exit status 4" when fsck was trying to run after a reboot.

I fire up BitTorrent and force a recheck, and sure enough, I'm stuck I'm back to 47%!!  How can I possibly lose 53% of such a large file, and mdadm report back that everything is fine.  My raid array is now full of such files as I'm trying to back everything up to a USB HD, but obviously, I can't copy many files since they're corrupt.

Any help on how to test for whether or not a HD of my 4x320GB RAID 5 setup would much appreciated.  I've had this system running since 2006.

Just want to add as well that I ran dmesg and for the first time I noticed this message:

> t=3072271464, limit=1758201216
[22915.381171] attempt to access beyond end of device
[22915.381189] md0: rw=0, want=3072271464, limit=1758201216
[22915.383805] attempt to access beyond end of device
[22915.383820] md0: rw=0, want=3072271464, limit=1758201216
[22915.387383] attempt to access beyond end of device
[22915.387397] md0: rw=0, want=3072271464, limit=1758201216
[22915.390669] attempt to access beyond end of device
[22915.390682] md0: rw=0, want=3072271464, limit=1758201216
[22915.395274] attempt to access beyond end of device
[22915.395288] md0: rw=0, want=3072271464, limit=1758201216
[22915.398846] attempt to access beyond end of device
[22915.398858] md0: rw=0, want=3072271464, limit=1758201216
[22915.403468] attempt to access beyond end of device
[22915.403481] md0: rw=0, want=3072271464, limit=1758201216
[22932.951509] EXT3-fs error (device md0): ext3_free_blocks: Freeing blocks not in datazone - block = 384033932, count = 1
...
[37239.198174] EXT3-fs error (device md0): ext3_free_blocks: Freeing blocks not in datazone - block = 475562187, count = 1
[37239.249570] EXT3-fs error (device md0): ext3_free_blocks: Freeing blocks not in datazone - block = 2786282527, count = 1
...
[125013.469766] md0: rw=0, want=25533152304, limit=1758201216
[126276.385543] EXT3-fs error (device md0): ext3_free_blocks: Freeing blocks not in datazone - block = 3191644037, count = 1
[126619.129769] UDP: bad checksum. From 203.xxx.xxx.xxx:50400 to 192.168.0.101:50000 ulen 111

In /var/log/messages:

> Jan 11 22:53:41 ubuntuserver kernel: [125013.459935] md0: rw=0, want=25533152304, limit=1758201216
Jan 11 22:53:41 ubuntuserver kernel: [125013.463848] attempt to access beyond end of device
Jan 11 22:53:41 ubuntuserver kernel: [125013.463864] md0: rw=0, want=25533152304, limit=1758201216
Jan 11 22:53:41 ubuntuserver kernel: [125013.469748] attempt to access beyond end of device
Jan 11 22:53:41 ubuntuserver kernel: [125013.469766] md0: rw=0, want=25533152304, limit=1758201216
Jan 11 23:10:44 ubuntuserver -- MARK --

Thanks

---

### Post by Cracauer on 2009-01-12
Nice screwup :)

Care to post your partition tables and df output?

I think it's pretty clear that either the partitions aren't as big as md thinks or that the filesystem thinks the block device is bigger than md thinks. Looks like the latter.

---

### Post by samosamo on 2009-01-12
I had a bad problem like this once.  It drove me insane.  It ended up being bad memory.  Replace all your memory, and then test by comparing md5 hashes on the source and destination machines.

---

### Post by fjgaude on 2009-01-12
Since the array looks healthy, the drives seem okay too, then seek out the memory as the element going bad, really bad.

---

### Post by Cracauer on 2009-01-12
No, this is clearly some software issue where the tool creating the filesystem thought that the block device (the raid) is bigger than it actually is.

---

### Post by whatever69 on 2009-01-12
This is a nice screw up indeed :(

I'm at work right now, but before going to bed last night, I ran Memtest for 9+ hours.  Not a single error this morning, so the RAM is fine.  Once I exited Memtest, I hit that "fsck has died status 4" message.  I ran:

$fsck /dev/md0

but I had to rush to work.  It's probably still waiting for my input as I didn't use the -a flag.

What command would you like me to issue for the partition table?
I will issue df -h and df as soon as I get home today.

Thanks!

---

### Post by Cracauer on 2009-01-12
fdisk and "p"

df not with -h, we need the exact number.

---

### Post by whatever69 on 2009-01-12
Ok.  Got home and fsck was waiting for me, so I answered yes to a bunch of fsck questions:

1.  inode xx has extents_fl flag set on filesystem without extents support.  Clear?
2.  i_file_acl for node xx is yyy, should be zero. Clear?
3.  Inode xx has invalid mode.  Clear?
4.  Checking group summary infomration.  Block bitmap differences: -xx -yy -zz etc....Fix?
5.  Free blocks count wrong for group #zz.  Fix? (this question occured 44 times)
6.  Free inodes count wrong for group #zz.  Fix? (this question occured 2 times)

Then:
/dev/md0: **** FILE SYSTEM WAS MODIFIED ***
/dev/md0:  xx/yy fiels (23.1% non-contiguous), xx/zz blocks.

Fsck is now done.
> 
$df
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sde1             18902836   3633220  14316964  21% /
tmpfs                   484308         0    484308   0% /lib/init/rw
varrun                  484308       304    484004   1% /var/run
varlock                 484308         0    484308   0% /var/lock
udev                    484308      2796    481512   1% /dev
tmpfs                   484308       352    483956   1% /dev/shm
lrm                     484308      2000    482308   1% /lib/modules/2.6.27-9-generic/volatile
/dev/md0             875581332 577906556 253719748  70% /mnt/raid

> roy@ubuntuserver:~$ sudo fdisk -l /dev/md0 

Disk /dev/md0: 900.1 GB, 900199022592 bytes
2 heads, 4 sectors/track, 219775152 cylinders
Units = cylinders of 8 * 512 = 4096 bytes
Disk identifier: 0x00000000

Disk /dev/md0 doesn't contain a valid partition table
roy@ubuntuserver:~$ sudo fdisk /dev/md0
Device contains neither a valid DOS partition table, nor Sun, SGI or OSF disklabel
Building a new DOS disklabel with disk identifier 0x7df2876d.
Changes will remain in memory only, until you decide to write them.
After that, of course, the previous content won't be recoverable.


The number of cylinders for this disk is set to 219775152.
There is nothing wrong with that, but this is larger than 1024,
and could in certain setups cause problems with:
1) software that runs at boot time (e.g., old versions of LILO)
2) booting and partitioning software from other OSs
   (e.g., DOS FDISK, OS/2 FDISK)
Warning: invalid flag 0x0000 of partition table 4 will be corrected by w(rite)

Command (m for help): m
Command action
   a   toggle a bootable flag
   b   edit bsd disklabel
   c   toggle the dos compatibility flag
   d   delete a partition
   l   list known partition types
   m   print this menu
   n   add a new partition
   o   create a new empty DOS partition table
   p   print the partition table
   q   quit without saving changes
   s   create a new empty Sun disklabel
   t   change a partition's system id
   u   change display/entry units
   v   verify the partition table
   w   write table to disk and exit
   x   extra functionality (experts only)

Command (m for help): p

Disk /dev/md0: 900.1 GB, 900199022592 bytes

and
> 
roy@ubuntuserver:~$ sudo fdisk -l

Disk /dev/sda: 300.0 GB, 300090728448 bytes
255 heads, 63 sectors/track, 36483 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       36483   293049666   fd  Linux raid autodetect

Disk /dev/sdb: 300.0 GB, 300090728448 bytes
255 heads, 63 sectors/track, 36483 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       36483   293049666   fd  Linux raid autodetect

Disk /dev/sdc: 300.0 GB, 300069052416 bytes
255 heads, 63 sectors/track, 36481 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1       36481   293033601   fd  Linux raid autodetect

Disk /dev/sdd: 300.0 GB, 300069052416 bytes
255 heads, 63 sectors/track, 36481 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1       36481   293033601   fd  Linux raid autodetect

Disk /dev/sde: 20.4 GB, 20409532416 bytes
255 heads, 63 sectors/track, 2481 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0002f6f7

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1               1        2372    19053058+  83  Linux
/dev/sde2            2373        2481      875542+   5  Extended
/dev/sde5            2373        2481      875511   82  Linux swap / Solaris


Let me know if there's any there output I can give you.

---

### Post by whatever69 on 2009-01-12
Btw, I have a highpoint card (HighPoint RocketRAID 1640 (4 Port SATA)) running in JBOD mode and just found this bug:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/256316](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/256316)

I'm running 2.26.27.9 kernel.  Maybe they never fixed it?  This sounds very bad.  I hope you can see something wrong in the above information and that it's not the above bug.  That would suck.  But it makes sense.  I've had this RAID array for 2 years and now it start going wacky after I went to 8.10.  I've not changed the array option in /etc/fstab to mount only in 'ro'.  I'm hoping this will stop the damage as the 2.26 kernel is the problem.  2.24 was fine.  But I can't go back.  Well I could, but I would need to format the OS.  What do you think?

---

### Post by whatever69 on 2009-01-14
Here's the Linux Kernel Bug:  [http://bugzilla.kernel.org/show_bug.cgi?id=11328](http://bugzilla.kernel.org/show_bug.cgi?id=11328)

If you have a HighPoint Card, and are using the HPT374 driver and are using Ubuntu 8.10 (2.26 Kernel), **_[COLOR="Red"]you are most likely loosing files every time you write to your drive[/COLOR]_**.  FSCK merely causes more data loss.  !!BE WARNED!!  Mount your array in ReadOnly mode for now, or go back to Ubuntu 8.04.  The bug is in progress.  

EDIT:  I hate using the colour RED, but I'd rather err on the side of caution.

---

### Post by Cracauer on 2009-01-14
> **whatever69 said:**
> Here's the Linux Kernel Bug:  [http://bugzilla.kernel.org/show_bug.cgi?id=11328](http://bugzilla.kernel.org/show_bug.cgi?id=11328)

If you have a HighPoint Card, and are using the HPT374 driver and are using Ubuntu 8.10 (2.26 Kernel), **_[COLOR="Red"]you are most likely loosing files every time you write to your drive[/COLOR]_**.  FSCK merely causes more data loss.  !!BE WARNED!!  Mount your array in ReadOnly mode for now, or go back to Ubuntu 8.04.  The bug is in progress.  

EDIT:  I hate using the colour RED, but I'd rather err on the side of caution.

Yeah but this thread as started has nothing to do with this driver.

---

### Post by whatever69 on 2009-01-14
> **Cracauer said:**
> Yeah but this thread as started has nothing to do with this driver.

You are correct.  Should I change the title?  I'm also looking for the button that indicates "SOLVED".  I'm going blind.

---

### Post by fjgaude on 2009-01-14
> **whatever69 said:**
> You are correct.  Should I change the title?  I'm also looking for the button that indicates "SOLVED".  I'm going blind.

Look at the top of the your post at **Thread Tools**, click. That will do it.

---

### Post by whatever69 on 2009-01-14
> **fjgaude said:**
> Look at the top of the your post at **Thread Tools**, click. That will do it.

That's where I thought it was. When I click on Thread tools, I get:

Thread Tools
Show Printable Version Show Printable Version
Email this Page Email this Page
Subscription Subscribe to this Thread
Add a Poll Add a Poll to this Thread

That's it.  I tried PMing an admin, but their box was full.:confused:

---

### Post by fjgaude on 2009-01-14
I  think the forums server and files are in a bad way... I'm sure things will clear up in a day or so. Notice the **Thanks** are not showing either, so some aspects of a very complex file system are down.

---

### Post by whatever69 on 2009-01-14
Cool.  I'm not going crazy after all!!  I'll wait it out.  I think the forums have been going down here and there.

---

### Post by Cracauer on 2009-01-15
"thanks" and "resolved" have been disabled to reduce server load.

Not that it seems to help...

---

### Post by rrohbeck on 2011-01-26
I just saw data corruption in a 5x 500GB md RAID5 (1 motherboard SATA port, 4 on a HighPoint 1640) with Maverick (2.6.35-24.)
The corruption only happens with large-ish files and is typically only 4 bytes. Comparing two copies of an MP3 files with cmp -bl, I get
2797565 145 e    156 n
2797566  47 '    142 b
2797567 116 N    342 M-b
2797568 206 M-^F 112 J
If I drop caches and try again, the difference is somewhere else or not present at all. Smells very much like corruption during the PCI transfer :(
I'll see if the HighPoint driver at [http://www.highpoint-tech.com/USA/bios_rr1640.htm#OpenBuilddriver](http://www.highpoint-tech.com/USA/bios_rr1640.htm#OpenBuilddriver) compiles although the readme file says "Support kernel up to 2.6.31".

---

### Post by kevinthecomputerguy on 2011-01-26
You have some people here helping you that are way better than me. But i too had a problem like this and replace the motherboard, and it went away.
 
Cracauer can tell from the errors whats going on, but i just wanted to pipe up and say that replacing hardware fixed it for me.
 
ugly error indeed, good luck. Keep up the good work.

---

### Post by rrohbeck on 2011-01-30
I can say with reasonable confidence now that installing the driver from [http://www.support-highpoint-tech.com/Main/rr1640/Linux/hpt374-src-v2.20-091127.tgz](http://www.support-highpoint-tech.com/Main/rr1640/Linux/hpt374-src-v2.20-091127.tgz) fixed it. I copied more than 1TB of random data back and forth (dropping the cache each time of course) and there was no corruption.

This is what I did.
Warning: Since you're messing with your disk drivers, do this with an older version of your kernel first or at least have a working backup kernel! In any case, test it sufficiently before using it. I corrupted quite a few files before I noticed the problem with the drivers in 2.6.35.24/25. Just imagine what happens if you rebuild an md RAID5 under spurious random corruption.
```
#! /bin/bash

# VERSION=2.6.35-24-generic
VERSION=`uname -r`
# Need kernel headers
[ -d /usr/src/linux-headers-$VERSION ] || exit 1
make KERNELDIR=/usr/src/linux-headers-$VERSION clean
make KERNELDIR=/usr/src/linux-headers-$VERSION RR154X=1 ARCH=x86
# get rid of conflicting drivers
sudo find /lib/modules/$VERSION/kernel/drivers/ata/ -name \*hpt\* -exec rm '{}' \;
sudo cp hpt374.ko /lib/modules/$VERSION/kernel/drivers/ata/
sudo depmod -a $VERSION
sudo update-initramfs -u -k $VERSION
echo Boot into kernel $VERSION now.

```

---

### Post by rrohbeck on 2011-03-18
I've been running Debian squeeze (using the hpt366 driver) for a while now and the problem is gone too.

---

