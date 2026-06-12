---
title: "raid5 problem after reinstall server"
date: 2009-08-03
forum: Server Platforms
---

### Post by albengy on 2009-08-03
First, I'm a newbie, and I'd made some stupid mistakes.
 
I have an external box with 4 HDs connect to addonics raid controller. I configured raid5 and everything worked, and transfered data to the new raid5 drive, but I had problem with some applications and decided to reinstall the server (ubuntu 8.10), forgetting to backup (stupid me), and now that my raid5 is gone. Is it still possible to get my raid5 back? I have some data that need to recover.
 
I tried this command and it shows:
 
sudo mdadm -E /dev/sdb
/dev/sdb:
Magic : a92b4efc
Version : 00.90.00
UUID : 3a18252f:231c699f:b62cfa25:81e9a18b (local to host bubuntu)
Creation Time : Fri Jul 3 07:38:26 2009
Raid Level : raid5
Used Dev Size : 1465138432 (1397.26 GiB 1500.30 GB)
Array Size : 4395415296 (4191.79 GiB 4500.91 GB)
Raid Devices : 4
Total Devices : 4
Preferred Minor : 0
Update Time : Sun Aug 2 17:02:16 2009
State : clean
Active Devices : 4
Working Devices : 4
Failed Devices : 0
Spare Devices : 0
Checksum : 2a92f905 - correct
Events : 4
Layout : left-symmetric
Chunk Size : 256K
Number Major Minor RaidDevice State
this 1 8 48 1 active sync /dev/sdd
0 0 8 16 0 active sync /dev/sdb
1 1 8 48 1 active sync /dev/sdd
2 2 8 32 2 active sync /dev/sdc
3 3 8 64 3 active sync /dev/sde
 
 
sudo mdadm --create /dev/md0 --assume-clean --level=5 --chunk=64 --raid-devices=4 /dev/sdb /dev/sdc /dev/sdd /dev/sde
mdadm: Cannot open /dev/sdb: Device or resource busy
mdadm: Cannot open /dev/sdc: Device or resource busy
mdadm: Cannot open /dev/sdd: Device or resource busy
mdadm: Cannot open /dev/sde: Device or resource busy
mdadm: create aborted

---

### Post by nunki on 2009-08-03
If you're trying to recover data, doesn't the command ```
mdadm --create 
``` wipe out all your data?

---

### Post by fjgaude on 2009-08-03
From the **-E** looks like everything is okay, so far.

Try doing this and then see if the array will mount:

```
sudo mdadm --examine --scan --config=mdadm.conf >> /etc/mdadm/mdadm.conf
```

And show us your **/etc/fstab** file.

Let us know what happens. Thanks!

---

### Post by albengy on 2009-08-03
sudo mdadm --examine --scan --config=mdadm.conf >> /etc/mdadm/md                                       adm.conf
-bash: /etc/mdadm/mdadm.conf: Permission denied

I had to switch to root user:
[EMAIL="root@bubuntu:/home/beta"]root@bubuntu:/home/beta[/EMAIL]# mdadm --examine --scan --config=mdadm.conf >> /etc                                       /mdadm/mdadm.conf

 
/etc/fstab
 
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=9b6dc28b-8116-4a03-a93f-13c37755f38e /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=e945e477-4747-437b-b4a9-cf39955b46a9 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0

 
Thanks for your help fjgaude!

---

### Post by albengy on 2009-08-03
yeah **[FONT=Arial][SIZE=2]nunki, I didn't know any better, I thought my raid was gone and tried to create it again. Somehow it said the disks were busy and the action was aborted.[/SIZE][/FONT]**

---

### Post by fjgaude on 2009-08-03
I see you don't have a mountpoint for the array setup in the fstab file. Did you ever?

Now, try to assemble the array:

```
sudo mdadm --assemble --scan
```

Just like that and let's see what the response is.

If the assemble doesn't work, please show us your **/etc/mdadm/mdadm.conf** file.

---

### Post by albengy on 2009-08-03
"I see you don't have a mountpoint for the array setup in the fstab file. Did you ever?"
    I reinstalled the last night and discovered that the raid5 dev, md0 is not there and I got panic and don't know what to do. It seems like the raid5 dev is there, but I don't know how to get ubuntu server to recognize after the fresh install.
 
Also, I wanted to see if the data is recoverable if somehow my system crash (due to hardward) and I have to rebuild (reinstall server) like in this case before I commit to add more data to the raid5 device. If I'm missing anything (alot so far), please help. Thanks again.

 
sudo mdadm --assemble --scan
[sudo] password for beta:
mdadm: no devices found for /dev/md0
 
 
sudo nano /etc/mdadm/mdadm.conf


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
# This file was auto-generated on Sun, 02 Aug 2009 21:23:32 -0700
# by mkconf $Id$
ARRAY /dev/md0 level=raid5 num-devices=4 UUID=3a18252f:231c699f:b62cfa25:81e9a18b

---

### Post by fjgaude on 2009-08-03
Very strange! The UUID for the array is as it should be the same as shown for your drive /dev/sdb from the -E showing.

Are you sure you have the drives physcially connected, powered on?

I see the mdadm.conf file was just created. Okay!

Show this:

```
sudo fdisk -l
```

From this we can see if the system has the drives mounted.

Say, you may have to reboot for things to work correctly.

---

### Post by albengy on 2009-08-03
Yes, the drives are connected and powered on, but somehow the system doesn't recognize /dev/md0
 
sudo fdisk -l
 
Disk /dev/sda: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000
Disk /dev/sda doesn't contain a valid partition table
Disk /dev/sdb: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000
Disk /dev/sdb doesn't contain a valid partition table
Disk /dev/sdc: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000
Disk /dev/sdc doesn't contain a valid partition table
Disk /dev/sdd: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000
Disk /dev/sdd doesn't contain a valid partition table
Disk /dev/sde: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000892e2
   Device Boot      Start         End      Blocks   Id  System
/dev/sde1               1       59856   480793288+  83  Linux
/dev/sde2           59857       60801     7590712+   5  Extended
/dev/sde5           59857       60801     7590681   82  Linux swap / Solaris

---

### Post by fjgaude on 2009-08-03
From the looks of the print out all the 1.5TB drives don't have partition tables... that's why mdadm doesn't see them. The disk identifiers are all listed the same as 0x00000000...

The controller for them may be bad... or something has happened that we don't know about. It's like there is no MBR or something like that.

I think you data is all lost... I would try to see if one drive can be made to have a filesystem on it, one partition. One of your drives:

Disk /dev/sda: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000
Disk /dev/sda doesn't contain a valid partition table

One of mind:

Disk /dev/sdc: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000521a0

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       38913   312568641   fd  Linux raid autodetect

You can see the difference!

Can you recall things that might have been done to get your results?

---

### Post by albengy on 2009-08-03
What I did was reinstalled the server. Actually I had ubuntu 9.04 server then decided to go with ubuntu 8.10 LTS. I had the warning regarding the table partition for each drive before too, but at least I was able to see the raid5 /dev/md0 and used it to store data. Maybe I didn't create raid5 correctly.
 
I have one more question: If I were to create raid5 for these 4 hds, and if something happen to the system and I have to install fresh copy of the server (due to hardware break down or some other problem), would be raid5 device still be intact and what command do I use to get it back?
 
Oh, another thing is that before, the 4 hd for the raid5 array was /dev/sdb, /dev/sdc, /dev/sdd, /dev/sde (these drive are 1.5T each) and the other hd for the system is 500Gb. The output for fdisk command is similar with all the warning about the partition table except for the dev name (the the array raid5 worked before). This time when I reinstalled the system, the system HD is named as /dev/sde, and the 4 hd for the raid5 arrays became /dev/sda, b, c, and d instead. Maybe that's why?
 
Thanks much.

---

### Post by fjgaude on 2009-08-03
First off, **mdadm** uses only the UUID for the array as first created to assemble, not the drive names.

The array can always be re-assembled after a motheboard, CPU, OS change using this simple command:

```
sudo mdadm --assemble --scan
```

With it a new **mdadm.conf** file will be automatically created. I've been using the same array through many changes, even going from an AMD CPU to an Intel one, new motherboard, etc.

It's doing the wrong thing to the array that usually does it in. It's the not-knowing what to do and then doing the wrong thing. Surprise!

BTW, always create a partition, even if it is the whole drive, before creating an array with mdadm.

Good luck! but do read all you can about mdadm first:

[http://linux-raid.osdl.org/index.php/Main_Page](http://linux-raid.osdl.org/index.php/Main_Page)
[http://www.hscripts.com/tutorials/linux-services/mdadm.html](http://www.hscripts.com/tutorials/linux-services/mdadm.html)

---

### Post by albengy on 2009-08-03
Thank you very much. I learned my lesson.

---

