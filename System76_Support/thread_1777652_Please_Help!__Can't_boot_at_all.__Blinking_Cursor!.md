---
title: "Please Help!  Can't boot at all.  Blinking Cursor!  (I've tried everything)"
date: 2011-06-08
forum: System76 Support
---

### Post by jimgwilliam on 2011-06-08
I have Ubuntu 10.10 on my System76 Pangolin.  I've never had a problem booting before, but now, it goes past the bios screen, then hangs with a blinking cursor.  I've seen people suggest

ctrl+alt+f1
unplugging all usb devices
holding shift to load grub screen then using e to edit the mode.  

The first two did nothing, and I don't think the 3rd is working either.  I hold shift . . . I do get the word "GRUB" to appear in the upper left hand corner, but right beside it the cursor continues to blink and I can't enter any input.

I'm really needing the computer tomorrow too, which is why I'm posting this at 1 in the morning. 

I'd really appreciate some help!

Thanks,
Jim

---

### Post by jimgwilliam on 2011-06-08
I've been using 11.04 actually, pardon my mistake.  I was usually just running in Ubuntu Classic Mode but I haven't had problems booting ever before and I'd upgraded almost 1-2 months ago.

---

### Post by Rubi1200 on 2011-06-08
Hi and welcome to the forums :-)

Please do the following so we can try and help you troubleshoot this:

Boot the Ubuntu Live CD/USB. Choose the option "Try Ubuntu without any changes." Once the desktop loads come back here and do the following:

1. Download the boot info script which is in a zipped file. There is a link in my signature.
2. Once downloaded, move the boot info script by either copying or dragging and dropping the zipped folder onto the desktop and unzip the contents by using right-click Extract here.
3. Open the folder and copy the script to the desktop (you can also drag and drop if you like)
4. Open a terminal and run the following command

```
sudo bash ~/Desktop/boot_info_script.sh
```

This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here in a new post. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

We also need to know what graphics card you have installed.

---

### Post by jimgwilliam on 2011-06-08
Thank you so much for your help!  The good news is I can see my entire file system on the desktop when I boot from live CD, so I know I haven't lost my stuff.  

I think I have an Nvidia graphics card, but I'm not totally positive.  Is there any easy way to find out?  I have a pangolin performance that I bought a year and a half or so.


```
                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 
    300673 of the same hard drive for core.img, but core.img can not be found 
    at this location.
 => Windows is installed in the MBR of /dev/sdb.
 => MS-DOS 3.30 through Windows 95 (A) is installed in the MBR of /dev/sdc.

sda1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub2 (v1.99)
    Boot sector info:   Grub2 (v1.99) is installed in the boot sector of sda1 
                       and looks at sector 318465 of the same hard drive for 
                       core.img. core.img is at this location and looks for 
                       (,msdos1)/boot/grub on this drive.
    Operating System:  Ubuntu 11.04
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sdc1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  Unknown
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *              1   965,355,468   965,355,468  83 Linux
/dev/sda2         965,355,469   976,773,167    11,417,699   5 Extended
/dev/sda5         965,355,470   976,773,167    11,417,698  83 Linux


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 999.5 GB, 999501594624 bytes
255 heads, 63 sectors/track, 121515 cylinders, total 1952151552 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1               2,048 1,952,151,551 1,952,149,504   7 NTFS / exFAT / HPFS


Drive: sdc _____________________________________________________________________

Disk /dev/sdc: 512 MB, 512483328 bytes
16 heads, 63 sectors/track, 993 cylinders, total 1000944 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdc1                 233       999,935       999,703   6 FAT16


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        625ed789-1cb3-4081-9c7e-f812810b5126   ext4       
/dev/sda5        6f2593f5-8a54-45b3-86d4-c4a0aaa3ee55   swap       
/dev/sdb1        12C23AD8C23AC031                       ntfs       warpdrive
/dev/sdc1        3B69-1AFD                              vfat       JIMGWILLIAM

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda1        /media/625ed789-1cb3-4081-9c7e-f812810b5126 ext4       (rw,nosuid,nodev,uhelper=udisks)
/dev/sdc1        /media/JIMGWILLIAM       vfat       (rw,nosuid,nodev,uhelper=udisks,uid=999,gid=999,shortname=mixed,dmask=0077,utf8=1,showexec,flush)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)


=========================== sda1/boot/grub/grub.cfg: ===========================

--------------------------------------------------------------------------------
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
  insmod video_bochs
  insmod video_cirrus
}

insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos1)'
search --no-floppy --fs-uuid --set=root 625ed789-1cb3-4081-9c7e-f812810b5126
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=1024x768
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos1)'
search --no-floppy --fs-uuid --set=root 625ed789-1cb3-4081-9c7e-f812810b5126
set locale_dir=($root)/boot/grub/locale
set lang=en_US
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
if background_color 44,0,30; then
  clear
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
set linux_gfx_mode=1024x768
export linux_gfx_mode
if [ "$linux_gfx_mode" != "text" ]; then load_video; fi
menuentry 'Ubuntu, with Linux 2.6.38-8-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root 625ed789-1cb3-4081-9c7e-f812810b5126
	linux	/boot/vmlinuz-2.6.38-8-generic root=UUID=625ed789-1cb3-4081-9c7e-f812810b5126 ro   quiet splash acpi_os_name=Linux acpi_osi=Linux vt.handoff=7
	initrd	/boot/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root 625ed789-1cb3-4081-9c7e-f812810b5126
	echo	'Loading Linux 2.6.38-8-generic ...'
	linux	/boot/vmlinuz-2.6.38-8-generic root=UUID=625ed789-1cb3-4081-9c7e-f812810b5126 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.38-8-generic
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, with Linux 2.6.35-28-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root 625ed789-1cb3-4081-9c7e-f812810b5126
	linux	/boot/vmlinuz-2.6.35-28-generic root=UUID=625ed789-1cb3-4081-9c7e-f812810b5126 ro   quiet splash acpi_os_name=Linux acpi_osi=Linux vt.handoff=7
	initrd	/boot/initrd.img-2.6.35-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-28-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root 625ed789-1cb3-4081-9c7e-f812810b5126
	echo	'Loading Linux 2.6.35-28-generic ...'
	linux	/boot/vmlinuz-2.6.35-28-generic root=UUID=625ed789-1cb3-4081-9c7e-f812810b5126 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-28-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root 625ed789-1cb3-4081-9c7e-f812810b5126
	linux	/boot/vmlinuz-2.6.32-28-generic root=UUID=625ed789-1cb3-4081-9c7e-f812810b5126 ro   quiet splash acpi_os_name=Linux acpi_osi=Linux vt.handoff=7
	initrd	/boot/initrd.img-2.6.32-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-28-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root 625ed789-1cb3-4081-9c7e-f812810b5126
	echo	'Loading Linux 2.6.32-28-generic ...'
	linux	/boot/vmlinuz-2.6.32-28-generic root=UUID=625ed789-1cb3-4081-9c7e-f812810b5126 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-28-generic
}
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root 625ed789-1cb3-4081-9c7e-f812810b5126
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root 625ed789-1cb3-4081-9c7e-f812810b5126
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
if [ "x${timeout}" != "x-1" ]; then
  if keystatus; then
    if keystatus --shift; then
      set timeout=-1
    else
      set timeout=0
    fi
  else
    if sleep --interruptible 3 ; then
      set timeout=0
    fi
  fi
fi
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
--------------------------------------------------------------------------------

=============================== sda1/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc	/proc	proc	nodev,noexec,nosuid	0	0
# / was on /dev/sda1 during installation
# Commented out by Dropbox
# UUID=625ed789-1cb3-4081-9c7e-f812810b5126	/	ext4	errors=remount-ro	0	1	# /dev/sda1
# swap was on /dev/sda5 during installation
UUID=6f2593f5-8a54-45b3-86d4-c4a0aaa3ee55	none	swap	sw	0	0	# /dev/sda5

//lstore.lcsr.jhu.edu/home/Haptics /media/lstore cifs auto,iocharset=utf8,uid=jimgwilliam,credentials=/root/.lstore_credentials,file_mode=0777,dir_mode=0777 0 0

# //172.30.4.5/Data /media/somsrv5_Data cifs auto,iocharset=utf8,uid=jimgwilliam,credentials=/root/.cifs_somsrv5_credentials,file_mode=0775,dir_mode=0775 0 0




UUID=625ed789-1cb3-4081-9c7e-f812810b5126 / ext4 errors=remount-ro,user_xattr 0 1
--------------------------------------------------------------------------------

=================== sda1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

   0.151882648 = 0.163082752    boot/grub/core.img                             1
   2.934402943 = 3.150791168    boot/grub/grub.cfg                             1
  90.772488117 = 97.466216960   boot/initrd.img-2.6.32-28-generic              2
  29.842716694 = 32.043373056   boot/initrd.img-2.6.35-28-generic              3
  33.696743488 = 36.181602816   boot/initrd.img-2.6.38-8-generic               3
   1.787209034 = 1.919001088    boot/vmlinuz-2.6.32-28-generic                 1
  31.763363361 = 34.105651712   boot/vmlinuz-2.6.35-28-generic                 2
  68.406559467 = 73.450983936   boot/vmlinuz-2.6.38-8-generic                  2
  33.696743488 = 36.181602816   initrd.img                                     3
  29.842716694 = 32.043373056   initrd.img.old                                 3
  68.406559467 = 73.450983936   vmlinuz                                        2
  31.763363361 = 34.105651712   vmlinuz.old                                    2

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sdc1

00000000  eb 3c 90 2b 42 73 36 72  49 48 43 00 02 20 01 00  |.<.+Bs6rIHC.. ..|
00000010  02 00 02 00 00 f8 7b 00  3f 00 10 00 e9 00 00 00  |......{.?.......|
00000020  17 41 0f 00 80 00 29 fd  1a 69 3b 4e 4f 20 4e 41  |.A....)..i;NO NA|
00000030  4d 45 20 20 20 20 46 41  54 31 36 20 20 20 fa 33  |ME    FAT16   .3|
00000040  c0 8e d0 bc 00 7c 16 07  bb 78 00 36 c5 37 1e 56  |.....|...x.6.7.V|
00000050  16 53 bf 3e 7c b9 0b 00  fc f3 a4 06 1f c6 45 fe  |.S.>|.........E.|
00000060  0f 8b 0e 18 7c 88 4d f9  89 47 02 c7 07 3e 7c fb  |....|.M..G...>|.|
00000070  cd 13 72 79 33 c0 39 06  13 7c 74 08 8b 0e 13 7c  |..ry3.9..|t....||
00000080  89 0e 20 7c a0 10 7c f7  26 16 7c 03 06 1c 7c 13  |.. |..|.&.|...|.|
00000090  16 1e 7c 03 06 0e 7c 83  d2 00 a3 50 7c 89 16 52  |..|...|....P|..R|
000000a0  7c a3 49 7c 89 16 4b 7c  b8 20 00 f7 26 11 7c 8b  ||.I|..K|. ..&.|.|
000000b0  1e 0b 7c 03 c3 48 f7 f3  01 06 49 7c 83 16 4b 7c  |..|..H....I|..K||
000000c0  00 bb 00 05 8b 16 52 7c  a1 50 7c e8 92 00 72 1d  |......R|.P|...r.|
000000d0  b0 01 e8 ac 00 72 16 8b  fb b9 0b 00 be e6 7d f3  |.....r........}.|
000000e0  a6 75 0a 8d 7f 20 b9 0b  00 f3 a6 74 18 be 9e 7d  |.u... .....t...}|
000000f0  e8 5f 00 33 c0 cd 16 5e  1f 8f 04 8f 44 02 cd 19  |._.3...^....D...|
00000100  58 58 58 eb e8 8b 47 1a  48 48 8a 1e 0d 7c 32 ff  |XXX...G.HH...|2.|
00000110  f7 e3 03 06 49 7c 13 16  4b 7c bb 00 07 b9 03 00  |....I|..K|......|
00000120  50 52 51 e8 3a 00 72 d8  b0 01 e8 54 00 59 5a 58  |PRQ.:.r....T.YZX|
00000130  72 bb 05 01 00 83 d2 00  03 1e 0b 7c e2 e2 8a 2e  |r..........|....|
00000140  15 7c 8a 16 24 7c 8b 1e  49 7c a1 4b 7c ea 00 00  |.|..$|..I|.K|...|
00000150  70 00 ac 0a c0 74 29 b4  0e bb 07 00 cd 10 eb f2  |p....t).........|
00000160  3b 16 18 7c 73 19 f7 36  18 7c fe c2 88 16 4f 7c  |;..|s..6.|....O||
00000170  33 d2 f7 36 1a 7c 88 16  25 7c a3 4d 7c f8 c3 f9  |3..6.|..%|.M|...|
00000180  c3 b4 02 8b 16 4d 7c b1  06 d2 e6 0a 36 4f 7c 8b  |.....M|.....6O|.|
00000190  ca 86 e9 8a 16 24 7c 8a  36 25 7c cd 13 c3 0d 0a  |.....$|.6%|.....|
000001a0  4e 6f 6e 2d 53 79 73 74  65 6d 20 64 69 73 6b 20  |Non-System disk |
000001b0  6f 72 20 64 69 73 6b 20  65 72 72 6f 72 0d 0a 52  |or disk error..R|
000001c0  65 70 6c 61 63 65 20 61  6e 64 20 70 72 65 73 73  |eplace and press|
000001d0  20 61 6e 79 20 6b 65 79  20 77 68 65 6e 20 72 65  | any key when re|
000001e0  61 64 79 0d 0a 00 49 4f  20 20 20 20 20 20 53 59  |ady...IO      SY|
000001f0  53 4d 53 44 4f 53 20 20  20 53 59 53 00 00 55 aa  |SMSDOS   SYS..U.|
00000200


=============================== StdErr Messages: ===============================

unlzma: Decoder error

```

---

### Post by Rubi1200 on 2011-06-08
Thanks for the results.

So, from the LiveCD this is what you need to do:

Open a terminal and run these 2 commands:
[FONT=monospace]
[/FONT]```
sudo mount /dev/sda1 /mnt
sudo grub-install --boot-directory=/mnt/boot /dev/sda

```

Once the command completes you can reboot taking out the CD.

Back in Ubuntu, run this command:

```
sudo update-grub
```

Hopefully this resolves the problem.

---

### Post by jimgwilliam on 2011-06-08
Just one question before I do this.  Is there any chance I will lose the files on my computer by doing this?

I guess just to be safe, I'm currently copying everything in my /home/jimgwilliam/   folder to an external hard drive.

Once that's done I'll run those commands.

Any idea why this might have happened or if there is something I can do to prevent it in the future?  Just want to understand what I did to cause this to happen?

---

### Post by Rubi1200 on 2011-06-08
In theory I think it is highly unlikely that could happen. The problem seems to be that some GRUB files were installed to the partition rather than the MBR of the drive.

All you are doing is reinstalling those files to the MBR.

Of course, backing up is something you should be doing anyway.

By the way, are you aware that 11.04 is marked as the current installation and not 10.10?

In other words, the system has been upgraded.

That is a possible cause of the problem with the GRUB files.

---

### Post by BoomSie on 2011-06-08
You should be safe entering the commands Rubi1200 suggested. All it does is reinstall grub in the designated map and reset the MBR.

You don't actually change partitions if that's what you're afraid of. (loosing / corrupting tables / data)

---

### Post by jimgwilliam on 2011-06-08
Rubi1200 thanks. Yes, I actually knew I had upgraded to 11.04 and it wasn't recently. I'm not sure why I wrote 10.10. That's what makes this very odd since I've been running 11.04 with no boot problems for many months.

I'll try the instructions a little later on when I'm home.
Thanks.

---

### Post by drs305 on 2011-06-08
Hopefully after (or even before) reinstalling Grub you will get to the menu. If holding down the SHIFT key during boot isn't showing it, you can also try repeatedly pressing the ESC key.

If you can get to the menu and press "e", the chances are reasonable that if you add "nomodeset" and remove "quiet splash vt.handoff=7" at the end of the *linux* line, then press CTRL-x to boot, you will get to the Desktop. If you do, add the nvidia driver and hopefully that will fix things.

---

### Post by jimgwilliam on 2011-06-08
Rubi1200,

I did the first two command lines in a terminal after booting from the live CD.  The following was returned:

```
/usr/sbin/grub-setup: warn: This msdos-style partition label has no post-MBR gap; embedding won't be possible!.
/usr/sbin/grub-setup: warn: Embedding is not possible.  GRUB can only be installed in this setup by using blocklists.  However, blocklists are UNRELIABLE and their use is discouraged..
/usr/sbin/grub-setup: error: will not proceed with blocklists.
```

Then I reboot, it ejects the Live CD, I selected F2 to now boot from the hard disk (since it was set to boot for the Live CD), and I'm back at the black screen with blinking terminal.  So I was never able to boot back into ubuntu in order to run the final update grub command.  

Thoughts?

---

### Post by jimgwilliam on 2011-06-08
drs305 I've tried this, but when I hold shift, all I get are the letters "GRUB" in the upper left corner with nothing else visible.  The blinking cursor sits and blinks next to the word "GRUB" and I can't enter, scroll, or see anything.  Eventually the keys start beeping if I try to scroll.  But the screen is still black w/ cursor except the word "GRUB" appears.

---

### Post by jimgwilliam on 2011-06-08
Rubi1200,

I was also suggested to try this but haven't yet.  Would this work since the other solution appeared not to?

[http://www.knowledge76.com/index.php/Restore_Grub_Bootloader](http://www.knowledge76.com/index.php/Restore_Grub_Bootloader)

---

### Post by drs305 on 2011-06-08
You can try purging/reinstalling Grub2. It won't hurt and it may solve the problem unless the issue has to do with a corrupted partition table.  In addition to the link you provided, you can take a look at the "Chroot" link in my signature line, which provides information on the same process but also details some additional information.

Also in my link, I've recently added a link in the "Chroot" section to a page which shows the process with a nice selection of graphics.

If you run the purge/reinstall procedure, make sure you install only to the MBR and not to a partition.

---

### Post by osx424242 on 2011-06-08
> **jimgwilliam said:**
> I did the first two command lines in a terminal after booting from the live CD.  The following was returned:

```
/usr/sbin/grub-setup: warn: This msdos-style partition label has no post-MBR gap; embedding won't be possible!.
/usr/sbin/grub-setup: warn: Embedding is not possible.  GRUB can only be installed in this setup by using blocklists.  However, blocklists are UNRELIABLE and their use is discouraged..
/usr/sbin/grub-setup: error: will not proceed with blocklists.
```

Really silly question here, but are you sure you got the right command?  I had to run grub-install last night and I think I got that exact same error when I tried to install to /dev/sda1 instead of /dev/sda.  Might be worth trying again, just in case.

---

### Post by jimgwilliam on 2011-06-08
Thanks for all the help folks.  This article on the 76 wiki page totally fixed my problem.  I really appreciate the responses. Very impressive how many offer help.  I hope someday to be an experienced enough linux user I can return the favor.

[http://www.knowledge76.com/index.php/Restore_Grub_Bootloader](http://www.knowledge76.com/index.php/Restore_Grub_Bootloader)

---

### Post by Rubi1200 on 2011-06-08
> **jimgwilliam said:**
> Thanks for all the help folks.  This article on the 76 wiki page totally fixed my problem.  I really appreciate the responses. Very impressive how many offer help.  I hope someday to be an experienced enough linux user I can return the favor.

[http://www.knowledge76.com/index.php/Restore_Grub_Bootloader](http://www.knowledge76.com/index.php/Restore_Grub_Bootloader)
Glad you got things sorted out in the end :-)

Please mark this Solved using the Thread Tools near the top of the page.

Enjoy!

---

