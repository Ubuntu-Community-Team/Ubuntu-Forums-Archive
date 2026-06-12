---
title: "Boot Problem after installing Ubuntu 10.4 on Windows XP"
date: 2010-12-14
forum: Ubuntu One (CLOSED)
---

### Post by h_gugu on 2010-12-14
hello to all,

This is my first post on ubuntu forum. I expect little soft corner from your side. 
First  i am very new in ubuntu. and today i installed ubuntu 10.4 on my HP NX7400 Laptop. I have Windows XP Service pack 2 installed. Now i'll tell you my situation, After installing ubuntu my windows xp never boot. on my boot menu i have listed 2 operating systems but when i select widows xp it comes back on boot menu. Now, i have googled and find some solution but it has not helped me. 

1. I have tested test drive in Ubuntu and apply all commands and everything but it did not work
2. Another solution was boot from windows xp cd and try fixmbr and fixboot on recovery console. but i really wonder when i put my windows xp bootable cd, it start booting but blue screen never come and my laptop become idle and do nothing (strange for me). Other bootable cd works fine.

Now, please experts give me very good solution because i want to learn linux. but i can not leave windows because i have to work on windows. like Microsoft .Net

regards
Hassan Mushtaq

---

### Post by oldfred on 2010-12-15
Was this a wubi install inside the windows partition or a full dual boot install with separate Linux formated partitions?

Do you have liveCD and can boot it directly? Download and run this script so we can see what you have installed where:
Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the post's menu and then paste the contents between the generated [ code] paste here [ /code] tags.

---

### Post by h_gugu on 2010-12-15
Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Lilo is installed in the MBR of /dev/sda

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda1 and 
                       looks at sector 229808474 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sda6: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda6 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sda7: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda7 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sda8: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   /grub/menu.lst /grub/grub.conf

sda9: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/menu.lst /boot/grub/grub.cfg /etc/fstab 
                       /boot/grub/core.img

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    61,447,679    61,447,617   7 HPFS/NTFS
/dev/sda2          61,447,741   234,420,479   172,972,739   f W95 Ext d (LBA)
/dev/sda5          61,447,743   122,895,359    61,447,617   7 HPFS/NTFS
/dev/sda6         122,895,423   184,343,039    61,447,617   7 HPFS/NTFS
/dev/sda7         184,343,103   204,830,639    20,487,537   7 HPFS/NTFS
/dev/sda8         204,844,878   205,037,594       192,717  83 Linux
/dev/sda9         205,037,658   234,420,479    29,382,822  8e Linux LVM


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        1712950721F14759                       ntfs                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        5C4A541C87C51D64                       ntfs       Software                      
/dev/sda6        CFA73D4B003CA911                       ntfs       Media                         
/dev/sda7        0A53B99D55C12C90                       ntfs       Study                         
/dev/sda8        0ecf0703-31c8-48b4-9e86-6744a20fa9e8   ext3       /boot                         
/dev/sda9        0ba41003-4506-4be2-a91a-7c84e0dcd020   ext3                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda9        /                        ext3       (rw,errors=remount-ro,commit=0)


================================ sda1/boot.ini: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect 

============================= sda8/grub/grub.conf: =============================

# grub.conf generated by anaconda
#
# Note that you do not have to rerun grub after making changes to this file
# NOTICE:  You have a /boot partition.  This means that
#          all kernel and initrd paths are relative to /boot/, eg.
#          root (hd0,7)
#          kernel /vmlinuz-version ro root=/dev/VolGroup00/LogVol00
#          initrd /initrd-version.img
#boot=/dev/sda
default=1
timeout=5
splashimage=(hd0,7)/grub/splash.xpm.gz
hiddenmenu
title Red Hat Enterprise Linux Server (2.6.18-194.el5)
    root (hd0,7)
    kernel /vmlinuz-2.6.18-194.el5 ro root=/dev/VolGroup00/LogVol00 rhgb quiet
    initrd /initrd-2.6.18-194.el5.img
title Other
    rootnoverify (hd0,0)
    chainloader +1

=================== sda8: Location of files loaded by Grub: ===================


 104.9GB: grub/grub.conf
 104.9GB: grub/menu.lst
 104.9GB: grub/stage2
 104.8GB: initrd-2.6.18-194.el5.img
 104.8GB: vmlinuz-2.6.18-194.el5

=========================== sda9/boot/grub/menu.lst: ===========================

title Windows XP
root (sd0,0)
makeactive
chainloader +1

=========================== sda9/boot/grub/grub.cfg: ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  set have_grubenv=true
  load_env
fi
set default="0"
if [ "${prev_saved_entry}" ]; then
  set saved_entry="${prev_saved_entry}"
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z "${boot_once}" ]; then
    saved_entry="${chosen}"
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n "${have_grubenv}" ]; then if [ -z "${boot_once}" ]; then save_env recordfail; fi; fi
}

function load_video {
  insmod vbe
  insmod vga
}

insmod part_msdos
insmod ext2
set root='(hd0,msdos9)'
search --no-floppy --fs-uuid --set 0ba41003-4506-4be2-a91a-7c84e0dcd020
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos9)'
search --no-floppy --fs-uuid --set 0ba41003-4506-4be2-a91a-7c84e0dcd020
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos9)'
    search --no-floppy --fs-uuid --set 0ba41003-4506-4be2-a91a-7c84e0dcd020
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=0ba41003-4506-4be2-a91a-7c84e0dcd020 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos9)'
    search --no-floppy --fs-uuid --set 0ba41003-4506-4be2-a91a-7c84e0dcd020
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=0ba41003-4506-4be2-a91a-7c84e0dcd020 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-22-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos9)'
    search --no-floppy --fs-uuid --set 0ba41003-4506-4be2-a91a-7c84e0dcd020
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos9)'
    search --no-floppy --fs-uuid --set 0ba41003-4506-4be2-a91a-7c84e0dcd020
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 1712950721f14759
    drivemap -s (hd0) ${root}
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

### BEGIN /etc/grub.d/41_custom ###
if [ -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###

=============================== sda9/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sda9       /               ext3    errors=remount-ro 0       1

=================== sda9: Location of files loaded by Grub: ===================


 117.6GB: boot/grub/core.img
 117.5GB: boot/grub/grub.cfg
 117.6GB: boot/grub/menu.lst
 117.6GB: boot/initrd.img-2.6.35-22-generic
 117.6GB: boot/vmlinuz-2.6.35-22-generic
 117.6GB: initrd.img
 117.6GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda2

00000000  c3 e9 00 29 26 6a e5 4d  52 14 48 d2 d0 2c 16 8f  |...)&j.MR.H..,..|
00000010  53 30 42 34 65 c3 02 27  7a 91 9a 0a 02 37 a7 ac  |S0B4e..'z....7..|
00000020  87 48 83 52 10 d6 cc c6  00 2f 04 17 aa aa 23 48  |.H.R...../....#H|
00000030  e2 20 b6 f4 80 3f d2 a9  d2 f4 97 4e 9d 3a 40 23  |. ...?.....N.:@#|
00000040  48 03 d2 aa 08 ab 44 36  8a ae ab aa 55 17 e9 d3  |H.....D6....U...|
00000050  c6 00 4f 9a 44 89 41 c1  e7 6e 5e 12 ec c3 23 80  |..O.D.A..n^...#.|
00000060  70 57 58 3b 76 79 72 07  30 31 77 62 80 01 00 00  |pWX;vyr.01wb....|
00000070  ff fb 94 64 ed 00 02 8a  26 50 9b 29 31 50 61 8a  |...d....&P.)1Pa.|
00000080  ca 9a 15 e3 07 0a e5 49  69 a4 a4 60 b1 8a 2b ea  |.......Ii..`..+.|
00000090  9c f3 0d 3a 76 39 3b 7a  99 f9 b0 22 f4 1e 5f 34  |...:v9;z...".._4|
000000a0  99 51 d5 54 ca d3 3d 10  b6 b3 b3 36 97 cd 2b e9  |.Q.T..=....6..+.|
000000b0  a4 c5 bc fe db cc 8d 77  23 bd da 73 35 bd 12 b7  |.......w#..s5...|
000000c0  12 63 bb 2c 65 08 28 8a  6d c6 d8 0c 52 3d 1b f5  |.c.,e.(.m...R=..|
000000d0  8f 67 31 d9 db e9 a4 88  64 02 a2 fa 97 52 e7 04  |.g1.....d....R..|
000000e0  ac 5b b1 ba 32 25 dc 8e  b4 7f d9 18 a6 62 3b 70  |.[..2%.......b;p|
000000f0  66 36 e6 2a c2 35 ba a2  26 fe cf 4d 6a 58 01 00  |f6.*.5..&..MjX..|
00000100  a9 35 fc 89 32 27 5d f1  0f 55 ad 55 d4 d4 7a 93  |.5..2']..U.U..z.|
00000110  98 5b b1 cc a4 4c 3a e3  a3 91 1b 46 59 45 96 9b  |.[...L:....FYE..|
00000120  5b 17 3f 10 e8 64 7b 8b  45 3f 9c ca 6d 35 cf 3c  |[.?..d{.E?..m5.<|
00000130  49 c5 e6 2e b4 ce ce cb  45 94 f2 d3 a5 73 b0 cb  |I.......E....s..|
00000140  50 d1 e8 ce b9 51 9f 4a  a3 77 6b 3d a8 56 b5 ce  |P....Q.J.wk=.V..|
00000150  53 31 c2 46 91 65 76 61  cf 45 58 b9 c3 82 65 15  |S1.F.eva.EX...e.|
00000160  d0 4c 63 2a 40 12 9b 89  d5 dc 9a b9 3c fa 09 51  |.Lc*@.......<..Q|
00000170  a7 66 d1 09 99 66 11 2f  0c 60 24 ee 21 da 32 c8  |.f...f./.`$.!.2.|
00000180  ee bc 14 c5 af 7c ee 7d  32 05 44 2a a6 3a 08 41  |.....|.}2.D*.:.A|
00000190  70 75 d4 fa eb b4 df 1f  68 27 f1 44 12 ff e4 09  |pu......h'.D....|
000001a0  a8 4e 4c 75 7d 1f ff fc  38 08 45 98 da 29 36 d2  |.NLu}...8.E..)6.|
000001b0  70 ad f8 d8 db 9e df d5  19 69 a2 04 60 a7 00 ef  |p........i..`...|
000001c0  ff ff 07 ef ff ff 02 00  00 00 c1 9d a9 03 00 fe  |................|
000001d0  ff ff 05 fe ff ff c3 9d  a9 03 00 9e a9 03 00 00  |................|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

---

### Post by oldfred on 2010-12-15
You have Lilo in the MBR and need to have have grub. Note on grub-install the line has no number at the end or just drive sda, only the mount command refers to a partition sda9. Do not know if LVM changes anything as normally Ubuntu is not installed in a LVM although some other linux systems are.

#Comments are anything after the #, enter commands in terminal session
#Install MBR from LiveCD, Ubuntu install on sda9 and want grub2 in drive sda's MBR:
#Find linux partition, change sda9 if not correct:
sudo fdisk -l
#confirm that linux is sda9
sudo mount /dev/sda9 /mnt
sudo grub-install --root-directory=/mnt/ /dev/sda
#If that returns any errors run:
sudo grub-install --recheck --root-directory=/mnt/ /dev/sda

#More info here
How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)
Reinstall grub2 - Short version
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202)



You installed grub to the windows partition. All NTFS partitions have to have a windows signature and sda1 has to have to XP in its boot sector.

sda1: __________________________________________________  _______________________

    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info: [COLOR=Red] Grub 2 is installed in the boot sector of sda1[/COLOR] and 
                       looks at sector 229808474 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

Sso many were doing this that there is a web page by the author of the boot script:

Fix for most, a few have other issues, better than windows fix in many cases as it also fixes other parameters:
This has instructions on using testdisk to repair the install of grub to the boot sector for windows from Ubuntu or Linux LiveCD.
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)

After fixing it and rebooting into Ubuntu, you will have to do this for grub2's os prober to find the windows install.

You show both menu.lst from old grub legacy and grub.cfg. If the simple reinstall of grub2 does not work:

chroot & grub uninstall & reinstall
[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)

---

