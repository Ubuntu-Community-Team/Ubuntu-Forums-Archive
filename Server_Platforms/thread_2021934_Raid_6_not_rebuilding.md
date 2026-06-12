---
title: "Raid 6 not rebuilding"
date: 2012-07-10
forum: Server Platforms
---

### Post by darkapec on 2012-07-10
A few months ago I added an additional drive to my RAID 5 and decided to reshape it to a RAID 6. Shortly after the process started the power went out and the RAID has not worked since. 

Also, when I reshaped the array I forgot to add it to the array concentration via the controller card. (I think this is the biggest issue)

another concern for me is if you look at the output of "mdadm --examine /dev/sdb1" it says the array size is only 4tb when in reality it should be 8tb is this because of the dual redundancy?

I am not sure what information is going to be most helpful so I will post as much as I can

```

ubuntu@ubuntu:~$ sudo mdadm --detail /dev/md0
/dev/md0:
        Version : 1.2
  Creation Time : Mon Oct 17 04:43:02 2011
     Raid Level : raid6
  Used Dev Size : 1953512960 (1863.02 GiB 2000.40 GB)
   Raid Devices : 4
  Total Devices : 4
    Persistence : Superblock is persistent

    Update Time : Sun Mar 11 23:06:02 2012
          State : active, degraded, Not Started
 Active Devices : 3
Working Devices : 4
 Failed Devices : 0
  Spare Devices : 1

         Layout : left-symmetric-6
     Chunk Size : 512K

     New Layout : left-symmetric

           Name : Kratos:0
           UUID : a534fd37:9406e049:57bd996c:53cc4b2e
         Events : 40035

    Number   Major   Minor   RaidDevice State
       0       8       17        0      active sync   /dev/sdb1
       1       8       33        1      active sync   /dev/sdc1
       2       8       49        2      active sync   /dev/sdd1
       3       8       64        3      spare rebuilding   /dev/sde

```The above code says drive 3 is rebuilding, correct? Or am I misunderstanding? The code below says that md0 is inactive. 


```

ubuntu@ubuntu:~$ cat /proc/mdstat
Personalities : [raid6] [raid5] [raid4] 
md0 : inactive sde[3] sdd1[2] sdb1[0] sdc1[1]
      [7814054115]("tel:7814054115") blocks super 1.2
       
unused devices: <none>

```

```

ubuntu@ubuntu:~$ sudo mdadm --examine /dev/sdb1/dev/sdb1:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x4
     Array UUID : a534fd37:9406e049:57bd996c:53cc4b2e
           Name : Kratos:0
  Creation Time : Mon Oct 17 04:43:02 2011
     Raid Level : raid6
   Raid Devices : 4

 Avail Dev Size : 3907027037 (1863.02 GiB 2000.40 GB)
     Array Size : [7814051840]("tel:7814051840") (3726.03 GiB 4000.79 GB)
  Used Dev Size : 3907025920 (1863.02 GiB 2000.40 GB)
    Data Offset : 2048 sectors
   Super Offset : 8 sectors
          State : clean
    Device UUID : fc438e7d:6252e19f:4c12e4aa:cc1bdfc8

  Reshape pos'n : 130744320 (124.69 GiB 133.88 GB)
     New Layout : left-symmetric

    Update Time : Sun Mar 11 23:06:02 2012
       Checksum : 7a5349fb - correct
         Events : 40035

         Layout : left-symmetric-6
     Chunk Size : 512K

   Device Role : Active device 0
   Array State : AAAA ('A' == active, '.' == missing)
ubuntu@ubuntu:~$ 

```All drives in the array (sdb1, sdc1, sdd1) report the following. However  sde1 reports differently as you can see from the code below. sde1 seems to be hit or miss, sometimes it reports that it is not a valid partition, other times it says no such file or directory. 

```

ubuntu@ubuntu:~$ sudo mdadm --examine /dev/sde1
mdadm: cannot open /dev/sde1: No such file or directory
ubuntu@ubuntu:~$ 

```The code below is also interesting, because it states the device is busy. However prior to starting mdadm I was able to run "fsck.ext4 -n /dev/sdb1" without issue, however fsck reported the drive had a bad superblock. 

```

ubuntu@ubuntu:~$ sudo mdadm --assemble --force /dev/md0 /dev/sdb1 /dev/sdc1 /dev/sdd1 /dev/sde1
mdadm: cannot open device /dev/sdb1: Device or resource busy
mdadm: /dev/sdb1 has no superblock - assembly aborted
ubuntu@ubuntu:~$ 

```I really don't know what to do at this point. I have searched the internet for solutions but nothing really seems to fit my situation. If anyone has any ideas as to what possibly could be going on here and a possible solution I will be grateful. 

Thanks
Jake

---

### Post by rubylaser on 2012-07-10
You seem to be pasting old output or at least some of them (from October).  Could you please provide the output of these commands.

```
cat /etc/mdadm/mdadm.conf
```
```
cat /etc/fstab
```
```
cat /proc/mdstat
```
```
mdadm -E /dev/sd[bcd]1 /dev/sde
```

There shouldn't be a superblock on /dev/sde1 because it appears that you  used the whole disk instead of a partition on that disk when you added it to the array.

With this information, I'll have a better idea what is going on and should be able to help you.  Also, what command did you use when you reshaped the array?

---

### Post by darkapec on 2012-07-10
Thank you so much for looking into my issue. Here is the information you requested. 

I am currently using a ubuntu live disk to pull this information is that going to give me any inaccurate information?

I am not aware of what command was used for the reshape / grow. I simply used the webmin web interface to do so. I attached a screenshot of the webmin info it gave me, it doesnt tell me much. 

[IMG]http://darkapec.net/webmin.bmp[/IMG]

```

ubuntu@ubuntu:~$ cat /etc/mdadm/mdadm.conf
# mdadm.conf
#
# Please refer to mdadm.conf(5) for information about this file.
#

# by default, scan all partitions (/proc/partitions) for MD superblocks.
# alternatively, specify devices to scan, using wildcards if desired.
DEVICE partitions

# auto-create devices with Debian standard permissions
CREATE owner=root group=disk mode=0660 auto=yes

# automatically tag new arrays as belonging to the local system
HOMEHOST <system>

# instruct the monitoring daemon where to send mail alerts
MAILADDR root

# definitions of existing MD arrays
ARRAY /dev/md/0 metadata=1.2 UUID=a534fd37:9406e049:57bd996c:53cc4b2e name=Kratos:0

# This file was auto-generated on Tue, 10 Jul 2012 06:19:12 +0000
# by mkconf $Id$
ubuntu@ubuntu:~$ 

```I adjusted fstab yesterday to remove the raid from auto mounting on startup. 

```

ubuntu@ubuntu:~$ cat /etc/fstab
aufs / aufs rw 0 0
tmpfs /tmp tmpfs nosuid,nodev 0 0
/dev/sda5 swap swap defaults 0 0
ubuntu@ubuntu:~$

``````

ubuntu@ubuntu:~$ cat /proc/mdstat
Personalities : [raid6] [raid5] [raid4] 
md0 : inactive sde[3] sdd1[2] sdb1[0] sdc1[1]
      [7814054115]("tel:7814054115") blocks super 1.2
       
unused devices: <none>
ubuntu@ubuntu:~$ 

``````

ubuntu@ubuntu:~$ sudo mdadm -E /dev/sd[bcd]1 /dev/sde
/dev/sdb1:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x4
     Array UUID : a534fd37:9406e049:57bd996c:53cc4b2e
           Name : Kratos:0
  Creation Time : Mon Oct 17 04:43:02 2011
     Raid Level : raid6
   Raid Devices : 4

 Avail Dev Size : 3907027037 (1863.02 GiB 2000.40 GB)
     Array Size : [7814051840]("tel:7814051840") (3726.03 GiB 4000.79 GB)
  Used Dev Size : 3907025920 (1863.02 GiB 2000.40 GB)
    Data Offset : 2048 sectors
   Super Offset : 8 sectors
          State : clean
    Device UUID : fc438e7d:6252e19f:4c12e4aa:cc1bdfc8

  Reshape pos'n : 130744320 (124.69 GiB 133.88 GB)
     New Layout : left-symmetric

    Update Time : Sun Mar 11 23:06:02 2012
       Checksum : 7a5349fb - correct
         Events : 40035

         Layout : left-symmetric-6
     Chunk Size : 512K

   Device Role : Active device 0
   Array State : AAAA ('A' == active, '.' == missing)
/dev/sdc1:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x4
     Array UUID : a534fd37:9406e049:57bd996c:53cc4b2e
           Name : Kratos:0
  Creation Time : Mon Oct 17 04:43:02 2011
     Raid Level : raid6
   Raid Devices : 4

 Avail Dev Size : 3907027037 (1863.02 GiB 2000.40 GB)
     Array Size : [7814051840]("tel:7814051840") (3726.03 GiB 4000.79 GB)
  Used Dev Size : 3907025920 (1863.02 GiB 2000.40 GB)
    Data Offset : 2048 sectors
   Super Offset : 8 sectors
          State : clean
    Device UUID : 174e4f18:1bb2b2ae:05bfece5:ccabc55b

  Reshape pos'n : 130744320 (124.69 GiB 133.88 GB)
     New Layout : left-symmetric

    Update Time : Sun Mar 11 23:06:02 2012
       Checksum : f1d50370 - correct
         Events : 40035

         Layout : left-symmetric-6
     Chunk Size : 512K

   Device Role : Active device 1
   Array State : AAAA ('A' == active, '.' == missing)
/dev/sdd1:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x4
     Array UUID : a534fd37:9406e049:57bd996c:53cc4b2e
           Name : Kratos:0
  Creation Time : Mon Oct 17 04:43:02 2011
     Raid Level : raid6
   Raid Devices : 4

 Avail Dev Size : 3907027037 (1863.02 GiB 2000.40 GB)
     Array Size : [7814051840]("tel:7814051840") (3726.03 GiB 4000.79 GB)
  Used Dev Size : 3907025920 (1863.02 GiB 2000.40 GB)
    Data Offset : 2048 sectors
   Super Offset : 8 sectors
          State : clean
    Device UUID : 31c79272:d019e24c:e792d4c1:c8d37298

  Reshape pos'n : 130744320 (124.69 GiB 133.88 GB)
     New Layout : left-symmetric

    Update Time : Sun Mar 11 23:06:02 2012
       Checksum : 2dccd37 - correct
         Events : 40035

         Layout : left-symmetric-6
     Chunk Size : 512K

   Device Role : Active device 2
   Array State : AAAA ('A' == active, '.' == missing)
/dev/sde:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x6
     Array UUID : a534fd37:9406e049:57bd996c:53cc4b2e
           Name : Kratos:0
  Creation Time : Mon Oct 17 04:43:02 2011
     Raid Level : raid6
   Raid Devices : 4

 Avail Dev Size : 3907027120 (1863.02 GiB 2000.40 GB)
     Array Size : [7814051840]("tel:7814051840") (3726.03 GiB 4000.79 GB)
  Used Dev Size : 3907025920 (1863.02 GiB 2000.40 GB)
    Data Offset : 2048 sectors
   Super Offset : 8 sectors
Recovery Offset : 130749440 sectors
          State : clean
    Device UUID : b5144d18:300cfe7e:7c66ec29:5759e861

  Reshape pos'n : 130744320 (124.69 GiB 133.88 GB)
     New Layout : left-symmetric

    Update Time : Sun Mar 11 23:06:02 2012
       Checksum : 140b7a94 - correct
         Events : 40035

         Layout : left-symmetric-6
     Chunk Size : 512K

   Device Role : Active device 3
   Array State : AAAA ('A' == active, '.' == missing)
ubuntu@ubuntu:~$ 

```Thanks again
Jake

---

### Post by rubylaser on 2012-07-10
This looks good.  All of your event counters match on each disk, all of them reflect that the array is a RAID6, and all of them show all devices present.

You should boot into your real OS to proceed.

Become the superuser.
```
sudo -i
```
Stop your mdadm array (it looks like it already is, but stop it anyways).
```
mdadm --stop /dev/md0
```
Force assemble the array (note the use of /dev/sde not /dev/sde1). 
```
mdadm  --assemble --force /dev/md0 /dev/sd[bcd]1 /dev/sde
```

See what the status is now
```
cat /proc/mdstat
```

**If the above assembles your array and gets it working, please proceed.**

I'd suggest you update your /etc/mdadm/mdadm.conf file to simply it like this.
```

DEVICE partitions
HOMEHOST <system>
MAILADDR root
ARRAY /dev/md0 metadata=1.2 UUID=a534fd37:9406e049:57bd996c:53cc4b2e
```

Finally, update your initramfs
```
update-initramfs -u
```

---

### Post by darkapec on 2012-07-10
The following code yielded "mdadm: cannot open device /dev/sde: device or resource busy"

```

mdadm  --assemble --force /dev/md0 /dev/sd[bcd]1 /dev/sde

```

---

### Post by rubylaser on 2012-07-10
So, your devices must be at different positions than the values you just gave me.  What's the output of this?

```
fdisk -l
```

And, now that you're running from the real OS, can you get the superblock info for each of your disks as I showed above with the mdadm -E command?

---

### Post by darkapec on 2012-07-10
```

jake@Kratos:~$ sudo fdisk -l
[sudo] password for jake:

WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sda: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1      243202  1953514583+  ee  GPT

WARNING: GPT (GUID Partition Table) detected on '/dev/sdb'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sdb: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1      243202  1953514583+  ee  GPT

WARNING: GPT (GUID Partition Table) detected on '/dev/sdc'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sdc: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1      243202  1953514583+  ee  GPT

Disk /dev/sdd: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/sdd doesn't contain a valid partition table

Disk /dev/sde: 64.0 GB, 64023257088 bytes
255 heads, 63 sectors/track, 7783 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0001fe85

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1   *           1        7393    59376640   83  Linux
/dev/sde2            7393        7784     3143681    5  Extended
/dev/sde5            7393        7784     3143680   82  Linux swap / Solaris

```

Looks like my boot drive is now sde when before it was sda (this is probably because I unplugged the boot drive yesterday and attempted raid recovery with another OS)

So I ran the following code but still no luck. 
```

jake@Kratos:~$ sudo mdadm  --assemble --force /dev/md0 /dev/sd[abc]1 /dev/sdd
mdadm: Failed to restore critical section for reshape, sorry.
      Possibly you needed to specify the --backup-file
jake@Kratos:~$

```

```

jake@Kratos:~$ sudo mdadm -E /dev/sd[abc]1 /dev/sdd
/dev/sda1:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x4
     Array UUID : a534fd37:9406e049:57bd996c:53cc4b2e
           Name : Kratos:0  (local to host Kratos)
  Creation Time : Mon Oct 17 00:43:02 2011
     Raid Level : raid6
   Raid Devices : 4

 Avail Dev Size : 3907027037 (1863.02 GiB 2000.40 GB)
     Array Size : 7814051840 (3726.03 GiB 4000.79 GB)
  Used Dev Size : 3907025920 (1863.02 GiB 2000.40 GB)
    Data Offset : 2048 sectors
   Super Offset : 8 sectors
          State : clean
    Device UUID : fc438e7d:6252e19f:4c12e4aa:cc1bdfc8

  Reshape pos'n : 130744320 (124.69 GiB 133.88 GB)
     New Layout : left-symmetric

    Update Time : Sun Mar 11 19:06:02 2012
       Checksum : 7a5349fb - correct
         Events : 40035

         Layout : left-symmetric-6
     Chunk Size : 512K

   Device Role : Active device 0
   Array State : AAAA ('A' == active, '.' == missing)
/dev/sdb1:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x4
     Array UUID : a534fd37:9406e049:57bd996c:53cc4b2e
           Name : Kratos:0  (local to host Kratos)
  Creation Time : Mon Oct 17 00:43:02 2011
     Raid Level : raid6
   Raid Devices : 4

 Avail Dev Size : 3907027037 (1863.02 GiB 2000.40 GB)
     Array Size : 7814051840 (3726.03 GiB 4000.79 GB)
  Used Dev Size : 3907025920 (1863.02 GiB 2000.40 GB)
    Data Offset : 2048 sectors
   Super Offset : 8 sectors
          State : clean
    Device UUID : 174e4f18:1bb2b2ae:05bfece5:ccabc55b

  Reshape pos'n : 130744320 (124.69 GiB 133.88 GB)
     New Layout : left-symmetric

    Update Time : Sun Mar 11 19:06:02 2012
       Checksum : f1d50370 - correct
         Events : 40035

         Layout : left-symmetric-6
     Chunk Size : 512K

   Device Role : Active device 1
   Array State : AAAA ('A' == active, '.' == missing)
/dev/sdc1:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x4
     Array UUID : a534fd37:9406e049:57bd996c:53cc4b2e
           Name : Kratos:0  (local to host Kratos)
  Creation Time : Mon Oct 17 00:43:02 2011
     Raid Level : raid6
   Raid Devices : 4

 Avail Dev Size : 3907027037 (1863.02 GiB 2000.40 GB)
     Array Size : 7814051840 (3726.03 GiB 4000.79 GB)
  Used Dev Size : 3907025920 (1863.02 GiB 2000.40 GB)
    Data Offset : 2048 sectors
   Super Offset : 8 sectors
          State : clean
    Device UUID : 31c79272:d019e24c:e792d4c1:c8d37298

  Reshape pos'n : 130744320 (124.69 GiB 133.88 GB)
     New Layout : left-symmetric

    Update Time : Sun Mar 11 19:06:02 2012
       Checksum : 2dccd37 - correct
         Events : 40035

         Layout : left-symmetric-6
     Chunk Size : 512K

   Device Role : Active device 2
   Array State : AAAA ('A' == active, '.' == missing)
/dev/sdd:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x6
     Array UUID : a534fd37:9406e049:57bd996c:53cc4b2e
           Name : Kratos:0  (local to host Kratos)
  Creation Time : Mon Oct 17 00:43:02 2011
     Raid Level : raid6
   Raid Devices : 4

 Avail Dev Size : 3907027120 (1863.02 GiB 2000.40 GB)
     Array Size : 7814051840 (3726.03 GiB 4000.79 GB)
  Used Dev Size : 3907025920 (1863.02 GiB 2000.40 GB)
    Data Offset : 2048 sectors
   Super Offset : 8 sectors
Recovery Offset : 130749440 sectors
          State : clean
    Device UUID : b5144d18:300cfe7e:7c66ec29:5759e861

  Reshape pos'n : 130744320 (124.69 GiB 133.88 GB)
     New Layout : left-symmetric

    Update Time : Sun Mar 11 19:06:02 2012
       Checksum : 140b7a94 - correct
         Events : 40035

         Layout : left-symmetric-6
     Chunk Size : 512K

   Device Role : Active device 3
   Array State : AAAA ('A' == active, '.' == missing)
jake@Kratos:~$

```

---

