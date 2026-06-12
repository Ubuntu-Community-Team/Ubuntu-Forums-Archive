---
title: "Elementary OS and Win 8.1 dual boot problem; Won't boot back into Windows. Grub loop"
date: 2019-07-29
forum: Ubuntu/Debian BASED
---

### Post by urneer on 2019-07-29
I'm fairly new to linux, but I have dual-booted elementary OS alongside Win 8.1 and everything seemed to be working fine. However, I can't seem to boot into Windows anymore. I created a menu entry for grub called Windows (UEFI) from the problem solution here:

[https://askubuntu.com/questions/217904/unable-to-boot-into-windows-after-installing-ubuntu-how-to-fix](https://askubuntu.com/questions/217904/unable-to-boot-into-windows-after-installing-ubuntu-how-to-fix)

But when I click on it, it loops back to grub. Same issue when I tried boot-repair, although it worked initially. Any solutions for me? This is the bootinfo from boot-repair:
```
Boot Info Script 8f991e4 + Boot-Repair extra info      [Boot-Info 25oct2017]


============================= Boot Info Summary: ===============================

 => No boot loader is installed in the MBR of /dev/sda.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows 8/2012: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sda2: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows 8/2012: FAT32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /EFI/ubuntu/grub.cfg /EFI/Boot/bkpbootx64.efi 
                       /EFI/Boot/bootx64.efi /EFI/Boot/fbx64.efi 
                       /EFI/ubuntu/grubx64.efi /EFI/ubuntu/mmx64.efi 
                       /EFI/ubuntu/shimx64.efi 
                       /EFI/Microsoft/Boot/bkpbootmgfw.efi 
                       /EFI/Microsoft/Boot/bootmgfw.efi 
                       /EFI/Microsoft/Boot/bootmgr.efi 
                       /EFI/Microsoft/Boot/bootx64.efi 
                       /EFI/Microsoft/Boot/memtest.efi 
                       /boot-repair/log/20190728_171513/sda2/bootx64.efi 
                       /boot-repair/log/20190728_182818/sda2/bootx64.efi 
                       /boot-repair/log/20190728_183137/sda2/bootx64.efi 
                       /boot-repair/log/20190728_184435/sda2/bootx64.efi 
                       /boot-repair/log/20190729_155622/sda2/bootmgfw.efi 
                       /boot-repair/log/20190729_155622/sda2/bootx64.efi

sda3: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Unknown
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sda4: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows 8/2012: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Windows/System32/winload.exe

sda5: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  elementary OS 5.0 Juno
    Boot files:        /boot/grub/grub.cfg /etc/fstab

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________
Disk /dev/sda: 465.8 GiB, 500107862016 bytes, 976773168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: gpt

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1                   1   976,773,167   976,773,167  ee GPT


GUID Partition Table detected.

Partition  Attrs   Start Sector    End Sector  # of Sectors System
/dev/sda1      R          2,048       616,447       614,400 Windows Recovery Environment (Windows)
/dev/sda2               616,448       821,247       204,800 EFI System partition
/dev/sda3               821,248     1,083,391       262,144 Microsoft Reserved Partition (Windows)
/dev/sda4             1,083,392   812,933,119   811,849,728 Data partition (Windows/Linux)
/dev/sda5           812,933,120   976,771,071   163,837,952 Data partition (Linux)

Attributes: R=Required, N=No Block IO, B=Legacy BIOS Bootable, +=More bits set

"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        6286B5E886B5BCBB                       ntfs       Recovery
/dev/sda2        8AB7-5FE0                              vfat       
/dev/sda3        095E03C20FB4599B                       ntfs       
/dev/sda4        EC1CB9F11CB9B744                       ntfs       
/dev/sda5        5cde23f2-64a0-41cc-8ad8-b25efffe4859   ext4       

========================= "ls -l /dev/disk/by-id" output: ======================

total 0
lrwxrwxrwx 1 root root  9 Jul 29 17:23 ata-MATSHITADVD-RAM_UJ8D3_WQ39_113463 -> ../../sr0
lrwxrwxrwx 1 root root  9 Jul 29 17:26 ata-ST500LM012_HN-M500MBB_S2RSJ9BD308996 -> ../../sda
lrwxrwxrwx 1 root root 10 Jul 29 17:27 ata-ST500LM012_HN-M500MBB_S2RSJ9BD308996-part1 -> ../../sda1
lrwxrwxrwx 1 root root 10 Jul 29 17:26 ata-ST500LM012_HN-M500MBB_S2RSJ9BD308996-part2 -> ../../sda2
lrwxrwxrwx 1 root root 10 Jul 29 17:26 ata-ST500LM012_HN-M500MBB_S2RSJ9BD308996-part3 -> ../../sda3
lrwxrwxrwx 1 root root 10 Jul 29 17:27 ata-ST500LM012_HN-M500MBB_S2RSJ9BD308996-part4 -> ../../sda4
lrwxrwxrwx 1 root root 10 Jul 29 17:26 ata-ST500LM012_HN-M500MBB_S2RSJ9BD308996-part5 -> ../../sda5
lrwxrwxrwx 1 root root  9 Jul 29 17:26 wwn-0x50004cf209ec3c36 -> ../../sda
lrwxrwxrwx 1 root root 10 Jul 29 17:27 wwn-0x50004cf209ec3c36-part1 -> ../../sda1
lrwxrwxrwx 1 root root 10 Jul 29 17:26 wwn-0x50004cf209ec3c36-part2 -> ../../sda2
lrwxrwxrwx 1 root root 10 Jul 29 17:26 wwn-0x50004cf209ec3c36-part3 -> ../../sda3
lrwxrwxrwx 1 root root 10 Jul 29 17:27 wwn-0x50004cf209ec3c36-part4 -> ../../sda4
lrwxrwxrwx 1 root root 10 Jul 29 17:26 wwn-0x50004cf209ec3c36-part5 -> ../../sda5

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda2        /boot/efi                vfat       (rw,relatime,fmask=0022,dmask=0022,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/sda5        /                        ext4       (rw,relatime,errors=remount-ro,data=ordered)


========================== sda2/EFI/ubuntu/grub.cfg: ===========================

--------------------------------------------------------------------------------
search.fs_uuid 5cde23f2-64a0-41cc-8ad8-b25efffe4859 root hd0,gpt5 
set prefix=($root)'/boot/grub'
configfile $prefix/grub.cfg
--------------------------------------------------------------------------------

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
if [ "${next_entry}" ] ; then
   set default="${next_entry}"
   set next_entry=
   save_env next_entry
   set boot_once=true
else
   set default="Windows Boot UEFI loader"
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
insmod part_gpt
insmod ext2
set root='hd0,gpt5'
if [ x$feature_platform_search_hint = xy ]; then
  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt5 --hint-efi=hd0,gpt5 --hint-baremetal=ahci0,gpt5  5cde23f2-64a0-41cc-8ad8-b25efffe4859
else
  search --no-floppy --fs-uuid --set=root 5cde23f2-64a0-41cc-8ad8-b25efffe4859
fi
    font="/usr/share/grub/unicode.pf2"
fi

if loadfont $font ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  set locale_dir=$prefix/locale
  set lang=en_US
  insmod gettext
fi
terminal_output gfxterm
if [ "${recordfail}" = 1 ] ; then
  set timeout=10
else
  if [ x$feature_timeout_style = xy ] ; then
    set timeout_style=hidden
    set timeout=10
  # Fallback hidden-timeout code in case the timeout_style feature is
  # unavailable.
  elif sleep --interruptible 10 ; then
    set timeout=10
  fi
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/white
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
function gfxmode {
	set gfxpayload="${1}"
	if [ "${1}" = "keep" ]; then
		set vt_handoff=vt.handoff=1
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
menuentry 'elementary' --class elementary --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-simple-5cde23f2-64a0-41cc-8ad8-b25efffe4859' {
	recordfail
	load_video
	gfxmode $linux_gfx_mode
	insmod gzio
	if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
	insmod part_gpt
	insmod ext2
	set root='hd0,gpt5'
	if [ x$feature_platform_search_hint = xy ]; then
	  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt5 --hint-efi=hd0,gpt5 --hint-baremetal=ahci0,gpt5  5cde23f2-64a0-41cc-8ad8-b25efffe4859
	else
	  search --no-floppy --fs-uuid --set=root 5cde23f2-64a0-41cc-8ad8-b25efffe4859
	fi
        linux	/boot/vmlinuz-4.15.0-55-generic root=UUID=5cde23f2-64a0-41cc-8ad8-b25efffe4859 ro  quiet splash $vt_handoff
	initrd	/boot/initrd.img-4.15.0-55-generic
}
submenu 'Advanced options for elementary' $menuentry_id_option 'gnulinux-advanced-5cde23f2-64a0-41cc-8ad8-b25efffe4859' {
	menuentry 'elementary, with Linux 4.15.0-55-generic' --class elementary --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-4.15.0-55-generic-advanced-5cde23f2-64a0-41cc-8ad8-b25efffe4859' {
		recordfail
		load_video
		gfxmode $linux_gfx_mode
		insmod gzio
		if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
		insmod part_gpt
		insmod ext2
		set root='hd0,gpt5'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt5 --hint-efi=hd0,gpt5 --hint-baremetal=ahci0,gpt5  5cde23f2-64a0-41cc-8ad8-b25efffe4859
		else
		  search --no-floppy --fs-uuid --set=root 5cde23f2-64a0-41cc-8ad8-b25efffe4859
		fi
		echo	'Loading Linux 4.15.0-55-generic ...'
	        linux	/boot/vmlinuz-4.15.0-55-generic root=UUID=5cde23f2-64a0-41cc-8ad8-b25efffe4859 ro  quiet splash $vt_handoff
		echo	'Loading initial ramdisk ...'
		initrd	/boot/initrd.img-4.15.0-55-generic
	}
	menuentry 'elementary, with Linux 4.15.0-55-generic (recovery mode)' --class elementary --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-4.15.0-55-generic-recovery-5cde23f2-64a0-41cc-8ad8-b25efffe4859' {
		recordfail
		load_video
		insmod gzio
		if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
		insmod part_gpt
		insmod ext2
		set root='hd0,gpt5'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt5 --hint-efi=hd0,gpt5 --hint-baremetal=ahci0,gpt5  5cde23f2-64a0-41cc-8ad8-b25efffe4859
		else
		  search --no-floppy --fs-uuid --set=root 5cde23f2-64a0-41cc-8ad8-b25efffe4859
		fi
		echo	'Loading Linux 4.15.0-55-generic ...'
	        linux	/boot/vmlinuz-4.15.0-55-generic root=UUID=5cde23f2-64a0-41cc-8ad8-b25efffe4859 ro recovery nomodeset 
		echo	'Loading initial ramdisk ...'
		initrd	/boot/initrd.img-4.15.0-55-generic
	}
	menuentry 'elementary, with Linux 4.15.0-36-generic' --class elementary --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-4.15.0-36-generic-advanced-5cde23f2-64a0-41cc-8ad8-b25efffe4859' {
		recordfail
		load_video
		gfxmode $linux_gfx_mode
		insmod gzio
		if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
		insmod part_gpt
		insmod ext2
		set root='hd0,gpt5'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt5 --hint-efi=hd0,gpt5 --hint-baremetal=ahci0,gpt5  5cde23f2-64a0-41cc-8ad8-b25efffe4859
		else
		  search --no-floppy --fs-uuid --set=root 5cde23f2-64a0-41cc-8ad8-b25efffe4859
		fi
		echo	'Loading Linux 4.15.0-36-generic ...'
	        linux	/boot/vmlinuz-4.15.0-36-generic root=UUID=5cde23f2-64a0-41cc-8ad8-b25efffe4859 ro  quiet splash $vt_handoff
		echo	'Loading initial ramdisk ...'
		initrd	/boot/initrd.img-4.15.0-36-generic
	}
	menuentry 'elementary, with Linux 4.15.0-36-generic (recovery mode)' --class elementary --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-4.15.0-36-generic-recovery-5cde23f2-64a0-41cc-8ad8-b25efffe4859' {
		recordfail
		load_video
		insmod gzio
		if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
		insmod part_gpt
		insmod ext2
		set root='hd0,gpt5'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt5 --hint-efi=hd0,gpt5 --hint-baremetal=ahci0,gpt5  5cde23f2-64a0-41cc-8ad8-b25efffe4859
		else
		  search --no-floppy --fs-uuid --set=root 5cde23f2-64a0-41cc-8ad8-b25efffe4859
		fi
		echo	'Loading Linux 4.15.0-36-generic ...'
	        linux	/boot/vmlinuz-4.15.0-36-generic root=UUID=5cde23f2-64a0-41cc-8ad8-b25efffe4859 ro recovery nomodeset 
		echo	'Loading initial ramdisk ...'
		initrd	/boot/initrd.img-4.15.0-36-generic
	}
}

### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###

### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/25_custom ###

menuentry "Windows UEFI bkpbootmgfw.efi" {
search --fs-uuid --no-floppy --set=root 8AB7-5FE0
chainloader (${root})/EFI/Microsoft/Boot/bkpbootmgfw.efi
}

menuentry "Windows Boot UEFI loader" {
search --fs-uuid --no-floppy --set=root 8AB7-5FE0
chainloader (${root})/EFI/Boot/bkpbootx64.efi
}

menuentry "Windows Boot UEFI fbx64.efi" {
search --fs-uuid --no-floppy --set=root 8AB7-5FE0
chainloader (${root})/EFI/Boot/fbx64.efi
}

menuentry "EFI/ubuntu/mmx64.efi" {
search --fs-uuid --no-floppy --set=root 8AB7-5FE0
chainloader (${root})/EFI/ubuntu/mmx64.efi
}
### END /etc/grub.d/25_custom ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry 'Windows Boot Manager (on /dev/sda2)' --class windows --class os $menuentry_id_option 'osprober-efi-8AB7-5FE0' {
	insmod part_gpt
	insmod fat
	set root='hd0,gpt2'
	if [ x$feature_platform_search_hint = xy ]; then
	  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt2 --hint-efi=hd0,gpt2 --hint-baremetal=ahci0,gpt2  8AB7-5FE0
	else
	  search --no-floppy --fs-uuid --set=root 8AB7-5FE0
	fi
	chainloader /EFI/Microsoft/Boot/bootmgfw.efi
}
set timeout_style=menu
if [ "${timeout}" = 0 ]; then
  set timeout=10
fi
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/30_uefi-firmware ###
menuentry 'System setup' $menuentry_id_option 'uefi-firmware' {
	fwsetup
}
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

=============================== sda5/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda5 during installation
UUID=5cde23f2-64a0-41cc-8ad8-b25efffe4859 /               ext4    errors=remount-ro 0       1
# /boot/efi was on /dev/sda2 during installation
#UUID=8AB7-5FE0  /boot/efi       vfat    umask=0077      0       1
/swapfile                                 none            swap    sw              0       0
UUID=8AB7-5FE0	/boot/efi	vfat	defaults	0	1
--------------------------------------------------------------------------------

=================== sda5: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 419.853839874 = 450.814627840  boot/grub/grub.cfg                             1
 399.774829865 = 429.254955008  boot/vmlinuz-4.15.0-36-generic                 1
 393.410064697 = 422.420840448  boot/vmlinuz-4.15.0-55-generic                 1
 393.410064697 = 422.420840448  vmlinuz                                        1
 399.774829865 = 429.254955008  vmlinuz.old                                    1
 390.478191376 = 419.272765440  boot/initrd.img-4.15.0-36-generic              3
 390.616687775 = 419.421474816  boot/initrd.img-4.15.0-55-generic              3
 390.616687775 = 419.421474816  initrd.img                                     3
 390.478191376 = 419.272765440  initrd.img.old                                 3

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda3

00000000  eb 52 90 4e 54 46 53 20  20 20 20 00 02 08 00 00  |.R.NTFS    .....|
00000010  00 00 00 00 00 f8 00 00  3f 00 ff 00 00 88 0c 00  |........?.......|
00000020  00 00 00 00 80 00 80 00  ff ff 03 00 00 00 00 00  |................|
00000030  04 00 00 00 00 00 00 00  ff 3f 00 00 00 00 00 00  |.........?......|
00000040  f6 00 00 00 01 00 00 00  9b 59 b4 0f c2 03 5e 09  |.........Y....^.|
00000050  00 00 00 00 0e 1f be 71  7c ac 22 c0 74 0b 56 b4  |.......q|.".t.V.|
00000060  0e bb 07 00 cd 10 5e eb  f0 32 e4 cd 16 cd 19 eb  |......^..2......|
00000070  fe 54 68 69 73 20 69 73  20 6e 6f 74 20 61 20 62  |.This is not a b|
00000080  6f 6f 74 61 62 6c 65 20  64 69 73 6b 2e 20 50 6c  |ootable disk. Pl|
00000090  65 61 73 65 20 69 6e 73  65 72 74 20 61 20 62 6f  |ease insert a bo|
000000a0  6f 74 61 62 6c 65 20 66  6c 6f 70 70 79 20 61 6e  |otable floppy an|
000000b0  64 0d 0a 70 72 65 73 73  20 61 6e 79 20 6b 65 79  |d..press any key|
000000c0  20 74 6f 20 74 72 79 20  61 67 61 69 6e 20 2e 2e  | to try again ..|
000000d0  2e 20 0d 0a 00 00 00 00  00 00 00 00 00 00 00 00  |. ..............|
000000e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=============================== StdErr Messages: ===============================

File descriptor 9 (/proc/3144/mountinfo) leaked on lvs invocation. Parent PID 12964: bash
File descriptor 63 (pipe:[49237]) leaked on lvs invocation. Parent PID 12964: bash

ADDITIONAL INFORMATION :
=================== log of boot-repair 20190729_1726 ===================
boot-repair version : 4ppa65
boot-sav version : 4ppa65
boot-sav-extra version : 4ppa65
glade2script version : 3.2.3~ppa4
File descriptor 9 (/proc/3144/mountinfo) leaked on lvs invocation. Parent PID 4980: /bin/sh
boot-repair is executed in installed-session (elementary OS 5.0 Juno, juno, elementary, x86_64)
CPU op-mode(s):      32-bit, 64-bit
BOOT_IMAGE=/boot/vmlinuz-4.15.0-55-generic root=UUID=5cde23f2-64a0-41cc-8ad8-b25efffe4859 ro quiet splash vt.handoff=1
The disk contains an unclean file system (0, 0).
Metadata kept in Windows cache, refused to mount.
Falling back to read-only mount because the NTFS partition is in an
unsafe state. Please resume and shutdown Windows fully (no hibernation
or fast restarting.)
Windows is hibernated, refused to mount.
The disk contains an unclean file system (0, 0).
Metadata kept in Windows cache, refused to mount.
Falling back to read-only mount because the NTFS partition is in an
unsafe state. Please resume and shutdown Windows fully (no hibernation
or fast restarting.)

=================== os-prober:
/dev/sda5:The OS now in use - elementary OS 5.0 Juno CurrentSession:linux
/dev/sda2@/EFI/Microsoft/Boot/bootmgfw.efi:Windows Boot Manager:Windows:efi

=================== blkid:
/dev/sda1: LABEL="Recovery" UUID="6286B5E886B5BCBB" TYPE="ntfs" PARTLABEL="Basic data partition" PARTUUID="a0660785-a8c0-4adb-9fbd-487c17896ccd"
/dev/sda2: UUID="8AB7-5FE0" TYPE="vfat" PARTLABEL="EFI system partition" PARTUUID="ca9d6755-612c-48fa-b603-ad693b1b7eaa"
/dev/sda3: UUID="095E03C20FB4599B" TYPE="ntfs" PTTYPE="dos" PARTLABEL="Microsoft reserved partition" PARTUUID="46a39675-a8e6-487d-b30f-ee1123062087"
/dev/sda4: UUID="EC1CB9F11CB9B744" TYPE="ntfs" PARTLABEL="Basic data partition" PARTUUID="0e1e1595-7fe0-43b1-845a-54acf50d83a6"
/dev/sda5: UUID="5cde23f2-64a0-41cc-8ad8-b25efffe4859" TYPE="ext4" PARTUUID="f6013299-57e3-41ad-b22c-b4b9fbc6fbb5"


1 disks with OS, 2 OS : 1 Linux, 0 MacOS, 1 Windows, 0 unknown type OS.

Windows not detected by os-prober on sda4.

=================== /etc/grub.d/ :
drwxr-xr-x  2 root root    4096 Jul 29 16:01 grub.d
total 80
-rwxr-xr-x 1 root root 10046 Apr  4 13:33 00_header
-rwxr-xr-x 1 root root  6276 Oct 11  2018 05_debian_theme
-rwxr-xr-x 1 root root 12683 Oct 11  2018 10_linux
-rwxr-xr-x 1 root root 11298 Oct 11  2018 20_linux_xen
-rwxr-xr-x 1 root root   587 Jul 29 16:01 25_custom
-rwxr-xr-x 1 root root 12059 Oct 11  2018 30_os-prober
-rwxr-xr-x 1 root root  1418 Oct 11  2018 30_uefi-firmware
-rwxr-xr-x 1 root root   214 Oct 11  2018 40_custom
-rwxr-xr-x 1 root root   216 Oct 11  2018 41_custom
-rw-r--r-- 1 root root   483 Oct 11  2018 README




=================== /etc/default/grub :

# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT="Windows Boot UEFI loader"
GRUB_TIMEOUT_STYLE=hidden
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

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



/boot/efi detected in the fstab of sda5: UUID=8AB7-5FE0	 (sda2)
Presence of EFI/Microsoft file detected: /boot/efi/EFI/Microsoft/Boot/bkpbootmgfw.efi
Presence of EFI/Microsoft file detected: /boot/efi/EFI/Microsoft/Boot/bootmgfw.efi
Presence of EFI/Microsoft file detected: /boot/efi/EFI/Microsoft/Boot/bootx64.efi
Presence of EFI/Boot file detected: /boot/efi/EFI/Boot/bkpbootx64.efi
Presence of EFI/Boot file detected: /boot/efi/EFI/Boot/bootx64.efi
Presence of EFI/Boot file detected: /boot/efi/EFI/Boot/fbx64.efi
Presence of bkp file detected: /boot/efi/EFI/Boot/bkpbootx64.efi
Presence of winbkp file detected: /boot/efi/EFI/Microsoft/Boot/bkpbootmgfw.efi
/usr/share/boot-sav/bs-cmd_terminal.sh: line 179: warning: command substitution: ignored null byte in input

=================== efibootmgr -v
BootCurrent: 0003
Timeout: 0 seconds
BootOrder: 0003,0000,0004,0005,2003,2001,2002
Boot0000* ubuntu	HD(2,GPT,ca9d6755-612c-48fa-b603-ad693b1b7eaa,0x96800,0x32000)/File(EFIubuntushimx64.efi)
Boot0001* EFI Network 0 for IPv4 (3C-07-71-6F-09-D5) 	PciRoot(0x0)/Pci(0x1c,0x2)/Pci(0x0,0x0)/MAC(3c07716f09d5,0)/IPv4(0.0.0.00.0.0.0,0,0)RC
Boot0002* EFI Network 0 for IPv6 (3C-07-71-6F-09-D5) 	PciRoot(0x0)/Pci(0x1c,0x2)/Pci(0x0,0x0)/MAC(3c07716f09d5,0)/IPv6([::]:<->[::]:,0,0)RC
Boot0003* Windows Boot Manager	HD(2,GPT,ca9d6755-612c-48fa-b603-ad693b1b7eaa,0x96800,0x32000)/File(EFIubuntushimx64.efi)WINDOWS.........x...B.C.D.O.B.J.E.C.T.=.{.9.d.e.a.8.6.2.c.-.5.c.d.d.-.4.e.7.0.-.a.c.c.1.-.f.3.2.b.3.4.4.d.4.7.9.5.}...a................
Boot0004* Windows Boot Manager	HD(2,GPT,ca9d6755-612c-48fa-b603-ad693b1b7eaa,0x96800,0x32000)/File(EFIMicrosoftBootbootmgfw.efi)RC
Boot0005* Ubuntu	HD(2,GPT,ca9d6755-612c-48fa-b603-ad693b1b7eaa,0x96800,0x32000)/File(EFIubuntugrubx64.efi)RC
Boot2001* EFI USB Device	RC
Boot2002* EFI DVD/CDROM	RC
Boot2003* EFI Network	RC

=================== UEFI/Legacy mode:
BIOS is EFI-compatible, and is setup in EFI-mode for this installed-session.
SecureBoot disabled. (maybe sec-boot, Please report this message to [email]boot.repair@gmail.com[/email])


=================== PARTITIONS & DISKS:
sda5	: sda,	not-sepboot,	grubenv-ok	grub2,	signed grub-pc grub-efi ,	update-grub,	64,	with-boot,	is-os,	not--efi--part,	fstab-without-boot,	fstab-has-goodEFI,	no-nt,	no-winload,	no-recov-nor-hid,	no-bmgr,	notwinboot,	apt-get,	grub-install,	with--usr,	fstab-without-usr,	not-sep-usr,	standard,	farbios,	notbiosboot, .
sda1	: sda,	not-sepboot,	no-grubenv	nogrub,	no-docgrub,	no-update-grub,	32,	no-boot,	no-os,	not--efi--part,	part-has-no-fstab,	part-has-no-fstab,	no-nt,	no-winload,	recovery-or-hidden,	no-bmgr,	notwinboot,	nopakmgr,	nogrubinstall,	no---usr,	part-has-no-fstab,	not-sep-usr,	standard,	not-far,	notbiosboot, /mnt/boot-sav/sda1.
sda2	: sda,	not-sepboot,	no-grubenv	nogrub,	no-docgrub,	no-update-grub,	32,	no-boot,	is-os,	is-correct-EFI,	part-has-no-fstab,	part-has-no-fstab,	no-nt,	no-winload,	no-recov-nor-hid,	no-bmgr,	notwinboot,	nopakmgr,	nogrubinstall,	no---usr,	part-has-no-fstab,	not-sep-usr,	standard,	not-far,	notbiosboot, /boot/efi.
sda4	: sda,	not-sepboot,	no-grubenv	nogrub,	no-docgrub,	no-update-grub,	32,	no-boot,	is-os,	not--efi--part,	part-has-no-fstab,	part-has-no-fstab,	no-nt,	haswinload,	no-recov-nor-hid,	bootmgr,	notwinboot,	nopakmgr,	nogrubinstall,	no---usr,	part-has-no-fstab,	not-sep-usr,	standard,	farbios,	notbiosboot, /mnt/boot-sav/sda4.

sda	: GPT,	no-BIOS_boot,	has-correctEFI, 	not-usb,	not-mmc, has-os,	2048 sectors * 512 bytes


=================== parted -lm:

BYT;
/dev/sda:500GB:scsi:512:4096:gpt:ATA ST500LM012 HN-M5:;
1:1049kB:316MB:315MB:ntfs:Basic data partition:hidden, diag;
2:316MB:420MB:105MB:fat32:EFI system partition:boot, esp;
3:420MB:555MB:134MB:ntfs:Microsoft reserved partition:msftres;
4:555MB:416GB:416GB:ntfs:Basic data partition:msftdata;
5:416GB:500GB:83.9GB:ext4::;

=================== lsblk:
KNAME TYPE FSTYPE   SIZE LABEL
sda   disk        465.8G
sda1  part ntfs     300M Recovery
sda2  part vfat     100M
sda3  part ntfs     128M
sda4  part ntfs   387.1G
sda5  part ext4    78.1G
sr0   rom          1024M

KNAME ROTA RO RM STATE   MOUNTPOINT
sda      1  0  0 running
sda1     1  0  0         /mnt/boot-sav/sda1
sda2     1  0  0         /boot/efi
sda3     1  0  0
sda4     1  0  0         /mnt/boot-sav/sda4
sda5     1  0  0         /
sr0      1  0  1 running


=================== mount:
sysfs on /sys type sysfs (rw,nosuid,nodev,noexec,relatime)
proc on /proc type proc (rw,nosuid,nodev,noexec,relatime)
udev on /dev type devtmpfs (rw,nosuid,relatime,size=3989688k,nr_inodes=997422,mode=755)
devpts on /dev/pts type devpts (rw,nosuid,noexec,relatime,gid=5,mode=620,ptmxmode=000)
tmpfs on /run type tmpfs (rw,nosuid,noexec,relatime,size=804388k,mode=755)
/dev/sda5 on / type ext4 (rw,relatime,errors=remount-ro,data=ordered)
securityfs on /sys/kernel/security type securityfs (rw,nosuid,nodev,noexec,relatime)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
tmpfs on /run/lock type tmpfs (rw,nosuid,nodev,noexec,relatime,size=5120k)
tmpfs on /sys/fs/cgroup type tmpfs (ro,nosuid,nodev,noexec,mode=755)
cgroup on /sys/fs/cgroup/unified type cgroup2 (rw,nosuid,nodev,noexec,relatime,nsdelegate)
cgroup on /sys/fs/cgroup/systemd type cgroup (rw,nosuid,nodev,noexec,relatime,xattr,name=systemd)
pstore on /sys/fs/pstore type pstore (rw,nosuid,nodev,noexec,relatime)
efivarfs on /sys/firmware/efi/efivars type efivarfs (rw,nosuid,nodev,noexec,relatime)
cgroup on /sys/fs/cgroup/memory type cgroup (rw,nosuid,nodev,noexec,relatime,memory)
cgroup on /sys/fs/cgroup/cpu,cpuacct type cgroup (rw,nosuid,nodev,noexec,relatime,cpu,cpuacct)
cgroup on /sys/fs/cgroup/freezer type cgroup (rw,nosuid,nodev,noexec,relatime,freezer)
cgroup on /sys/fs/cgroup/perf_event type cgroup (rw,nosuid,nodev,noexec,relatime,perf_event)
cgroup on /sys/fs/cgroup/rdma type cgroup (rw,nosuid,nodev,noexec,relatime,rdma)
cgroup on /sys/fs/cgroup/net_cls,net_prio type cgroup (rw,nosuid,nodev,noexec,relatime,net_cls,net_prio)
cgroup on /sys/fs/cgroup/cpuset type cgroup (rw,nosuid,nodev,noexec,relatime,cpuset)
cgroup on /sys/fs/cgroup/devices type cgroup (rw,nosuid,nodev,noexec,relatime,devices)
cgroup on /sys/fs/cgroup/pids type cgroup (rw,nosuid,nodev,noexec,relatime,pids)
cgroup on /sys/fs/cgroup/hugetlb type cgroup (rw,nosuid,nodev,noexec,relatime,hugetlb)
cgroup on /sys/fs/cgroup/blkio type cgroup (rw,nosuid,nodev,noexec,relatime,blkio)
systemd-1 on /proc/sys/fs/binfmt_misc type autofs (rw,relatime,fd=45,pgrp=1,timeout=0,minproto=5,maxproto=5,direct,pipe_ino=16193)
mqueue on /dev/mqueue type mqueue (rw,relatime)
debugfs on /sys/kernel/debug type debugfs (rw,relatime)
hugetlbfs on /dev/hugepages type hugetlbfs (rw,relatime,pagesize=2M)
fusectl on /sys/fs/fuse/connections type fusectl (rw,relatime)
configfs on /sys/kernel/config type configfs (rw,relatime)
/dev/sda2 on /boot/efi type vfat (rw,relatime,fmask=0022,dmask=0022,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
tmpfs on /run/user/1000 type tmpfs (rw,nosuid,nodev,relatime,size=804384k,mode=700,uid=1000,gid=1000)
gvfsd-fuse on /run/user/1000/gvfs type fuse.gvfsd-fuse (rw,nosuid,nodev,relatime,user_id=1000,group_id=1000)
/dev/sda1 on /mnt/boot-sav/sda1 type fuseblk (ro,relatime,user_id=0,group_id=0,allow_other,blksize=4096)
/dev/sda4 on /mnt/boot-sav/sda4 type fuseblk (ro,relatime,user_id=0,group_id=0,allow_other,blksize=4096)


=================== ls:
/sys/block/sda (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range hidden holders inflight integrity power queue range removable ro sda1 sda2 sda3 sda4 sda5 size slaves stat subsystem trace uevent
/sys/block/sr0 (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range hidden holders inflight integrity power queue range removable ro size slaves stat subsystem trace uevent
/dev (filtered):  autofs block bsg btrfs-control bus cdrom cdrw char console core cpu cpu_dma_latency cuse disk dri drm_dp_aux0 dvd dvdrw ecryptfs fb0 fd full fuse hidraw0 hidraw1 hpet hugepages hwrng i2c-0 i2c-1 i2c-2 i2c-3 i2c-4 i2c-5 i2c-6 initctl input kmsg kvm lightnvm log mapper mcelog media0 mei0 mem memory_bandwidth mqueue net network_latency network_throughput null port ppp psaux ptmx pts random rfkill sda sda1 sda2 sda3 sda4 sda5 sg0 sg1 shm snapshot snd sr0 stderr stdin stdout uhid uinput urandom usb userio v4l vfio vga_arbiter vhci vhost-net vhost-vsock video0 zero
ls /dev/mapper:  control

=================== hexdump -n512 -C /dev/sda1
00000000  eb 52 90 4e 54 46 53 20  20 20 20 00 02 08 00 00  |.R.NTFS    .....|
00000010  00 00 00 00 00 f8 00 00  3f 00 ff 00 00 08 00 00  |........?.......|
00000020  00 00 00 00 80 00 80 00  ff 5f 09 00 00 00 00 00  |........._......|
00000030  00 64 00 00 00 00 00 00  02 00 00 00 00 00 00 00  |.d..............|
00000040  f6 00 00 00 01 00 00 00  bb bc b5 86 e8 b5 86 62  |...............b|
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

=================== hexdump -n512 -C /dev/sda2
00000000  eb 58 90 4d 53 44 4f 53  35 2e 30 00 02 02 fe 19  |.X.MSDOS5.0.....|
00000010  02 00 00 00 00 f8 00 00  3f 00 ff 00 00 68 09 00  |........?....h..|
00000020  00 20 03 00 01 03 00 00  00 00 00 00 02 00 00 00  |. ..............|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  80 01 29 e0 5f b7 8a 4e  4f 20 4e 41 4d 45 20 20  |..)._..NO NAME  |
00000050  20 20 46 41 54 33 32 20  20 20 33 c9 8e d1 bc f4  |  FAT32   3.....|
00000060  7b 8e c1 8e d9 bd 00 7c  88 56 40 88 4e 02 8a 56  |{......|.V@.N..V|
00000070  40 b4 41 bb aa 55 cd 13  72 10 81 fb 55 aa 75 0a  |@.A..U..r...U.u.|
00000080  f6 c1 01 74 05 fe 46 02  eb 2d 8a 56 40 b4 08 cd  |...t..F..-.V@...|
00000090  13 73 05 b9 ff ff 8a f1  66 0f b6 c6 40 66 0f b6  |.s......f...@f..|
000000a0  d1 80 e2 3f f7 e2 86 cd  c0 ed 06 41 66 0f b7 c9  |...?.......Af...|
000000b0  66 f7 e1 66 89 46 f8 83  7e 16 00 75 39 83 7e 2a  |f..f.F..~..u9.~*|
000000c0  00 77 33 66 8b 46 1c 66  83 c0 0c bb 00 80 b9 01  |.w3f.F.f........|
000000d0  00 e8 2c 00 e9 a8 03 a1  f8 7d 80 c4 7c 8b f0 ac  |..,......}..|...|
000000e0  84 c0 74 17 3c ff 74 09  b4 0e bb 07 00 cd 10 eb  |..t.<.t.........|
000000f0  ee a1 fa 7d eb e4 a1 7d  80 eb df 98 cd 16 cd 19  |...}...}........|
00000100  66 60 80 7e 02 00 0f 84  20 00 66 6a 00 66 50 06  |f`.~.... .fj.fP.|
00000110  53 66 68 10 00 01 00 b4  42 8a 56 40 8b f4 cd 13  |Sfh.....B.V@....|
00000120  66 58 66 58 66 58 66 58  eb 33 66 3b 46 f8 72 03  |fXfXfXfX.3f;F.r.|
00000130  f9 eb 2a 66 33 d2 66 0f  b7 4e 18 66 f7 f1 fe c2  |..*f3.f..N.f....|
00000140  8a ca 66 8b d0 66 c1 ea  10 f7 76 1a 86 d6 8a 56  |..f..f....v....V|
00000150  40 8a e8 c0 e4 06 0a cc  b8 01 02 cd 13 66 61 0f  |@............fa.|
00000160  82 74 ff 81 c3 00 02 66  40 49 75 94 c3 42 4f 4f  |.t.....f@Iu..BOO|
00000170  54 4d 47 52 20 20 20 20  00 00 00 00 00 00 00 00  |TMGR    ........|
00000180  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001a0  00 00 00 00 00 00 00 00  00 00 00 00 0d 0a 44 69  |..............Di|
000001b0  73 6b 20 65 72 72 6f 72  ff 0d 0a 50 72 65 73 73  |sk error...Press|
000001c0  20 61 6e 79 20 6b 65 79  20 74 6f 20 72 65 73 74  | any key to rest|
000001d0  61 72 74 0d 0a 00 00 00  00 00 00 00 00 00 00 00  |art.............|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  ac 01 b9 01 00 00 55 aa  |..............U.|
00000200

=================== hexdump -n512 -C /dev/sda4
00000000  eb 52 90 4e 54 46 53 20  20 20 20 00 02 08 00 00  |.R.NTFS    .....|
00000010  00 00 00 00 00 f8 00 00  3f 00 ff 00 00 88 10 00  |........?.......|
00000020  00 00 00 00 80 00 80 00  ff d7 63 30 00 00 00 00  |..........c0....|
00000030  00 00 0c 00 00 00 00 00  02 00 00 00 00 00 00 00  |................|
00000040  f6 00 00 00 01 00 00 00  44 b7 b9 1c f1 b9 1c ec  |........D.......|
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
udev           devtmpfs  3.9G     0  3.9G   0% /dev
tmpfs          tmpfs     786M  1.6M  785M   1% /run
/dev/sda5      ext4       77G  8.0G   65G  11% /
tmpfs          tmpfs     3.9G   25M  3.9G   1% /dev/shm
tmpfs          tmpfs     5.0M  4.0K  5.0M   1% /run/lock
tmpfs          tmpfs     3.9G     0  3.9G   0% /sys/fs/cgroup
/dev/sda2      vfat       96M   44M   53M  46% /boot/efi
tmpfs          tmpfs     786M   64K  786M   1% /run/user/1000
/dev/sda1      fuseblk   300M   12M  289M   4% /mnt/boot-sav/sda1
/dev/sda4      fuseblk   388G   30G  358G   8% /mnt/boot-sav/sda4

=================== fdisk -l:
Disk /dev/sda: 465.8 GiB, 500107862016 bytes, 976773168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: gpt
Disk identifier: 61E5AC4E-9CF9-40E1-BEB0-B626C6774A4E

Device         Start       End   Sectors   Size Type
/dev/sda1       2048    616447    614400   300M Windows recovery environment
/dev/sda2     616448    821247    204800   100M EFI System
/dev/sda3     821248   1083391    262144   128M Microsoft reserved
/dev/sda4    1083392 812933119 811849728 387.1G Microsoft basic data
/dev/sda5  812933120 976771071 163837952  78.1G Linux filesystem




=================== Suggested repair
The default repair of the Boot-Repair utility would reinstall the grub-efi-amd64-signed of sda5, using the following options:        sda2/boot/efi,
Additional repair would be performed: unhide-bootmenu-10s   fix-windows-boot use-standard-efi-file  restore-efi-backups


=================== Final advice in case of suggested repair
Please do not forget to make your BIOS boot on sda2/efi/.../grub*.efi file!

If your computer reboots directly into Windows, try to change the boot order in your BIOS.
If your BIOS does not allow to change the boot order, change the default boot entry of the Windows bootloader.
For example you can boot into Windows, then type the following command in an admin command prompt:
bcdedit /set {bootmgr} path \EFI\...\grub*.efi


=================== User settings
The settings chosen by the user will not act on the boot.


```


paste2.org ko ([http://paste2.org/](http://paste2.org/))

---

### Post by wildmanne39 on 2019-07-29
Hello and welcome to the forum.

*Thread moved to **Ubuntu/Debian BASED a more appropriate sub-forum**.*

Please use code tags - if you are using New Reply button - highlight text and use the # button in the text box header. 
 
If using Quick Reply then [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.

---

### Post by oldfred on 2019-07-29
Do not do fixes from 2012.
That was a work around for some very broken UEFI that only booted Windows. Now many other work arounds and most UEFI will boot an Ubuntu entry.

You show this, scroll right to see that shimx64.efi under Windows :
```
Boot0003* Windows Boot Manager    HD(2,GPT,ca9d6755-612c-48fa-b603-ad693b1b7eaa,0x96800,0x32000)/File([COLOR=#ff0000]EFIubuntushimx64.efi[/COLOR])WINDOWS.........x...B.C.D.O.B.J.E.C.T.=.{.9.d.e.a.8.6.2.c.-.5.c.d.d.-.4.e.7.0.-.a.c.c.1.-.f.3.2.b.3.4.4.d.4.7.9.5.}...a................
Boot0004* Windows Boot Manager    HD(2,GPT,ca9d6755-612c-48fa-b603-ad693b1b7eaa,0x96800,0x32000)/File(EFIMicrosoftBootbootmgfw.efi)RC 
    
```

Delete entry 0003 as that is using the "Windows Boot Manager" entry to boot Ubuntu/grub.
Second Windows entry should still boot Windows.

       sudo efibootmgr -v
The "-v" option displays all the entries so you can confirm you're deleting the right one, and then you use the combination of "-b ####" (to specify the entry) and "-B" (to delete it). Examples #5 is delete:, with Ubuntu you need sudo, others must be at root. some need all 4 hex chars, others only need significant digits
sudo efibootmgr -b XXXX -B
man efibootmgr 

Grub only boots working Windows and you must then have Windows fast start up off.
       Fast Start up off (always on hibernation), note that Windows turns this back on with updates
[http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472](http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472)
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)
[http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html](http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html)

---

### Post by urneer on 2019-07-30
No problem. Sorry about that. I'll use code tags next time.

---

### Post by urneer on 2019-07-30
I still couldn't get it to boot Windows after deleting 0003. When I try booting to "Windows Boot UEFI loader" in grub, it says "start_image() returned Not Found". I'm not sure what to do.

---

### Post by oldfred on 2019-07-30
Grub only boots working Windows. And that also means Windows hibernation or fast start up must be off. So grub entry will not work as Boot-Repair says this which means fast start up is still on.

      >  The disk contains an unclean file system (0, 0).
Metadata kept in Windows cache, refused to mount.
Falling back to read-only mount because the NTFS partition is in an
unsafe state. Please resume and shutdown Windows fully (no hibernation
or fast restarting.) 

    



But you should be able to directly boot Windows from UEFI boot entry, that is the 0004 entry (f10 or f12 on many systems).
You may need to go into safe mode & run repairs.

---

