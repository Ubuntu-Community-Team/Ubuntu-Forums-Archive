---
title: "Ubuntu 8.04.3 Raid Problem"
date: 2009-12-06
forum: Server Platforms
---

### Post by sndnichols on 2009-12-06
After building the raid (raid5) with mdadm and rebooting, I get this message:The kernel RAID status file /proc/mdstat does not exist on your system. Your kernel probably does not support RAID. I ran modprobe md-mod and got no feedback, so I assumed the module is available.  I rebuilt it thinking I had missed something, well the same message showed up. Can anyone explain this?

Here is /etc/fstab:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdf2
UUID=9ebf12d2-6ad5-4ffa-b379-f196ed2c5327 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sdf1
UUID=23fb61e8-2e72-4d22-8965-4f873229b7ad /boot           ext3    relatime        0       2
# /dev/md1
/dev/md1 /home            auto     defaults       0       0
# /dev/sdf8
UUID=eb0440fa-af0e-4359-94ff-d6d535bd9ffd /media          ext3    relatime        0       2
# /dev/sdf9
UUID=d698cb3b-1904-4161-a65d-443c4df44a35 /opt            ext3    relatime        0       2
# /dev/sdf7
UUID=47418e01-41bb-4d1b-9624-15582f966d9b /srv            ext3    relatime        0       2
# /dev/sdf5
UUID=65a4f6f4-6352-440c-a842-ae16174962f4 /tmp            ext3    relatime        0       2
# /dev/sdf10
UUID=32943528-a8bb-4f20-81b5-cdffdfb4221e /usr            ext3    relatime        0       2
# /dev/md0
/dev/md0 /usr/local       auto    defaults        0       0
# /dev/sdf6
UUID=d7f34f6f-78c3-4254-99a1-e3b3adcdf112 /var            ext3    relatime        0       2
# /dev/sda7
UUID=d95c1085-0405-4862-8a5c-c9e23633145c  none            swap    sw              0       0
# /dev/sdb7
UUID=48daf326-6355-48ba-95fc-2d6aabe81514  none            swap    sw              0       0
# /dev/sdc7
UUID=a660b998-9a37-4937-b4a5-d09aa3cd22ec  none            swap    sw              0       0
# /dev/sdd7
UUID=46053d1f-28af-46e4-9906-9538ed137721 none             swap    sw              0       0
# /dev/sde7
UUID=21a6e147-e920-4599-8933-bb39765330f7 pri=1  none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0


Here is the mdadm.conf

# mdadm.conf
#
# Please refer to mdadm.conf(5) for information about this file.
#

# by default, scan all partitions (/proc/partitions) for MD superblocks.
# alternatively, specify devices to scan, using wildcards if desired.
#DEVICE partitions
DEVICE /dev/sda5 /dev/sdb5 /dev/sdc5 /dev/sdd5 /dev/sde5
DEVICE /dev/sda6 /dev/sdb6 /dev/sdc6 /dev/sdd6 /dev/sde6

# auto-create devices with Debian standard permissions
CREATE owner=root group=disk mode=0660 auto=yes

# automatically tag new arrays as belonging to the local system
HOMEHOST <system>

# instruct the monitoring daemon where to send mail alerts
MAILADDR [email]sndnichols@gmail.com[/email]

# definitions of existing MD arrays
ARRAY /dev/md0 UUID=f90716c3-0ccf149e-e20b3d4d-b9df07ab
ARRAY /dev/md1 UUID=ed0ccab0:f51bdfab:e20b3d4d:b9df07ab


Here is the fdisk -l

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0001b6b0

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1      121591   976679676    5  Extended
/dev/sda5               1       50000   401624937   fd  Linux raid autodetect
/dev/sda6           50001      121591   575054676   fd  Linux raid autodetect

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00073ea3

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1      121591   976679676    5  Extended
/dev/sdb5               1       50000   401624937   fd  Linux raid autodetect
/dev/sdb6           50001      121591   575054676   fd  Linux raid autodetect

Disk /dev/sdc: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000d6fba

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1      121591   976679676    5  Extended
/dev/sdc5               1       50000   401624937   fd  Linux raid autodetect
/dev/sdc6           50001      121591   575054676   fd  Linux raid autodetect

Disk /dev/sdd: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000429b7

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1      121591   976679676    5  Extended
/dev/sdd5               1       50000   401624937   fd  Linux raid autodetect
/dev/sdd6           50001      121591   575054676   fd  Linux raid autodetect

Disk /dev/sde: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00051d07

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1               1      121591   976679676    5  Extended
/dev/sde5               1       50000   401624937   fd  Linux raid autodetect
/dev/sde6           50001      121591   575054676   fd  Linux raid autodetect

Disk /dev/sdf: 73.4 GB, 73407820800 bytes
255 heads, 63 sectors/track, 8924 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x570ad0cb

   Device Boot      Start         End      Blocks   Id  System
/dev/sdf1   *           1          40      321268+  83  Linux
/dev/sdf2              41        2650    20964825   83  Linux
/dev/sdf3            2651        8924    50395905    5  Extended
/dev/sdf5            2651        3310     5301418+  83  Linux
/dev/sdf6            3311        4700    11165143+  83  Linux
/dev/sdf7            4701        4850     1204843+  83  Linux
/dev/sdf8            4851        5000     1204843+  83  Linux
/dev/sdf9            5001        5608     4883728+  83  Linux
/dev/sdf10           5609        8924    26635738+  83  Linux


After the first failure I reset the superblock using mdadm --zero-superblock /dev/sda /dev/sdb /dev/sdc /dev/sdd /dev/sde.

Here is the command I used to create the raid: mdadm --create /dev/md0 --level=5 --raid-devices=5 /dev/sda5 /dev/sdb5 /dev/sdc5 /dev/sdd5 /dev/sde5

I am at a loss and somewhat frustrated. I have looked for almost a week to figure this out. Thanks for any help you can give.

---

### Post by sndnichols on 2009-12-07
After reboot I run modprobe mda-mod, then I ran mdadm --assemble --scan and the raid is back. I have a separate root partition. It is not flagged as bootable. Could this be the problem?

---

### Post by sndnichols on 2009-12-10
No ideas?

---

