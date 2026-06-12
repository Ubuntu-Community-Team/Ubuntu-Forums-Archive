---
title: "[SOLVED] reaplace GRUB"
date: 2008-12-14
forum: Windows
---

### Post by inxygnuu on 2008-12-14
hello, I have not been able to boot into my vista, and I realized that i had a recovery cd that would allow me to change the bootloader back to vistas. Should i do it? or should i stay with grub and configure it. i always get "error 12: invalid device requested"

---

### Post by caljohnsmith on 2008-12-14
I would stick with Grub if that is what you are currently using. How about booting your Live CD, download the attached "boot_info6.sh.txt" file to your desktop, open a terminal (Applications > Accessories > Terminal) and do:
```
sudo sh ~/Desktop/boot_info6.sh.txt
```
That will create a "BootInfo.txt" file on your desktop; please attach that to your next post, or simply copy/paste the contents to your next post. That will greatly clarify your setup and what your problem might be about booting Vista.

---

### Post by inxygnuu on 2008-12-14
/dev/sda:Grub:07ff
sda1 :ntfs:BS: Vista:OS Vista: 
sda3 ::BS: None:OS : 
sda5 :ntfs:BS: XP:OS Vista: 
sda6 :ntfs:BS: Vista:OS : 
sda7 :swap:BS: None:OS : 
sda8 :ext3:BS: None:OS Linux: /boot/grub/menu.lst /boot /boot/grub 

Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders, total 390721968 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x1ddd1ddc

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048    62363647    31180800    7  HPFS/NTFS
/dev/sda3        62364330   390716864   164176267+   5  Extended
/dev/sda5        68517288   244332584    87907648+   7  HPFS/NTFS
/dev/sda6       310022144   390715391    40346624    7  HPFS/NTFS
/dev/sda7        62364456    68517224     3076384+  82  Linux swap / Solaris
/dev/sda8       244332648   310006304    32836828+  83  Linux

Partition table entries are not in disk order
# partition table of /dev/sda
unit: sectors

/dev/sda1 : start=     2048, size= 62361600, Id= 7, bootable
/dev/sda2 : start=        0, size=        0, Id= 0
/dev/sda3 : start= 62364330, size=328352535, Id= 5
/dev/sda4 : start=        0, size=        0, Id= 0
/dev/sda5 : start= 68517288, size=175815297, Id= 7
/dev/sda6 : start=310022144, size= 80693248, Id= 7
/dev/sda7 : start= 62364456, size=  6152769, Id=82
/dev/sda8 : start=244332648, size= 65673657, Id=83

sda8/boot/grub/menu.lst

# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		3

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu

# Pretty colours
color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
## password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title		Windows 95/98/NT/2000
# root		(hd0,0)
# makeactive
# chainloader	+1
#
# title		Linux
# root		(hd0,1)
# kernel	/vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=1869fedd-4125-4bbc-94ff-65c782c2f77c ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,7)

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash vga=792

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowedsudo sh ~/Desktop/boot_info6.sh.txt
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title		Ubuntu 8.10, kernel 2.6.27-7-generic
root		(hd0,7)
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=1869fedd-4125-4bbc-94ff-65c782c2f77c ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
root		(hd0,7)
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=1869fedd-4125-4bbc-94ff-65c782c2f77c ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, kernel 2.6.24-19-generic
root		(hd0,7)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=1869fedd-4125-4bbc-94ff-65c782c2f77c ro quiet splash 
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.10, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,7)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=1869fedd-4125-4bbc-94ff-65c782c2f77c ro  single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.10, memtest86+
root		(hd0,7)
kernel		/boot/memtest86+.bin
quiet


### END DEBIAN AUTOMAGIC KERNELS LIST

title windows Vista
rootnoverify (hd0,4)
savedefault
makeactive
chainloader +1
boot

title windows se7en
rootnoverify (hd0,2)
savedefault
makeactive
chainloader+1
boot

title vista
rootnoverify (hd0,5)
savedefault
chainloader +1
makeactive
boot

sda8/boot

total 35000
drwxr-xr-x  3 root root    4096 2008-11-28 10:46 .
drwxr-xr-x 21 root root    4096 2008-11-28 10:40 ..
-rw-r--r--  1 root root  422667 2008-06-18 14:11 abi-2.6.24-19-generic
-rw-r--r--  1 root root  507665 2008-11-04 16:00 abi-2.6.27-7-generic
-rw-r--r--  1 root root  507665 2008-11-20 18:46 abi-2.6.27-9-generic
-rw-r--r--  1 root root   80049 2008-06-18 14:11 config-2.6.24-19-generic
-rw-r--r--  1 root root   91364 2008-11-04 16:00 config-2.6.27-7-generic
-rw-r--r--  1 root root   91364 2008-11-20 18:46 config-2.6.27-9-generic
drwxr-xr-x  3 root root    4096 2008-12-14 07:30 grub
-rw-r--r--  1 root root 8265639 2008-11-26 19:46 initrd.img-2.6.24-19-generic
-rw-r--r--  1 root root 8120885 2008-11-26 19:45 initrd.img-2.6.27-7-generic
-rw-r--r--  1 root root 8121863 2008-11-28 10:46 initrd.img-2.6.27-9-generic
-rw-r--r--  1 root root  124152 2008-09-11 16:11 memtest86+.bin
-rw-r--r--  1 root root  905146 2008-06-18 14:11 System.map-2.6.24-19-generic
-rw-r--r--  1 root root 1029585 2008-11-04 16:00 System.map-2.6.27-7-generic
-rw-r--r--  1 root root 1029585 2008-11-20 18:46 System.map-2.6.27-9-generic
-rw-r--r--  1 root root    1073 2008-11-04 16:02 vmcoreinfo-2.6.27-7-generic
-rw-r--r--  1 root root    1073 2008-11-20 18:48 vmcoreinfo-2.6.27-9-generic
-rw-r--r--  1 root root 1920472 2008-06-18 14:11 vmlinuz-2.6.24-19-generic
-rw-r--r--  1 root root 2244464 2008-11-04 16:00 vmlinuz-2.6.27-7-generic
-rw-r--r--  1 root root 2244304 2008-11-20 18:46 vmlinuz-2.6.27-9-generic

sda8/boot/grub

total 240
drwxr-xr-x 3 root root   4096 2008-12-14 07:30 .
drwxr-xr-x 3 root root   4096 2008-11-28 10:46 ..
-rw-r--r-- 1 root root    197 2008-11-26 12:31 default
-rw-r--r-- 1 root root     15 2008-11-26 12:31 device.map
-rw-r--r-- 1 root root   8056 2008-11-26 12:31 e2fs_stage1_5
-rw-r--r-- 1 root root   7904 2008-11-26 12:31 fat_stage1_5
-rw-r--r-- 1 root root     16 2008-11-26 12:31 installed-version
-rw-r--r-- 1 root root   8608 2008-11-26 12:31 jfs_stage1_5
-rw-r--r-- 1 root root   4874 2008-12-14 07:30 menu.lst
-rw-r--r-- 1 root root   4874 2008-12-14 07:26 menu.lst~
-rw-r--r-- 1 root root   4620 2008-11-26 19:33 menu.lst-backup
-rw-r--r-- 1 root root   4624 2008-11-26 18:59 menu.lst.backup
-rw-r--r-- 1 root root   4624 2008-11-26 18:49 menu.lst_original
-rw-r--r-- 1 root root   7324 2008-11-26 12:31 minix_stage1_5
-rw-r--r-- 1 root root   9632 2008-11-26 12:31 reiserfs_stage1_5
drwxrwxr-x 2 root evan   4096 2008-11-26 18:50 splashimages
-rw-r--r-- 1 root root    512 2008-11-26 12:31 stage1
-rw-r--r-- 1 root root 108356 2008-11-26 12:31 stage2
-rw-r--r-- 1 root root   9276 2008-11-26 12:31 xfs_stage1_5

---

### Post by inxygnuu on 2008-12-14
please note in the post above that the entries used for booting vista have been edited numerous times.

---

### Post by caljohnsmith on 2008-12-14
It also looks like you might be missing Vista's boot files, so how about downloading the attached "script1.sh.txt" and run it with:
```
sudo sh ~/Desktop/script1.sh.txt
```
And please post the output.

---

### Post by inxygnuu on 2008-12-14
+ mkdir /mnt/sda1 /mnt/sda5 /mnt/sda6
+ mount /dev/sda1 /mnt/sda1
+ mount /dev/sda5 /mnt/sda5
+ mount /dev/sda6 /mnt/sda6
+ ls -l /mnt/sda1 /mnt/sda5 /mnt/sda6
/mnt/sda1:
total 6464617
-rwxrwxrwx 1 root root         24 2008-06-25 16:54 autoexec.bat
-rwxrwxrwx 1 root root         10 2008-06-25 16:54 config.sys
drwxrwxrwx 1 root root       4096 2008-11-25 15:46 Documents
drwxrwxrwx 1 root root          0 2008-09-13 22:21 Documents and Settings
-rwxrwxrwx 1 root root 3152887808 2008-11-25 07:35 hiberfil.sys
-rwxrwxrwx 1 root root 3466776576 2008-11-25 07:35 pagefile.sys
drwxrwxrwx 1 root root          0 2008-09-14 07:57 PerfLogs
drwxrwxrwx 1 root root       4096 2008-11-23 01:21 ProgramData
drwxrwxrwx 1 root root       8192 2008-11-24 20:47 Program Files
drwxrwxrwx 1 root root          0 2008-11-23 01:05 Recovery
drwxrwxrwx 1 root root          0 2008-11-23 13:06 $Recycle.Bin
drwxrwxrwx 1 root root          0 2008-11-23 10:19 swsetup
drwxrwxrwx 1 root root       4096 2008-11-25 15:22 System Volume Information
drwxrwxrwx 1 root root          0 2008-12-14 00:50 Temp
drwxrwxrwx 1 root root          0 2008-11-15 15:59 Ubuntu usb
drwxrwxrwx 1 root root       4096 2008-11-23 01:05 Users
drwxrwxrwx 1 root root      16384 2008-11-25 15:10 Windows

/mnt/sda5:
total 6466094
drwxrwxrwx 1 root root          0 2008-11-22 10:43 2caafe7616c0c5a44221b9afb0
drwxrwxrwx 1 root root          0 2008-11-14 21:25 AHCache
-rwxrwxrwx 1 root root         24 2006-09-18 17:43 autoexec.bat
drwxrwxrwx 1 root root       4096 2008-11-20 22:06 $AVG8.VAULT$
drwxrwxrwx 1 root root       4096 2008-11-24 16:44 black USB
-rwxrwxrwx 1 root root      25687 2008-04-18 15:47 cmdtool8.bat
drwxrwxrwx 1 root root          0 2008-11-21 15:28 Config.Msi
-rwxrwxrwx 4 root root         10 2006-09-18 17:43 config.sys
drwxrwxrwx 1 root root          0 2008-10-30 19:50 Converted
drwxrwxrwx 1 root root       4096 2008-11-22 14:21 CoolOutput
drwxrwxrwx 1 root root          0 2006-11-02 08:02 Documents and Settings
drwxrwxrwx 1 root root       4096 2008-11-06 21:27 drives
drwxrwxrwx 1 root root          0 2008-10-19 20:12 DVDVideoSoft
-rwxrwxrwx 1 root root 3152871424 2008-11-25 16:11 hiberfil.sys
drwxrwxrwx 1 root root       4096 2008-11-25 15:23 Kalyway_10.5.2_DVD_Intel_Amd
-rwxrwxrwx 1 root root       1117 2008-03-02 17:20 mannager.bat
drwxrwxrwx 1 root root          0 2008-11-23 18:18 MSOCache
-rwxrwxrwx 1 root root 3466776576 2008-11-25 16:11 pagefile.sys
-rwxrwxrwx 1 root root        177 2008-01-11 15:36 part3.bat
drwxrwxrwx 1 root root          0 2008-10-19 13:22 PerfLogs
drwxrwxrwx 1 root root       8192 2008-11-19 21:45 ProgramData
drwxrwxrwx 1 root root      28672 2008-11-22 12:44 Program Files
drwxrwxrwx 1 root root       4096 2008-11-23 01:06 $Recycle.Bin
drwxrwxrwx 1 root root       8192 2008-11-24 16:50 seans computer
drwxrwxrwx 1 root root       4096 2008-11-14 13:23 shares old files
drwxrwxrwx 1 root root       4096 2008-10-11 20:53 swsetup
drwxrwxrwx 1 root root          0 2008-10-12 17:08 sysl
drwxrwxrwx 1 root root      20480 2008-11-25 19:45 System Volume Information
drwxrwxrwx 1 root root       4096 2008-10-12 17:08 Ubuntu810
drwxrwxrwx 1 root root       4096 2008-10-10 21:34 Users
-rwxrwxrwx 1 root root     917096 2008-02-17 10:29 vista.exe
drwxrwxrwx 1 root root      24576 2008-11-22 22:27 Windows
drwxrwxrwx 1 root root       4096 2008-09-14 08:22 $WINDOWS.~BT
-rwxrwxrwx 1 root root     362766 2008-03-23 16:17 xp.exe

/mnt/sda6:
total 953
drwxrwxrwx 1 root root      0 2008-11-16 12:24 $AVG8.VAULT$
drwxrwxrwx 1 root root  16384 2008-11-22 23:22 Documents
drwxrwxrwx 1 root root      0 2008-11-14 20:06 EVAN-HP6910
drwxrwxrwx 1 root root  12288 2008-11-22 23:44 Hacks 'n such
drwxrwxrwx 1 root root      0 2008-11-22 23:44 Infiniti
drwxrwxrwx 1 root root   4096 2008-11-25 15:56 making themes
-rwxrwxrwx 1 root root    528 2008-11-14 20:01 MediaID.bin
drwxrwxrwx 1 root root  12288 2008-11-25 15:56 Music
drwxrwxrwx 1 root root      0 2008-11-22 23:59 My U3
drwxrwxrwx 1 root root  20480 2008-11-25 15:56 Pictures
drwxrwxrwx 1 root root      0 2008-11-23 01:06 $RECYCLE.BIN
drwxrwxrwx 1 root root 786432 2008-11-11 15:22 System32
drwxrwxrwx 1 root root  16384 2008-11-25 16:18 System Volume Information
drwxrwxrwx 1 root root   4096 2008-11-23 00:12 Videos
drwxrwxrwx 1 root root      0 2008-11-25 15:42 Windows.old

---

### Post by caljohnsmith on 2008-12-14
OK, it looks quite messy because it seems you have remnants of XP left in your partitions; it also looks like you may have Vista installed to both sda1 and sda5, yet neither of those partitions have Vista's boot files. If you have your Vista Install CD, I would boot that and do a "Vista Repair". That should reinstall Vista's boot files to sda1. If you don't have a Vista Install CD, you can instead download and use a Vista Recovery CD from [here]("http://neosmart.net/blog/2008/download-windows-vista-x64-recovery-disc/"). Once you are done with that, open up your menu.lst in Ubuntu:
```
gksudo gedit /boot/grub/menu.lst
```
And change your Vista's entry to be:
```
title Windows Vista
rootnoverify (hd0,0)
chainloader +1

```
And then try to boot Vista with that entry; let me know how it goes.

---

### Post by inxygnuu on 2008-12-14
Thank you!!!!

---

### Post by caljohnsmith on 2008-12-14
Glad that worked for you; cheers and have fun with Vista and Ubuntu. :)

---

