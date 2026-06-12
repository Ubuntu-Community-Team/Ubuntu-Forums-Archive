---
title: "problems installing wtith separate home folder"
date: 2011-12-05
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by mick222 on 2011-12-05
I tried to install the alpha of 12.04. after boot it seems i have no home folder. sda5 is / sda7 is /home  also tried using sda4 as home as this is where my home folder is in 11.10 and 11.04 .
After booting into recovery i get dropped to a root prompt when i cd /home and do ls -l i get total 0
Does this mean home wasn't mounted.

I have attached a screenshot of my partitions

---

### Post by nanog on 2011-12-05
you need to edit /etc/passwd  to include the path to your "home".

---

### Post by mick222 on 2011-12-06
Tried to edit etc/passwd but everything seems ok fstab also has the correct address for /home
```
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=1c44dac4-0301-4df7-815d-10ba0c368167 /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda7 during installation
UUID=50e0fd68-4db9-487b-992e-d1e75822dfd7 /home           ext4    defaults        0       2
# swap was on /dev/sda6 during installation
UUID=ec51e594-b3c9-491d-b096-ac879bc02770 none            swap    sw              0       0
```
```
root:x:0:0:root:/root:/bin/bash
daemon:x:1:1:daemon:/usr/sbin:/bin/sh
bin:x:2:2:bin:/bin:/bin/sh
sys:x:3:3:sys:/dev:/bin/sh
sync:x:4:65534:sync:/bin:/bin/sync
games:x:5:60:games:/usr/games:/bin/sh
man:x:6:12:man:/var/cache/man:/bin/sh
lp:x:7:7:lp:/var/spool/lpd:/bin/sh
mail:x:8:8:mail:/var/mail:/bin/sh
news:x:9:9:news:/var/spool/news:/bin/sh
uucp:x:10:10:uucp:/var/spool/uucp:/bin/sh
proxy:x:13:13:proxy:/bin:/bin/sh
www-data:x:33:33:www-data:/var/www:/bin/sh
backup:x:34:34:backup:/var/backups:/bin/sh
list:x:38:38:Mailing List Manager:/var/list:/bin/sh
irc:x:39:39:ircd:/var/run/ircd:/bin/sh
gnats:x:41:41:Gnats Bug-Reporting System (admin):/var/lib/gnats:/bin/sh
nobody:x:65534:65534:nobody:/nonexistent:/bin/sh
libuuid:x:100:101::/var/lib/libuuid:/bin/sh
syslog:x:101:103::/home/syslog:/bin/false
colord:x:102:105:colord colour management daemon,,,:/var/lib/colord:/bin/false
messagebus:x:103:107::/var/run/dbus:/bin/false
lightdm:x:104:108:Light Display Manager:/var/lib/lightdm:/bin/false
avahi-autoipd:x:105:112:Avahi autoip daemon,,,:/var/lib/avahi-autoipd:/bin/false
avahi:x:106:113:Avahi mDNS daemon,,,:/var/run/avahi-daemon:/bin/false
usbmux:x:107:46:usbmux daemon,,,:/home/usbmux:/bin/false
kernoops:x:108:65534:Kernel Oops Tracking Daemon,,,:/:/bin/false
pulse:x:109:118:PulseAudio daemon,,,:/var/run/pulse:/bin/false
rtkit:x:110:121:RealtimeKit,,,:/proc:/bin/false
speech-dispatcher:x:111:29:Speech Dispatcher,,,:/var/run/speech-dispatcher:/bin/sh
hplip:x:112:7:HPLIP system user,,,:/var/run/hplip:/bin/false
saned:x:113:122::/home/saned:/bin/false
michael:x:1000:1000:michael,,,:/home/michael:/bin/bash
```

---

### Post by mick222 on 2011-12-06
Also ran bootinfoscript posted below.
[PHP]                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for  on this drive.

sda1: __________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.10
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda2: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda3: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu precise (development 
                       branch)
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda7: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        

sda4: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *             63    29,302,559    29,302,497  83 Linux
/dev/sda2         183,141,000   212,437,874    29,296,875  83 Linux
/dev/sda3         212,441,086   312,580,095   100,139,010   5 Extended
/dev/sda5         212,441,088   242,884,607    30,443,520  83 Linux
/dev/sda6         310,542,336   312,580,095     2,037,760  82 Linux swap / Solaris
/dev/sda7         242,886,656   310,540,287    67,653,632  83 Linux
/dev/sda4          29,302,560   183,140,999   153,838,440  83 Linux


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        73cf4420-f9de-495c-ac7d-a6278e0ee811   ext3       
/dev/sda2        47f17943-077c-4d64-b573-360bd8ba2c06   ext4       ubuntu
/dev/sda4        6e503435-c52b-44d5-ac46-e88fc896a79e   ext4       home
/dev/sda5        1c44dac4-0301-4df7-815d-10ba0c368167   ext4       
/dev/sda6        ec51e594-b3c9-491d-b096-ac879bc02770   swap       
/dev/sda7        50e0fd68-4db9-487b-992e-d1e75822dfd7   ext4       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda1        /                        ext3       (rw,errors=remount-ro,commit=0)
/dev/sda4        /home                    ext4       (rw,commit=0)
/dev/sda5        /media/1c44dac4-0301-4df7-815d-10ba0c368167 ext4       (rw,nosuid,nodev,uhelper=udisks)
/dev/sda7        /media/50e0fd68-4db9-487b-992e-d1e75822dfd7 ext4       (rw,nosuid,nodev,uhelper=udisks)


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
set root='(hd0,msdos1)'
search --no-floppy --fs-uuid --set=root 73cf4420-f9de-495c-ac7d-a6278e0ee811
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  insmod part_msdos
  insmod ext2
  set root='(hd0,msdos1)'
  search --no-floppy --fs-uuid --set=root 73cf4420-f9de-495c-ac7d-a6278e0ee811
  set locale_dir=($root)/boot/grub/locale
  set lang=en_US
  insmod gettext
fi
terminal_output gfxterm
if [ "${recordfail}" = 1 ]; then
  set timeout=10
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
insmod part_msdos
insmod ext2
set root='(hd0,msdos1)'
search --no-floppy --fs-uuid --set=root 73cf4420-f9de-495c-ac7d-a6278e0ee811
insmod png
if background_image /usr/share/images/desktop-base/spacefun-grub.png; then
  set color_normal=light-gray/black
  set color_highlight=white/black
else
  set menu_color_normal=white/black
  set menu_color_highlight=black/light-gray
  if background_color 44,0,30; then
    clear
  fi
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
if [ ${recordfail} != 1 ]; then
  if [ -e ${prefix}/gfxblacklist.txt ]; then
    if hwmatch ${prefix}/gfxblacklist.txt 3; then
      if [ ${match} = 0 ]; then
        set linux_gfx_mode=keep
      else
        set linux_gfx_mode=text
      fi
    else
      set linux_gfx_mode=text
    fi
  else
    set linux_gfx_mode=keep
  fi
else
  set linux_gfx_mode=text
fi
export linux_gfx_mode
if [ "$linux_gfx_mode" != "text" ]; then load_video; fi
menuentry 'Ubuntu, with Linux 3.0.0-13-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set=root 73cf4420-f9de-495c-ac7d-a6278e0ee811
	linux	/boot/vmlinuz-3.0.0-13-generic root=UUID=73cf4420-f9de-495c-ac7d-a6278e0ee811 ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-3.0.0-13-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-13-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set=root 73cf4420-f9de-495c-ac7d-a6278e0ee811
	echo	'Loading Linux 3.0.0-13-generic ...'
	linux	/boot/vmlinuz-3.0.0-13-generic root=UUID=73cf4420-f9de-495c-ac7d-a6278e0ee811 ro recovery nomodeset 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-3.0.0-13-generic
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, with Linux 3.0.0-12-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set=root 73cf4420-f9de-495c-ac7d-a6278e0ee811
	linux	/boot/vmlinuz-3.0.0-12-generic root=UUID=73cf4420-f9de-495c-ac7d-a6278e0ee811 ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-3.0.0-12-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-12-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set=root 73cf4420-f9de-495c-ac7d-a6278e0ee811
	echo	'Loading Linux 3.0.0-12-generic ...'
	linux	/boot/vmlinuz-3.0.0-12-generic root=UUID=73cf4420-f9de-495c-ac7d-a6278e0ee811 ro recovery nomodeset 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-3.0.0-12-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-11-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set=root 73cf4420-f9de-495c-ac7d-a6278e0ee811
	linux	/boot/vmlinuz-3.0.0-11-generic root=UUID=73cf4420-f9de-495c-ac7d-a6278e0ee811 ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-3.0.0-11-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-11-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set=root 73cf4420-f9de-495c-ac7d-a6278e0ee811
	echo	'Loading Linux 3.0.0-11-generic ...'
	linux	/boot/vmlinuz-3.0.0-11-generic root=UUID=73cf4420-f9de-495c-ac7d-a6278e0ee811 ro recovery nomodeset 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-3.0.0-11-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-10-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set=root 73cf4420-f9de-495c-ac7d-a6278e0ee811
	linux	/boot/vmlinuz-3.0.0-10-generic root=UUID=73cf4420-f9de-495c-ac7d-a6278e0ee811 ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-3.0.0-10-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-10-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set=root 73cf4420-f9de-495c-ac7d-a6278e0ee811
	echo	'Loading Linux 3.0.0-10-generic ...'
	linux	/boot/vmlinuz-3.0.0-10-generic root=UUID=73cf4420-f9de-495c-ac7d-a6278e0ee811 ro recovery nomodeset 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-3.0.0-10-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-9-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set=root 73cf4420-f9de-495c-ac7d-a6278e0ee811
	linux	/boot/vmlinuz-3.0.0-9-generic root=UUID=73cf4420-f9de-495c-ac7d-a6278e0ee811 ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-3.0.0-9-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-9-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set=root 73cf4420-f9de-495c-ac7d-a6278e0ee811
	echo	'Loading Linux 3.0.0-9-generic ...'
	linux	/boot/vmlinuz-3.0.0-9-generic root=UUID=73cf4420-f9de-495c-ac7d-a6278e0ee811 ro recovery nomodeset 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-3.0.0-9-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-8-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set=root 73cf4420-f9de-495c-ac7d-a6278e0ee811
	linux	/boot/vmlinuz-3.0.0-8-generic root=UUID=73cf4420-f9de-495c-ac7d-a6278e0ee811 ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-3.0.0-8-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-8-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set=root 73cf4420-f9de-495c-ac7d-a6278e0ee811
	echo	'Loading Linux 3.0.0-8-generic ...'
	linux	/boot/vmlinuz-3.0.0-8-generic root=UUID=73cf4420-f9de-495c-ac7d-a6278e0ee811 ro recovery nomodeset 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-3.0.0-8-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-7-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set=root 73cf4420-f9de-495c-ac7d-a6278e0ee811
	linux	/boot/vmlinuz-3.0.0-7-generic root=UUID=73cf4420-f9de-495c-ac7d-a6278e0ee811 ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-3.0.0-7-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-7-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set=root 73cf4420-f9de-495c-ac7d-a6278e0ee811
	echo	'Loading Linux 3.0.0-7-generic ...'
	linux	/boot/vmlinuz-3.0.0-7-generic root=UUID=73cf4420-f9de-495c-ac7d-a6278e0ee811 ro recovery nomodeset 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-3.0.0-7-generic
}
menuentry 'Ubuntu, with Linux 3.0-3-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set=root 73cf4420-f9de-495c-ac7d-a6278e0ee811
	linux	/boot/vmlinuz-3.0-3-generic root=UUID=73cf4420-f9de-495c-ac7d-a6278e0ee811 ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-3.0-3-generic
}
menuentry 'Ubuntu, with Linux 3.0-3-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set=root 73cf4420-f9de-495c-ac7d-a6278e0ee811
	echo	'Loading Linux 3.0-3-generic ...'
	linux	/boot/vmlinuz-3.0-3-generic root=UUID=73cf4420-f9de-495c-ac7d-a6278e0ee811 ro recovery nomodeset 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-3.0-3-generic
}
menuentry 'Ubuntu, with Linux 3.0-1-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set=root 73cf4420-f9de-495c-ac7d-a6278e0ee811
	linux	/boot/vmlinuz-3.0-1-generic root=UUID=73cf4420-f9de-495c-ac7d-a6278e0ee811 ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-3.0-1-generic
}
menuentry 'Ubuntu, with Linux 3.0-1-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set=root 73cf4420-f9de-495c-ac7d-a6278e0ee811
	echo	'Loading Linux 3.0-1-generic ...'
	linux	/boot/vmlinuz-3.0-1-generic root=UUID=73cf4420-f9de-495c-ac7d-a6278e0ee811 ro recovery nomodeset 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-3.0-1-generic
}
menuentry 'Ubuntu, with Linux 3.0-0-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set=root 73cf4420-f9de-495c-ac7d-a6278e0ee811
	linux	/boot/vmlinuz-3.0-0-generic root=UUID=73cf4420-f9de-495c-ac7d-a6278e0ee811 ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-3.0-0-generic
}
menuentry 'Ubuntu, with Linux 3.0-0-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set=root 73cf4420-f9de-495c-ac7d-a6278e0ee811
	echo	'Loading Linux 3.0-0-generic ...'
	linux	/boot/vmlinuz-3.0-0-generic root=UUID=73cf4420-f9de-495c-ac7d-a6278e0ee811 ro recovery nomodeset 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-3.0-0-generic
}
menuentry 'Ubuntu, with Linux 2.6.39-3-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set=root 73cf4420-f9de-495c-ac7d-a6278e0ee811
	linux	/boot/vmlinuz-2.6.39-3-generic root=UUID=73cf4420-f9de-495c-ac7d-a6278e0ee811 ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-2.6.39-3-generic
}
menuentry 'Ubuntu, with Linux 2.6.39-3-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set=root 73cf4420-f9de-495c-ac7d-a6278e0ee811
	echo	'Loading Linux 2.6.39-3-generic ...'
	linux	/boot/vmlinuz-2.6.39-3-generic root=UUID=73cf4420-f9de-495c-ac7d-a6278e0ee811 ro recovery nomodeset 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.39-3-generic
}
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set=root 73cf4420-f9de-495c-ac7d-a6278e0ee811
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set=root 73cf4420-f9de-495c-ac7d-a6278e0ee811
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Ubuntu, with Linux 2.6.38-10-generic-pae (on /dev/sda2)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set=root 47f17943-077c-4d64-b573-360bd8ba2c06
	linux /boot/vmlinuz-2.6.38-10-generic-pae root=UUID=47f17943-077c-4d64-b573-360bd8ba2c06 ro quiet splash vt.handoff=7
	initrd /boot/initrd.img-2.6.38-10-generic-pae
}
menuentry "Ubuntu, with Linux 2.6.38-10-generic-pae (recovery mode) (on /dev/sda2)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set=root 47f17943-077c-4d64-b573-360bd8ba2c06
	linux /boot/vmlinuz-2.6.38-10-generic-pae root=UUID=47f17943-077c-4d64-b573-360bd8ba2c06 ro single
	initrd /boot/initrd.img-2.6.38-10-generic-pae
}
menuentry "Ubuntu, with Linux 2.6.38-8-generic-pae (on /dev/sda2)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set=root 47f17943-077c-4d64-b573-360bd8ba2c06
	linux /boot/vmlinuz-2.6.38-8-generic-pae root=UUID=47f17943-077c-4d64-b573-360bd8ba2c06 ro quiet splash vt.handoff=7
	initrd /boot/initrd.img-2.6.38-8-generic-pae
}
menuentry "Ubuntu, with Linux 2.6.38-8-generic-pae (recovery mode) (on /dev/sda2)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set=root 47f17943-077c-4d64-b573-360bd8ba2c06
	linux /boot/vmlinuz-2.6.38-8-generic-pae root=UUID=47f17943-077c-4d64-b573-360bd8ba2c06 ro single
	initrd /boot/initrd.img-2.6.38-8-generic-pae
}
menuentry "Ubuntu, with Linux 2.6.35-28-generic-pae (on /dev/sda2)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set=root 47f17943-077c-4d64-b573-360bd8ba2c06
	linux /boot/vmlinuz-2.6.35-28-generic-pae root=UUID=47f17943-077c-4d64-b573-360bd8ba2c06 ro quiet splash vt.handoff=7
	initrd /boot/initrd.img-2.6.35-28-generic-pae
}
menuentry "Ubuntu, with Linux 2.6.35-28-generic-pae (recovery mode) (on /dev/sda2)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set=root 47f17943-077c-4d64-b573-360bd8ba2c06
	linux /boot/vmlinuz-2.6.35-28-generic-pae root=UUID=47f17943-077c-4d64-b573-360bd8ba2c06 ro single
	initrd /boot/initrd.img-2.6.35-28-generic-pae
}
menuentry "Ubuntu, with Linux 2.6.35-24-generic-pae (on /dev/sda2)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set=root 47f17943-077c-4d64-b573-360bd8ba2c06
	linux /boot/vmlinuz-2.6.35-24-generic-pae root=UUID=47f17943-077c-4d64-b573-360bd8ba2c06 ro quiet splash vt.handoff=7
	initrd /boot/initrd.img-2.6.35-24-generic-pae
}
menuentry "Ubuntu, with Linux 2.6.35-24-generic-pae (recovery mode) (on /dev/sda2)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set=root 47f17943-077c-4d64-b573-360bd8ba2c06
	linux /boot/vmlinuz-2.6.35-24-generic-pae root=UUID=47f17943-077c-4d64-b573-360bd8ba2c06 ro single
	initrd /boot/initrd.img-2.6.35-24-generic-pae
}
menuentry "Ubuntu, with Linux 2.6.35-23-generic-pae (on /dev/sda2)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set=root 47f17943-077c-4d64-b573-360bd8ba2c06
	linux /boot/vmlinuz-2.6.35-23-generic-pae root=UUID=47f17943-077c-4d64-b573-360bd8ba2c06 ro quiet splash vt.handoff=7
	initrd /boot/initrd.img-2.6.35-23-generic-pae
}
menuentry "Ubuntu, with Linux 2.6.35-23-generic-pae (recovery mode) (on /dev/sda2)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set=root 47f17943-077c-4d64-b573-360bd8ba2c06
	linux /boot/vmlinuz-2.6.35-23-generic-pae root=UUID=47f17943-077c-4d64-b573-360bd8ba2c06 ro single
	initrd /boot/initrd.img-2.6.35-23-generic-pae
}
menuentry "Ubuntu, with Linux 2.6.35-22-generic-pae (on /dev/sda2)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set=root 47f17943-077c-4d64-b573-360bd8ba2c06
	linux /boot/vmlinuz-2.6.35-22-generic-pae root=UUID=47f17943-077c-4d64-b573-360bd8ba2c06 ro quiet splash vt.handoff=7
	initrd /boot/initrd.img-2.6.35-22-generic-pae
}
menuentry "Ubuntu, with Linux 2.6.35-22-generic-pae (recovery mode) (on /dev/sda2)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set=root 47f17943-077c-4d64-b573-360bd8ba2c06
	linux /boot/vmlinuz-2.6.35-22-generic-pae root=UUID=47f17943-077c-4d64-b573-360bd8ba2c06 ro single
	initrd /boot/initrd.img-2.6.35-22-generic-pae
}
menuentry "Ubuntu, with Linux 2.6.32-25-generic-pae (on /dev/sda2)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set=root 47f17943-077c-4d64-b573-360bd8ba2c06
	linux /boot/vmlinuz-2.6.32-25-generic-pae root=UUID=47f17943-077c-4d64-b573-360bd8ba2c06 ro quiet splash vt.handoff=7
	initrd /boot/initrd.img-2.6.32-25-generic-pae
}
menuentry "Ubuntu, with Linux 2.6.32-25-generic-pae (recovery mode) (on /dev/sda2)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set=root 47f17943-077c-4d64-b573-360bd8ba2c06
	linux /boot/vmlinuz-2.6.32-25-generic-pae root=UUID=47f17943-077c-4d64-b573-360bd8ba2c06 ro single
	initrd /boot/initrd.img-2.6.32-25-generic-pae
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
--------------------------------------------------------------------------------

=============================== sda1/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=73cf4420-f9de-495c-ac7d-a6278e0ee811 /               ext3    errors=remount-ro 0       1
# /home was on /dev/sda4 during installation
UUID=6e503435-c52b-44d5-ac46-e88fc896a79e /home           ext4    defaults        0       2
# swap was on /dev/sda6 during installation
UUID=8635eaa6-7eee-4f77-aa06-9b52db10a9a6 none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

  13.070369244 = 14.034202112   boot/grub/core.img                             1
  13.164241314 = 14.134996480   boot/grub/grub.cfg                             3
  13.068145275 = 14.031814144   boot/initrd.img-2.6.39-3-generic               6
  13.193210125 = 14.166101504   boot/initrd.img-3.0.0-10-generic              49
  13.245311260 = 14.222044672   boot/initrd.img-3.0.0-11-generic              113
  13.424312115 = 14.414245376   boot/initrd.img-3.0.0-12-generic              23
  13.341720104 = 14.325562880   boot/initrd.img-3.0.0-13-generic              12
  13.121882915 = 14.089514496   boot/initrd.img-3.0.0-7-generic               14
  13.173507214 = 14.144945664   boot/initrd.img-3.0.0-8-generic               179
  13.190738201 = 14.163447296   boot/initrd.img-3.0.0-9-generic               42
  13.030929089 = 13.991853568   boot/initrd.img-3.0-0-generic                  9
  13.053561687 = 14.016155136   boot/initrd.img-3.0-1-generic                  8
  13.147120953 = 14.116613632   boot/initrd.img-3.0-3-generic                 18
  13.101970196 = 14.068133376   boot/vmlinuz-2.6.39-3-generic                  3
  13.091578960 = 14.056975872   boot/vmlinuz-3.0.0-10-generic                 14
  13.218612194 = 14.193376768   boot/vmlinuz-3.0.0-11-generic                  4
  13.214278698 = 14.188723712   boot/vmlinuz-3.0.0-12-generic                 67
  13.324981213 = 14.307589632   boot/vmlinuz-3.0.0-13-generic                  3
  13.039081097 = 14.000606720   boot/vmlinuz-3.0.0-7-generic                   3
  13.012282848 = 13.971832320   boot/vmlinuz-3.0.0-8-generic                   4
  13.176772594 = 14.148451840   boot/vmlinuz-3.0.0-9-generic                  237
  13.108680248 = 14.075338240   boot/vmlinuz-3.0-0-generic                     3
  13.123790264 = 14.091562496   boot/vmlinuz-3.0-1-generic                     7
  13.073268414 = 14.037315072   boot/vmlinuz-3.0-3-generic                     5
  13.341720104 = 14.325562880   initrd.img                                    12
  13.424312115 = 14.414245376   initrd.img.old                                23
  13.324981213 = 14.307589632   vmlinuz                                        3
  13.214278698 = 14.188723712   vmlinuz.old                                   67

=========================== sda2/boot/grub/grub.cfg: ===========================

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
set root='(/dev/sda,msdos2)'
search --no-floppy --fs-uuid --set=root 47f17943-077c-4d64-b573-360bd8ba2c06
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos2)'
search --no-floppy --fs-uuid --set=root 47f17943-077c-4d64-b573-360bd8ba2c06
set locale_dir=($root)/boot/grub/locale
set lang=en_GB
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
if [ ${recordfail} != 1 ]; then
  if [ -e ${prefix}/gfxblacklist.txt ]; then
    if hwmatch ${prefix}/gfxblacklist.txt 3; then
      if [ ${match} = 0 ]; then
        set linux_gfx_mode=keep
      else
        set linux_gfx_mode=text
      fi
    else
      set linux_gfx_mode=text
    fi
  else
    set linux_gfx_mode=keep
  fi
else
  set linux_gfx_mode=text
fi
export linux_gfx_mode
if [ "$linux_gfx_mode" != "text" ]; then load_video; fi
menuentry 'Ubuntu, with Linux 2.6.38-11-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos2)'
	search --no-floppy --fs-uuid --set=root 47f17943-077c-4d64-b573-360bd8ba2c06
	linux	/boot/vmlinuz-2.6.38-11-generic-pae root=UUID=47f17943-077c-4d64-b573-360bd8ba2c06 ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-2.6.38-11-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.38-11-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos2)'
	search --no-floppy --fs-uuid --set=root 47f17943-077c-4d64-b573-360bd8ba2c06
	echo	'Loading Linux 2.6.38-11-generic-pae ...'
	linux	/boot/vmlinuz-2.6.38-11-generic-pae root=UUID=47f17943-077c-4d64-b573-360bd8ba2c06 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.38-11-generic-pae
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, with Linux 2.6.38-10-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos2)'
	search --no-floppy --fs-uuid --set=root 47f17943-077c-4d64-b573-360bd8ba2c06
	linux	/boot/vmlinuz-2.6.38-10-generic-pae root=UUID=47f17943-077c-4d64-b573-360bd8ba2c06 ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-2.6.38-10-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.38-10-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos2)'
	search --no-floppy --fs-uuid --set=root 47f17943-077c-4d64-b573-360bd8ba2c06
	echo	'Loading Linux 2.6.38-10-generic-pae ...'
	linux	/boot/vmlinuz-2.6.38-10-generic-pae root=UUID=47f17943-077c-4d64-b573-360bd8ba2c06 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.38-10-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos2)'
	search --no-floppy --fs-uuid --set=root 47f17943-077c-4d64-b573-360bd8ba2c06
	linux	/boot/vmlinuz-2.6.38-8-generic-pae root=UUID=47f17943-077c-4d64-b573-360bd8ba2c06 ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-2.6.38-8-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos2)'
	search --no-floppy --fs-uuid --set=root 47f17943-077c-4d64-b573-360bd8ba2c06
	echo	'Loading Linux 2.6.38-8-generic-pae ...'
	linux	/boot/vmlinuz-2.6.38-8-generic-pae root=UUID=47f17943-077c-4d64-b573-360bd8ba2c06 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.38-8-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.35-28-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos2)'
	search --no-floppy --fs-uuid --set=root 47f17943-077c-4d64-b573-360bd8ba2c06
	linux	/boot/vmlinuz-2.6.35-28-generic-pae root=UUID=47f17943-077c-4d64-b573-360bd8ba2c06 ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-2.6.35-28-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.35-28-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos2)'
	search --no-floppy --fs-uuid --set=root 47f17943-077c-4d64-b573-360bd8ba2c06
	echo	'Loading Linux 2.6.35-28-generic-pae ...'
	linux	/boot/vmlinuz-2.6.35-28-generic-pae root=UUID=47f17943-077c-4d64-b573-360bd8ba2c06 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-28-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.35-24-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos2)'
	search --no-floppy --fs-uuid --set=root 47f17943-077c-4d64-b573-360bd8ba2c06
	linux	/boot/vmlinuz-2.6.35-24-generic-pae root=UUID=47f17943-077c-4d64-b573-360bd8ba2c06 ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-2.6.35-24-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.35-24-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos2)'
	search --no-floppy --fs-uuid --set=root 47f17943-077c-4d64-b573-360bd8ba2c06
	echo	'Loading Linux 2.6.35-24-generic-pae ...'
	linux	/boot/vmlinuz-2.6.35-24-generic-pae root=UUID=47f17943-077c-4d64-b573-360bd8ba2c06 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-24-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.35-23-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos2)'
	search --no-floppy --fs-uuid --set=root 47f17943-077c-4d64-b573-360bd8ba2c06
	linux	/boot/vmlinuz-2.6.35-23-generic-pae root=UUID=47f17943-077c-4d64-b573-360bd8ba2c06 ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-2.6.35-23-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.35-23-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos2)'
	search --no-floppy --fs-uuid --set=root 47f17943-077c-4d64-b573-360bd8ba2c06
	echo	'Loading Linux 2.6.35-23-generic-pae ...'
	linux	/boot/vmlinuz-2.6.35-23-generic-pae root=UUID=47f17943-077c-4d64-b573-360bd8ba2c06 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-23-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos2)'
	search --no-floppy --fs-uuid --set=root 47f17943-077c-4d64-b573-360bd8ba2c06
	linux	/boot/vmlinuz-2.6.35-22-generic-pae root=UUID=47f17943-077c-4d64-b573-360bd8ba2c06 ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-2.6.35-22-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos2)'
	search --no-floppy --fs-uuid --set=root 47f17943-077c-4d64-b573-360bd8ba2c06
	echo	'Loading Linux 2.6.35-22-generic-pae ...'
	linux	/boot/vmlinuz-2.6.35-22-generic-pae root=UUID=47f17943-077c-4d64-b573-360bd8ba2c06 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-22-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.32-25-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos2)'
	search --no-floppy --fs-uuid --set=root 47f17943-077c-4d64-b573-360bd8ba2c06
	linux	/boot/vmlinuz-2.6.32-25-generic-pae root=UUID=47f17943-077c-4d64-b573-360bd8ba2c06 ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-2.6.32-25-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.32-25-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos2)'
	search --no-floppy --fs-uuid --set=root 47f17943-077c-4d64-b573-360bd8ba2c06
	echo	'Loading Linux 2.6.32-25-generic-pae ...'
	linux	/boot/vmlinuz-2.6.32-25-generic-pae root=UUID=47f17943-077c-4d64-b573-360bd8ba2c06 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-25-generic-pae
}
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos2)'
	search --no-floppy --fs-uuid --set=root 47f17943-077c-4d64-b573-360bd8ba2c06
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos2)'
	search --no-floppy --fs-uuid --set=root 47f17943-077c-4d64-b573-360bd8ba2c06
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Ubuntu, with Linux 3.0.0-13-generic (on /dev/sda1)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root 73cf4420-f9de-495c-ac7d-a6278e0ee811
	linux /boot/vmlinuz-3.0.0-13-generic root=UUID=73cf4420-f9de-495c-ac7d-a6278e0ee811 ro quiet splash vt.handoff=7
	initrd /boot/initrd.img-3.0.0-13-generic
}
menuentry "Ubuntu, with Linux 3.0.0-13-generic (recovery mode) (on /dev/sda1)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root 73cf4420-f9de-495c-ac7d-a6278e0ee811
	linux /boot/vmlinuz-3.0.0-13-generic root=UUID=73cf4420-f9de-495c-ac7d-a6278e0ee811 ro recovery nomodeset
	initrd /boot/initrd.img-3.0.0-13-generic
}
menuentry "Ubuntu, with Linux 3.0.0-12-generic (on /dev/sda1)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root 73cf4420-f9de-495c-ac7d-a6278e0ee811
	linux /boot/vmlinuz-3.0.0-12-generic root=UUID=73cf4420-f9de-495c-ac7d-a6278e0ee811 ro quiet splash vt.handoff=7
	initrd /boot/initrd.img-3.0.0-12-generic
}
menuentry "Ubuntu, with Linux 3.0.0-12-generic (recovery mode) (on /dev/sda1)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root 73cf4420-f9de-495c-ac7d-a6278e0ee811
	linux /boot/vmlinuz-3.0.0-12-generic root=UUID=73cf4420-f9de-495c-ac7d-a6278e0ee811 ro recovery nomodeset
	initrd /boot/initrd.img-3.0.0-12-generic
}
menuentry "Ubuntu, with Linux 3.0.0-11-generic (on /dev/sda1)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root 73cf4420-f9de-495c-ac7d-a6278e0ee811
	linux /boot/vmlinuz-3.0.0-11-generic root=UUID=73cf4420-f9de-495c-ac7d-a6278e0ee811 ro quiet splash vt.handoff=7
	initrd /boot/initrd.img-3.0.0-11-generic
}
menuentry "Ubuntu, with Linux 3.0.0-11-generic (recovery mode) (on /dev/sda1)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root 73cf4420-f9de-495c-ac7d-a6278e0ee811
	linux /boot/vmlinuz-3.0.0-11-generic root=UUID=73cf4420-f9de-495c-ac7d-a6278e0ee811 ro recovery nomodeset
	initrd /boot/initrd.img-3.0.0-11-generic
}
menuentry "Ubuntu, with Linux 3.0.0-10-generic (on /dev/sda1)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root 73cf4420-f9de-495c-ac7d-a6278e0ee811
	linux /boot/vmlinuz-3.0.0-10-generic root=UUID=73cf4420-f9de-495c-ac7d-a6278e0ee811 ro quiet splash vt.handoff=7
	initrd /boot/initrd.img-3.0.0-10-generic
}
menuentry "Ubuntu, with Linux 3.0.0-10-generic (recovery mode) (on /dev/sda1)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root 73cf4420-f9de-495c-ac7d-a6278e0ee811
	linux /boot/vmlinuz-3.0.0-10-generic root=UUID=73cf4420-f9de-495c-ac7d-a6278e0ee811 ro recovery nomodeset
	initrd /boot/initrd.img-3.0.0-10-generic
}
menuentry "Ubuntu, with Linux 3.0.0-9-generic (on /dev/sda1)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root 73cf4420-f9de-495c-ac7d-a6278e0ee811
	linux /boot/vmlinuz-3.0.0-9-generic root=UUID=73cf4420-f9de-495c-ac7d-a6278e0ee811 ro quiet splash vt.handoff=7
	initrd /boot/initrd.img-3.0.0-9-generic
}
menuentry "Ubuntu, with Linux 3.0.0-9-generic (recovery mode) (on /dev/sda1)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root 73cf4420-f9de-495c-ac7d-a6278e0ee811
	linux /boot/vmlinuz-3.0.0-9-generic root=UUID=73cf4420-f9de-495c-ac7d-a6278e0ee811 ro recovery nomodeset
	initrd /boot/initrd.img-3.0.0-9-generic
}
menuentry "Ubuntu, with Linux 3.0.0-8-generic (on /dev/sda1)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root 73cf4420-f9de-495c-ac7d-a6278e0ee811
	linux /boot/vmlinuz-3.0.0-8-generic root=UUID=73cf4420-f9de-495c-ac7d-a6278e0ee811 ro quiet splash vt.handoff=7
	initrd /boot/initrd.img-3.0.0-8-generic
}
menuentry "Ubuntu, with Linux 3.0.0-8-generic (recovery mode) (on /dev/sda1)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root 73cf4420-f9de-495c-ac7d-a6278e0ee811
	linux /boot/vmlinuz-3.0.0-8-generic root=UUID=73cf4420-f9de-495c-ac7d-a6278e0ee811 ro recovery nomodeset
	initrd /boot/initrd.img-3.0.0-8-generic
}
menuentry "Ubuntu, with Linux 3.0.0-7-generic (on /dev/sda1)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root 73cf4420-f9de-495c-ac7d-a6278e0ee811
	linux /boot/vmlinuz-3.0.0-7-generic root=UUID=73cf4420-f9de-495c-ac7d-a6278e0ee811 ro quiet splash vt.handoff=7
	initrd /boot/initrd.img-3.0.0-7-generic
}
menuentry "Ubuntu, with Linux 3.0.0-7-generic (recovery mode) (on /dev/sda1)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root 73cf4420-f9de-495c-ac7d-a6278e0ee811
	linux /boot/vmlinuz-3.0.0-7-generic root=UUID=73cf4420-f9de-495c-ac7d-a6278e0ee811 ro recovery nomodeset
	initrd /boot/initrd.img-3.0.0-7-generic
}
menuentry "Ubuntu, with Linux 3.0-3-generic (on /dev/sda1)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root 73cf4420-f9de-495c-ac7d-a6278e0ee811
	linux /boot/vmlinuz-3.0-3-generic root=UUID=73cf4420-f9de-495c-ac7d-a6278e0ee811 ro quiet splash vt.handoff=7
	initrd /boot/initrd.img-3.0-3-generic
}
menuentry "Ubuntu, with Linux 3.0-3-generic (recovery mode) (on /dev/sda1)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root 73cf4420-f9de-495c-ac7d-a6278e0ee811
	linux /boot/vmlinuz-3.0-3-generic root=UUID=73cf4420-f9de-495c-ac7d-a6278e0ee811 ro recovery nomodeset
	initrd /boot/initrd.img-3.0-3-generic
}
menuentry "Ubuntu, with Linux 3.0-1-generic (on /dev/sda1)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root 73cf4420-f9de-495c-ac7d-a6278e0ee811
	linux /boot/vmlinuz-3.0-1-generic root=UUID=73cf4420-f9de-495c-ac7d-a6278e0ee811 ro quiet splash vt.handoff=7
	initrd /boot/initrd.img-3.0-1-generic
}
menuentry "Ubuntu, with Linux 3.0-1-generic (recovery mode) (on /dev/sda1)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root 73cf4420-f9de-495c-ac7d-a6278e0ee811
	linux /boot/vmlinuz-3.0-1-generic root=UUID=73cf4420-f9de-495c-ac7d-a6278e0ee811 ro recovery nomodeset
	initrd /boot/initrd.img-3.0-1-generic
}
menuentry "Ubuntu, with Linux 3.0-0-generic (on /dev/sda1)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root 73cf4420-f9de-495c-ac7d-a6278e0ee811
	linux /boot/vmlinuz-3.0-0-generic root=UUID=73cf4420-f9de-495c-ac7d-a6278e0ee811 ro quiet splash vt.handoff=7
	initrd /boot/initrd.img-3.0-0-generic
}
menuentry "Ubuntu, with Linux 3.0-0-generic (recovery mode) (on /dev/sda1)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root 73cf4420-f9de-495c-ac7d-a6278e0ee811
	linux /boot/vmlinuz-3.0-0-generic root=UUID=73cf4420-f9de-495c-ac7d-a6278e0ee811 ro recovery nomodeset
	initrd /boot/initrd.img-3.0-0-generic
}
menuentry "Ubuntu, with Linux 2.6.39-3-generic (on /dev/sda1)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root 73cf4420-f9de-495c-ac7d-a6278e0ee811
	linux /boot/vmlinuz-2.6.39-3-generic root=UUID=73cf4420-f9de-495c-ac7d-a6278e0ee811 ro quiet splash vt.handoff=7
	initrd /boot/initrd.img-2.6.39-3-generic
}
menuentry "Ubuntu, with Linux 2.6.39-3-generic (recovery mode) (on /dev/sda1)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root 73cf4420-f9de-495c-ac7d-a6278e0ee811
	linux /boot/vmlinuz-2.6.39-3-generic root=UUID=73cf4420-f9de-495c-ac7d-a6278e0ee811 ro recovery nomodeset
	initrd /boot/initrd.img-2.6.39-3-generic
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
--------------------------------------------------------------------------------

=============================== sda2/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda2 during installation
UUID=47f17943-077c-4d64-b573-360bd8ba2c06 /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda4 during installation
UUID=6e503435-c52b-44d5-ac46-e88fc896a79e /home           ext4    defaults        0       2
# swap was on /dev/sda6 during installation
UUID=8635eaa6-7eee-4f77-aa06-9b52db10a9a6 none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda2: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

  91.706844330 = 98.469474304   boot/grub/core.img                             1
  92.346961975 = 99.156795392   boot/grub/grub.cfg                             1
  90.531558990 = 97.207521280   boot/initrd.img-2.6.32-25-generic-pae          2
  88.484683990 = 95.009705984   boot/initrd.img-2.6.35-22-generic-pae          2
 100.002460480 = 107.376824320  boot/initrd.img-2.6.35-23-generic-pae          2
  90.986873627 = 97.696411648   boot/initrd.img-2.6.35-24-generic-pae          1
 100.840873718 = 108.277063680  boot/initrd.img-2.6.35-28-generic-pae          2
  90.317878723 = 96.978083840   boot/initrd.img-2.6.38-10-generic-pae          3
  92.754455566 = 99.594338304   boot/initrd.img-2.6.38-11-generic-pae          1
  87.693695068 = 94.160388096   boot/initrd.img-2.6.38-8-generic-pae          58
  91.723533630 = 98.487394304   boot/vmlinuz-2.6.32-25-generic-pae             4
  91.714031219 = 98.477191168   boot/vmlinuz-2.6.35-22-generic-pae             2
  91.751041412 = 98.516930560   boot/vmlinuz-2.6.35-23-generic-pae             4
  91.762229919 = 98.528944128   boot/vmlinuz-2.6.35-24-generic-pae            91
  91.776828766 = 98.544619520   boot/vmlinuz-2.6.35-28-generic-pae            108
  88.547615051 = 95.077277696   boot/vmlinuz-2.6.38-10-generic-pae             1
  92.449958801 = 99.267387392   boot/vmlinuz-2.6.38-11-generic-pae             2
  88.783390045 = 95.330439168   boot/vmlinuz-2.6.38-8-generic-pae              1
  92.754455566 = 99.594338304   initrd.img                                     1
  90.317878723 = 96.978083840   initrd.img.old                                 3
  92.449958801 = 99.267387392   vmlinuz                                        2
  88.547615051 = 95.077277696   vmlinuz.old                                    1

=========================== sda5/boot/grub/grub.cfg: ===========================

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
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set=root 1c44dac4-0301-4df7-815d-10ba0c368167
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  insmod part_msdos
  insmod ext2
  set root='(hd0,msdos5)'
  search --no-floppy --fs-uuid --set=root 1c44dac4-0301-4df7-815d-10ba0c368167
  set locale_dir=($root)/boot/grub/locale
  set lang=en_GB
  insmod gettext
fi
terminal_output gfxterm
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
if [ ${recordfail} != 1 ]; then
  if [ -e ${prefix}/gfxblacklist.txt ]; then
    if hwmatch ${prefix}/gfxblacklist.txt 3; then
      if [ ${match} = 0 ]; then
        set linux_gfx_mode=keep
      else
        set linux_gfx_mode=text
      fi
    else
      set linux_gfx_mode=text
    fi
  else
    set linux_gfx_mode=keep
  fi
else
  set linux_gfx_mode=text
fi
export linux_gfx_mode
if [ "$linux_gfx_mode" != "text" ]; then load_video; fi
menuentry 'Ubuntu, with Linux 3.2.0-2-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set=root 1c44dac4-0301-4df7-815d-10ba0c368167
	linux	/boot/vmlinuz-3.2.0-2-generic root=UUID=1c44dac4-0301-4df7-815d-10ba0c368167 ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-3.2.0-2-generic
}
menuentry 'Ubuntu, with Linux 3.2.0-2-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set=root 1c44dac4-0301-4df7-815d-10ba0c368167
	echo	'Loading Linux 3.2.0-2-generic ...'
	linux	/boot/vmlinuz-3.2.0-2-generic root=UUID=1c44dac4-0301-4df7-815d-10ba0c368167 ro recovery nomodeset 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-3.2.0-2-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set=root 1c44dac4-0301-4df7-815d-10ba0c368167
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set=root 1c44dac4-0301-4df7-815d-10ba0c368167
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Ubuntu, with Linux 3.0.0-13-generic (on /dev/sda1)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set=root 73cf4420-f9de-495c-ac7d-a6278e0ee811
	linux /boot/vmlinuz-3.0.0-13-generic root=UUID=73cf4420-f9de-495c-ac7d-a6278e0ee811 ro quiet splash vt.handoff=7
	initrd /boot/initrd.img-3.0.0-13-generic
}
menuentry "Ubuntu, with Linux 3.0.0-13-generic (recovery mode) (on /dev/sda1)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set=root 73cf4420-f9de-495c-ac7d-a6278e0ee811
	linux /boot/vmlinuz-3.0.0-13-generic root=UUID=73cf4420-f9de-495c-ac7d-a6278e0ee811 ro recovery nomodeset
	initrd /boot/initrd.img-3.0.0-13-generic
}
menuentry "Ubuntu, with Linux 3.0.0-12-generic (on /dev/sda1)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set=root 73cf4420-f9de-495c-ac7d-a6278e0ee811
	linux /boot/vmlinuz-3.0.0-12-generic root=UUID=73cf4420-f9de-495c-ac7d-a6278e0ee811 ro quiet splash vt.handoff=7
	initrd /boot/initrd.img-3.0.0-12-generic
}
menuentry "Ubuntu, with Linux 3.0.0-12-generic (recovery mode) (on /dev/sda1)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set=root 73cf4420-f9de-495c-ac7d-a6278e0ee811
	linux /boot/vmlinuz-3.0.0-12-generic root=UUID=73cf4420-f9de-495c-ac7d-a6278e0ee811 ro recovery nomodeset
	initrd /boot/initrd.img-3.0.0-12-generic
}
menuentry "Ubuntu, with Linux 3.0.0-11-generic (on /dev/sda1)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set=root 73cf4420-f9de-495c-ac7d-a6278e0ee811
	linux /boot/vmlinuz-3.0.0-11-generic root=UUID=73cf4420-f9de-495c-ac7d-a6278e0ee811 ro quiet splash vt.handoff=7
	initrd /boot/initrd.img-3.0.0-11-generic
}
menuentry "Ubuntu, with Linux 3.0.0-11-generic (recovery mode) (on /dev/sda1)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set=root 73cf4420-f9de-495c-ac7d-a6278e0ee811
	linux /boot/vmlinuz-3.0.0-11-generic root=UUID=73cf4420-f9de-495c-ac7d-a6278e0ee811 ro recovery nomodeset
	initrd /boot/initrd.img-3.0.0-11-generic
}
menuentry "Ubuntu, with Linux 3.0.0-10-generic (on /dev/sda1)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set=root 73cf4420-f9de-495c-ac7d-a6278e0ee811
	linux /boot/vmlinuz-3.0.0-10-generic root=UUID=73cf4420-f9de-495c-ac7d-a6278e0ee811 ro quiet splash vt.handoff=7
	initrd /boot/initrd.img-3.0.0-10-generic
}
menuentry "Ubuntu, with Linux 3.0.0-10-generic (recovery mode) (on /dev/sda1)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set=root 73cf4420-f9de-495c-ac7d-a6278e0ee811
	linux /boot/vmlinuz-3.0.0-10-generic root=UUID=73cf4420-f9de-495c-ac7d-a6278e0ee811 ro recovery nomodeset
	initrd /boot/initrd.img-3.0.0-10-generic
}
menuentry "Ubuntu, with Linux 3.0.0-9-generic (on /dev/sda1)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set=root 73cf4420-f9de-495c-ac7d-a6278e0ee811
	linux /boot/vmlinuz-3.0.0-9-generic root=UUID=73cf4420-f9de-495c-ac7d-a6278e0ee811 ro quiet splash vt.handoff=7
	initrd /boot/initrd.img-3.0.0-9-generic
}
menuentry "Ubuntu, with Linux 3.0.0-9-generic (recovery mode) (on /dev/sda1)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set=root 73cf4420-f9de-495c-ac7d-a6278e0ee811
	linux /boot/vmlinuz-3.0.0-9-generic root=UUID=73cf4420-f9de-495c-ac7d-a6278e0ee811 ro recovery nomodeset
	initrd /boot/initrd.img-3.0.0-9-generic
}
menuentry "Ubuntu, with Linux 3.0.0-8-generic (on /dev/sda1)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set=root 73cf4420-f9de-495c-ac7d-a6278e0ee811
	linux /boot/vmlinuz-3.0.0-8-generic root=UUID=73cf4420-f9de-495c-ac7d-a6278e0ee811 ro quiet splash vt.handoff=7
	initrd /boot/initrd.img-3.0.0-8-generic
}
menuentry "Ubuntu, with Linux 3.0.0-8-generic (recovery mode) (on /dev/sda1)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set=root 73cf4420-f9de-495c-ac7d-a6278e0ee811
	linux /boot/vmlinuz-3.0.0-8-generic root=UUID=73cf4420-f9de-495c-ac7d-a6278e0ee811 ro recovery nomodeset
	initrd /boot/initrd.img-3.0.0-8-generic
}
menuentry "Ubuntu, with Linux 3.0.0-7-generic (on /dev/sda1)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set=root 73cf4420-f9de-495c-ac7d-a6278e0ee811
	linux /boot/vmlinuz-3.0.0-7-generic root=UUID=73cf4420-f9de-495c-ac7d-a6278e0ee811 ro quiet splash vt.handoff=7
	initrd /boot/initrd.img-3.0.0-7-generic
}
menuentry "Ubuntu, with Linux 3.0.0-7-generic (recovery mode) (on /dev/sda1)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set=root 73cf4420-f9de-495c-ac7d-a6278e0ee811
	linux /boot/vmlinuz-3.0.0-7-generic root=UUID=73cf4420-f9de-495c-ac7d-a6278e0ee811 ro recovery nomodeset
	initrd /boot/initrd.img-3.0.0-7-generic
}
menuentry "Ubuntu, with Linux 3.0-3-generic (on /dev/sda1)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set=root 73cf4420-f9de-495c-ac7d-a6278e0ee811
	linux /boot/vmlinuz-3.0-3-generic root=UUID=73cf4420-f9de-495c-ac7d-a6278e0ee811 ro quiet splash vt.handoff=7
	initrd /boot/initrd.img-3.0-3-generic
}
menuentry "Ubuntu, with Linux 3.0-3-generic (recovery mode) (on /dev/sda1)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set=root 73cf4420-f9de-495c-ac7d-a6278e0ee811
	linux /boot/vmlinuz-3.0-3-generic root=UUID=73cf4420-f9de-495c-ac7d-a6278e0ee811 ro recovery nomodeset
	initrd /boot/initrd.img-3.0-3-generic
}
menuentry "Ubuntu, with Linux 3.0-1-generic (on /dev/sda1)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set=root 73cf4420-f9de-495c-ac7d-a6278e0ee811
	linux /boot/vmlinuz-3.0-1-generic root=UUID=73cf4420-f9de-495c-ac7d-a6278e0ee811 ro quiet splash vt.handoff=7
	initrd /boot/initrd.img-3.0-1-generic
}
menuentry "Ubuntu, with Linux 3.0-1-generic (recovery mode) (on /dev/sda1)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set=root 73cf4420-f9de-495c-ac7d-a6278e0ee811
	linux /boot/vmlinuz-3.0-1-generic root=UUID=73cf4420-f9de-495c-ac7d-a6278e0ee811 ro recovery nomodeset
	initrd /boot/initrd.img-3.0-1-generic
}
menuentry "Ubuntu, with Linux 3.0-0-generic (on /dev/sda1)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set=root 73cf4420-f9de-495c-ac7d-a6278e0ee811
	linux /boot/vmlinuz-3.0-0-generic root=UUID=73cf4420-f9de-495c-ac7d-a6278e0ee811 ro quiet splash vt.handoff=7
	initrd /boot/initrd.img-3.0-0-generic
}
menuentry "Ubuntu, with Linux 3.0-0-generic (recovery mode) (on /dev/sda1)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set=root 73cf4420-f9de-495c-ac7d-a6278e0ee811
	linux /boot/vmlinuz-3.0-0-generic root=UUID=73cf4420-f9de-495c-ac7d-a6278e0ee811 ro recovery nomodeset
	initrd /boot/initrd.img-3.0-0-generic
}
menuentry "Ubuntu, with Linux 2.6.39-3-generic (on /dev/sda1)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set=root 73cf4420-f9de-495c-ac7d-a6278e0ee811
	linux /boot/vmlinuz-2.6.39-3-generic root=UUID=73cf4420-f9de-495c-ac7d-a6278e0ee811 ro quiet splash vt.handoff=7
	initrd /boot/initrd.img-2.6.39-3-generic
}
menuentry "Ubuntu, with Linux 2.6.39-3-generic (recovery mode) (on /dev/sda1)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set=root 73cf4420-f9de-495c-ac7d-a6278e0ee811
	linux /boot/vmlinuz-2.6.39-3-generic root=UUID=73cf4420-f9de-495c-ac7d-a6278e0ee811 ro recovery nomodeset
	initrd /boot/initrd.img-2.6.39-3-generic
}
menuentry "Ubuntu, with Linux 2.6.38-11-generic-pae (on /dev/sda2)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set=root 47f17943-077c-4d64-b573-360bd8ba2c06
	linux /boot/vmlinuz-2.6.38-11-generic-pae root=UUID=47f17943-077c-4d64-b573-360bd8ba2c06 ro quiet splash vt.handoff=7
	initrd /boot/initrd.img-2.6.38-11-generic-pae
}
menuentry "Ubuntu, with Linux 2.6.38-11-generic-pae (recovery mode) (on /dev/sda2)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set=root 47f17943-077c-4d64-b573-360bd8ba2c06
	linux /boot/vmlinuz-2.6.38-11-generic-pae root=UUID=47f17943-077c-4d64-b573-360bd8ba2c06 ro single
	initrd /boot/initrd.img-2.6.38-11-generic-pae
}
menuentry "Ubuntu, with Linux 2.6.38-10-generic-pae (on /dev/sda2)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set=root 47f17943-077c-4d64-b573-360bd8ba2c06
	linux /boot/vmlinuz-2.6.38-10-generic-pae root=UUID=47f17943-077c-4d64-b573-360bd8ba2c06 ro quiet splash vt.handoff=7
	initrd /boot/initrd.img-2.6.38-10-generic-pae
}
menuentry "Ubuntu, with Linux 2.6.38-10-generic-pae (recovery mode) (on /dev/sda2)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set=root 47f17943-077c-4d64-b573-360bd8ba2c06
	linux /boot/vmlinuz-2.6.38-10-generic-pae root=UUID=47f17943-077c-4d64-b573-360bd8ba2c06 ro single
	initrd /boot/initrd.img-2.6.38-10-generic-pae
}
menuentry "Ubuntu, with Linux 2.6.38-8-generic-pae (on /dev/sda2)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set=root 47f17943-077c-4d64-b573-360bd8ba2c06
	linux /boot/vmlinuz-2.6.38-8-generic-pae root=UUID=47f17943-077c-4d64-b573-360bd8ba2c06 ro quiet splash vt.handoff=7
	initrd /boot/initrd.img-2.6.38-8-generic-pae
}
menuentry "Ubuntu, with Linux 2.6.38-8-generic-pae (recovery mode) (on /dev/sda2)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set=root 47f17943-077c-4d64-b573-360bd8ba2c06
	linux /boot/vmlinuz-2.6.38-8-generic-pae root=UUID=47f17943-077c-4d64-b573-360bd8ba2c06 ro single
	initrd /boot/initrd.img-2.6.38-8-generic-pae
}
menuentry "Ubuntu, with Linux 2.6.35-28-generic-pae (on /dev/sda2)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set=root 47f17943-077c-4d64-b573-360bd8ba2c06
	linux /boot/vmlinuz-2.6.35-28-generic-pae root=UUID=47f17943-077c-4d64-b573-360bd8ba2c06 ro quiet splash vt.handoff=7
	initrd /boot/initrd.img-2.6.35-28-generic-pae
}
menuentry "Ubuntu, with Linux 2.6.35-28-generic-pae (recovery mode) (on /dev/sda2)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set=root 47f17943-077c-4d64-b573-360bd8ba2c06
	linux /boot/vmlinuz-2.6.35-28-generic-pae root=UUID=47f17943-077c-4d64-b573-360bd8ba2c06 ro single
	initrd /boot/initrd.img-2.6.35-28-generic-pae
}
menuentry "Ubuntu, with Linux 2.6.35-24-generic-pae (on /dev/sda2)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set=root 47f17943-077c-4d64-b573-360bd8ba2c06
	linux /boot/vmlinuz-2.6.35-24-generic-pae root=UUID=47f17943-077c-4d64-b573-360bd8ba2c06 ro quiet splash vt.handoff=7
	initrd /boot/initrd.img-2.6.35-24-generic-pae
}
menuentry "Ubuntu, with Linux 2.6.35-24-generic-pae (recovery mode) (on /dev/sda2)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set=root 47f17943-077c-4d64-b573-360bd8ba2c06
	linux /boot/vmlinuz-2.6.35-24-generic-pae root=UUID=47f17943-077c-4d64-b573-360bd8ba2c06 ro single
	initrd /boot/initrd.img-2.6.35-24-generic-pae
}
menuentry "Ubuntu, with Linux 2.6.35-23-generic-pae (on /dev/sda2)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set=root 47f17943-077c-4d64-b573-360bd8ba2c06
	linux /boot/vmlinuz-2.6.35-23-generic-pae root=UUID=47f17943-077c-4d64-b573-360bd8ba2c06 ro quiet splash vt.handoff=7
	initrd /boot/initrd.img-2.6.35-23-generic-pae
}
menuentry "Ubuntu, with Linux 2.6.35-23-generic-pae (recovery mode) (on /dev/sda2)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set=root 47f17943-077c-4d64-b573-360bd8ba2c06
	linux /boot/vmlinuz-2.6.35-23-generic-pae root=UUID=47f17943-077c-4d64-b573-360bd8ba2c06 ro single
	initrd /boot/initrd.img-2.6.35-23-generic-pae
}
menuentry "Ubuntu, with Linux 2.6.35-22-generic-pae (on /dev/sda2)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set=root 47f17943-077c-4d64-b573-360bd8ba2c06
	linux /boot/vmlinuz-2.6.35-22-generic-pae root=UUID=47f17943-077c-4d64-b573-360bd8ba2c06 ro quiet splash vt.handoff=7
	initrd /boot/initrd.img-2.6.35-22-generic-pae
}
menuentry "Ubuntu, with Linux 2.6.35-22-generic-pae (recovery mode) (on /dev/sda2)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set=root 47f17943-077c-4d64-b573-360bd8ba2c06
	linux /boot/vmlinuz-2.6.35-22-generic-pae root=UUID=47f17943-077c-4d64-b573-360bd8ba2c06 ro single
	initrd /boot/initrd.img-2.6.35-22-generic-pae
}
menuentry "Ubuntu, with Linux 2.6.32-25-generic-pae (on /dev/sda2)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set=root 47f17943-077c-4d64-b573-360bd8ba2c06
	linux /boot/vmlinuz-2.6.32-25-generic-pae root=UUID=47f17943-077c-4d64-b573-360bd8ba2c06 ro quiet splash vt.handoff=7
	initrd /boot/initrd.img-2.6.32-25-generic-pae
}
menuentry "Ubuntu, with Linux 2.6.32-25-generic-pae (recovery mode) (on /dev/sda2)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set=root 47f17943-077c-4d64-b573-360bd8ba2c06
	linux /boot/vmlinuz-2.6.32-25-generic-pae root=UUID=47f17943-077c-4d64-b573-360bd8ba2c06 ro single
	initrd /boot/initrd.img-2.6.32-25-generic-pae
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
--------------------------------------------------------------------------------

=============================== sda5/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=1c44dac4-0301-4df7-815d-10ba0c368167 /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda7 during installation
UUID=50e0fd68-4db9-487b-992e-d1e75822dfd7 /home           ext4    defaults        0       2
# swap was on /dev/sda6 during installation
UUID=ec51e594-b3c9-491d-b096-ac879bc02770 none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda5: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 113.912548065 = 122.312667136  boot/grub/core.img                             1
 111.825393677 = 120.071602176  boot/grub/grub.cfg                             1
 110.430011749 = 118.573322240  boot/initrd.img-3.2.0-2-generic                2
 107.692699432 = 115.634155520  boot/vmlinuz-3.2.0-2-generic                   1
 110.430011749 = 118.573322240  initrd.img                                     2
 107.692699432 = 115.634155520  vmlinuz                                        1

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda3

00000000  56 bf 51 29 b1 70 c8 59  b1 ba e7 2b bd 13 de f4  |V.Q).p.Y...+....|
00000010  fe ed e7 64 6e db 1a cb  5c 99 99 4d 36 99 a3 f6  |...dn...\..M6...|
00000020  13 27 45 3f 19 db ab 57  56 24 42 d4 1c da 47 cc  |.'E?...WV$B...G.|
00000030  a6 77 2b 6a 55 88 a6 3c  65 76 db 4c 86 03 84 ab  |.w+jU..<ev.L....|
00000040  46 93 07 22 0a f0 f1 2f  29 9f c1 43 b5 d1 33 1d  |F..".../)..C..3.|
00000050  db 2e 6e 3c 88 d0 4f ba  c7 7d 1f a0 33 82 dc 89  |..n<..O..}..3...|
00000060  15 d5 5a 45 00 75 3f 89  16 e5 46 29 10 e5 5e e5  |..ZE.u?...F)..^.|
00000070  15 0a 94 25 13 a7 a4 3a  1f 58 b3 20 0a a6 bc 7d  |...%...:.X. ...}|
00000080  cb 0b a6 a4 6f 75 14 4d  1a 0a cd 5c 84 90 11 e8  |....ou.M...\....|
00000090  38 c2 10 10 7f 78 4c fd  5a ef 88 3f 93 42 7a d8  |8....xL.Z..?.Bz.|
000000a0  58 bd ff 15 75 43 26 0e  a9 ee 63 e0 fd 65 29 c4  |X...uC&...c..e).|
000000b0  6d ef 89 67 be 3a 7f 0c  1b 51 0e 9e 29 51 56 f8  |m..g.:...Q..)QV.|
000000c0  c2 be a4 92 a4 13 44 81  bd 74 a7 72 7d 12 2c 4f  |......D..t.r}.,O|
000000d0  80 3f e7 98 0e 40 32 8f  2f be 0f 0a 93 d1 e1 08  |.?...@2./.......|
000000e0  51 91 c8 87 45 91 f2 50  3e 3f e6 60 86 d3 0e 37  |Q...E..P>?.`...7|
000000f0  06 2c be ba b5 72 d3 12  c1 7f 57 1f ab 80 8f ca  |.,...r....W.....|
00000100  27 b9 5b 42 e6 2d 36 c9  48 bd e5 a0 34 bd df da  |'.[B.-6.H...4...|
00000110  1c 52 a4 53 30 23 08 7d  58 00 a7 34 bf fe 6b 4b  |.R.S0#.}X..4..kK|
00000120  ee 24 4f c6 53 ac 42 e9  1a 52 3b ad 0b 99 a3 a2  |.$O.S.B..R;.....|
00000130  d4 26 e0 d5 76 26 ce e8  5e 67 ae 09 fd 64 bc d8  |.&..v&..^g...d..|
00000140  47 9b e9 90 05 65 10 c4  a2 c8 f0 74 2d 37 93 25  |G....e.....t-7.%|
00000150  a6 9b da c2 54 ba 3b 70  4e 21 82 15 22 21 02 93  |....T.;pN!.."!..|
00000160  d5 ce 78 ad 8c 63 a8 2f  06 9c 8f 8f 2a 62 f8 43  |..x..c./....*b.C|
00000170  dd cf 9e c5 5b 30 6f 5d  95 2d 36 9e 50 82 c2 01  |....[0o].-6.P...|
00000180  0e 57 0e b7 ed c7 52 af  22 57 86 10 b3 c7 17 8f  |.W....R."W......|
00000190  70 90 55 a8 d8 7c bd bd  95 7c 6a 4d 3a f7 8b c3  |p.U..|...|jM:...|
000001a0  7a aa 0f 99 10 ae 58 3a  d3 4e eb 3a a5 5e 4a a4  |z.....X:.N.:.^J.|
000001b0  fb 59 33 ee 75 d0 5e 4c  fe 80 2b 58 c0 c1 00 fe  |.Y3.u.^L..+X....|
000001c0  ff ff 83 fe ff ff 02 00  00 00 00 88 d0 01 00 fe  |................|
000001d0  ff ff 05 fe ff ff 02 e0  d8 05 00 20 1f 00 00 00  |........... ....|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


========= Devices which don't seem to have a corresponding hard drive: =========

sdb sdc sdd sde sdf sdg 

=============================== StdErr Messages: ===============================

unlzma: Decoder error
[/PHP]

---

### Post by nanog on 2011-12-06
use blkid to make sure your uuids in /etc/fstab match.

---

### Post by mick222 on 2011-12-07
checked uuids they match started in recovery mode options seem different. There was an option to mount all partitons or something like that .Used that thewn ran dpkg which seemed to update  I seem to have my home now but still can't boot into 12.04. Tried reinstalling nvidia-current but x wont start will check error messages and post again busy just now.

---

