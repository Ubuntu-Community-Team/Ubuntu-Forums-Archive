---
title: "Slightly different RAID5 / madadm / LSI failure"
date: 2017-01-01
forum: Server Platforms
---

### Post by annndy on 2017-01-01
Hey,

Hoping someone can help me with a slight (fairly catastrophic) issue I have with mdadm - I have a ten 2TB drives RAID5 running across two LSI cards (off the top of my head I'd say they're 9220-8i's but it's been a while and probably doesn't matter). I noticed that I wasn't able to access my data, but could browse the FS no problems.

```

server:~$ cd /tank/
server:/tank$ ls -l
total 48
drwxrwxr-x   4 user user  4096 Jun 10  2016 data1
drwx------   2 root root 16384 Jun  9  2016 lost+found
drwxrwxr-x 155 user user 12288 Dec 29 20:24 data2
drwxrwxr-x 183 user user  4096 Dec  9 15:47 data3
drwxrwxr-x 116 user user  4096 Dec 26 14:12 data4
drwxrwxr-x   3 user user  4096 Jul 11 22:47 data5
drwxrwxr-x   3 user user  4096 Oct 27 09:27 data6



```

Took a quick look at mdadm --detail on the tank and five of the ten drives are removed, leading me to believe I lost a card.

[B]mdadm --detail /dev/md0
[/B]```

server:/tank$ sudo mdadm --detail /dev/md0
/dev/md0:
        Version : 1.2
  Creation Time : Thu Jun  9 13:17:42 2016
     Raid Level : raid5
     Array Size : 17580432384 (16766.01 GiB 18002.36 GB)
  Used Dev Size : 1953381376 (1862.89 GiB 2000.26 GB)
   Raid Devices : 10
  Total Devices : 5
    Persistence : Superblock is persistent


  Intent Bitmap : Internal

server
    Update Time : Sat Dec 31 11:29:36 2016
          State : clean, FAILED 
 Active Devices : 5
Working Devices : 5
 Failed Devices : 0
  Spare Devices : 0


         Layout : left-symmetric
     Chunk Size : 512K


           Name : server:0  (local to host server)
           UUID : 7d644f5d:09d80ecc:f82459f5:487a91b7
         Events : 4029


    Number   Major   Minor   RaidDevice State
       0       8       17        0      active sync   /dev/sdb1
       1       8       33        1      active sync   /dev/sdc1
       2       8       49        2      active sync   /dev/sdd1
       3       8       65        3      active sync   /dev/sde1
       4       8       81        4      active sync   /dev/sdf1
      10       0        0       10      removed
      12       0        0       12      removed
      14       0        0       14      removed
      16       0        0       16      removed
      18       0        0       18      removed

```

Did a quick reboot to see if they were there (found them all in POST) and hung when trying to auto-mount /dev/md0 during boot, so after #'ing out the fstab line for /dev/md0, I was able to boot again. After getting back up and running with the RAID out of commission, I started poking around, tried a force assemble, etc. to no avail. which is where you guys come in - hoping someone out there knows more than me and isn't going to say the only thing left is to zero the superblock and do a create in the right order, which is my last resort.

Below are the bits and pieces I've tried from all my googling (post reboot).

**mdadm --detail /dev/md0**
```

server:~$ sudo mdadm --detail /dev/md0
/dev/md0:
        Version : 1.2
     Raid Level : raid0
  Total Devices : 10
    Persistence : Superblock is persistent


          State : inactive


           Name : server:0  (local to host server)
           UUID : 7d644f5d:09d80ecc:f82459f5:487a91b7
         Events : 4031


    Number   Major   Minor   RaidDevice


       -       8        1        -        /dev/sda1
       -       8       17        -        /dev/sdb1
       -       8       33        -        /dev/sdc1
       -       8       49        -        /dev/sdd1
       -       8       65        -        /dev/sde1
       -       8       81        -        /dev/sdf1
       -       8       97        -        /dev/sdg1
       -       8      113        -        /dev/sdh1
       -       8      129        -        /dev/sdi1
       -       8      145        -        /dev/sdj1

```


**cat /proc/mdstat**
```

server:~$ cat /proc/mdstat 
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md0 : inactive sdb1[1](S) sde1[4](S) sdc1[2](S) sdd1[3](S) sda1[0](S) sdg1[6](S) sdf1[5](S) sdh1[7](S) sdj1[10](S) sdi1[8](S)
      19533813760 blocks super 1.2
       
unused devices: <none>

```

**sudo mdadm --stop /dev/md0 - stopped to try to do an assemble.**
```

server:~$ sudo mdadm --stop /dev/md0
mdadm: stopped /dev/md0


server:~$ sudo mdadm --detail /dev/md0
/dev/md0:
        Version : 
     Raid Level : raid0
  Total Devices : 0


          State : inactive


    Number   Major   Minor   RaidDevice

```

[B]sudo mdadm --assemble --force --scan --verbose /dev/md0 - you can see that there is a version mismatch on 5 of the drives. Unsure why the inverse of the previously removed drives are now showing as out of date. Would have expected the removed drives to show out of date.
[/B]```

server:~$ sudo mdadm --assemble --force --scan --verbose /dev/md0 --uuid=7d644f5d:09d80ecc:f82459f5:487a91b7
mdadm: looking for devices for /dev/md0
mdadm: /dev/sdg1 is identified as a member of /dev/md0, slot 6.
mdadm: /dev/sdi1 is identified as a member of /dev/md0, slot 8.
mdadm: /dev/sdf1 is identified as a member of /dev/md0, slot 5.
mdadm: /dev/sdh1 is identified as a member of /dev/md0, slot 7.
mdadm: /dev/sdj1 is identified as a member of /dev/md0, slot 9.
mdadm: /dev/sda1 is identified as a member of /dev/md0, slot 0.
mdadm: /dev/sdd1 is identified as a member of /dev/md0, slot 3.
mdadm: /dev/sde1 is identified as a member of /dev/md0, slot 4.
mdadm: /dev/sdb1 is identified as a member of /dev/md0, slot 1.
mdadm: /dev/sdc1 is identified as a member of /dev/md0, slot 2.
mdadm: added /dev/sdb1 to /dev/md0 as 1
mdadm: added /dev/sdc1 to /dev/md0 as 2
mdadm: added /dev/sdd1 to /dev/md0 as 3
mdadm: added /dev/sde1 to /dev/md0 as 4
mdadm: added /dev/sdf1 to /dev/md0 as 5 (possibly out of date)
mdadm: added /dev/sdg1 to /dev/md0 as 6 (possibly out of date)
mdadm: added /dev/sdh1 to /dev/md0 as 7 (possibly out of date)
mdadm: added /dev/sdi1 to /dev/md0 as 8 (possibly out of date)
mdadm: added /dev/sdj1 to /dev/md0 as 9 (possibly out of date)
mdadm: added /dev/sda1 to /dev/md0 as 0
mdadm: /dev/md0 assembled from 5 drives - not enough to start the array.

```

**sudo mdadm --examine /dev/sd[a-j]1 - sdh and sdj have bad blocks, but don't think this is too relevant and will replace one at a time once it's back up**
```

server:~$ sudo mdadm --examine /dev/sd[a-j]1
/dev/sda1:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x1
     Array UUID : 7d644f5d:09d80ecc:f82459f5:487a91b7
           Name : server:0  (local to host server)
  Creation Time : Thu Jun  9 13:17:42 2016
     Raid Level : raid5
   Raid Devices : 10


 Avail Dev Size : 3906762752 (1862.89 GiB 2000.26 GB)
     Array Size : 17580432384 (16766.01 GiB 18002.36 GB)
    Data Offset : 262144 sectors
   Super Offset : 8 sectors
   Unused Space : before=262056 sectors, after=0 sectors
          State : clean
    Device UUID : 840fce75:fc2591a7:6290c072:ed0eb5ad


Internal Bitmap : 8 sectors from superblock
    Update Time : Sat Dec 31 14:01:24 2016
  Bad Block Log : 512 entries available at offset 72 sectors
       Checksum : a438af3f - correct
         Events : 4031


         Layout : left-symmetric
     Chunk Size : 512K


   Device Role : Active device 0
   Array State : AAAAA..... ('A' == active, '.' == missing, 'R' == replacing)
/dev/sdb1:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x1
     Array UUID : 7d644f5d:09d80ecc:f82459f5:487a91b7
           Name : server:0  (local to host server)
  Creation Time : Thu Jun  9 13:17:42 2016
     Raid Level : raid5
   Raid Devices : 10


 Avail Dev Size : 3906762752 (1862.89 GiB 2000.26 GB)
     Array Size : 17580432384 (16766.01 GiB 18002.36 GB)
    Data Offset : 262144 sectors
   Super Offset : 8 sectors
   Unused Space : before=262056 sectors, after=0 sectors
          State : clean
    Device UUID : d805036f:4895200d:d3ccf958:4ab7d378


Internal Bitmap : 8 sectors from superblock
    Update Time : Sat Dec 31 14:01:24 2016
  Bad Block Log : 512 entries available at offset 72 sectors
       Checksum : b454f9ad - correct
         Events : 4031


         Layout : left-symmetric
     Chunk Size : 512K


   Device Role : Active device 1
   Array State : AAAAA..... ('A' == active, '.' == missing, 'R' == replacing)
/dev/sdc1:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x1
     Array UUID : 7d644f5d:09d80ecc:f82459f5:487a91b7
           Name : server:0  (local to host server)
  Creation Time : Thu Jun  9 13:17:42 2016
     Raid Level : raid5
   Raid Devices : 10


 Avail Dev Size : 3906762752 (1862.89 GiB 2000.26 GB)
     Array Size : 17580432384 (16766.01 GiB 18002.36 GB)
    Data Offset : 262144 sectors
   Super Offset : 8 sectors
   Unused Space : before=262056 sectors, after=0 sectors
          State : clean
    Device UUID : 4c7cf77c:e39f347b:e415ef88:44c3f57c


Internal Bitmap : 8 sectors from superblock
    Update Time : Sat Dec 31 14:01:24 2016
  Bad Block Log : 512 entries available at offset 72 sectors
       Checksum : 6474cfc9 - correct
         Events : 4031


         Layout : left-symmetric
     Chunk Size : 512K


   Device Role : Active device 2
   Array State : AAAAA..... ('A' == active, '.' == missing, 'R' == replacing)
/dev/sdd1:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x1
     Array UUID : 7d644f5d:09d80ecc:f82459f5:487a91b7
           Name : server:0  (local to host server)
  Creation Time : Thu Jun  9 13:17:42 2016
     Raid Level : raid5
   Raid Devices : 10


 Avail Dev Size : 3906762752 (1862.89 GiB 2000.26 GB)
     Array Size : 17580432384 (16766.01 GiB 18002.36 GB)
    Data Offset : 262144 sectors
   Super Offset : 8 sectors
   Unused Space : before=262056 sectors, after=0 sectors
          State : clean
    Device UUID : ba7bbfc2:39acfdab:0335bbe4:05ece929


Internal Bitmap : 8 sectors from superblock
    Update Time : Sat Dec 31 14:01:24 2016
  Bad Block Log : 512 entries available at offset 72 sectors
       Checksum : e3c6236e - correct
         Events : 4031


         Layout : left-symmetric
     Chunk Size : 512K


   Device Role : Active device 3
   Array State : AAAAA..... ('A' == active, '.' == missing, 'R' == replacing)
/dev/sde1:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x1
     Array UUID : 7d644f5d:09d80ecc:f82459f5:487a91b7
           Name : server:0  (local to host server)
  Creation Time : Thu Jun  9 13:17:42 2016
     Raid Level : raid5
   Raid Devices : 10


 Avail Dev Size : 3906762752 (1862.89 GiB 2000.26 GB)
     Array Size : 17580432384 (16766.01 GiB 18002.36 GB)
    Data Offset : 262144 sectors
   Super Offset : 8 sectors
   Unused Space : before=262056 sectors, after=0 sectors
          State : clean
    Device UUID : 8ce168b3:71154484:ad87d321:8421b396


Internal Bitmap : 8 sectors from superblock
    Update Time : Sat Dec 31 14:01:24 2016
  Bad Block Log : 512 entries available at offset 72 sectors
       Checksum : 56977aa2 - correct
         Events : 4031


         Layout : left-symmetric
     Chunk Size : 512K


   Device Role : Active device 4
   Array State : AAAAA..... ('A' == active, '.' == missing, 'R' == replacing)
/dev/sdf1:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x1
     Array UUID : 7d644f5d:09d80ecc:f82459f5:487a91b7
           Name : server:0  (local to host server)
  Creation Time : Thu Jun  9 13:17:42 2016
     Raid Level : raid5
   Raid Devices : 10


 Avail Dev Size : 3906762752 (1862.89 GiB 2000.26 GB)
     Array Size : 17580432384 (16766.01 GiB 18002.36 GB)
    Data Offset : 262144 sectors
   Super Offset : 8 sectors
   Unused Space : before=262056 sectors, after=0 sectors
          State : clean
    Device UUID : 5df8cc48:4260dc5d:8e246869:f393ea00


Internal Bitmap : 8 sectors from superblock
    Update Time : Sat Dec 31 11:17:39 2016
  Bad Block Log : 512 entries available at offset 72 sectors
       Checksum : 776cc542 - correct
         Events : 4019


         Layout : left-symmetric
     Chunk Size : 512K


   Device Role : Active device 5
   Array State : AAAAAAAAAA ('A' == active, '.' == missing, 'R' == replacing)
/dev/sdg1:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x1
     Array UUID : 7d644f5d:09d80ecc:f82459f5:487a91b7
           Name : server:0  (local to host server)
  Creation Time : Thu Jun  9 13:17:42 2016
     Raid Level : raid5
   Raid Devices : 10


 Avail Dev Size : 3906762752 (1862.89 GiB 2000.26 GB)
     Array Size : 17580432384 (16766.01 GiB 18002.36 GB)
    Data Offset : 262144 sectors
   Super Offset : 8 sectors
   Unused Space : before=262056 sectors, after=0 sectors
          State : clean
    Device UUID : 89f0dc98:c44dfe02:28a93920:df2bf79d


Internal Bitmap : 8 sectors from superblock
    Update Time : Sat Dec 31 11:17:39 2016
  Bad Block Log : 512 entries available at offset 72 sectors
       Checksum : c07cc777 - correct
         Events : 4019


         Layout : left-symmetric
     Chunk Size : 512K


   Device Role : Active device 6
   Array State : AAAAAAAAAA ('A' == active, '.' == missing, 'R' == replacing)
/dev/sdh1:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x9
     Array UUID : 7d644f5d:09d80ecc:f82459f5:487a91b7
           Name : server:0  (local to host server)
  Creation Time : Thu Jun  9 13:17:42 2016
     Raid Level : raid5
   Raid Devices : 10


 Avail Dev Size : 3906762752 (1862.89 GiB 2000.26 GB)
     Array Size : 17580432384 (16766.01 GiB 18002.36 GB)
    Data Offset : 262144 sectors
   Super Offset : 8 sectors
   Unused Space : before=262056 sectors, after=0 sectors
          State : clean
    Device UUID : 01324242:15bb4e61:56ff222d:3d8d4cd0


Internal Bitmap : 8 sectors from superblock
    Update Time : Sat Dec 31 11:17:39 2016
**  Bad Block Log : 512 entries available at offset 72 sectors - bad blocks present.**
       Checksum : 7712f8e - correct
         Events : 4019


         Layout : left-symmetric
     Chunk Size : 512K


   Device Role : Active device 7
   Array State : AAAAAAAAAA ('A' == active, '.' == missing, 'R' == replacing)
/dev/sdi1:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x1
     Array UUID : 7d644f5d:09d80ecc:f82459f5:487a91b7
           Name : server:0  (local to host server)
  Creation Time : Thu Jun  9 13:17:42 2016
     Raid Level : raid5
   Raid Devices : 10


 Avail Dev Size : 3906762752 (1862.89 GiB 2000.26 GB)
     Array Size : 17580432384 (16766.01 GiB 18002.36 GB)
    Data Offset : 262144 sectors
   Super Offset : 8 sectors
   Unused Space : before=262056 sectors, after=0 sectors
          State : clean
    Device UUID : 04ee2f68:f093445f:90c8d806:0290457b


Internal Bitmap : 8 sectors from superblock
    Update Time : Sat Dec 31 11:17:39 2016
  Bad Block Log : 512 entries available at offset 72 sectors
       Checksum : b0038eab - correct
         Events : 4019


         Layout : left-symmetric
     Chunk Size : 512K


   Device Role : Active device 8
   Array State : AAAAAAAAAA ('A' == active, '.' == missing, 'R' == replacing)
/dev/sdj1:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x9
     Array UUID : 7d644f5d:09d80ecc:f82459f5:487a91b7
           Name : server:0  (local to host server)
  Creation Time : Thu Jun  9 13:17:42 2016
     Raid Level : raid5
   Raid Devices : 10


 Avail Dev Size : 3906762752 (1862.89 GiB 2000.26 GB)
     Array Size : 17580432384 (16766.01 GiB 18002.36 GB)
    Data Offset : 262144 sectors
   Super Offset : 8 sectors
   Unused Space : before=262056 sectors, after=0 sectors
          State : clean
    Device UUID : 3ff8a5c2:916a335a:8b18a170:e73bbe2c


Internal Bitmap : 8 sectors from superblock
    Update Time : Sat Dec 31 11:17:39 2016
**  Bad Block Log : 512 entries available at offset 72 sectors - bad blocks present.**
       Checksum : 20a96b72 - correct
         Events : 4019


         Layout : left-symmetric
     Chunk Size : 512K


   Device Role : Active device 9
   Array State : AAAAAAAAAA ('A' == active, '.' == missing, 'R' == replacing)

```

**sudo mdadm --examine-badblocks /dev/sd[hj]1 - notice they're the same. This came up in another thread that was resolved through kernel patching, but very different scenario (they were hanging during a grow).**
```

server:~$ sudo mdadm --examine-badblocks /dev/sd[hj]1
Bad-blocks on /dev/sdh1:
             6212976 for 128 sectors
            15009384 for 128 sectors
            15070408 for 128 sectors
            15115464 for 128 sectors
Bad-blocks on /dev/sdj1:
             6212976 for 128 sectors
            15009384 for 128 sectors
            15070408 for 128 sectors
            15115464 for 128 sectors


```

**ls -l /dev/sd* - Lastly at one point half the drives disappeared randomly and were brought back after a reboot. I can always see them being detected during POST.**
```

server:~$ ls -l /dev/sd*
brw-rw---- 1 root disk 8,   0 Dec 31 14:29 /dev/sda
brw-rw---- 1 root disk 8,   1 Dec 31 15:01 /dev/sda1
brw-rw---- 1 root disk 8,  16 Dec 31 14:29 /dev/sdb
brw-rw---- 1 root disk 8,  17 Dec 31 15:01 /dev/sdb1
brw-rw---- 1 root disk 8,  32 Dec 31 14:29 /dev/sdc
brw-rw---- 1 root disk 8,  33 Dec 31 15:01 /dev/sdc1
brw-rw---- 1 root disk 8,  48 Dec 31 14:29 /dev/sdd
brw-rw---- 1 root disk 8,  49 Dec 31 15:01 /dev/sdd1
brw-rw---- 1 root disk 8,  64 Dec 31 14:29 /dev/sde
brw-rw---- 1 root disk 8,  65 Dec 31 15:01 /dev/sde1

```

Given that I lost all five drives at once, I have to assume that no further writes were done to the RAID and I can assume it's clean. Is there another way to get it online without zeroing out the superblock as it sounds risky af. I haven't been able to find anything similar where people have lost so many drives at once and the fixes to a single drive being out of date / faulty don't seem to work / apply, so any direction or suggestions would be appreciated.

Cheers and Happy New Year ;)

---

### Post by darkod on 2017-01-01
As you can see in the examine info, the Events counters are slightly different. First 5 disks have 4031 and last 5 have 4019.

Since you already tried --assemble --force one thing you can try now is adding --run to it. If that doesn't work, I'm afraid the only remaining thing is a --create --assume-clean. Be very careful with --create and don't use it without --assume-clean.
If the array is stopped, try:
```
sudo mdadm --assemble --force --run --verbose /dev/md0 /dev/sd[abcdefghij]1
```

See how that goes...

Looks like at one point one of the controllers dropped all disks and that made them out of date. So even though it is recognizing the disks now, the array can't start with so many disks out of date. You should probably be careful and watch if this happens again, maybe the controller is getting ready to die. Hopefully it is presenting the disks stable now because if it not enough to see that the disks are detected, the real thing is when you start writing on them. It might drop them again.

---

### Post by annndy on 2017-01-01
I had already tried --run with the same result as --scan (from [this thread]("http://unix.stackexchange.com/questions/230788/mdadm-dev-md0-assembled-from-3-drives-not-enough-to-start-the-array") with a couple of tips) - I should have mentioned, but they seemed like the same thing. Looks like --create with --assume-clean was the trick. Glad I didn't have to mess with the superblock as I've seen in a few threads. Thank you, you are a scholar and a gentleman!

For reference for anyone else having problems, I hope it helps.

**sudo mdadm --create /dev/md0 --level=5 --raid-devices=10 --assume-clean /dev/sd[a-j]1 - I'm pretty sure you need to put the /dev/sd's in the original order, which you can see from sudo mdadm --examine /dev/sd[a-j]1 in the device role section.**
```

server:~$ sudo mdadm --create /dev/md0 --level=5 --raid-devices=10 --assume-clean /dev/sd[a-j]1
mdadm: /dev/sda1 appears to be part of a raid array:
       level=raid5 devices=10 ctime=Thu Jun  9 13:17:42 2016
mdadm: /dev/sdb1 appears to be part of a raid array:
       level=raid5 devices=10 ctime=Thu Jun  9 13:17:42 2016
mdadm: /dev/sdc1 appears to be part of a raid array:
       level=raid5 devices=10 ctime=Thu Jun  9 13:17:42 2016
mdadm: /dev/sdd1 appears to be part of a raid array:
       level=raid5 devices=10 ctime=Thu Jun  9 13:17:42 2016
mdadm: /dev/sde1 appears to be part of a raid array:
       level=raid5 devices=10 ctime=Thu Jun  9 13:17:42 2016
mdadm: /dev/sdf1 appears to be part of a raid array:
       level=raid5 devices=10 ctime=Thu Jun  9 13:17:42 2016
mdadm: /dev/sdg1 appears to be part of a raid array:
       level=raid5 devices=10 ctime=Thu Jun  9 13:17:42 2016
mdadm: /dev/sdh1 appears to be part of a raid array:
       level=raid5 devices=10 ctime=Thu Jun  9 13:17:42 2016
mdadm: /dev/sdi1 appears to be part of a raid array:
       level=raid5 devices=10 ctime=Thu Jun  9 13:17:42 2016
mdadm: /dev/sdj1 appears to be part of a raid array:
       level=raid5 devices=10 ctime=Thu Jun  9 13:17:42 2016
Continue creating array? y
mdadm: Defaulting to version 1.2 metadata
mdadm: array /dev/md0 started.

```

[B]sudo mdadm --detail /dev/md0 - Note the new UUID
[/B]```

server:~$ sudo mdadm --detail /dev/md0
/dev/md0:
        Version : 1.2
  Creation Time : Mon Jan  2 08:23:41 2017
     Raid Level : raid5
     Array Size : 17580432384 (16766.01 GiB 18002.36 GB)
  Used Dev Size : 1953381376 (1862.89 GiB 2000.26 GB)
   Raid Devices : 10
  Total Devices : 10
    Persistence : Superblock is persistent


  Intent Bitmap : Internal


    Update Time : Mon Jan  2 08:23:41 2017
          State : clean 
 Active Devices : 10
Working Devices : 10
 Failed Devices : 0
  Spare Devices : 0


         Layout : left-symmetric
     Chunk Size : 512K


           Name : server:0  (local to host server)
           UUID : 3a23043d:8714045a:4f1f03ab:fed33281
         Events : 0


    Number   Major   Minor   RaidDevice State
       0       8        1        0      active sync   /dev/sda1
       1       8       17        1      active sync   /dev/sdb1
       2       8       33        2      active sync   /dev/sdc1
       3       8       49        3      active sync   /dev/sdd1
       4       8       65        4      active sync   /dev/sde1
       5       8       81        5      active sync   /dev/sdf1
       6       8       97        6      active sync   /dev/sdg1
       7       8      113        7      active sync   /dev/sdh1
       8       8      129        8      active sync   /dev/sdi1
       9       8      145        9      active sync   /dev/sdj1

```

**sudo mount /dev/md0 /tank**
```

server:~$ sudo mount /dev/md0 /tank
server:~$ cd /tank/
server:/tank$ ls -l
total 48
drwxrwxr-x   4 user user  4096 Jun 10  2016 data1
drwx------   2 root root 16384 Jun  9  2016 lost+found
drwxrwxr-x 155 user user 12288 Dec 29 20:24 data2
drwxrwxr-x 183 user user  4096 Dec  9 15:47 data3
drwxrwxr-x 116 user user  4096 Dec 26 14:12 data4
drwxrwxr-x   3 user user  4096 Jul 11 22:47 data5
drwxrwxr-x   3 user user  4096 Oct 27 09:27 data6

```

**Lastly, need to do something like this to update the UUID in the conf file, but I hand edited my mdadm.conf and removed the # from fstab**
```

mdadm --examine --scan >> /etc/mdadm/mdadm.conf

```

---

