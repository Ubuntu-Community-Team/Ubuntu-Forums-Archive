---
title: "LVM2 does not recognize /dev/md1 anymore"
date: 2011-06-26
forum: Server Platforms
---

### Post by mxu on 2011-06-26
Hi, all,

Recently I have upgraded my home file server from ubuntu 10.10 to 11.04. I found my LVM+RAID5 does not work any more. Here are stuff I have explored so far


[COLOR=Blue] $sudo lvdisplay
  --- Logical volume ---
  LV Name                /dev/fsvr_main/var
  VG Name                fsvr_main
  LV UUID                Lhq14y-cLVy-lwv1-B4NU-twj2-MQdU-Lws7Xf
  LV Write Access        read/write
  LV Status              suspended
  # open                 0
  LV Size                3.71 TiB
  Current LE             971400
  Segments               1
  Allocation             inherit
  Read ahead sectors     auto
  - currently set to     256
  Block device           252:0
   
[/COLOR]
lvdisplay indicates that LV is suspended. I try to activate LV by
[COLOR=Blue] $ sudo lvchange -ay /dev/fsvr_main/var
  device-mapper: resume ioctl failed: Invalid argument
  Unable to resume fsvr_main-var (252:0)
[/COLOR] 
/var/log/syslog reports:
[COLOR=Blue] kernel: [  974.845365] device-mapper: table: 252:0: md1p1 too small for target: start=384, len=7957708800, dev_size=3907024002
[/COLOR] 

indicating that the recorded size of volume is different to the real size.

Furthermore I found 

[COLOR=Blue] $ sudo pvdisplay 
  --- Physical volume ---
  PV Name               /dev/md1p1
  VG Name               fsvr_main
  PV Size               5.46 TiB / not usable 3.31 MiB
  Allocatable           yes 
  PE Size               4.00 MiB
  Total PE              1430794
  Free PE               459394
  Allocated PE          971400
  PV UUID               EO3XiB-KMWn-nn7i-oAcs-4A2F-Q2eJ-hbTJ1J


[/COLOR]     This indicates the PV is assigned to /dev/md1p1

However, when I originally create this PV, I used /dev/md1 not /dev/md1p1

So I try to remove PV label of /dev/md1p1 by

[COLOR=Blue]sudo pvremove -ff /dev/md1p1
[/COLOR] 
and create PV metadata on /dev/md1 by

[COLOR=Blue]sudo pvcreate --uuid "EO3XiB-KMWn-nn7i-oAcs-4A2F-Q2eJ-hbTJ1J" --restorefile /etc/lvm/archive/fsvr_main_00016.vg /dev/md1
  Couldn't find device with uuid EO3XiB-KMWn-nn7i-oAcs-4A2F-Q2eJ-hbTJ1J.
  Device /dev/md1 not found (or ignored by filtering).

[/COLOR]  
Which indicates that /dev/md1 is not recognized, even through the filter option in /etc/lvm/lvm.conf is default.


Here are details of my RAID5

[COLOR=Blue]sudo mdadm --detail /dev/md1
/dev/md1:
        Version : 00.90
  Creation Time : Tue Sep 21 23:49:57 2010
     Raid Level : raid5
     Array Size : 5860543488 (5589.05 GiB 6001.20 GB)
  Used Dev Size : 1953514496 (1863.02 GiB 2000.40 GB)
   Raid Devices : 4
  Total Devices : 4
Preferred Minor : 1
    Persistence : Superblock is persistent

    Update Time : Sun Jun 26 15:32:00 2011
          State : clean
 Active Devices : 4
Working Devices : 4
 Failed Devices : 0
  Spare Devices : 0

         Layout : left-symmetric
     Chunk Size : 64K

           UUID : 63f9024b:ad62c004:c2ca5516:a7a98e62
         Events : 0.54

    Number   Major   Minor   RaidDevice State
       0       8       32        0      active sync   /dev/sdc
       1       8       48        1      active sync   /dev/sdd
       2       8        0        2      active sync   /dev/sda
       3       8       16        3      active sync   /dev/sdb


$ sudo mdadm --detail /dev/md1p1
/dev/md1p1:
        Version : 00.90
  Creation Time : Tue Sep 21 23:49:57 2010
     Raid Level : raid5
     Array Size : 1953512001 (1863.01 GiB 2000.40 GB)
  Used Dev Size : 1953514496 (1863.02 GiB 2000.40 GB)
   Raid Devices : 4
  Total Devices : 4
Preferred Minor : 1
    Persistence : Superblock is persistent

    Update Time : Sun Jun 26 16:00:21 2011
          State : clean
 Active Devices : 4
Working Devices : 4
 Failed Devices : 0
  Spare Devices : 0

         Layout : left-symmetric
     Chunk Size : 64K

           UUID : 63f9024b:ad62c004:c2ca5516:a7a98e62
         Events : 0.54

    Number   Major   Minor   RaidDevice State
       0       8       32        0      active sync   /dev/sdc
       1       8       48        1      active sync   /dev/sdd
       2       8        0        2      active sync   /dev/sda
       3       8       16        3      active sync   /dev/sdb


[/COLOR]

I am still pretty new to LVM and RAID. I don't know where /dev/md1p1 come from and why /dev/md1 is not recognized by lvm any more.
Any suggestions? 

Best,
M

---

### Post by rubylaser on 2011-06-26
Did you create a partition on your array?  That's typically where the p1 would come from, or your array is not assembling itself properly. What do you have in your /etc/mdadm/mdadm.conf file?

```
cat /etc/mdadm/mdadm.conf
```

---

### Post by mxu on 2011-06-26
Hi, [rubylaser]("http://ubuntuforums.org/member.php?u=1115132"),

Thanks a lot for reply. I did not create any partition on my array at all. Before upgrading, I belive there was no /dev/md1p1. After upgrading, I noticed the existence of /dev/md1p1. 

as for mdadm.conf, because I noticed that 

[COLOR=Blue]$ sudo mdadm --examine --scan --verbose
ARRAY /dev/md1 level=raid5 num-devices=4 UUID=63f9024b:ad62c004:c2ca5516:a7a98e62
   devices=/dev/sda,/dev/sdb,/dev/sdc,/dev/sdd
[/COLOR][COLOR=Blue]ARRAY /dev/md1 level=raid5 num-devices=4 UUID=[/COLOR][COLOR=Blue]183aafcf:edb61e3b:b1a61967:6827a389[/COLOR]
[COLOR=Blue]    devices=/dev/sda1,/dev/sdb1,/dev/sdc1,/dev/sdd1
[/COLOR]
But seems [COLOR=Blue]/dev/md1[COLOR=Black] should [/COLOR][/COLOR]be assembled from partitions of the hard drives, so I have modified /etc/mdadm/mdadm.conf  to prevent /dev/md1 to be assembled from whole hard drives. Here is contend of /etc/mdadm/mdadm.conf

[COLOR=Blue]# mdadm.conf
#
# Please refer to mdadm.conf(5) for information about this file.
#

# by default, scan all partitions (/proc/partitions) for MD superblocks.
# alternatively, specify devices to scan, using wildcards if desired.
#DEVICE partitions
DEVICE /dev/sd?1
#DEVICE /dev/sda /dev/sdb /dev/sdc /dev/sdd

# auto-create devices with Debian standard permissions
CREATE owner=root group=disk mode=0660 auto=yes

# automatically tag new arrays as belonging to the local system
HOMEHOST <system>

# instruct the monitoring daemon where to send mail alerts
MAILADDR root

# definitions of existing MD arrays
#ARRAY /dev/md1 level=raid5 num-devices=4 UUID=63f9024b:ad62c004:c2ca5516:a7a98e62
ARRAY /dev/md1 level=raid5 num-devices=4 UUID=183aafcf:edb61e3b:b1a61967:6827a389

# This file was auto-generated on Sun, 26 Jun 2011 15:22:27 -0700
# by mkconf $Id$





[/COLOR]

---

### Post by rubylaser on 2011-06-27
This is why I try to avoid LVM on top of mdadm, troubleshooting is a pain :) But, let's see if we can figure this out.  mdadm is tried to use the whole disk at some point instead of the disk partitions that you setup.

First, I'd stop all running arrays.
```
mdadm --stop /dev/md1
mdadm --stop /dev/md1p1
```

Then, I'd assemble your array yourself
```
mdadm -A /dev/md1 /dev/sd[abcd]1
```

Then, I'd recreate your /etc/mdadm/mdadm.conf file like this...
```
echo "DEVICE partitions" > /etc/mdadm/mdadm.conf
echo "HOMEHOST fileserver" >> /etc/mdadm/mdadm.conf
echo "MAILADDR root@localhost" >> /etc/mdadm/mdadm.conf
mdadm --detail --scan >> /etc/mdadm/mdadm.conf
```

Check your /etc/mdadm/mdadm.conf file at this point and make sure there's only one ARRAY line, and that it is the correct UUID.

```
cat /etc/mdadm/mdadm.conf
```
**If you have the correct ARRAY, and only one, then proceed, otherwise we'll have to try something else and you'll want to stop here.**

Next, I'd reconfigure mdadm
```
dpkg-reconfigure mdadm
```

Finally,
```
update-initramfs -u -k all
```

---

### Post by mxu on 2011-06-27
Thank you so much [rubylaser]("http://ubuntuforums.org/member.php?u=1115132"). Your guidance is very helpful. Now my RAID can correctly assembled, and my LVM works. Yes, I also found LVM+software RAID brings a lot of trouble. I will get raid of LVM once I get an extra hard drive that is big enough to move files.  Thanks again!!

---

### Post by rubylaser on 2011-06-27
Glad to be of service :) Please mark the thread as solved with the Thread tools at the top.

---

