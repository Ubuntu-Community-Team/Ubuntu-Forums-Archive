---
title: "How do i mount my raid array at startup"
date: 2012-04-30
forum: Server Platforms
---

### Post by virtual81 on 2012-04-30
Evenin' ladies and gents,

I have used ubuntu server 11.10 on a HP N40L with 4 spare 500 gig hard disks to make a little nas (+web/sql/torrent etc soon if relevant) and the orignal 250 gig drive for the OS

The disks came from an existing array from a windows box on the intel ICH9R.

During install this seemed to be detected, and i couldn't figure out how to break it and make it fresh, so i left it and formatted it as ext4 (i think).

I mounted it a few days ago as /dev/md0 to /mnt/nas and was able to write to it as root, then put the project on hold a few days to do other things.

First question - after a few days i have come back and can't remember what the file system, how would i find that out?

I googled and tried the following...
```
root@bits:~# fdisk -l

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000dd0f8

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            2048   976771071   488384512   fd  Linux RAID autodetect

Disk /dev/sdd: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000ea3c8

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1            2048   976771071   488384512   fd  Linux RAID autodetect

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000e5ec8

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1            2048   976771071   488384512   fd  Linux RAID autodetect

Disk /dev/sde: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0002b038

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1   *        2048   484270079   242134016   83  Linux
/dev/sde2       484272126   488396799     2062337    5  Extended
/dev/sde5       484272128   488396799     2062336   82  Linux swap / Solaris

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000e1b03

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1            2048   976771071   488384512   fd  Linux RAID autodetect

Disk /dev/md0: 1500.3 GB, 1500312502272 bytes
2 heads, 4 sectors/track, 366287232 cylinders, total 2930297856 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 524288 bytes / 1572864 bytes
Disk identifier: 0x00000000

Disk /dev/md0 doesn't contain a valid partition table
root@bits:~#

```

But no luck.

What is my best course of action from here.
Is the RAID setup ideal, or should i remake it? if so, how?
Once i have a good setup, how do i mount it at boot?
Most importantly, looking forward - how do i look after it?
I'd like to simulate a failure (pull a disk whilst running or similar?) to see how to fix it.

I do have samba working at the moment, very nicely, good read and write speads over the gig network, 66MB/sec with random small files acording to the Win7 copy dialogue.

Not as important at the moment, but i would also like to be able to have each user have samba access to their home directory to map on their windows machine

Any assistance appreciated.

Cheers.

---

### Post by rubylaser on 2012-04-30
I answer all of those questions minus setting up Samba on my mdadm [tutorials on my website]("http://zackreed.me/articles/38-software-raid-5-in-debian-with-mdadm").  I'd suggest you follow along to setup mdadm, your filesystem, automouting, alerting, smart montoring, etc.

Please let me know if you have any questions following along with them.

---

### Post by virtual81 on 2012-04-30
Thanks for your reply rubylaser

Its time to hit the sack here, but i did quickly run a few commands...
```
root@bits:~# mdadm -V
mdadm - v3.1.4 - 31st August 2010
root@bits:~# mdadm --detail /dev/md0
/dev/md0:
        Version : 1.2
  Creation Time : Wed Apr 25 00:15:45 2012
     Raid Level : raid5
     Array Size : 1465148928 (1397.27 GiB 1500.31 GB)
  Used Dev Size : 488382976 (465.76 GiB 500.10 GB)
   Raid Devices : 4
  Total Devices : 4
    Persistence : Superblock is persistent

    Update Time : Mon Apr 30 20:38:41 2012
          State : clean
 Active Devices : 4
Working Devices : 4
 Failed Devices : 0
  Spare Devices : 0

         Layout : left-symmetric
     Chunk Size : 512K

           Name : bitbox:0
           UUID : df6467f4:90f15487:4d6a36dd:111f214f
         Events : 37

    Number   Major   Minor   RaidDevice State
       0       8        1        0      active sync   /dev/sda1
       1       8       17        1      active sync   /dev/sdb1
       2       8       33        2      active sync   /dev/sdc1
       3       8       49        3      active sync   /dev/sdd1
root@bits:~#

```

mdadm looks like it is already configured with a working array.

If it looks good, then i'll stick with it as is, and follow your tutorial from that point.

Will look closer at it tomorrow.
Cheers.

::PS
Tried mount --help and then mount -l and it appears the file system is xfs
I remember now having a quick read about xfs and ext4 on Wikipedia and choosing xfs because it sounded ok.
I do remember using ext2 and ext3 some time ago during my last incursion into linux world.

---

### Post by rubylaser on 2012-04-30
Personally, I've had nothing but problems from XFS, so I avoid it.  Good luck, and let us know how it goes.

---

### Post by CharlesA on 2012-04-30
> **virtual81 said:**
> 
I do have samba working at the moment, very nicely, good read and write speads over the gig network, 66MB/sec with random small files acording to the Win7 copy dialogue.

Not as important at the moment, but i would also like to be able to have each user have samba access to their home directory to map on their windows machine

That speed is pretty good for Samba, I get around 100MB/sec for sequential reads off my RAID-5 array.

As for giving each user access to their /home/$USER folder, change:
```
# Un-comment the following (and tweak the other settings below to suit)
# to enable the default home directory shares. This will share each
# user's home director as \\server\username
;[homes]
;   comment = Home Directories
;   browseable = no
```

To:
```
# Un-comment the following (and tweak the other settings below to suit)
# to enable the default home directory shares. This will share each
# user's home director as \\server\username
 [homes]
    comment = Home Directories
    browseable = no

```

Add a smb user:

```
sudo smbpasswd -a username
```

Restart smbd and nmbd:

```
sudo service smbd restart && sudo service nmbd restart
```

You should be good.

Note: Setting up Samba this way will not sync up the smb passwords with the user passwords, so if they change their password there, you'd have to change it for them on the server. LDAP gets around that, but I don't have any experience setting it up.

---

