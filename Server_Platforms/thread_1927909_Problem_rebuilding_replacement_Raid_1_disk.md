---
title: "Problem rebuilding replacement Raid 1 disk"
date: 2012-02-19
forum: Server Platforms
---

### Post by ransae on 2012-02-19
I'm running a 10.04 server at home using two 2TB WD caviar drives in a linux s/w raid 1 configuration.

The two drives were set up during Ubuntu install.

They contain three partitions, as follows:

> root@server2:~# gdisk /dev/sda
GPT fdisk (gdisk) version 0.8.2

Partition table scan:
  MBR: protective
  BSD: not present
  APM: not present
  GPT: present

Found valid GPT with protective MBR; using GPT.

Command (? for help): p
Disk /dev/sda: 3907029168 sectors, 1.8 TiB
Logical sector size: 512 bytes
Disk identifier (GUID): 87B365C3-1217-47F4-9122-F8DD1F386153
Partition table holds up to 128 entries
First usable sector is 34, last usable sector is 3907029134
Partitions will be aligned on 2048-sector boundaries
Total free space is 387181 sectors (189.1 MiB)

Number  Start (sector)    End (sector)     Size                      Code       Name
   1                        2048                         4095                 1024.0 KiB      EF02        bios
   2                         4096                       589823              286.0 MiB      FD00        boot
   3                      589824           906643967        1.8      TiB          FD00        rootThe disk shown above is the replacement drive. I have set it up identically to  /dev/sda. 

Below shows the array rebuilding after the disk is replaced. As you'd expect.

> root@server2:~# cat /proc/mdstat 
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md1 : active raid1 sdb3[2] sda3[1]
      1953027008 blocks [2/1] [_U]
      [>....................]  recovery =  0.0% (225792/1953027008) finish=864.8min speed=37632K/sec
      
md0 : active raid1 sdb2[0] sda2[1]
      292800 blocks [2/2] [UU]

The arrays rebuild correctly and seem to be working as they should. 

The problem happens when the box is rebooted.

The array goes into degraded mode. It starts to incorrectly rebuild the array as shown below. It ignores md0, and tries to rebuild the md1 array to sdb, not sdb3.

> root@server2:~# cat /proc/mdstat 
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md1 : active raid1 [COLOR=Red]**sdb**[/COLOR][2] sda3[1]
      1953027008 blocks [2/1] [_U]
      [=>...................]  recovery =  9.0% (177317632/1953027008) finish=453.9min speed=65198K/sec
      
md0 : active raid1 sda2[1]
      292800 blocks [2/1] [_U]When I check the sdb disk partition table, it is corrupted ....

> root@server2:~# gdisk /dev/sdb
GPT fdisk (gdisk) version 0.8.2

Caution: invalid main GPT header, but valid backup; regenerating main header
from backup!

Caution! After loading partitions, the CRC doesn't check out!
Warning! Main partition table CRC mismatch! Loaded backup partition table
instead of main partition table!

Warning! One or more CRCs don't match. You should repair the disk!

Partition table scan:
  MBR: not present
  BSD: not present
  APM: not present
  GPT: damaged

Found invalid MBR and corrupt GPT. What do you want to do? (Using the
GPT MAY permit recovery of GPT data.)
 1 - Use current GPT
 2 - Create blank GPT
I've checked the new disk with WD's diagnostic software. It passes the extended test.

I'm presently trying for the third time to get this to work. I'm not confident as I'm not really doing anything differently from the first two efforts. 

Does anyone have any idea why this is happening? Any assistance is greatly appreciated.

---

### Post by ransae on 2012-02-21
Got the answer from the software raid mailing list.

Disk sdb and partition sdb3 had the same superblock which confused things when rebooting the machine. 

Cure was to delete the superblock on sdb.

---

