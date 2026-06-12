---
title: "Secondary Drive Sync Script"
date: 2010-08-03
forum: Server Platforms
---

### Post by Nextraztus on 2010-08-03
Hello, first a little backstory;

I work for a small community college and have recently taken up the reigns of "webmaster". One of the great things about working at a community college is the ability to have a lot of freedom and flexibility in your strategy.  We have a pretty poor website (I inherited quite the mess), so I've spent the last 6 months beating content out of everyone and migrating over to a Drupal-powered one based on Ubuntu, dumping our existing Windows 2008 server.

In the last couple of weeks, I've been "blessed" with a new piece of hardware, which was purchased by our previous IT Director last year sometime. While it is a pretty decent HP server, it is lacking one crucial thing...a RAID controller. It does have two harddrives though and is otherwise unused. I was also given a single tape drive that it came with (it works nicely with no configuration, thanks Ubuntu!) so overall, this is letting me keep the old webserver in production and this one on the floor of my office until I launch in two weeks.

I decided to task myself with building a cron script that will copy the primary drive over to the second drive. I figured this couldn't be that hard and I've made excellent progress, but I've finally hit a snag and I just can't figure out what to do next. I only have a few hours invested in this, so I'm not out too much if it's just not viable. But then I'm going to have to figure out what to do for disaster recovery.

The script that I put together to sync the drives;
```
#!/bin/bash

#simple backup script
BTARG=/dev/sdb1
BTARGPT=/mnt/backup
BSRC=/
EXCLUDE=/tmp/excludes.list
SED_SCRIPT_EXT='s/f0cfb2fc-90a4-4bca-9f88-ef7888d970e4/34bacac8-e496-43c9-bd12-31b34ca1e20f/g'
SED_SCRIPT_SWAP='s/daddc7c7-37dc-4201-8e6c-0648551f08b4/8a7e2e8d-0723-421d-8eda-bb750a4a65d0/g'
LOCKFILE=/tmp/backupTapeCNCC

#make sure this script doesn't mess up our weekly tape backup
if [ -f $LOCKFILE ]
then
  exit
fi

#exclusion list
echo "/tmp/*" >$EXCLUDE
echo "/mnt/*" >>$EXCLUDE
echo "/root/ThisIsPrimaryDrive" >> $EXCLUDE
mount | grep "^none\|^proc" | cut -f 3 -d ' ' - >>$EXCLUDE

#mount backup harddrive
mkdir $BTARGPT
mount $BTARG $BTARGPT

#backup mostly everything
rsync -ax --stats --exclude-from=$EXCLUDE --delete / $BTARGPT

#fix our grub & fstabs
sed -i $SED_SCRIPT_EXT $BTARGPT/etc/fstab
sed -i $SED_SCRIPT_EXT $BTARGPT/boot/grub/grub.cfg
sed -i $SED_SCRIPT_SWAP $BTARGPT/etc/fstab
sed -i $SED_SCRIPT_SWAP $BTARGPT/boot/grub/grub.cfg

#probably should just figure out how to generate the exclude list differently
if [ ! -d /mnt/backup/dev ]
then
  mkdir /mnt/backup/dev
fi

if [ ! -d /mnt/backup/sys ]
then
  mkdir /mnt/backup/sys
fi

if [ ! -d /mnt/backup/proc ]
then
  mkdir /mnt/backup/proc
fi

#clean up
rm $EXCLUDE

umount $BTARGPT
rmdir $BTARGPT

```

Ok, all I'm doing is generating a list of mountpoints that I know I don't want to copy (stuff like /proc) and building a temporary exclusion list that rsync can use. I mount the secondary harddrive & rsync everything over. I think make sure that the /proc, /sys, and /dev mountpoints are built and ready to use (this was the first problem I ran into).

Now, the block of sed-scripts there are just to update the UUID's of the drives in /etc/fstab & grub.cfg.

I BELIEVE this is the only information that really changes in the event my primary drive fails. The idea of this script is that if the primary drive fails, I can just unplug it, reboot, and be back up and running until I can replace the failed drive. On this particular system, the grub paths (hd0,1) all work out. That is, when I unplug the primary drive (hd0,1) and only have the secondary drive plugged in, grub then sees it as (hd0,1).

I think I'm getting past the grub phase because the first problem I had was a kernel panic with mounting the /sys, /dev, & /proc filesystems. I managed to fix that, but now I've hit a wall;

The kernel never boots. I just get a flashing cursor until eternity (ok, so I've only let it sit for 5 minutes or so, but that's basically eternity). I have no idea what I'm missing at this point and don't know where to go from here.  Without any error messages or boot messages I'm at a complete loss for what to do next.

Ideas & Suggestions? Thanks in advance for any advice.

_Some more useful information perhaps;_
/dev/sda = primary drive
/dev/sdb = secondary drive

I have copied over the MBR with dd.

UUID's of the partitions according to sudo blkid.
```

/dev/sda1: UUID="f0cfb2fc-90a4-4bca-9f88-ef7888d970e4" TYPE="ext4" 
/dev/sda5: UUID="daddc7c7-37dc-4201-8e6c-0648551f08b4" TYPE="swap" 
/dev/sdb1: UUID="34bacac8-e496-43c9-bd12-31b34ca1e20f" TYPE="ext4" 
/dev/sdb5: UUID="8a7e2e8d-0723-421d-8eda-bb750a4a65d0" TYPE="swap" 

```

/etc/fstab on Primary Drive
```
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0

UUID=f0cfb2fc-90a4-4bca-9f88-ef7888d970e4 /               ext4    errors=remount-ro 0       1
UUID=daddc7c7-37dc-4201-8e6c-0648551f08b4 none            swap    sw                0       0

```

/etc/fstab on Secondary Drive (after script runs)
```
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0

UUID=34bacac8-e496-43c9-bd12-31b34ca1e20f /               ext4    errors=remount-ro 0       1
UUID=8a7e2e8d-0723-421d-8eda-bb750a4a65d0 none            swap    sw                0       0

```

/boot/grub/grub.cfg on Primary Drive
```
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
search --no-floppy --fs-uuid --set f0cfb2fc-90a4-4bca-9f88-ef7888d970e4
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
search --no-floppy --fs-uuid --set f0cfb2fc-90a4-4bca-9f88-ef7888d970e4
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=5
fi
insmod play
play 480 440 1
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.32-21-server' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set f0cfb2fc-90a4-4bca-9f88-ef7888d970e4
	linux	/boot/vmlinuz-2.6.32-21-server root=UUID=f0cfb2fc-90a4-4bca-9f88-ef7888d970e4 ro   quiet
	initrd	/boot/initrd.img-2.6.32-21-server
}
menuentry 'Ubuntu, with Linux 2.6.32-21-server (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set f0cfb2fc-90a4-4bca-9f88-ef7888d970e4
	echo	'Loading Linux 2.6.32-21-server ...'
	linux	/boot/vmlinuz-2.6.32-21-server root=UUID=f0cfb2fc-90a4-4bca-9f88-ef7888d970e4 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-21-server
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set f0cfb2fc-90a4-4bca-9f88-ef7888d970e4
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set f0cfb2fc-90a4-4bca-9f88-ef7888d970e4
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

```

grub.cfg on Secondary Drive
```

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
search --no-floppy --fs-uuid --set 34bacac8-e496-43c9-bd12-31b34ca1e20f
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
search --no-floppy --fs-uuid --set 34bacac8-e496-43c9-bd12-31b34ca1e20f
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=5
fi
insmod play
play 480 440 1
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.32-21-server' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 34bacac8-e496-43c9-bd12-31b34ca1e20f
	linux	/boot/vmlinuz-2.6.32-21-server root=UUID=34bacac8-e496-43c9-bd12-31b34ca1e20f ro   quiet
	initrd	/boot/initrd.img-2.6.32-21-server
}
menuentry 'Ubuntu, with Linux 2.6.32-21-server (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 34bacac8-e496-43c9-bd12-31b34ca1e20f
	echo	'Loading Linux 2.6.32-21-server ...'
	linux	/boot/vmlinuz-2.6.32-21-server root=UUID=34bacac8-e496-43c9-bd12-31b34ca1e20f ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-21-server
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 34bacac8-e496-43c9-bd12-31b34ca1e20f
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 34bacac8-e496-43c9-bd12-31b34ca1e20f
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

```

---

### Post by Fafler on 2010-08-04
Whats wrong with software RAID1?

---

### Post by Nextraztus on 2010-08-04
Software RAID is certainly something I can look into down the road, but I wasn't given this hardware until about last week. I didn't have enough time to research setting it up and testing it. In other words, I'm ignorant to how software RAID works and I didn't want to duff it.

The original migration plan was to build up the server on a virtual machine and clonezilla/gparted it over to the existing webserver's iron. Unfortunately I couldn't get those tools to properly cooperate with LVM, so I decided to just try a regular ext4/swap setup. GParted didn't want to cooperate with that either (for some strange reason). It may have been the test desktop IT let me use, but I couldn't risk the same problem happening for the actual migration to the production server.

So, instead, IT gave me this server (since it was laying around unused) and I've just built it up as if it was going to be the production server. We're gonna swap cables in the server room when the time comes.

Is software RAID something I can do after-the-fact now that I've already built the drives up? Or is that something I would need to copy all my stuff over to an external drive, reinstall, and then copy/configure everything back?

---

### Post by LightningCrash on 2010-08-04
> **Nextraztus said:**
> 
Is software RAID something I can do after-the-fact now that I've already built the drives up? Or is that something I would need to copy all my stuff over to an external drive, reinstall, and then copy/configure everything back?

yes, you can do mdadm RAID after the fact.
i've had to do this before, it's been a while but it goes something like this:

partition the second drive like the first (sfdisk)
label its partitions linux raid
make broken mirrors
mkfs on the broken mirrors
rsync everything over from the single drive to the broken mirror
edit fstab on the broken mirror (don't forget the swap!)
edit mdadm.conf on the broken mirror
grub-install on the broken mirror


pull first drive, make sure grub comes up from the second drive (the broken mirror)
boot on the broken mirror
verify operation
put first drive back in
sfdisk first drive
add first drive to mirrors
grub-install on first drive
reboot, check to make sure grub comes up on the first drive

ta-da

i'm sure if you google you can find a more thorough explanation
but there's no reason to reinstall anything at all.

and you have backup tapes, right?

---

### Post by Nextraztus on 2010-08-04
Ok perfect, this looks like something I can probably do then and will be a lot cleaner then my current method.

I'll start doing some research, I can probably get this to work on some leftover test hardware.

As for "backup tapes"...yea not yet lol. My backup tape is that secondary harddrive at the moment. I need to throw something together for that script.

Thanks for the reply, I'll mark this solved.

---

