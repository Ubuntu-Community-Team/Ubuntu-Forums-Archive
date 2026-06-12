---
title: "Linux Software raid help"
date: 2011-06-15
forum: Server Platforms
---

### Post by 0bit on 2011-06-15
Hi Guys and girls,

I have set up a software raid a little while ago. Today I noticed that one of my drives is not behaving.

[HTML][ 6924.748836] end_request: I/O error, dev sdc, sector 1953519927
[ 6924.748986] sd 3:0:0:0: [sdc] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK,SUGGEST_OK
[ 6924.748990] end_request: I/O error, dev sdc, sector 575
[/HTML]I'd like to bring the raid up using the other one only. But I get this:
[HTML]cris@playground:~$ sudo mdadm -E /dev/sdb1
/dev/sdb1:
          Magic : a92b4efc
        Version : 00.90.00
           UUID : e33ce429:7c983328:0e4391d1:54aac046
  Creation Time : Mon Sep 22 22:44:28 2008
     Raid Level : raid1
  Used Dev Size : 976759936 (931.51 GiB 1000.20 GB)
     Array Size : 976759936 (931.51 GiB 1000.20 GB)
   Raid Devices : 2
  Total Devices : 2
Preferred Minor : 0

    Update Time : Wed Jun 15 00:31:10 2011
          State : clean
 Active Devices : 1
Working Devices : 2
 Failed Devices : 0
  Spare Devices : 1
       Checksum : 3d0199a4 - correct
         Events : 332582


      Number   Major   Minor   RaidDevice State
this     2       8       17        2      spare   /dev/sdb1

   0     0       0        0        0      removed
   1     1       8       33        1      active sync   /dev/sdc1
   2     2       8       17        2      spare   /dev/sdb1
[/HTML][HTML]cris@playground:~$ sudo mdadm -A /mnt/md0 /dev/sdb1
mdadm: No suitable drives found for /mnt/md0
[/HTML]Please help me recover the data. I have all the semi-pro pictures since 2007 on there (1TB)...

Thanks!
PS: I have read this thread: [http://ubuntuforums.org/showthread.php?t=1707416](http://ubuntuforums.org/showthread.php?t=1707416) but it didn't help me.
PPS: Raid was creating following: [http://ubuntuforums.org/showthread.php?t=408461](http://ubuntuforums.org/showthread.php?t=408461)

UPDATE:
Can someone help me by answering these questions:

- in Raid 1 (which is what I have) does having a spare drive mean the data is written only on 1 drive and then if that fails it's mirrored or both of my drives have the data?

---

### Post by Lars Noodén on 2011-06-15
> **0bit said:**
> 
Can someone help me by answering these questions:

- in Raid 1 (which is what I have) does having a spare drive mean the data is written only on 1 drive and then if that fails it's mirrored or both of my drives have the data?

RAID 1 means that the data is mirrored on all drives in the array.  If one fails, when the drive is replaced the new drive receives a full copy of the data as it becomes part of the array.

---

### Post by gurgelsmurf on 2011-06-15
Have a look at this link, especially the Event part.
[http://kevin.deldycke.com/2008/07/heroic-journey-to-raid-5-data-recovery/]("http://kevin.deldycke.com/2008/07/heroic-journey-to-raid-5-data-recovery/")

My guess is that if the event numbers don't match then the drive is actually broken and should be replaced.

---

### Post by 0bit on 2011-06-15
Thanks guys.

Following the guide from gurgelsmurf, I was able to mount the raid using sdb1 only.

However, now I'm getting this:
```
cris@playground:~$ dmesg | tail
[  459.988273] Buffer I/O error on device sdb1, logical block 976759937
[  459.988276] Buffer I/O error on device sdb1, logical block 976759938
[  459.988279] Buffer I/O error on device sdb1, logical block 976759939
[  459.988300] sd 1:0:0:0: [sdb] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK,SUGGEST_OK
[  459.988303] end_request: I/O error, dev sdb, sector 1953519935
[  459.988306] Buffer I/O error on device sdb1, logical block 976759936
[  459.989874] sd 1:0:0:0: [sdb] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK,SUGGEST_OK
[  459.989878] end_request: I/O error, dev sdb, sector 63
[  459.989904] sd 1:0:0:0: [sdb] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK,SUGGEST_OK
[  459.989908] end_request: I/O error, dev sdb, sector 63

```So does that mean that both of my drives are bad? Sounds fishy!

BTW, fsck /dev/md0 returned clean...

BTW, you where right for the events, sdb1 had a much higher number than sdc1...

---

### Post by 0bit on 2011-06-15
"Following the guide" is a little vague.

Here is what I did:

```

- stopped the md0 with : sudo mdadm --stop /dev/md0
- recreated it using: sudo mdadm --create /dev/md0 --assume-clean --level=1 --verbose --raid-devices=3 /dev/sdb1 missing /dev/sdc1- sudo mdadm --manage --set-faulty /dev/md0 /dev/sdc1
- sudo mdadm /dev/md0 -r /dev/sdc1
- sudo fdsk /dev/md0
- sudo mount /mnt/raid 
- tried to copy files sudo cp -R Pictures ../back/ (where a brand new drive is mounted
- got all the I/O errors

```

---

