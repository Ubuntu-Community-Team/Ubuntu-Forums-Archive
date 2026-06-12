---
title: "Ubuntu 11.04 Server Problems booting Raid1"
date: 2011-12-04
forum: Server Platforms
---

### Post by joe joe on 2011-12-04
I am trying to build a server using Ubuntu 11.04 Server OS and configuring it as raid1 (mirroring two 1TB hard drives).  I have done the installation following the instructions from [https://help.ubuntu.com/10.04/serverguide/C/advanced-installation.html](https://help.ubuntu.com/10.04/serverguide/C/advanced-installation.html).  

From a "cat /proc/mdstat" command, it looks like my / and /swap partitions are being being synced properly.    

[COLOR=Red]joet@auslx01:~$ cat /proc/mdstat
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md0 : active raid1 sdb2[1] sda2[0]
      945510264 blocks super 1.2 [2/2] [UU]
      
md1 : active raid1 sdb1[1] sda1[0]
      31248312 blocks super 1.2 [2/2] [UU]
      
unused devices: <none>
[/COLOR]
--------------------------------------------------------------------------------------------------

[COLOR=Red]joet@auslx01:~$ sudo mdadm -D /dev/md0
/dev/md0:
        Version : 1.2
  Creation Time : Wed Nov  9 20:29:18 2011
     Raid Level : raid1
     Array Size : 945510264 (901.71 GiB 968.20 GB)
  Used Dev Size : 945510264 (901.71 GiB 968.20 GB)
   Raid Devices : 2
  Total Devices : 2
    Persistence : Superblock is persistent

    Update Time : Fri Dec  2 10:45:23 2011
          State : clean
 Active Devices : 2
Working Devices : 2
 Failed Devices : 0
  Spare Devices : 0

           Name : auslx01:0  (local to host auslx01)
           UUID : 918a33c7:62fd2bbe:218de769:017624fa
         Events : 26

    Number   Major   Minor   RaidDevice State
       0       8        2        0      active sync   /dev/sda2
       1       8       18        1      active sync   /dev/sdb2
[/COLOR]

Now, I'm trying to test it by disconnecting one drive at a time and seeing if I'm able to boot from a single drive.  When I disconnect sdb, I'm still able to bootup from sda, however when I disconnect sda and connect sdb, I get a "Operating system not found" message during boot and it hangs without booting the OS.  Of course, I'm disconnecting/connecting the drives while the system is turned off. 

My first suspicion was that maybe sdb was missing the grub bootloader, but according to the following command it's on both sda and sdb.  

[COLOR=Red]joet@auslx01:~$ sudo dd bs=512 count=1 if=/dev/sda 2>/dev/null | strings
ZRr=
`|f    
\|f1
GRUB 
Geom
Hard Disk
Read
 Error
joet@auslx01:~$ sudo dd bs=512 count=1 if=/dev/sdb 2>/dev/null | strings
ZRr=
`|f    
\|f1
GRUB 
Geom
Hard Disk
Read
 Error
[/COLOR]
Anybody have a clue what could be my problem?  I'm also including the log I got from running a harddrive scan with a script I found online that describes my current configuration.

---

### Post by darkod on 2011-12-04
I assume you are waiting for everything to sync after plugging back one disk before continuing with unplugging the other?

---

### Post by joe joe on 2011-12-05
That is correct, I do wait for everything to reach 100% sync after I plug everything once again.

---

### Post by joe joe on 2011-12-05
I played with it a bit more and I was able to get my machine to boot from either driver by itself without its mirrored one connected. However, I found that it would only boot from the drive if it was connected to one of the SATA cables (i.e. Cable "A").  Having one of the drives connected to the other cable, Cable "B", does gives me the "Operating System not found".  Seems to me likes it's a BIOS issue, as if BIOS was not cycling through all the ports to see which one had a bootable image, and instead quits if it doesn't see anything on SATA Cable "A".   

Is this theory plausible?

---

### Post by darkod on 2011-12-06
Look in BIOS in hdd boot order. Most recent BIOSes have separate Device Order setting, for like CD-ROM, USB, HDD, etc.
But then there is HDD boot order which just lists in what order it tries to boot from the HDDs you have present.
But I was under the impression it cycles them all too.

Another option is some sort of bug in 11.10, maybe 11.04 too. I was trying to test this same thing in Virtual Box and it was doing the same. The first disk can work without the second, but not the second without the first.

I tried lots of options, and if I remember correctly it only worked when I used 10.04 LTS server. I don't know if the fact it is LTS made the difference. With 10.04 it seemed to work fine no matter which disk you unplug.

For me it was just a test, so it didn't matter. Not sure if you want to run 10.04 instead of 11.04.

---

### Post by zeljkojagust on 2011-12-07
Did you install grub boot loader in MBR of both disks?

---

