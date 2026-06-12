---
title: "dualboot, XP does not boot"
date: 2020-08-30
forum: Ubuntu/Debian BASED
---

### Post by svenmatti on 2020-08-30
Hello,

I'm new to the subject but after a few days of trying I have to ask for help.

Installed linuslite on my old XP computer. Linux is running, but when I try to boot XP the screen remains black.

Last tried Boot-Repair. Here is the file: [http://paste.ubuntu.com/p/J7ZBQb9Syg/](http://paste.ubuntu.com/p/J7ZBQb9Syg/)

So it seems it doesn't find the partition with the XP. But

sudo blkid
[sudo] password for xxxx: 
/dev/sda1: UUID="14182E4B182E2BE4" TYPE="ntfs" PARTUUID="26572656-01"
/dev/sda5: LABEL="Bilder" UUID="3C8C1B538C1B06D4" TYPE="ntfs" PARTUUID="26572656-05"
/dev/sda6: LABEL="Daten" UUID="D898104A98102A10" TYPE="ntfs" PARTUUID="26572656-06"
/dev/sda7: UUID="540052ba-df84-4736-9189-5448db3ef9f7" TYPE="ext3" PTTYPE="dos" PARTUUID="26572656-07"

So there it is. sda1 is Win XP sda5+6 user data, sda7 linux

Does anybody have an idea what's wrong?

---

### Post by jeremy31 on 2020-08-30
Moved to Ubuntu/Debian based

---

### Post by oldfred on 2020-08-30
Did you post full report, it is missing a large part of what it normally shows.

The only issue shown is flexnet, which used to be an issue but grub now works around it. Flexnet is the security system for some proprietary Windows software you have and it writes hidden info in sector 32. Grub used to write into sector 32 with core.img as part of boot which caused major issues. Now resolved.

You do know Windows XP is long obsolete. You can only safely use if not connecting to Internet.

Grub only boots working Windows, but that grub's os-prober finds the XP partition and adds to grub menu means you have boot files and partition can be seen(mounted).
You may just need Windows repairs, like chkdsk from your Windows repair disk. I do not remember but XP did not have separate repair disk, and back then I did use a Windows 7 repair disk for chkdsk which worked better for chkdsk, but then modified NTFS partition boot sector to Windows 7 type. So have to convert BS back to XP type.

---

### Post by svenmatti on 2020-08-30
Thanks for the answer.

It's the full report.

I know one should not use Win XP anymore, that's why I'm changing to linux now. I know it's a bit late. Never had time for that. 
But for a start I want to have the two systems in parallel until everything works in linux. 

The Windows worked until I startet installing linux. First I installed elementaryOS, both systems worked fine for a few days, then suddenly windoscould not bee booted any more. Then I installed linuxliteOS, still Windows doesn't boot.

I'm a bit worried using the windows repair CD, one never knows what happens ...

---

### Post by oldfred on 2020-08-30
Run this report.
Either post to a pastebin site or post in code tags.
Boot-Repair report normally includes this report, but Yann has updated it to include newer NVMe drives and made other changes.

Updated fork  as original bootinfoscript does not seem to be maintained
[https://github.com/arvidjaar/bootinfoscript](https://github.com/arvidjaar/bootinfoscript)

---

### Post by svenmatti on 2020-08-31
Thanks, well, tried my best, here's the result:

                 ```
Boot Info Script 0.78      [09 October 2019]


============================= Boot Info Summary: ===============================

 => Grub2 (v2.00) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos7)/boot/grub. It also embeds following components:
    
    modules
    ---------------------------------------------------------------------------
    fshelp ext2 part_msdos biosdisk
    ---------------------------------------------------------------------------

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub2 (v1.99-2.00)
    Boot sector info:  Grub2 (v1.99-2.00) is installed in the boot sector of 
                       sda1 and looks at sector 317288288 of the same hard 
                       drive for core.img, but core.img can not be found at 
                       this location. No errors found in the Boot Parameter 
                       Block.
    Operating System:  Windows XP
    Boot files:        /boot.ini /ntldr /NTDETECT.COM

sda2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info: 

sda5: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows 2000/XP: NTFS
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 63.
    Operating System:  
    Boot files:        

sda6: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows 2000/XP: NTFS
    Boot sector info:  According to the info in the boot sector, sda6 starts 
                       at sector 63.
    Operating System:  
    Boot files:        

sda7: __________________________________________________________________________

    File system:       ext3
    Boot sector type:  Grub2 (v1.99-2.00)
    Boot sector info:  Grub2 (v2.00) is installed in the boot sector of sda7 
                       and looks at sector 307473992 of the same hard drive 
                       for core.img. core.img is at this location and looks 
                       for (,msdos7)/boot/grub. It also embeds following 
                       components:
                       
                       modules
                       -------------------------------------------------------
                       fshelp ext2 part_msdos biosdisk
                       -------------------------------------------------------
    Operating System:  Ubuntu 20.04.1 LTS
    Boot files:        /boot/grub/grub.cfg /etc/fstab 
                       /boot/grub/i386-pc/core.img

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________
Disk /dev/sda: 153,39 GiB, 164696555520 bytes, 321672960 sectors
Disk model: ExcelStor Techno
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *             63    69,641,774    69,641,712   7 NTFS / exFAT / HPFS
/dev/sda2          69,641,836   321,670,641   252,028,806   f W95 Extended (LBA)
/dev/sda5          69,641,838   197,647,694   128,005,857   7 NTFS / exFAT / HPFS
/dev/sda6         197,647,758   302,137,992   104,490,235   7 NTFS / exFAT / HPFS
/dev/sda7         302,139,392   321,670,641    19,531,250  83 Linux


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        14182E4B182E2BE4                       ntfs       
/dev/sda5        3C8C1B538C1B06D4                       ntfs       Bilder
/dev/sda6        D898104A98102A10                       ntfs       Daten
/dev/sda7        540052ba-df84-4736-9189-5448db3ef9f7   ext3       
/dev/zram0       b56250d3-2051-4e93-8ce3-d8005a1b5b5c   swap       

========================= "ls -l /dev/disk/by-id" output: ======================

total 0
lrwxrwxrwx 1 root root  9 Aug 30 19:34 ata-ExcelStor_Technology_J8160S_PVB300Q407DYAA -> ../../sda
lrwxrwxrwx 1 root root 10 Aug 30 19:34 ata-ExcelStor_Technology_J8160S_PVB300Q407DYAA-part1 -> ../../sda1
lrwxrwxrwx 1 root root 10 Aug 30 19:34 ata-ExcelStor_Technology_J8160S_PVB300Q407DYAA-part2 -> ../../sda2
lrwxrwxrwx 1 root root 10 Aug 30 19:34 ata-ExcelStor_Technology_J8160S_PVB300Q407DYAA-part5 -> ../../sda5
lrwxrwxrwx 1 root root 10 Aug 30 19:34 ata-ExcelStor_Technology_J8160S_PVB300Q407DYAA-part6 -> ../../sda6
lrwxrwxrwx 1 root root 10 Aug 30 19:34 ata-ExcelStor_Technology_J8160S_PVB300Q407DYAA-part7 -> ../../sda7
lrwxrwxrwx 1 root root  9 Aug 30 19:34 ata-LITE-ON_DVD_D_LH-16D1P -> ../../sr0

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda7        /                        ext3       (rw,relatime,errors=remount-ro)


================================ sda1/boot.ini: ================================

--------------------------------------------------------------------------------
[boot loader]
timeout=3
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS1="Microsoft Windows XP Professional" /noexecute=optin /fastdetect
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="alte Version" /noexecute=optin /fastdetect
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
if [ "${initrdfail}" = 2 ]; then
   set initrdfail=
elif [ "${initrdfail}" = 1 ]; then
   set next_entry="${prev_entry}"
   set prev_entry=
   save_env prev_entry
   if [ "${next_entry}" ]; then
      set initrdfail=2
   fi
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
function initrdfail {
    if [ -n "${have_grubenv}" ]; then if [ -n "${partuuid}" ]; then
      if [ -z "${initrdfail}" ]; then
        set initrdfail=1
        if [ -n "${boot_once}" ]; then
          set prev_entry="${default}"
          save_env prev_entry
        fi
      fi
      save_env initrdfail
    fi; fi
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
set root='hd0,msdos7'
if [ x$feature_platform_search_hint = xy ]; then
  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos7 --hint-efi=hd0,msdos7 --hint-baremetal=ahci0,msdos7  540052ba-df84-4736-9189-5448db3ef9f7
else
  search --no-floppy --fs-uuid --set=root 540052ba-df84-4736-9189-5448db3ef9f7
fi
    font="/usr/share/grub/unicode.pf2"
fi

if loadfont $font ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  set locale_dir=$prefix/locale
  set lang=de_DE
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
set menu_color_highlight=black/light-gray
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
menuentry 'Ubuntu' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-simple-540052ba-df84-4736-9189-5448db3ef9f7' {
    recordfail
    load_video
    gfxmode $linux_gfx_mode
    insmod gzio
    if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
    insmod part_msdos
    insmod ext2
    set root='hd0,msdos7'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos7 --hint-efi=hd0,msdos7 --hint-baremetal=ahci0,msdos7  540052ba-df84-4736-9189-5448db3ef9f7
    else
      search --no-floppy --fs-uuid --set=root 540052ba-df84-4736-9189-5448db3ef9f7
    fi
    linux    /boot/vmlinuz-5.4.0-42-generic root=UUID=540052ba-df84-4736-9189-5448db3ef9f7 ro  quiet splash $vt_handoff
    initrd    /boot/initrd.img-5.4.0-42-generic
}
submenu 'Advanced options for Ubuntu' $menuentry_id_option 'gnulinux-advanced-540052ba-df84-4736-9189-5448db3ef9f7' {
    menuentry 'Ubuntu, with Linux 5.4.0-42-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-5.4.0-42-generic-advanced-540052ba-df84-4736-9189-5448db3ef9f7' {
        recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos7'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos7 --hint-efi=hd0,msdos7 --hint-baremetal=ahci0,msdos7  540052ba-df84-4736-9189-5448db3ef9f7
        else
          search --no-floppy --fs-uuid --set=root 540052ba-df84-4736-9189-5448db3ef9f7
        fi
        echo    'Loading Linux 5.4.0-42-generic ...'
        linux    /boot/vmlinuz-5.4.0-42-generic root=UUID=540052ba-df84-4736-9189-5448db3ef9f7 ro  quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-5.4.0-42-generic
    }
    menuentry 'Ubuntu, with Linux 5.4.0-42-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-5.4.0-42-generic-recovery-540052ba-df84-4736-9189-5448db3ef9f7' {
        recordfail
        load_video
        insmod gzio
        if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos7'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos7 --hint-efi=hd0,msdos7 --hint-baremetal=ahci0,msdos7  540052ba-df84-4736-9189-5448db3ef9f7
        else
          search --no-floppy --fs-uuid --set=root 540052ba-df84-4736-9189-5448db3ef9f7
        fi
        echo    'Loading Linux 5.4.0-42-generic ...'
        linux    /boot/vmlinuz-5.4.0-42-generic root=UUID=540052ba-df84-4736-9189-5448db3ef9f7 ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-5.4.0-42-generic
    }
    menuentry 'Ubuntu, with Linux 5.4.0-33-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-5.4.0-33-generic-advanced-540052ba-df84-4736-9189-5448db3ef9f7' {
        recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos7'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos7 --hint-efi=hd0,msdos7 --hint-baremetal=ahci0,msdos7  540052ba-df84-4736-9189-5448db3ef9f7
        else
          search --no-floppy --fs-uuid --set=root 540052ba-df84-4736-9189-5448db3ef9f7
        fi
        echo    'Loading Linux 5.4.0-33-generic ...'
        linux    /boot/vmlinuz-5.4.0-33-generic root=UUID=540052ba-df84-4736-9189-5448db3ef9f7 ro  quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-5.4.0-33-generic
    }
    menuentry 'Ubuntu, with Linux 5.4.0-33-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-5.4.0-33-generic-recovery-540052ba-df84-4736-9189-5448db3ef9f7' {
        recordfail
        load_video
        insmod gzio
        if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos7'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos7 --hint-efi=hd0,msdos7 --hint-baremetal=ahci0,msdos7  540052ba-df84-4736-9189-5448db3ef9f7
        else
          search --no-floppy --fs-uuid --set=root 540052ba-df84-4736-9189-5448db3ef9f7
        fi
        echo    'Loading Linux 5.4.0-33-generic ...'
        linux    /boot/vmlinuz-5.4.0-33-generic root=UUID=540052ba-df84-4736-9189-5448db3ef9f7 ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-5.4.0-33-generic
    }
}

### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/10_linux_zfs ###
### END /etc/grub.d/10_linux_zfs ###

### BEGIN /etc/grub.d/20_linux_xen ###

### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry 'Windows NT/2000/XP (on /dev/sda1)' --class windows --class os $menuentry_id_option 'osprober-chain-14182E4B182E2BE4' {
    insmod part_msdos
    insmod ntfs
    set root='hd0,msdos1'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  14182E4B182E2BE4
    else
      search --no-floppy --fs-uuid --set=root 14182E4B182E2BE4
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

=============================== sda7/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda7 during installation
UUID=540052ba-df84-4736-9189-5448db3ef9f7 /               ext3    errors=remount-ro 0       1
/swapfile                                 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
--------------------------------------------------------------------------------

=================== sda7: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 146.706848145 = 157.525278720  boot/grub/grub.cfg                             1
 146.706584930 = 157.524996096  boot/grub/i386-pc/core.img                     1
 150.261837006 = 161.342418944  boot/vmlinuz                                   8
 152.160274506 = 163.380850688  boot/vmlinuz-5.4.0-33-generic                  8
 150.261837006 = 161.342418944  boot/vmlinuz-5.4.0-42-generic                  8
 152.160274506 = 163.380850688  boot/vmlinuz.old                               8
 150.571285248 = 161.674686464  boot/initrd.img                               15
 153.275737762 = 164.578570240  boot/initrd.img-5.4.0-33-generic              197
 150.571285248 = 161.674686464  boot/initrd.img-5.4.0-42-generic              15
 153.275737762 = 164.578570240  boot/initrd.img.old                           197

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda2

00000000  e7 d8 d5 48 ec 7c d9 06  e5 2c ef 80 a0 9e 33 52  |...H.|...,....3R|
00000010  ef 6d 06 b5 45 98 ec 7c  b7 0c ca bb d9 ba 01 c1  |.m..E..|........|
00000020  fa d4 df d9 e8 07 11 05  cb 65 b0 3a ff 00 f5 e8  |.........e.:....|
00000030  87 c0 86 9d 98 a6 c8 fc  aa 84 6d 2d 93 c5 43 2d  |..........m-..C-|
00000040  b3 2b 05 24 67 d0 0e 3f  cf 5a b8 a4 dd 84 24 76  |.+.$g..?.Z....$v|
00000050  93 31 56 db b4 63 38 3d  fe 94 5c 29 3b 50 a8 2b  |.1V..c8=..\);P.+|
00000060  d0 e0 6d 20 62 b3 4d 4a  69 22 b4 e5 21 2b b8 8d  |..m b.MJi"..!+..|
00000070  aa 70 14 6e c7 38 fa e6  a5 80 bc 5b dd 99 be 46  |.p.n.8.....[...F|
00000080  18 c2 e7 39 e9 9a c9 bb  92 5d 25 f3 b9 46 cc e4  |...9.....]%..F..|
00000090  72 7b d4 6d 89 1c 29 d8  46 dc fd ee 33 51 00 1e  |r{.m..).F...3Q..|
000000a0  39 c8 dd f7 4f 5c 75 f6  a7 ab 3f ca 77 2a a2 ae  |9...O\u...?.w*..|
000000b0  02 e3 df bd 75 a9 28 d3  49 80 82 76 c9 da 3a 1c  |....u.(.I..v..:.|
000000c0  13 d2 ad ad c0 08 80 0c  2e ef 90 81 db d2 a6 6a  |...............j|
000000d0  1c 9a 00 8d 3c 79 65 72  51 97 96 6c 71 f9 d4 60  |....<yerQ..lq..`|
000000e0  a3 64 9e 4e ee b9 ac 6c  03 87 94 c4 be 00 e0 0c  |.d.N...l........|
000000f0  28 eb ee 6a 57 86 33 b0  29 f9 41 05 c3 0e 0d 20  |(..jW.3.).A.... |
00000100  d8 6b 2a 65 36 90 3b 10  33 4e 36 f1 60 92 07 4c  |.k*e6.;.3N6.`..L|
00000110  8c 0e 82 b5 8d 9c 6c 02  2d a0 d8 a7 73 31 50 73  |......l.-...s1Ps|
00000120  c5 29 8d ce 00 3d b1 d2  a2 3f 10 0d 08 c3 20 8d  |.)...=...?.... .|
00000130  c4 67 f4 ef 50 90 01 63  86 c9 5f 93 b0 04 55 cf  |.g..P..c.._...U.|
00000140  60 29 48 19 9d 72 18 6d  ee 0f 5a 69 2c 33 81 f3  |`)H..r.m..Zi,3..|
00000150  fd 38 a7 14 b9 49 8c b4  bb 23 91 f6 9d 85 89 60  |.8...I...#.....`|
00000160  d9 04 8e 07 d2 a9 ba fc  d8 dc 4f 3d 5b 81 53 51  |..........O=[.SQ|
00000170  15 e4 57 95 c2 02 cc 48  ff 00 6b 15 97 3c a9 20  |..W....H..k..<. |
00000180  f9 78 21 7e 52 46 72 05  62 d7 b3 40 60 c9 20 68  |.x!~RFr.b..@`. h|
00000190  5d 64 03 a9 1c 73 59 90  ca d0 8b 87 43 86 8a ca  |]d...sY.....C...|
000001a0  e5 90 8e d8 8d 88 fe 55  cf 25 7b 09 ab ab 0d f8  |.......U.%{.....|
000001b0  51 6d b3 e0 5f c3 c9 09  f9 e5 82 fe 57 20 00 01  |Qm.._.......W ..|
000001c0  c1 ff 07 fe ff ff 02 00  00 00 e1 36 a1 07 00 fe  |...........6....|
000001d0  ff ff 05 fe ff ff e3 36  a1 07 3a 65 3a 06 00 00  |.......6..:e:...|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200
```

---

### Post by oldfred on 2020-08-31
This breaks Windows in sda1:

>     File system:       ntfs
    Boot sector type:  Grub2 (v1.99-2.00)

You normally do not install grub to a Boot Sector (BS) or PBR - partition boot sector like sda1, only to MBR like sda.
And NTFS partitions have essential Windows boot info in the PBR.
NTFS does have a backup, which you should be able to restore with testdisk.

[http://www.ntfs.com/fat-partition-sector.htm](http://www.ntfs.com/fat-partition-sector.htm)
PBR - partition boot sector NTFS must be Windows
[HowTo] Repair the bootsector of a Windows partition  - YannBuntu
[https://help.ubuntu.com/community/BootSectorFix](https://help.ubuntu.com/community/BootSectorFix)
[http://ubuntuforums.org/showthread.php?t=1926510](http://ubuntuforums.org/showthread.php?t=1926510)
[http://askubuntu.com/questions/655290/grub-is-not-letting-me-switch-to-windows-8-dual-boot-process-ubuntu-15-04/655486#655486](http://askubuntu.com/questions/655290/grub-is-not-letting-me-switch-to-windows-8-dual-boot-process-ubuntu-15-04/655486#655486)
As described, testdisk has an option to "Recover NTFS boot sector from its backup"
If Backup BS isn't available, choose RebuildBS, otherwise Windows repairs will not work 
Instructions - see section on NTFS partition boot sector recovery
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)
You want to get to this screen:
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step#NTFS_Boot_sector_recovery](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step#NTFS_Boot_sector_recovery)
select [Advanced] instead of [Analyse] and select [BackupBS]

---

### Post by svenmatti on 2020-08-31
THANK YOU!

This did the job. Somehow my ubuntu got stuck when updating, so I made a CD with gpart on it which contains testdisk.
Somewhere in the process I had forgotten the sudo first, but after I got that I could fix the problem.

So I'm ready for the next trask ;)

---

