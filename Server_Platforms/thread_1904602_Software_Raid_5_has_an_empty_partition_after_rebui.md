---
title: "Software Raid 5 has an empty partition after rebuilding"
date: 2012-01-05
forum: Server Platforms
---

### Post by Brigadieren on 2012-01-05
Folks please help - I am a newb with a major headache at hand (perfect storm situation:().

I have a 3 1tb hdd on my ubuntu 11.04 configured as software raid 5. The data had been copied weekly onto another separate off the computer hard drive until that completely failed. A few days back we had a power outage and after rebooting my box wouldn't mount the raid. In my infinite wisdom I entered 

mdadm **[COLOR="Red"]--create[/COLOR]** -f... 

command instead of 

mdadm --assemble 

and didn't notice the travesty that I had done until after. It started the array degraded and proceeded with building it which took ~10 hours. After I was back I saw that that the array is successfully up and running but the raid is not 

I mean the individual drives are partitioned (partition type f8 ) but the md0 device is not. Realizing in horror what I have done I am trying to find some solutions. I just pray that --create didn't overwrite entire content of the hard drivers...

Could someone PLEASE help me out with this - the data that's on the drive is very important and unique:(.

Is it possible that by specifying the participating hard drives in wrong order can make mdadm overwrite them? when I do 

mdadm --examine --scan 

I get something like *ARRAY /dev/md/0 metadata=1.2 UUID=f1b4084a:720b5712:6d03b9e9:43afe51b name=<hostname>:0*

Interestingly enough name used to be 'raid' and not the host hame with :0 appended.

Here is the 'sanitized' config entries:

[I]DEVICE /dev/sdf1 /dev/sde1 /dev/sdd1

CREATE owner=root group=disk mode=0660 auto=yes

HOMEHOST <system>

MAILADDR root


ARRAY /dev/md0 metadata=1.2 name=tanserv:0 UUID=f1b4084a:720b5712:6d03b9e9:43afe51b[/I]


Here is the output from mdstat

[I]cat /proc/mdstat 
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md0 : active raid5 sdd1[0] sdf1[3] sde1[1]
      1953517568 blocks super 1.2 level 5, 512k chunk, algorithm 2 [3/3] [UUU]
      
unused devices: <none>[/I]


fdisk shows the following:

[I]fdisk -l

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000bf62e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9443    75846656   83  Linux
/dev/sda2            9443        9730     2301953    5  Extended
/dev/sda5            9443        9730     2301952   82  Linux swap / Solaris

Disk /dev/sdb: 750.2 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000de8dd

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       91201   732572001   8e  Linux LVM

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00056a17

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       60801   488384001   8e  Linux LVM

Disk /dev/sdd: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000ca948

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1      121601   976760001   fd  Linux raid autodetect

Disk /dev/dm-0: 1250.3 GB, 1250254913536 bytes
255 heads, 63 sectors/track, 152001 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

**Disk /dev/dm-0 doesn't contain a valid partition table**

Disk /dev/sde: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x93a66687

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1               1      121601   976760001   fd  Linux raid autodetect

Disk /dev/sdf: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xe6edc059

   Device Boot      Start         End      Blocks   Id  System
/dev/sdf1               1      121601   976760001   fd  Linux raid autodetect

Disk /dev/md0: 2000.4 GB, 2000401989632 bytes
2 heads, 4 sectors/track, 488379392 cylinders
Units = cylinders of 8 * 512 = 4096 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 524288 bytes / 1048576 bytes
Disk identifier: 0x00000000

**[COLOR="Red"]Disk /dev/md0 doesn't contain a valid partition table[/COLOR]**[/I]


Any suggestions?

Regards!

---

### Post by rubylaser on 2012-01-05
mdadm arrays don't typically have a partition on them as there's really no reason for it.  You just add a filesystem to the  block device.  Have you tried to mount your /dev/md0 yet? Something like this as a test (if you used the ext4 filesystem).

```
sudo mount /dev/md0 /mnt/
cd /mnt
ls 
```

Typically, the create action is not destructive and mdadm will recognize there's data on the disks and just recreate the metadata for the array.  Do you have a copy of your previous /etc/mdadm/mdadm.conf/

```
cat /etc/mdadm/mdadm.conf
```

---

### Post by Brigadieren on 2012-01-05
Hi rubylaser,

Here is the output from mount


[I]mount: wrong fs type, bad option, bad superblock on /dev/md0,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so[/I]

The mdadm.conf content is the following:


[I]# mdadm.conf
#
# Please refer to mdadm.conf(5) for information about this file.
#

# by default, scan all partitions (/proc/partitions) for MD superblocks.
# alternatively, specify devices to scan, using wildcards if desired.
DEVICE /dev/sdf1 /dev/sde1 /dev/sdd1

# auto-create devices with Debian standard permissions
CREATE owner=root group=disk mode=0660 auto=yes

# automatically tag new arrays as belonging to the local system
HOMEHOST <system>

# instruct the monitoring daemon where to send mail alerts
MAILADDR root

# definitions of existing MD arrays
# ARRAY /dev/md0 level=raid5 num-devices=3 metadata=01.02 name=:raid UUID=3ee14c78:2b107a76:964a1a96:1734e867 devices=/dev/sdf1,/dev/sde1,/dev/sdd1

ARRAY /dev/md0 metadata=1.2 name=tanserv:0 UUID=f1b4084a:720b5712:6d03b9e9:43afe51b

# This file was auto-generated on Tue, 19 Apr 2011 22:30:27 -0700
# by mkconf $Id$[/I]

It seems that from the last time the UUID has changed or something. Also, it changed the name from raid to tanserv:0 

I truly hope I can revive the data = 10+ years worth of photos + docs:(:(:(

PLEASE HELP

---

### Post by Brigadieren on 2012-01-05
Also, I wonder does the order have to do with anything? I believe the original raid was created with specifying /dev/sdf1 /dev/sde1 /dev/sdd1 but now when I run

mdadm --detail --scan -v 

I get the following output


[I]ARRAY /dev/md0 level=raid5 num-devices=3 metadata=1.2 name=tanserv:0 UUID=f1b4084a:720b5712:6d03b9e9:43afe51b
   devices=/dev/sdd1,/dev/sde1,/dev/sdf1[/I]

Could the order be an issue here? How to specify the right order?

---

### Post by rubylaser on 2012-01-06
Your /etc/mdadm/mdadm.conf file is not correct at this point, but you can fix that easily later if you can get this working first.  When you recreated the array, it used the newer metadata version that your array was orginally created with.  This is really about the best way to put it back at this point. But, I'm guessing since you created a new array with a newer metadata version and didn't pass the assume clean option, it hosed your existing filesystem and the data on it (I've never tried this in a virtual machine before) :(

```
mdadm --stop /dev/md0
```
```
mdadm --zero-superblock /dev/sd[def]1
```
```
mdadm --create /dev/md0 --assume-clean --level=5 --raid-devices=3 /dev/sd[def]1 --metadata=1.02
```

If that works, you can recreate your mdadm.conf file like this (leave the partitions in there rather than device names).

```
echo "DEVICE partitions" > /etc/mdadm/mdadm.conf
echo "HOMEHOST fileserver" >> /etc/mdadm/mdadm.conf
echo "MAILADDR  youruser@gmail.com" >> /etc/mdadm/mdadm.conf
mdadm --detail --scan >> /etc/mdadm/mdadm.conf
```

---

### Post by Brigadieren on 2012-01-06
Hmm, thanks a lot. I will give it a try and will report back. Co-incidentally, does anyone have any recommendation of any raid recovery tools that can help in this situation? 

If I know what mdadm has done to the drives after 're-creating' the raid 5, given the layout (which I don't know at this point) I can write some software to extract the data by 'un-doing' what's been done.

Thanks

---

### Post by Vegan on 2012-01-06
I have to mention, next time have a backup

Lots of options, get one and use it

---

### Post by Brigadieren on 2012-01-07
Hi rubylaser,

I re-created the array with --assume-clean after zero-ing the superblock and the result is the same - the raid shows as not partitioned. Do you guys know of any other remedy? Do you know if there are any tools that can un-do what create had done? Does anyone know what exactly create had done so I can write en un-do tool or something?

Vegan, you won't believe me but my backup drive got physically damaged just couple of weeks ago... What could go wrong did go wrong:(.

Any suggestions at this stage are very much appreciated.

---

### Post by rubylaser on 2012-01-08
> **Brigadieren said:**
> Hi rubylaser,

I re-created the array with --assume-clean after zero-ing the superblock and the result is the same - the raid shows as not partitioned. Do you guys know of any other remedy? Do you know if there are any tools that can un-do what create had done? Does anyone know what exactly create had done so I can write en un-do tool or something?

Vegan, you won't believe me but my backup drive got physically damaged just couple of weeks ago... What could go wrong did go wrong:(.

Any suggestions at this stage are very much appreciated.

The array is not going to show up as partitioned. 99.9% of people (estimate :) ) do not put a partition on mdadm arrays because they are unnecessary.  There is no "undo" tool, you're working with a block level device.  If the data is screwed up by user error, it's gone.  If none of the above worked, I can very confidently say that your data is gone and not recoverable.  

I don't like to rub salt on wounds, but as Vegan said, a good backup could have prevented this.  Even with the disks failing only a few weeks ago, you could have had time to RMA the defective disks or buy new ones.

---

