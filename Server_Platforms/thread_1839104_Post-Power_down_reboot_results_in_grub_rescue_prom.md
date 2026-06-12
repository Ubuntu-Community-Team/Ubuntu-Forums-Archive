---
title: "Post-Power down reboot results in grub rescue prompt"
date: 2011-09-04
forum: Server Platforms
---

### Post by Milz on 2011-09-04
Hi,

I'm currently rebuilding a server with ubuntu server 10.04.3 LTS. 

Everything was going fine, however after shutting down with a shutdown -h and then disconnecting the power cable things got weird. Upon reboot I end up at grub rescue with hd read error messages. Weird because I'd rebooted using shutdown -r a few times previously, yet this had not occurred.

When installing I created a software RAID with 2 1TB hdds (Raid 1), 3 partitions on each drive, /boot / and swap. I don't understand what I could have done wrong?

What the hell happened when I disconnected the power? LiveCD can see the array?

I have no ideas how to proceed in debugging this problem, I'm way out of my depth.

Thank you in advance

---

### Post by Milz on 2011-09-05
Hi,

I booted into live disk, mounted the array and ran the boot script.

Here is my boot info script:

> 
                                    Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.97-1.98) is installed in the MBR of /dev/sda and looks at sector 
    1 of the same hard drive for core.img. core.img is at this location and 
    looks for (md0)/grub on this drive.
 => Grub2 (v1.97-1.98) is installed in the MBR of /dev/sdb and looks at sector 
    1 of the same hard drive for core.img. core.img is at this location and 
    looks for (md0)/grub on this drive.
 => Syslinux MBR (4.04 and higher) is installed in the MBR of /dev/sdc.

sda1: __________________________________________________________________________

    File system:       linux_raid_member
    Boot sector type:  -
    Boot sector info:  

sda2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       linux_raid_member
    Boot sector type:  -
    Boot sector info:  

sda6: __________________________________________________________________________

    File system:       linux_raid_member
    Boot sector type:  -
    Boot sector info:  

sdb1: __________________________________________________________________________

    File system:       linux_raid_member
    Boot sector type:  -
    Boot sector info:  

sdb2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: __________________________________________________________________________

    File system:       linux_raid_member
    Boot sector type:  -
    Boot sector info:  

sdb6: __________________________________________________________________________

    File system:       linux_raid_member
    Boot sector type:  -
    Boot sector info:  

sdc1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  SYSLINUX 4.04 2011-04-18
    Boot sector info:   Syslinux looks at sector 15264 of /dev/sdc1 for its 
                       second stage. SYSLINUX is installed in the  directory. 
                       The integrity check of the ADV area failed. No errors 
                       found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /syslinux/syslinux.cfg /ldlinux.sys

md0: ___________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        /grub/grub.cfg /grub/core.img

md2: ___________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.3 LTS
    Boot files:        /etc/fstab

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048       292,863       290,816  fd Linux raid autodetect
/dev/sda2             294,910 1,953,523,711 1,953,228,802   5 Extended
/dev/sda5             294,912    19,824,639    19,529,728  fd Linux raid autodetect
/dev/sda6          19,826,688 1,953,523,711 1,933,697,024  fd Linux raid autodetect


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *          2,048       292,863       290,816  fd Linux raid autodetect
/dev/sdb2             294,910 1,953,523,711 1,953,228,802   5 Extended
/dev/sdb5             294,912    19,824,639    19,529,728  fd Linux raid autodetect
/dev/sdb6          19,826,688 1,953,523,711 1,933,697,024  fd Linux raid autodetect


Drive: sdc _____________________________________________________________________

Disk /dev/sdc: 2003 MB, 2003828736 bytes
255 heads, 63 sectors/track, 243 cylinders, total 3913728 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdc1    *             63     3,913,685     3,913,623   c W95 FAT32 (LBA)


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/md0         e1f9c7f3-b809-42d4-bd46-310fce810779   ext3       
/dev/md2         8737a7b8-6ac8-439a-926f-c2434ef2e20a   ext3       
/dev/sda1        8b15f8ca-0225-fe92-50e8-b5f7c080aea1   linux_raid_member 
/dev/sda5        eeada709-f933-7c50-14b6-54f80b02cdf1   linux_raid_member 
/dev/sda6        c2aa3b57-f45a-7f66-d390-ae41bf4494cd   linux_raid_member 
/dev/sdb1        8b15f8ca-0225-fe92-50e8-b5f7c080aea1   linux_raid_member 
/dev/sdb5        eeada709-f933-7c50-14b6-54f80b02cdf1   linux_raid_member 
/dev/sdb6        c2aa3b57-f45a-7f66-d390-ae41bf4494cd   linux_raid_member 
/dev/sdc1        0BF2-0A54                              vfat       PENDRIVE

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/md0         /tmp/md0                 ext3       (rw)
/dev/md2         /tmp/md2                 ext3       (rw)
/dev/sdc1        /cdrom                   vfat       (rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)


========================= sdc1/syslinux/syslinux.cfg: ==========================

--------------------------------------------------------------------------------
# D-I config version 2.0
include menu.cfg
default vesamenu.c32
prompt 0
timeout 50

# If you would like to use the new menu and be presented with the option to install or run from USB at startup, remove # from the following line. This line wa
s commented out (by request of many) to allow the old menu to be presented and to enable booting straight into the Live Environment! 
# ui gfxboot bootlogo
--------------------------------------------------------------------------------

================= sdc1: Location of files loaded by Syslinux: ==================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             ldlinux.sys                                    1
            ?? = ??             syslinux/gfxboot.c32                           1
            ?? = ??             syslinux/syslinux.cfg                          1
            ?? = ??             syslinux/vesamenu.c32                          1

============== sdc1: Version of COM32(R) files used by Syslinux: ===============

 syslinux/gfxboot.c32               :  COM32R module (v4.xx)
 syslinux/vesamenu.c32              :  COM32R module (v4.xx)

============================== md0/grub/grub.cfg: ==============================

--------------------------------------------------------------------------------
#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  set saved_entry=${prev_saved_entry}
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z ${boot_once} ]; then
    saved_entry=${chosen}
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n ${have_grubenv} ]; then if [ -z ${boot_once} ]; then save_env recordfail; fi; fi
}
insmod raid
insmod mdraid
insmod ext2
set root='(md2)'
search --no-floppy --fs-uuid --set 8737a7b8-6ac8-439a-926f-c2434ef2e20a
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  insmod gfxterm
  insmod vbe
  if terminal_output gfxterm ; then true ; else
    # For backward compatibility with versions of terminal.mod that don't
    # understand terminal_output
    terminal gfxterm
  fi
fi
insmod raid
insmod mdraid
insmod ext2
set root='(md0)'
search --no-floppy --fs-uuid --set e1f9c7f3-b809-42d4-bd46-310fce810779
set locale_dir=($root)/grub/locale
set lang=C.UTF-8
insmod gettext
if [ ${recordfail} = 1 ]; then
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
menuentry 'Ubuntu, with Linux 2.6.32-33-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod raid
    insmod mdraid
    insmod ext2
    set root='(md0)'
    search --no-floppy --fs-uuid --set e1f9c7f3-b809-42d4-bd46-310fce810779
    linux    /vmlinuz-2.6.32-33-generic root=UUID=8737a7b8-6ac8-439a-926f-c2434ef2e20a ro   splash quiet
    initrd    /initrd.img-2.6.32-33-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-33-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod raid
    insmod mdraid
    insmod ext2
    set root='(md0)'
    search --no-floppy --fs-uuid --set e1f9c7f3-b809-42d4-bd46-310fce810779
    echo    'Loading Linux 2.6.32-33-generic ...'
    linux    /vmlinuz-2.6.32-33-generic root=UUID=8737a7b8-6ac8-439a-926f-c2434ef2e20a ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /initrd.img-2.6.32-33-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod raid
    insmod mdraid
    insmod ext2
    set root='(md0)'
    search --no-floppy --fs-uuid --set e1f9c7f3-b809-42d4-bd46-310fce810779
    linux16    /memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod raid
    insmod mdraid
    insmod ext2
    set root='(md0)'
    search --no-floppy --fs-uuid --set e1f9c7f3-b809-42d4-bd46-310fce810779
    linux16    /memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
if [ ${timeout} != -1 ]; then
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
--------------------------------------------------------------------------------

==================== md0: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

   0.032922745 = 0.035350528    grub/core.img                                  2
   0.031497955 = 0.033820672    grub/grub.cfg                                  1
   0.028049469 = 0.030117888    initrd.img-2.6.32-33-generic                  37
   0.013847351 = 0.014868480    vmlinuz-2.6.32-33-generic                     17

================================ md2/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/md2 during installation
UUID=8737a7b8-6ac8-439a-926f-c2434ef2e20a /               ext3    errors=remount-ro 0       1
# /boot was on /dev/md0 during installation
UUID=e1f9c7f3-b809-42d4-bd46-310fce810779 /boot           ext3    defaults        0       2
# swap was on /dev/md1 during installation
UUID=312e039e-6d89-4a93-af31-4f36ef6358e6 none            swap    sw              0       0
--------------------------------------------------------------------------------

=============================== StdErr Messages: ===============================

./boot_info_script.sh: line 1579: [: 2.73495e+09: integer expression expected





---

### Post by Milz on 2011-09-05
After rebooting out of the LiveCD the server booted fine.....but I didn't change anything.....

Tested again, shutdown -h. Disconnect the power. Rebooting -> lands me at grub rescuse with hdd read error(0,1) and (1,1).

What the hell?

Okay I think I understand why manually building the array in liveCD and then rebooting allows me to get back into my system. So how to I go about making the array persistent on reboot?

Very similar thread: [http://ubuntuforums.org/showthread.php?t=1207071](http://ubuntuforums.org/showthread.php?t=1207071)

---

