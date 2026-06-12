---
title: "Raid5 how to fix partition problem"
date: 2012-03-27
forum: Server Platforms
---

### Post by speed32219 on 2012-03-27
Description:    Ubuntu 11.10
Release:        11.10
Codename:       oneiric

I have a small raid 5 setup with mdadm raid5 with LVM2.  I recently migrated (fresh install) from karmic to oneric minimal install and after fixing a few issues system was working fine.

I rebooted the server and was brought to the initramfs prompt after it had given me an error on the raid.  I truned off the array and booted into the system to run some tests.

cat /proc/mdstat
md1 : **inactive** sdd[0](S) sdc[1](S) sdb[3](S) sde[2](S)
      5860553984 blocks
unused devices: <none>

sudo mdadm --examine --scan
ARRAY /dev/md1 UUID=7e6f942e:fb608064:d66a740f:8642d62d

I've run sudo smartctl -a on all drives and they pass.  

sudo mdadm --assemble --scan -v
mdadm: looking for devices for /dev/md1
mdadm: cannot open device /dev/sde: Device or resource busy
mdadm: /dev/sde has wrong uuid.
mdadm: cannot open device /dev/sdd: Device or resource busy
mdadm: /dev/sdd has wrong uuid.
mdadm: cannot open device /dev/sdc1: Device or resource busy
mdadm: /dev/sdc1 has wrong uuid.
mdadm: cannot open device /dev/sdc: Device or resource busy
mdadm: /dev/sdc has wrong uuid.
mdadm: cannot open device /dev/sdb: Device or resource busy
mdadm: /dev/sdb has wrong uuid.
mdadm: cannot open device /dev/sda3: Device or resource busy
mdadm: /dev/sda3 has wrong uuid.
mdadm: cannot open device /dev/sda2: Device or resource busy
mdadm: /dev/sda2 has wrong uuid.
mdadm: cannot open device /dev/sda1: Device or resource busy
mdadm: /dev/sda1 has wrong uuid.
mdadm: cannot open device /dev/sda: Device or resource busy
mdadm: /dev/sda has wrong uuid.

From this it looks like I have no UUIDs and no Superblocks for sdb, sdc, sdd, and sde that is in the array. I don't know why sda1/2/3 is there since it is the internal 500GB HD with root/home/swap on it.

SO I ran this command to check super blocks and found SDC is setup for TYPE EXT4.  How did this happen, it should be linux_raid_member. 

sudo blkid

/dev/sda1: LABEL="Root" UUID="d10eade2-473d-4049-a9ba-13af0de5938a" TYPE="ext3"
/dev/sda2: UUID="200faa25-ad30-4841-afd4-3bc177ea1015" TYPE="swap"
/dev/sda3: LABEL="Home" UUID="3b4351b1-2232-4a4f-aec1-863af26f8f6e" TYPE="ext3"
/dev/sdb: UUID="7e6f942e-fb60-8064-d66a-740f8642d62d" TYPE="linux_raid_member"
/dev/sdc1: UUID="4e793a50-bc27-433b-872c-48b6829f3391" TYPE="**ext4**"
/dev/sdd: UUID="7e6f942e-fb60-8064-d66a-740f8642d62d" TYPE="linux_raid_member"
/dev/sde: UUID="7e6f942e-fb60-8064-d66a-740f8642d62d" TYPE="linux_raid_member"

sudo fdisk -l
Disk /dev/sda: 500.1 GB, 500106780160 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976771055 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000f1e81

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    12691349     6345643+  83  Linux
/dev/sda2        12691350    15647309     1477980   82  Linux swap / Solaris
/dev/sda3        15647310   976768064   480560377+  83  Linux

Disk /dev/sdb: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders, total 2930277168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
**Disk identifier: 0x50610834**

**Disk /dev/sdb doesn't contain a valid partition table**

Disk /dev/sdc: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders, total 2930277168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
**Disk identifier: 0x50610834**

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1              64  2930277167  1465138552   fd  Linux raid autodetect

Disk /dev/sdd: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders, total 2930277168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
**Disk identifier: 0x00000000**

Disk /dev/sdd doesn't contain a valid partition table

Disk /dev/sde: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders, total 2930277168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
**Disk identifier: 0x00000000**

Disk /dev/sde doesn't contain a valid partition table

So, somehow sdc parition type has changed to EXT4.  How do I get it back to linux_raid_member type?

---

### Post by darkod on 2012-03-27
I am no expert to help you, but I have noticed something which might have created your issue.

Why are the disks raid_members? Usually you would create a partition taking the whole disk (or more partitions depending on your planning) and you make the partition type linux_raid_member, not the whole disk device.

---

### Post by rubylaser on 2012-03-27
> **darkod said:**
> I am no expert to help you, but I have noticed something which might have created your issue.

Why are the disks raid_members? Usually you would create a partition taking the whole disk (or more partitions depending on your planning) and you make the partition type linux_raid_member, not the whole disk device.

Although, I prefer to use disk partitions, there is nothing wrong with using raw disks to create a raid an mdadm array.  To the OP, have you tried viewing your individual disks for superblock metadata?

```
mdadm -E /dev/sd[bcde]
```

---

### Post by darkod on 2012-03-27
> **rubylaser said:**
> Although, I prefer to use disk partitions, there is nothing wrong with using raw disks to create a raid an mdadm array.  To the OP, have you tried viewing your individual disks for superblock metadata?

```
mdadm -E /dev/sd[bcde]
```
 
Didn't know that. :)

---

### Post by speed32219 on 2012-03-27
> **rubylaser said:**
> Although, I prefer to use disk partitions, there is nothing wrong with using raw disks to create a raid an mdadm array.  To the OP, have you tried viewing your individual disks for superblock metadata?

```
mdadm -E /dev/sd[bcde]
```

Here is the output.  Although I am concerned about sdc shwoing up as an ext4 type/partition.  I never set paritions and it is the first dirve in the array. How can I change it back to the raid type?  Using fdisk?  SDC looks to be the problem I think.

sudo mdadm -E /dev/sd[bcde]

```
/dev/sdb:
          Magic : a92b4efc
        Version : 0.90.00
           UUID : 7e6f942e:fb608064:d66a740f:8642d62d
  Creation Time : Sat Apr 17 09:03:07 2010
     Raid Level : raid5
  Used Dev Size : 1465138496 (1397.26 GiB 1500.30 GB)
     Array Size : 4395415488 (4191.79 GiB 4500.91 GB)
   Raid Devices : 4
  Total Devices : 4
Preferred Minor : 1

    Update Time : Sat Mar 24 06:26:31 2012
          State : clean
Internal Bitmap : present
 Active Devices : 4
Working Devices : 4
 Failed Devices : 0
  Spare Devices : 0
       Checksum : 723c4fe7 - correct
         Events : 231398

         Layout : left-symmetric
     Chunk Size : 64K

      Number   Major   Minor   RaidDevice State
this     3       8        0        3      active sync   /dev/sda

   0     0       8       32        0      active sync   /dev/sdc
   1     1       8       16        1      active sync   /dev/sdb
   2     2       8       48        2      active sync   /dev/sdd
   3     3       8        0        3      active sync   /dev/sda
/dev/sdc:
          Magic : a92b4efc
        Version : 0.90.00
           UUID : 7e6f942e:fb608064:d66a740f:8642d62d
  Creation Time : Sat Apr 17 09:03:07 2010
     Raid Level : raid5
  Used Dev Size : 1465138496 (1397.26 GiB 1500.30 GB)
     Array Size : 4395415488 (4191.79 GiB 4500.91 GB)
   Raid Devices : 4
  Total Devices : 4
Preferred Minor : 1

    Update Time : Sat Mar 24 06:26:31 2012
          State : clean
Internal Bitmap : present
 Active Devices : 4
Working Devices : 4
 Failed Devices : 0
  Spare Devices : 0
       Checksum : 723c4ff3 - correct
         Events : 231398

         Layout : left-symmetric
     Chunk Size : 64K

      Number   Major   Minor   RaidDevice State
this     1       8       16        1      active sync   /dev/sdb

   0     0       8       32        0      active sync   /dev/sdc
   1     1       8       16        1      active sync   /dev/sdb
   2     2       8       48        2      active sync   /dev/sdd
   3     3       8        0        3      active sync   /dev/sda
/dev/sdd:
          Magic : a92b4efc
        Version : 0.90.00
           UUID : 7e6f942e:fb608064:d66a740f:8642d62d
  Creation Time : Sat Apr 17 09:03:07 2010
     Raid Level : raid5
  Used Dev Size : 1465138496 (1397.26 GiB 1500.30 GB)
     Array Size : 4395415488 (4191.79 GiB 4500.91 GB)
   Raid Devices : 4
  Total Devices : 4
Preferred Minor : 1

    Update Time : Sat Mar 24 21:56:03 2012
          State : clean
Internal Bitmap : present
 Active Devices : 1
Working Devices : 1
 Failed Devices : 3
  Spare Devices : 0
       Checksum : 723d2a0c - correct
         Events : 231402

         Layout : left-symmetric
     Chunk Size : 64K

      Number   Major   Minor   RaidDevice State
this     0       8       32        0      active sync   /dev/sdc

   0     0       8       32        0      active sync   /dev/sdc
   1     1       0        0        1      faulty removed
   2     2       0        0        2      faulty removed
   3     3       0        0        3      faulty removed
/dev/sde:
          Magic : a92b4efc
        Version : 0.90.00
           UUID : 7e6f942e:fb608064:d66a740f:8642d62d
  Creation Time : Sat Apr 17 09:03:07 2010
     Raid Level : raid5
  Used Dev Size : 1465138496 (1397.26 GiB 1500.30 GB)
     Array Size : 4395415488 (4191.79 GiB 4500.91 GB)
   Raid Devices : 4
  Total Devices : 4
Preferred Minor : 1

    Update Time : Sat Mar 24 21:55:11 2012
          State : clean
Internal Bitmap : present
 Active Devices : 2
Working Devices : 2
 Failed Devices : 2
  Spare Devices : 0
       Checksum : 723d29db - correct
         Events : 231401

         Layout : left-symmetric
     Chunk Size : 64K

      Number   Major   Minor   RaidDevice State
this     2       8       48        2      active sync   /dev/sdd

   0     0       8       32        0      active sync   /dev/sdc
   1     1       0        0        1      faulty removed
   2     2       8       48        2      active sync   /dev/sdd
   3     3       0        0        3      faulty removed

```

---

### Post by rmil on 2012-03-27
seems that Superblocks are clean. 

1) make backup if possible.

2) Have you thought that something else might brought you to iniramfs. i.e. wrong /etc/fstab settings.

3) Do you use swap? Since you are using raw disks you might lost connection with swap file

4) Happened to me and it can be 5min job or whole day lost, your FS might be damaged you should use fsck of your raid from some live distro or rescue mode from live cd for servers.

---

### Post by speed32219 on 2012-03-27
> **rmil said:**
> seems that Superblocks are clean. 

1) make backup if possible.

2) Have you thought that something else might brought you to iniramfs. i.e. wrong /etc/fstab settings.

3) Do you use swap? Since you are using raw disks you might lost connection with swap file

4) Happened to me and it can be 5min job or whole day lost, your FS might be damaged you should use fsck of your raid from some live distro or rescue mode from live cd for servers.

1. I wish I could, if I get this back I am going to buy external 3TB drives and use rysnc on a weekly basis after I write a script to do so.

2. Hmm, no but I did add a # in front of the /dev/vg1/raid /mnt/raid so it would boot up all the way for trouble shooting purposes.  Maybe I should use the uuid of the mdadm config instead.  I thought the mdadm.conf looked different somehow, but did not have a backup of it.

3. I do have swap, but I have set mdadm not to use write cache.  We did have a bad thunder storm with severe lightning the night before and it is possible that writes were taking place from an online app. although I do have a ups and nothing seemed wrong.

I have tried using fsck but I always get drive is in use by another service or program. Also, in my first post trying to assemble I got errors that I had the wrong uuids of the drives.
It is probably a simple fix.  I'm going to persue the uuid and fsck problems for now.  I have these issues about once a year and since I don't use it reguraly, I forget many little tricks. LOL!  And 5 minutes is not my norm, more like 5-hrs to 5 days!

EDIT:  Just changed the /etc/fstab entry to the UUID of the mdadm.conf file and recieved this error: **mount: special device UUID=31283299-0c118170-8b4eb9a8-4e935bf2 does not exist**

---

### Post by rubylaser on 2012-03-27
Your superblocks exist, but do not look good.  Your event counters are the same on two of your 4 disks, and those are the two oldest copies (sdb,sdc).  The other two disks have different, newer (higher) event counters. 

If you don't have a backup, you're going to have to try to force the array back together.   The first thing to do is verify that all of your disks are healthly via smartmontools tools.  If the disks are all healthy, you can try to force it back together like this.```
mdadm --assemble --force /dev/md1 /dev/sd[bcde]
```

You won't be able to fsck the array, until you can get it assembled properly first.

Unfortunately, this is really the time that a good backup would really give you piece of mind :(

---

### Post by speed32219 on 2012-03-27
**I'm back **in business.  Don't know what happened, but made a few changes and did the following:

$ sudo mdadm --stop /dev/md1
mdadm: stopped /dev/md1
$ sudo mdadm --assemble -f -v /dev/md1 /dev/sd[b-e]
mdadm: looking for devices for /dev/md1
mdadm: /dev/sdb is identified as a member of /dev/md1, slot 3.
mdadm: /dev/sdc is identified as a member of /dev/md1, slot 1.
mdadm: /dev/sdd is identified as a member of /dev/md1, slot 0.
mdadm: /dev/sde is identified as a member of /dev/md1, slot 2.
mdadm: forcing event count in /dev/sdc(1) from 231398 upto 231402
mdadm: forcing event count in /dev/sdb(3) from 231398 upto 231402
mdadm: clearing FAULTY flag for device 1 in /dev/md1 for /dev/sdc
mdadm: clearing FAULTY flag for device 3 in /dev/md1 for /dev/sde
mdadm: clearing FAULTY flag for device 0 in /dev/md1 for /dev/sdb
mdadm: added /dev/sdc to /dev/md1 as 1
mdadm: added /dev/sde to /dev/md1 as 2
mdadm: added /dev/sdb to /dev/md1 as 3
mdadm: added /dev/sdd to /dev/md1 as 0
**mdadm: /dev/md1 has been started with 4 drives.**

OMG!!!!
$ sudo mount -a
$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             6.0G  2.3G  3.7G  38% /
udev                  747M   16K  747M   1% /dev
tmpfs                 302M  872K  301M   1% /run
none                  5.0M     0  5.0M   0% /run/lock
none                  754M     0  754M   0% /run/shm
/dev/sda3             452G  176G  253G  42% /home
**/dev/mapper/vg1-raid  4.1T  2.7T  1.2T  70% /mnt/raid**

Yeah!  Yeah!  Yeah!
Now to go buy my external usb3.0 3TB drives (2) and setup a rsync with weekly real backup script.

Thank you all for lending me your ears while I plowed through my many, many, many notes.  **This thread is solved**!!!!!!!!!!!!!

---

### Post by rubylaser on 2012-03-27
Glad you got it working, and that realizing you needed a backup didn't come at the expense of your data.

---

### Post by Vegan on 2012-03-27
I learned long ago its prudent to have several layers of backup just in case the unthinkable happens

:guitar::guitar::guitar:

---

