---
title: "raid5 device won't asseble/mount at boot after adding drives"
date: 2010-06-12
forum: Server Platforms
---

### Post by wheniwork on 2010-06-12
Hi. I just added a couple drives to my raid device /dev/md1 and now the system will not mount/assemble this device at boot. I have to assemble manually and then mount.

My mdadm.conf seems to be right and I did a:

```
update-initramfs -u
```

after I updated the mdadm.conf, but I now get this output when running: update-initramfs -u 

```
root@kiwi:~# update-initramfs -u
update-initramfs: Generating /boot/initrd.img-2.6.27-17-server
Warning: LBA32 addressing assumed
Warning: '/proc/partitions' does not match '/dev' directory structure.
    Name change: '/dev/dm-0' -> '/dev/block/254:0'
Warning: Name change: '/dev/dm-1' -> '/dev/block/254:1'
Warning: The initial RAM disk is too big to fit between the kernel and
   the 15M-16M memory hole.  It will be loaded in the highest memory as
   though the configuration file specified "large-memory" and it will
   be assumed that the BIOS supports memory moves above 16M.
Added Linux ? *
Warning: The initial RAM disk is too big to fit between the kernel and
   the 15M-16M memory hole.  It will be loaded in the highest memory as
   though the configuration file specified "large-memory" and it will
   be assumed that the BIOS supports memory moves above 16M.
Added LinuxOLD ?
The Master boot record of  /dev/sda  has been updated.
Warning: /dev/sdb is not on the first disk
The Master boot record of  /dev/sdb  has been updated.
6 warnings were issued.
```

Is this why the RAID device /dev/md1 is not assembling/mounting at boot? If so, how do I get "update-initramfs -u" to run successfully? Thanks!

---

### Post by disabledaccount on 2010-06-12
Main question: what is array status? - You say yor Raid wont assemble -> You should start from analysis of mdadm --detail output. Initramfs seems to be confused due to messed partition table on one of the drives.
Also, It would be helpful if you provide complete list of hdd/partitions list f.e >fdisk -ul

---

### Post by wheniwork on 2010-06-12
The array is fine. I am able to assemble and mount it fine manually. It just won't mount at boot. 

```

root@kiwi:~# mdadm --assemble /dev/md1 /dev/sdc1 /dev/sde1 /dev/sdf1 /dev/sdg1 /dev/sdh1 /dev/sdi1 /dev/sdj1
mdadm: /dev/md1 has been started with 7 drives.

```

I think the issue has something to do with when i try update-initramfs and get the warnings. Not sure if its taking into account the changes to mdadm.conf.

Here's my current mdadm.conf. I've been trying different things. But I don't think it's taking when running update-initramfs.

```

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
#ARRAY /dev/md0 level=raid1 num-devices=2 UUID=68a8c99c:e62233cf:a2d777ff:3851570a
#ARRAY /dev/md1 level=raid5 num-devices=7 UUID=93ae091b:b4aa0eb1:8e7c4951:0f0ba6be
#   spares=1
#ARRAY /dev/md1 level=raid5 num-devices=7 UUID=93ae091b:b4aa0eb1:8e7c4951:0f0ba6be
#   spares=1
ARRAY /dev/md0 level=raid1 num-devices=2 metadata=00.90 UUID=68a8c99c:e62233cf:a2d777ff:3851570a
   devices=/dev/sda1,/dev/sdb1
ARRAY /dev/md1 level=raid5 num-devices=7 metadata=00.90 spares=1 UUID=93ae091b:b4aa0eb1:8e7c4951:0f0ba6be
   devices=/dev/sde1,/dev/sdf1,/dev/sdg1,/dev/sdh1,/dev/sdi1,/dev/sdj1,/dev/sdc1,/dev/sdd1

```

---

### Post by wheniwork on 2010-06-12
and this is this:

```
root@kiwi:/etc/mdadm# mdadm --detail /dev/md1
mdadm: metadata format 00.90 unknown, ignored.
mdadm: metadata format 00.90 unknown, ignored.
/dev/md1:
        Version : 00.90
  Creation Time : Thu Mar 26 20:02:07 2009
     Raid Level : raid5
     Array Size : 5860559616 (5589.07 GiB 6001.21 GB)
  Used Dev Size : 976759936 (931.51 GiB 1000.20 GB)
   Raid Devices : 7
  Total Devices : 8
Preferred Minor : 1
    Persistence : Superblock is persistent

    Update Time : Sat Jun 12 02:03:36 2010
          State : clean
 Active Devices : 7
Working Devices : 8
 Failed Devices : 0
  Spare Devices : 1

         Layout : left-symmetric
     Chunk Size : 64K

           UUID : 93ae091b:b4aa0eb1:8e7c4951:0f0ba6be
         Events : 0.1324996

    Number   Major   Minor   RaidDevice State
       0       8       65        0      active sync   /dev/sde1
       1       8       81        1      active sync   /dev/sdf1
       2       8       97        2      active sync   /dev/sdg1
       3       8      113        3      active sync   /dev/sdh1
       4       8      129        4      active sync   /dev/sdi1
       5       8      145        5      active sync   /dev/sdj1
       6       8       33        6      active sync   /dev/sdc1

       7       8       49        -      spare   /dev/sdd1

```


```
root@kiwi:/etc/mdadm# fdisk -ul 

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0006e9cf

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   976768064   488384001   fd  Linux raid autodetect

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00073827

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63   976768064   488384001   fd  Linux raid autodetect

Disk /dev/sdc: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x92a523c2

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1              63  1953520064   976760001   fd  Linux raid autodetect

Disk /dev/sdd: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x848bd6cd

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1              63  1953520064   976760001   fd  Linux raid autodetect

Disk /dev/sde: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0004c3c1

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1              63  1953520064   976760001   fd  Linux raid autodetect

Disk /dev/sdf: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00057c65

   Device Boot      Start         End      Blocks   Id  System
/dev/sdf1              63  1953520064   976760001   fd  Linux raid autodetect

Disk /dev/sdg: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0005c706

   Device Boot      Start         End      Blocks   Id  System
/dev/sdg1              63  1953520064   976760001   fd  Linux raid autodetect

Disk /dev/sdh: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0006529e

   Device Boot      Start         End      Blocks   Id  System
/dev/sdh1              63  1953520064   976760001   fd  Linux raid autodetect

Disk /dev/sdi: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00069c24

   Device Boot      Start         End      Blocks   Id  System
/dev/sdi1              63  1953520064   976760001   fd  Linux raid autodetect

Disk /dev/sdj: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xc7b8fc49

   Device Boot      Start         End      Blocks   Id  System
/dev/sdj1              63  1953520064   976760001   fd  Linux raid autodetect

```

---

### Post by disabledaccount on 2010-06-12
You have this: "mdadm: metadata format 00.90 unknown, ignored."
This is effect of automatic scanning for array members at boot-time and means
that one or two of drives was previously member(s) of another array.
Mdadm finds that unused superblocks and most propably this is reason why it doesnt
automatically assemble the array. It should work, if you disable automatic scanning in mdadm.conf 
Always clear old md superblocks before you add drive to another array. In speciall cases, if unused superblock has same uuid like the "right one" you can get broken array.

---

### Post by wheniwork on 2010-06-12
How do you disable automatic scanning in mdadm.conf ?

Or how do you clear old md superblocks?

After doing this will update-initramfs -u work?

---

### Post by wheniwork on 2010-06-12
Fixed the 

mdadm: metadata format 00.90 unknown, ignored.

With this:
[http://ubuntuforums.org/showthread.php?p=6345457#post6345457](http://ubuntuforums.org/showthread.php?p=6345457#post6345457)

```
root@kiwi:/etc/mdadm# mdadm --detail /dev/md1
/dev/md1:
        Version : 00.90
  Creation Time : Thu Mar 26 20:02:07 2009
     Raid Level : raid5
     Array Size : 5860559616 (5589.07 GiB 6001.21 GB)
  Used Dev Size : 976759936 (931.51 GiB 1000.20 GB)
   Raid Devices : 7
  Total Devices : 8
Preferred Minor : 1
    Persistence : Superblock is persistent

    Update Time : Sat Jun 12 03:00:47 2010
          State : clean
 Active Devices : 7
Working Devices : 8
 Failed Devices : 0
  Spare Devices : 1

         Layout : left-symmetric
     Chunk Size : 64K

           UUID : 93ae091b:b4aa0eb1:8e7c4951:0f0ba6be
         Events : 0.1324996

    Number   Major   Minor   RaidDevice State
       0       8       65        0      active sync   /dev/sde1
       1       8       81        1      active sync   /dev/sdf1
       2       8       97        2      active sync   /dev/sdg1
       3       8      113        3      active sync   /dev/sdh1
       4       8      129        4      active sync   /dev/sdi1
       5       8      145        5      active sync   /dev/sdj1
       6       8       33        6      active sync   /dev/sdc1

       7       8       49        -      spare   /dev/sdd1

```

---

### Post by wheniwork on 2010-06-12
Looks like it's mounting now at boot. Fixed that meta thing.

But I'm getting mixed messages on how much disc space is available.

On the gdm desktop the mounted raid device says there is 

6001.2 GB Media

but when running df I get

```
chad@kiwi:~$ df
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/mapper/system_mirror-ubuntu_system
                     409693988   6012200 403681788   2% /
tmpfs                  2070384         0   2070384   0% /lib/init/rw
varrun                 2070384       364   2070020   1% /var/run
varlock                2070384         0   2070384   0% /var/lock
udev                   2070384      2976   2067408   1% /dev
tmpfs                  2070384       104   2070280   1% /dev/shm
lrm                    2070384      2204   2068180   1% /lib/modules/2.6.27-17-server/volatile
/dev/md1             3906920504 2670118000 1236802504  69% /media/storage

```


AND for the raid device. I get this reading.

```
root@kiwi:~# mdadm -D /dev/md1
/dev/md1:
        Version : 00.90
  Creation Time : Thu Mar 26 20:02:07 2009
     Raid Level : raid5
     Array Size : 5860559616 (5589.07 GiB 6001.21 GB)
  Used Dev Size : 976759936 (931.51 GiB 1000.20 GB)
   Raid Devices : 7
  Total Devices : 8
Preferred Minor : 1
    Persistence : Superblock is persistent

    Update Time : Sat Jun 12 09:45:29 2010
          State : clean
 Active Devices : 7
Working Devices : 8
 Failed Devices : 0
  Spare Devices : 1

         Layout : left-symmetric
     Chunk Size : 64K

           UUID : 93ae091b:b4aa0eb1:8e7c4951:0f0ba6be
         Events : 0.1324996

    Number   Major   Minor   RaidDevice State
       0       8       65        0      active sync   /dev/sde1
       1       8       81        1      active sync   /dev/sdf1
       2       8       97        2      active sync   /dev/sdg1
       3       8      113        3      active sync   /dev/sdh1
       4       8      129        4      active sync   /dev/sdi1
       5       8      145        5      active sync   /dev/sdj1
       6       8       33        6      active sync   /dev/sdc1

       7       8       49        -      spare   /dev/sdd1

```

Why is df reading the raid device as having much less available storage than what the GDM desktop and mdadm says? How do i get the system to recognize the correct drive space on the device?

---

