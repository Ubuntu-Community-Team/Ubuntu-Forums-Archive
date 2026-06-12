---
title: "Installed Ubuntu, But will not boot up on SSD Drive"
date: 2017-07-12
forum: Ubuntu/Debian BASED
---

### Post by Bakuchris on 2017-07-12
I Installed Ubuntu on my computer but I cannot get it to boot up, I think this might have something to do with the boot file it put on my other two data hard drives and now the operating system won't boot up. Can someone help me or atleast link me to some instructions about Installing Linux on SSD Drives.

---

### Post by yancek on 2017-07-12
Installing Linux to an SSD drive isn't really different than installing to a SATA drive, you just need to point it to the correct drive.
How old is this computer?
Is it the older style MBR or UEFI system?
Did you select the option to Erase Disk and Install Ubuntu?  You don't mention having any other OS.
If you have multiple drives then it is up to you to select which drive to install to and also where/how to install the bootloader.  Answers to the above questions would be a start to resolving the issue.

---

### Post by Bakuchris on 2017-07-12
The computer is from 2010, It use to have Windows 8.1 Installed on it, It is using the MBR system. OK thank you Yancek.

---

### Post by yancek on 2017-07-12
Get boot repair from the link below while booted to the Ubuntu installation media and run it with the option to "Create BootInfo Summary" and post a link to the output here.  That will give some details and someone should be able to make a suggestion as to how to resolve your problem.

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by Bakuchris on 2017-07-13
OK I created the info file Yancek and its listed below. I should of mentioned that the operating system is a derivative of Ubuntu its called "Zorin OS", but everything should be the same as the normal Ubuntu ISO file. 

```
_______________________________________________________________________________________

 Boot Info Script cfd9efe + Boot-Repair extra info      [Boot-Info 26Apr2016]


============================= Boot Info Summary: ===============================

 => Grub2 (v2.00) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for /boot/grub. It also embeds following components:
    
    modules
    ---------------------------------------------------------------------------
    fshelp ext2 part_msdos biosdisk search_fs_uuid
    ---------------------------------------------------------------------------
    
    config script
    ---------------------------------------------------------------------------
    search.fs_uuid 5f6514df-f45d-451e-a8d6-ab51c2d67475 root hd1,msdos1 
    set prefix=($root)'/boot/grub'
    
    ---------------------------------------------------------------------------
 => libparted MBR boot code is installed in the MBR of /dev/sdb.
 => Windows 7/8/2012 is installed in the MBR of /dev/sdc.
 => Syslinux MBR (5.00 and higher) is installed in the MBR of /dev/sdd.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows 8/2012: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sdb1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Zorin OS 12.1
    Boot files:        /boot/grub/grub.cfg /etc/fstab 
                       /boot/grub/i386-pc/core.img

sdc1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows 8/2012: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Boot/BCD

sdd1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  SYSLINUX 4.07
    Boot sector info:  Syslinux looks at sector 32784 of /dev/sdd1 for its 
                       second stage. The integrity check of Syslinux failed. 
                       No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /boot/grub/grub.cfg /syslinux.cfg 
                       /EFI/BOOT/grubx64.efi /ldlinux.sys

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________
Disk /dev/sda: 1.8 TiB, 2000398934016 bytes, 3907029168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: dos

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048 3,907,026,943 3,907,024,896   7 NTFS / exFAT / HPFS


Drive: sdb _____________________________________________________________________
Disk /dev/sdb: 59.6 GiB, 64023257088 bytes, 125045424 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1               2,048   125,044,735   125,042,688  83 Linux


Drive: sdc _____________________________________________________________________
Disk /dev/sdc: 1.8 TiB, 2000398934016 bytes, 3907029168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: dos

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdc1    *          2,048 3,907,026,943 3,907,024,896   7 NTFS / exFAT / HPFS


Drive: sdd _____________________________________________________________________
Disk /dev/sdd: 14.5 GiB, 15606349824 bytes, 30481152 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdd1    *          2,048    30,481,151    30,479,104   c W95 FAT32 (LBA)


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        7808101E080FD9D0                       ntfs       Backup One
/dev/sdb1        5f6514df-f45d-451e-a8d6-ab51c2d67475   ext4       
/dev/sdc1        6CAEF646AEF607FA                       ntfs       Seagate
/dev/sdd1        7EBD-9050                              vfat       ZORIN OS 12
/dev/sr0         2013-08-22-12-28-08-00                 udf        IRM_CCSA_X64FRE_EN-US_DV5

========================= "ls -l /dev/disk/by-id" output: ======================

total 0
lrwxrwxrwx 1 root root  9 Jul 13 18:01 ata-HL-DT-ST_DVDRAM_GSA-H10N_5D0ADBA384C3 -> ../../sr0
lrwxrwxrwx 1 root root  9 Jul 13 18:05 ata-KINGSTON_SV200S364G_12IA33VSKATK -> ../../sdb
lrwxrwxrwx 1 root root 10 Jul 13 18:05 ata-KINGSTON_SV200S364G_12IA33VSKATK-part1 -> ../../sdb1
lrwxrwxrwx 1 root root  9 Jul 13 18:05 ata-ST2000DM001-1ER164_W4Z0Z1X8 -> ../../sdc
lrwxrwxrwx 1 root root 10 Jul 13 18:06 ata-ST2000DM001-1ER164_W4Z0Z1X8-part1 -> ../../sdc1
lrwxrwxrwx 1 root root  9 Jul 13 18:05 ata-WDC_WD20EZRX-00D8PB0_WD-WCC4MPAH0931 -> ../../sda
lrwxrwxrwx 1 root root 10 Jul 13 18:06 ata-WDC_WD20EZRX-00D8PB0_WD-WCC4MPAH0931-part1 -> ../../sda1
lrwxrwxrwx 1 root root  9 Jul 13 18:05 usb-Kingston_DataTraveler_G3_001CC0EC3507EC60D5A000DA-0:0 -> ../../sdd
lrwxrwxrwx 1 root root 10 Jul 13 18:05 usb-Kingston_DataTraveler_G3_001CC0EC3507EC60D5A000DA-0:0-part1 -> ../../sdd1
lrwxrwxrwx 1 root root  9 Jul 13 18:05 wwn-0x5000c5007d18ca34 -> ../../sdc
lrwxrwxrwx 1 root root 10 Jul 13 18:06 wwn-0x5000c5007d18ca34-part1 -> ../../sdc1
lrwxrwxrwx 1 root root  9 Jul 13 18:05 wwn-0x50014ee2b54c5821 -> ../../sda
lrwxrwxrwx 1 root root 10 Jul 13 18:06 wwn-0x50014ee2b54c5821-part1 -> ../../sda1

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdd1        /cdrom                   vfat       (ro,noatime,fmask=0022,dmask=0022,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/sr0         /media/zorin/IRM_CCSA_X64FRE_EN-US_DV5 udf        (ro,nosuid,nodev,relatime,uid=999,gid=999,iocharset=utf8,uhelper=udisks2)


=========================== sdb1/boot/grub/grub.cfg: ===========================

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
if [ "${next_entry}" ] ; then
   set default="${next_entry}"
   set next_entry=
   save_env next_entry
   set boot_once=true
else
   set default="0"
fi

if [ x"${feature_menuentry_id}" = xy ]; then
  menuentry_id_option="--id"
else
  menuentry_id_option=""
fi

export menuentry_id_option

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
  if [ x$feature_all_video_module = xy ]; then
    insmod all_video
  else
    insmod efi_gop
    insmod efi_uga
    insmod ieee1275_fb
    insmod vbe
    insmod vga
    insmod video_bochs
    insmod video_cirrus
  fi
}

if [ x$feature_default_font_path = xy ] ; then
   font=unicode
else
insmod part_msdos
insmod ext2
set root='hd1,msdos1'
if [ x$feature_platform_search_hint = xy ]; then
  search --no-floppy --fs-uuid --set=root --hint-bios=hd1,msdos1 --hint-efi=hd1,msdos1 --hint-baremetal=ahci1,msdos1  5f6514df-f45d-451e-a8d6-ab51c2d67475
else
  search --no-floppy --fs-uuid --set=root 5f6514df-f45d-451e-a8d6-ab51c2d67475
fi
    font="/usr/share/grub/unicode.pf2"
fi

if loadfont $font ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  set locale_dir=$prefix/locale
  set lang=en_CA
  insmod gettext
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='hd1,msdos1'
if [ x$feature_platform_search_hint = xy ]; then
  search --no-floppy --fs-uuid --set=root --hint-bios=hd1,msdos1 --hint-efi=hd1,msdos1 --hint-baremetal=ahci1,msdos1  5f6514df-f45d-451e-a8d6-ab51c2d67475
else
  search --no-floppy --fs-uuid --set=root 5f6514df-f45d-451e-a8d6-ab51c2d67475
fi
insmod gfxmenu
insmod png
set theme=($root)/usr/share/grub/themes/zorin/theme.txt
export theme
if [ "${recordfail}" = 1 ] ; then
  set timeout=30
else
  if [ x$feature_timeout_style = xy ] ; then
    set timeout_style=menu
    set timeout=10
  # Fallback normal timeout code in case the timeout_style feature is
  # unavailable.
  else
    set timeout=10
  fi
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
if background_color 2,14,18; then
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
menuentry 'Zorin' --class zorin --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-simple-5f6514df-f45d-451e-a8d6-ab51c2d67475' {
    recordfail
    load_video
    gfxmode $linux_gfx_mode
    insmod gzio
    if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
    insmod part_msdos
    insmod ext2
    set root='hd1,msdos1'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd1,msdos1 --hint-efi=hd1,msdos1 --hint-baremetal=ahci1,msdos1  5f6514df-f45d-451e-a8d6-ab51c2d67475
    else
      search --no-floppy --fs-uuid --set=root 5f6514df-f45d-451e-a8d6-ab51c2d67475
    fi
    linux    /boot/vmlinuz-4.8.0-39-generic root=UUID=5f6514df-f45d-451e-a8d6-ab51c2d67475 ro acpi=off quiet splash $vt_handoff
    initrd    /boot/initrd.img-4.8.0-39-generic
}
submenu 'Advanced options for Zorin' $menuentry_id_option 'gnulinux-advanced-5f6514df-f45d-451e-a8d6-ab51c2d67475' {
    menuentry 'Zorin, with Linux 4.8.0-39-generic' --class zorin --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-4.8.0-39-generic-advanced-5f6514df-f45d-451e-a8d6-ab51c2d67475' {
        recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
        insmod part_msdos
        insmod ext2
        set root='hd1,msdos1'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd1,msdos1 --hint-efi=hd1,msdos1 --hint-baremetal=ahci1,msdos1  5f6514df-f45d-451e-a8d6-ab51c2d67475
        else
          search --no-floppy --fs-uuid --set=root 5f6514df-f45d-451e-a8d6-ab51c2d67475
        fi
        echo    'Loading Linux 4.8.0-39-generic ...'
        linux    /boot/vmlinuz-4.8.0-39-generic root=UUID=5f6514df-f45d-451e-a8d6-ab51c2d67475 ro acpi=off quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-4.8.0-39-generic
    }
    menuentry 'Zorin, with Linux 4.8.0-39-generic (recovery mode)' --class zorin --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-4.8.0-39-generic-recovery-5f6514df-f45d-451e-a8d6-ab51c2d67475' {
        recordfail
        load_video
        insmod gzio
        if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
        insmod part_msdos
        insmod ext2
        set root='hd1,msdos1'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd1,msdos1 --hint-efi=hd1,msdos1 --hint-baremetal=ahci1,msdos1  5f6514df-f45d-451e-a8d6-ab51c2d67475
        else
          search --no-floppy --fs-uuid --set=root 5f6514df-f45d-451e-a8d6-ab51c2d67475
        fi
        echo    'Loading Linux 4.8.0-39-generic ...'
        linux    /boot/vmlinuz-4.8.0-39-generic root=UUID=5f6514df-f45d-451e-a8d6-ab51c2d67475 ro recovery nomodeset acpi=off
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-4.8.0-39-generic
    }
}

### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###

### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry 'Memory test (memtest86+)' {
    insmod part_msdos
    insmod ext2
    set root='hd1,msdos1'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd1,msdos1 --hint-efi=hd1,msdos1 --hint-baremetal=ahci1,msdos1  5f6514df-f45d-451e-a8d6-ab51c2d67475
    else
      search --no-floppy --fs-uuid --set=root 5f6514df-f45d-451e-a8d6-ab51c2d67475
    fi
    knetbsd    /boot/memtest86+.elf
}
menuentry 'Memory test (memtest86+, serial console 115200)' {
    insmod part_msdos
    insmod ext2
    set root='hd1,msdos1'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd1,msdos1 --hint-efi=hd1,msdos1 --hint-baremetal=ahci1,msdos1  5f6514df-f45d-451e-a8d6-ab51c2d67475
    else
      search --no-floppy --fs-uuid --set=root 5f6514df-f45d-451e-a8d6-ab51c2d67475
    fi
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry 'Windows 10 (loader) (on /dev/sdc1)' --class windows --class os $menuentry_id_option 'osprober-chain-6CAEF646AEF607FA' {
    insmod part_msdos
    insmod ntfs
    set root='hd2,msdos1'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd2,msdos1 --hint-efi=hd2,msdos1 --hint-baremetal=ahci2,msdos1  6CAEF646AEF607FA
    else
      search --no-floppy --fs-uuid --set=root 6CAEF646AEF607FA
    fi
    parttool ${root} hidden-
    drivemap -s (hd0) ${root}
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
if [ -f  ${config_directory}/custom.cfg ]; then
  source ${config_directory}/custom.cfg
elif [ -z "${config_directory}" -a -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###
--------------------------------------------------------------------------------

=============================== sdb1/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sdb1 during installation
UUID=5f6514df-f45d-451e-a8d6-ab51c2d67475 /               ext4    errors=remount-ro 0       1
--------------------------------------------------------------------------------

=================== sdb1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

  32.363437653 = 34.749976576   boot/grub/grub.cfg                             1
  56.149604797 = 60.290179072   boot/grub/i386-pc/core.img                     1
  56.138599396 = 60.278362112   boot/vmlinuz-4.8.0-39-generic                  1
  56.138599396 = 60.278362112   vmlinuz                                        1
   2.702404022 = 2.901684224    boot/initrd.img-4.8.0-39-generic               2
   2.702404022 = 2.901684224    initrd.img                                     2

=========================== sdd1/boot/grub/grub.cfg: ===========================

--------------------------------------------------------------------------------

if loadfont /boot/grub/font.pf2 ; then
    set gfxmode=auto
    insmod efi_gop
    insmod efi_uga
    insmod gfxterm
    terminal_output gfxterm
    insmod gfxmenu
    insmod png
    set theme=/boot/grub/themes/zorin/theme.txt
    export theme
fi

set menu_color_normal=white/black
set menu_color_highlight=black/light-gray

menuentry "Try Zorin OS without installing" {
    set gfxpayload=keep
    linux    /casper/vmlinuz  file=/cdrom/preseed/ubuntu.seed boot=casper quiet splash ---
    initrd    /casper/initrd.lz
}
menuentry "Install Zorin OS" {
    set gfxpayload=keep
    linux    /casper/vmlinuz  file=/cdrom/preseed/ubuntu.seed boot=casper only-ubiquity quiet splash ---
    initrd    /casper/initrd.lz
}
menuentry "Check disc for defects" {
    set gfxpayload=keep
    linux    /casper/vmlinuz  boot=casper integrity-check quiet splash ---
    initrd    /casper/initrd.lz
}
--------------------------------------------------------------------------------

============================== sdd1/syslinux.cfg: ==============================

--------------------------------------------------------------------------------
DEFAULT loadconfig

LABEL loadconfig
  CONFIG /isolinux/isolinux.cfg
  APPEND /isolinux/
--------------------------------------------------------------------------------

=================== sdd1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             boot/grub/grub.cfg                             1

================= sdd1: Location of files loaded by Syslinux: ==================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             syslinux.cfg                                   1
            ?? = ??             ldlinux.sys                                    1

=============================== StdErr Messages: ===============================

File descriptor 9 (/proc/31525/mounts) leaked on lvs invocation. Parent PID 8877: bash
File descriptor 63 (pipe:[273979]) leaked on lvs invocation. Parent PID 8877: bash

ADDITIONAL INFORMATION :
=================== log of boot-repair 2017-07-13__18h05 ===================
boot-repair version : 4ppa40
boot-sav version : 4ppa40
glade2script version : 3.2.3~ppa1
boot-sav-extra version : 4ppa40
Warning: Unable to open /dev/sr0 read-write (Read-only file system).  /dev/sr0 has been opened read-only.
Error: /dev/sr0: unrecognised disk label
Warning: Unable to open /dev/sr0 read-write (Read-only file system).  /dev/sr0 has been opened read-only.
Error: /dev/sr0: unrecognised disk label
boot-repair is executed in live-session (Zorin OS 12.1, xenial, Zorin, x86_64)
CPU op-mode(s):        32-bit, 64-bit
boot=casper initrd=/casper/initrd.lz quiet splash --  acpi=off
ls: cannot access '/home/usr/.config': No such file or directory

=================== os-prober:
/dev/sdb1:Zorin OS 12.1 (12):Zorin:linux
/dev/sdc1:Windows 10 (loader):Windows:chain

=================== blkid:
/dev/sda1: LABEL="Backup One" UUID="7808101E080FD9D0" TYPE="ntfs" PARTUUID="5786dd37-01"
/dev/sdb1: UUID="5f6514df-f45d-451e-a8d6-ab51c2d67475" TYPE="ext4" PARTUUID="d36cb6ee-01"
/dev/sdc1: LABEL="Seagate" UUID="6CAEF646AEF607FA" TYPE="ntfs" PARTUUID="e715c2a0-01"
/dev/sdd1: LABEL="ZORIN OS 12" UUID="7EBD-9050" TYPE="vfat" PARTUUID="0294ad8b-01"
/dev/loop0: TYPE="squashfs"
/dev/sr0: UUID="2013-08-22-12-28-08-00" LABEL="IRM_CCSA_X64FRE_EN-US_DV5" TYPE="udf"


2 disks with OS, 2 OS : 1 Linux, 0 MacOS, 1 Windows, 0 unknown type OS.


=================== sdb1/etc/grub.d/ :
drwxr-xr-x  2 root root     4096 Feb 24 06:19 grub.d
total 76
-rwxr-xr-x 1 root root  9791 Feb 13 18:24 00_header
-rwxr-xr-x 1 root root  6258 Feb 12 20:39 05_debian_theme
-rwxr-xr-x 1 root root 12251 Feb 13 18:24 10_linux
-rwxr-xr-x 1 root root 11082 Feb 13 18:24 20_linux_xen
-rwxr-xr-x 1 root root  1992 Jan 28  2016 20_memtest86+
-rwxr-xr-x 1 root root 11692 Feb 13 18:24 30_os-prober
-rwxr-xr-x 1 root root  1418 Feb 13 18:24 30_uefi-firmware
-rwxr-xr-x 1 root root   214 Feb 13 18:24 40_custom
-rwxr-xr-x 1 root root   216 Feb 13 18:24 41_custom
-rw-r--r-- 1 root root   483 Feb 13 18:24 README




=================== sdb1/etc/default/grub :

# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX="acpi=off"

# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"

GRUB_THEME=/usr/share/grub/themes/zorin/theme.txt




=================== UEFI/Legacy mode:
This live-session is not in EFI-mode.
SecureBoot maybe enabled.


=================== PARTITIONS & DISKS:
sda1    : sda,    not-sepboot,    no-grubenv    nogrub,    no-docgrub,    no-update-grub,    32,    no-boot,    no-os,    not--efi--part,    part-has-no-fstab,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot,    nopakmgr,    nogrubinstall,    no---usr,    part-has-no-fstab,    not-sep-usr,    standard,    farbios,    /mnt/boot-sav/sda1.
sdb1    : sdb,    not-sepboot,    grubenv-ok    grub2,    signed grub-pc ,    update-grub,    64,    with-boot,    is-os,    not--efi--part,    fstab-without-boot,    fstab-without-efi,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot,    apt-get,    grub-install,    with--usr,    fstab-without-usr,    not-sep-usr,    standard,    not-far,    /mnt/boot-sav/sdb1.
sdc1    : sdc,    not-sepboot,    no-grubenv    nogrub,    no-docgrub,    no-update-grub,    32,    no-boot,    is-os,    not--efi--part,    part-has-no-fstab,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    bootmgr,    is-winboot,    nopakmgr,    nogrubinstall,    no---usr,    part-has-no-fstab,    not-sep-usr,    standard,    farbios,    /mnt/boot-sav/sdc1.

sda    : not-GPT,    BIOSboot-not-needed,    has-no-EFIpart,     not-usb,    no-os,    2048 sectors * 512 bytes
sdb    : not-GPT,    BIOSboot-not-needed,    has-no-EFIpart,     not-usb,    has-os,    2048 sectors * 512 bytes
sdc    : not-GPT,    BIOSboot-not-needed,    has-no-EFIpart,     not-usb,    has-os,    2048 sectors * 512 bytes


=================== parted -l:

Model: ATA WDC WD20EZRX-00D (scsi)
Disk /dev/sda: 2000GB
Sector size (logical/physical): 512B/4096B
Partition Table: msdos
Disk Flags:

Number  Start   End     Size    Type     File system  Flags
1      1049kB  2000GB  2000GB  primary  ntfs         boot


Model: ATA KINGSTON SV200S3 (scsi)
Disk /dev/sdb: 64.0GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Disk Flags:

Number  Start   End     Size    Type     File system  Flags
1      1049kB  64.0GB  64.0GB  primary  ext4


Model: ATA ST2000DM001-1ER1 (scsi)
Disk /dev/sdc: 2000GB
Sector size (logical/physical): 512B/4096B
Partition Table: msdos
Disk Flags:

Number  Start   End     Size    Type     File system  Flags
1      1049kB  2000GB  2000GB  primary  ntfs         boot


Model: Kingston DataTraveler G3 (scsi)
Disk /dev/sdd: 15.6GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Disk Flags:

Number  Start   End     Size    Type     File system  Flags
1      1049kB  15.6GB  15.6GB  primary  fat32        boot, lba


Model: HL-DT-ST DVDRAM GSA-H10N (scsi)
Disk /dev/sr0: 3899MB
Sector size (logical/physical): 2048B/2048B
Partition Table: unknown
Disk Flags:

=================== parted -lm:

BYT;
/dev/sda:2000GB:scsi:512:4096:msdos:ATA WDC WD20EZRX-00D:;
1:1049kB:2000GB:2000GB:ntfs::boot;

BYT;
/dev/sdb:64.0GB:scsi:512:512:msdos:ATA KINGSTON SV200S3:;
1:1049kB:64.0GB:64.0GB:ext4::;

BYT;
/dev/sdc:2000GB:scsi:512:4096:msdos:ATA ST2000DM001-1ER1:;
1:1049kB:2000GB:2000GB:ntfs::boot;

BYT;
/dev/sdd:15.6GB:scsi:512:512:msdos:Kingston DataTraveler G3:;
1:1049kB:15.6GB:15.6GB:fat32::boot, lba;

BYT;
/dev/sr0:3899MB:scsi:2048:2048:unknown:HL-DT-ST DVDRAM GSA-H10N:;

=================== lsblk:
KNAME TYPE FSTYPE    SIZE LABEL
sdd   disk          14.5G
sdd1  part vfat     14.5G ZORIN OS 12
sdb   disk          59.6G
sdb1  part ext4     59.6G
sr0   rom  udf       3.6G IRM_CCSA_X64FRE_EN-US_DV5
loop0 loop squashfs  1.4G
sdc   disk           1.8T
sdc1  part ntfs      1.8T Seagate
sda   disk           1.8T
sda1  part ntfs      1.8T Backup One

KNAME ROTA RO RM STATE   MOUNTPOINT
sdd      1  0  1 running
sdd1     1  0  1         /cdrom
sdb      0  0  0 running
sdb1     0  0  0         /mnt/boot-sav/sdb1
sr0      1  0  1 running /media/zorin/IRM_CCSA_X64FRE_EN-US_DV5
loop0    1  1  0         /rofs
sdc      1  0  0 running
sdc1     1  0  0         /mnt/boot-sav/sdc1
sda      1  0  0 running
sda1     1  0  0         /mnt/boot-sav/sda1


=================== mount:
sysfs on /sys type sysfs (rw,nosuid,nodev,noexec,relatime)
proc on /proc type proc (rw,nosuid,nodev,noexec,relatime)
udev on /dev type devtmpfs (rw,nosuid,relatime,size=5321140k,nr_inodes=1330285,mode=755)
devpts on /dev/pts type devpts (rw,nosuid,noexec,relatime,gid=5,mode=620,ptmxmode=000)
tmpfs on /run type tmpfs (rw,nosuid,noexec,relatime,size=1075288k,mode=755)
/dev/sdd1 on /cdrom type vfat (ro,noatime,fmask=0022,dmask=0022,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop0 on /rofs type squashfs (ro,noatime)
aufs on / type aufs (rw,noatime,si=260514732e044837)
securityfs on /sys/kernel/security type securityfs (rw,nosuid,nodev,noexec,relatime)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
tmpfs on /run/lock type tmpfs (rw,nosuid,nodev,noexec,relatime,size=5120k)
tmpfs on /sys/fs/cgroup type tmpfs (ro,nosuid,nodev,noexec,mode=755)
cgroup on /sys/fs/cgroup/systemd type cgroup (rw,nosuid,nodev,noexec,relatime,xattr,release_agent=/lib/systemd/systemd-cgroups-agent,name=systemd)
pstore on /sys/fs/pstore type pstore (rw,nosuid,nodev,noexec,relatime)
cgroup on /sys/fs/cgroup/hugetlb type cgroup (rw,nosuid,nodev,noexec,relatime,hugetlb)
cgroup on /sys/fs/cgroup/memory type cgroup (rw,nosuid,nodev,noexec,relatime,memory)
cgroup on /sys/fs/cgroup/net_cls,net_prio type cgroup (rw,nosuid,nodev,noexec,relatime,net_cls,net_prio)
cgroup on /sys/fs/cgroup/perf_event type cgroup (rw,nosuid,nodev,noexec,relatime,perf_event)
cgroup on /sys/fs/cgroup/cpu,cpuacct type cgroup (rw,nosuid,nodev,noexec,relatime,cpu,cpuacct)
cgroup on /sys/fs/cgroup/blkio type cgroup (rw,nosuid,nodev,noexec,relatime,blkio)
cgroup on /sys/fs/cgroup/cpuset type cgroup (rw,nosuid,nodev,noexec,relatime,cpuset)
cgroup on /sys/fs/cgroup/devices type cgroup (rw,nosuid,nodev,noexec,relatime,devices)
cgroup on /sys/fs/cgroup/freezer type cgroup (rw,nosuid,nodev,noexec,relatime,freezer)
cgroup on /sys/fs/cgroup/pids type cgroup (rw,nosuid,nodev,noexec,relatime,pids)
systemd-1 on /proc/sys/fs/binfmt_misc type autofs (rw,relatime,fd=28,pgrp=1,timeout=0,minproto=5,maxproto=5,direct,pipe_ino=9113)
hugetlbfs on /dev/hugepages type hugetlbfs (rw,relatime)
mqueue on /dev/mqueue type mqueue (rw,relatime)
debugfs on /sys/kernel/debug type debugfs (rw,relatime)
tracefs on /sys/kernel/debug/tracing type tracefs (rw,relatime)
fusectl on /sys/fs/fuse/connections type fusectl (rw,relatime)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev,relatime)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,relatime)
tmpfs on /run/user/999 type tmpfs (rw,nosuid,nodev,relatime,size=1075288k,mode=700,uid=999,gid=999)
gvfsd-fuse on /run/user/999/gvfs type fuse.gvfsd-fuse (rw,nosuid,nodev,relatime,user_id=999,group_id=999)
/dev/sr0 on /media/zorin/IRM_CCSA_X64FRE_EN-US_DV5 type udf (ro,nosuid,nodev,relatime,uid=999,gid=999,iocharset=utf8,uhelper=udisks2)
/dev/sda1 on /mnt/boot-sav/sda1 type fuseblk (rw,relatime,user_id=0,group_id=0,allow_other,blksize=4096)
/dev/sdb1 on /mnt/boot-sav/sdb1 type ext4 (rw,relatime,data=ordered)
/dev/sdc1 on /mnt/boot-sav/sdc1 type fuseblk (rw,relatime,user_id=0,group_id=0,allow_other,blksize=4096)


=================== ls:
/sys/block/sda (filtered):  alignment_offset badblocks bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight integrity power queue range removable ro sda1 size slaves stat subsystem trace uevent
/sys/block/sdb (filtered):  alignment_offset badblocks bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight integrity power queue range removable ro sdb1 size slaves stat subsystem trace uevent
/sys/block/sdc (filtered):  alignment_offset badblocks bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight integrity power queue range removable ro sdc1 size slaves stat subsystem trace uevent
/sys/block/sdd (filtered):  alignment_offset badblocks bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight integrity power queue range removable ro sdd1 size slaves stat subsystem trace uevent
/sys/block/sr0 (filtered):  alignment_offset badblocks bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight integrity power queue range removable ro size slaves stat subsystem trace uevent
/dev (filtered):  autofs block bsg btrfs-control bus cdrom cdrw char console core cpu cpu_dma_latency cuse disk dri dvd dvdrw ecryptfs fb0 fd full fuse fw0 hidraw0 hidraw1 hidraw2 hidraw3 hidraw4 hidraw5 hpet hugepages hwrng i2c-0 i2c-1 i2c-2 i2c-3 i2c-4 i2c-5 initctl input kfd kmsg kvm lightnvm log lp0 mapper mcelog media0 mem memory_bandwidth mqueue net network_latency network_throughput null parport0 port ppp psaux ptmx pts radio0 random rfkill rtc rtc0 sda sda1 sdb sdb1 sdc sdc1 sdd sdd1 sg0 sg1 sg2 sg3 sg4 shm snapshot snd sr0 stderr stdin stdout uhid uinput urandom usb userio v4l vbi0 vfio vga_arbiter vhci vhost-net video0 zero
ls /dev/mapper:  control

=================== hexdump -n512 -C /dev/sda1
00000000  eb 52 90 4e 54 46 53 20  20 20 20 00 02 08 00 00  |.R.NTFS    .....|
00000010  00 00 00 00 00 f8 00 00  3f 00 ff 00 00 08 00 00  |........?.......|
00000020  00 00 00 00 80 00 80 00  ff 77 e0 e8 00 00 00 00  |.........w......|
00000030  00 00 0c 00 00 00 00 00  02 00 00 00 00 00 00 00  |................|
00000040  f6 00 00 00 01 00 00 00  d0 d9 0f 08 1e 10 08 78  |...............x|
00000050  00 00 00 00 fa 33 c0 8e  d0 bc 00 7c fb 68 c0 07  |.....3.....|.h..|
00000060  1f 1e 68 66 00 cb 88 16  0e 00 66 81 3e 03 00 4e  |..hf......f.>..N|
00000070  54 46 53 75 15 b4 41 bb  aa 55 cd 13 72 0c 81 fb  |TFSu..A..U..r...|
00000080  55 aa 75 06 f7 c1 01 00  75 03 e9 dd 00 1e 83 ec  |U.u.....u.......|
00000090  18 68 1a 00 b4 48 8a 16  0e 00 8b f4 16 1f cd 13  |.h...H..........|
000000a0  9f 83 c4 18 9e 58 1f 72  e1 3b 06 0b 00 75 db a3  |.....X.r.;...u..|
000000b0  0f 00 c1 2e 0f 00 04 1e  5a 33 db b9 00 20 2b c8  |........Z3... +.|
000000c0  66 ff 06 11 00 03 16 0f  00 8e c2 ff 06 16 00 e8  |f...............|
000000d0  4b 00 2b c8 77 ef b8 00  bb cd 1a 66 23 c0 75 2d  |K.+.w......f#.u-|
000000e0  66 81 fb 54 43 50 41 75  24 81 f9 02 01 72 1e 16  |f..TCPAu$....r..|
000000f0  68 07 bb 16 68 52 11 16  68 09 00 66 53 66 53 66  |h...hR..h..fSfSf|
00000100  55 16 16 16 68 b8 01 66  61 0e 07 cd 1a 33 c0 bf  |U...h..fa....3..|
00000110  0a 13 b9 f6 0c fc f3 aa  e9 fe 01 90 90 66 60 1e  |.............f`.|
00000120  06 66 a1 11 00 66 03 06  1c 00 1e 66 68 00 00 00  |.f...f.....fh...|
00000130  00 66 50 06 53 68 01 00  68 10 00 b4 42 8a 16 0e  |.fP.Sh..h...B...|
00000140  00 16 1f 8b f4 cd 13 66  59 5b 5a 66 59 66 59 1f  |.......fY[ZfYfY.|
00000150  0f 82 16 00 66 ff 06 11  00 03 16 0f 00 8e c2 ff  |....f...........|
00000160  0e 16 00 75 bc 07 1f 66  61 c3 a1 f6 01 e8 09 00  |...u...fa.......|
00000170  a1 fa 01 e8 03 00 f4 eb  fd 8b f0 ac 3c 00 74 09  |............<.t.|
00000180  b4 0e bb 07 00 cd 10 eb  f2 c3 0d 0a 41 20 64 69  |............A di|
00000190  73 6b 20 72 65 61 64 20  65 72 72 6f 72 20 6f 63  |sk read error oc|
000001a0  63 75 72 72 65 64 00 0d  0a 42 4f 4f 54 4d 47 52  |curred...BOOTMGR|
000001b0  20 69 73 20 63 6f 6d 70  72 65 73 73 65 64 00 0d  | is compressed..|
000001c0  0a 50 72 65 73 73 20 43  74 72 6c 2b 41 6c 74 2b  |.Press Ctrl+Alt+|
000001d0  44 65 6c 20 74 6f 20 72  65 73 74 61 72 74 0d 0a  |Del to restart..|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 8a 01  a7 01 bf 01 00 00 55 aa  |..............U.|
00000200

=================== hexdump -n512 -C /dev/sdc1
00000000  eb 52 90 4e 54 46 53 20  20 20 20 00 02 08 00 00  |.R.NTFS    .....|
00000010  00 00 00 00 00 f8 00 00  3f 00 ff 00 00 08 00 00  |........?.......|
00000020  00 00 00 00 80 00 80 00  ff 77 e0 e8 00 00 00 00  |.........w......|
00000030  00 00 0c 00 00 00 00 00  02 00 00 00 00 00 00 00  |................|
00000040  f6 00 00 00 01 00 00 00  fa 07 f6 ae 46 f6 ae 6c  |............F..l|
00000050  00 00 00 00 fa 33 c0 8e  d0 bc 00 7c fb 68 c0 07  |.....3.....|.h..|
00000060  1f 1e 68 66 00 cb 88 16  0e 00 66 81 3e 03 00 4e  |..hf......f.>..N|
00000070  54 46 53 75 15 b4 41 bb  aa 55 cd 13 72 0c 81 fb  |TFSu..A..U..r...|
00000080  55 aa 75 06 f7 c1 01 00  75 03 e9 dd 00 1e 83 ec  |U.u.....u.......|
00000090  18 68 1a 00 b4 48 8a 16  0e 00 8b f4 16 1f cd 13  |.h...H..........|
000000a0  9f 83 c4 18 9e 58 1f 72  e1 3b 06 0b 00 75 db a3  |.....X.r.;...u..|
000000b0  0f 00 c1 2e 0f 00 04 1e  5a 33 db b9 00 20 2b c8  |........Z3... +.|
000000c0  66 ff 06 11 00 03 16 0f  00 8e c2 ff 06 16 00 e8  |f...............|
000000d0  4b 00 2b c8 77 ef b8 00  bb cd 1a 66 23 c0 75 2d  |K.+.w......f#.u-|
000000e0  66 81 fb 54 43 50 41 75  24 81 f9 02 01 72 1e 16  |f..TCPAu$....r..|
000000f0  68 07 bb 16 68 52 11 16  68 09 00 66 53 66 53 66  |h...hR..h..fSfSf|
00000100  55 16 16 16 68 b8 01 66  61 0e 07 cd 1a 33 c0 bf  |U...h..fa....3..|
00000110  0a 13 b9 f6 0c fc f3 aa  e9 fe 01 90 90 66 60 1e  |.............f`.|
00000120  06 66 a1 11 00 66 03 06  1c 00 1e 66 68 00 00 00  |.f...f.....fh...|
00000130  00 66 50 06 53 68 01 00  68 10 00 b4 42 8a 16 0e  |.fP.Sh..h...B...|
00000140  00 16 1f 8b f4 cd 13 66  59 5b 5a 66 59 66 59 1f  |.......fY[ZfYfY.|
00000150  0f 82 16 00 66 ff 06 11  00 03 16 0f 00 8e c2 ff  |....f...........|
00000160  0e 16 00 75 bc 07 1f 66  61 c3 a1 f6 01 e8 09 00  |...u...fa.......|
00000170  a1 fa 01 e8 03 00 f4 eb  fd 8b f0 ac 3c 00 74 09  |............<.t.|
00000180  b4 0e bb 07 00 cd 10 eb  f2 c3 0d 0a 41 20 64 69  |............A di|
00000190  73 6b 20 72 65 61 64 20  65 72 72 6f 72 20 6f 63  |sk read error oc|
000001a0  63 75 72 72 65 64 00 0d  0a 42 4f 4f 54 4d 47 52  |curred...BOOTMGR|
000001b0  20 69 73 20 63 6f 6d 70  72 65 73 73 65 64 00 0d  | is compressed..|
000001c0  0a 50 72 65 73 73 20 43  74 72 6c 2b 41 6c 74 2b  |.Press Ctrl+Alt+|
000001d0  44 65 6c 20 74 6f 20 72  65 73 74 61 72 74 0d 0a  |Del to restart..|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 8a 01  a7 01 bf 01 00 00 55 aa  |..............U.|
00000200

=================== df -Th:

Filesystem     Type      Size  Used Avail Use% Mounted on
udev           devtmpfs  5.1G     0  5.1G   0% /dev
tmpfs          tmpfs     1.1G  9.6M  1.1G   1% /run
/dev/sdd1      vfat       15G  1.6G   13G  11% /cdrom
/dev/loop0     squashfs  1.5G  1.5G     0 100% /rofs
aufs           aufs      5.2G  385M  4.8G   8% /
tmpfs          tmpfs     5.2G   21M  5.2G   1% /dev/shm
tmpfs          tmpfs     5.0M  8.0K  5.0M   1% /run/lock
tmpfs          tmpfs     5.2G     0  5.2G   0% /sys/fs/cgroup
tmpfs          tmpfs     5.2G  4.0K  5.2G   1% /tmp
tmpfs          tmpfs     1.1G   40K  1.1G   1% /run/user/999
/dev/sr0       udf       3.7G  3.7G     0 100% /media/zorin/IRM_CCSA_X64FRE_EN-US_DV5
/dev/sda1      fuseblk   1.9T  1.8T   80G  96% /mnt/boot-sav/sda1
/dev/sdb1      ext4       59G  5.5G   51G  10% /mnt/boot-sav/sdb1
/dev/sdc1      fuseblk   1.9T  1.7T  131G  93% /mnt/boot-sav/sdc1

=================== fdisk -l:
Disk /dev/ram0: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram1: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram2: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram3: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram4: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram5: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram6: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram7: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram8: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram9: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram10: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram11: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram12: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram13: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram14: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram15: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/loop0: 1.4 GiB, 1525719040 bytes, 2979920 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/sda: 1.8 TiB, 2000398934016 bytes, 3907029168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: dos
Disk identifier: 0x5786dd37

Device     Boot Start        End    Sectors  Size Id Type
/dev/sda1  *     2048 3907026943 3907024896  1.8T  7 HPFS/NTFS/exFAT


Disk /dev/sdb: 59.6 GiB, 64023257088 bytes, 125045424 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0xd36cb6ee

Device     Boot Start       End   Sectors  Size Id Type
/dev/sdb1        2048 125044735 125042688 59.6G 83 Linux


Disk /dev/sdc: 1.8 TiB, 2000398934016 bytes, 3907029168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: dos
Disk identifier: 0xe715c2a0

Device     Boot Start        End    Sectors  Size Id Type
/dev/sdc1  *     2048 3907026943 3907024896  1.8T  7 HPFS/NTFS/exFAT


Disk /dev/sdd: 14.5 GiB, 15606349824 bytes, 30481152 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x0294ad8b

Device     Boot Start      End  Sectors  Size Id Type
/dev/sdd1  *     2048 30481151 30479104 14.5G  c W95 FAT32 (LBA)


Gtk-Message: GtkDialog mapped without a transient parent. This is discouraged.
User choice: Is sdb (64.0GB) a removable disk? no




=================== Suggested repair
The default repair of the Boot-Repair utility would purge (in order to) and reinstall the grub2 of sdb1 into the MBRs of all disks (except USB without OS).
Additional repair would be performed: unhide-bootmenu-10s


=================== Final advice in case of suggested repair
Please do not forget to make your BIOS boot on sdb (64.0GB) disk!


=================== User settings
The settings chosen by the user will not act on the boot.
```

---

### Post by yancek on 2017-07-13
You have Zorin installed on sdb1 (60GB drive) and have the Grub boot code in the MBR of sda, the 2TB drive with windows on it so you would need to set that to first boot priority in your BIOS.  You have 2 2TB drives which both have windows partitions so I'm not sure which it is.  Try each to see if it boots.

---

### Post by oldfred on 2017-07-13
Moved to Other OS since not Ubuntu offical flavor.

Do not run auto fix in Boot-Repair as that will install grub to every MBR. You want to keep Windows boot loader on Windows drive and only have grub on Zorin drive and BIOS set to boot that drive as default.
Use Boot-Repair's advanced mode to choose operating system and then choose drive to install grub.

---

