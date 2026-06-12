---
title: "Software RAID"
date: 2010-08-04
forum: Server Platforms
---

### Post by Jaken Veina on 2010-08-04
Can someone please describe to me the proper procedure to set up a Software RAID Array. I'm now 50 hours into this project to utilize 6 new 2TB hard drives as as 10TB RAID 5 array, and I'm really getting fed up with the endless searching and incomplete solutions and nothing working the way it should for long. As a primarily virgin Linux user, I've learned quite a lot this past week, but at this point I'm tired of learning. I just want this project to be done.

What I have is 6 2TB Hard Drives, devices sda through sdf, running Ubuntu 10.04 minimal on an 80GB sdg. 

The process I've come up with is this:
 - (parted) select sda
 - (parted) mklabel gpt
 - (parted) mkpart primary ext2 1M 2000G
 - (parted) set 1 raid on
 --- Repeat for sdb -> sdf
 - mdadm --create /dev/md0 --level=5 --raid-devices=6 sda1 sdb1 sdc1 sdd1 sde1 sdf1
 - mkfs -t ext3 /dev/md0
 - mount -t ext3 /dev/md0 /data

This procedure has worked once, but upon reboot md0 has disappeared, replaced by md_d0, md_d0p1, md_d0p2, md_d0p3, and md_d0p4. The partition tables are intact, but running mdadm to create md0 again fails, on account of the drives being used by (I can only assume) md_d0 and the rest, although according to mdadm, md_d0 is not actually running, and mdadm yields no information on the other 4 devices. This happened once before and I couldn't find squat online about why these items showed up, what they were, or how to get rid of them, and I eventually had to do a fresh install.

What am I missing here?

---

### Post by kevin11951 on 2010-08-04
have you tried installing webmin and using its raid gui?

---

### Post by Jaken Veina on 2010-08-04
Currently, the machine is command-line only. Perhaps I'm just being a bit stubborn in trying to keep it that way, but if no other thoughts come up, that'll be my next step. webmin is the package?

---

### Post by kevin11951 on 2010-08-04
> **Jaken Veina said:**
> Currently, the machine is command-line only. Perhaps I'm just being a bit stubborn in trying to keep it that way, but if no other thoughts come up, that'll be my next step. webmin is the package?

webmin is a web gui, so it will only use resources when you actually connect to it, and your servers stays cli.  Though its not in the repos, it is open source.

to install it (my way):

```
sudo -i

wget 'http://downloads.sourceforge.net/project/webadmin/webmin/1.510/webmin_1.510-2_all.deb?use_mirror=iweb&ts=1280909807&r=http://www.webmin.com/'

apt-get install gdebi-core

gdebi webmin_1.510-2_all.deb
```

Then you can access it via https://<server-ip>:10000

---

### Post by kevin11951 on 2010-08-04
For raid, go to "Hardware > Linux RAID"

It's pretty simple from there.  Let me know if you have trouble.

---

### Post by jacekk015 on 2010-08-04
> **Jaken Veina said:**
> Can someone please describe to me the proper procedure to set up a Software RAID Array. I'm now 50 hours into this project to utilize 6 new 2TB hard drives as as 10TB RAID 5 array, and I'm really getting fed up with the endless searching and incomplete solutions and nothing working the way it should for long. As a primarily virgin Linux user, I've learned quite a lot this past week, but at this point I'm tired of learning. I just want this project to be done.

What I have is 6 2TB Hard Drives, devices sda through sdf, running Ubuntu 10.04 minimal on an 80GB sdg. 

The process I've come up with is this:
 - (parted) select sda
 - (parted) mklabel gpt
 - (parted) mkpart primary ext2 1M 2000G
 - (parted) set 1 raid on
 --- Repeat for sdb -> sdf
 - mdadm --create /dev/md0 --level=5 --raid-devices=6 sda1 sdb1 sdc1 sdd1 sde1 sdf1
 - mkfs -t ext3 /dev/md0
 - mount -t ext3 /dev/md0 /data

This procedure has worked once, but upon reboot md0 has disappeared, replaced by md_d0, md_d0p1, md_d0p2, md_d0p3, and md_d0p4. The partition tables are intact, but running mdadm to create md0 again fails, on account of the drives being used by (I can only assume) md_d0 and the rest, although according to mdadm, md_d0 is not actually running, and mdadm yields no information on the other 4 devices. This happened once before and I couldn't find squat online about why these items showed up, what they were, or how to get rid of them, and I eventually had to do a fresh install.

What am I missing here?


Give results of:
```
cat /etc/mdadm/mdadm.conf
and
cat /etc/fstab
```I'm shooting that after create RAID you didn't add needed info to mdadm.conf

[edit]
By the way - there is no need to create partitions for devices that will be only used in RAID.
You could only add devices like /dev/sda, /dev/sdb and etc...

For performance reasons you should define use of this big array. What sizes of files will be mostly used and etc.
That infos should be used to proper define STRIPE size of RAID5 and STRIDE parameter for mkfs ext3.

---

### Post by Jaken Veina on 2010-08-04
What I'm setting up is a large-scale storage server, lots of reads, very, very few writes, and primarily large video files. And editing mdadm.conf would definately be the step I missed; none of the info online mentioned that I would need to edit any config files manually. I'll look into that.

And I very much like the idea of a web GUI. Thanks. I'll try it out when I get home tonight.

---

### Post by Jaken Veina on 2010-08-04
Ended up breaking grub trying to fix a hanging problem, so I went ahead and did another fresh install, only this time around, after setting up the raid array, I didn't mistakenly install grub on one of the raid drives, rather than my OS drive, which is what forced me to have to configure mdadm from the command line last time. Everything works great, and upon inspection, the installer created an ARRAY entry in mdadm.conf for the array, which seems to be the only thing I was missing. I've since build an ext4 file system on the array and set a permanent mount point, and after several more reboots, I've had no problems.

Thanks a bunch for the tips.

---

### Post by doogy2004 on 2010-08-04
Here is some documentation that I have written look in the section titled - Create Raid Array with LVM2 Volume Inside

[http://www.google.com/notebook/public/04497302348663211786/BDQzTSwoQtNGpob4i](http://www.google.com/notebook/public/04497302348663211786/BDQzTSwoQtNGpob4i)

the LVM portions are optional, but it is step by step.

NOTE: As far as I know grub cannot boot into a Software RAID array, because mdadm must be running and that doesn't happen till after the kernel has started running.

---

### Post by jacekk015 on 2010-08-05
GRUB can be installed only on RAID1
[https://help.ubuntu.com/10.04/serverguide/C/advanced-installation.html](https://help.ubuntu.com/10.04/serverguide/C/advanced-installation.html)

---

### Post by rubylaser on 2010-08-05
Did you get this working via webmin?  I've never used Webmin for mdadm tasks.  If you still haven't been successful, here are some quick copy and paste directions to get it working.

You'll want to fdisk each of those drives, and delete all existing partitions with fdisk (obviously backup any data on them first).  Then I use fdisk create a new partition id, and set it and linux raid like this...
```
server1:~# sudo fdisk /dev/sdb

The number of cylinders for this disk is set to 10443.
There is nothing wrong with that, but this is larger than 1024,
and could in certain setups cause problems with:
1) software that runs at boot time (e.g., old versions of LILO)
2) booting and partitioning software from other OSs
(e.g., DOS FDISK, OS/2 FDISK)

Command (m for help): [COLOR="Red"]<-- m[/COLOR]
Command action
  a   toggle a bootable flag
  b   edit bsd disklabel
  c   toggle the dos compatibility flag
  d   delete a partition
  l   list known partition types
  m   print this menu
  n   add a new partition
  o   create a new empty DOS partition table
  p   print the partition table
  q   quit without saving changes
  s   create a new empty Sun disklabel
  t   change a partition's system id
  u   change display/entry units
  v   verify the partition table
  w   write table to disk and exit
  x   extra functionality (experts only)

Command (m for help): [COLOR="red"]<-- n[/COLOR]
Command action
  e   extended
  p   primary partition (1-4)
[COLOR="red"]<-- p[/COLOR]
Partition number (1-4): [COLOR="red"]<-- 1[/COLOR]
First cylinder (1-10443, default 1): [COLOR="red"]<-- <ENTER>[/COLOR]
Using default value 1
Last cylinder or +size or +sizeM or +sizeK (1-10443, default 10443): [COLOR="red"]<-- <ENTER>[/COLOR]
 
Command (m for help): [COLOR="red"]<-- t[/COLOR]
Selected partition 1
Hex code (type L to list codes): [COLOR="red"]<-- L[/COLOR]

0  Empty           1e  Hidden W95 FAT1 80  Old Minix       be  Solaris boot
1  FAT12           24  NEC DOS         81  Minix / old Lin bf  Solaris
2  XENIX root      39  Plan 9          82  Linux swap / So c1  DRDOS/sec (FAT-
3  XENIX usr       3c  PartitionMagic  83  Linux           c4  DRDOS/sec (FAT-
4  FAT16 <32M      40  Venix 80286     84  OS/2 hidden C:  c6  DRDOS/sec (FAT-
5  Extended        41  PPC PReP Boot   85  Linux extended  c7  Syrinx
6  FAT16           42  SFS             86  NTFS volume set da  Non-FS data
7  HPFS/NTFS       4d  QNX4.x          87  NTFS volume set db  CP/M / CTOS / .
8  AIX             4e  QNX4.x 2nd part 88  Linux plaintext de  Dell Utility
9  AIX bootable    4f  QNX4.x 3rd part 8e  Linux LVM       df  BootIt
a  OS/2 Boot Manag 50  OnTrack DM      93  Amoeba          e1  DOS access
b  W95 FAT32       51  OnTrack DM6 Aux 94  Amoeba BBT      e3  DOS R/O
c  W95 FAT32 (LBA) 52  CP/M            9f  BSD/OS          e4  SpeedStor
e  W95 FAT16 (LBA) 53  OnTrack DM6 Aux a0  IBM Thinkpad hi eb  BeOS fs
f  W95 Ext'd (LBA) 54  OnTrackDM6      a5  FreeBSD         ee  EFI GPT
10  OPUS            55  EZ-Drive        a6  OpenBSD         ef  EFI (FAT-12/16/
11  Hidden FAT12    56  Golden Bow      a7  NeXTSTEP        f0  Linux/PA-RISC b
12  Compaq diagnost 5c  Priam Edisk     a8  Darwin UFS      f1  SpeedStor
14  Hidden FAT16 <3 61  SpeedStor       a9  NetBSD          f4  SpeedStor
16  Hidden FAT16    63  GNU HURD or Sys ab  Darwin boot     f2  DOS secondary
17  Hidden HPFS/NTF 64  Novell Netware  b7  BSDI fs         fd  Linux raid auto
18  AST SmartSleep  65  Novell Netware  b8  BSDI swap       fe  LANstep
1b  Hidden W95 FAT3 70  DiskSecure Mult bb  Boot Wizard hid ff  BBT
1c  Hidden W95 FAT3 75  PC/IX
Hex code (type L to list codes): [COLOR="red"]<-- fd[/COLOR]
Changed system type of partition 1 to fd (Linux LVM)

Command (m for help): [COLOR="red"]<-- w[/COLOR]
The partition table has been altered!
 
Calling ioctl() to re-read partition table.
Syncing disks.
```

After fdisking each of them, they should look like this...
```
raidtest:~# fdisk -l

Disk /dev/sda: 5368 MB, 5368709120 bytes
255 heads, 63 sectors/track, 652 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          12       96358+  83  Linux
/dev/sda2              13         652     5140800    5  Extended
/dev/sda5              13         134      979933+  82  Linux swap / Solaris
/dev/sda6             135         652     4160803+  83  Linux

Disk /dev/sdb: 21.4 GB, 21474836480 bytes
255 heads, 63 sectors/track, 2610 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
 
  Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        2610    20964793+  fd  Linux raid autodetect
 
Disk /dev/sdc: 21.4 GB, 21474836480 bytes
255 heads, 63 sectors/track, 2610 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

  Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1        2610    20964793+  fd  Linux raid autodetect

Disk /dev/sdd: 21.4 GB, 21474836480 bytes
255 heads, 63 sectors/track, 2610 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

  Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1        2610    20964793+  fd  Linux raid autodetect
 
Disk /dev/sde: 21.4 GB, 21474836480 bytes
255 heads, 63 sectors/track, 2610 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

  Device Boot      Start         End      Blocks   Id  System
/dev/sde1               1        2610    20964793+  fd  Linux raid autodetect
 
Disk /dev/sdf: 21.4 GB, 21474836480 bytes
255 heads, 63 sectors/track, 2610 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

  Device Boot      Start         End      Blocks   Id  System
/dev/sdf1               1        2610    20964793+  fd  Linux raid autodetect
```

Then, you could use your mdadm create line...

```
sudo mdadm --create /dev/md0 --chunk=512 --level=raid5 --raid devices=8 /dev/sd[abdef]1
```

mdadm will automatically assemble the array for you and begin syncing the disks.  I usually do this to watch it build...
```
watch cat /proc/mdstat
```

When it's done syncing, you can add the filesystem,

```
sudo mkfs.ext4 /dev/md0

```

Hope that helps.

Your array will be working after this, and have a filesystem, so you'll just need to make an /etc/mdadm/mdadm.conf file like this...

```
echo "DEVICE partitions" > /etc/mdadm/mdadm.conf
echo "HOMEHOST fileserver" >> /etc/mdadm/mdadm.conf
echo "MAILADDR root@localhost" >> /etc/mdadm/mdadm.conf
mdadm --detail --scan >> /etc/mdadm/mdadm.conf
```

Finally, you'll need a place to mount the drives.
```
sudo mkdir /storage
```

And setup /etc/fstab to mount it...
```
sudo nano /etc/fstab
```

And paste this at the bottom...
```
/dev/md0 /storage ext4 defaults 0 0
```

And, finally mount your new directory...
```
sudo mount -a
```

If you haven't solved it already, I hope this helps.

---

### Post by Jaken Veina on 2010-08-05
The grub problem was a separate issue, and it's installed on a separate 80GB drive with the OS. The 10TB is purely for storage/file serving use.

The process you describe is precisely what I've been using, only I did skip the mdadm.conf step. And, instead of fdisk, I used parted, since fdisk doesn't support GPT. I originally was going to do this via a FakeRAID chip, but since it didn't support GPT, it couldn't build arrays greater than 2.2TB. Do I not actually need GPTs, since each drive is within MBR's limit?

Also, in the mdadm --create command, is --raid-devices=8 a typo? I would think it's not, but I have noticed that after successfully executing mdadm --create, the mdadm --detail for the new array lists the array as having 5 active devices and one spare, even though I specified --raid-devices=6. Is that a function of the initial building process?

I haven't actually tried creating an array with webmin, but it's been extremely useful otherwise. It was the first to tell me what went wrong when I was watching a video file streaming from the array and it suddenly crashed. Apparently, two of the six brand new drives failed without having actually failed. I've run every test I can on the drives and they all passed like champs. And since the array lost two drives rather than just one, mdadm wouldn't let me just rebuild it, so I've had to start again from scratch.

Any ideas how two drives could just get kicked from the array like that, without having any actual failures? I'd rather this didn't happen again after I spend another 5 hours building the array and copying data to it.

And, yeah, you can boot to a RAID 1 array because, for a RAID 1 only, mdadm doesn't need to be running to read from the disks, because they're not striped. Both disks will contain the proper bootstrap for grub. BIOS can pick either of the two drives to begin the boot process, and since no writing is done until the OS (and mdadm) is loaded, doing so won't degrade the array.

---

### Post by jacekk015 on 2010-08-06
> **Jaken Veina said:**
> The grub problem was a separate issue, and it's installed on a separate 80GB drive with the OS. The 10TB is purely for storage/file serving use.

The process you describe is precisely what I've been using, only I did skip the mdadm.conf step. And, instead of fdisk, I used parted, since fdisk doesn't support GPT. I originally was going to do this via a FakeRAID chip, but since it didn't support GPT, it couldn't build arrays greater than 2.2TB. Do I not actually need GPTs, since each drive is within MBR's limit?

Also, in the mdadm --create command, is --raid-devices=8 a typo? I would think it's not, but I have noticed that after successfully executing mdadm --create, the mdadm --detail for the new array lists the array as having 5 active devices and one spare, even though I specified --raid-devices=6. Is that a function of the initial building process?

I haven't actually tried creating an array with webmin, but it's been extremely useful otherwise. It was the first to tell me what went wrong when I was watching a video file streaming from the array and it suddenly crashed. Apparently, two of the six brand new drives failed without having actually failed. I've run every test I can on the drives and they all passed like champs. And since the array lost two drives rather than just one, mdadm wouldn't let me just rebuild it, so I've had to start again from scratch.

Any ideas how two drives could just get kicked from the array like that, without having any actual failures? I'd rather this didn't happen again after I spend another 5 hours building the array and copying data to it.

And, yeah, you can boot to a RAID 1 array because, for a RAID 1 only, mdadm doesn't need to be running to read from the disks, because they're not striped. Both disks will contain the proper bootstrap for grub. BIOS can pick either of the two drives to begin the boot process, and since no writing is done until the OS (and mdadm) is loaded, doing so won't degrade the array.

Yeap the drives maybe are brand new but... they aren't specific RAID drives I think.
Read about TLER. That's why they jumps out. Desktop drives doesn't have this mechanism so they cannot give info that they aren't ready yet or they are fighting with errors internally. So they are assumed to be failed.

What's the detail model of the drives ? Aren't they sometimes WD EARS drives ??

For my array I'm using Samsung F1R RAID drives, they are working 1,5year on Openfiler [linux - software raid] without problems.

[http://www.samsung.com/global/business/hdd/learningresource/whitepapers/LearningResource_CCTL.html](http://www.samsung.com/global/business/hdd/learningresource/whitepapers/LearningResource_CCTL.html)

---

### Post by Jaken Veina on 2010-08-06
Seems like EARS drive don't support activating TLER, no...

Bah... I don't want to have to buy six more, more expensive drives.....

Is there any way to raise the timeout threshold mdadm uses to determine if a drive should be kicked?

---

### Post by jacekk015 on 2010-08-06
I didn't see anywhere solutions form the side of mdadm.

About TLER/CCTL you can try to examine your drive with:
```
sdparm -all /dev/sda | grep RTL
```

---

### Post by Jaken Veina on 2010-08-06
RTL is 0ms, and is listed in red, which I'd say means it can't be changed, considering I tried and failed to do so.

I stumbled upon the following thread while researching TLER and RTL. They seem to be under the very clear impression that the md controller doesn't have a timeout limit for kicking drives.

[http://www.issociate.de/board/post/498851/mdadm_and_TLER_%28Time_Limited_Error_Recovery%29.html](http://www.issociate.de/board/post/498851/mdadm_and_TLER_%28Time_Limited_Error_Recovery%29.html)

> The only reason for TLER (Time Limited Error Recovery) is to behave
"friendly" toward RAID controllers that timeout disks.
In fact, md does not timeout disks as many Hardware RAID controllers do.
So, from md's point of view, TLER is useless, i.e. it has no benefit.What gives?

---

### Post by jacekk015 on 2010-08-06
I've wasn't for 100% about that.
I don't think that mdadm is so stupid to take action only when the drive will burn out or cable jumps out.

You didn't confirm this, but if you have EARS drive the problem is global.
You can read this on WDC community forum. There are a many people complaining about EARS disk in RAID different type, Linux and Windows, Intel or other...

[http://www.google.pl/search?hl=pl&client=firefox-a&rls=org.mozilla%3Arazz%3Al%3Aeek%3Afficial&q=site%3Awdc.com+EARS+raid&aq=f&aqi=&aql=&oq=&gs_rfai=](http://www.google.pl/search?hl=pl&client=firefox-a&rls=org.mozilla%3Arazz%3Al%3Aeek%3Afficial&q=site%3Awdc.com+EARS+raid&aq=f&aqi=&aql=&oq=&gs_rfai=)

RTL = 0ms means that TLER is disabled/unavailable.
[ ]("http://www.google.pl/search?q=site%3Awdc.com+EARS&ie=utf-8&oe=utf-8&aq=t&rls=org.mozilla:pl:official&client=firefox-a")

---

### Post by Jaken Veina on 2010-08-06
The drives are Seagate.

---

### Post by Jaken Veina on 2010-08-10
Well, it seems to be a motherboard/SATA controller problem. I swapped around the drives and cables, and it was still sdc and sdd that failed during the array build. Upon inspection, I see that those two only show up as not SMART capable, until the next reboot. Luckily, I've got a few extra SATA ports I can move to and see if I can get a successful build.

Anyone ever hear of a bug like this?

---

### Post by F35 on 2011-02-17
I just found your thread, so I read it from the start to what you have now.  I assume you now have your issues resolved or you gave up.  Either way, I would like to see any additional comments, results or problems you have had. 

I wouldn't have commented here on your thread, except that I can so identify with the frustrations you express at the beginning.

---

