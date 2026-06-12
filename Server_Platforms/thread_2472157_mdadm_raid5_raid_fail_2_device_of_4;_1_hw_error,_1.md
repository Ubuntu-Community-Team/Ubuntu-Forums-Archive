---
title: "mdadm: raid5: raid fail 2 device of 4; 1 hw error, 1 in faulty, md0 in read-only"
date: 2022-02-19
forum: Server Platforms
---

### Post by fmartelli on 2022-02-19
mdadm: recovered raid5 fault 2 device of 4; 1 hw error, 1 in faulty, md0 in read-only


my array /etc/mdadm/mdadm.conf


```
ARRAY /dev/md0  level=raid5 metadata=1.2 num-devices=4 UUID=7d22e134:684f07be:0cf75a1a:1116488f name=wright:0 devices=/dev/sdb1,/dev/sdc1,/dev/sdd1,/dev/sde1
```


hd dimension 4TB each


the array is normally backuped to /dev/sdf1 (hd 12TB)


during the weekend, a fault happened on my host.
/dev/sdc1 hw error and don't works anymore
/dev/sdd1 have got an error and the raid put it in "faulty"
after this /dev/md0 went in "read-only" status




```
syslog.4:wright kernel: [2683065.797483] sd 1:0:0:0: [sdc] tag#0 FAILED Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
syslog.4:wright kernel: [2683065.797487] sd 1:0:0:0: [sdc] tag#0 Sense Key : Medium Error [current] 
syslog.4:wright kernel: [2683065.797491] sd 1:0:0:0: [sdc] tag#0 Add. Sense: Unrecovered read error
syslog.4:wright kernel: [2683065.797496] sd 1:0:0:0: [sdc] tag#0 CDB: Read(16) 88 00 00 00 00 00 cd 54 38 00 00 00 04 00 00 00
syslog.4:wright kernel: [2683065.797499] print_req_error: I/O error, dev sdc, sector 3444848640
```




```
wright kernel: [2923496.679481] md/raid:md0: Disk failure on sdd1, disabling device.
wright kernel: [2923496.679481] md/raid:md0: Operation continuing on 3 devices.
wright kernel: [2923496.679509] md/raid:md0: Disk failure on sdc1, disabling device.
wright kernel: [2923496.679509] md/raid:md0: Operation continuing on 2 devices.
```


```
wright kernel: [2922712.958439] print_req_error: I/O error, dev sdc, sector 1743580816
......
wright kernel: [2923496.410136] print_req_error: I/O error, dev sdc, sector 1828395872
wright kernel: [2923496.679509] md/raid:md0: Disk failure on sdc1, disabling device.
root@wright:/var/log# grep " sdd" kern.log.2
wright kernel: [2923496.408739] print_req_error: I/O error, dev sdd, sector 1828386656
wright kernel: [2923496.409032] print_req_error: I/O error, dev sdd, sector 1828387680
wright kernel: [2923496.409389] print_req_error: I/O error, dev sdd, sector 1828388704
wright kernel: [2923496.409696] print_req_error: I/O error, dev sdd, sector 1828389728
wright kernel: [2923496.409985] print_req_error: I/O error, dev sdd, sector 1828390752
wright kernel: [2923496.679481] md/raid:md0: Disk failure on sdd1, disabling device.
```




After crash this is the mdadm --examine (obviously this is the status now and not at the moment of the crash but very similar.




```
mdadm -E /dev/sd[b-e]1
/dev/sdb1:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x1
     Array UUID : 7d22e134:684f07be:0cf75a1a:1116488f
           Name : wright:0  (local to host wright)
  Creation Time : Mon Sep  2 03:10:55 2019
     Raid Level : raid5
   Raid Devices : 4


 Avail Dev Size : 7813771264 (3725.90 GiB 4000.65 GB)
     Array Size : 11720656896 (11177.69 GiB 12001.95 GB)
    Data Offset : 262144 sectors
   Super Offset : 8 sectors
   Unused Space : before=262064 sectors, after=0 sectors
          State : clean
    Device UUID : 3c76e769:2ab88527:d45d4523:48294f01


Internal Bitmap : 8 sectors from superblock
    Update Time : Wed Feb  9 14:01:33 2022
  Bad Block Log : 512 entries available at offset 24 sectors
       Checksum : f6532f66 - correct
         Events : 80121


         Layout : left-symmetric
     Chunk Size : 512K


   Device Role : Active device 0
   Array State : A.A. ('A' == active, '.' == missing, 'R' == replacing)
/dev/sdd1:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x1
     Array UUID : 7d22e134:684f07be:0cf75a1a:1116488f
           Name : wright:0  (local to host wright)
  Creation Time : Mon Sep  2 03:10:55 2019
     Raid Level : raid5
   Raid Devices : 4


 Avail Dev Size : 7813771264 (3725.90 GiB 4000.65 GB)
     Array Size : 11720656896 (11177.69 GiB 12001.95 GB)
    Data Offset : 262144 sectors
   Super Offset : 8 sectors
   Unused Space : before=262056 sectors, after=0 sectors
          State : clean
    Device UUID : 1a01a024:f9d07565:5b99f7af:09372b41


Internal Bitmap : 8 sectors from superblock
    Update Time : Wed Feb  9 14:01:33 2022
  Bad Block Log : 512 entries available at offset 72 sectors
       Checksum : bb8a1c89 - correct
         Events : 80121


         Layout : left-symmetric
     Chunk Size : 512K


   Device Role : Active device 2
   Array State : A.A. ('A' == active, '.' == missing, 'R' == replacing)
/dev/sde1:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x1
     Array UUID : 7d22e134:684f07be:0cf75a1a:1116488f
           Name : wright:0  (local to host wright)
  Creation Time : Mon Sep  2 03:10:55 2019
     Raid Level : raid5
   Raid Devices : 4


 Avail Dev Size : 7813771264 (3725.90 GiB 4000.65 GB)
     Array Size : 11720656896 (11177.69 GiB 12001.95 GB)
    Data Offset : 262144 sectors
   Super Offset : 8 sectors
   Unused Space : before=262064 sectors, after=0 sectors
          State : active
    Device UUID : d4924810:2741feba:5e20360b:da2cfeec


Internal Bitmap : 8 sectors from superblock
    Update Time : Wed Feb  9 14:01:16 2022
  Bad Block Log : 512 entries available at offset 24 sectors
       Checksum : 3cb9b07 - correct
         Events : 80116


         Layout : left-symmetric
     Chunk Size : 512K


   Device Role : Active device 3
   Array State : A.AA ('A' == active, '.' == missing, 'R' == replacing)
```


After read a lot of documentation and forum
[https://raid.wiki.kernel.org/index.php/Linux_Raid](https://raid.wiki.kernel.org/index.php/Linux_Raid)
[https://raid.wiki.kernel.org/index.php/RAID_superblock_formats](https://raid.wiki.kernel.org/index.php/RAID_superblock_formats)
[https://kevin.deldycke.com/2007/03/how-to-recover-a-raid-array-after-having-zero-ized-superblocks/](https://kevin.deldycke.com/2007/03/how-to-recover-a-raid-array-after-having-zero-ized-superblocks/)
[https://lists.debian.org/debian-user-french/2006/03/msg00607.html](https://lists.debian.org/debian-user-french/2006/03/msg00607.html) (this is french)


all command made "mdadm --assembly" didn't assembly the array
probably the superblock of /dev/sdd1 is corrupted and the tentative to clean or force didn't work correctly




and I have made a possible "safe" path to recover raid


.) I have got an external NAS with a bigger capacity (my actual raid is "old")
.) ddrescue of each raid device to file image
```
ddrescue -f -n /dev/sdb /store0/raid/disk0.dd /root/ddr_disk0.log
ddrescue -f -n /dev/sdc /store0/raid/disk1.dd /root/ddr_disk1.log (this is didn't work, hw fail)
ddrescue -f -n /dev/sdd /store0/raid/disk2.dd /root/ddr_disk2.log
ddrescue -f -n /dev/sde /store0/raid/disk3.dd /root/ddr_disk3.log
```
.) disable /dev/md0 on mdadm.conf
.) creation of loop device to use the image files instead of original devices
```
losetup -P /dev/loop0 /store0/raid/disk0.dd
losetup -P /dev/loop2 /store0/raid/disk2.dd
losetup -P /dev/loop3 /store0/raid/disk3.dd
```
.) the command that probably solve my issue (recreation of the superblock on each device) must have the same number of devices (4 in my case)
mdadm --create /dev/md0 --verbose --assume-clean --level=5 --raid-devices=4 /dev/loop0p1 "missed" /dev/loop2p1 /dev/loop3p1 
.) using a qcow2 image with the same virtual dimension of the /dev/sdc I can execute the command above with the device
follow [https://unix.stackexchange.com/questions/268460/how-to-mount-qcow2-image](https://unix.stackexchange.com/questions/268460/how-to-mount-qcow2-image) and adapt the commands


```
qemu-img create -f qcow2 /store0/raid/disk1.qcow2 3815448M  
```


the number of MB is the dimension of the original disk that have got from /dev/sdd rounded up


```
fdisk -l /dev/sdd
Disk /dev/sdd: 3,7 TiB, 4000787030016 bytes, 7814037168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: gpt
Disk identifier: BCA87C1B-96D4-41CD-9691-7FC201DEFBD0


Device     Start        End    Sectors  Size Type
/dev/sdd1   2048 7814035455 7814033408  3,7T Linux RAID
```


with the nbd commands
```
modprobe nbd max_part=63
qemu-nbd --connect=/dev/nbd1 /store0/raid/disk1.qcow2
```


and with 
```
dd if=/dev/sdd of=/dev/nbd1 bs=4096 count=1
```


have copied the partition table from /dev/sdd


```
fdisk /dev/nbd1 -l
The backup GPT table is corrupt, but the primary appears OK, so that will be used.
Disk /dev/nbd1: 3,7 TiB, 4000787202048 bytes, 7814037504 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: gpt
Disk identifier: D6F861EC-0808-4418-874A-9B34B5102144


Device      Start        End    Sectors  Size Type
/dev/nbd1p1  2048 7814035455 7814033408  3,7T Linux RAID
```


that now have the same dimension of the original /dev/sdc


```
stop ndb and reconnect
qemu-nbd --disconnect /dev/nbd1
qemu-nbd --connect=/dev/nbd1 /store0/raid/disk1.qcow2
```


list of the images of the raid
```
-rw-r--r-- 1 root root 4000787030016 feb 19 07:32 disk0.dd
-rw-r--r-- 1 root root       2686976 feb 19 03:16 disk1.qcow2
-rw-r--r-- 1 root root 4000787030016 feb 19 07:32 disk2.dd
-rw-r--r-- 1 root root 4000787030016 feb 19 07:32 disk3.dd
```


now I have all 4 devices


.) check all partitions


```
lsblk -f
NAME      FSTYPE            LABEL    UUID                                 MOUNTPOINT
loop0                                                                     
&#9492;&#9472;loop0p1 linux_raid_member wright:0 7d22e134-684f-07be-0cf7-5a1a1116488f 
loop2                                                                     
&#9492;&#9472;loop2p1 linux_raid_member wright:0 7d22e134-684f-07be-0cf7-5a1a1116488f 
loop3                                                                     
&#9492;&#9472;loop3p1 linux_raid_member wright:0 7d22e134-684f-07be-0cf7-5a1a1116488f 
nbd1                                                                      
&#9492;&#9472;nbd1p1                                                                  


sdb                                                                       
&#9492;&#9472;sdb1    linux_raid_member wright:0 7d22e134-684f-07be-0cf7-5a1a1116488f 
sdc                                                                       
sdd                                                                       
&#9492;&#9472;sdd1    linux_raid_member wright:0 7d22e134-684f-07be-0cf7-5a1a1116488f 
sde                                                                       
&#9492;&#9472;sde1    linux_raid_member wright:0 7d22e134-684f-07be-0cf7-5a1a1116488f 
```




.) recreate the superblock of each devices
```
mdadm --create /dev/md0 --verbose --assume-clean --level=5 --raid-devices=4 /dev/loop0p1 /dev/nbd1p1 /dev/loop2p1 /dev/loop3p1
```


```
mdadm -D /dev/md0
/dev/md0:
        Version : 1.2
  Creation Time : Sat Feb 19 03:05:25 2022
     Raid Level : raid5
     Array Size : 11720656896 (11177.69 GiB 12001.95 GB)
  Used Dev Size : 3906885632 (3725.90 GiB 4000.65 GB)
   Raid Devices : 4
  Total Devices : 4
    Persistence : Superblock is persistent


  Intent Bitmap : Internal


    Update Time : Sat Feb 19 03:05:25 2022
          State : clean 
 Active Devices : 4
Working Devices : 4
 Failed Devices : 0
  Spare Devices : 0


         Layout : left-symmetric
     Chunk Size : 512K


           Name : wright:0  (local to host wright)
           UUID : babffb21:05a5f33f:0d1d07ca:53d1aff9
         Events : 0


    Number   Major   Minor   RaidDevice State
       0     259        0        0      active sync   /dev/loop0p1
       1      43       65        1      active sync   /dev/nbd1p1
       2     259        1        2      active sync   /dev/loop2p1
       3     259        2        3      active sync   /dev/loop3p1
```


cat /proc/mdstat 
```
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md0 : active raid5 loop3p1[3] loop2p1[2] nbd1p1[1] loop0p1[0]
      11720656896 blocks super 1.2 level 5, 512k chunk, algorithm 2 [4/4] [UUUU]
      bitmap: 0/30 pages [0KB], 65536KB chunk


unused devices: <none>
```


.) but the device 2 has empty and need to be change the status to "faulty" assuming that
original devices
```
/dev/sdb1   OK
/dev/sdc1   HW ERROR (no more usable)
/dev/sdd1   superblock corrupted (but data on it)
/dev/sde1   OK
```




```
mdadm /dev/md0 -f /dev/nbd1p1
mdadm: set /dev/nbd1p1 faulty in /dev/md0
root@wright:/store0/raid# mdadm --detail /dev/md0
/dev/md0:
        Version : 1.2
  Creation Time : Sat Feb 19 03:05:25 2022
     Raid Level : raid5
     Array Size : 11720656896 (11177.69 GiB 12001.95 GB)
  Used Dev Size : 3906885632 (3725.90 GiB 4000.65 GB)
   Raid Devices : 4
  Total Devices : 4
    Persistence : Superblock is persistent


  Intent Bitmap : Internal


    Update Time : Sat Feb 19 03:25:03 2022
          State : clean, degraded 
 Active Devices : 3
Working Devices : 3
 Failed Devices : 1
  Spare Devices : 0


         Layout : left-symmetric
     Chunk Size : 512K


           Name : wright:0  (local to host wright)
           UUID : babffb21:05a5f33f:0d1d07ca:53d1aff9
         Events : 4


    Number   Major   Minor   RaidDevice State
       0     259        0        0      active sync   /dev/loop0p1
       -       0        0        1      removed
       2     259        1        2      active sync   /dev/loop2p1
       3     259        2        3      active sync   /dev/loop3p1


       1      43       65        -      faulty   /dev/nbd1p1
```


cat /proc/mdstat
```
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md0 : active raid5 loop3p1[3] loop2p1[2] nbd1p1[1](F) loop0p1[0]
      11720656896 blocks super 1.2 level 5, 512k chunk, algorithm 2 [4/3] [U_UU]
      bitmap: 30/30 pages [120KB], 65536KB chunk


unused devices: <none>
```


.) using testdisk to verifiy the filesystem and so on on /dev/md0
the partition seems ok, but testdisk 
```
Disk /dev/md0 - 12 TB / 10 TiB - CHS 2930164224 2 4


     Partition                  Start        End    Size in sectors


  ext4                     0   0  1 2930164223   1  4 23441313792
superblock 0, blocksize=4096 []
superblock 32768, blocksize=4096 []
superblock 98304, blocksize=4096 []
superblock 163840, blocksize=4096 []
superblock 229376, blocksize=4096 []
superblock 294912, blocksize=4096 []
superblock 819200, blocksize=4096 []
superblock 884736, blocksize=4096 []
superblock 1605632, blocksize=4096 []
superblock 2654208, blocksize=4096 []


To repair the filesystem using alternate superblock, run
fsck.ext4 -p -b superblock -B blocksize device
```


and the relative commands is (my filesystem is ext4)


```
fsck.ext4 -p -b 32768 -B 4096 /dev/md0
/dev/md0 was not cleanly unmounted, check forced.
/dev/md0: Inode 7, i_blocks is 101256, should be 124808.  FIXED.
/dev/md0: Inode 13 extent tree (at level 2) could be narrower.  IGNORED.
/dev/md0: Inode 354681684 extent tree (at level 1) could be narrower.  IGNORED.
/dev/md0: Inode 354681815 extent tree (at level 1) could be narrower.  IGNORED.
/dev/md0: Inode 354681848 extent tree (at level 1) could be narrower.  IGNORED.
/dev/md0: Inode 354681993 extent tree (at level 1) could be narrower.  IGNORED.
/dev/md0: Inode 354682000 extent tree (at level 1) could be narrower.  IGNORED.
/dev/md0: Inode 354682011 extent tree (at level 2) could be narrower.  IGNORED.
/dev/md0: Inode 354682096 extent tree (at level 1) could be narrower.  IGNORED.
/dev/md0: Inode 354682162 extent tree (at level 1) could be narrower.  IGNORED.
/dev/md0: Inode 354682588 extent tree (at level 1) could be narrower.  IGNORED.
/dev/md0: Inode 354682590 extent tree (at level 1) could be narrower.  IGNORED.
/dev/md0: Inode 354682596 extent tree (at level 1) could be narrower.  IGNORED.
/dev/md0: Inode 354682618 extent tree (at level 1) could be narrower.  IGNORED.
/dev/md0: Inode 354682622 extent tree (at level 2) could be narrower.  IGNORED.
/dev/md0: Inode 354682638 extent tree (at level 1) could be narrower.  IGNORED.
/dev/md0: Inode 354682763 extent tree (at level 2) could be narrower.  IGNORED.
/dev/md0: 646386/366272512 files (6.8% non-contiguous), 1313614629/2930164224 blocks
```


.) WELL DONE, mount /dev/md0 
```
/dev/md0                       11627190512  5160992132 5880149152  47% /store1
```

---

### Post by MAFoElffen on 2022-02-19
Dang... Please go back to your post and edit it to wrap your output within CODE TAGs. One, it is very hard to read the post. Second, raw output sometimes does terrible things to the Forums system.

The easiest way to do that is "Edit Post" > Advanced. Select/Highlight the output with your mouse. Press the ICON "#" in the toolbar... Preview to make sure what it looks like. Save.

---

### Post by CharlesA on 2022-02-19
I would verify the data on the array against the data from the last backup, as normally losing 2 disks in a RAID 5 will kill the entire array.

It looks like you recreated the array from disk images of the existing disks, but I'm not exactly sure what the point of that was. You should have replaced the failing drive(s), recreated the array and restored from backups.

---

### Post by fmartelli on 2022-02-20
> **CharlesA said:**
> I would verify the data on the array against the data from the last backup, as normally losing 2 disks in a RAID 5 will kill the entire array.

It looks like you recreated the array from disk images of the existing disks, but I'm not exactly sure what the point of that was. You should have replaced the failing drive(s), recreated the array and restored from backups.

in this case, the starting situation was:
1) a very old array (already changed 2 HD with hw error in two different time)
2) I have the backup but I examinated the status of the disk and starting with

/dev/sdb1   OK
/dev/sdc1   HW ERROR (no more usable)
/dev/sdd1   faulty superblock corrupted (but data on it)
/dev/sde1   OK

and the disk in faulty was disconnected when the other disk stop for HW error
and seems only or "superblock corrupted" or "not synced" but mdadm does't dover this situation or not described in detail to solve the situation.
I wasn't in critical situation but I should try to extract data from the array in fault
and probably the way described in this post can be usefull for anyone in a more critical situation than mine.

in the same time I have renew the array with a new one NAS bigger and now I can reuse the old one for other use.

---

### Post by fmartelli on 2022-02-20
thanks so much to [MAFoElffen]("https://ubuntuforums.org/member.php?u=1044547")[COLOR=#000000] .and the edit of CharlesA[/COLOR]

---

