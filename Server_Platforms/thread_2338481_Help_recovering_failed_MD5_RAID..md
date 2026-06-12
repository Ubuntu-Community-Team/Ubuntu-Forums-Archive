---
title: "Help recovering failed MD5 RAID."
date: 2016-09-28
forum: Server Platforms
---

### Post by Bushflyr on 2016-09-28
I had a 4 disk mdadm RAID 5 running on my old server when the motherboard failed. It was old enough that no replacement mobo's are available. I built a new system and moved the disks into it and am now trying to recover the data. 

I've tried everything in the other threads up to zeroing the superblock on sdc (SB is missing on sdb1, sdd1, and sde1).

```
@DESKTOP-7UFBOTC:~$ sudo mdadm -E /dev/sdb
/dev/sdb:
   MBR Magic : aa55
Partition[0] :   3907029167 sectors at            1 (type ee)
scot@DESKTOP-7UFBOTC:~$ sudo mdadm -E /dev/sdc
/dev/sdc:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x0
     Array UUID : d620348e:49dc546a:3fad1f25:794ccd17
           Name : mars.local:Mars
  Creation Time : Sun Nov 11 11:34:51 2012
     Raid Level : raid5
   Raid Devices : 4

 Avail Dev Size : 3907027120 (1863.02 GiB 2000.40 GB)
     Array Size : 5860538880 (5589.05 GiB 6001.19 GB)
  Used Dev Size : 3907025920 (1863.02 GiB 2000.40 GB)
    Data Offset : 2048 sectors
   Super Offset : 8 sectors
   Unused Space : before=1968 sectors, after=1200 sectors
          State : clean
    Device UUID : ec241702:f4cd403b:3b54cabf:f9c455b5

    Update Time : Tue Oct 13 19:55:33 2015
       Checksum : 2d6fa7b5 - correct
         Events : 104333

         Layout : left-symmetric
     Chunk Size : 512K

   Device Role : Active device 3
   Array State : AAAA ('A' == active, '.' == missing, 'R' == replacing)

```

Then I tried 

```
@DESKTOP-7UFBOTC:~$ sudo mdadm --assemble /dev/md127 /dev/sdc /dev/sdd1 /dev/sde1 --force
mdadm: no RAID superblock on /dev/sdd1
mdadm: /dev/sdd1 has no superblock - assembly aborted


```


lsblk gives
```
@DESKTOP-7UFBOTC:~$ lsblk
NAME   MAJ:MIN RM   SIZE RO TYPE MOUNTPOINT
sda      8:0    0   3.7T  0 disk 
&#9500;&#9472;sda1   8:1    0     1M  0 part 
&#9500;&#9472;sda2   8:2    0   3.6T  0 part /
&#9492;&#9472;sda3   8:3    0  31.9G  0 part [SWAP]
sdb      8:16   0   1.8T  0 disk 
&#9492;&#9472;sdb1   8:17   0   1.8T  0 part 
sdc      8:32   0   1.8T  0 disk 
sdd      8:48   0   1.8T  0 disk 
&#9492;&#9472;sdd1   8:49   0   1.8T  0 part 
sde      8:64   0   1.8T  0 disk 
&#9492;&#9472;sde1   8:65   0   1.8T  0 part 
sdf      8:80   0 111.8G  0 disk 
&#9500;&#9472;sdf1   8:81   0   450M  0 part 
&#9500;&#9472;sdf2   8:82   0   100M  0 part 
&#9500;&#9472;sdf3   8:83   0    16M  0 part 
&#9492;&#9472;sdf4   8:84   0 111.2G  0 part 
scot@DESKTOP-7UFBOTC:~$ sudo cat /proc/mdstat
Personalities : [raid6] [raid5] [raid4] 
md127 : inactive sdc[5](S)
      1953513560 blocks super 1.2
       
unused devices: <none>


```

Where sda is my boot drive, sdb,c,d, & e are the RAID drives and sdf is my Windows ssd.

Is this recoverable? Or am I screwed? TIA

---

### Post by darkod on 2016-09-28
First you need to recall whether you used the disk label to create the array (like sdb, sdc) or the partitions (like sdb1, sdc1)... If you don't remember look for SB on both:
```
sudo mdadm -E /dev/sd[bcde]
sudo mdadm -E /dev/sd[bcde]1
```

After you post the output of that we can discuss what to do. And be careful, don't try running commands you don't understand just because you found them in google search. Maybe the array is perfectly fine and you can easily lose it by running wrong mdadm commands.

---

### Post by Bushflyr on 2016-09-28
Thanks for the reply, heres the output of those. I think originally I created it on the partition, but it has been a while.

```
mdadm -E /dev/sd[bcde]
/dev/sdb:
   MBR Magic : aa55
Partition[0] :   3907029167 sectors at            1 (type ee)
/dev/sdc:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x0
     Array UUID : d620348e:49dc546a:3fad1f25:794ccd17
           Name : mars.local:Mars
  Creation Time : Sun Nov 11 11:34:51 2012
     Raid Level : raid5
   Raid Devices : 4

 Avail Dev Size : 3907027120 (1863.02 GiB 2000.40 GB)
     Array Size : 5860538880 (5589.05 GiB 6001.19 GB)
  Used Dev Size : 3907025920 (1863.02 GiB 2000.40 GB)
    Data Offset : 2048 sectors
   Super Offset : 8 sectors
   Unused Space : before=1968 sectors, after=1200 sectors
          State : clean
    Device UUID : ec241702:f4cd403b:3b54cabf:f9c455b5

    Update Time : Tue Oct 13 19:55:33 2015
       Checksum : 2d6fa7b5 - correct
         Events : 104333

         Layout : left-symmetric
     Chunk Size : 512K

   Device Role : Active device 3
   Array State : AAAA ('A' == active, '.' == missing, 'R' == replacing)
/dev/sdd:
   MBR Magic : aa55
Partition[0] :   3907029167 sectors at            1 (type ee)
/dev/sde:
   MBR Magic : aa55
Partition[0] :   3907029167 sectors at            1 (type ee)
root@DESKTOP-7UFBOTC:/home/xxxx# mdadm -E /dev/sd[bcde]1
mdadm: No md superblock detected on /dev/sdb1.
mdadm: No md superblock detected on /dev/sdd1.
mdadm: No md superblock detected on /dev/sde1.
root@DESKTOP-7UFBOTC:/home/# 


```

---

### Post by darkod on 2016-09-28
How did you end up with no SB except on one member? As it is, it will not assemble because the SB info has been lost. What you could try is --create but using the --assume-clean parameter. Be careful, if you don't use that parameter the --create will create a new blank array.

I see the only SB is on /dev/sdc, so assuming you used disks and not partitions you can try the create with:
```
sudo mdadm --create --assume-clean --verbose --level=raid5 --raid-devices=4 /dev/md0 /dev/sdb /dev/sdc /dev/sdd /dev/sde
```

That should create new array md0 and keep the existing data when using --assume-clean.

---

### Post by Bushflyr on 2016-09-28
OK, cool, that got me a RAID, but it doesn't want to mount. (wrong fs type) 

```
root@DESKTOP-7UFBOTC:/home/asdf# mdadm --create --assume-clean --verbose --level=raid5 --raid-devices=4 /dev/md0 /dev/sdb /dev/sdc /dev/sdd /dev/sde
mdadm: layout defaults to left-symmetric
mdadm: layout defaults to left-symmetric
mdadm: chunk size defaults to 512K
mdadm: /dev/sdb appears to be part of a raid array:
       level=raid0 devices=0 ctime=Wed Dec 31 14:00:00 1969
mdadm: partition table exists on /dev/sdb but will be lost or
       meaningless after creating array
mdadm: /dev/sdc appears to be part of a raid array:
       level=raid5 devices=4 ctime=Sun Nov 11 11:34:51 2012
mdadm: /dev/sdd appears to be part of a raid array:
       level=raid0 devices=0 ctime=Wed Dec 31 14:00:00 1969
mdadm: partition table exists on /dev/sdd but will be lost or
       meaningless after creating array
mdadm: /dev/sde appears to be part of a raid array:
       level=raid0 devices=0 ctime=Wed Dec 31 14:00:00 1969
mdadm: partition table exists on /dev/sde but will be lost or
       meaningless after creating array
mdadm: size set to 1953383424K
mdadm: automatically enabling write-intent bitmap on large array
Continue creating array? yes
mdadm: Defaulting to version 1.2 metadata
mdadm: array /dev/md0 started.

root@DESKTOP-7UFBOTC:/home/asfd# mount /dev/md0 /mnt/
mount: wrong fs type, bad option, bad superblock on /dev/md0,
       missing codepage or helper program, or other error

       In some cases useful info is found in syslog - try
       dmesg | tail or so.

root@DESKTOP-7UFBOTC:/home/asdf# mount /dev/md0 /mnt
mount: wrong fs type, bad option, bad superblock on /dev/md0,
       missing codepage or helper program, or other error

       In some cases useful info is found in syslog - try
       dmesg | tail or so.

root@DESKTOP-7UFBOTC:/home/asdf# cat /proc/mdstat
Personalities : [raid6] [raid5] [raid4] 
md0 : active raid5 sde[3] sdd[2] sdc[1] sdb[0]
      5860150272 blocks super 1.2 level 5, 512k chunk, algorithm 2 [4/4] [UUUU]
      bitmap: 0/15 pages [0KB], 65536KB chunk

unused devices: <none>


```

---

### Post by Bushflyr on 2016-09-28
:popcorn: Sorry, double tap. Posting not playing well right now.

---

### Post by darkod on 2016-09-29
Not recognizing a filesystem might mean you need to assemble the partitions instead of disks. But it could also mean something is wrong with the data.

I am also worried about those messages that raid0 was discovered on sdb, sdd and sde. Basically it said it found raid5 only on sdc.

What you can try next is zeroing the SB and trying to re-create with the partitions:
```
sudo mdadm --stop /dev/md0
sudo mdadm --zero-superblock /dev/sdb
sudo mdadm --zero-superblock /dev/sdc
sudo mdadm --zero-superblock /dev/sdd
sudo mdadm --zero-superblock /dev/sde
sudo mdadm --create --assume-clean --verbose --level=raid5 --raid-devices=4 /dev/md0 /dev/sdb1 /dev/sdc1 /dev/sdd1 /dev/sde1
```

---

### Post by Bushflyr on 2016-09-29
:( That didn't seem to work. Can I mix sd[bde]1 and sdc?

```
asdf@DESKTOP-7UFBOTC:~$ sudo mdadm --stop /dev/md0
mdadm: stopped /dev/md0
asdf@DESKTOP-7UFBOTC:~$ sudo mdadm --zero-superblock /dev/sdb
mdadm: Unrecognised md component device - /dev/sdb
asdf@DESKTOP-7UFBOTC:~$ sudo mdadm --zero-superblock /dev/sdc
asdf@DESKTOP-7UFBOTC:~$ sudo mdadm --zero-superblock /dev/sdd
mdadm: Unrecognised md component device - /dev/sdd
asdf@DESKTOP-7UFBOTC:~$ sudo mdadm --zero-superblock /dev/sde
mdadm: Unrecognised md component device - /dev/sde
asdf@DESKTOP-7UFBOTC:~$ sudo mdadm --create --assume-clean --verbose --level=raid5 --raid-devices=4 /dev/md0 /dev/sdb1 /dev/sdc1 /dev/sdd1 /dev/sde1
mdadm: layout defaults to left-symmetric
mdadm: layout defaults to left-symmetric
mdadm: chunk size defaults to 512K
mdadm: cannot open /dev/sdc1: No such file or directory
asf@DESKTOP-7UFBOTC:~$ lsblk
NAME   MAJ:MIN RM   SIZE RO TYPE MOUNTPOINT
sda      8:0    0   3.7T  0 disk 
&#9500;&#9472;sda1   8:1    0     1M  0 part 
&#9500;&#9472;sda2   8:2    0   3.6T  0 part /
&#9492;&#9472;sda3   8:3    0  31.9G  0 part [SWAP]
sdb      8:16   0   1.8T  0 disk 
&#9492;&#9472;sdb1   8:17   0   1.8T  0 part 
sdc      8:32   0   1.8T  0 disk 
sdd      8:48   0   1.8T  0 disk 
&#9492;&#9472;sdd1   8:49   0   1.8T  0 part 
sde      8:64   0   1.8T  0 disk 
&#9492;&#9472;sde1   8:65   0   1.8T  0 part 
sdf      8:80   0 111.8G  0 disk 
&#9500;&#9472;sdf1   8:81   0   450M  0 part 
&#9500;&#9472;sdf2   8:82   0   100M  0 part 
&#9500;&#9472;sdf3   8:83   0    16M  0 part 
&#9492;&#9472;sdf4   8:84   0 111.2G  0 part 


```

---

### Post by darkod on 2016-09-29
You can. If you used partitions on all disks except sdc, then use the partitions on the other disks and for sdc use /dev/sdc.

---

### Post by Bushflyr on 2016-09-29
It created, but still doesn't want to mount.

```
sudo mdadm --create --assume-clean --verbose --level=raid5 --raid-devices=4 /dev/md0 /dev/sdb1 /dev/sdc /dev/sdd1 /dev/sde1
mdadm: layout defaults to left-symmetric
mdadm: layout defaults to left-symmetric
mdadm: chunk size defaults to 512K
mdadm: size set to 1953381376K
mdadm: automatically enabling write-intent bitmap on large array
mdadm: Defaulting to version 1.2 metadata
mdadm: array /dev/md0 started.
asdf@DESKTOP-7UFBOTC:~$ cat /proc/mdstat
Personalities : [raid6] [raid5] [raid4] 
md0 : active raid5 sde1[3] sdd1[2] sdc[1] sdb1[0]
      5860144128 blocks super 1.2 level 5, 512k chunk, algorithm 2 [4/4] [UUUU]
      bitmap: 0/15 pages [0KB], 65536KB chunk

unused devices: <none>
asdf@DESKTOP-7UFBOTC:~$ sudo mount /dev/md0 /mnt/
mount: wrong fs type, bad option, bad superblock on /dev/md0,
       missing codepage or helper program, or other error

       In some cases useful info is found in syslog - try
       dmesg | tail or so.
asdf@DESKTOP-7UFBOTC:~$ 

```

---

### Post by darkod on 2016-09-29
Unfortunately it doesn't look good... You might not be able to assemble it correctly unless you recall the exact order. Do you remember which mdadm commands you were running on the array after you got the new board? Because a mdadm array should have assembled without problems on the new board too. And the initial --verbose output did say sdb, sdd and sde are part of raid0, not raid5. And they didn't have SB on them. So something very bad definitely happened. Whether during the crash of the board, or because of commands you ran later.

How about assembling without sdc?
```
sudo mdadm --stop /dev/md0
sudo mdadm --create --assume-clean --verbose --level=raid5 --raid-devices=4 /dev/md0 /dev/sdb1 missing /dev/sdd1 /dev/sde1
```

The 'missing' can replace one member in a raid5 because the array can work with one member missing. However we are still not sure that that order of members is the correct one.

---

### Post by Bushflyr on 2016-09-29
Same issue. :( It may be they just got corrupted when the mobo fried. Something really bad did happen, because the mobo failed, then a second identical replacement died within a week, so something else was definitely bad. Salt air and corrosion don't agree with computers apparently.

It shouldn't have been anything I ran afterwards, but who knows? Is there anything you can think of in the more drastic/more dangerous but possible to work vein? I'd like to recover the data, it was a pretty huge losless music collection and all my video files, but nothing that can't be recreated given a chunk of effort. 

Thanks for your time, I really appreciate it. But this one may be a write off, reformat, and be done with RAID5. Seems safer to just use individual drives and back them up RAID 1.

---

