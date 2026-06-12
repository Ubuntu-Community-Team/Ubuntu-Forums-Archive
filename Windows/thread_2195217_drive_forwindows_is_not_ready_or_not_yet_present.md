---
title: "drive for/windows is not ready or not yet present?"
date: 2013-12-22
forum: Windows
---

### Post by corey6 on 2013-12-22
I have run into an interesting problem after doing a fresh install on a tri boot setup.  I installed windows 7, Mint 13, and Ultimate edition 3.4 lite in that order.  I also have a seperate ntfs partition I created to put data on (photos and music files) to share between os's.  I get a strange error only when booting the mint os and can't figure out how to fix it.  it states "The disk drive for /windows is not yet ready or not present.  Continue to wait, or press S to skip or M for manual recovery"

---

### Post by QIII on 2013-12-22
*Moved to **Other OS/Distro Support***

---

### Post by oldfred on 2013-12-23
Probably easiest just to post link to BootInfo report as it will output all the relevant partition, UUID and mount info, plus a lot of other boot related.

       Post the link to the Create BootInfo report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

---

### Post by corey6 on 2013-12-23
I'm thinking the problem is with sda5 which is a ntfs partition that I created to share data between os's.  I originally created it using the partition manager on one of the linux distros and thought I only had the option of FAT32 which I did and then later formatted it in Windows as ntfs

Boot info script:
```
Boot Info Script 0.61      [1 April 2012]


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos8)/boot/grub on this drive.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /boot.ini /bootmgr /Boot/bcd /ntldr /NTDETECT.COM

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /Windows/System32/winload.exe

sda3: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info: 

sda5: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 2. But according to the info from fdisk, 
                       sda5 starts at sector 271308800.
    Operating System:  
    Boot files:        

sda6: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info: 

sda7: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Linux Mint 13 Maya
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda8: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ultimate Edition 3.4 LTS
    Boot files:        /boot/grub/grub.cfg /etc/fstab 
                       /boot/extlinux/extlinux.conf /boot/grub/core.img

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *             63    23,149,664    23,149,602   7 NTFS / exFAT / HPFS
/dev/sda2          23,150,592   271,306,751   248,156,160   7 NTFS / exFAT / HPFS
/dev/sda3         271,308,798   488,396,799   217,088,002   5 Extended
/dev/sda5         271,308,800   392,400,895   121,092,096   7 NTFS / exFAT / HPFS
/dev/sda6         392,402,944   396,599,295     4,196,352  82 Linux swap / Solaris
/dev/sda7         396,601,344   437,614,591    41,013,248  83 Linux
/dev/sda8         437,616,640   488,396,799    50,780,160  83 Linux


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        08340D34340D25F2                       ntfs       RECOVERY
/dev/sda2        F664E71664E6D87F                       ntfs       
/dev/sda5        1AD24BC4D24BA33D                       ntfs       New Volume
/dev/sda6        e81c8403-128a-4b35-8c07-efab31e362a6   swap       
/dev/sda7        e58a2295-aeba-45ce-b20a-cbf137743b84   ext4       
/dev/sda8        dcf2da40-ed1f-45df-9c74-aaca72419d5f   ext4       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda5        /media/New Volume        fuseblk    (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)
/dev/sda8        /                        ext4       (rw,errors=remount-ro)


================================ sda1/boot.ini: ================================

--------------------------------------------------------------------------------
;
;Warning: Boot.ini is used on Windows XP and earlier operating systems.
;Warning: Use BCDEDIT.exe to modify Windows Vista boot options.
;
[boot loader]
timeout=1
default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Professional" /NOEXECUTE=OPTIN /FASTDETECT
--------------------------------------------------------------------------------

=========================== sda7/boot/grub/grub.cfg: ===========================

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
set root='(hd0,msdos7)'
search --no-floppy --fs-uuid --set=root e58a2295-aeba-45ce-b20a-cbf137743b84
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  insmod part_msdos
  insmod ext2
  set root='(hd0,msdos7)'
  search --no-floppy --fs-uuid --set=root e58a2295-aeba-45ce-b20a-cbf137743b84
  set locale_dir=($root)/boot/grub/locale
  set lang=en_US
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
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/06_mint_theme ###
set menu_color_normal=white/black
set menu_color_highlight=white/light-gray
### END /etc/grub.d/06_mint_theme ###

### BEGIN /etc/grub.d/10_linux_proxy ###
function gfxmode {
    set gfxpayload="$1"
    if [ "$1" = "keep" ]; then
        set vt_handoff=vt.handoff=7
    else
        set vt_handoff=
    fi
}
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
### END /etc/grub.d/10_linux_proxy ###

### BEGIN /etc/grub.d/30_os-prober_proxy ###
menuentry "Windows 7 (loader) (on /dev/sda1)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set=root 08340D34340D25F2
    chainloader +1
}
### END /etc/grub.d/30_os-prober_proxy ###

### BEGIN /etc/grub.d/31_linux_proxy ###
menuentry "Linux Mint 13 MATE 64-bit, 3.2.0-23-generic (/dev/sda7)" --class linuxmint --class gnu-linux --class gnu --class os {
    recordfail
    gfxmode $linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos7)'
    search --no-floppy --fs-uuid --set=root e58a2295-aeba-45ce-b20a-cbf137743b84
    linux    /boot/vmlinuz-3.2.0-23-generic root=UUID=e58a2295-aeba-45ce-b20a-cbf137743b84 ro   quiet splash $vt_handoff
    initrd    /boot/initrd.img-3.2.0-23-generic
}
menuentry "Linux Mint 13 MATE 64-bit, 3.2.0-23-generic (/dev/sda7) -- recovery mode" --class linuxmint --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos7)'
    search --no-floppy --fs-uuid --set=root e58a2295-aeba-45ce-b20a-cbf137743b84
    echo    'Loading Linux 3.2.0-23-generic ...'
    linux    /boot/vmlinuz-3.2.0-23-generic root=UUID=e58a2295-aeba-45ce-b20a-cbf137743b84 ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-3.2.0-23-generic
}
### END /etc/grub.d/31_linux_proxy ###

### BEGIN /etc/grub.d/32_lupin ###
### END /etc/grub.d/32_lupin ###

### BEGIN /etc/grub.d/33_linux_xen ###
### END /etc/grub.d/33_linux_xen ###

### BEGIN /etc/grub.d/34_memtest86+_proxy ###
### END /etc/grub.d/34_memtest86+_proxy ###

### BEGIN /etc/grub.d/35_os-prober_proxy ###
menuentry "Ultimate_Edition_Lite, with Linux 3.2.0-38-generic (on /dev/sda8)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos8)'
    search --no-floppy --fs-uuid --set=root 2e2ed0f8-e8b7-463e-b69b-61e14a1cebfd
    linux /boot/vmlinuz-3.2.0-38-generic root=UUID=2e2ed0f8-e8b7-463e-b69b-61e14a1cebfd ro quiet splash $vt_handoff
    initrd /boot/initrd.img-3.2.0-38-generic
}
### END /etc/grub.d/35_os-prober_proxy ###

### BEGIN /etc/grub.d/36_memtest86+_proxy ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos7)'
    search --no-floppy --fs-uuid --set=root e58a2295-aeba-45ce-b20a-cbf137743b84
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos7)'
    search --no-floppy --fs-uuid --set=root e58a2295-aeba-45ce-b20a-cbf137743b84
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/36_memtest86+_proxy ###

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

=============================== sda7/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda7 during installation
UUID=e58a2295-aeba-45ce-b20a-cbf137743b84 /               ext4    errors=remount-ro 0       1
# /windows was on /dev/sda5 during installation
UUID=C626-4880  /windows        vfat    utf8,umask=007,gid=46 0       1
# swap was on /dev/sda6 during installation
UUID=e81c8403-128a-4b35-8c07-efab31e362a6 none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda7: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 197.663627625 = 212.239704064  boot/grub/core.img                             1
 199.518474579 = 214.231330816  boot/grub/grub.cfg                             1
 203.566368103 = 218.577723392  boot/initrd.img-3.2.0-23-generic               2
 195.251693726 = 209.649909760  boot/vmlinuz-3.2.0-23-generic                  1
 203.566368103 = 218.577723392  initrd.img                                     2
 195.251693726 = 209.649909760  vmlinuz                                        1

=========================== sda8/boot/grub/grub.cfg: ===========================

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
set root='(hd0,msdos8)'
search --no-floppy --fs-uuid --set=root dcf2da40-ed1f-45df-9c74-aaca72419d5f
if loadfont /boot/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  insmod part_msdos
  insmod ext2
  set root='(hd0,msdos8)'
  search --no-floppy --fs-uuid --set=root dcf2da40-ed1f-45df-9c74-aaca72419d5f
  set locale_dir=($root)/boot/grub/locale
  set lang=en_US
  insmod gettext
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos8)'
search --no-floppy --fs-uuid --set=root dcf2da40-ed1f-45df-9c74-aaca72419d5f
insmod png
background_image -m stretch /usr/share/wallpapers/Ultimate_Edition_3.4.png
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
insmod part_msdos
insmod ext2
set root='(hd0,msdos8)'
search --no-floppy --fs-uuid --set=root dcf2da40-ed1f-45df-9c74-aaca72419d5f
insmod png
if background_image /usr/share/wallpapers/Ultimate_Edition_3.4.png; then
  true
else
  set menu_color_normal=white/black
  set menu_color_highlight=black/light-gray
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
menuentry 'Ultimate_Edition_Lite, with Linux 3.2.0-38-generic' --class ultimate_edition_lite --class gnu-linux --class gnu --class os {
    recordfail
    gfxmode $linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos8)'
    search --no-floppy --fs-uuid --set=root dcf2da40-ed1f-45df-9c74-aaca72419d5f
    linux    /boot/vmlinuz-3.2.0-38-generic root=UUID=dcf2da40-ed1f-45df-9c74-aaca72419d5f ro   quiet splash $vt_handoff
    initrd    /boot/initrd.img-3.2.0-38-generic
}
menuentry 'Ultimate_Edition_Lite, with Linux 3.2.0-38-generic (recovery mode)' --class ultimate_edition_lite --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos8)'
    search --no-floppy --fs-uuid --set=root dcf2da40-ed1f-45df-9c74-aaca72419d5f
    echo    'Loading Linux 3.2.0-38-generic ...'
    linux    /boot/vmlinuz-3.2.0-38-generic root=UUID=dcf2da40-ed1f-45df-9c74-aaca72419d5f ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-3.2.0-38-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos8)'
    search --no-floppy --fs-uuid --set=root dcf2da40-ed1f-45df-9c74-aaca72419d5f
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos8)'
    search --no-floppy --fs-uuid --set=root dcf2da40-ed1f-45df-9c74-aaca72419d5f
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set=root 08340D34340D25F2
    chainloader +1
}
menuentry "Linux Mint 13 MATE 64-bit, 3.2.0-23-generic (/dev/sda7) (on /dev/sda7)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos7)'
    search --no-floppy --fs-uuid --set=root e58a2295-aeba-45ce-b20a-cbf137743b84
    linux /boot/vmlinuz-3.2.0-23-generic root=UUID=e58a2295-aeba-45ce-b20a-cbf137743b84 ro quiet splash $vt_handoff
    initrd /boot/initrd.img-3.2.0-23-generic
}
menuentry "Linux Mint 13 MATE 64-bit, 3.2.0-23-generic (/dev/sda7) -- recovery mode (on /dev/sda7)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos7)'
    search --no-floppy --fs-uuid --set=root e58a2295-aeba-45ce-b20a-cbf137743b84
    linux /boot/vmlinuz-3.2.0-23-generic root=UUID=e58a2295-aeba-45ce-b20a-cbf137743b84 ro recovery nomodeset
    initrd /boot/initrd.img-3.2.0-23-generic
}
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

=============================== sda8/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda8 during installation
UUID=dcf2da40-ed1f-45df-9c74-aaca72419d5f /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=e81c8403-128a-4b35-8c07-efab31e362a6 none            swap    sw              0       0
--------------------------------------------------------------------------------

====================== sda8/boot/extlinux/extlinux.conf: =======================

--------------------------------------------------------------------------------
## /boot/extlinux/extlinux.conf
##
## IMPORTANT WARNING
##
## The configuration of this file is generated automatically.
## Do not edit this file manually, use: extlinux-update


default l0
prompt 1
timeout 50

include themes/debian/theme.cfg
--------------------------------------------------------------------------------

=================== sda8: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 213.324371338 = 229.055299584  boot/grub/core.img                             1
 213.324390411 = 229.055320064  boot/grub/grub.cfg                             1
 213.466739655 = 229.208166400  boot/initrd.img-3.2.0-38-generic               1
 213.303642273 = 229.033041920  boot/vmlinuz-3.2.0-38-generic                  1
 213.466739655 = 229.208166400  initrd.img                                     1
 213.303642273 = 229.033041920  vmlinuz                                        1

================= sda8: Location of files loaded by Syslinux: ==================

           GiB - GB             File                                 Fragment(s)

 213.324268341 = 229.055188992  boot/extlinux/chain.c32                        1
 212.805431366 = 228.498092032  boot/extlinux/extlinux.conf                    1

============== sda8: Version of COM32(R) files used by Syslinux: ===============

 boot/extlinux/chain.c32            :  COM32R module (v4.xx)

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda3

00000000  fa 42 ab f6 af 5a 44 14  6c ea c9 f6 4d c7 21 c4  |.B...ZD.l...M.!.|
00000010  8a d7 e5 25 47 ec 3f 01  ee f4 9a 6a a5 a9 13 2c  |...%G.?....j...,|
00000020  ed 13 02 90 82 07 35 c4  35 95 74 8e 6c 68 88 76  |......5.5.t.lh.v|
00000030  52 89 0e ff c7 26 84 60  42 5a ae e8 ca fd c3 8d  |R....&.`BZ......|
00000040  dc 1e e6 1b 7b 4b 9c 2e  60 e3 c6 50 99 7c 20 2c  |....{K..`..P.| ,|
00000050  d1 52 45 1e 29 02 6e 3d  f9 c3 a7 c0 a8 6a 27 3a  |.RE.).n=.....j':|
00000060  66 fe f3 39 f4 20 a5 21  a4 f7 76 76 fa 5b 80 6f  |f..9. .!..vv.[.o|
00000070  d3 d0 6b d0 ac a8 06 92  75 2e 13 eb 93 e6 41 df  |..k.....u.....A.|
00000080  0e 1c 8b 1e cc 2c 6c 28  10 9d cc 89 34 97 9b 7a  |.....,l(....4..z|
00000090  d4 3c 2d a8 3a c4 5f e9  ed 8f 9b c1 a7 7d 08 b8  |.<-.:._......}..|
000000a0  d2 76 29 a7 85 e4 58 91  7c 79 fe 3e 8b 27 4e 75  |.v)...X.|y.>.'Nu|
000000b0  08 d7 04 ab 2c 95 98 28  e5 a0 e5 f9 04 26 05 7d  |....,..(.....&.}|
000000c0  9b af 49 2d 07 98 c3 c5  fb fe cc d4 e0 ba 30 dd  |..I-..........0.|
000000d0  9c 2a 62 5b 58 de 65 20  90 41 68 ee 8e aa 46 82  |.*b[X.e .Ah...F.|
000000e0  9a c1 b1 b0 ac ec a7 15  58 c4 2e 23 bd 73 e9 12  |........X..#.s..|
000000f0  e8 e3 52 5f 75 9d 55 51  35 16 dc 6a 9d 00 ed 9a  |..R_u.UQ5..j....|
00000100  0f 18 59 64 b3 ba dd 09  ba 0a 0f 7d 34 5f 9b 07  |..Yd.......}4_..|
00000110  7d 56 ca 76 71 3e 93 c6  43 5b ce 45 24 33 61 69  |}V.vq>..C[.E$3ai|
00000120  b1 b3 04 9e 23 55 f1 b2  7b ea 6c 6e 02 e8 e2 00  |....#U..{.ln....|
00000130  49 6d 0e d7 e6 25 d9 c6  20 00 03 60 00 e0 21 0c  |Im...%.. ..`..!.|
00000140  54 7d c2 89 62 a8 30 68  48 43 23 1f 02 14 35 95  |T}..b.0hHC#...5.|
00000150  52 6a a5 af 42 c5 38 53  31 b7 73 39 04 c1 7c 9b  |Rj..B.8S1.s9..|.|
00000160  3b e9 35 cd a0 b6 3c 6d  7e c0 55 56 11 10 3d 73  |;.5...<m~.UV..=s|
00000170  7b f6 8d 26 eb 24 33 6c  2b cb f2 fd 48 7e 35 e4  |{..&.$3l+...H~5.|
00000180  bd e5 3b 82 bd de 7e f5  56 1f 64 e9 bc a1 bb a8  |..;...~.V.d.....|
00000190  ee e0 13 6e bb 72 70 7f  0d 47 7f 6f 88 2d 65 f4  |...n.rp..G.o.-e.|
000001a0  3d bb 13 1c ba 31 97 17  8f 4d 0d 82 79 01 f9 e4  |=....1...M..y...|
000001b0  ec 0d 62 b1 50 c7 ed c3  fb cf b0 71 38 6d 00 fe  |..b.P......q8m..|
000001c0  ff ff 07 fe ff ff 02 00  00 00 00 b8 37 07 00 fe  |............7...|
000001d0  ff ff 05 fe ff ff 02 b8  37 07 00 10 40 00 00 00  |........7...@...|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


========= Devices which don't seem to have a corresponding hard drive: =========

sdb 

=============================== StdErr Messages: ===============================

xz: (stdin): Compressed data is corrupt
mdadm: No arrays found in config file or automatically


```

---

### Post by oldfred on 2013-12-23
I would suggest running chkdsk on the NTFS partition that is sda5. The PBR or partition boot sector has to have the same start and size info as the partition table. Even though not a boot partition it needs the correct info. You have to run chkdsk from Windows and use the Windows 7 version. 

You show both Windows 7 and XP boot loaders in your sda1. Perhaps that is why neither versions have found the Windows install with os-prober. Have you tried this?
sudo update-grub

I would also mount the NTFS partition with fstab.

       [http://ubuntuforums.org/showthread.php?t=1983336](http://ubuntuforums.org/showthread.php?t=1983336)
Mount & edit fstab from user Morbius1 in Post # 6 - suggest using templates instead.
For ntfs UUID shown is example only see below:
UUID=XXXXXXXXXXX   /media/WinD ntfs defaults,nls=utf8,umask=000,uid=1000,windows_names 0 0
Window_names prevents the use of invalid windows characters:
(which are the nine characters &#8221; * / : < > ? \ | and those whose code is less than 0×20) 
uid=1000 should fix the trash problems as well:


 ** To find the correct UUID for your partitions:
sudo blkid -c /dev/null -o list
** You will have to create the mount point yourself, for example:
sudo mkdir /media/WinD
and/or 
sudo mkdir /media/Data
** Then add the template with the correct UUID and mount point to fstab:
sudo cp /etc/fstab /etc/fstab.backup
gksu gedit /etc/fstab

   ** And when you are done editing fstab and saving it run the following command to test for errors and mount the partitions without requiring a reboot. You will know before you reboot if something is amiss. Make sure you have partition unmounted if previously mounted:
sudo mount -a

If you boot into both installs you need to add the same entry to both fstabs.

---

### Post by corey6 on 2013-12-24
Well i guess I don't quite understand.  The sda1 partition is actually the recovery partition that came installed on the pc when purchased.  I have never been able to figure out how to boot into it. even downloading the user manual for the pc did not help. It appears that you need a cd from gateway to boot into it according to the documentation.  I probably should have deleted it but have always kept it around just in case. I believe it is probably a vista install which is what the pc originally came with.  All these are fresh installs and it may just be quicker to repartition and re-install.  When you say that the fstabs have to be the same are you referring to both the ubuntu installs.  if i could fix by just copying the fstab from ultimate and overwriting the mint fstab that would be easy.  the problem is figuring out which ntfs partition is causing the problem.  I was assuming it was sda5 but if it's the recovery i would probably have to delete it or start over anyway.  what i dont understand is why is mint picking on it but ultimate doesnt care unless it has something to do with the fstabs.

---

### Post by oldfred on 2013-12-24
You cannot copy an entire fstab as that is unique to each install, but can copy the entry to mount other partitions.

---

