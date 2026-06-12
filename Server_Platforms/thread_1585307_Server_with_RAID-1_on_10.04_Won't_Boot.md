---
title: "Server with RAID-1 on 10.04 Won't Boot"
date: 2010-09-30
forum: Server Platforms
---

### Post by steve_c on 2010-09-30
I'm attempting to re-install a server with Ubuntu 10.04 32-bit Server. I want the boot drives to be in a RAID-1 array. I have three identical drives so I'm trying to configure it with 1 spare as per the instructions here:
[https://help.ubuntu.com/community/Installation/SoftwareRAID]("https://help.ubuntu.com/community/Installation/SoftwareRAID")

Once it completes the install and reboots, however, I get a blank screen with a flashing cursor. My impression is that GRUB isn't booting. I've tried installing a couple times with slightly different variations on the way I did things, and those wound up with a screen saying only something to the effect of "grub error: disk not found" and dropping me to a grub recovery prompt. Going step by step through the instructions at the URL though, I just get the blank screen and cursor.

Any suggestions/help please?

---

### Post by psusi on 2010-09-30
Why not use a raid-5 instead of a raid-1 with hot spare?

Boot the livecd, download this script, and post its output please:

[http://sourceforge.net/projects/bootinfoscript/](http://sourceforge.net/projects/bootinfoscript/)

---

### Post by steve_c on 2010-09-30
Re: RAID-1 vs RAID-5
I have a separate array that is RAID-5 for data. This is the OS array, so firstly I'm only concerned about keeping enough integrity that it can boot and get me to my data on the RAID-5 array. Also to my knowledge Linux won't allow you to boot from a software RAID-5 array. I think the idea is that if you lose a drive you won't be able to boot to heal the array. With a RAID-1 array though I'm pretty sure if you lose one drive it can still boot from the other as if it were just a single master drive.

Here is the output from the script:
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks for (md0)/boot/grub.
 => Grub 2 is installed in the MBR of /dev/sdb and looks for (md0)/boot/grub.
 => No boot loader is installed in the MBR of /dev/sdc
 => No boot loader is installed in the MBR of /dev/sdd

sda1: _________________________________________________________________________

    File system:       linux_raid_member
    Boot sector type:  -
    Boot sector info:  

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       linux_raid_member
    Boot sector type:  -
    Boot sector info:  

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdc1: _________________________________________________________________________

    File system:       linux_raid_member
    Boot sector type:  -
    Boot sector info:  

sdc2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sdc5: _________________________________________________________________________

    File system:       linux_raid_member
    Boot sector type:  -
    Boot sector info:  

sdd1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

md/0_0: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 120.0 GB, 120000000000 bytes
255 heads, 63 sectors/track, 14589 cylinders, total 234375000 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000be6e1

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048   228,435,967   228,433,920  fd Linux raid autodetect
/dev/sda2         228,438,014   234,440,703     6,002,690   5 Extended
/dev/sda5         228,438,016   234,440,703     6,002,688  fd Linux raid autodetect

/dev/sda2 ends after the last sector of /dev/sda
/dev/sda5 ends after the last sector of /dev/sda

Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 120.0 GB, 120000000000 bytes
255 heads, 63 sectors/track, 14589 cylinders, total 234375000 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000e38a1

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *          2,048   228,435,967   228,433,920  fd Linux raid autodetect
/dev/sdb2         228,438,014   234,440,703     6,002,690   5 Extended
/dev/sdb5         228,438,016   234,440,703     6,002,688  fd Linux raid autodetect

/dev/sdb2 ends after the last sector of /dev/sdb
/dev/sdb5 ends after the last sector of /dev/sdb

Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000b5a41

Partition  Boot         Start           End          Size  Id System

/dev/sdc1    *          2,048   228,435,967   228,433,920  fd Linux raid autodetect
/dev/sdc2         228,438,014   234,440,703     6,002,690   5 Extended
/dev/sdc5         228,438,016   234,440,703     6,002,688  fd Linux raid autodetect


Drive: sdd ___________________ _____________________________________________________

Disk /dev/sdd: 360.0 GB, 359997112320 bytes
255 heads, 63 sectors/track, 43767 cylinders, total 703119360 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00000000

Partition  Boot         Start           End          Size  Id System

/dev/sdd1                  63   703,116,854   703,116,792  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/cloop0                                             iso9660    KNOPPIX_FS                    
/dev/md/0_0      93c8eac4-158f-4967-932c-7b14c143c7fa   ext4                                     
/dev/sda1        df412274-b4f8-70a0-dd89-41b57d9593be   linux_raid_member                               
/dev/sda5        aab455c4-b730-43c8-9ac6-caf1437f1a2c   swap                                     
/dev/sdb1        df412274-b4f8-70a0-dd89-41b57d9593be   linux_raid_member                               
/dev/sdb5        aab455c4-b730-43c8-9ac6-caf1437f1a2c   swap                                     
/dev/sdc1        df412274-b4f8-70a0-dd89-41b57d9593be   linux_raid_member                               
/dev/sdc5        2c7e48c7-6569-cd24-a187-e680ed32b898   linux_raid_member                               
/dev/sdd1        a67a1b32-1457-4fe6-9cd7-424019953ab4   ext3                                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

rootfs           /                        rootfs     (rw,relatime)
/dev/sr0         /mnt-system              iso9660    (ro,relatime)
/dev/cloop       /KNOPPIX                 iso9660    (ro,relatime)


========================== md/0_0/boot/grub/grub.cfg: ==========================

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
set root='(md0)'
search --no-floppy --fs-uuid --set 93c8eac4-158f-4967-932c-7b14c143c7fa
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
search --no-floppy --fs-uuid --set 93c8eac4-158f-4967-932c-7b14c143c7fa
set locale_dir=($root)/boot/grub/locale
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
menuentry 'Ubuntu, with Linux 2.6.32-21-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod raid
	insmod mdraid
	insmod ext2
	set root='(md0)'
	search --no-floppy --fs-uuid --set 93c8eac4-158f-4967-932c-7b14c143c7fa
	linux	/boot/vmlinuz-2.6.32-21-generic-pae root=UUID=93c8eac4-158f-4967-932c-7b14c143c7fa ro   quiet
	initrd	/boot/initrd.img-2.6.32-21-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod raid
	insmod mdraid
	insmod ext2
	set root='(md0)'
	search --no-floppy --fs-uuid --set 93c8eac4-158f-4967-932c-7b14c143c7fa
	echo	'Loading Linux 2.6.32-21-generic-pae ...'
	linux	/boot/vmlinuz-2.6.32-21-generic-pae root=UUID=93c8eac4-158f-4967-932c-7b14c143c7fa ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-21-generic-pae
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod raid
	insmod mdraid
	insmod ext2
	set root='(md0)'
	search --no-floppy --fs-uuid --set 93c8eac4-158f-4967-932c-7b14c143c7fa
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod raid
	insmod mdraid
	insmod ext2
	set root='(md0)'
	search --no-floppy --fs-uuid --set 93c8eac4-158f-4967-932c-7b14c143c7fa
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
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

============================== md/0_0/etc/fstab: ==============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/md0 during installation
UUID=93c8eac4-158f-4967-932c-7b14c143c7fa /               ext4    errors=remount-ro 0       1
# swap was on /dev/md1 during installation
UUID=aab455c4-b730-43c8-9ac6-caf1437f1a2c none            swap    sw              0       0

================== md/0_0: Location of files loaded by Grub: ==================


  40.9GB: boot/grub/core.img
  32.6GB: boot/grub/grub.cfg
  40.9GB: boot/initrd.img-2.6.32-21-generic-pae
  40.9GB: boot/vmlinuz-2.6.32-21-generic-pae
  40.9GB: initrd.img
  40.9GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda2

00000000  16 00 00 8b bb 88 00 00  00 85 ff 0f 84 8f 00 00  |................|
00000010  00 8d 57 02 89 d8 e8 d5  ce ff ff 84 c0 75 41 a1  |..W..........uA.|
00000020  00 00 00 00 89 83 c0 00  00 00 8b 83 88 01 00 00  |................|
00000030  89 44 24 0c 8b 83 84 00  00 00 89 34 24 c7 44 24  |.D$........4$.D$|
00000040  04 4a 00 00 00 89 44 24  08 e8 fc ff ff ff 8b 5d  |.J....D$.......]|
00000050  f4 31 c0 8b 75 f8 8b 7d  fc 89 ec 5d c3 8d 76 00  |.1..u..}...]..v.|
00000060  8b 83 84 00 00 00 8b 8b  88 01 00 00 c6 04 01 20  |............... |
00000070  c6 44 01 01 20 8b 93 88  00 00 00 83 c0 02 89 83  |.D.. ...........|
00000080  84 00 00 00 85 d2 75 30  8d 04 01 ba 04 0e 00 00  |......u0........|
00000090  e8 fc ff ff ff 01 bb 84  00 00 00 eb 82 8d 76 00  |..............v.|
000000a0  8b 7d f0 89 d8 8d 57 02  e8 43 ce ff ff 84 c0 0f  |.}....W..C......|
000000b0  84 6a ff ff ff eb a9 90  8d 93 90 2a 00 00 8d 04  |.j.........*....|
000000c0  01 e8 fc ff ff ff eb cd  90 8d b4 26 00 00 00 00  |...........&....|
000000d0  55 89 e5 83 ec 24 89 5d  f4 89 75 f8 89 7d fc e8  |U....$.]..u..}..|
000000e0  fc ff ff ff 83 f8 01 89  d3 8d 70 58 19 c0 f7 d0  |..........pX....|
000000f0  21 c6 a1 00 00 00 00 89  4d e4 8b 55 e4 8d 7d e8  |!.......M..U..}.|
00000100  89 f9 89 45 e0 8d 45 f0  89 04 24 89 f0 e8 fc ff  |...E..E...$.....|
00000110  ff ff 85 c0 74 52 8b 7d  f0 85 ff 74 60 8b 45 e8  |....tR.}...t`.E.|
00000120  8b 55 ec 89 3b 89 7b 10  89 43 04 89 43 14 8b 45  |.U..;.{..C..C..E|
00000130  e4 89 53 08 89 53 18 8b  55 e4 89 c1 89 43 0c c1  |..S..S..U....C..|
00000140  e9 02 31 c0 f3 ab f6 c2  02 74 02 66 ab f6 c2 01  |..1......t.f....|
00000150  74 01 aa b8 01 00 00 00  8b 5d f4 8b 75 f8 8b 7d  |t........]..u..}|
00000160  fc 89 ec 5d c3 8d 76 00  85 f6 74 5c 8b 96 d0 00  |...]..v...t\....|
00000170  00 00 85 d2 74 07 8b 42  04 0b 02 75 0b 31 c0 eb  |....t..B...u.1..|
00000180  d7 8d b4 26 00 00 00 00  8b 55 e0 8b 12 85 d2 89  |...&.....U......|
00000190  55 e0 74 e9 8b 86 d4 00  00 00 85 c0 74 31 3d ff  |U.t.........t1=.|
000001a0  ff ff 00 77 2a b8 21 00  00 00 8b 55 e4 89 f9 89  |...w*.!....U....|
000001b0  04 24 89 f0 ff 55 e0 89  c7 89 45 f0 e9 58 00 fe  |.$...U....E..X..|
000001c0  ff ff fd fe ff ff 02 00  00 00 00 98 5b 00 00 00  |............[...|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

Unknown BootLoader  on sdb2

00000000  16 00 00 8b bb 88 00 00  00 85 ff 0f 84 8f 00 00  |................|
00000010  00 8d 57 02 89 d8 e8 d5  ce ff ff 84 c0 75 41 a1  |..W..........uA.|
00000020  00 00 00 00 89 83 c0 00  00 00 8b 83 88 01 00 00  |................|
00000030  89 44 24 0c 8b 83 84 00  00 00 89 34 24 c7 44 24  |.D$........4$.D$|
00000040  04 4a 00 00 00 89 44 24  08 e8 fc ff ff ff 8b 5d  |.J....D$.......]|
00000050  f4 31 c0 8b 75 f8 8b 7d  fc 89 ec 5d c3 8d 76 00  |.1..u..}...]..v.|
00000060  8b 83 84 00 00 00 8b 8b  88 01 00 00 c6 04 01 20  |............... |
00000070  c6 44 01 01 20 8b 93 88  00 00 00 83 c0 02 89 83  |.D.. ...........|
00000080  84 00 00 00 85 d2 75 30  8d 04 01 ba 04 0e 00 00  |......u0........|
00000090  e8 fc ff ff ff 01 bb 84  00 00 00 eb 82 8d 76 00  |..............v.|
000000a0  8b 7d f0 89 d8 8d 57 02  e8 43 ce ff ff 84 c0 0f  |.}....W..C......|
000000b0  84 6a ff ff ff eb a9 90  8d 93 90 2a 00 00 8d 04  |.j.........*....|
000000c0  01 e8 fc ff ff ff eb cd  90 8d b4 26 00 00 00 00  |...........&....|
000000d0  55 89 e5 83 ec 24 89 5d  f4 89 75 f8 89 7d fc e8  |U....$.]..u..}..|
000000e0  fc ff ff ff 83 f8 01 89  d3 8d 70 58 19 c0 f7 d0  |..........pX....|
000000f0  21 c6 a1 00 00 00 00 89  4d e4 8b 55 e4 8d 7d e8  |!.......M..U..}.|
00000100  89 f9 89 45 e0 8d 45 f0  89 04 24 89 f0 e8 fc ff  |...E..E...$.....|
00000110  ff ff 85 c0 74 52 8b 7d  f0 85 ff 74 60 8b 45 e8  |....tR.}...t`.E.|
00000120  8b 55 ec 89 3b 89 7b 10  89 43 04 89 43 14 8b 45  |.U..;.{..C..C..E|
00000130  e4 89 53 08 89 53 18 8b  55 e4 89 c1 89 43 0c c1  |..S..S..U....C..|
00000140  e9 02 31 c0 f3 ab f6 c2  02 74 02 66 ab f6 c2 01  |..1......t.f....|
00000150  74 01 aa b8 01 00 00 00  8b 5d f4 8b 75 f8 8b 7d  |t........]..u..}|
00000160  fc 89 ec 5d c3 8d 76 00  85 f6 74 5c 8b 96 d0 00  |...]..v...t\....|
00000170  00 00 85 d2 74 07 8b 42  04 0b 02 75 0b 31 c0 eb  |....t..B...u.1..|
00000180  d7 8d b4 26 00 00 00 00  8b 55 e0 8b 12 85 d2 89  |...&.....U......|
00000190  55 e0 74 e9 8b 86 d4 00  00 00 85 c0 74 31 3d ff  |U.t.........t1=.|
000001a0  ff ff 00 77 2a b8 21 00  00 00 8b 55 e4 89 f9 89  |...w*.!....U....|
000001b0  04 24 89 f0 ff 55 e0 89  c7 89 45 f0 e9 58 00 fe  |.$...U....E..X..|
000001c0  ff ff fd fe ff ff 02 00  00 00 00 98 5b 00 00 00  |............[...|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

Unknown BootLoader  on sdc2

00000000  6a b7 8f 80 91 1e c0 39  3f 17 aa e1 61 26 45 bf  |j......9?...a&E.|
00000010  7d 12 17 fd 57 d0 98 cd  43 d9 cc 35 1f ac 9c f9  |}...W...C..5....|
00000020  63 b1 e7 83 b0 a8 e5 66  67 65 75 40 32 8d 9e c9  |c......fgeu@2...|
00000030  03 b2 53 c4 ff b0 fc 9f  64 ad 67 3b 27 a0 e0 7c  |..S.....d.g;'..||
00000040  64 f3 cd 60 8a 58 7c 31  1b a4 57 9b 53 2d ae 45  |d..`.X|1..W.S-.E|
00000050  bd da fa 18 e3 31 56 97  74 a2 04 bc 84 c5 dd 56  |.....1V.t......V|
00000060  61 b0 0e 34 10 3b 39 98  28 34 9c 1d 5f 37 38 69  |a..4.;9.(4.._78i|
00000070  8f c7 11 98 96 79 d6 c8  1e 5c 87 cb 2c b4 0b 7c  |.....y...\..,..||
00000080  08 6a 37 2c cd 52 36 87  21 76 db ef 8d f5 7b cf  |.j7,.R6.!v....{.|
00000090  21 d0 a6 c8 a4 af 9c f5  28 85 33 f9 8a bf bd cf  |!.......(.3.....|
000000a0  49 6b d9 6f 75 58 b4 d9  81 6b 24 c7 5a d0 d5 27  |Ik.ouX...k$.Z..'|
000000b0  b4 fb fd a8 d1 fa c4 6d  d7 3e 78 5a 33 b1 a2 2d  |.......m.>xZ3..-|
000000c0  a4 fe d8 69 d6 fb 7e 78  2f 4b d3 c8 26 0b c2 c7  |...i..~x/K..&...|
000000d0  17 0d 6b 4d 63 78 bf af  02 22 65 1f 30 a2 ae 5a  |..kMcx..."e.0..Z|
000000e0  2f b3 c9 03 27 d9 65 98  47 52 42 e6 b2 df 82 0a  |/...'.e.GRB.....|
000000f0  da 12 cb 6b 64 ec 30 52  3a 1b 54 05 40 fa 5f fe  |...kd.0R:.T.@._.|
00000100  90 a9 7c 36 55 93 52 10  5f 9e 72 c8 1c c4 d5 24  |..|6U.R._.r....$|
00000110  11 76 cb cd e6 53 7b 34  0a 28 b6 68 80 2a 4c c2  |.v...S{4.(.h.*L.|
00000120  34 c4 a3 b9 0d 8a 96 97  ec 94 c4 f2 f0 eb 8f 64  |4..............d|
00000130  c4 c5 13 db 91 90 dd 69  20 37 fd e5 3f aa 39 96  |.......i 7..?.9.|
00000140  02 01 01 6a db d5 f4 ab  6a 48 2b 99 a7 9d da 11  |...j....jH+.....|
00000150  06 af 01 40 f0 e4 1f 4d  9d cb 62 cd ab 27 4e fb  |...@...M..b..'N.|
00000160  33 60 53 d8 ec 3b c0 12  e6 23 a3 ac b5 bb 03 7b  |3`S..;...#.....{|
00000170  95 ed 9c c2 24 65 a1 a6  42 52 09 9a 21 e8 b5 7a  |....$e..BR..!..z|
00000180  76 de 4f 2c 9e 5a d0 a9  f9 0a a0 e4 d9 58 1c 85  |v.O,.Z.......X..|
00000190  16 52 f0 e7 8f 8e e4 12  33 1a 9c d2 52 20 f1 f1  |.R......3...R ..|
000001a0  62 1c d7 f1 f2 b7 95 dd  c5 92 36 a2 31 a2 4d de  |b.........6.1.M.|
000001b0  9b 38 e3 7d 52 71 66 73  33 d1 d5 04 74 77 00 fe  |.8.}Rqfs3...tw..|
000001c0  ff ff fd fe ff ff 02 00  00 00 00 98 5b 00 00 00  |............[...|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=============================== StdErr Messages: ===============================

mdadm: No suitable drives found for /dev/md/1_0
mdadm: /dev/md/0_0 has been started with 2 drives and 1 spare.
mdadm: No suitable drives found for /dev/md/1_0
mdadm: stopped /dev/md/0_0
```

Thank you for the help.

---

### Post by psusi on 2010-10-01
I'm not sure why your sdd drive has only a single Linux partition on it, instead of the two raid partitions like all of the other drives.  It also appears that you only have the boot loader on the first two disks, so the most likely problem is that your machine is trying to boot from those disks instead of the ones with the loader.  Check your bios boot order and try booting from different drives.

I'm also pretty sure that these days you can boot from a raid-5 array, so you might be better off just reinstalling and configuring a single raid partition on all 4 disks, and combining them into a single raid-5 array.  The whole point of raid-5 is that it keeps running even when a drive has failed.

---

### Post by steve_c on 2010-10-01
The SDD disk is actually a RAID-5 array--the storage array--managed by a hardware RAID controller. That's why it shows up as one disk. The first two disks are supposed to be the ones with the OS install mirrored, and sdc is supposed to be the hot-spare.

I found the following tutorial I'm going to attempt next by installing on one drive then creating the RAID post-install:
[http://www.howtoforge.com/how-to-set-up-software-raid1-on-a-running-system-incl-grub2-configuration-ubuntu-10.04]("http://www.howtoforge.com/how-to-set-up-software-raid1-on-a-running-system-incl-grub2-configuration-ubuntu-10.04")

The advantage of RAID-1 for me is that then I have a hot spare ready to go so effectively the machine is safe from two drive failures. This machine is not performance-critical but it is mission-critical; the storage array houses our internal Subversion repository (hopefully to migrate to a Bazaar repository after the upgrade) and our internal wiki, as well as some other internal items.

---

### Post by psusi on 2010-10-01
> **steve_c said:**
> The SDD disk is actually a RAID-5 array--the storage array--managed by a hardware RAID controller. That's why it shows up as one disk. The first two disks are supposed to be the ones with the OS install mirrored, and sdc is supposed to be the hot-spare.

Ohh, well then why not just put all of the disks on the hardware raid card?  Then you just install as if you only have a single disk.

> **steve_c said:**
> 
The advantage of RAID-1 for me is that then I have a hot spare ready to go so effectively the machine is safe from two drive failures. This machine is not performance-critical but it is mission-critical; the storage array houses our internal Subversion repository (hopefully to migrate to a Bazaar repository after the upgrade) and our internal wiki, as well as some other internal items.

You should be able to configure the hardware raid to have a hot spare.  The way you are doing it, you aren't really safe from a double failure.  If two disks in the raid 5 fail, you've lost your data.  It doesn't help that you have the OS on a mirror with a hot spare.

Even with a hot spare, you can't handle two disks failing, if they fail at the same time ( or close to it ).  To really be able to handle two disks failing, you need raid-6.

---

### Post by steve_c on 2010-10-01
It's an older machine. The RAID card doesn't support that many disks, and I'm not even sure it supports RAID-6, otherwise I would be very tempted to do just that.

...That said I think I'm gonna double-check on both of those things right now to make sure I'm absolutely correct.

Thank you very much for your help!

---

### Post by psusi on 2010-10-01
Another option would be to forget about the hardware raid, and just go for software raid 5 or 6.

---

