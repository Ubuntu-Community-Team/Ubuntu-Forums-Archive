---
title: "Recover Linux RAID ext3 filesystem"
date: 2008-06-18
forum: Server Platforms
---

### Post by darkblade on 2008-06-18
I had an OS drive failure and as such had to reinstall ubuntu 8.04. 

In my old system I had 5x 500GB on Linux RAID 5 and when I went to reinitialize the RAID it rebuilt and upon trying to mount it as ext3 it says: 

mount: wrong fs type, bad option, bad superblock on /dev/mapper/lvm--raid-lvm0,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

In the past system I had it setup using lvm so that I could easily add more space later so I have tried to mimic the previous system as close as possible. 


I've tried using TestDisk however it lists each drive instead of as a whole to recover. I've looked around here and elsewhere yet haven't found a solution that works.

---

### Post by doogy2004 on 2008-06-18
give this a try [http://www.linuxjournal.com/article/8874](http://www.linuxjournal.com/article/8874)

---

### Post by darkblade on 2008-06-19
Thanks for the response, I'll look that over and give it a shot.

Upon further investigating I noticed when running fdisk -l it shows the raid array as nothing having a valid partition table.

Is it possible to rebuild the table without losing data?

---

### Post by doogy2004 on 2008-06-19
I'm not 100% on the specifics of how raid is managed on the partition tables, but I don't believe that fdisk is able to detect the partion tables because your disk structure is as follows:

outside<inside

Physical Disk<Partion Information<RAID Information<LVM Information<Filesystem Information<Data

a typical setup is
Physical Disk<Partition Information<Filesystem Information<Data

Fdisk is able to read up to the Filesystem Information on a typical setup, however when fdisk looks at your drives it thinks that it is looking at the filesystem information when it is actually looking at the RAID information and fdisk doesn't understand the RAID information so it gives errors such as not having a valid partition table.

Using the instructions in the link that I posted you should be able to recover everything without a problem and without loosing any data.  Please remember that it should work, however there is always a chance that something will go wrong and you could loose data.  Good Luck

---

### Post by darkblade on 2008-06-19
I think it is hosed because I've tried following the steps a few times and each time it still says no file system.

I was thinking of rebuilding the ext3 filesystem and recovering files that way, how feasible is that?

---

### Post by doogy2004 on 2008-06-19
> **darkblade said:**
> I was thinking of rebuilding the ext3 filesystem and recovering files that way, how feasible is that?

Since it was originally RAID5 with LVM inside with EXT3 inside, I don't think that it is going to happen because of the way RAID writes data accross multiple disks to make it redundant.  So you couldn't attempt to recover data off of each disk separately because it would be all cut up on each disk.  But if you could recover the raid portion you might be able to recover data from the entire array.

---

### Post by olivero on 2008-06-20
darkblade, could you please post the output of your raid superblocks using

mdadm -E /dev/[...] 

with the [...] replaced by the partitions/drives that you build your raid from?

Example: mdadm -E /dev/sda1

P.S. In the meantime don't try to recreate the raid with mdadm --create or mdadm --build.

---

### Post by fjgaude on 2008-06-20
After you re-installed the OS and booted, did you install mdadm? And then run the command:

```
sudo --assemble --scan --verbose
```

Do you have your old mdadm.conf file to get the UUID from?

Please do not use the create or build command... you will not be happy if you do.

You can try

```
sudo --assemble -f /dev/md[nn]
```

If you know the md number for the array.

A good philosophy for raid is to always have backup to everything important. So many things to go wrong, raid is for speed and drive failure protection. Much to learn to be able to recover from such failure.

---

### Post by Tamale on 2009-08-24
I'm hoping someone can help me recover my raid5 array.

My setup is 9 identical drives, with 8 of them active.  

```
$ sudo mdadm --detail /dev/md0
/dev/md0:
        Version : 00.90
  Creation Time : Sun Aug 23 22:55:40 2009
     Raid Level : raid5
     Array Size : 1094035712 (1043.35 GiB 1120.29 GB)
  Used Dev Size : 156290816 (149.05 GiB 160.04 GB)
   Raid Devices : 8
  Total Devices : 9
Preferred Minor : 0
    Persistence : Superblock is persistent

    Update Time : Mon Aug 24 09:28:16 2009
          State : clean
 Active Devices : 8
Working Devices : 9
 Failed Devices : 0
  Spare Devices : 1

         Layout : left-symmetric
     Chunk Size : 64K

           UUID : 61142506:e860a234:57b0c734:a913951c
         Events : 0.18

    Number   Major   Minor   RaidDevice State
       0       8        0        0      active sync   /dev/sda
       1       8       16        1      active sync   /dev/sdb
       2       8       32        2      active sync   /dev/sdc
       3       8       48        3      active sync   /dev/sdd
       4       8       64        4      active sync   /dev/sde
       5       8       80        5      active sync   /dev/sdf
       6       8       96        6      active sync   /dev/sdg
       7       8      112        7      active sync   /dev/sdh

       8       8      144        -      spare   /dev/sdj

```

my problem is last night I wasn't seeing two of the drives.. so I turned the machine off, re-seated the controller card, fired the computer back up, and.. uh.. no raid device. I tried mdadm assemble and force to no avail, and finally ran across advice to re-create with the assume clean command.

I did this, and it started recovering one of the 8 drives.  It finally finished this morning, but I'm still not seeing my filesystem:

[43323.485559] VFS: Can't find ext3 filesystem on dev md0.

How can I recover my files!? :(

---

### Post by tgrimley on 2009-08-24
Tamale:

You'll get more results if you start a new thread instead of resurrecting a 14 month old one.

I would not have tried to assemble assuming clean until I had exhausted the rest of my options.  Maybe someone else has a suggestion.

---

### Post by fjgaude on 2009-08-27
Much I don't understand, Tamale. You don't see your filesystem? How are you looking for it.

The --detail command shows everything is correct.

How did you try to assemble the array? to mount it?

What does the **/etc/mdadm/mdadm.conf** show?

The **fdisk -l** command shows drives of a system and doesn't correctly show raid arrays.

---

