---
title: "Software Raid after update lost /boot"
date: 2013-02-09
forum: Server Platforms
---

### Post by StuartIanNaylor on 2013-02-09
Hi I have a raid array with raid1 /boot
raid 5 /
raid 5 /home
raid 5 swap (dunno why :) )

anyway after a recent upgrade I rebooted and to my horror seemed to of lost the /boot

So anyway used boot-repair.

The raid partitions are there if I run the livecd but when grub is booting it doesn't find /

from busybox an ls /dev/disk/by-uuid/ only lists the swap if I remember correctly.
[EDIT]
I remember incorrectly its /boot which is raid 1 so none of the raid5 partitions are being found.
livecd does though?
[/EDIT]

Its OK if you don't know how exactly to fix it but had a day at this and suffering from blind alley overload :-x

Many Thanks

Stuart

---

### Post by darkod on 2013-02-09
Hold on. Don't rush with any commands in case things get more messed up and your data gets in danger. I'm not sure if boot-repair can help with mdadm.

From live mode, if you try adding the mdadm package and assemble automatically what will it do?
```
sudo apt-get install mdadm
sudo mdadm --assemble --scan
```

Also, can you post the output of:
```
sudo mdadm --examine /dev/sd[abc]
```

In the above command I assume the disks members of the raid are /dev/sda, /dev/sdb and /dev/sdc. If not true, replace the letters in the [ ] with the correct ones.

EDIT PS: I just checked, that last command might not work with specifying the disks. Do you remember which partitions were members of each md device?

---

### Post by StuartIanNaylor on 2013-02-09
Hi, The raid partitions seem to be fine I think its grub that is confused.

Its trying to load / and that is raid5 there is noting in /dev/disk/by-uuid

What loads mdadm on boot?

Anyway here is some detail.

Your right about boot-repair though, well in this case anyway.

It does give some good info though so I will run it again as it did seem only to have a go at the /boot partition.

mdadm --assemble --scan
mdadm: /dev/md/0 has been started with 4 drives.
mdadm: /dev/md/3 has been started with 4 drives.
mdadm: /dev/md/2 has been started with 4 drives.
mdadm: /dev/md/1 has been started with 4 drives.

root@ubuntu:/home/ubuntu# mdadm --examine /dev/sda
/dev/sda:
   MBR Magic : aa55
Partition[0] :      8388608 sectors at         2048 (type fd)
Partition[1] :       612352 sectors at   1952911360 (type 83)
Partition[2] :    920520704 sectors at   1032390656 (type fd)
Partition[3] :   1024000000 sectors at      8390656 (type fd)

root@ubuntu:/home/ubuntu# mdadm --examine /dev/sdb
/dev/sdb:
   MBR Magic : aa55
Partition[0] :      8388608 sectors at         2048 (type fd)
Partition[1] :       612352 sectors at   1952911360 (type 83)
Partition[2] :    920520704 sectors at   1032390656 (type fd)
Partition[3] :   1024000000 sectors at      8390656 (type fd)
root@ubuntu:/home/ubuntu# mdadm --examine /dev/sdc
/dev/sdc:
   MBR Magic : aa55
Partition[0] :      8388608 sectors at         2048 (type fd)
Partition[1] :       612352 sectors at   1952911360 (type 83)
Partition[2] :    920520704 sectors at   1032390656 (type fd)
Partition[3] :   1024000000 sectors at      8390656 (type fd)
root@ubuntu:/home/ubuntu# mdadm --examine /dev/sdd
/dev/sdd:
   MBR Magic : aa55
Partition[0] :      8388608 sectors at         2048 (type fd)
Partition[1] :       612352 sectors at   1952911360 (type 83)
Partition[2] :    920520704 sectors at   1032390656 (type fd)
Partition[3] :   1024000000 sectors at      8390656 (type fd)
root@ubuntu:/home/ubuntu# 

after the assemble I can mount the drives and all seems ok via the livecd

still scratching my head on boot

:)

Many thanks

Stuart

---

### Post by StuartIanNaylor on 2013-02-09
Boot Info Script e7fc706 + Boot-Repair extra info      [Boot-Info 31Jan2013]


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (mduuid/1f8a6ffb01a069042bbbf568dc263a0c)/grub on this drive.
 => Grub2 (v1.99) is installed in the MBR of /dev/sdb and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (mduuid/1f8a6ffb01a069042bbbf568dc263a0c)/grub on this drive.
 => Grub2 (v1.99) is installed in the MBR of /dev/sdc and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (mduuid/1f8a6ffb01a069042bbbf568dc263a0c)/grub on this drive.
 => Grub2 (v1.99) is installed in the MBR of /dev/sdd and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (mduuid/1f8a6ffb01a069042bbbf568dc263a0c)/grub on this drive.
 => Syslinux MBR (3.61-4.03) is installed in the MBR of /dev/sde.

sda1: __________________________________________________________________________

    File system:       linux_raid_member
    Boot sector type:  -
    Boot sector info: 

sda2: __________________________________________________________________________

    File system:       linux_raid_member
    Boot sector type:  -
    Boot sector info: 

sda3: __________________________________________________________________________

    File system:       linux_raid_member
    Boot sector type:  -
    Boot sector info: 

sda4: __________________________________________________________________________

    File system:       linux_raid_member
    Boot sector type:  Unknown
    Boot sector info: 

sdb1: __________________________________________________________________________

    File system:       linux_raid_member
    Boot sector type:  -
    Boot sector info: 

sdb2: __________________________________________________________________________

    File system:       linux_raid_member
    Boot sector type:  -
    Boot sector info: 

sdb3: __________________________________________________________________________

    File system:       linux_raid_member
    Boot sector type:  -
    Boot sector info: 

sdb4: __________________________________________________________________________

    File system:       linux_raid_member
    Boot sector type:  Unknown
    Boot sector info: 

sdc1: __________________________________________________________________________

    File system:       linux_raid_member
    Boot sector type:  -
    Boot sector info: 

sdc2: __________________________________________________________________________

    File system:       linux_raid_member
    Boot sector type:  -
    Boot sector info: 

sdc3: __________________________________________________________________________

    File system:       linux_raid_member
    Boot sector type:  -
    Boot sector info: 

sdc4: __________________________________________________________________________

    File system:       linux_raid_member
    Boot sector type:  Unknown
    Boot sector info: 

sdd1: __________________________________________________________________________

    File system:       linux_raid_member
    Boot sector type:  -
    Boot sector info: 

sdd2: __________________________________________________________________________

    File system:       linux_raid_member
    Boot sector type:  -
    Boot sector info: 

sdd3: __________________________________________________________________________

    File system:       linux_raid_member
    Boot sector type:  -
    Boot sector info: 

sdd4: __________________________________________________________________________

    File system:       linux_raid_member
    Boot sector type:  Unknown
    Boot sector info: 

sde1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  SYSLINUX 4.03 2010-10-22 ........>..sr>.......;..8...0...~.....~...f...M.f.f....f..0~....>E}.u......
    Boot sector info:  Syslinux looks at sector 7369736 of /dev/sde1 for its 
                       second stage. SYSLINUX is installed in the  directory. 
                       No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /syslinux.cfg /ldlinux.sys

md/0: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info: 

md/3: __________________________________________________________________________

    File system:       ext2
    Boot sector type:  -
    Boot sector info: 
    Operating System:  
    Boot files:        /grub/grub.cfg /grub/core.img

md/2: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  
    Boot files:        /boot/grub/grub.cfg /boot/grub/core.img

md/1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 12.04.2 LTS 
    Boot files:        /etc/fstab

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1               2,048     8,390,655     8,388,608  fd Linux raid autodetect
/dev/sda2    *  1,952,911,360 1,953,523,711       612,352  83 Linux
/dev/sda3       1,032,390,656 1,952,911,359   920,520,704  fd Linux raid autodetect
/dev/sda4           8,390,656 1,032,390,655 1,024,000,000  fd Linux raid autodetect


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1               2,048     8,390,655     8,388,608  fd Linux raid autodetect
/dev/sdb2    *  1,952,911,360 1,953,523,711       612,352  83 Linux
/dev/sdb3       1,032,390,656 1,952,911,359   920,520,704  fd Linux raid autodetect
/dev/sdb4           8,390,656 1,032,390,655 1,024,000,000  fd Linux raid autodetect


Drive: sdc _____________________________________________________________________

Disk /dev/sdc: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdc1               2,048     8,390,655     8,388,608  fd Linux raid autodetect
/dev/sdc2    *  1,952,911,360 1,953,523,711       612,352  83 Linux
/dev/sdc3       1,032,390,656 1,952,911,359   920,520,704  fd Linux raid autodetect
/dev/sdc4           8,390,656 1,032,390,655 1,024,000,000  fd Linux raid autodetect


Drive: sdd _____________________________________________________________________

Disk /dev/sdd: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdd1               2,048     8,390,655     8,388,608  fd Linux raid autodetect
/dev/sdd2    *  1,952,911,360 1,953,523,711       612,352  83 Linux
/dev/sdd3       1,032,390,656 1,952,911,359   920,520,704  fd Linux raid autodetect
/dev/sdd4           8,390,656 1,032,390,655 1,024,000,000  fd Linux raid autodetect


Drive: sde _____________________________________________________________________

Disk /dev/sde: 4004 MB, 4004511744 bytes
255 heads, 63 sectors/track, 486 cylinders, total 7821312 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sde1    *          2,048     7,821,311     7,819,264   b W95 FAT32


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/loop1       d45af0b4-4582-0e4c-847e-f6e36cda5002   ext2       
/dev/md/0        abd98da1-fe2b-41e1-998d-a313d4cd64c3   swap       
/dev/md/1        16a0b094-4635-4b14-bdd7-a5601c2e3694   ext4       
/dev/md/2        29342fce-67ac-43ec-b95d-a94366c28a2a   ext4       
/dev/md/3        6f393cca-bbdd-492f-a575-ee2bfefd7e2c   ext2       
/dev/md0         abd98da1-fe2b-41e1-998d-a313d4cd64c3   swap       
/dev/md1         16a0b094-4635-4b14-bdd7-a5601c2e3694   ext4       
/dev/md2         29342fce-67ac-43ec-b95d-a94366c28a2a   ext4       
/dev/md3         6f393cca-bbdd-492f-a575-ee2bfefd7e2c   ext2       
/dev/sda1        e7beb7c1-0d2d-2af7-f5f2-9ca7ace79a50   linux_raid_member zen1:0
/dev/sda2        1f8a6ffb-01a0-6904-2bbb-f568dc263a0c   linux_raid_member zen1:3
/dev/sda3        684ece4d-38f9-6eb6-7d75-c0862ff179ea   linux_raid_member zen1:2
/dev/sda4        e5fe242f-e6fb-b62b-1524-51c13f7d58fb   linux_raid_member zen1:1
/dev/sdb1        e7beb7c1-0d2d-2af7-f5f2-9ca7ace79a50   linux_raid_member zen1:0
/dev/sdb2        1f8a6ffb-01a0-6904-2bbb-f568dc263a0c   linux_raid_member zen1:3
/dev/sdb3        684ece4d-38f9-6eb6-7d75-c0862ff179ea   linux_raid_member zen1:2
/dev/sdb4        e5fe242f-e6fb-b62b-1524-51c13f7d58fb   linux_raid_member zen1:1
/dev/sdc1        e7beb7c1-0d2d-2af7-f5f2-9ca7ace79a50   linux_raid_member zen1:0
/dev/sdc2        1f8a6ffb-01a0-6904-2bbb-f568dc263a0c   linux_raid_member zen1:3
/dev/sdc3        684ece4d-38f9-6eb6-7d75-c0862ff179ea   linux_raid_member zen1:2
/dev/sdc4        e5fe242f-e6fb-b62b-1524-51c13f7d58fb   linux_raid_member zen1:1
/dev/sdd1        e7beb7c1-0d2d-2af7-f5f2-9ca7ace79a50   linux_raid_member zen1:0
/dev/sdd2        1f8a6ffb-01a0-6904-2bbb-f568dc263a0c   linux_raid_member zen1:3
/dev/sdd3        684ece4d-38f9-6eb6-7d75-c0862ff179ea   linux_raid_member zen1:2
/dev/sdd4        e5fe242f-e6fb-b62b-1524-51c13f7d58fb   linux_raid_member zen1:1
/dev/sde1        B868-BF20                              vfat       UBUNTU-SERV

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sde1        /cdrom                   vfat       (rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)


============================== sde1/syslinux.cfg: ==============================

--------------------------------------------------------------------------------
default menu.c32 
prompt 0 
menu title UNetbootin 
timeout 100 
 
label unetbootindefault 
menu label Default 
kernel /ubnkern 
append initrd=/ubninit file=/cdrom/preseed/ubuntu.seed boot=casper quiet splash -- persistent 
 
label ubnentry0 
menu label ^Help 
kernel /ubnkern 
append initrd=/ubninit  persistent 
 
label ubnentry1 
menu label ^Try Ubuntu without installing 
kernel /casper/vmlinuz 
append initrd=/casper/initrd.lz file=/cdrom/preseed/ubuntu.seed boot=casper  quiet splash -- persistent 
 
label ubnentry2 
menu label ^Install Ubuntu 
kernel /casper/vmlinuz 
append initrd=/casper/initrd.lz file=/cdrom/preseed/ubuntu.seed boot=casper only-ubiquity  quiet splash -- persistent 
 
label ubnentry3 
menu label ^Check disc for defects 
kernel /casper/vmlinuz 
append initrd=/casper/initrd.lz boot=casper integrity-check  quiet splash -- persistent 
 
label ubnentry4 
menu label Test ^memory 
kernel /install/mt86plus 
append initrd=/ubninit  persistent 
 
label ubnentry5 
menu label ^Boot from first hard disk 
kernel /ubnkern 
append initrd=/ubninit  persistent 
 
--------------------------------------------------------------------------------

================= sde1: Location of files loaded by Syslinux: ==================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             syslinux.cfg                                   1
            ?? = ??             ldlinux.sys                                    1
            ?? = ??             menu.c32                                       1

============== sde1: Version of COM32(R) files used by Syslinux: ===============

 menu.c32                           :  COM32R module (v4.xx)

============================= md/3/grub/grub.cfg: ==============================

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

insmod raid
insmod raid5rec
insmod mdraid1x
insmod part_msdos
insmod part_msdos
insmod part_msdos
insmod part_msdos
insmod ext2
set root='(mduuid/e5fe242fe6fbb62b152451c13f7d58fb)'
search --no-floppy --fs-uuid --set=root 16a0b094-4635-4b14-bdd7-a5601c2e3694
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  insmod raid
  insmod mdraid1x
  insmod part_msdos
  insmod part_msdos
  insmod part_msdos
  insmod part_msdos
  insmod ext2
  set root='(mduuid/1f8a6ffb01a069042bbbf568dc263a0c)'
  search --no-floppy --fs-uuid --set=root 6f393cca-bbdd-492f-a575-ee2bfefd7e2c
  set locale_dir=($root)/grub/locale
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
menuentry 'Ubuntu, with Linux 3.2.0-37-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    gfxmode $linux_gfx_mode
    insmod gzio
    insmod raid
    insmod mdraid1x
    insmod part_msdos
    insmod part_msdos
    insmod part_msdos
    insmod part_msdos
    insmod ext2
    set root='(mduuid/1f8a6ffb01a069042bbbf568dc263a0c)'
    search --no-floppy --fs-uuid --set=root 6f393cca-bbdd-492f-a575-ee2bfefd7e2c
    linux    /vmlinuz-3.2.0-37-generic-pae root=UUID=16a0b094-4635-4b14-bdd7-a5601c2e3694 ro   quiet splash $vt_handoff
    initrd    /initrd.img-3.2.0-37-generic-pae
}
menuentry 'Ubuntu, with Linux 3.2.0-37-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod raid
    insmod mdraid1x
    insmod part_msdos
    insmod part_msdos
    insmod part_msdos
    insmod part_msdos
    insmod ext2
    set root='(mduuid/1f8a6ffb01a069042bbbf568dc263a0c)'
    search --no-floppy --fs-uuid --set=root 6f393cca-bbdd-492f-a575-ee2bfefd7e2c
    echo    'Loading Linux 3.2.0-37-generic-pae ...'
    linux    /vmlinuz-3.2.0-37-generic-pae root=UUID=16a0b094-4635-4b14-bdd7-a5601c2e3694 ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /initrd.img-3.2.0-37-generic-pae
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/30_os-prober ###
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

=================== md/3: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

   0.204690933 = 0.219785216    grub/grub.cfg                                  1
   0.203501701 = 0.218508288    grub/core.img                                  3
   0.006648064 = 0.007138304    vmlinuz-3.2.0-37-generic-pae                  21
   0.024569511 = 0.026381312    initrd.img-3.2.0-37-generic-pae               58

=========================== md/2/boot/grub/grub.cfg: ===========================

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

insmod raid
insmod raid5rec
insmod mdraid1x
insmod part_msdos
insmod part_msdos
insmod part_msdos
insmod part_msdos
insmod ext2
set root='(mduuid/e5fe242fe6fbb62b152451c13f7d58fb)'
search --no-floppy --fs-uuid --set=root 16a0b094-4635-4b14-bdd7-a5601c2e3694
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  insmod part_msdos
  insmod ext2
  set root='(hd0,msdos2)'
  search --no-floppy --fs-uuid --set=root 35fad17e-9ae5-4293-8489-0ced02d6a0c6
  set locale_dir=($root)/grub/locale
  set lang=en_GB
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
if [ "${linux_gfx_mode}" != "text" ]; then load_video; fi
menuentry 'Ubuntu, with Linux 3.2.0-35-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    gfxmode $linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set=root 35fad17e-9ae5-4293-8489-0ced02d6a0c6
    linux    /vmlinuz-3.2.0-35-generic-pae root=UUID=16a0b094-4635-4b14-bdd7-a5601c2e3694 ro persistent  quiet splash $vt_handoff
    initrd    /initrd.img-3.2.0-35-generic-pae
}
menuentry 'Ubuntu, with Linux 3.2.0-35-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set=root 35fad17e-9ae5-4293-8489-0ced02d6a0c6
    echo    'Loading Linux 3.2.0-35-generic-pae ...'
    linux    /vmlinuz-3.2.0-35-generic-pae root=UUID=16a0b094-4635-4b14-bdd7-a5601c2e3694 ro recovery nomodeset persistent
    echo    'Loading initial ramdisk ...'
    initrd    /initrd.img-3.2.0-35-generic-pae
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, with Linux 3.2.0-34-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    gfxmode $linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set=root 35fad17e-9ae5-4293-8489-0ced02d6a0c6
    linux    /vmlinuz-3.2.0-34-generic-pae root=UUID=16a0b094-4635-4b14-bdd7-a5601c2e3694 ro persistent  quiet splash $vt_handoff
    initrd    /initrd.img-3.2.0-34-generic-pae
}
menuentry 'Ubuntu, with Linux 3.2.0-34-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set=root 35fad17e-9ae5-4293-8489-0ced02d6a0c6
    echo    'Loading Linux 3.2.0-34-generic-pae ...'
    linux    /vmlinuz-3.2.0-34-generic-pae root=UUID=16a0b094-4635-4b14-bdd7-a5601c2e3694 ro recovery nomodeset persistent
    echo    'Loading initial ramdisk ...'
    initrd    /initrd.img-3.2.0-34-generic-pae
}
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set=root 35fad17e-9ae5-4293-8489-0ced02d6a0c6
    linux16    /memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set=root 35fad17e-9ae5-4293-8489-0ced02d6a0c6
    linux16    /memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
if [ "x${timeout}" != "x-1" ]; then
  if keystatus; then
    if keystatus --shift; then
      set timeout=10
    else
      set timeout=10
    fi
  else
    if sleep --interruptible 3 ; then
      set timeout=10
    fi
  fi
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

=================== md/2: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

1022.144927979 = 1097.519759360 boot/grub/grub.cfg                             1
1022.132480621 = 1097.506394112 boot/grub/core.img                             1
1022.129673004 = 1097.503379456 boot/vmlinuz-3.2.0-34-generic-pae              1
1022.142627716 = 1097.517289472 boot/vmlinuz-3.2.0-35-generic-pae              1
   0.384674072 = 0.413040640    boot/initrd.img-3.2.0-34-generic-pae           2
   0.390438080 = 0.419229696    boot/initrd.img-3.2.0-35-generic-pae           2

=============================== md/1/etc/fstab: ================================

--------------------------------------------------------------------------------
#    /etc/fstab:    static    file    system    information.
#
#    Use    'blkid'    to    print    the    universally    unique    identifier    for    a
#    device;    this    may    be    used    with    UUID=    as    a    more    robust    way    to    name    devices
#    that    works    even    if    disks    are    added    and    removed.    See    fstab(5).
#
#    <file    system>    <mount    point>    <type>    <options>    <dump>    <pass>
proc    /proc    proc    nodev,noexec,nosuid    0    0
#    /    was    on    /dev/md1    during    installation
UUID=16a0b094-4635-4b14-bdd7-a5601c2e3694    /    ext4    errors=remount-ro,acl,user_xattr    0    1
#/dev/md1    /    ext4    errors=remount-ro,acl,user_xattr    0
#    /boot    was    on    /dev/sda2    during    installation
#    /home    was    on    /dev/md2    during    installation
UUID=29342fce-67ac-43ec-b95d-a94366c28a2a    /home    ext4    defaults,usrquota,grpquota,acl,user_xattr    0    2
#/dev/md2    /home    ext4    defaults,usrquota,grpquota,acl,user_xattr    0    2
#    swap    was    on    /dev/md0    during    installation
UUID=abd98da1-fe2b-41e1-998d-a313d4cd64c3    none    swap    sw    0    0
#/dev/md0    none    swap    sw    0    0
none    /run/lock    tmpfs    rw,noexec,nosuid,nodev,size=52428800    0    0
#/dev/md3    /boot    ext2    defaults    0    2
UUID=6f393cca-bbdd-492f-a575-ee2bfefd7e2c    /boot    ext2    defaults    0    2
--------------------------------------------------------------------------------

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda4

00000000  78 84 bb 47 6c e3 e7 66  0a b2 26 49 07 a7 4f ca  |x..Gl..f..&I..O.|
00000010  bd 76 5f 0f ea 71 a5 bc  97 11 98 fe d3 10 b8 89  |.v_..q..........|
00000020  19 88 62 a7 a6 7d 33 5c  f3 72 57 2e 9c a2 a7 66  |..b..}3\.rW....f|
00000030  ce 97 43 f0 ed e4 ec 0a  a1 70 a7 e6 23 38 af a5  |..C......p..#8..|
00000040  7e 1c f8 0a 7b 8d 42 d1  9e 32 ec e4 17 1b 4e 00  |~...{.B..2....N.|
00000050  ce 6b 92 71 e7 3d 39 d6  82 87 2b 67 a7 fc 7f b8  |.k.q.=9...+g....|
00000060  93 c2 5e 17 b7 d3 e2 71  04 2d 64 5e 40 1b 05 9b  |..^....q.-d^@...|
00000070  b1 3f a7 1f 4f 5c d7 e3  87 89 af 17 50 d4 ee 19  |.?..O\......P...|
00000080  9f e4 12 90 ab 9c 80 2b  d5 a6 bf 73 18 d8 e7 8b  |.......+...s....|
00000090  70 a2 e4 96 e7 2f 24 28  7f 87 80 30 08 e4 0a 88  |p..../$(...0....|
000000a0  5b 85 3c e0 77 34 34 e2  d6 87 9b 29 b5 26 5a 88  |[.<.w44....).&Z.|
000000b0  00 38 c6 7a 76 ab 0b 82  71 8c e6 b6 56 6c a4 ee  |.8.zv...q...Vl..|
000000c0  ae 5e 84 64 f3 f8 57 47  63 06 ec 15 ec 3e a4 9a  |.^.d..WGc....>..|
000000d0  e8 8c 7a 23 39 49 ea ac  74 f6 f6 47 8d c0 f5 04  |..z#9I..t..G....|
000000e0  7c a4 9a eb b4 7b 33 b8  02 a0 60 fa 0c e3 f4 ad  ||....{3...`.....|
000000f0  e9 c3 de d0 89 49 f2 e8  8f 4b b1 40 8a 0f 6c 67  |.....I...K.@..lg|
00000100  35 d4 db c8 ae a9 ff 00  7c f1 c8 35 d7 28 da c6  |5.......|..5.(..|
00000110  14 e3 76 dc 91 b1 69 18  27 ee 93 cf 6f 4a e5 3e  |..v...i.'...oJ.>|
00000120  29 48 2d fc 3d b7 20 16  62 c5 4e 01 c5 65 37 68  |)H-.=. .b.N..e7h|
00000130  b6 75 d3 b3 92 47 c6 37  12 16 99 db 27 1b c5 6a  |.u...G.7....'..j|
00000140  58 7c e7 27 a0 f5 af 3e  32 6e fa 17 2b a4 ce aa  |X|.'...>2n..+...|
00000150  d4 03 8f 7c f1 de ba db  18 72 07 c8 49 03 af 7a  |...|.....r..I..z|
00000160  e8 84 1e a6 17 37 23 b7  20 67 b9 19 39 e7 9a da  |.....7#. g..9...|
00000170  d3 d5 83 0c 71 fe 1c d6  b1 85 9e c6 aa ed 2d 0e  |....q.........-.|
00000180  96 44 32 da ca a7 a3 46  cb fa 57 c7 fe 32 cc 3a  |.D2....F..W..2.:|
00000190  8d c8 23 9d c4 f4 cf 35  8e 26 37 4d dc e8 a6 ed  |..#....5.&7M....|
000001a0  74 70 c0 ee 73 c7 7c f3  eb 5a 09 bc e0 f1 f8 f5  |tp..s.|..Z......|
000001b0  af 39 25 aa 31 93 b5 da  2f 89 36 0e 30 18 71 8a  |.9%.1.../.6.0.q.|
000001c0  d7 b1 d4 0a b8 07 2d c0  ce 7e b4 4a 0d ec 28 36  |......-..~.J..(6|
000001d0  ee 7b 7f 83 f1 76 d1 c6  cb 9d e3 04 1e 46 33 58  |.{...v.......F3X|
000001e0  7e 3d d2 e3 d3 ae c7 94  a1 09 0d c8 03 9e f4 e8  |~=..............|
000001f0  b1 d9 5e f6 3c e0 38 2d  ec 70 48 1d 2b 5e da 40  |..^.<.8-.pH.+^.@|
00000200

Unknown BootLoader on sdb4

00000000  98 1b 8d 42 75 92 ea e1  88 2c 88 3b 12 7a 7a 71  |...Bu....,.;.zzq|
00000010  e9 45 44 9d 45 2b ec 75  51 69 c1 b7 a5 cd 3f 1e  |.ED.E+.uQi....?.|
00000020  dd 59 5a e9 57 36 af 72  b6 ed 75 6c 02 9c 85 66  |.YZ.W6.r..ul...f|
00000030  24 74 1d 7a 8e 0d 7c ff  00 f0 ae d6 6d 33 53 f1  |$t.z..|.....m3S.|
00000040  05 d4 96 ea 83 ca 66 b6  93 68 c2 a0 3f 2b 7e 59  |......f..h..?+~Y|
00000050  fd 2b a9 46 f1 4d 18 c9  da e9 33 ea 3f 87 73 69  |.+.F.M....3.?.si|
00000060  f7 9a 36 b3 e2 1b f9 f7  85 9f ec d1 5d 4e e3 e6  |..6.........]N..|
00000070  20 1f 91 07 7c 63 24 fd  3d 6b c5 60 f1 1d db 78  | ...|c$.=k.`...x|
00000080  bf 58 9c 46 60 59 2e 1a  c6 3b 9b 91 80 ca 3a 85  |.X.F`Y...;....:.|
00000090  cf 7c 1e 71 52 a4 d4 d3  44 c2 0f de 4d 1d b5 e6  |.|.qR...D...M...|
000000a0  9b 75 3d c4 06 ce d5 ae  0c 25 5d 42 20 54 56 3d  |.u=......%]B TV=|
000000b0  4b 1e fc 71 8f 53 58 1a  7f 85 ed 2d 3c 4f 7d e2  |K..q.SX....-<O}.|
000000c0  6d 52 57 d4 2e ee a3 68  40 c1 d9 18 39 f9 13 24  |mRW....h@...9..$|
000000d0  fa e0 9a aa cd 3b 73 19  34 e5 a4 4f 73 d3 b5 8b  |.....;s.4..Os...|
000000e0  2f 0e 78 6e 69 2c 34 f8  22 bb bf df 1c 11 b2 0d  |/.xni,4.".......|
000000f0  d8 23 93 eb 9c 1e 95 e3  3a 7f 87 35 0d 57 53 33  |.#......:..5.WS3|
00000100  dd c7 e4 cb 79 39 9d 93  00 b1 05 8e 3e 9f 8d 4d  |....y9......>..M|
00000110  56 aa a8 42 2a c6 b8 59  4a 8f 35 46 f5 67 a4 f8  |V..B*..YJ.5F.g..|
00000120  cb 53 d0 fc 19 a2 5b e8  37 f7 82 e2 f2 e6 31 33  |.S....[.7.....13|
00000130  d8 db 32 96 8d 3d 58 8c  e0 9e c3 ad 73 36 57 cd  |..2..=X.....s6W.|
00000140  05 a5 b5 eb db 8b 4b 59  6d fe d3 1f 9a d9 98 c7  |......KYm.......|
00000150  d9 40 e8 bb ba e4 f3 8a  6d c7 da 7b 34 5c a9 c9  |.@......m..{4\..|
00000160  d3 e7 7d 4f 2f d6 26 d5  64 d3 35 2b eb eb 82 e9  |..}O/.&.d.5+....|
00000170  35 c3 25 95 b5 b3 06 76  52 78 e7 a2 f5 03 f1 35  |5.%....vRx.....5|
00000180  05 87 86 65 8f c2 37 1a  ec e5 65 f2 49 fb 3d bc  |...e..7...e.I.=.|
00000190  40 31 92 5c 72 33 fc 5b  7a 7a 73 ef 59 a8 bf 69  |@1.\r3.[zzs.Y..i|
000001a0  76 f4 22 52 7c 89 58 f3  df 0e 5f ea 16 b0 ea 1a  |v."R|.X..._.....|
000001b0  92 59 ac 30 dd 92 93 6a  32 b9 54 89 07 de 54 f5  |.Y.0...j2.T...T.|
000001c0  3e a4 73 cf bd 78 d5 b7  8b f4 d3 e3 1b 89 af 6d  |>.s..x.........m|
000001d0  8d e4 2d 7a b0 58 d8 4b  f3 24 93 1c 00 ee 3d 89  |..-z.X.K.$....=.|
000001e0  c8 1d 3d 7a 52 73 70 5b  1a aa 4a ee 4d 9f 44 9b  |..=zRsp[..J.M.D.|
000001f0  57 b8 63 a2 cc 82 dd 3c  91 a9 dd 24 10 80 55 88  |W.c....<...$..U.|
00000200

Unknown BootLoader on sdc4

00000000  9b ab 73 aa 69 b6 b2 9b  bf 37 75 ad 8c 19 d8 08  |..s.i....7u.....|
00000010  e4 7c bf 4f 5f 5f 6c d4  5a ef 86 ef bc 59 a9 2f  |.|.O__l.Z....Y./|
00000020  87 ac 2d bc ab bd 5e e9  6d 22 9e 75 2d e4 c5 fc  |..-...^.m".u-...|
00000030  6d f4 03 8f cb de bd ac  46 12 ae 23 14 95 ac 99  |m.......F..#....|
00000040  e5 d3 a9 18 c6 5a ec 7b  cf 87 3e 1a 3f 83 21 b6  |.....Z.{..>.?.!.|
00000050  d0 7c 31 a2 4b ab 47 6b  10 86 fb 5c 92 30 96 ed  |.|1.K.Gk...\.0..|
00000060  37 74 42 47 38 3d 58 67  af e7 c9 68 37 cd 7d f1  |7tBG8=Xg...h7.}.|
00000070  6f 52 d2 f5 23 6d 79 06  83 62 d1 5e 1b 6d c2 de  |oR..#my..b.^.m..|
00000080  3b 87 c7 ca 1f f8 ca 02  06 7b 9f ad 75 63 30 34  |;........{..uc04|
00000090  70 38 27 2e c4 51 ab 3a  f3 6d 33 e8 2f 16 dd 46  |p8'..Q.:.m3./..F|
000000a0  9a 3e 9f 69 a7 3c cd 74  ec 62 b5 81 18 28 2a 7a  |.>.i.<.t.b...(*z|
000000b0  e0 8e 73 5e 17 77 e3 1d  28 36 b0 de 33 b9 b0 b9  |..s^.w..(6..3...|
000000c0  bc d1 6c c5 86 83 a6 48  76 5b db 4b 8c ee 55 ea  |..l....Hv[.K..U.|
000000d0  e4 64 9c 8e ad d7 a1 15  e2 e1 b3 4a 72 b3 b9 da  |.d.........Jr...|
000000e0  a8 4d c5 b4 b5 3c e6 f1  f4 af 10 68 f3 cd a8 b5  |.M...<.....h....|
000000f0  c6 a7 71 29 50 cf 2a 36  c8 e0 1f 78 29 39 55 2c  |..q)P.*6...x)9U,|
00000100  71 d0 67 af 3c 57 23 37  c4 59 6c a1 9e 4b 0b 85  |q.g.<W#7.Yl..K..|
00000110  78 ad c0 b4 b3 b6 80 11  23 b0 18 25 8f 4e d8 c0  |x.......#..%.N..|
00000120  f4 24 d7 c9 55 c6 54 ad  98 d4 97 46 7a 14 25 2e  |.$..U.T....Fz.%.|
00000130  45 09 1f 43 78 1f 59 13  f8 3a c2 eb c4 37 0a 2f  |E..Cx.Y..:...7./|
00000140  ef 6e 13 fb 1f 4b 57 55  50 d9 e5 98 75 24 1c 71  |.n...KWUP...u$.q|
00000150  eb c9 af a9 34 6f 0f 41  ad fd 9f ed 1a c4 ba ad  |....4o.A........|
00000160  ec b0 a4 5f 65 57 2b 12  12 30 aa 54 63 24 67 bf  |..._eW+..0.Tc$g.|
00000170  19 af 62 83 b4 a3 29 33  2a b1 92 94 a3 63 e3 4f  |..b...)3*....c.O|
00000180  da 7b e1 4d b6 81 74 d2  58 5f c9 7d 79 96 dd 0d  |.{.M..t.X_.}y...|
00000190  a3 0f 25 5b b8 1b 7a e3  d7 f2 f5 af 9b 3e 1a f8  |..%[..z......>..|
000001a0  0a e3 4f 9e e2 e5 6c a5  bb f1 2e a0 c1 a2 89 10  |..O...l.........|
000001b0  93 1a 67 00 01 db 3d c9  af 97 cf 61 53 11 8d f6  |..g...=....aS...|
000001c0  31 d7 98 e9 8d 7e 5a 0b  99 6c 7e 82 f8 1f 48 d7  |1....~Z..l~...H.|
000001d0  bc 03 e1 fd 27 56 f1 24  b3 5a dd dd c8 1e 0d 22  |....'V.$.Z....."|
000001e0  de 4c bb e3 27 32 1e 30  bc e0 0f c7 eb e4 bf 11  |.L..'2.0........|
000001f0  bc 45 16 a7 e3 3b 5d 52  5b e9 5b 53 91 0b dd 79  |.E...;]R[.[S...y|
00000200

Unknown BootLoader on sdd4

00000000  7b 34 45 af 70 c7 bf 1c  3d a9 db df 99 c4 ed b3  |{4E.p...=.......|
00000010  b0 4f a4 dd f0 05 25 1d  9c 97 df a6 ca 84 2e b8  |.O....%.........|
00000020  43 7d 15 f2 5a f6 c2 c7  28 bd bc 37 b3 da e7 fc  |C}..Z...(..7....|
00000030  87 17 5d 05 a8 37 2d 59  e7 92 a7 13 5a 9e 50 cd  |..]..7-Y....Z.P.|
00000040  9e 1b c7 f8 3e 1d c8 1c  c2 dd 10 5e 17 b3 11 ef  |....>......^....|
00000050  e3 3c 0a 95 5d db 66 74  48 e8 e3 d1 0a 4b 9a 3c  |.<..].ftH....K.<|
00000060  53 2c 2a e3 6d f5 43 e1  2e 55 41 e7 2a 98 9b 8c  |S,*.m.C..UA.*...|
00000070  fe 72 e4 ed 10 52 8a 18  39 80 bb 29 ba a4 f7 bf  |.r...R..9..)....|
00000080  1b 3b 49 1c d4 3d 64 33  15 e6 bb 4f ed 71 ed 3a  |.;I..=d3...O.q.:|
00000090  cf e6 dd c9 71 da 5b c1  c8 28 bc 06 6a ef 62 28  |....q.[..(..j.b(|
000000a0  5a ce 9e 4d d6 c6 2c 38  36 c0 73 ea 8d 5a 26 cf  |Z..M..,86.s..Z&.|
000000b0  ab a8 49 55 ee 8f b0 85  26 3f bb 45 59 9a 69 b5  |..IU....&?.EY.i.|
000000c0  7f dd bf 75 5b 95 52 67  55 9c ee 46 59 29 e2 54  |...u[.RgU..FY).T|
000000d0  f6 08 7c 07 59 a5 38 a0  a2 f2 e1 42 8c a0 f9 55  |..|.Y.8....B...U|
000000e0  fb e7 27 31 68 6b e1 b1  d4 b4 cf 4d e3 3f ee 15  |..'1hk.....M.?..|
000000f0  f7 47 3c 12 45 98 4d 3d  7d d4 29 0d ae 61 6a 78  |.G<.E.M=}.)..ajx|
00000100  99 c3 58 ac eb c7 41 a4  b8 19 a1 1a 77 fc 5c 0e  |..X...A.....w.\.|
00000110  3a e4 1e 2a 08 c1 51 50  4e d1 be ac 15 63 99 06  |:..*..QPN....c..|
00000120  16 3f 2a c9 71 d3 2f 53  cd e6 5b a5 4d 97 23 75  |.?*.q./S..[.M.#u|
00000130  2b a7 fe 66 67 65 c7 a8  0a b2 98 9d 90 1a 98 88  |+..fge..........|
00000140  b2 b7 41 37 64 35 b3 32  0f 49 cc 90 c4 59 4a 1c  |..A7d5.2.I...YJ.|
00000150  e6 8a c8 6e 7f 55 46 10  d8 48 42 5e 67 9b bc 1e  |...n.UF..HB^g...|
00000160  d7 d3 c7 b6 5d b6 2e 70  56 84 26 66 b1 28 7f 8c  |....]..pV.&f.(..|
00000170  ff b9 c4 1a 70 ee 33 93  c9 4c eb f0 fc 8d 3f 74  |....p.3..L....?t|
00000180  49 b8 55 f2 f3 e4 e0 8e  7f 40 fb 48 ce 5f 2c 8b  |I.U......@.H._,.|
00000190  6e f6 94 9a 0e dc 49 8d  23 ae b1 0d 1e 7e 03 7c  |n.....I.#....~.||
000001a0  08 67 ad 22 ed ab 48 a5  8f a5 78 f6 37 e3 9b ff  |.g."..H...x.7...|
000001b0  ae 7a ee 9a ed da 1b 79  b2 a7 ad e6 64 d7 a8 89  |.z.....y....d...|
000001c0  d8 c2 3f 2c 88 01 a2 7c  dc e6 19 2b ee 7a cf 8c  |..?,...|...+.z..|
000001d0  df 9c b3 04 66 78 f8 a9  8b e3 ad c5 d6 b6 03 f3  |....fx..........|
000001e0  68 6c 54 7a a6 ef a9 ff  07 43 48 e1 a5 e5 0f 62  |hlTz.....CH....b|
000001f0  5a 24 2b f3 13 59 b8 43  26 30 ce 6a aa d5 52 b1  |Z$+..Y.C&0.j..R.|
00000200



ADDITIONAL INFORMATION :
=================== log of boot-repair 2013-02-09__21h51 ===================
boot-repair version : 3.197~ppa31~precise
boot-sav version : 3.197~ppa31~precise
glade2script version : 3.2.2~ppa45~precise
boot-sav-extra version : 3.197~ppa31~precise

BLKID BEFORE RAID ACTIVATION:
/dev/loop0: TYPE="squashfs"
/dev/loop1: UUID="d45af0b4-4582-0e4c-847e-f6e36cda5002" TYPE="ext2"
/dev/sda1: UUID="e7beb7c1-0d2d-2af7-f5f2-9ca7ace79a50" UUID_SUB="5e3ce442-b1d4-2750-bbb0-50d102b38d6d" LABEL="zen1:0" TYPE="linux_raid_member"
/dev/sda2: UUID="1f8a6ffb-01a0-6904-2bbb-f568dc263a0c" UUID_SUB="b6d09a5d-31fd-4aee-e91e-578aa665f3cc" LABEL="zen1:3" TYPE="linux_raid_member"
/dev/sda3: UUID="684ece4d-38f9-6eb6-7d75-c0862ff179ea" UUID_SUB="862b6c69-d8c5-96bb-fd15-c35c98a8973d" LABEL="zen1:2" TYPE="linux_raid_member"
/dev/sda4: UUID="e5fe242f-e6fb-b62b-1524-51c13f7d58fb" UUID_SUB="00cc9263-8acb-04c8-3a81-2b4a6542081c" LABEL="zen1:1" TYPE="linux_raid_member"
/dev/sdb1: UUID="e7beb7c1-0d2d-2af7-f5f2-9ca7ace79a50" UUID_SUB="350d7c45-db09-f816-c8f4-916feca5da56" LABEL="zen1:0" TYPE="linux_raid_member"
/dev/sdb2: UUID="1f8a6ffb-01a0-6904-2bbb-f568dc263a0c" UUID_SUB="8b9f1539-e8c6-ffbe-8d3f-620a028520ff" LABEL="zen1:3" TYPE="linux_raid_member"
/dev/sdb3: UUID="684ece4d-38f9-6eb6-7d75-c0862ff179ea" UUID_SUB="1251e60d-4ae3-598e-4ab7-f1a3008d3210" LABEL="zen1:2" TYPE="linux_raid_member"
/dev/sdb4: UUID="e5fe242f-e6fb-b62b-1524-51c13f7d58fb" UUID_SUB="f015af83-d45e-708b-95fe-78c8cef2f4f2" LABEL="zen1:1" TYPE="linux_raid_member"
/dev/sdc1: UUID="e7beb7c1-0d2d-2af7-f5f2-9ca7ace79a50" UUID_SUB="3adb2d89-448e-fa9b-16da-ec9cfb09e027" LABEL="zen1:0" TYPE="linux_raid_member"
/dev/sdc2: UUID="1f8a6ffb-01a0-6904-2bbb-f568dc263a0c" UUID_SUB="2c5ec6b7-70ce-78b2-2298-640e22d66d5a" LABEL="zen1:3" TYPE="linux_raid_member"
/dev/sdc3: UUID="684ece4d-38f9-6eb6-7d75-c0862ff179ea" UUID_SUB="eac92093-8e8d-cf8f-ffff-62ca7312edc7" LABEL="zen1:2" TYPE="linux_raid_member"
/dev/sdc4: UUID="e5fe242f-e6fb-b62b-1524-51c13f7d58fb" UUID_SUB="2fa9660d-b628-c0b9-6165-efea828e0770" LABEL="zen1:1" TYPE="linux_raid_member"
/dev/sdd1: UUID="e7beb7c1-0d2d-2af7-f5f2-9ca7ace79a50" UUID_SUB="e994aa6b-9bd7-7ffa-bd11-55f78b594be0" LABEL="zen1:0" TYPE="linux_raid_member"
/dev/sdd2: UUID="1f8a6ffb-01a0-6904-2bbb-f568dc263a0c" UUID_SUB="52919a92-5851-e0e3-ee34-6083ad9a867b" LABEL="zen1:3" TYPE="linux_raid_member"
/dev/sdd3: UUID="684ece4d-38f9-6eb6-7d75-c0862ff179ea" UUID_SUB="0f48df39-b808-a6f7-91c2-579dfb00375a" LABEL="zen1:2" TYPE="linux_raid_member"
/dev/sdd4: UUID="e5fe242f-e6fb-b62b-1524-51c13f7d58fb" UUID_SUB="2301c8fe-fcab-d624-ee02-023f49c178bd" LABEL="zen1:1" TYPE="linux_raid_member"
/dev/sde1: LABEL="UBUNTU-SERV" UUID="B868-BF20" TYPE="vfat"
/dev/md0: UUID="abd98da1-fe2b-41e1-998d-a313d4cd64c3" TYPE="swap"
/dev/md3: UUID="6f393cca-bbdd-492f-a575-ee2bfefd7e2c" TYPE="ext2"
/dev/md2: UUID="29342fce-67ac-43ec-b95d-a94366c28a2a" TYPE="ext4"
/dev/md1: UUID="16a0b094-4635-4b14-bdd7-a5601c2e3694" TYPE="ext4"
dmraid -si -c: no raid disks
No DMRAID disk.
[dmraid] packages may interfer with MDraid. Do you want to remove them? yes
apt-get remove -y --force-yes dmraid
The following packages will be REMOVED:
dmraid
0 upgraded, 0 newly installed, 1 to remove and 353 not upgraded.
(Reading database ... [email]SET@_progressbar1.pulse[/email]()
149170 files and directories currently installed.)
Removing dmraid ...
update-initramfs: deferring update (trigger activated)
Processing triggers for man-db ...
debconf: unable to initialize frontend: Dialog
debconf: (Dialog frontend will not work on a dumb terminal, an emacs shell buffer, or without a controlling terminal.)
debconf: falling back to frontend: Readline
debconf: unable to initialize frontend: Readline
debconf: (This frontend requires a controlling tty.)
debconf: falling back to frontend: Teletype
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-3.2.0-29-generic-pae
cryptsetup: WARNING: failed to detect canonical device of overlayfs
cryptsetup: WARNING: could not determine root device from /etc/fstab
Scanning MDraid Partitions
mdadm --detail --scan: ARRAY /dev/md/0 metadata=1.2 name=zen1:0 UUID=e7beb7c1:0d2d2af7:f5f29ca7:ace79a50
ARRAY /dev/md/3 metadata=1.2 name=zen1:3 UUID=1f8a6ffb:01a06904:2bbbf568:dc263a0c
ARRAY /dev/md/2 metadata=1.2 name=zen1:2 UUID=684ece4d:38f96eb6:7d75c086:2ff179ea
ARRAY /dev/md/1 metadata=1.2 name=zen1:1 UUID=e5fe242f:e6fbb62b:152451c1:3f7d58fb
boot-repair is executed in live-session (Ubuntu 12.04.1 LTS, precise, Ubuntu, i686)
CPU op-mode(s):        32-bit, 64-bit
initrd=/ubninit file=/cdrom/preseed/ubuntu.seed boot=casper quiet splash -- persistent BOOT_IMAGE=/ubnkern
Set sda as corresponding disk of md3
Set sda as corresponding disk of md2
Set sda as corresponding disk of md1
Disk /dev/md0 doesn't contain a valid partition table
Disk /dev/md3 doesn't contain a valid partition table
Disk /dev/md2 doesn't contain a valid partition table
Disk /dev/md1 doesn't contain a valid partition table

=================== os-prober:


=================== blkid:
/dev/loop0: TYPE="squashfs"
/dev/loop1: UUID="d45af0b4-4582-0e4c-847e-f6e36cda5002" TYPE="ext2"
/dev/sda1: UUID="e7beb7c1-0d2d-2af7-f5f2-9ca7ace79a50" UUID_SUB="5e3ce442-b1d4-2750-bbb0-50d102b38d6d" LABEL="zen1:0" TYPE="linux_raid_member"
/dev/sda2: UUID="1f8a6ffb-01a0-6904-2bbb-f568dc263a0c" UUID_SUB="b6d09a5d-31fd-4aee-e91e-578aa665f3cc" LABEL="zen1:3" TYPE="linux_raid_member"
/dev/sda3: UUID="684ece4d-38f9-6eb6-7d75-c0862ff179ea" UUID_SUB="862b6c69-d8c5-96bb-fd15-c35c98a8973d" LABEL="zen1:2" TYPE="linux_raid_member"
/dev/sda4: UUID="e5fe242f-e6fb-b62b-1524-51c13f7d58fb" UUID_SUB="00cc9263-8acb-04c8-3a81-2b4a6542081c" LABEL="zen1:1" TYPE="linux_raid_member"
/dev/sdb1: UUID="e7beb7c1-0d2d-2af7-f5f2-9ca7ace79a50" UUID_SUB="350d7c45-db09-f816-c8f4-916feca5da56" LABEL="zen1:0" TYPE="linux_raid_member"
/dev/sdb2: UUID="1f8a6ffb-01a0-6904-2bbb-f568dc263a0c" UUID_SUB="8b9f1539-e8c6-ffbe-8d3f-620a028520ff" LABEL="zen1:3" TYPE="linux_raid_member"
/dev/sdb3: UUID="684ece4d-38f9-6eb6-7d75-c0862ff179ea" UUID_SUB="1251e60d-4ae3-598e-4ab7-f1a3008d3210" LABEL="zen1:2" TYPE="linux_raid_member"
/dev/sdb4: UUID="e5fe242f-e6fb-b62b-1524-51c13f7d58fb" UUID_SUB="f015af83-d45e-708b-95fe-78c8cef2f4f2" LABEL="zen1:1" TYPE="linux_raid_member"
/dev/sdc1: UUID="e7beb7c1-0d2d-2af7-f5f2-9ca7ace79a50" UUID_SUB="3adb2d89-448e-fa9b-16da-ec9cfb09e027" LABEL="zen1:0" TYPE="linux_raid_member"
/dev/sdc2: UUID="1f8a6ffb-01a0-6904-2bbb-f568dc263a0c" UUID_SUB="2c5ec6b7-70ce-78b2-2298-640e22d66d5a" LABEL="zen1:3" TYPE="linux_raid_member"
/dev/sdc3: UUID="684ece4d-38f9-6eb6-7d75-c0862ff179ea" UUID_SUB="eac92093-8e8d-cf8f-ffff-62ca7312edc7" LABEL="zen1:2" TYPE="linux_raid_member"
/dev/sdc4: UUID="e5fe242f-e6fb-b62b-1524-51c13f7d58fb" UUID_SUB="2fa9660d-b628-c0b9-6165-efea828e0770" LABEL="zen1:1" TYPE="linux_raid_member"
/dev/sdd1: UUID="e7beb7c1-0d2d-2af7-f5f2-9ca7ace79a50" UUID_SUB="e994aa6b-9bd7-7ffa-bd11-55f78b594be0" LABEL="zen1:0" TYPE="linux_raid_member"
/dev/sdd2: UUID="1f8a6ffb-01a0-6904-2bbb-f568dc263a0c" UUID_SUB="52919a92-5851-e0e3-ee34-6083ad9a867b" LABEL="zen1:3" TYPE="linux_raid_member"
/dev/sdd3: UUID="684ece4d-38f9-6eb6-7d75-c0862ff179ea" UUID_SUB="0f48df39-b808-a6f7-91c2-579dfb00375a" LABEL="zen1:2" TYPE="linux_raid_member"
/dev/sdd4: UUID="e5fe242f-e6fb-b62b-1524-51c13f7d58fb" UUID_SUB="2301c8fe-fcab-d624-ee02-023f49c178bd" LABEL="zen1:1" TYPE="linux_raid_member"
/dev/sde1: LABEL="UBUNTU-SERV" UUID="B868-BF20" TYPE="vfat"
/dev/md0: UUID="abd98da1-fe2b-41e1-998d-a313d4cd64c3" TYPE="swap"
/dev/md3: UUID="6f393cca-bbdd-492f-a575-ee2bfefd7e2c" TYPE="ext2"
/dev/md2: UUID="29342fce-67ac-43ec-b95d-a94366c28a2a" TYPE="ext4"
/dev/md1: UUID="16a0b094-4635-4b14-bdd7-a5601c2e3694" TYPE="ext4"

Linux not detected by os-prober on md1. Please report this message to [email]yannubuntu@gmail.com[/email]


=================== md1/etc/default/grub :

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




=================== md1/etc/grub.d/ :
drwxr-xr-x   2 root    root     4096 Feb  9 20:33 grub.d
drwxr-xr-x   2 root    root     4096 Feb  9 11:55 grub.d.bak
total 56
-rwxr-xr-x 1 root root 6743 Jan 22 19:19 00_header
-rwxr-xr-x 1 root root 5522 Jan 22 19:05 05_debian_theme
-rwxr-xr-x 1 root root 7780 Jan 22 19:19 10_linux
-rwxr-xr-x 1 root root 6335 Jan 22 19:19 20_linux_xen
-rwxr-xr-x 1 root root 7603 Jan 22 19:19 30_os-prober
-rwxr-xr-x 1 root root 1388 Jan 22 19:19 30_uefi-firmware
-rwxr-xr-x 1 root root  214 Jan 22 19:19 40_custom
-rwxr-xr-x 1 root root   95 Jan 22 19:19 41_custom
-rw-r--r-- 1 root root  483 Jan 22 19:19 README


/boot detected in the fstab of md1: UUID=6f393cca-bbdd-492f-a575-ee2bfefd7e2c     (md3)

=================== md1/etc/mdadm/mdadm.conf :
# mdadm.conf
#
# Please refer to mdadm.conf(5) for information about this file.
#

# by default (built-in), scan all partitions (/proc/partitions) and all
# containers for MD superblocks. alternatively, specify devices to scan, using
# wildcards if desired.
#DEVICE partitions containers

# auto-create devices with Debian standard permissions
CREATE owner=root group=disk mode=0660 auto=yes

# automatically tag new arrays as belonging to the local system
HOMEHOST <system>

# instruct the monitoring daemon where to send mail alerts
MAILADDR [email]dickychipps@sky.com[/email]

# definitions of existing MD arrays
ARRAY /dev/md/0 metadata=1.2 UUID=e7beb7c1:0d2d2af7:f5f29ca7:ace79a50 name=zen1:0
ARRAY /dev/md/2 metadata=1.2 UUID=684ece4d:38f96eb6:7d75c086:2ff179ea name=zen1:2
ARRAY /dev/md/1 metadata=1.2 UUID=e5fe242f:e6fbb62b:152451c1:3f7d58fb name=zen1:1

# This file was auto-generated on Thu, 06 Dec 2012 19:17:24 +0000
# by mkconf $Id$
DEVICE /dev/sda2 /dev/sdb2 /dev/sdc2 /dev/sdd2
ARRAY /dev/md3 level=raid1 devices=/dev/sda2,/dev/sdb2,/dev/sdc2,/dev/sdd2



=================== UEFI/Legacy mode:
This live-session is not EFI-compatible.
SecureBoot maybe enabled.


=================== PARTITIONS & DISKS:
md3    : sda,    is-sepboot,    grubenv-ok    nogrub,    no-docgrub,    no-update-grub,    32,    no-boot,    no-os,    not--efi--part,    part-has-no-fstab,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot,    nopakmgr,    nogrubinstall,    no---usr,    part-has-no-fstab,    not-sep-usr,    standard,    farbios,    /mnt/boot-sav/md3.
md2    : sda,    maybesepboot,    no-grubenv    nogrub,    no-docgrub,    no-update-grub,    32,    with-boot,    no-os,    not--efi--part,    part-has-no-fstab,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot,    nopakmgr,    nogrubinstall,    no---usr,    part-has-no-fstab,    not-sep-usr,    standard,    farbios,    /mnt/boot-sav/md2.
md1    : sda,    not-sepboot,    no-grubenv    grub2,    grub-pc ,    update-grub,    32,    no-boot,    is-os,    not--efi--part,    fstab-has-goodBOOT,    fstab-without-efi,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot,    apt-get,    grub-install,    with--usr,    fstab-without-usr,    not-sep-usr,    standard,    not-far,    /mnt/boot-sav/md1.

sda    : not-GPT,    BIOSboot-not-needed,    has-no-EFIpart,     not-usb,    has-os,    2048 sectors * 512 bytes
sdb    : not-GPT,    BIOSboot-not-needed,    has-no-EFIpart,     not-usb,    no-os,    2048 sectors * 512 bytes
sdc    : not-GPT,    BIOSboot-not-needed,    has-no-EFIpart,     not-usb,    no-os,    2048 sectors * 512 bytes
sdd    : not-GPT,    BIOSboot-not-needed,    has-no-EFIpart,     not-usb,    no-os,    2048 sectors * 512 bytes


=================== parted -l:

Model: ATA WDC WD1002FBYS-0 (scsi)
Disk /dev/sda: 1000GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
1      1049kB  4296MB  4295MB  primary               raid
4      4296MB  529GB   524GB   primary               raid
3      529GB   1000GB  471GB   primary               raid
2      1000GB  1000GB  314MB   primary  ext2         boot


Model: ATA WDC WD1002FBYS-0 (scsi)
Disk /dev/sdb: 1000GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
1      1049kB  4296MB  4295MB  primary               raid
4      4296MB  529GB   524GB   primary               raid
3      529GB   1000GB  471GB   primary               raid
2      1000GB  1000GB  314MB   primary  ext2         boot


Model: ATA WDC WD1002FBYS-0 (scsi)
Disk /dev/sdc: 1000GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
1      1049kB  4296MB  4295MB  primary               raid
4      4296MB  529GB   524GB   primary               raid
3      529GB   1000GB  471GB   primary               raid
2      1000GB  1000GB  314MB   primary  ext2         boot


Model: ATA WDC WD1002FBYS-0 (scsi)
Disk /dev/sdd: 1000GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
1      1049kB  4296MB  4295MB  primary  ext2         raid
4      4296MB  529GB   524GB   primary               raid
3      529GB   1000GB  471GB   primary               raid
2      1000GB  1000GB  314MB   primary  ext2         boot


Model: SanDisk Cruzer Blade (scsi)
Disk /dev/sde: 4005MB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
1      1049kB  4005MB  4003MB  primary  fat32        boot


Model: Linux Software RAID Array (md)
Disk /dev/md0: 12.9GB
Sector size (logical/physical): 512B/512B
Partition Table: loop

Number  Start  End     Size    File system     Flags
1      0.00B  12.9GB  12.9GB  linux-swap(v1)


Model: Linux Software RAID Array (md)
Disk /dev/md3: 313MB
Sector size (logical/physical): 512B/512B
Partition Table: loop

Number  Start  End    Size   File system  Flags
1      0.00B  313MB  313MB  ext2


Model: Linux Software RAID Array (md)
Disk /dev/md2: 1414GB
Sector size (logical/physical): 512B/512B
Partition Table: loop

Number  Start  End     Size    File system  Flags
1      0.00B  1414GB  1414GB  ext4


Model: Linux Software RAID Array (md)
Disk /dev/md1: 1572GB
Sector size (logical/physical): 512B/512B
Partition Table: loop

Number  Start  End     Size    File system  Flags
1      0.00B  1572GB  1572GB  ext4

=================== parted -lm:

BYT;
/dev/sda:1000GB:scsi:512:512:msdos:ATA WDC WD1002FBYS-0;
1:1049kB:4296MB:4295MB:::raid;
4:4296MB:529GB:524GB:::raid;
3:529GB:1000GB:471GB:::raid;
2:1000GB:1000GB:314MB:ext2::boot;

BYT;
/dev/sdb:1000GB:scsi:512:512:msdos:ATA WDC WD1002FBYS-0;
1:1049kB:4296MB:4295MB:::raid;
4:4296MB:529GB:524GB:::raid;
3:529GB:1000GB:471GB:::raid;
2:1000GB:1000GB:314MB:ext2::boot;

BYT;
/dev/sdc:1000GB:scsi:512:512:msdos:ATA WDC WD1002FBYS-0;
1:1049kB:4296MB:4295MB:::raid;
4:4296MB:529GB:524GB:::raid;
3:529GB:1000GB:471GB:::raid;
2:1000GB:1000GB:314MB:ext2::boot;

BYT;
/dev/sdd:1000GB:scsi:512:512:msdos:ATA WDC WD1002FBYS-0;
1:1049kB:4296MB:4295MB:ext2::raid;
4:4296MB:529GB:524GB:::raid;
3:529GB:1000GB:471GB:::raid;
2:1000GB:1000GB:314MB:ext2::boot;

BYT;
/dev/sde:4005MB:scsi:512:512:msdos:SanDisk Cruzer Blade;
1:1049kB:4005MB:4003MB:fat32::boot;

BYT;
/dev/md0:12.9GB:md:512:512:loop:Linux Software RAID Array;
1:0.00B:12.9GB:12.9GB:linux-swap(v1)::;

BYT;
/dev/md3:313MB:md:512:512:loop:Linux Software RAID Array;
1:0.00B:313MB:313MB:ext2::;

BYT;
/dev/md2:1414GB:md:512:512:loop:Linux Software RAID Array;
1:0.00B:1414GB:1414GB:ext4::;

BYT;
/dev/md1:1572GB:md:512:512:loop:Linux Software RAID Array;
1:0.00B:1572GB:1572GB:ext4::;


=================== mount:
/cow on / type overlayfs (rw)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
/dev/sde1 on /cdrom type vfat (rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop0 on /rofs type squashfs (ro,noatime)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)
/dev/md3 on /mnt/boot-sav/md3 type ext2 (rw)
/dev/md2 on /mnt/boot-sav/md2 type ext4 (rw)
/dev/md1 on /mnt/boot-sav/md1 type ext4 (rw)


=================== ls:
/sys/block/md0 (filtered):  alignment_offset bdi capability dev discard_alignment ext_range holders inflight md power queue range removable ro size slaves stat subsystem trace uevent
/sys/block/md1 (filtered):  alignment_offset bdi capability dev discard_alignment ext_range holders inflight md power queue range removable ro size slaves stat subsystem trace uevent
/sys/block/md2 (filtered):  alignment_offset bdi capability dev discard_alignment ext_range holders inflight md power queue range removable ro size slaves stat subsystem trace uevent
/sys/block/md3 (filtered):  alignment_offset bdi capability dev discard_alignment ext_range holders inflight md power queue range removable ro size slaves stat subsystem trace uevent
/sys/block/sda (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro sda1 sda2 sda3 sda4 size slaves stat subsystem trace uevent
/sys/block/sdb (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro sdb1 sdb2 sdb3 sdb4 size slaves stat subsystem trace uevent
/sys/block/sdc (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro sdc1 sdc2 sdc3 sdc4 size slaves stat subsystem trace uevent
/sys/block/sdd (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro sdd1 sdd2 sdd3 sdd4 size slaves stat subsystem trace uevent
/sys/block/sde (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro sde1 size slaves stat subsystem trace uevent
/sys/block/sr0 (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro size slaves stat subsystem trace uevent
/dev (filtered):  autofs block bsg btrfs-control bus cdrom cdrw char console core cpu cpu_dma_latency disk dvd dvdrw ecryptfs fd full fuse hidraw0 hidraw1 hidraw2 hpet input kmsg log mapper mcelog md md0 md1 md2 md3 mem net network_latency network_throughput null oldmem port ppp psaux ptmx pts random rfkill rtc rtc0 sda sda1 sda2 sda3 sda4 sdb sdb1 sdb2 sdb3 sdb4 sdc sdc1 sdc2 sdc3 sdc4 sdd sdd1 sdd2 sdd3 sdd4 sde sde1 sg0 sg1 sg2 sg3 sg4 sg5 shm snapshot snd sr0 stderr stdin stdout uinput urandom usbmon0 usbmon1 usbmon2 vga_arbiter zero
ls /dev/md:  0 1 2 3
ls /dev/mapper:  control
Disk /dev/md0 doesn't contain a valid partition table
Disk /dev/md3 doesn't contain a valid partition table
Disk /dev/md2 doesn't contain a valid partition table
Disk /dev/md1 doesn't contain a valid partition table

=================== df -Th:

Filesystem     Type       Size  Used Avail Use% Mounted on
/cow           overlayfs  992M  135M  807M  15% /
udev           devtmpfs   7.9G   12K  7.9G   1% /dev
tmpfs          tmpfs      3.2G  836K  3.2G   1% /run
/dev/sde1      vfat       3.8G  1.7G  2.1G  46% /cdrom
/dev/loop0     squashfs   667M  667M     0 100% /rofs
tmpfs          tmpfs      7.9G   28K  7.9G   1% /tmp
none           tmpfs      5.0M     0  5.0M   0% /run/lock
none           tmpfs      7.9G   80K  7.9G   1% /run/shm
/dev/md3       ext2       290M   29M  247M  11% /mnt/boot-sav/md3
/dev/md2       ext4       1.3T   23G  1.2T   2% /mnt/boot-sav/md2
/dev/md1       ext4       1.5T   27G  1.4T   2% /mnt/boot-sav/md1

=================== fdisk -l:

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000ce259

Device Boot      Start         End      Blocks   Id  System
/dev/sda1            2048     8390655     4194304   fd  Linux raid autodetect
/dev/sda2   *  1952911360  1953523711      306176   83  Linux
/dev/sda3      1032390656  1952911359   460260352   fd  Linux raid autodetect
/dev/sda4         8390656  1032390655   512000000   fd  Linux raid autodetect

Partition table entries are not in disk order

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000ee9f5

Device Boot      Start         End      Blocks   Id  System
/dev/sdb1            2048     8390655     4194304   fd  Linux raid autodetect
/dev/sdb2   *  1952911360  1953523711      306176   83  Linux
/dev/sdb3      1032390656  1952911359   460260352   fd  Linux raid autodetect
/dev/sdb4         8390656  1032390655   512000000   fd  Linux raid autodetect

Partition table entries are not in disk order

Disk /dev/sdc: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0001f31b

Device Boot      Start         End      Blocks   Id  System
/dev/sdc1            2048     8390655     4194304   fd  Linux raid autodetect
/dev/sdc2   *  1952911360  1953523711      306176   83  Linux
/dev/sdc3      1032390656  1952911359   460260352   fd  Linux raid autodetect
/dev/sdc4         8390656  1032390655   512000000   fd  Linux raid autodetect

Partition table entries are not in disk order

Disk /dev/sdd: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00030cd8

Device Boot      Start         End      Blocks   Id  System
/dev/sdd1            2048     8390655     4194304   fd  Linux raid autodetect
/dev/sdd2   *  1952911360  1953523711      306176   83  Linux
/dev/sdd3      1032390656  1952911359   460260352   fd  Linux raid autodetect
/dev/sdd4         8390656  1032390655   512000000   fd  Linux raid autodetect

Partition table entries are not in disk order

Disk /dev/sde: 4004 MB, 4004511744 bytes
255 heads, 63 sectors/track, 486 cylinders, total 7821312 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x018eb0cf

Device Boot      Start         End      Blocks   Id  System
/dev/sde1   *        2048     7821311     3909632    b  W95 FAT32

Disk /dev/md0: 12.9 GB, 12877037568 bytes
2 heads, 4 sectors/track, 3143808 cylinders, total 25150464 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 524288 bytes / 1572864 bytes
Disk identifier: 0x00000000


Disk /dev/md3: 313 MB, 313196544 bytes
2 heads, 4 sectors/track, 76464 cylinders, total 611712 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000


Disk /dev/md2: 1413.5 GB, 1413515575296 bytes
2 heads, 4 sectors/track, 345096576 cylinders, total 2760772608 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 524288 bytes / 1572864 bytes
Disk identifier: 0x00000000


Disk /dev/md1: 1572.5 GB, 1572459773952 bytes
2 heads, 4 sectors/track, 383901312 cylinders, total 3071210496 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 524288 bytes / 1572864 bytes
Disk identifier: 0x00000000


/boot detected. Please check the options.
=================== Final advice in case of recommended repair
Please do not forget to make your BIOS boot on sda (1000GB) disk!

=================== Default settings
Recommended-Repair
This setting would purge (in order to enable-raid) and reinstall the grub2 of md1 into the MBRs of all disks (except USB without OS), using the following options:        md3/boot,
Additional repair would be performed: unhide-bootmenu-10s

=================== Settings chosen by the user
Boot-Info
This setting will not act on the MBR.



No change has been performed on your computer.
pastebinit  packages needed
User refused to install pastebinit

---

### Post by StuartIanNaylor on 2013-02-09
Grub loads and mmmm yeap I cleared all but the newest kernel options whoops but it still tries.

In grub.cfg its this bit where the second uuid (not the mduuid) is trying to load / which is raid5

set root='(mduuid/e5fe242fe6fbb62b152451c13f7d58fb)'
search --no-floppy --fs-uuid --set=root 16a0b094-4635-4b14-bdd7-a5601c2e3694

when does the software raid kick in ?

md0 swap raid5
md1 / raid5
md2 /home raid5
md3 /boot raid1

---

### Post by darkod on 2013-02-09
It seems /boot was the sda2 partition on install, and you later changed to use md3 as /boot, right?

But grub might have remembered the original location so during major updates of the package it can get confused and look for it.

The good thing is that all md devices assemble and function correctly. You can try entering the installation with chroot, and try updating grub:
```
sudo apt-get install mdadm
sudo mdadm --assemble --scan
sudo mount /dev/md1 /mnt
sudo mount /dev/md3 /mnt/boot
sudo mount --bind /proc /mnt/proc
sudo mount --bind /dev /mnt/dev
sudo mount --bind /sys /mnt/sys
sudo chroot /mnt
```

Now you are inside the installation as root:
```
update-grub
grub-install /dev/sda /dev/sdb /dev/sdc /dev/sdd
exit
```

Reboot and keep fingers crossed. See if that can help.

---

### Post by StuartIanNaylor on 2013-02-10
Its strange but after an upgrade and the newest kernel the server was reporting missing operating system.

It was as if the MBR was missing as it wasn't even getting to grub.

The partitions are the same as in install and have never changed.

sda1 = swap =md0
sda2 = / =md1
sda3 = /home =md2
sda4 = /boot =md3

Ok here goes for your suggestion.

Seems to do the same as Boot-Repair and it has confused me as I thought it should work.

Its as if the software raid isn't being loaded.
From boot and using the ubuntu grub option for recover you can see where it fails.

For some reason when end with a boot failure and at the BusyBox prompt if you do a LS for /dev/disk/by-uuid/
the only drive listed is the /boot /md3 /sda4 raid1 partition.

Which I guess is because Raid1 is just a mirror and doesn't need software RAID drivers.

I just don't know how to force the kernel to load the RAID drivers so that / /md1 /sda2 raid5 is detected.

This is the bit where grub bangs out to BusyBox

set root='(mduuid/e5fe242fe6fbb62b152451c13f7d58fb)'
search --no-floppy --fs-uuid --set=root 16a0b094-4635-4b14-bdd7-a5601c2e3694

ALERT! /dev/disk/by-uuid/16a0b094-4635-4b14-bdd7-a5601c2e3694 does not exist.
Dropping to a shell!

cat /proc/mdstat 
md3: active raid1 sdc2[2] sdd2[3] sdb2[1] sda2[0]
305856 blocks super 1.2 [4/4] [UUUU]

Where are my other arrays !!! Help :)

---

### Post by darkod on 2013-02-10
I just noticed this in your bootinfo results for mdadm.conf:
```
=================== md1/etc/mdadm/mdadm.conf :
# mdadm.conf
#
# Please refer to mdadm.conf(5) for information about this file.
#

# by default (built-in), scan all partitions (/proc/partitions) and all
# containers for MD superblocks. alternatively, specify devices to scan, using
# wildcards if desired.
[COLOR="Red"]#DEVICE partitions containers[/COLOR]

# auto-create devices with Debian standard permissions
CREATE owner=root group=disk mode=0660 auto=yes

# automatically tag new arrays as belonging to the local system
HOMEHOST <system>

# instruct the monitoring daemon where to send mail alerts
MAILADDR dickychipps@sky.com

# definitions of existing MD arrays
ARRAY /dev/md/0 metadata=1.2 UUID=e7beb7c1:0d2d2af7:f5f29ca7:ace79a50 name=zen1:0
ARRAY /dev/md/2 metadata=1.2 UUID=684ece4d:38f96eb6:7d75c086:2ff179ea name=zen1:2
ARRAY /dev/md/1 metadata=1.2 UUID=e5fe242f:e6fbb62b:152451c1:3f7d58fb name=zen1:1

# This file was auto-generated on Thu, 06 Dec 2012 19:17:24 +0000
# by mkconf $Id$
[COLOR="red"]DEVICE /dev/sda2 /dev/sdb2 /dev/sdc2 /dev/sdd2[/COLOR]
ARRAY /dev/md3 level=raid1 devices=/dev/sda2,/dev/sdb2,/dev/sdc2,/dev/sdd2

```

Somehow, either by you earlier or by the upgrade, the DEVICE definition for all partitions and containers has been commented out, and at the bottom of the file there is a new DEVICE definition but it only includes the second partition of all four disks. It looks to me like that would allow it to assemble only md3, which it does, and not any other md device. From live mode open that mdadm.conf and try commenting the line specifying the sda2, sdb2, etc partitions, and uncomment the generic line DEVICE partitions containers. Save and close the file.

Reboot and see how it goes.

Missing operating system by the bios is reported if your bios requests that any partition on any disk has the boot flag. Linux doesn't use the boot flag so in single boot systems often it is never set to any partition. Some boards don't boot if it's missing, even though linux doesn't need it to boot. But you do have a boot flag on the second parttion of all disks. That should be fine.

See if that change in mdadm.conf helps.

---

### Post by StuartIanNaylor on 2013-02-10
Darko, i could kiss you. Haven't tried it yet but I am presuming you are correct.
I haven't a clue why this has happened but i have my fingers crossed.

Being stupid I thought mdadm would never get that far as md1 had not been mounted.

I will give it a go now. Its Sunday and I hope this is working as monday is soon. :)

Doh! No! :)

# This file was auto-generated on Thu, 06 Dec 2012 19:17:24 +0000
# by mkconf $Id$
DEVICE /dev/sda2 /dev/sdb2 /dev/sdc2 /dev/sdd2
ARRAY /dev/md3 level=raid1 devices=/dev/sda2,/dev/sdb2,/dev/sdc2,/dev/sdd2

Should be

# This file was auto-generated on Thu, 06 Dec 2012 19:17:24 +0000
# by mkconf $Id$
DEVICE /dev/sda4 /dev/sdb4 /dev/sdc4 /dev/sdd4
ARRAY /dev/md3 level=raid1 devices=/dev/sda4,/dev/sdb4,/dev/sdc4,/dev/sdd4

I did change it to that as well but no good, puzzled.

Also on initrafs: mdadm --assemble --scan
mdadm: CREATE user root not found
mdadm: CREATE group disk not found

---

### Post by StuartIanNaylor on 2013-02-10
Darko many thanks as you pointed me into the right direction.

I created a dir /mnt/root
mount and binded there

ran an update-initramfs -u

and that told me that /dev/md/3 with uuid xxxxx... wasn't included.

So I changed
# definitions of existing MD arrays
ARRAY /dev/md/0 metadata=1.2 UUID=e7beb7c1:0d2d2af7:f5f29ca7:ace79a50 name=zen1:0
ARRAY /dev/md/2 metadata=1.2 UUID=684ece4d:38f96eb6:7d75c086:2ff179ea name=zen1:2
ARRAY /dev/md/1 metadata=1.2 UUID=e5fe242f:e6fbb62b:152451c1:3f7d58fb name=zen1:1

ARRAY /dev/md/3 metadata=1.2 UUID=xxx name=zen1:3

ran update-initramfs

no error

ran update-grub

ran grub-install /dev/sda
... /sdb
... /sdc
... /sdd

Reboot and many thanks.

Oooof monday was getting close :)

Still haven't a clue what caused it ?!!!

---

### Post by darkod on 2013-02-10
Glad you got it working. Yeah, the md3 definition in mdadm.conf looked weird.

Please support my application for ubuntu membership by posting in the thread in my signature. :)

---

