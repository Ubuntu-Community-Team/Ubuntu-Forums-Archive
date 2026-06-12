---
title: "Problems accessing gpt raid partitions on linux ubuntu 16.04.2 LTS"
date: 2019-08-31
forum: Server Platforms
---

### Post by tom-dean on 2019-08-31
[COLOR=#242729][FONT=Arial]I had a 6 year old server which I replaced the hard drives and upgraded last summer. It was a 2 cpu (18 cores each) AMD Athlon system who's only purpose was to run VM's (using kvm)for my grad students to use for testing their research. It contained a 1TB boot disk and 4 - 2T disks in a Raid6 array. Periodically I would take the VM's down and back up the virtual drives. The server was located in a secure server room with limited access. However, earlier this week, the unthinkable happened, and there was a fire in the server room. I was able to access the system remotely and do an orderly shutdown (shutdown -h now).
[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]The machine itself is not too badly damaged, but is full of toxic soot. The techs were able to remove the drives from the machine and clean them. I currently have them in a borrowed desktop 7 core intel machine, and while there are not enough drive bays, there are enough sata ports. The thought was to boot off the transplanted boot disk and mdadm would reassemble the drives based on UUIDs. We could then back up the virtual disks in a priority order. However when we booted, the raid array was not present. Placing them back in the previous machine is not really an option as there is still a significant amount of very fine toxic soot in the case which the fans will spread all over the place.

[/FONT][/COLOR][COLOR=#242729][FONT=Arial]I'm currently in the process of imaging the raw data from the 4 raid disks to a large external drive using dd so that if they fail because of damage we still have the data. So far the disks are behaving themselves. Two disks have been copied without any errors reported by dd, and the 3rd is underway. There don't seem to be any disk errors reported in the system logs either.[/FONT][/COLOR]

[COLOR=#242729][FONT=Arial]Right now the problem appears to be that the system is not seeing the partitions on the 2TB drives. The command 'parted /dev/sdb print' does not report anything on the drives. I used fdisk and got the following results. I've shown the help menus (but elided to only show the options I used).[/FONT][/COLOR]

```

Script started on Sat 31 Aug 2019 11:17:57 AM EDT
root@perseus:~/usb2# fsdisk /dev/sdb
Welcome to fdisk (util-linux 2.27.1).
Changes will remain in memory only, until you decide to write them.
Be careful before using the write command.

Command (m for help): p
Disk /dev/sdb: 1.8 TiB, 2000398934016 bytes, 3907029168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: gpt
Disk identifier: 2947A17A-DC83-4C60-8D2A-63D2403015DD

Command (m for help): m

Help:
...
  Misc
   m   print this menu
   x   extra functionality (experts only)
...

Command (m for help): x

Expert command (m for help): m

Help (expert commands):
  GPT
   i   change disk GUID
   n   change partition name
   u   change partition UUID
   M   enter protective/hybrid MBR
...

Expert command (m for help): M
Entering protective/hybrid MBR disklabel.

Expert command (m for help): p
Disk /dev/sdb: 1.8 TiB, 2000398934016 bytes, 3907029168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: dos
Disk identifier: 0x00000000

Device     Boot Start        End    Sectors Id Type Start-C/H/S   End-C/H/S[0m Attrs
/dev/sdb1           1  3907029167 3907029167 ee GPT        0/2/0 1023/63/255      

Partition 1 does not start on physical sector boundary.

Expert command (m for help): q

root@perseus:~/usb2# exit
exit

Script done on Sat 31 Aug 2019 11:18:51 AM EDT

```

[COLOR=#242729][FONT=Arial]All of the drives print identical results. I assume that if there was problem during shutdown during the fire, they would not all be corrupted in the same way.

[/FONT][/COLOR][COLOR=#242729][FONT=Arial]So the partition appears to be there, but parted and partprobe don't find it. I've checked with asmod, and the modules raid456, raid6_pq and async_raid6_recov modules are loaded. As far as I know, if the partition is not in /dev then the variants of mdadm to scan or specifically assemble the raid are not going to work. I did give them a try anyways, but no luck.

[/FONT][/COLOR][COLOR=#242729][FONT=Arial]The system was reinstalled and configured using the ubuntu 16.04 server installation DVD last summer (the previous raids disks were backed up and replaced with new ones). There was nothing special about the installation, as far as I know, other than using a bridge network device so that the graduate students could access their individual vm's remotely. The boot volume and the raid array were created and configured by the ubuntu installer with default options as far as I remember.

I[/FONT][/COLOR][COLOR=#242729][FONT=Arial] was trying to follow the advice the following link, but I haven't used anything from it that might be destructive as I'm still in the process of backing up the raw data from the drives.

[/FONT][/COLOR][Partition Not Showing up in /dev]("https://superuser.com/questions/676093/partition-not-showing-up-in-dev?newreg=3b8df654c4d34dec8b8242daaecb8a1e")

[COLOR=#242729][FONT=Arial]Any ideas how I can make the partitions visible? The grad student is in the process of thesis writing, and while she has most of the data (from previous backups), there is data on these disks that is needed.[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]Thanks.[/FONT][/COLOR]

---

### Post by TheFu on 2019-08-31
Was LVM used to manage the mdadm parts?  If LVM is used, it could be outside or inside the array.  **sudo vgchange -ay** will scan for it.

Also, **sudo fdisk -l /dev/sda** should save you time.
**lsblk** is handy too.

---

### Post by tom-dean on 2019-08-31
Thanks for the reply.

I'm at home right now, but going back in tomorrow. I did try the command **lsblck**. It does not show the partitions. It shows the partitions on the boot disk (/dev/sda1) and the backup drive (/dev/sdg1). It only lists the devices files for the entire raid drives (i.e. /dev/sdb, /dev/sdc, /dev/sdd, /dev/sde) but does not list any partition devices (i.e. does not show /dev/sdb1, /dev/sdc1, /dev/sdd1, /dev/sde1). 

I don't remember if it was llvm managed. I can check to see if the llvm kernel module is loaded, since I was reading that **partprobe** doesn't add the partition if the file system is not recognized. Will **vgchange -ay** find the partition if the partition is not in the kernel?

---

### Post by darkod on 2019-09-01
Are you sure you used partitions? I ask because I have seen many cases people use the whole disk in mdadm, without creating any partition. I always do partitions by the way.

One of the tools I know for detecting and recovering partitions is testdisk.
[https://www.cgsecurity.org/wiki/TestDisk](https://www.cgsecurity.org/wiki/TestDisk)

But if you have never used it, read carefully first because much damage can be done with that tool.

---

### Post by TheFu on 2019-09-01
I always use partitions for RAID and for LVM, though it isn't strictly required, for just this purpose.  I know there is a partition there and the partition table says if it is LVM or a RAID member.

Sadly, sometimes the only answer for RAID problems is to start over and recover from backups.

Please be exact with your posts.  Typos just confuse the issues and there are a number of them in post #3 above.

---

