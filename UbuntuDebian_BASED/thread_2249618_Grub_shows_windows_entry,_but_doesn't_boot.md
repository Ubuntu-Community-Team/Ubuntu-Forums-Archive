---
title: "Grub shows windows entry, but doesn't boot"
date: 2014-10-23
forum: Ubuntu/Debian BASED
---

### Post by prat22 on 2014-10-23
Hi,
This is with Elementary OS, Luna and Win 7.

I am having 2 HDDs, sda having no OS, and sdb having Elementary OS (EOs)  and Win 7. I have installed EOs after Win 7, but when grub shows, it shows win7 in the boot menu, but doesnt really boot.
I reinstalled win 7 while disconnecting sda (as win 7 wont install with too many partitions), and when I boot with only sdb connected, win 7 boots with ease (no mbr choice is shown)!
Again when I connect the two HDD sda and sdb, grub menu shows up at display, as before, but doesnt boot into windows.

I have tried rescatux 0.29, Super grub disk, but in vain. Also I have booted with live cd ubuntu and done a os-probe, where windows is shown, and then grub-update doesnt solve the issue, it shows the win 7 entry, but doesnt boot.

Help???

---

### Post by yancek on 2014-10-23
You probably need to go to the site below and download and run the bootinfoscript from Elementary OS and post the output, a results.txt file here.  Instructions are in the Description box at the site. You might also try just posting the output you get form running update grub, at least the windows part of it.

[http://sourceforge.net/projects/bootinfoscript/](http://sourceforge.net/projects/bootinfoscript/)

---

### Post by grahammechanical on 2014-10-23
I do not support Elementary OS but I know that the Ubuntu installer defaults to installing Grub into the MBR of sda. Now, if you have Windows 7 on sdb, then its boot loader is on sdb and that does not recognise Elementary OS. If Grub is indeed on sda and sda was disconnected when Windows was installed, then the Grub on sda does not know about Windows.

Some times we need not only to update-grub but also to grub-install to get the changes working.

If you want to keep the windows boot loader on sdb but use Grub to load both OS, then run

```
sudo grub-install /dev/sda
sudo update-grub
```

But if you want to over-write the Windows boot loader with Grub then run this

```
sudo grub-install /dev/sdb
sudo update-grub
```

Providing you are correct in saying the Windows is not on sda. I quote

> [COLOR=#000000]I reinstalled win 7 while disconnecting sda[/COLOR]

Regards.

---

### Post by howefield on 2014-10-23
Thread moved to the "*Other Operating Systems*" forum.

---

### Post by prat22 on 2014-10-24
Thanks grahammechanical for your support, but installing grub in sdb didnt solve the issue..

Yancek: find my bootinfo below:

                  Boot Info Script 0.61      [1 April 2012]




============================= Boot Info Summary: ===============================


 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and uses an 
    embedded config file:
    
    ---------------------------------------------------------------------------
    search.fs_uuid 83ed0c73-1c9a-4e6f-8944-da8afeaae166 root 
    set prefix=($root)/boot/grub
    ---------------------------------------------------------------------------
    -----.
 => Grub2 (v1.99) is installed in the MBR of /dev/sdb and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos2)/boot/grub on this drive.


sda1: __________________________________________________________________________


    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info: 


sda5: __________________________________________________________________________


    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        


sda6: __________________________________________________________________________


    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        


sda7: __________________________________________________________________________


    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        


sda8: __________________________________________________________________________


    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        


sdb1: __________________________________________________________________________


    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /grldr /bootmgr /Boot/BCD 
                       /Windows/System32/winload.exe /grldr


sdb2: __________________________________________________________________________


    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  elementary OS Luna
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img


sdb3: __________________________________________________________________________


    File system:       swap
    Boot sector type:  -
    Boot sector info: 


sdb4: __________________________________________________________________________


    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info: 


sdb5: __________________________________________________________________________


    File system:       ntfs
    Boot sector type:  Windows XP: NTFS
    Boot sector info:  According to the info in the boot sector, sdb5 starts 
                       at sector 63.
    Operating System:  
    Boot files:        


sdb6: __________________________________________________________________________


    File system:       ntfs
    Boot sector type:  Windows XP: NTFS
    Boot sector info:  According to the info in the boot sector, sdb6 starts 
                       at sector 63.
    Operating System:  
    Boot files:        


sdb7: __________________________________________________________________________


    File system:       ntfs
    Boot sector type:  Windows XP: NTFS
    Boot sector info:  According to the info in the boot sector, sdb7 starts 
                       at sector 63.
    Operating System:  
    Boot files:        


============================ Drive/Partition Info: =============================


Drive: sda _____________________________________________________________________


Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes


Partition  Boot  Start Sector    End Sector  # of Sectors  Id System


/dev/sda1    *          2,048 1,953,523,711 1,953,521,664   5 Extended
/dev/sda5               4,096   512,004,095   512,000,000   7 NTFS / exFAT / HPFS
/dev/sda6         512,006,144 1,024,006,143   512,000,000   7 NTFS / exFAT / HPFS
/dev/sda7       1,024,008,192 1,536,008,191   512,000,000   7 NTFS / exFAT / HPFS
/dev/sda8       1,536,010,240 1,953,523,711   417,513,472   7 NTFS / exFAT / HPFS




Drive: sdb _____________________________________________________________________


Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes


Partition  Boot  Start Sector    End Sector  # of Sectors  Id System


/dev/sdb1    *          2,048    32,774,143    32,772,096   7 NTFS / exFAT / HPFS
/dev/sdb2          32,774,144    65,546,239    32,772,096  83 Linux
/dev/sdb3          65,546,240    66,070,527       524,288  82 Linux swap / Solaris
/dev/sdb4          66,075,406   312,576,704   246,501,299   5 Extended
/dev/sdb5          66,075,408   143,412,254    77,336,847   7 NTFS / exFAT / HPFS
/dev/sdb6         143,412,318   227,994,479    84,582,162   7 NTFS / exFAT / HPFS
/dev/sdb7         227,994,543   312,576,704    84,582,162   7 NTFS / exFAT / HPFS




"blkid" output: ________________________________________________________________


Device           UUID                                   TYPE       LABEL


/dev/sda5        132E36BA0B084634                       ntfs       
/dev/sda6        0B70B8921F6A9B91                       ntfs       Games
/dev/sda7        26DE24A608D7A794                       ntfs       Work
/dev/sda8        42193F4731FE9BF6                       ntfs       MotionPictures
/dev/sdb1        F08E29158E28D5BE                       ntfs       
/dev/sdb2        83ed0c73-1c9a-4e6f-8944-da8afeaae166   ext4       
/dev/sdb3        a621effd-6f54-4962-a986-6ace0639a0d3   swap       
/dev/sdb5        5CC8897CC88954E4                       ntfs       Games/Downloads
/dev/sdb6        FC60918960914B72                       ntfs       Compatible
/dev/sdb7        403887F73887EA6C                       ntfs       NewVolume


================================ Mount points: =================================


Device           Mount_Point              Type       Options


/dev/sdb2        /                        ext4       (rw,errors=remount-ro)




=========================== sdb2/boot/grub/grub.cfg: ===========================


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
set root='(hd1,msdos2)'
search --no-floppy --fs-uuid --set=root 83ed0c73-1c9a-4e6f-8944-da8afeaae166
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  insmod part_msdos
  insmod ext2
  set root='(hd1,msdos2)'
  search --no-floppy --fs-uuid --set=root 83ed0c73-1c9a-4e6f-8944-da8afeaae166
  set locale_dir=($root)/boot/grub/locale
  set lang=en_IN
  insmod gettext
fi
terminal_output gfxterm
if [ "${recordfail}" = 1 ] ; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###


### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
if background_color 0,0,0; then
  clear
fi
### END /etc/grub.d/05_debian_theme ###


### BEGIN /etc/grub.d/10_linux ###
function gfxmode {
	set gfxpayload="${1}"
	if [ "${1}" = "keep" ]; then
		set vt_handoff=vt.handoff=7
	else
		set vt_handoff=
	fi
}
if [ "${recordfail}" != 1 ]; then
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
if [ "${linux_gfx_mode}" != "text" ]; then load_video; fi
menuentry 'elementary OS, with Linux 3.2.0-68-generic-pae' --class elementary --class gnu-linux --class gnu --class os {
	recordfail
	gfxmode $linux_gfx_mode
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos2)'
	search --no-floppy --fs-uuid --set=root 83ed0c73-1c9a-4e6f-8944-da8afeaae166
	linux	/boot/vmlinuz-3.2.0-68-generic-pae root=UUID=83ed0c73-1c9a-4e6f-8944-da8afeaae166 ro   quiet splash $vt_handoff
	initrd	/boot/initrd.img-3.2.0-68-generic-pae
}
menuentry 'elementary OS, with Linux 3.2.0-68-generic-pae (recovery mode)' --class elementary --class gnu-linux --class gnu --class os {
	recordfail
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos2)'
	search --no-floppy --fs-uuid --set=root 83ed0c73-1c9a-4e6f-8944-da8afeaae166
	echo	'Loading Linux 3.2.0-68-generic-pae ...'
	linux	/boot/vmlinuz-3.2.0-68-generic-pae root=UUID=83ed0c73-1c9a-4e6f-8944-da8afeaae166 ro recovery nomodeset 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-3.2.0-68-generic-pae
}
submenu "Previous Linux versions" {
menuentry 'elementary OS, with Linux 3.2.0-51-generic-pae' --class elementary --class gnu-linux --class gnu --class os {
	recordfail
	gfxmode $linux_gfx_mode
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos2)'
	search --no-floppy --fs-uuid --set=root 83ed0c73-1c9a-4e6f-8944-da8afeaae166
	linux	/boot/vmlinuz-3.2.0-51-generic-pae root=UUID=83ed0c73-1c9a-4e6f-8944-da8afeaae166 ro   quiet splash $vt_handoff
	initrd	/boot/initrd.img-3.2.0-51-generic-pae
}
menuentry 'elementary OS, with Linux 3.2.0-51-generic-pae (recovery mode)' --class elementary --class gnu-linux --class gnu --class os {
	recordfail
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos2)'
	search --no-floppy --fs-uuid --set=root 83ed0c73-1c9a-4e6f-8944-da8afeaae166
	echo	'Loading Linux 3.2.0-51-generic-pae ...'
	linux	/boot/vmlinuz-3.2.0-51-generic-pae root=UUID=83ed0c73-1c9a-4e6f-8944-da8afeaae166 ro recovery nomodeset 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-3.2.0-51-generic-pae
}
}
### END /etc/grub.d/10_linux ###


### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###


### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sdb1)" --class windows --class os {
	insmod part_msdos
	insmod ntfs
	set root='(hd1,msdos1)'
	search --no-floppy --fs-uuid --set=root F08E29158E28D5BE
	chainloader +1
}
set timeout_style=menu
if [ "${timeout}" = 0 ]; then
  set timeout=10
fi
### END /etc/grub.d/30_os-prober ###


### BEGIN /etc/grub.d/30_uefi-firmware ###
### END /etc/grub.d/30_uefi-firmware ###


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


=============================== sdb2/etc/fstab: ================================


--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb2 during installation
UUID=83ed0c73-1c9a-4e6f-8944-da8afeaae166 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb3 during installation
UUID=a621effd-6f54-4962-a986-6ace0639a0d3 none            swap    sw              0       0
--------------------------------------------------------------------------------


=================== sdb2: Location of files loaded by Grub: ====================


           GiB - GB             File                                 Fragment(s)


               =                boot/grub/core.img                             1
               =                boot/grub/grub.cfg                             1
               =                boot/initrd.img-3.2.0-51-generic-pae           3
               =                boot/initrd.img-3.2.0-68-generic-pae           2
               =                boot/vmlinuz-3.2.0-51-generic-pae              1
               =                boot/vmlinuz-3.2.0-68-generic-pae              1
               =                initrd.img                                     2
               =                initrd.img.old                                 3
               =                vmlinuz                                        1
               =                vmlinuz.old                                    1


=============================== StdErr Messages: ===============================


xz: (stdin): Compressed data is corrupt
xz: (stdin): Compressed data is corrupt
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in

---

