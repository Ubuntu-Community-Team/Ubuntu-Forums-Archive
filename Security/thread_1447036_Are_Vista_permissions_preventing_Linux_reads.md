---
title: "Are Vista permissions preventing Linux reads?"
date: 2010-04-04
forum: Security
---

### Post by mel2000 on 2010-04-04
I'm finding that some Linux distros and apps cannot see all the hard drives on my system (Acer Aspire 5520 laptop, Vista Home Premium), especially the C: drive, which is one of two partitions (C, D) of my internal laptop drive.
 
I also have an external USB hard drive with three partitions (J, K, L), two flash drives and a CD/DVD drive. I have no trouble reading or writing the flash and optical drives, and no trouble reading/writing all my drives in Vista.
 
Things used to be worse. I found that I had to set the permission of username Owner/Administrator (that's me) to "Full Control" in Vista before any distro except Puppy 4.3.1 could read the drive. YLMF (Ubuntu) Linux, Ophcrack Live CD, and UBCD4Win cannot read all or some of C: but can fully read/write D:. Bruno Puppy Linux can see all except J: (which has two folders with Vista permissions set to be read only by users with Admin privilege).
 
The good news is that Puppy Linux 4.3.1 and the live CD apps Dr. Web Cure It, Partition Wizard and Paragon Backup & Recovery can see all my drives.
 
I'd like some advice on why there is inconsistency with seeing all my drives, and why seeing the drives depend on Vista permission settings. Thanks.

---

### Post by mel2000 on 2010-04-04
I just discovered the Palimpsest Disk Utility in YLMF and found that it shows all my drives, even the C: drive. All drives show the same LABEL name as shown in Vista. I noticed that the TYPE for all the browsable drives is HPFS/NTFS (0x07), whereas for the C: drive it shows EMPTY (0x00). Palimpsest allows me to change the TYPE but I'm wary of unexpected consequences.

Would it be OK to change the C: drive's TYPE to  HPFS/NTFS to see if it will become browsable?

---

### Post by mel2000 on 2010-04-05
Ok, I found that Ophcrack is seriously affected by not being able to read the C: drive so someone posted a way to mount the c: drive manually, and I found that it allowed me to see all of my C: drive.

1.) sudo mkdir /mnt/ntfs)
2.) sudo mount /dev/sda1 /mnt/ntfs

I'm still curious as to why my C: drive isn't detected automatically.

---

### Post by CharlesA on 2010-04-06
Linux ignores NTFS permissions, so you wouldn't have any problems with it. Is this one of those factory pcs with Vista on it (with a recovery partition)?

---

### Post by mel2000 on 2010-04-06
Thanks for your response. Vista Home Premium was installed on my system without a recovery partition.
 
I too thought Linux was oblivious to Vista's permission schemes until my experience described above showed otherwise. So far Puppy Linux is the only Linux distro that read all my drives without having me modify my Vista permissions. I can't think of any other explanation for Linux not reading all my Vista partitions.

---

### Post by garvinrick4 on 2010-04-07
What is Code:

sudo fdisk -l   (small L)

sudo blkid   ( small L second letter)


Post them in your thread here.

---

### Post by mel2000 on 2010-04-10
Sorry for the delayed response. Here are my results.
> **garvinrick4 said:**
> What is Code:
 
sudo fdisk -l (small L)
 
Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xbb1873f9
Device Boot Start End Blocks Id System
/dev/sda1 * 1 5519 44326880+ 27 Unknown
/dev/sda2 5519 9730 33822720 7 HPFS/NTFS
Disk /dev/sdb: 4022 MB, 4022337024 bytes
255 heads, 63 sectors/track, 489 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x4bc54bc5
Device Boot Start End Blocks Id System
/dev/sdb1 * 1 488 3919841 b W95 FAT32
Disk /dev/sdc: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x16cc6bf0
Device Boot Start End Blocks Id System
/dev/sdc1 1 9179 73730286 7 HPFS/NTFS
/dev/sdc2 9180 18358 73730317+ 7 HPFS/NTFS
/dev/sdc3 18359 30402 96735232 7 HPFS/NTFS
 
> sudo blkid ( small L second letter)
 
/dev/loop0: LABEL="YLMF OS" TYPE="iso9660" 
/dev/loop1: TYPE="squashfs" 
/dev/sda1: UUID="DCDC98A0DC98768C" LABEL="ACER" TYPE="ntfs" 
/dev/sda2: UUID="80B01505B01502F8" LABEL="DATA" TYPE="ntfs" 
/dev/sdb1: LABEL="MULTIBOOT" UUID="8EAC-C46A" TYPE="vfat" 
/dev/sdc1: UUID="1EBADC30BADC05E5" LABEL="DISK_J" TYPE="ntfs" 
/dev/sdc2: UUID="CC76BB3A76BB245C" LABEL="DISK_K" TYPE="ntfs" 
/dev/sdc3: UUID="D662D0EB62D0D17B" LABEL="DISK_L" TYPE="ntfs"

---

### Post by wilee-nilee on 2010-04-10
So it looks like this a wubi install, make sure if you can, if this is the case, mention this when you post it will probably get you more response. Ubuntu in a real dual boot would see everything else on there all the time.

If this is a wubi install and you have gotten used to Ubuntu and you like it, you might consider a dual boot.

Edit: So I am curious about how you were running Puppy in order to get everything mountable?, if it was the live CD then that is why it sees everything it is not inside of another OS, the Ubuntu live CD would do the same.

---

### Post by mel2000 on 2010-04-10
No Wubi involved. Both Puppy Linux 4.3.1 and YLMF 1.0 are Live CD boots.

---

### Post by wilee-nilee on 2010-04-10
> **mel2000 said:**
> No Wubi involved. Both Puppy Linux 4.3.1 and YLMF 1.0 are Live CD installs.

Post this commonly used boot script so we can see whats up. I don't see a standard Linux partition in your list.
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

I see the multi boot sdb that you mention in your other thread is this where Ubuntu is.

---

### Post by mel2000 on 2010-04-11
wilee-nilee, can you tell me what the script is for? I'm a Windows Vista user and am using Linux distros only from a Live CD after a fresh reboot out of Vista. Linux has not been installed onto my hard drive.

---

### Post by wilee-nilee on 2010-04-11
> **mel2000 said:**
> wilee-nilee, can you tell me what the script is for? I'm a Windows Vista user and am using Linux distros only from a Live CD after a fresh reboot out of Vista. Linux has not been installed onto my hard drive.

The script is run from a live cd and shows everything all partitions MBR info and the boot flags. 

But I think the reason your having problems with Ubuntu reading everything is, if the Live cd your running is in that custom multi boot partitioning it may have limitations. Puppy runs in root so I can see why it might be more likely to work.

Part of the problem with getting any help I think is full disclosure... which the bootscript will do. 

So burn a live Ubuntu CD boot your computer run the script and post it, you will probably not get any help without this in the end, you have to much stuff to analyze without a readable accurate information of what and where stuff is. This boot script is well known on this site and is used all the time,totally safe just follow the directions.

It also looks like you have a boot flag on more then one partition, probably not the problem but you have what looks to me to be a pretty messy setup, so it makes it more difficult to figure the answers.

---

### Post by wilee-nilee on 2010-04-11
In the future I wouldn't mention things like the oph installs, this site does not support associated problems with that sort of set up. And this is why you wont post the boot script isn't it?

---

### Post by mel2000 on 2010-04-13
> **wilee-nilee said:**
> In the future I wouldn't mention things like the oph installs, this site does not support associated problems with that sort of set up. And this is why you wont post the boot script isn't it?
wilee-nilee, I don't understand what any of the quote above means.
 
Sorry for the delayed response. I appreciate your investigative assistance getting to the root of my Linux issues but I think some clarifications are in order because I don't think my system configuration is messy at all:
 
sdb1 is my 4 GB USB flash drive that contains several Live CD boot ISOs configured by MultibootISOs.exe to boot from a USB stick instead of a CDROM. Live CDs on the stick include YLMF 1.0 and Puppy 4.3.1, among other Linux bootable CD apps.
There is no dual booting of any kind on my Vista system.
There is no custom multi boot partitioning on my Vista system.
There is no Wubi install on my Vista system.
 
With that said, I now present you with my Results.txt file.

```
 
Boot Info Script 0.55 dated February 15th, 2010 
============================= Boot Info Summary: ==============================
=> Acer 3 is installed in the MBR of /dev/sda
=> Syslinux is installed in the MBR of /dev/sdb
=> Windows is installed in the MBR of /dev/sdc
=> Windows is installed in the MBR of /dev/sdd
sda1: _________________________________________________________________________
File system: ntfs
Boot sector type: Windows Vista/7
Boot sector info: No errors found in the Boot Parameter Block.
Operating System: Windows Vista
Boot files/dirs: /bootmgr /Boot/BCD /Windows/System32/winload.exe
sda2: _________________________________________________________________________
File system: ntfs
Boot sector type: Windows Vista/7
Boot sector info: No errors found in the Boot Parameter Block.
Operating System: 
Boot files/dirs: 
sdb1: _________________________________________________________________________
File system: vfat
Boot sector type: Fat32
Boot sector info: No errors found in the Boot Parameter Block.
Operating System: 
Boot files/dirs: /menu.lst /boot/bcd
sdc1: _________________________________________________________________________
File system: ntfs
Boot sector type: Windows Vista/7
Boot sector info: No errors found in the Boot Parameter Block.
Operating System: 
Boot files/dirs: 
sdc2: _________________________________________________________________________
File system: ntfs
Boot sector type: Windows Vista/7
Boot sector info: No errors found in the Boot Parameter Block.
Operating System: 
Boot files/dirs: 
sdc3: _________________________________________________________________________
File system: ntfs
Boot sector type: Windows Vista/7
Boot sector info: No errors found in the Boot Parameter Block.
Operating System: 
Boot files/dirs: 
sdd1: _________________________________________________________________________
File system: vfat
Boot sector type: Vista: Fat 32
Boot sector info: No errors found in the Boot Parameter Block.
Operating System: 
Boot files/dirs: 
=========================== Drive/Partition Info: =============================
Drive: sda ___________________ _____________________________________________________
Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xbb1873f9
Partition Boot Start End Size Id System
/dev/sda1 * 63 88,653,823 88,653,761 27 Hidden HPFS/NTFS
/dev/sda2 88,653,824 156,299,263 67,645,440 7 HPFS/NTFS
 
Drive: sdb ___________________ _____________________________________________________
Disk /dev/sdb: 4022 MB, 4022337024 bytes
255 heads, 63 sectors/track, 489 cylinders, total 7856127 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x4bc54bc5
Partition Boot Start End Size Id System
/dev/sdb1 * 38 7,839,719 7,839,682 b W95 FAT32
 
Drive: sdc ___________________ _____________________________________________________
Disk /dev/sdc: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x16cc6bf0
Partition Boot Start End Size Id System
/dev/sdc1 63 147,460,634 147,460,572 7 HPFS/NTFS
/dev/sdc2 147,460,635 294,921,269 147,460,635 7 HPFS/NTFS
/dev/sdc3 294,922,240 488,392,703 193,470,464 7 HPFS/NTFS
 
Drive: sdd ___________________ _____________________________________________________
Disk /dev/sdd: 4009 MB, 4009754624 bytes
255 heads, 63 sectors/track, 487 cylinders, total 7831552 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xe927d0f4
Partition Boot Start End Size Id System
/dev/sdd1 * 63 7,831,551 7,831,489 b W95 FAT32
 
blkid -c /dev/null: ____________________________________________________________
Device UUID TYPE LABEL 
/dev/loop0 iso9660 YLMF OS 
/dev/loop1 squashfs 
/dev/sda1 DCDC98A0DC98768C ntfs ACER 
/dev/sda2 80B01505B01502F8 ntfs DATA 
/dev/sdb1 8EAC-C46A vfat MULTIBOOT 
/dev/sdc1 1EBADC30BADC05E5 ntfs DISK_J 
/dev/sdc2 CC76BB3A76BB245C ntfs DISK_K 
/dev/sdc3 D662D0EB62D0D17B ntfs DISK_L 
/dev/sdd1 543E-132D vfat FLASH 
============================ "mount | grep ^/dev output: ===========================
Device Mount_Point Type Options
aufs / aufs (rw)
/dev/sdb1 /isodevice vfat (rw)
/dev/loop0 /cdrom iso9660 (rw)
/dev/loop1 /rofs squashfs (rw)
/dev/sdd1 /media/FLASH vfat (rw,nosuid,nodev,uhelper=devkit,uid=999,gid=999,shortname=mixed,dmask=0077,utf8=1,flush)
/dev/sdc2 /media/DISK_K fuseblk (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)
/dev/sdc1 /media/DISK_J fuseblk (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)
/dev/sdc3 /media/DISK_L fuseblk (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)
 
================================ sdb1/menu.lst: ================================
default 0
timeout 120
color NORMAL HIGHLIGHT HELPTEXT HEADING
splashimage /bgimage/tux.xpm.gz
foreground=0000FF
background=0066FF 
 
title AVG Rescue CD 9.0.10014 (AntiVirus)
find --set-root /avg_arl_en_90_100114.iso
map --mem /avg_arl_en_90_100114.iso (hd32)
map --hook
root (hd32)
chainloader (hd32)
 
title DBAN 1.0.7 (Drive Nuker)
find --set-root /dban-1.0.7_i386.iso
map --mem /dban-1.0.7_i386.iso (hd32)
map --hook
root (hd32)
chainloader (hd32)
 
title Memtest86 (Memory Tester)
find --set-root /memtest86+-4.00.iso
map /memtest86+-4.00.iso (hd32)
map --hook
root (hd32)
chainloader (hd32)
 
title Offline NT Password & Registy Editor
find --set-root /cd080802.iso
map /cd080802.iso (hd32)
map --hook
root (hd32)
chainloader (hd32)
 
title Ophcrack Vista 2.3.1 (Password Revealer, Resetter, Cracker)
kernel /ophvista/boot/bzImage rw root=/dev/null vga=normal lang=C kmap=us screen=1024x768x16 autologin quiet splash
initrd /ophvista/boot/rootfs.gz
 
title Ophcrack XP 2.3.1 (Password Revealer, Resetter, Cracker)
kernel /ophxp/boot/bzImage rw root=/dev/null vga=normal lang=C kmap=us screen=1024x768x16 autologin quiet splash
initrd /ophxp/boot/rootfs.gz
 
title Paragon Backup & Recovery 10.1
find --set-root /paragon_backup101.iso
map /paragon_backup101.iso (hd32)
map --hook
root (hd32)
chainloader (hd32)
 
title Partition Wizard 4.2.2
find --set-root /pwhe42.iso
map /pwhe42.iso (hd32)
map --hook
root (hd32)
chainloader (hd32)
 
title Puppy Linux 4.3.1
find --set-root /puppy/pup-431.sfs
kernel /puppy/vmlinuz root=/dev/rd/0 pmedia=usbflash
initrd /puppy/initrd.gz
 
title YLMF Linux 1.0
find --set-root /YlmF_OS_EN_v1.0.iso
map /YlmF_OS_EN_v1.0.iso (hd32)
map --hook
root (hd32)
chainloader (hd32)
kernel /casper/vmlinuz file=/preseed/ylmf.seed boot=casper iso-scan/filename=/YlmF_OS_EN_v1.0.iso quiet splash
initrd /casper/initrd.lz
 
#this is for a space
title
kernel
initr
 
title Restart The Computer
reboot
 
=================== sdb1: Location of files loaded by Grub: ===================
 
??GB: menu.lst

```

---

