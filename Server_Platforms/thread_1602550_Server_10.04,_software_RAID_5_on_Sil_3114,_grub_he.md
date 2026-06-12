---
title: "Server 10.04, software RAID 5 on Sil 3114, grub headaches"
date: 2010-10-21
forum: Server Platforms
---

### Post by ERIC H on 2010-10-21
AMD Athlon XP 1800 on MSI KM2M Combo-L
1GB PC3200 DDR

I am using a Vantec UGT-ST310R (Sil 3114) SATA RAID pci card to (attempt to) run an Ubuntu Server 10.04.01 32-bit install with the system installed on the primary master IDE device (WD 80GB) and /home mounted on software RAID 5 over 4 160GB SATA II drives. 

Long story somewhat short, I got the system to install finally yesterday by putting the system/swap on the IDE drive and then making a software RAID 5 array on 4 SATA drives. IDE drive shows up in installer/rescue mode as /dev/sde and installed grub to /dev/sde and voila, bootable system with RAID. I didn't trust my success so rebooted a few times over the next couple hours and sometimes I would boot straight to a login prompt, sometimes I would notice flashing udev errors in relation to the individual SATA drives (dev/sda , b, c, etc) not being found but I would still get a login prompt. I did notice a resync on /dev/md0 almost immediately after installing, which took about 2 hours for my ~440GB partition. After that finished I thought I was in the clear and left the system up all night as I installed services and configured. Tested with hdparm at the end of the night and everything seemed pretty good and around what I should be getting with the card. Shutdown for the night.

When I booted it up today for the first time....Read error and flashing cursor. So back to rescue mode, re-install grub and reboot to get '(hd0,2) out of disk errors' and the grub rescue console. Check all relevant grub params. and boot manually without issue, like this:

```

set prefix=(hd0,2)/boot/grub
set root=(hd0,2)
    set shows matching prefix and root
    ls /boot - shows kernels, initrd, grub, etc
insmod /boot/grub/linux.mod
linux /vmlinuz root=/dev/sde2 ro 
initrd /initrd.img
boot



```

Once I login, I check grub.cfg to find root as being (hd4,2), hence the out of disk errors (I guess?). Make a copy and set to hd0,2 again and reboot successfully to login prompt. I then do an fdisk -l and notice that the IDE drive sometimes is showing up as /dev/sde, sometimes as /dev/sda, which is where it's at now. So when I reboot, I get hd0,2 out of disk again BUT I still can boot to a login prompt.

What can I do to ensure stability and keep from having to reinstall grub every time I restart the system? I would love to keep it running always but there are large blocks of time it will go unused, and that gets expensive for home use.

Anyway, any help would be appreciated.

---

### Post by ERIC H on 2010-10-21
So, I shutdown for a couple hours only to start up and have to go through the same process again...boot to rescue and reinstall grub. Didn't have to boot manually or edit grub.cfg.


In previous installs, the IDE device was always showing up as /dev/sde and then while in linux was reporting as /dev/sda after multiple reboots. This time in rescue, IDE shows up as /dev/sda.

Reinstalled grub and got out of disk errors for hd0,2 (dev/sda2) but still booted to login and now IDE showing up as /dev/sde again. What is going on?

```
Disk /dev/sda: 160.0 GB, 160000000000 bytes
255 heads, 63 sectors/track, 19452 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000ba040

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       19453   156248064   fd  Linux raid autodetect

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000602

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       19458   156289024   fd  Linux raid autodetect

Disk /dev/sdc: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0004bf80

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       19458   156289024   fd  Linux raid autodetect

Disk /dev/sde: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000e3410

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1            9487        9730     1952768   82  Linux swap / Solaris
/dev/sde2   *           1        9487    76196864   83  Linux

Partition table entries are not in disk order

Disk /dev/sdd: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000a17a4

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1       19458   156289024   fd  Linux raid autodetect

Disk /dev/md0: 480.0 GB, 479993856000 bytes
2 heads, 4 sectors/track, 117186000 cylinders
Units = cylinders of 8 * 512 = 4096 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 65536 bytes / 196608 bytes
Disk identifier: 0x00000000

Disk /dev/md0 doesn't contain a valid partition table

```

---

### Post by psusi on 2010-10-21
What are prefix and root before you set them?  And what is the exact error message when you hit the rescue prompt?

---

### Post by ian dobson on 2010-10-22
Hi,

I have a similar setup. My system boots from a RAID1 array,where the drives are running off the onboard SATA controller, and the backup array is running on a Sil 3214 PCI-express card.

After installing and setting up the Sil3214 the system would boot normally about 50% of the time. When it didn't boot is dropped to busybox with a message the root was missing.

To solve this I blacklisted the Sil module and manually load it in rc.local. The problem seems to be a race between the intel and the sil driver. When the intel driver started first then alls OK, if the Sil started first then the drive order is totally screwed up.

Regards
Ian Dobson

---

### Post by ERIC H on 2010-10-22
> **psusi said:**
> What are prefix and root before you set them?  And what is the exact error message when you hit the rescue prompt?

prefix=hd0,2/boot/grub
root=hd0,2

The thing is, sometimes hd0 is /dev/sda2 and sometimes it's /dev/sde2.

hd0,2 out of disk

I still get that even though I get to login prompt when rebooting, though when I poweroff and restart I get Read Error and have to reinstall grub.

---

### Post by ERIC H on 2010-10-22
Actually, this time I'm not able to boot the system by reinstalling grub. Just stuck at Read Error with flashing cursor...

---

### Post by psusi on 2010-10-22
The letter assigned to the drive by the kernel depends on the order they are detected in, which can change.  It does not matter.  Now it sounds like your drive might be going bad.  Open the disk utility on the live cd and take a look at the SMART values and have the disk run the long self test.  If that looks ok, then run the script here:

[http://sourceforge.net/projects/bootinfoscript/](http://sourceforge.net/projects/bootinfoscript/)

And post the output.

---

### Post by ERIC H on 2010-10-22
Ok, was able to boot again. I'm using a 9.10 live disc and in the live env the IDE hdd is showing up as /dev/sdd. Running long self-test now and will run that script when I get a chance.

One thing I just realized, in grub, hd0 is (for example) /dev/sde, so hd0,2 would be /dev/sde3 right? System was installed to /dev/sde2. I also don't have a device.map file in grub. Is that a pre grub2 file or should I create one?

---

### Post by ERIC H on 2010-10-22
Extended self-test passed.

Noticing grub was installed on /dev/sda and sdb. Must have been from a failed attempt to use RAID arrays set up in the add-on cards BIOS. So depending on which is detected first, would explain the failures I presume? One thing that has happened after last time I had to reinstall grub is that md0 is resyncing for like the third time. Could this be related to having grub installed on the MBR of 1 of it's devices?


```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks for (md0)/boot/grub.
 => Grub 2 is installed in the MBR of /dev/sdb and looks for (md0)/boot/grub.
 => No boot loader is installed in the MBR of /dev/sdc
 => No boot loader is installed in the MBR of /dev/sdd
 => Grub 2 is installed in the MBR of /dev/sde and looks on the same drive in 
    partition #2 for /boot/grub.
 => Syslinux is installed in the MBR of /dev/sdf

sda1: _________________________________________________________________________

    File system:       linux_raid_member
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       linux_raid_member
    Boot sector type:  Unknown
    Boot sector info:  

sdc1: _________________________________________________________________________

    File system:       linux_raid_member
    Boot sector type:  -
    Boot sector info:  

sdd1: _________________________________________________________________________

    File system:       linux_raid_member
    Boot sector type:  Unknown
    Boot sector info:  

sde1: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sde2: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdf1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

md0: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160000000000 bytes
255 heads, 63 sectors/track, 19452 cylinders, total 312500000 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1               2,048   312,498,175   312,496,128  fd Linux raid autodetect


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1               2,048   312,580,095   312,578,048  fd Linux raid autodetect


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1               2,048   312,580,095   312,578,048  fd Linux raid autodetect


Drive: sdd ___________________ _____________________________________________________

Disk /dev/sdd: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdd1               2,048   312,580,095   312,578,048  fd Linux raid autodetect


Drive: sde ___________________ _____________________________________________________

Disk /dev/sde: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sde1         152,395,776   156,301,311     3,905,536  82 Linux swap / Solaris
/dev/sde2    *          2,048   152,395,775   152,393,728  83 Linux


Drive: sdf ___________________ _____________________________________________________

Disk /dev/sdf: 1019 MB, 1019215360 bytes
255 heads, 63 sectors/track, 123 cylinders, total 1990655 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdf1    *             63     1,990,654     1,990,592   b W95 FAT32


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/md0         8e69528c-2a0a-4efb-8dfd-6eed4e68e931   ext4                                     
/dev/sda1        7081a896-242c-38d5-41f0-fe6b26ca677c   linux_raid_member                               
/dev/sda                                                silicon_medley_raid_member                               
/dev/sdb1        7081a896-242c-38d5-41f0-fe6b26ca677c   linux_raid_member                               
/dev/sdb                                                silicon_medley_raid_member                               
/dev/sdc1        7081a896-242c-38d5-41f0-fe6b26ca677c   linux_raid_member                               
/dev/sdc                                                silicon_medley_raid_member                               
/dev/sdd1        7081a896-242c-38d5-41f0-fe6b26ca677c   linux_raid_member                               
/dev/sdd                                                silicon_medley_raid_member                               
/dev/sde1        9ba62c76-c3b1-4282-a1e5-394c13c3099a   swap                                     
/dev/sde2        7963da18-daac-4253-82f6-3a6b572b39ed   ext4                                     
/dev/sde: PTTYPE="dos" 
/dev/sdf1        7425-713F                              vfat       PENDRIVE                      
/dev/sdf: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sde2        /                        ext4       (rw,errors=remount-ro)
/dev/md0         /home                    ext4       (rw)


=========================== sde2/boot/grub/grub.cfg: ===========================

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
insmod ext2
set root='(hd0,1)'
search --no-floppy --fs-uuid --set 7963da18-daac-4253-82f6-3a6b572b39ed
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
insmod ext2
set root='(hd0,1)'
search --no-floppy --fs-uuid --set 7963da18-daac-4253-82f6-3a6b572b39ed
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
menuentry 'Ubuntu, with Linux 2.6.32-25-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 7963da18-daac-4253-82f6-3a6b572b39ed
	linux	/boot/vmlinuz-2.6.32-25-generic-pae root=UUID=7963da18-daac-4253-82f6-3a6b572b39ed ro   quiet
	initrd	/boot/initrd.img-2.6.32-25-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.32-25-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 7963da18-daac-4253-82f6-3a6b572b39ed
	echo	'Loading Linux 2.6.32-25-generic-pae ...'
	linux	/boot/vmlinuz-2.6.32-25-generic-pae root=UUID=7963da18-daac-4253-82f6-3a6b572b39ed ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-25-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 7963da18-daac-4253-82f6-3a6b572b39ed
	linux	/boot/vmlinuz-2.6.32-24-generic-pae root=UUID=7963da18-daac-4253-82f6-3a6b572b39ed ro   quiet
	initrd	/boot/initrd.img-2.6.32-24-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 7963da18-daac-4253-82f6-3a6b572b39ed
	echo	'Loading Linux 2.6.32-24-generic-pae ...'
	linux	/boot/vmlinuz-2.6.32-24-generic-pae root=UUID=7963da18-daac-4253-82f6-3a6b572b39ed ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-24-generic-pae
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 7963da18-daac-4253-82f6-3a6b572b39ed
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 7963da18-daac-4253-82f6-3a6b572b39ed
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

=============================== sde2/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sde2 during installation
UUID=7963da18-daac-4253-82f6-3a6b572b39ed /               ext4    errors=remount-ro 0       1
# /home was on /dev/md0 during installation
UUID=8e69528c-2a0a-4efb-8dfd-6eed4e68e931 /home           ext4    defaults        0       2
# swap was on /dev/sde1 during installation
UUID=9ba62c76-c3b1-4282-a1e5-394c13c3099a none            swap    sw              0       0

=================== sde2: Location of files loaded by Grub: ===================


  66.7GB: boot/grub/core.img
  66.7GB: boot/grub/grub.cfg
  66.8GB: boot/initrd.img-2.6.32-24-generic-pae
  66.8GB: boot/initrd.img-2.6.32-25-generic-pae
  66.7GB: boot/vmlinuz-2.6.32-24-generic-pae
  66.7GB: boot/vmlinuz-2.6.32-25-generic-pae
  66.8GB: initrd.img
  66.8GB: initrd.img.old
  66.7GB: vmlinuz
  66.7GB: vmlinuz.old
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sdb1

00000000  00 00 c0 03 10 00 c0 03  20 00 c0 03 e0 5f 00 20  |........ ...._. |
00000010  00 00 05 00 00 00 00 00  00 00 00 00 00 20 7d d7  |............. }.|
00000020  01 00 c0 03 11 00 c0 03  20 02 c0 03 00 80 00 20  |........ ...... |
00000030  00 00 07 00 00 00 00 00  00 00 00 00 00 20 00 4c  |............. .L|
00000040  02 00 c0 03 12 00 c0 03  20 04 c0 03 00 80 00 20  |........ ...... |
00000050  00 00 07 00 00 00 00 00  00 00 00 00 00 20 6e ed  |............. n.|
00000060  03 00 c0 03 13 00 c0 03  20 06 c0 03 00 80 00 20  |........ ...... |
00000070  00 00 07 00 00 00 00 00  00 00 00 00 00 20 b5 4d  |............. .M|
00000080  04 00 c0 03 14 00 c0 03  20 08 c0 03 00 80 00 20  |........ ...... |
00000090  00 00 07 00 00 00 00 00  00 00 00 00 00 20 b1 ef  |............. ..|
000000a0  05 00 c0 03 15 00 c0 03  20 0a c0 03 00 80 00 20  |........ ...... |
000000b0  00 00 07 00 00 00 00 00  00 00 00 00 00 20 6a 4f  |............. jO|
000000c0  06 00 c0 03 16 00 c0 03  20 0c c0 03 00 80 00 20  |........ ...... |
000000d0  00 00 07 00 00 00 00 00  00 00 00 00 00 20 04 ee  |............. ..|
000000e0  07 00 c0 03 17 00 c0 03  20 0e c0 03 00 80 00 20  |........ ...... |
000000f0  00 00 07 00 00 00 00 00  00 00 00 00 00 20 df 4e  |............. .N|
00000100  08 00 c0 03 18 00 c0 03  20 10 c0 03 00 80 00 20  |........ ...... |
00000110  00 00 07 00 00 00 00 00  00 00 00 00 00 20 0f ea  |............. ..|
00000120  09 00 c0 03 19 00 c0 03  20 12 c0 03 00 80 00 20  |........ ...... |
00000130  00 00 07 00 00 00 00 00  00 00 00 00 00 20 d4 4a  |............. .J|
00000140  0a 00 c0 03 1a 00 c0 03  20 14 c0 03 00 80 00 20  |........ ...... |
00000150  00 00 07 00 00 00 00 00  00 00 00 00 00 20 ba eb  |............. ..|
00000160  0b 00 c0 03 1b 00 c0 03  20 16 c0 03 00 80 00 20  |........ ...... |
00000170  00 00 07 00 00 00 00 00  00 00 00 00 00 20 61 4b  |............. aK|
00000180  0c 00 c0 03 1c 00 c0 03  20 18 c0 03 00 80 00 20  |........ ...... |
00000190  00 00 07 00 00 00 00 00  00 00 00 00 00 20 65 e9  |............. e.|
000001a0  0d 00 c0 03 1d 00 c0 03  20 1a c0 03 00 80 00 20  |........ ...... |
000001b0  00 00 07 00 00 00 00 00  00 00 00 00 00 20 be 49  |............. .I|
000001c0  0e 00 c0 03 1e 00 c0 03  20 1c c0 03 00 80 00 20  |........ ...... |
000001d0  00 00 07 00 00 00 00 00  00 00 00 00 00 20 d0 e8  |............. ..|
000001e0  0f 00 c0 03 1f 00 c0 03  20 1e c0 03 00 80 00 20  |........ ...... |
000001f0  00 00 07 00 00 00 00 00  00 00 00 00 00 20 0b 48  |............. .H|
00000200

Unknown BootLoader  on sdd1

00000000  20 80 c0 03 30 80 c1 03  00 80 c2 03 c0 df 03 20  | ...0.......... |
00000010  20 80 01 00 20 80 0c 00  20 80 0d 00 20 a0 65 d7  | ... ... ... .e.|
00000020  21 80 e8 03 31 80 fe 03  00 82 b9 03 20 00 ab 20  |!...1....... .. |
00000030  20 80 3f 01 20 80 6c 01  20 80 45 04 20 a0 b0 48  | .?. .l. .E. ..H|
00000040  22 80 da 05 12 00 c0 03  20 04 c0 03 00 80 00 20  |"....... ...... |
00000050  00 00 07 00 00 00 00 00  00 00 00 00 00 20 6e ed  |............. n.|
00000060  03 00 c0 03 13 00 c0 03  20 06 c0 03 00 80 00 20  |........ ...... |
00000070  00 00 07 00 00 00 00 00  00 00 00 00 00 20 b5 4d  |............. .M|
00000080  04 00 c0 03 14 00 c0 03  20 08 c0 03 00 80 00 20  |........ ...... |
00000090  00 00 07 00 00 00 00 00  00 00 00 00 00 20 b1 ef  |............. ..|
000000a0  05 00 c0 03 15 00 c0 03  20 0a c0 03 00 80 00 20  |........ ...... |
000000b0  00 00 07 00 00 00 00 00  00 00 00 00 00 20 6a 4f  |............. jO|
000000c0  06 00 c0 03 16 00 c0 03  20 0c c0 03 00 80 00 20  |........ ...... |
000000d0  00 00 07 00 00 00 00 00  00 00 00 00 00 20 04 ee  |............. ..|
000000e0  07 00 c0 03 17 00 c0 03  20 0e c0 03 00 80 00 20  |........ ...... |
000000f0  00 00 07 00 00 00 00 00  00 00 00 00 00 20 df 4e  |............. .N|
00000100  08 00 c0 03 18 00 c0 03  20 10 c0 03 00 80 00 20  |........ ...... |
00000110  00 00 07 00 00 00 00 00  00 00 00 00 00 20 0f ea  |............. ..|
00000120  09 00 c0 03 19 00 c0 03  20 12 c0 03 00 80 00 20  |........ ...... |
00000130  00 00 07 00 00 00 00 00  00 00 00 00 00 20 d4 4a  |............. .J|
00000140  0a 00 c0 03 1a 00 c0 03  20 14 c0 03 00 80 00 20  |........ ...... |
00000150  00 00 07 00 00 00 00 00  00 00 00 00 00 20 ba eb  |............. ..|
00000160  0b 00 c0 03 1b 00 c0 03  20 16 c0 03 00 80 00 20  |........ ...... |
00000170  00 00 07 00 00 00 00 00  00 00 00 00 00 20 61 4b  |............. aK|
00000180  0c 00 c0 03 1c 00 c0 03  20 18 c0 03 00 80 00 20  |........ ...... |
00000190  00 00 07 00 00 00 00 00  00 00 00 00 00 20 65 e9  |............. e.|
000001a0  0d 00 c0 03 1d 00 c0 03  20 1a c0 03 00 80 00 20  |........ ...... |
000001b0  00 00 07 00 00 00 00 00  00 00 00 00 00 20 be 49  |............. .I|
000001c0  0e 00 c0 03 1e 00 c0 03  20 1c c0 03 00 80 00 20  |........ ...... |
000001d0  00 00 07 00 00 00 00 00  00 00 00 00 00 20 d0 e8  |............. ..|
000001e0  0f 00 c0 03 1f 00 c0 03  20 1e c0 03 00 80 00 20  |........ ...... |
000001f0  00 00 07 00 00 00 00 00  00 00 00 00 00 20 0b 48  |............. .H|
00000200



```

---

### Post by ERIC H on 2010-10-23
Final bump...

I ended up wiping all drives and trying over to see if grub on the non-boot drives MBR was causing the issue and ended up with the same results. I've taken the IDE drive out of the equation and made 2 RAID 1 volumes via the card BIOS and am successfully booting every time, even after shutdown, without issue. Seems RAID 5, software or fakeRAID, just doesn't work with this card.

---

### Post by psusi on 2010-10-23
You have leftover fakeraid signatures on the drives.  If you are't using the fake raid then you need to delete the array in the bios ( not just disable it ) or use dmraid -E to remove them.

---

### Post by roddersg on 2010-10-24
I am running an Intel D510 board with a SIL3114 board and 6 1T Drives (Western Digital).  I tried the same process of installing software raid 5 on all 6 drives as stated in the Ubuntu Documentation, with 512MB as Swap and the rest as Software Raid.
The installation worked ok, everything initiallised properly with Grub etc, however, when it came to the boot process, the system refused to boot.  It kept getting stuck at the grub rescue> prompt....

Well, teaches me a lesson to google for SIL3114 and not to rely on VMWare or virtualisation to show that it works.

I guess its the SIL3114 so its back to freenas again, unless someone can come up with an idea of using a thumbdrive to boot ubuntu off it (will some kind soul point me that way?)

Thanks for this post though, really opened up my eyes

---

### Post by psusi on 2010-10-24
> **roddersg said:**
> I am running an Intel D510 board with a SIL3114 board and 6 1T Drives (Western Digital).  I tried the same process of installing software raid 5 on all 6 drives as stated in the Ubuntu Documentation, with 512MB as Swap and the rest as Software Raid.
The installation worked ok, everything initiallised properly with Grub etc, however, when it came to the boot process, the system refused to boot.  It kept getting stuck at the grub rescue> prompt....

Well, teaches me a lesson to google for SIL3114 and not to rely on VMWare or virtualisation to show that it works.

I guess its the SIL3114 so its back to freenas again, unless someone can come up with an idea of using a thumbdrive to boot ubuntu off it (will some kind soul point me that way?)

Thanks for this post though, really opened up my eyes

Run the bootinfo script.

---

### Post by annoyingrob on 2010-10-25
I had a similar problem to what you were having on my old server. I had a 6 drive software raid5 for root filesystem. The problem was that most of the time, it wouldn't find the array at boot, and boot would stop. It turned out to be a sort of race condition between the software raid drivers loading, and the kernel looking for a boot device. The drivers were loaded, then it would take a few seconds for the array to be recognized and initialized. During that few seconds, the kernel was trying to mount the array. Sometimes, it would time-out before the array initialized, sometimes it wouldn't.

The solution was just to edit the initrd image, and add a 10 second wait after the raid drivers were loaded.

---

