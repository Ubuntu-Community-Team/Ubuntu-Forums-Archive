---
title: "Setting up Software RAID 1"
date: 2009-06-22
forum: Server Platforms
---

### Post by Ankhwatcher on 2009-06-22
Hi, I'm running a home server on Ubuntu-Server Edition.
I want to create two Raid1 zones.
Firstly I want to create a partition on two 1TerraByte drives that will be host to all of my soft copy multimedia.
This will be mounted at /media_library and shared via samba and ushare with my LAN.

Secondly I want to create a partition on two 74.3GB WD Raptors, which will become my /home.
(If all of the multimedia is elsewhere /home doesn't need to be that big)

> rory@ZUBUNT:~$ sudo fdisk -l

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xfad35c47

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1      121601   976760001   83  Linux

Disk /dev/sdb: 74.3 GB, 74355769344 bytes
255 heads, 63 sectors/track, 9039 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x13941393

   Device Boot      Start         End      Blocks   Id  System

Disk /dev/sdc: 74.3 GB, 74355769344 bytes
255 heads, 63 sectors/track, 9039 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x13941393

   Device Boot      Start         End      Blocks   Id  System

Disk /dev/sdd: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000453ff

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1   *           1       38882   312319633+  8e  Linux LVM
/dev/sdd2           38883       38913      249007+   5  Extended
/dev/sdd5           38883       38913      248976   83  Linux

Disk /dev/sde: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xacb687cc

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1               1      121601   976760001   83  Linux

Disk /dev/sdf: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xebf5ebf5

   Device Boot      Start         End      Blocks   Id  System
/dev/sdf1               1       24321   195358401   83  Linux
I have been trying unsuccessfully to create these RAID partitions for a few days now, using mdadm and I would like to remove any traces of previous mistakes before I have another go.
What is the best way to do this?

---

### Post by Bachstelze on 2009-06-22
You have nothing particular to do, all your drives have an empty partition table, so you can just go ahead and create your RAID partitions on them.

---

### Post by doogy2004 on 2009-06-22
> **Ankhwatcher said:**
> I would like to remove any traces of previous mistakes before I have another go.
What is the best way to do this?

Use the shred command to wipe the drives clean.

---

### Post by Ankhwatcher on 2009-06-24
> rory@ZUBUNT:~$ sudo mdadm --create --verbose /dev/md0 --chunk=4 --level=1 --raid-devices=2 /dev/sda1 /dev/sde1
mdadm: chunk size ignored for this level
mdadm: Cannot open /dev/sda1: Device or resource busy
mdadm: Cannot open /dev/sde1: Device or resource busy
mdadm: create aborted

> rory@ZUBUNT:~$ sudo mdadm --create --verbose /dev/md1 --chunk=4 --level=1 --raid-devices=2 /dev/sdb1 /dev/sdc1
mdadm: chunk size ignored for this level
mdadm: Cannot open /dev/sdc1: Device or resource busy
mdadm: create aborted

Any thoughts?

---

### Post by billylid on 2009-06-24
check what partitions have been created by using
 
[COLOR=black]mdadm --detail /dev/[device name/number][/COLOR]
 
if the setup is not correct you can stop/remove the partitions using
 
mdadm --stop /dev/[device name/number]
 
which will allow you to set up the paritions again and stop throwing up the "busy" error

---

### Post by Ankhwatcher on 2009-06-24
```
rory@ZUBUNT:~$ sudo mdadm --detail /dev/md0
mdadm: md device /dev/md0 does not appear to be active.
rory@ZUBUNT:~$ sudo mdadm --detail /dev/md1
mdadm: md device /dev/md1 does not appear to be active.
rory@ZUBUNT:~$ sudo mdadm --create --verbose /dev/md0 --chunk=4 --level=1 --raid-devices=2 /dev/sda1 /dev/sde1
mdadm: chunk size ignored for this level
mdadm: Cannot open /dev/sda1: Device or resource busy
mdadm: Cannot open /dev/sde1: Device or resource busy
mdadm: create aborted
rory@ZUBUNT:~$ sudo mdadm --create --verbose /dev/md1 --chunk=4 --level=1 --raid-devices=2 /dev/sdb1 /dev/sdc1
mdadm: chunk size ignored for this level
mdadm: Cannot open /dev/sdb1: No such file or directory
mdadm: Cannot open /dev/sdc1: Device or resource busy
mdadm: create aborted
```
latest FDISK -L
```
rory@ZUBUNT:~$ sudo fdisk -lu

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xfad35c47

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63  1953520064   976760001   fd  Linux raid autodetect

Disk /dev/sdb: 74.3 GB, 74355769344 bytes
255 heads, 63 sectors/track, 9039 cylinders, total 145226112 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x13941393

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63   145211534    72605736   fd  Linux raid autodetect

Disk /dev/sdc: 74.3 GB, 74355769344 bytes
255 heads, 63 sectors/track, 9039 cylinders, total 145226112 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x13941393

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1              63   145211534    72605736   fd  Linux raid autodetect

Disk /dev/sdd: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000453ff

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1   *          63   624639329   312319633+  8e  Linux LVM
/dev/sdd2       624639330   625137344      249007+   5  Extended
/dev/sdd5       624639393   625137344      248976   83  Linux

Disk /dev/sde: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xacb687cc

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1              63  1953520064   976760001   fd  Linux raid autodetect

Disk /dev/sdf: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders, total 390721968 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xebf5ebf5

   Device Boot      Start         End      Blocks   Id  System
/dev/sdf1              63   390716864   195358401   83  Linux
```

---

### Post by doogy2004 on 2009-06-24
What is the output of this?
```
df -h
```
It will tell you if you have the disks mounted somewhere.


This will give you the status of and software raid volumes.
```
cat /proc/mdstat
```

---

### Post by Ankhwatcher on 2009-06-25
Okay, here are the results:
```
rory@ZUBUNT:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/mapper/ZUBUNT-root
                      288G  5.3G  268G   2% /
tmpfs                 994M     0  994M   0% /lib/init/rw
varrun                994M  360K  994M   1% /var/run
varlock               994M     0  994M   0% /var/lock
udev                  994M  176K  994M   1% /dev
tmpfs                 994M   12K  994M   1% /dev/shm
lrm                   994M  2.7M  991M   1% /lib/modules/2.6.28-11-server/volatile
/dev/sdd5             228M   15M  202M   7% /boot
/home/rory/.Private   288G  5.3G  268G   2% /home/rory
```
```

rory@ZUBUNT:~$ cat /proc/mdstat
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10]
md1 : active raid1 sdb[0]
      72612992 blocks [2/1] [U_]

unused devices: <none>
```

---

### Post by Luke has no name on 2009-06-25
Hey, use the [ code ] tag, not the [ quote ] tag. Much easier to read... code.

---

### Post by Ankhwatcher on 2009-06-28
```
rory@ZUBUNT:~$ cat /proc/mdstat
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10]
md1 : active raid1 sdb[0]
      72612992 blocks [2/1] [U_]

md_d1 : inactive sdc[1](S)
      72612992 blocks

md_d0 : inactive dm-3[0](S)
      976759936 blocks

unused devices: <none>
```
okay, this is what it has been saying since I restarted and ran --assemble --scan
(which output)
```
rory@ZUBUNT:~$ sudo mdadm --assemble --scan
mdadm: /dev/md1 has been started with 1 drive (out of 2).
mdadm: no devices found for /dev/md0
```
Need help.

---

### Post by doogy2004 on 2009-06-29
what is the output of:
```
lshw -short
```

---

### Post by Ankhwatcher on 2009-06-29
```
rory@ZUBUNT:~$ sudo lshw -short
H/W path             Device      Class       Description
========================================================
                                 system      MS-7519
/0                               bus         MS-7519
/0/0                             memory      64KiB BIOS
/0/4                             processor   Intel(R) Pentium(R) Dual  CPU  E2200  @ 2.20GHz
/0/4/5                           memory      64KiB L1 cache
/0/4/6                           memory      1MiB L2 cache
/0/4/7                           memory      L3 cache
/0/2d                            memory      2GiB System Memory
/0/2d/0                          memory      1GiB DIMM SDRAM Synchronous
/0/2d/1                          memory      DIMM [empty]
/0/2d/2                          memory      1GiB DIMM SDRAM Synchronous
/0/2d/3                          memory      DIMM [empty]
/0/100                           bridge      4 Series Chipset DRAM Controller
/0/100/1                         bridge      4 Series Chipset PCI Express Root Port
/0/100/1/0                       display     GeForce 8400 GS
/0/100/1a                        bus         82801JI (ICH10 Family) USB UHCI Controller #4
/0/100/1a.1                      bus         82801JI (ICH10 Family) USB UHCI Controller #5
/0/100/1a.2                      bus         82801JI (ICH10 Family) USB UHCI Controller #6
/0/100/1a.7                      bus         82801JI (ICH10 Family) USB2 EHCI Controller #2
/0/100/1b                        multimedia  82801JI (ICH10 Family) HD Audio Controller
/0/100/1c                        bridge      82801JI (ICH10 Family) PCI Express Port 1
/0/100/1c/0          scsi4       storage     JMB368 IDE controller
/0/100/1c/0/0.0.0    /dev/cdrom  disk        DVD writer
/0/100/1c/0/0.1.0    /dev/sdf    disk        200GB WDC WD2000BB-14G
/0/100/1c/0/0.1.0/1  /dev/sdf1   volume      186GiB EXT3 volume
/0/100/1c.1                      bridge      82801JI (ICH10 Family) PCI Express Port 2
/0/100/1c.5                      bridge      82801JI (ICH10 Family) PCI Express Port 6
/0/100/1c.5/0        eth0        network     RTL8111/8168B PCI Express Gigabit Ethernet controller
/0/100/1d                        bus         82801JI (ICH10 Family) USB UHCI Controller #1
/0/100/1d.1                      bus         82801JI (ICH10 Family) USB UHCI Controller #2
/0/100/1d.2                      bus         82801JI (ICH10 Family) USB UHCI Controller #3
/0/100/1d.7                      bus         82801JI (ICH10 Family) USB2 EHCI Controller #1
/0/100/1e                        bridge      82801 PCI Bridge
/0/100/1f                        bridge      82801JIB (ICH10) LPC Interface Controller
/0/100/1f.2          scsi0       storage     82801JI (ICH10 Family) 4 port SATA IDE Controller
/0/100/1f.2/0        /dev/sda    disk        1TB SAMSUNG HD103UJ
/0/100/1f.2/0/1      /dev/sda1   volume      931GiB Linux raid autodetect partition
/0/100/1f.2/1        /dev/sdb    disk        74GB WDC WD740ADFD-00
/0/100/1f.2/1/1                  volume      69GiB Linux raid autodetect partition
/0/100/1f.2/2        /dev/sdc    disk        74GB WDC WD740ADFD-00
/0/100/1f.2/2/1      /dev/sdc1   volume      69GiB Linux raid autodetect partition
/0/100/1f.2/3        /dev/sdd    disk        320GB SAMSUNG HD321KJ
/0/100/1f.2/3/1      /dev/sdd1   volume      297GiB Linux LVM Physical Volume partition
/0/100/1f.2/3/2      /dev/sdd2   volume      243MiB Extended partition
/0/100/1f.2/3/2/5    /dev/sdd5   volume      243MiB Linux filesystem partition
/0/100/1f.3                      bus         82801JI (ICH10 Family) SMBus Controller
/0/100/1f.5          scsi2       storage     82801JI (ICH10 Family) 2 port SATA IDE Controller
/0/100/1f.5/0.0.0    /dev/sde    disk        1TB Hitachi HDT72101
/0/100/1f.5/0.0.0/1  /dev/sde1   volume      931GiB Linux raid autodetect partition
/1                               power       Nikon Ultra Plus
/2                   pan0        network     Ethernet interface
```

---

### Post by doogy2004 on 2009-06-29
Please send the output of:
```
sudo mdadm --detail /dev/md0
```
for each of your arrays

---

### Post by Ankhwatcher on 2009-06-30
```
rory@ZUBUNT:~$ sudo mdadm --detail /dev/md0
mdadm: md device /dev/md0 does not appear to be active.
rory@ZUBUNT:~$ sudo mdadm --detail /dev/md1
/dev/md1:
        Version : 00.90
  Creation Time : Sun Jun 21 19:07:02 2009
     Raid Level : raid1
     Array Size : 72612992 (69.25 GiB 74.36 GB)
  Used Dev Size : 72612992 (69.25 GiB 74.36 GB)
   Raid Devices : 2
  Total Devices : 1
Preferred Minor : 1
    Persistence : Superblock is persistent

    Update Time : Wed Jun 24 16:41:39 2009
          State : clean, degraded
 Active Devices : 1
Working Devices : 1
 Failed Devices : 0
  Spare Devices : 0

           UUID : 58375ab1:7499da2c:f6855d66:41b92356 (local to host ZUBUNT)
         Events : 0.10

    Number   Major   Minor   RaidDevice State
       0       8       16        0      active sync   /dev/sdb
       1       0        0        1      removed
```

---

### Post by doogy2004 on 2009-06-30
I'm assuming that since the raid arrays are not mounted that you do not have any data on them yet, correct?

If so do the following for each array:
```
sudo mdadm --stop /dev/md0
```

Then use the following steps to create your arrays:
```
-Determine the Logical location of all drives to be included in array.
sudo lshw -short | grep "/dev/"
-Zero all drives to be included in array
sudo shred -vfz -n 0 /dev/sdd
-Restart Computer so that the kernel sees the changes.
-Format all drives to be included in array.
sudo fdisk /dev/sdd
--Delete all partitions from the drive.
--Create a new primary partition with the default size (default is the entire disk).
--Change partition type to "Linux raid auto"
--Write Changes to Drive
--Repeat for each disk that will be included in the array.
-Restart Computer so that the kernel sees the changes.
-Determine the Logical locations of all drives to be included in the array again to verify if any have changed.
sudo lshw -short | grep "/dev/"
-Create the Raid device (if you have a missing drive replace it with "missing")
sudo mdadm --create --verbose /dev/md0 --level=1 --raid-devices=2 /dev/sdd1 /dev/sde1
-Wait for the array to build.  You can check the progress with:
sudo mdadm --detail /dev/md0
cat /proc/mdstat

```

When creating an array I prefer to manually enter each device rather than using a regular expression to specify the devices.

---

### Post by Ankhwatcher on 2009-07-01
Hey, I'm running the big shred now.
```
screen sudo shred -vfz -n 0 /dev/sd%
-So I can disconnect putty without worrying about accidentally quitting.
```
 The two Terrabyte drives will take all night.
If I wanted to set-up my raid by adding one drive at a time, how would I do that?

---

### Post by doogy2004 on 2009-07-01
> **Ankhwatcher said:**
> Hey, I'm running the big shred now.
```
screen sudo shred -vfz -n 0 /dev/sd%
-So I can disconnect putty without worrying about accidentally quitting.
```
 The two Terrabyte drives will take all night.
If I wanted to set-up my raid by adding one drive at a time, how would I do that?

WARNING!!! Using regular expressions improperly with shred may result in wiping ALL disks!!!

Sorry for the disclaimer but I have to put that out there.

As stated in the instructions, you can create a degraded array by replacing the device path with:
```
missing
```
Rather than the device path.

---

### Post by doogy2004 on 2009-07-01
If for some reason you create an array that is degraded or one of your disks fail, you can use the following instructions to replace the failed/missing disk:
```
-Determine the location of all drives to be added to the array.
sudo lshw -short | grep "/dev/"
-Zero any new drives to be added to the array.
sudo shred -vfz -n 0 /dev/sdd
-Restart the computer so that the kernel sees the changes.
-Format all drives to be added to the array.
sudo fdisk /dev/sdd
--Delete all partitions from the drive.
--Create a new primary partition with the default size (default is the entire disk).
--Change partition type to "Linux raid auto"
--Write changes to drive.
--Repeat for each disk that will be added to the array.
-Restart the computer so that the kernel sees the changes.
-Add the new disk to the array.
sudo mdadm --manage --verbose /dev/md0 --add /dev/sdd1
-Confirm that disk is added and check progress with:
cat /proc/mdstat
```

---

### Post by Ankhwatcher on 2009-07-01
Hey thanks! All of that worked great.
Sadly my problems are still not resolved, yet.
You see the crux of my problem is that when I restart, my raid devices do not reappear.
if I run an --assemble --scan
it will restart my raids with 1 device, (/dev/mdx) and leave the other device in an inactive raid called /dev/md_dx
I've now found I can --stop /dev/md_dx and then sudo mdadm --manage --verbose /dev/mdx --add /dev/sdy1
and when I check the --detail it will be rebuilding the array.

so how can I make my arrays more persistent?
Also, which method would you prefer for creating partitions on the arrays when they are running? And how should I go about finding their UUID when they are created?

---

### Post by doogy2004 on 2009-07-01
> **Ankhwatcher said:**
> so how can I make my arrays more persistent?
Also, which method would you prefer for creating partitions on the arrays when they are running? And how should I go about finding their UUID when they are created?

To create partitions on arrays is done the same as and other "disk"
```
sudo fdisk /dev/md0
```

You can skip the step of creating partitions and jump straight to formatting the "disk"/array.

the following to format:
```
sudo mkfs.ext3 /dev/md01
```

Once you format the "disk" run the following to locate the UUID:
```
sudo blkid
```
Once you have the UUID update your fstab to mount the "disk"/array at boot.

---

### Post by Ankhwatcher on 2009-07-01
Great! I'm doing just that. By the way it actually calls the partition /dev/md0p1.

---

### Post by doogy2004 on 2009-07-01
> **Ankhwatcher said:**
> Great! I'm doing just that. By the way it actually calls the partition /dev/md0p1.

Thanks for the tip, I've never bothered partitioning an array before and I was going to test it in a vm tonight. Now there is no need for me to test it. :p

---

### Post by sjalloq on 2009-07-02
Hi there,

I've been following the instructions on this thread to try and set up my RAID array but am having problems.

My original post is here:  [http://ubuntuforums.org/showthread.php?t=1201075](http://ubuntuforums.org/showthread.php?t=1201075)

I have since used shred to start from scratch, but when I reboot after creating and formatting the array, I still get an fsck error at boot.  This time:

fsck.ext3: Unable to resolve UUID=<some_long_number>
fsck died with exit status 8

The UUID number is the one belonging to /dev/md0 which is the array I created.

What else haven't I done that is causing it to fail?

Thanks.

---

### Post by doogy2004 on 2009-07-02
> **sjalloq said:**
> Hi there,

I've been following the instructions on this thread to try and set up my RAID array but am having problems.

My original post is here:  [http://ubuntuforums.org/showthread.php?t=1201075](http://ubuntuforums.org/showthread.php?t=1201075)

I have since used shred to start from scratch, but when I reboot after creating and formatting the array, I still get an fsck error at boot.  This time:

fsck.ext3: Unable to resolve UUID=<some_long_number>
fsck died with exit status 8

The UUID number is the one belonging to /dev/md0 which is the array I created.

What else haven't I done that is causing it to fail?

Thanks.

Did you format the array and use ```
blkid
``` to find the UUID of the formated array rather than the UUID in ```
mdadm --details /dev/md0
``` ?

---

### Post by sjalloq on 2009-07-02
Hi, yes I used blkid.

When I start up now and try to use mdadm --assemble, I get an error that mdadm couldn't open device /dev/sda1: device or resource busy.

So I guess I have to start again?

---

### Post by doogy2004 on 2009-07-02
> **sjalloq said:**
> Hi, yes I used blkid.

When I start up now and try to use mdadm --assemble, I get an error that mdadm couldn't open device /dev/sda1: device or resource busy.

So I guess I have to start again?

Try this to see if /dev/sda1 is already mounted somewhere
```
df -h
```

---

### Post by sjalloq on 2009-07-02
No it's not mounted somewhere else.  I just found this post which is very similar to what I'm seeing but I'm not sure I understand.

[http://ubuntuforums.org/showthread.php?t=1194974](http://ubuntuforums.org/showthread.php?t=1194974)

---

### Post by sjalloq on 2009-07-02
So I can run mke2fs -n /dev/sda1 but on /dev/sdb1 I get told that the disk is apparently in use by the system.

---

### Post by doogy2004 on 2009-07-02
I have never had to manually start the arrays at start up.

Do both of you have these two files?
```
/etc/init.d/mdadm
```
```
/etc/rc0.d/K25mdadm
```

---

### Post by sjalloq on 2009-07-03
Yes, I have both of those files.

Right, I'm going to start from scratch again but for now I'm not going to update my /etc/fstab so that I can at least boot.

These are the steps I'm going to take.  Please modify and post if I have missed something.  My two drives are /dev/sda and /dev/sdb.  I will not be booting off them and only using them for a data store.

```
1.  % sudo shred -vfz -n 0 /dev/sda
2.  % sudo shred -vfz -n 0 /dev/sdb
3.  restart
4.  % sudo fdisk /dev/sda
    Creating a single primary partition of default size with partition type of 0xFD.
5.  % sudo fdisk /dev/sdb
    Creating a single primary partition of default size with partition type of 0xFD.
6.  restart
7.  % sudo mdadm --create --verbose /dev/md0 --level=1 --raid-devices=2 /dev/sda1 /dev/sdb1
```Now, once the array has finished synchronising, what do we expect to see if I restart?  I am not going to updated /etc/fstab because that causes everything to break.  Will I see /dev/md0 at restart or will I have to use --assemble?

Thanks.  I'm shredding at the moment so will be done by tomorrow morning.

---

### Post by sjalloq on 2009-07-03
Right, shred finished sooner than I thought it would.  Sorry to fill up this thread with my muck but if I log everthing then maybe someone can see what I've done wrong.

Here's the output of fdisk (/dev/sdb is identical):

```
ubuntu-server:~> sudo fdisk /dev/sda
[sudo] password for sjalloq: 
Device contains neither a valid DOS partition table, nor Sun, SGI or OSF disklabel
Building a new DOS disklabel with disk identifier 0xa210266c.
Changes will remain in memory only, until you decide to write them.
After that, of course, the previous content won't be recoverable.


The number of cylinders for this disk is set to 60801.
There is nothing wrong with that, but this is larger than 1024,
and could in certain setups cause problems with:
1) software that runs at boot time (e.g., old versions of LILO)
2) booting and partitioning software from other OSs
   (e.g., DOS FDISK, OS/2 FDISK)
Warning: invalid flag 0x0000 of partition table 4 will be corrected by w(rite)

Command (m for help): n
Command action
   e   extended
   p   primary partition (1-4)
p
Partition number (1-4): 1
First cylinder (1-60801, default 1): 
Using default value 1
Last cylinder, +cylinders or +size{K,M,G} (1-60801, default 60801): 
Using default value 60801

Command (m for help): t
Selected partition 1
Hex code (type L to list codes): fd
Changed system type of partition 1 to fd (Linux raid autodetect)

Command (m for help): w
The partition table has been altered!

Calling ioctl() to re-read partition table.
Syncing disks.
ubuntu-server:~> 

```

---

### Post by sjalloq on 2009-07-03
After restart:

```
ubuntu-server:~> sudo fdisk -l
[sudo] password for sjalloq: 

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xa210266c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       60801   488384001   fd  Linux raid autodetect

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x1f5ec600

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       60801   488384001   fd  Linux raid autodetect

Disk /dev/sdc: 61.4 GB, 61492838400 bytes
255 heads, 63 sectors/track, 7476 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x547c316a

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1        7165    57552831   83  Linux
/dev/sdc2            7166        7476     2498107+   5  Extended
/dev/sdc5            7166        7476     2498076   82  Linux swap / Solaris
ubuntu-server:~> 

```

Followed by this:

```
ubuntu-server:~> sudo mdadm --create --verbose /dev/md0 --level=1 --raid-devices=2 /dev/sda1 /dev/sdb1
mdadm: size set to 488383936K
mdadm: array /dev/md0 started.
ubuntu-server:~> cat /proc/mdstat 
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md0 : active raid1 sdb1[1] sda1[0]
      488383936 blocks [2/2] [UU]
      [>....................]  resync =  0.2% (1100288/488383936) finish=103.3min speed=78592K/sec
      
unused devices: <none>
ubuntu-server:~> sudo fdisk -l

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xa210266c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       60801   488384001   fd  Linux raid autodetect

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x1f5ec600

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       60801   488384001   fd  Linux raid autodetect

Disk /dev/sdc: 61.4 GB, 61492838400 bytes
255 heads, 63 sectors/track, 7476 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x547c316a

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1        7165    57552831   83  Linux
/dev/sdc2            7166        7476     2498107+   5  Extended
/dev/sdc5            7166        7476     2498076   82  Linux swap / Solaris

Disk /dev/md0: 500.1 GB, 500105150464 bytes
2 heads, 4 sectors/track, 122095984 cylinders
Units = cylinders of 8 * 512 = 4096 bytes
Disk identifier: 0x00000000

Disk /dev/md0 doesn't contain a valid partition table
ubuntu-server:~> 

```

Once that has finished sync'ing I just need to run mkfs.ext3 right?  Or do I need to run fdisk again on the new /dev/md0?

Thanks.

---

### Post by doogy2004 on 2009-07-03
> **sjalloq said:**
> Yes, I have both of those files.

Right, I'm going to start from scratch again but for now I'm not going to update my /etc/fstab so that I can at least boot.

These are the steps I'm going to take.  Please modify and post if I have missed something.  My two drives are /dev/sda and /dev/sdb.  I will not be booting off them and only using them for a data store.

```
1.  % sudo shred -vfz -n 0 /dev/sda
2.  % sudo shred -vfz -n 0 /dev/sdb
3.  restart
4.  % sudo fdisk /dev/sda
    Creating a single primary partition of default size with partition type of 0xFD.
5.  % sudo fdisk /dev/sdb
    Creating a single primary partition of default size with partition type of 0xFD.
6.  restart
7.  % sudo mdadm --create --verbose /dev/md0 --level=1 --raid-devices=2 /dev/sda1 /dev/sdb1
```Now, once the array has finished synchronising, what do we expect to see if I restart?  I am not going to updated /etc/fstab because that causes everything to break.  Will I see /dev/md0 at restart or will I have to use --assemble?

Thanks.  I'm shredding at the moment so will be done by tomorrow morning.

You need to format the array, find the UUID with blkid, then change the fstab to mount the formated array.

---

### Post by doogy2004 on 2009-07-03
You should verify that when the system is starting up you see a line that states that the system is starting MD devices.  If you are missing this step during boot up, there may be something wrong with your installation of mdadm.

---

### Post by sjalloq on 2009-07-03
Is there a handy log of the boot as I'm running this headless?

Ta.

---

### Post by lmlypfan on 2009-07-03
I have found both the guides below extremely helpful with mdadm.
I consider myself a complete knewb and was able to get RAID 5 up and running fairly easily with these guides.


[http://ubuntuforums.org/showthread.php?t=860087]("http://ubuntuforums.org/showthread.php?t=860087")

<snipped url>

The <snipped> link describes RAID1 as well.

---

### Post by doogy2004 on 2009-07-03
> **sjalloq said:**
> Is there a handy log of the boot as I'm running this headless?

Ta.

```
/var/log/dmesg
```

---

### Post by sjalloq on 2009-07-04
Success!

Right, the only difference this time was creating a /etc/mdadm/mdadm.conf file.  I ran:

```
% mdadm --detail --scan --verbose > /etc/mdadm/mdadm.conf

```And all seems well.  Thanks for all your help.

I did find this guide which is pretty much the steps you recommended but is all in one article.  Might help others too.  A lot of the guides didn't make it explicit that you needed to create the mdadm.conf so that's important to highlight.

[http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch26_:_Linux_Software_RAID](http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch26_:_Linux_Software_RAID)

---

