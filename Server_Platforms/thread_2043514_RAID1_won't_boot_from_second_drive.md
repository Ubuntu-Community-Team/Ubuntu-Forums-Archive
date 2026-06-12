---
title: "RAID1 won't boot from second drive"
date: 2012-08-16
forum: Server Platforms
---

### Post by lordhedgehog on 2012-08-16
I've installed 12.04 LTS server with no issues, using two identical 1.5TB drives with GPT partitions (100mb EFI boot, 8Gb swap, 1.35TB /) set up as a RAID1 configuration, but it will only boot from the primary drive.

I can confirm the RAID1 is working -- removing the secondary drive, it works fine (except for a warning about degraded mode). Removing the primary drive, it will not boot. Using a bootdisk with the primary drive removed, I can see that data is being copied to both drives, but I cannot boot. Instead I get the standard "Insert boot media in selected boot device" error that you get with you have a non-bootable drive as primary.

I've verified the /boot partition is marked as bootable on both drives, and run grub-install on both drives. I ran the bootinfoscript and received the information below. The key difference between the drives appears to be the boot files:

```

sda1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  -
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /efi/ubuntu/grubx64.efi


sdb1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  -
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /grub/grub.cfg


```

Complete output follows:

```

                  Boot Info Script 0.61      [1 April 2012]


============================= Boot Info Summary: ===============================

 => No boot loader is installed in the MBR of /dev/sda.
 => No boot loader is installed in the MBR of /dev/sdb.

sda1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  -
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /efi/ubuntu/grubx64.efi

sda2: __________________________________________________________________________

    File system:       linux_raid_member
    Boot sector type:  -
    Boot sector info: 

sda3: __________________________________________________________________________

    File system:       linux_raid_member
    Boot sector type:  -
    Boot sector info: 

sdb1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  -
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /grub/grub.cfg

sdb2: __________________________________________________________________________

    File system:       linux_raid_member
    Boot sector type:  -
    Boot sector info: 

sdb3: __________________________________________________________________________

    File system:       linux_raid_member
    Boot sector type:  -
    Boot sector info: 

md/2: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Mounting failed:   mount: /dev/md2 already mounted or MDRaid/md/2 busy
mount: according to mtab, /dev/md2 is mounted on /

md/1: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info: 

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders, total 2930277168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1                   1 2,930,277,167 2,930,277,167  ee GPT


GUID Partition Table detected.

Partition    Start Sector    End Sector  # of Sectors System
/dev/sda1              34       195,346       195,313 EFI System partition
/dev/sda2         195,347    15,820,347    15,625,001 RAID partition (Linux)
/dev/sda3      15,820,348 2,930,277,118 2,914,456,771 RAID partition (Linux)

Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders, total 2930277168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1                   1 2,930,277,167 2,930,277,167  ee GPT


GUID Partition Table detected.

Partition    Start Sector    End Sector  # of Sectors System
/dev/sdb1              34       195,346       195,313 EFI System partition
/dev/sdb2         195,347    15,820,347    15,625,001 RAID partition (Linux)
/dev/sdb3      15,820,348 2,930,277,118 2,914,456,771 RAID partition (Linux)

"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/md1         5acddfbd-8666-4f0a-a017-1522700faba7   swap       
/dev/md/1        5acddfbd-8666-4f0a-a017-1522700faba7   swap       
/dev/md2         4d47b5a9-e833-429e-a8ad-96d5e81b076f   ext4       
/dev/md/2        4d47b5a9-e833-429e-a8ad-96d5e81b076f   ext4       
/dev/sda1        00E6-E6F7                              vfat       
/dev/sda2        86e576a9-5463-490b-53c6-4861d9a5148a   linux_raid_member hedgie:1
/dev/sda3        b24ebd83-9ec0-3539-624c-b624e5f400f2   linux_raid_member hedgie:2
/dev/sdb1        F322-2526                              vfat       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/md2         /                        ext4       (rw,errors=remount-ro)
/dev/sda1        /boot/efi                vfat       (rw)


============================= sdb1/grub/grub.cfg: ==============================

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
true
}

insmod raid
insmod mdraid1x
insmod part_gpt
insmod ext2
set root='(mduuid/b24ebd839ec03539624cb624e5f400f2)'
search --no-floppy --fs-uuid --set=root 4d47b5a9-e833-429e-a8ad-96d5e81b076f
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=2
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
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
### END /etc/grub.d/30_os-prober ###

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

=================== sdb1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             grub/grub.cfg                                  1

=============================== StdErr Messages: ===============================

mdadm: /dev/md/1 is already in use.
mdadm: /dev/md/2 is already in use.


```

---

### Post by bakegoodz on 2012-08-17
Sorry, you need hardware RAID to get completely automated fail-over with your boot drive. It is because Grub boot manager needs to load on the primary disk. Raid 1 is not even online until a bit into the boot process. You could make sure you have a Grub rescue disk ready like [http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

I think you could make your test work. I would need someone to confirm testing this, but you could clone the boot sector to the other drive and then make sure Grub config is set to find the disk by device name(eg /dev/sda1) instead of by UUID. It still won't automatically fail over if the BIOS and Kernel can still detect the bad drive though.

Example code to clone boot sector: Warning only use this if you have drives the same size with identical partition layout and are sure about your drives device names.
```
sudo dd if=/dev/sda of=/dev/sdb bs=512 count=1
```

Personally I would only use hardware raid when you need good uptime. For data preservation rely on backups. Software RAID does add some extra piece of mind. I use software RAID 1 to duplicate important important mount points, like in my Desktop computer I use a single SSD for root, but 2 hard drive in RAID 1 for /home

---

### Post by lordhedgehog on 2012-08-17
I don't need 100% automated fail-over. I'd be happy with "remove the bad drive and it boots up". The utility of a RAID is greatly reduced for me if I have to re-install Ubuntu to bring the system back up after the primary drive fails.

---

### Post by pcouderc on 2012-08-22
I have the same kind of problem, and a bit lost, and yes, we do not want to boot in RAID mode, we want that if the "1rst disk" fails or is removed, the server boots on the second disk (or anywhere but it boots...).
This seems suppose that some GPT is present on the second disk even if not used in normal use.

---

