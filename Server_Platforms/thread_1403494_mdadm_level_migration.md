---
title: "mdadm level migration"
date: 2010-02-10
forum: Server Platforms
---

### Post by tgrimley on 2010-02-10
Hi,

I've installed the experimental deb of mdadm 3.1.1, which I intended to use to migrate from a 4 disk raid5 to a 5 disk raid6, but mdadm won't ahve any of it.  Running 9.04 64bit server. 

Any suggestions?

```

tgrimley@gutsy:~$ sudo mdadm --grow /dev/md0 --level=6 --raid-devices=5 --backup-file=/home/tgrimley/md0.backup

```

```


tgrimley@gutsy:~$ sudo mdadm -D /dev/md0
/dev/md0:
        Version : 0.90
  Creation Time : Sat Aug 22 13:50:42 2009
     Raid Level : raid5
     Array Size : 5860535808 (5589.04 GiB 6001.19 GB)
  Used Dev Size : 1953511936 (1863.01 GiB 2000.40 GB)
   Raid Devices : 4
  Total Devices : 5
Preferred Minor : 0
    Persistence : Superblock is persistent

    Update Time : Wed Feb 10 07:32:50 2010
          State : active
 Active Devices : 4
Working Devices : 5
 Failed Devices : 0
  Spare Devices : 1

         Layout : left-symmetric
     Chunk Size : 128K

           UUID : 117232ce:f55876b7:9822568f:9ddc1a1a
         Events : 0.1387401

    Number   Major   Minor   RaidDevice State
       0       8       65        0      active sync   /dev/sde1
       1       8       97        1      active sync   /dev/sdg1
       2       8       49        2      active sync   /dev/sdd1
       3       8      161        3      active sync   /dev/sdk1

       4       8      145        -      spare   /dev/sdj1

```

---

### Post by tgrimley on 2010-02-12
Upgraded to 2.6.32 kernel and now it says


```
tgrimley@gutsy:~$ sudo mdadm --grow /dev/md0 --level=6 --raid-devices=5 --backup-file=/home/tgrimley/md0.backup
[sudo] password for tgrimley:
mdadm level of /dev/md0 changed to raid6
mdadm: this change will reduce the size of the array.
       use --grow --array-size first to truncate array.
       e.g. mdadm --grow /dev/md0 --array-size 1565568512
mdadm: aborting level change
tgrimley@gutsy:~$

```

Looked online and it seems this is common if there is a bitmap, but I don't have one!

```
tgrimley@gutsy:~$ sudo mdadm -D /dev/md0
/dev/md0:
        Version : 0.90
  Creation Time : Sat Aug 22 13:50:42 2009
     Raid Level : raid5
     Array Size : 5860535808 (5589.04 GiB 6001.19 GB)
  Used Dev Size : 1953511936 (1863.01 GiB 2000.40 GB)
   Raid Devices : 4
  Total Devices : 5
Preferred Minor : 0
    Persistence : Superblock is persistent

    Update Time : Fri Feb 12 08:12:52 2010
          State : clean
 Active Devices : 4
Working Devices : 5
 Failed Devices : 0
  Spare Devices : 1

         Layout : left-symmetric
     Chunk Size : 128K

           UUID : 117232ce:f55876b7:9822568f:9ddc1a1a
         Events : 0.1388737

    Number   Major   Minor   RaidDevice State
       0       8       81        0      active sync   /dev/sdf1
       1       8      129        1      active sync   /dev/sdi1
       2       8       65        2      active sync   /dev/sde1
       3       8       33        3      active sync   /dev/sdc1

       4       8       97        -      spare   /dev/sdg1
tgrimley@gutsy:~$

```

---

### Post by drave on 2010-02-12
I dont think you can migrate levels 5 -> 6 only grow an existing level

If you want to use the old disks to create a new raid then zero the superblock (mdadm --zero-superblock /dev/sd?) on each disk before creating the new raid. Otherwise mdadm gets its knickers in a twist about which disk belongs to which raid setup

---

### Post by tgrimley on 2010-02-12
> **drave said:**
> I dont think you can migrate levels 5 -> 6 only grow an existing level

mdadm 3.1.1 supports level migration (see: [http://neil.brown.name/blog/20090817000931](http://neil.brown.name/blog/20090817000931))

---

### Post by joberly on 2010-02-12
Did you add the new disk to the array before growing it? 

Something like sudo mdadm --manage /dev/md0 --add /dev/<drive>/

---

### Post by tgrimley on 2010-02-12
Yes, it's sitting there as a spare

---

### Post by tgrimley on 2010-02-24
For future reference, this is a known bug which is apparently patched 7 days after 3.1.1 was released.  So if one wants to upgrade from raid5 to raid6 with one disk addition, they will need to compile the current release from git repository.

---

### Post by fjgaude on 2010-02-25
Thanks, this is useful to know!

---

### Post by tgrimley on 2010-02-25
If anyone is brave enough to try a raid5->raid6 migration with only a one disk addition under 9.04 with a manually installed 2.6.32 kernel, please let me know :)

---

### Post by kingbelrik on 2010-03-09
> **tgrimley said:**
> If anyone is brave enough to try a raid5->raid6 migration with only a one disk addition under 9.04 with a manually installed 2.6.32 kernel, please let me know :)

I've done this in a VM, migrated RAID5 -> RAID6 and also back again. It worked as advertised, keeping the array online and the filesystem intact.

---

