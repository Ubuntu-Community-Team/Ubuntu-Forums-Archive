---
title: "Grub killed my wubi install of 10.10"
date: 2011-02-24
forum: Ubuntu Studio
---

### Post by eastexsteve on 2011-02-24
I installed ubuntu studio in its own separate partition.  In another partition, I have Vista, and a wubi install of 10.10.  It appears that when ubuntustudio installed GRUB, it killed my access to the wubi install of 10.10 on the windows partition.

When the machine boots, I get the GRUB menu with ubuntu studio as the default choice, and the windows boot loader at the bottom of the list.  When I choose the windows loader, it takes me to the original windows boot menu that lists Vista and Ubuntu as the choices.  Vista works fine.  Ubuntu only gives me a quick flash on the screen that looks like "file not found" and then restarts the machine.  Any ideas on how I can get my wubi install of 10.10 back?

Thanks -

---

### Post by sgx on 2011-02-24
> **eastexsteve said:**
> I installed ubuntu studio in its own separate partition.  In another partition, I have Vista, and a wubi install of 10.10.  It appears that when ubuntustudio installed GRUB, it killed my access to the wubi install of 10.10 on the windows partition.

When the machine boots, I get the GRUB menu with ubuntu studio as the default choice, and the windows boot loader at the bottom of the list.  When I choose the windows loader, it takes me to the original windows boot menu that lists Vista and Ubuntu as the choices.  Vista works fine.  Ubuntu only gives me a quick flash on the screen that looks like "file not found" and then restarts the machine.  Any ideas on how I can get my wubi install of 10.10 back?

Thanks -
Just get any needed data files off the wubi folder, and reinstall it, if its still needed.
There is probably a google tip on how to edit the grub configs, if you made a special setup you really want to keep.

You also could copy your home/username and .etc folders, and do the exact same wubi install again, and over-write those folders, to regain settings. It only takes a few minutes to do the experiment.
Cheers
:)

---

### Post by eastexsteve on 2011-02-24
> **sgx said:**
> Just get any needed data files off the wubi folder, and reinstall it, if its still needed.
There is probably a google tip on how to edit the grub configs, if you made a special setup you really want to keep.

You also could copy your home/username and .etc folders, and do the exact same wubi install again, and over-write those folders, to regain settings. It only takes a few minutes to do the experiment.
Cheers
:)

I would like to do with without having to go through the drawn out hassle of a re-install.  It appears everything is there.  The windows boot just doesn't see it.

---

### Post by bcbc on 2011-02-24
> **eastexsteve said:**
> I installed ubuntu studio in its own separate partition.  In another partition, I have Vista, and a wubi install of 10.10.  It appears that when ubuntustudio installed GRUB, it killed my access to the wubi install of 10.10 on the windows partition.

That's not really possible... wubi uses an entirely independent method of booting... but anyway there obviously is some problem so can you post the results of the [bootinfoscript]("http://bootinfoscript.sourceforge.net/") and hopefully that will make it clearer. Also if you upgraded your wubi to 10.10 from 10.04 then let me know.

If you just need the data off the wubi you can access it independently from your new install. Or alternatively you can transfer the wubi install from the root.disk to a partition install. Those are some options, but start off with the bootinfoscript.

---

### Post by eastexsteve on 2011-02-24
I did a wubi installation of 64 bit 10.10 in Windows Vista 32.  Everything was working fine until I freed up a small logical partition and installed ubuntu studio on it.  Here is the contents of my bootinfoscript:

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for (,msdos5)/boot/grub.

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Dell Utility: Fat16
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /COMMAND.COM

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe 
                       /wubildr.mbr /ubuntu/winboot/wubildr.mbr /wubildr 
                       /ubuntu/winboot/wubildr /ubuntu/disks/root.disk 
                       /ubuntu/disks/swap.disk

sda3/Wubi: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160000000000 bytes
255 heads, 63 sectors/track, 19452 cylinders, total 312500000 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63        80,324        80,262  de Dell Utility
/dev/sda2              81,920    12,861,431    12,779,512   7 HPFS/NTFS
/dev/sda3    *     21,053,440   312,496,127   291,442,688   7 HPFS/NTFS
/dev/sda4          12,861,438    21,053,439     8,192,002   5 Extended
/dev/sda5          12,861,440    20,580,351     7,718,912  83 Linux
/dev/sda6          20,582,400    21,053,439       471,040  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0       8208e58f-880b-49c8-bb61-315971e0325b   ext4                                     
/dev/sda1        07D7-0512                              vfat       DellUtility                   
/dev/sda2        721EBF301EBEEBEB                       ntfs       RECOVERY                      
/dev/sda3        6400C4D800C4B1FA                       ntfs       OS                            
/dev/sda4: PTTYPE="dos" 
/dev/sda5        31dcec78-faca-4ba1-9026-bce6c357d366   ext4                                     
/dev/sda6        673c6eae-9b86-4f36-a871-34d143e6363e   swap                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda5        /                        ext4       (rw,errors=remount-ro,commit=0)


======================== sda3/Wubi/boot/grub/grub.cfg: ========================

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
insmod ntfs
set root='(hd0,msdos3)'
search --no-floppy --fs-uuid --set 6400c4d800c4b1fa
loopback loop0 /ubuntu/disks/root.disk
set root=(loop0)
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ntfs
set root='(hd0,msdos3)'
search --no-floppy --fs-uuid --set 6400c4d800c4b1fa
loopback loop0 /ubuntu/disks/root.disk
set root=(loop0)
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
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/10_lupin ###
menuentry "Ubuntu, Linux 2.6.35-25-generic" {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos3)'
	search --no-floppy --fs-uuid --set 6400c4d800c4b1fa
	loopback loop0 /ubuntu/disks/root.disk
	set root=(loop0)
	linux /boot/vmlinuz-2.6.35-25-generic root=/dev/sda3 loop=/ubuntu/disks/root.disk ro   quiet splash
	initrd /boot/initrd.img-2.6.35-25-generic
}
menuentry "Ubuntu, Linux 2.6.35-25-generic (recovery mode)" {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos3)'
	search --no-floppy --fs-uuid --set 6400c4d800c4b1fa
	loopback loop0 /ubuntu/disks/root.disk
	set root=(loop0)
	linux /boot/vmlinuz-2.6.35-25-generic root=/dev/sda3 loop=/ubuntu/disks/root.disk ro single 
	initrd /boot/initrd.img-2.6.35-25-generic
}
menuentry "Ubuntu, Linux 2.6.32-28-generic" {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos3)'
	search --no-floppy --fs-uuid --set 6400c4d800c4b1fa
	loopback loop0 /ubuntu/disks/root.disk
	set root=(loop0)
	linux /boot/vmlinuz-2.6.32-28-generic root=/dev/sda3 loop=/ubuntu/disks/root.disk ro   quiet splash
	initrd /boot/initrd.img-2.6.32-28-generic
}
menuentry "Ubuntu, Linux 2.6.32-28-generic (recovery mode)" {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos3)'
	search --no-floppy --fs-uuid --set 6400c4d800c4b1fa
	loopback loop0 /ubuntu/disks/root.disk
	set root=(loop0)
	linux /boot/vmlinuz-2.6.32-28-generic root=/dev/sda3 loop=/ubuntu/disks/root.disk ro single 
	initrd /boot/initrd.img-2.6.32-28-generic
}
### END /etc/grub.d/10_lupin ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Dell Utility Partition (on /dev/sda1)" {
	insmod part_msdos
	insmod fat
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set 07d7-0512
	drivemap -s (hd0) ${root}
	chainloader +1
}
menuentry "Windows Recovery Environment (loader) (on /dev/sda3)" {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos3)'
	search --no-floppy --fs-uuid --set 6400c4d800c4b1fa
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

============================= sda3/Wubi/etc/fstab: =============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/host/ubuntu/disks/root.disk /               ext4    loop,errors=remount-ro 0       1
/host/ubuntu/disks/swap.disk none            swap    loop,sw         0       0

================= sda3/Wubi: Location of files loaded by Grub: =================


   7.3GB: boot/grub/grub.cfg
   3.1GB: boot/initrd.img-2.6.32-28-generic
   3.4GB: boot/initrd.img-2.6.35-25-generic
  13.6GB: boot/vmlinuz-2.6.32-28-generic
   2.8GB: boot/vmlinuz-2.6.35-25-generic
   3.4GB: initrd.img
   3.1GB: initrd.img.old
   2.8GB: vmlinuz
  13.6GB: vmlinuz.old

=========================== sda5/boot/grub/grub.cfg: ===========================

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
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set 31dcec78-faca-4ba1-9026-bce6c357d366
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set 31dcec78-faca-4ba1-9026-bce6c357d366
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
menuentry 'Ubuntu, with Linux 2.6.35-25-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set 31dcec78-faca-4ba1-9026-bce6c357d366
	linux	/boot/vmlinuz-2.6.35-25-generic root=UUID=31dcec78-faca-4ba1-9026-bce6c357d366 ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-25-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set 31dcec78-faca-4ba1-9026-bce6c357d366
	echo	'Loading Linux 2.6.35-25-generic ...'
	linux	/boot/vmlinuz-2.6.35-25-generic root=UUID=31dcec78-faca-4ba1-9026-bce6c357d366 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set 31dcec78-faca-4ba1-9026-bce6c357d366
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=31dcec78-faca-4ba1-9026-bce6c357d366 ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set 31dcec78-faca-4ba1-9026-bce6c357d366
	echo	'Loading Linux 2.6.35-22-generic ...'
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=31dcec78-faca-4ba1-9026-bce6c357d366 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-22-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set 31dcec78-faca-4ba1-9026-bce6c357d366
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set 31dcec78-faca-4ba1-9026-bce6c357d366
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Dell Utility Partition (on /dev/sda1)" {
	insmod part_msdos
	insmod fat
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set 07d7-0512
	drivemap -s (hd0) ${root}
	chainloader +1
}
menuentry "Windows Recovery Environment (loader) (on /dev/sda3)" {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos3)'
	search --no-floppy --fs-uuid --set 6400c4d800c4b1fa
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

=============================== sda5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=31dcec78-faca-4ba1-9026-bce6c357d366 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=673c6eae-9b86-4f36-a871-34d143e6363e none            swap    sw              0       0

=================== sda5: Location of files loaded by Grub: ===================


   6.7GB: boot/grub/core.img
   7.8GB: boot/grub/grub.cfg
  10.4GB: boot/initrd.img-2.6.35-22-generic
  10.3GB: boot/initrd.img-2.6.35-25-generic
  10.0GB: boot/vmlinuz-2.6.35-22-generic
  10.1GB: boot/vmlinuz-2.6.35-25-generic
  10.3GB: initrd.img
  10.4GB: initrd.img.old
  10.1GB: vmlinuz
  10.0GB: vmlinuz.old

---

### Post by bcbc on 2011-02-24
> **eastexsteve said:**
> I did a wubi installation of 64 bit 10.10 in Windows Vista 32.  
From the wubi grub.cfg I'd say you upgraded to 10.10 Wubi from 10.04. Your grub.cfg has sections in it that are not present from a default 10.10 install (unless there has been a grub update that I am not aware of). 

At any rate, I believe you have the problem described in the [Wubi megathread]("http://ubuntuforums.org/showthread.php?t=1639198") Problem #2, Solution #1. 

You can do the fix from your working ubuntu install.
Just substitute /dev/sda3 (in place of /dev/sda1 from the wubi megathread instructions). After booting, apply the permanent fix to the wubi install.

Actually you can also boot your wubi install directly from your normal install's grub menu. When you see the grub menu, hit 'c' to get to a grub prompt. Then enter the following:
```
insmod ntfs
set root=(hd0,3)
loopback loop0 /ubuntu/disks/root.disk
set root=(loop0)
linux /vmlinuz root=/dev/sda3 loop=/ubuntu/disks/root.disk ro quiet splash
initrd /initrd.img
boot
```
After booting apply the Permanent Fix from the megathread.

---

### Post by eastexsteve on 2011-02-24
Thanks for the help.  I had an installation of wubi 10.04 32 bit and uninstalled it.  I then did a wubi install of 10.10 64 bit.  I was unaware that ubuntu would see this as an upgrade.

> **bcbc said:**
> From the wubi grub.cfg I'd say you upgraded to 10.10 Wubi from 10.04. Your grub.cfg has sections in it that are not present from a default 10.10 install (unless there has been a grub update that I am not aware of). 

At any rate, I believe you have the problem described in the [Wubi megathread]("http://ubuntuforums.org/showthread.php?t=1639198") Problem #2, Solution #1. 

You can do the fix from your working ubuntu install.
Just substitute /dev/sda3 (in place of /dev/sda1 from the wubi megathread instructions). After booting, apply the permanent fix to the wubi install.

Actually you can also boot your wubi install directly from your normal install's grub menu. When you see the grub menu, hit 'c' to get to a grub prompt. Then enter the following:
```
insmod ntfs
set root=(hd0,3)
loopback loop0 /ubuntu/disks/root.disk
set root=(loop0)
linux /vmlinuz root=/dev/sda3 loop=/ubuntu/disks/root.disk ro quiet splash
initrd /initrd.img
boot
```
After booting apply the Permanent Fix from the megathread.

---

