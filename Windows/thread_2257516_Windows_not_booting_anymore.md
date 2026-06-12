---
title: "Windows not booting anymore"
date: 2014-12-20
forum: Windows
---

### Post by henri.cazottes on 2014-12-20
Hi everyones !

I decided to install a dual boot on my windows 8.1 machine. Everything was working fine, but I had the not good looking grub booting option. I wanted to have the nice graphical windows selection to choose between windows and linux (yeah, why spending severals hours on something that useless...).
Anyway, I used easybcd, on it, I added a new entry for ubuuntu, specifying the partition "/boot" that I had created when installing ubuntu. The I applied the changes buy clicking on write mbr or something like that. And now, can't load windows... 
At least grub is launched so I can use my laptop with ubuntu, but I would appreciate to get it back :)

Here is the error displayed:
[IMG]http://i39.servimg.com/u/f39/13/84/06/30/10877310.jpg[/IMG]

What I have tried so far:
-Boot repair (recommended): didn't change it, except that I have more entries in grub
-Boot on a recovery key and run /fixmbr /fixboot: didn't change it (I don't know what I'm doing with those commands, don't thinks I do in your answers :p)

I ran the bootinfo script and I get this (quiet long sorry):

>                   Boot Info Script 0.61      [1 April 2012]


============================= Boot Info Summary: ===============================

 => Windows is installed in the MBR of /dev/sda.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sda2: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  Unknown
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sda3: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  Unknown
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /efi/Boot/bootx64.efi /efi/ubuntu/shimx64.efi /bootmgr 
                       /boot/bcd

sda4: __________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info: 
    Mounting failed:   mount: unknown filesystem type ''

sda5: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Boot/bcd /Windows/System32/winload.exe

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

sda9: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 14.10
    Boot files:        /etc/fstab

sda10: _________________________________________________________________________

    File system:       ext2
    Boot sector type:  -
    Boot sector info: 
    Operating System:  
    Boot files:        /grub/grub.cfg

sda11: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info: 

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 931,5 GiB, 1000204886016 bytes, 1953525168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1                   1 1,953,525,167 1,953,525,167  ee GPT


GUID Partition Table detected.

Partition    Start Sector    End Sector  # of Sectors System
/dev/sda1           2,048     2,050,047     2,048,000 Windows Recovery Environment (Windows)
/dev/sda2       2,050,048     2,582,527       532,480 EFI System partition
/dev/sda3       2,582,528     4,630,527     2,048,000 -
/dev/sda4       4,630,528     4,892,671       262,144 Microsoft Reserved Partition (Windows)
/dev/sda5       4,892,672 1,751,011,327 1,746,118,656 Data partition (Windows/Linux)
/dev/sda6   1,791,971,328 1,873,889,279    81,917,952 Data partition (Windows/Linux)
/dev/sda7   1,873,891,328 1,926,320,127    52,428,800 Data partition (Windows/Linux)
/dev/sda8   1,926,320,128 1,953,523,711    27,203,584 Windows Recovery Environment (Windows)
/dev/sda9   1,751,011,328 1,788,121,087    37,109,760 Data partition (Linux)
/dev/sda10  1,788,121,088 1,788,706,815       585,728 Data partition (Linux)
/dev/sda11  1,788,706,816 1,791,971,327     3,264,512 Swap partition (Linux)

"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        7814FCA014FC6294                       ntfs       WINRE_DRV
/dev/sda10       ab344828-59cf-4dcd-a71c-acaeae5860f0   ext2       
/dev/sda11       07af2aac-8036-4eb8-905b-83dbcdbfa756   swap       
/dev/sda2        C6FD-50F5                              vfat       SYSTEM_DRV
/dev/sda3        B49E-85E2                              vfat       LRS_ESP
/dev/sda4                                                          
/dev/sda5        70AC0233AC01F47E                       ntfs       Windows8_OS
/dev/sda6        DE9C2D269C2CFAA3                       ntfs       Data
/dev/sda7        68C248C4C2489868                       ntfs       LENOVO
/dev/sda8        9204A93F04A92767                       ntfs       PBR_DRV
/dev/sda9        243278cd-4879-4328-88af-52aae3ad6629   ext4       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda10       /boot                    ext2       (rw)
/dev/sda2        /boot/efi                vfat       (rw)
/dev/sda9        /                        ext4       (rw,errors=remount-ro)


=============================== sda9/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda9 during installation
UUID=243278cd-4879-4328-88af-52aae3ad6629 /               ext4    errors=remount-ro 0       1
# /boot was on /dev/sda10 during installation
UUID=ab344828-59cf-4dcd-a71c-acaeae5860f0 /boot           ext2    defaults        0       2
# /boot/efi was on /dev/sda2 during installation
#UUID=C6FD-50F5  /boot/efi       vfat    defaults        0       1
# swap was on /dev/sda11 during installation
UUID=07af2aac-8036-4eb8-905b-83dbcdbfa756 none            swap    sw              0       0
UUID=C6FD-50F5    /boot/efi    vfat    defaults    0    1
--------------------------------------------------------------------------------

=================== sda9: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)


============================= sda10/grub/grub.cfg: =============================

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
insmod part_gpt
insmod ext2
set root='hd0,gpt9'
if [ x$feature_platform_search_hint = xy ]; then
  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt9 --hint-efi=hd0,gpt9 --hint-baremetal=ahci0,gpt9  243278cd-4879-4328-88af-52aae3ad6629
else
  search --no-floppy --fs-uuid --set=root 243278cd-4879-4328-88af-52aae3ad6629
fi
    font="/usr/share/grub/unicode.pf2"
fi

if loadfont $font ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  set locale_dir=$prefix/locale
  set lang=fr_FR
  insmod gettext
fi
terminal_output gfxterm
if [ "${recordfail}" = 1 ] ; then
  set timeout=10
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
if background_color 45,51,53; then
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
menuentry 'Ubuntu' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-simple-243278cd-4879-4328-88af-52aae3ad6629' {
    recordfail
    load_video
    gfxmode $linux_gfx_mode
    insmod gzio
    insmod part_gpt
    insmod ext2
    set root='hd0,gpt10'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt10 --hint-efi=hd0,gpt10 --hint-baremetal=ahci0,gpt10  ab344828-59cf-4dcd-a71c-acaeae5860f0
    else
      search --no-floppy --fs-uuid --set=root ab344828-59cf-4dcd-a71c-acaeae5860f0
    fi
    linux    /vmlinuz-3.16.0-28-generic.efi.signed root=UUID=243278cd-4879-4328-88af-52aae3ad6629 ro  quiet splash $vt_handoff
    initrd    /initrd.img-3.16.0-28-generic
}
submenu 'Advanced options for Ubuntu' $menuentry_id_option 'gnulinux-advanced-243278cd-4879-4328-88af-52aae3ad6629' {
    menuentry 'Ubuntu, with Linux 3.16.0-28-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.16.0-28-generic-advanced-243278cd-4879-4328-88af-52aae3ad6629' {
        recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod part_gpt
        insmod ext2
        set root='hd0,gpt10'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt10 --hint-efi=hd0,gpt10 --hint-baremetal=ahci0,gpt10  ab344828-59cf-4dcd-a71c-acaeae5860f0
        else
          search --no-floppy --fs-uuid --set=root ab344828-59cf-4dcd-a71c-acaeae5860f0
        fi
        echo    'Loading Linux 3.16.0-28-generic ...'
        linux    /vmlinuz-3.16.0-28-generic.efi.signed root=UUID=243278cd-4879-4328-88af-52aae3ad6629 ro  quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /initrd.img-3.16.0-28-generic
    }
    menuentry 'Ubuntu, with Linux 3.16.0-28-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.16.0-28-generic-recovery-243278cd-4879-4328-88af-52aae3ad6629' {
        recordfail
        load_video
        insmod gzio
        insmod part_gpt
        insmod ext2
        set root='hd0,gpt10'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt10 --hint-efi=hd0,gpt10 --hint-baremetal=ahci0,gpt10  ab344828-59cf-4dcd-a71c-acaeae5860f0
        else
          search --no-floppy --fs-uuid --set=root ab344828-59cf-4dcd-a71c-acaeae5860f0
        fi
        echo    'Loading Linux 3.16.0-28-generic ...'
        linux    /vmlinuz-3.16.0-28-generic.efi.signed root=UUID=243278cd-4879-4328-88af-52aae3ad6629 ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /initrd.img-3.16.0-28-generic
    }
    menuentry 'Ubuntu, with Linux 3.16.0-23-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.16.0-23-generic-advanced-243278cd-4879-4328-88af-52aae3ad6629' {
        recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod part_gpt
        insmod ext2
        set root='hd0,gpt10'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt10 --hint-efi=hd0,gpt10 --hint-baremetal=ahci0,gpt10  ab344828-59cf-4dcd-a71c-acaeae5860f0
        else
          search --no-floppy --fs-uuid --set=root ab344828-59cf-4dcd-a71c-acaeae5860f0
        fi
        echo    'Loading Linux 3.16.0-23-generic ...'
        linux    /vmlinuz-3.16.0-23-generic root=UUID=243278cd-4879-4328-88af-52aae3ad6629 ro  quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /initrd.img-3.16.0-23-generic
    }
    menuentry 'Ubuntu, with Linux 3.16.0-23-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.16.0-23-generic-recovery-243278cd-4879-4328-88af-52aae3ad6629' {
        recordfail
        load_video
        insmod gzio
        insmod part_gpt
        insmod ext2
        set root='hd0,gpt10'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt10 --hint-efi=hd0,gpt10 --hint-baremetal=ahci0,gpt10  ab344828-59cf-4dcd-a71c-acaeae5860f0
        else
          search --no-floppy --fs-uuid --set=root ab344828-59cf-4dcd-a71c-acaeae5860f0
        fi
        echo    'Loading Linux 3.16.0-23-generic ...'
        linux    /vmlinuz-3.16.0-23-generic root=UUID=243278cd-4879-4328-88af-52aae3ad6629 ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /initrd.img-3.16.0-23-generic
    }
}

### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###

### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/25_custom ###

menuentry "efi/EFI/Boot/bootx64.efi" {
search --fs-uuid --no-floppy --set=root ab344828-59cf-4dcd-a71c-acaeae5860f0
chainloader (${root})/efi/EFI/Boot/bootx64.efi
}

menuentry "efi/EFI/ubuntu/MokManager.efi" {
search --fs-uuid --no-floppy --set=root ab344828-59cf-4dcd-a71c-acaeae5860f0
chainloader (${root})/efi/EFI/ubuntu/MokManager.efi
}

menuentry "Windows UEFI recovery bootmgfw.efi" {
search --fs-uuid --no-floppy --set=root C6FD-50F5
chainloader (${root})/EFI/Microsoft/Boot/bootmgfw.efi
}

menuentry "Windows Boot UEFI recovery" {
search --fs-uuid --no-floppy --set=root C6FD-50F5
chainloader (${root})/EFI/Boot/bootx64.efi
}

menuentry "EFI/ubuntu/MokManager.efi sda2" {
search --fs-uuid --no-floppy --set=root C6FD-50F5
chainloader (${root})/EFI/ubuntu/MokManager.efi
}

menuentry "Windows UEFI recovery LrsBootmgr.efi" {
search --fs-uuid --no-floppy --set=root B49E-85E2
chainloader (${root})/EFI/Microsoft/Boot/LrsBootmgr.efi
}

menuentry "Windows Boot UEFI recovery bootx64.efi" {
search --fs-uuid --no-floppy --set=root B49E-85E2
chainloader (${root})/EFI/Boot/bootx64.efi
}
### END /etc/grub.d/25_custom ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry 'Windows Boot Manager (on /dev/sda2)' --class windows --class os $menuentry_id_option 'osprober-efi-C6FD-50F5' {
    insmod part_gpt
    insmod fat
    set root='hd0,gpt2'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt2 --hint-efi=hd0,gpt2 --hint-baremetal=ahci0,gpt2  C6FD-50F5
    else
      search --no-floppy --fs-uuid --set=root C6FD-50F5
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

=================== sda10: Location of files loaded by Grub: ===================

           GiB - GB             File                                 Fragment(s)


======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown GPT Partiton Type
e7afbfbf4fa38a449a5b6213eb736c22
Unknown BootLoader on sda2

00000000  eb 58 90 4d 53 44 4f 53  35 2e 30 00 02 08 fe 1b  |.X.MSDOS5.0.....|
00000010  02 00 00 00 00 f8 00 00  3f 00 ff 00 00 48 1f 00  |........?....H..|
00000020  00 20 08 00 01 02 00 00  00 00 00 00 02 00 00 00  |. ..............|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  80 01 29 f5 50 fd c6 4e  4f 20 4e 41 4d 45 20 20  |..).P..NO NAME  |
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

Unknown BootLoader on sda3

00000000  eb 58 90 4d 53 44 4f 53  35 2e 30 00 02 08 6e 10  |.X.MSDOS5.0...n.|
00000010  02 00 00 00 00 f8 00 00  3f 00 ff 00 00 68 27 00  |........?....h'.|
00000020  00 40 1f 00 c9 07 00 00  00 00 00 00 02 00 00 00  |.@..............|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  80 00 29 e2 85 9e b4 4e  4f 20 4e 41 4d 45 20 20  |..)....NO NAME  |
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


=============================== StdErr Messages: ===============================

cat: /tmp/BootInfo-tkoHMcLu/Tmp_Log: Aucun fichier ou dossier de ce type
cat: /tmp/BootInfo-tkoHMcLu/Tmp_Log: Aucun fichier ou dossier de ce type




Any idea how to recussite my windows ?
Thanks in advance for your help ;)

---

