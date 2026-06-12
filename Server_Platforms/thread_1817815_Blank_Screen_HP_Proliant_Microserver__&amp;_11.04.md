---
title: "Blank Screen: HP Proliant Microserver  &amp; 11.04"
date: 2011-08-03
forum: Server Platforms
---

### Post by lessblue on 2011-08-03
Ok, so I've installed Ubuntu Server 11.04 64-bit on an HP Proliant Microserver. The install seems fine but I'm having a start-up problem. When I boot the server, I get a blank screen after the Grub Menu. If I press ALT-F2 I get the login prompt.

I've tried editing the grub file (after having done some googling) and tried adding nomodeset to the following line in the grub file:

[INDENT][/INDENT]*GRUB_CMDLINE_LINUX_DEFAULT="quiet splash* ***nomodeset acpi_osi=Linux***"

I added ***nomodeset ***as well as ***acpi_osi=Linux*** to see if that would help. 

After adding ***nomodeset***, when I boot the server, I still get a blank screen after the Grub menu but this time a blinking cursor. Again, if I press ALT-F2 the login prompt shows up. 

So it boots (I'm able to putty/Webmin in even when the screen is blank) but don't know why I need to press ALT-F2 all the time to get the login prompt to appear. Plus I don't see the boot process right before the login as well.

If it helps, the HP Proliant has the following chipset and processor:

[INDENT][INDENT]• AMD RS785E – north bridge, core logic controller
• AMD SB820M– south bridge
• AMD Athlon II NEO Processor 1.3 GHz Dual Core
[/INDENT][/INDENT]
Any ideas? I've also tried adding ***xforcevesa ***instead of ***nomodeset ***and that option too leaves me with a blank screen.

---

### Post by lessblue on 2011-08-03
I'm wondering if this post is on to something:

[http://ubuntuforums.org/showpost.php?p=9926920&postcount=12](http://ubuntuforums.org/showpost.php?p=9926920&postcount=12)

The boot drive on my HP Proliant is actually the sata port for a USB/optical drive. 

I have
[INDENT]sda (2TB HD with split into two partitions)[/INDENT]
[INDENT]sdb (2TB HD with split into two partitions)[/INDENT]
[INDENT]sdc (2TB HD with split into two partitions)[/INDENT]
[INDENT]sdd (2TB HD with split into two partitions)[/INDENT]
and then
[INDENT]sde (160GB HD with three partitions on it, including boot and swap)[/INDENT]

Might Grub be looking for /dev/sda ?

Though the server does seem to boot, just doesn't show the boot process and hangs unless you press ALT-F2 to bring up the login prompt.

---

### Post by lessblue on 2011-08-03
I tried running the following: grub-install /dev/sde
The command executed, I followed with grub-update and then a reboot. 

Still the same blank screen upon boot, with ALT-F2 bringing up:

[INDENT]Ubuntu 11.04 ubuntu tty2

ubuntu login:_[/INDENT]


No external USB device is connected and the Grub version shows: 1.99~rc1-13ubuntu3

---

### Post by lessblue on 2011-08-03
I've tried this page as well:

[http://ubuntu4beginners.blogspot.com/2011/01/ubuntumaverick-blank-screen-problem.html](http://ubuntu4beginners.blogspot.com/2011/01/ubuntumaverick-blank-screen-problem.html)

Added ***radeon.modeset=0*** since the chipset is ATI and was left with a blinking cursor (yellow in color this time).

Pressing ALT-F2 again resulted in the login prompt appearing.

I guess it boots fine but this does bother me.

---

### Post by lessblue on 2011-08-03
Just updating what I've tried in case it helps anyone else that may end up in the same boat.

So I edited the grub file and set it back to default:

[INDENT][COLOR="Navy"]GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=2
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""[/COLOR][/INDENT]

As a result, no Ubuntu 11.04 loading splash screen and I was left with a blinking cursor at the tend. However, *this time *ALT-F2 did not bring up the login prompt. I also could not putty or Webmin in. So it never fully booted.

I then added modeset back:

[INDENT][COLOR="Navy"]GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=2
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash ***_nomodeset_***"
GRUB_CMDLINE_LINUX=""[/COLOR][/INDENT]

This time I saw the Ubuntu 11.04 splash screen. Afterwards just a blinking cursor again. This time though, ALT-F2 did bring up the login prompt and I was able to putty/webmin in. So it fully booted, but did not show the scrolling boot process info or the final login prompt.

Not sure what to make of this.

---

### Post by Wim Sturkenboom on 2011-08-04
> **lessblue said:**
> 
**Might Grub be looking for /dev/sda ?**

Though the server does seem to boot, just doesn't show the boot process and hangs unless you press ALT-F2 to bring up the login prompt.
I doubt it. Your system boots fine, so there is actually nothing wrong with grub. I would take the _quiet splash_ out and leave _nomodeset_ in. That would show the boot process on tty1.

Not sure why you don't end up with a login prompt on tty1. <alt><F2> gives you tty2. If that works properly, it's no train smash, just an annoyance ;) You propapbly still have tty3 (<alt><F3>).. tty6 (<alt><F6>) as well.

---

### Post by lessblue on 2011-08-04
Thank you Wim, I'm going to try taking out ***quiet splash ***and leave ***nomodeset ***and see what happens.

As I was digging around, I managed to run the Boot Info Script and wanted to see if anyone could look at the results. Particularly the sde1, sde2, and sde3. 

Just to note, I manually created three (Primary) partitions on sde (160GB hard drive) for the Ubuntu Server install. The 1st partition I created was 500MB set to /boot. The other two (also Primary partitions) were also manually created with one large partition for file system and ~5.3 GB for the swap partition.   
 
```
                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    in partition 3 for ??.
 => No boot loader is installed in the MBR of /dev/sdb.
 => No boot loader is installed in the MBR of /dev/sdc.
 => Windows is installed in the MBR of /dev/sdd.
 => Grub2 (v1.99) is installed in the MBR of /dev/sde and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for ?? on this drive.

sda1: __________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        

sda2: __________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        

sdb1: __________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        

sdb2: __________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        

sdc1: __________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        

sdc2: __________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        

sdd1: __________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        

sdd2: __________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        

sde1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub2 (v1.99)
    Boot sector info:   Grub2 (v1.99) is installed in the boot sector of sde1 
                       and looks at sector 9701736 of the same hard drive for 
                       core.img. core.img is at this location and looks for 
                       ?? on this drive.
    Mounting failed:   mount: wrong fs type, bad option, bad superblock on /dev/sde1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so


sde2: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sde3: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1                  63 1,953,503,999 1,953,503,937  83 Linux
/dev/sda2       1,953,504,000 3,907,024,064 1,953,520,065  83 Linux


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1                  63 1,953,503,999 1,953,503,937  83 Linux
/dev/sdb2       1,953,504,000 3,907,024,064 1,953,520,065  83 Linux


Drive: sdc _____________________________________________________________________

Disk /dev/sdc: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdc1                  63 1,953,503,999 1,953,503,937  83 Linux
/dev/sdc2       1,953,504,000 3,907,024,064 1,953,520,065  83 Linux


Drive: sdd _____________________________________________________________________

Disk /dev/sdd: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdd1                  63 1,953,503,999 1,953,503,937  83 Linux
/dev/sdd2       1,953,504,000 3,907,024,064 1,953,520,065  83 Linux


Drive: sde _____________________________________________________________________

Disk /dev/sde: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sde1               2,048       976,895       974,848  83 Linux
/dev/sde2         302,360,576   312,580,095    10,219,520  82 Linux swap / Solaris
/dev/sde3             976,896   302,360,575   301,383,680  83 Linux


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        e7c047b1-2133-498d-ae77-468065056cb6   ext3       Film A
/dev/sda2        aad56a18-93ff-4548-850b-f50095c97451   ext3       
/dev/sdb1        fe317646-74aa-4e29-88b2-5c9058b7836c   ext3       Film C
/dev/sdb2        184b7760-a539-4ad7-a55a-f5a317d08f47   ext3       
/dev/sdc1        dc6fdcc0-3ebb-4acc-80b8-47cee0cbc354   ext3       
/dev/sdc2        69f9e192-ab9f-4624-8637-3b7501dba84b   ext3       
/dev/sdd1        22d9564b-bf61-408c-b48b-77dbe6d21e1f   ext3       
/dev/sdd2        1fe18d67-b863-413b-a128-9d1cad278c5c   ext3       
/dev/sde1        359523f6-82fe-478c-8cd1-81c1a86e3c37   ext4       
/dev/sde2        a3c70d7f-1d71-4a0e-940a-bf4874f80455   swap       
/dev/sde3        49c2e7ff-5bfa-4dfd-8b81-8df04af19545   ext4       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda1        /mydata/hda1             ext3       (rw,usrquota)
/dev/sda2        /mydata/hda2             ext3       (rw,usrquota)
/dev/sdb1        /mydata/hdb1             ext3       (rw,usrquota)
/dev/sdb2        /mydata/hdb2             ext3       (rw,usrquota)
/dev/sdc1        /mydata/hdc1             ext3       (rw,usrquota)
/dev/sdc2        /mydata/hdc2             ext3       (rw,usrquota)
/dev/sdd1        /mydata/hdd1             ext3       (rw,usrquota)
/dev/sdd2        /mydata/hdd2             ext3       (rw,usrquota)
/dev/sde3        /                        ext4       (rw,errors=remount-ro)


=========================== sde3/boot/grub/grub.cfg: ===========================

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
set root='(/dev/sde,msdos3)'
search --no-floppy --fs-uuid --set=root 49c2e7ff-5bfa-4dfd-8b81-8df04af19545
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sde,msdos3)'
search --no-floppy --fs-uuid --set=root 49c2e7ff-5bfa-4dfd-8b81-8df04af19545
set locale_dir=($root)/boot/grub/locale
set lang=en_US
insmod gettext
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
menuentry 'Ubuntu, with Linux 2.6.38-10-server' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sde,msdos3)'
	search --no-floppy --fs-uuid --set=root 49c2e7ff-5bfa-4dfd-8b81-8df04af19545
	linux	/boot/vmlinuz-2.6.38-10-server root=UUID=49c2e7ff-5bfa-4dfd-8b81-8df04af19545 ro   quiet splash nomodeset vt.handoff=7
	initrd	/boot/initrd.img-2.6.38-10-server
}
menuentry 'Ubuntu, with Linux 2.6.38-10-server (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sde,msdos3)'
	search --no-floppy --fs-uuid --set=root 49c2e7ff-5bfa-4dfd-8b81-8df04af19545
	echo	'Loading Linux 2.6.38-10-server ...'
	linux	/boot/vmlinuz-2.6.38-10-server root=UUID=49c2e7ff-5bfa-4dfd-8b81-8df04af19545 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.38-10-server
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, with Linux 2.6.38-8-server' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sde,msdos3)'
	search --no-floppy --fs-uuid --set=root 49c2e7ff-5bfa-4dfd-8b81-8df04af19545
	linux	/boot/vmlinuz-2.6.38-8-server root=UUID=49c2e7ff-5bfa-4dfd-8b81-8df04af19545 ro   quiet splash nomodeset vt.handoff=7
	initrd	/boot/initrd.img-2.6.38-8-server
}
menuentry 'Ubuntu, with Linux 2.6.38-8-server (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sde,msdos3)'
	search --no-floppy --fs-uuid --set=root 49c2e7ff-5bfa-4dfd-8b81-8df04af19545
	echo	'Loading Linux 2.6.38-8-server ...'
	linux	/boot/vmlinuz-2.6.38-8-server root=UUID=49c2e7ff-5bfa-4dfd-8b81-8df04af19545 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.38-8-server
}
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sde,msdos3)'
	search --no-floppy --fs-uuid --set=root 49c2e7ff-5bfa-4dfd-8b81-8df04af19545
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sde,msdos3)'
	search --no-floppy --fs-uuid --set=root 49c2e7ff-5bfa-4dfd-8b81-8df04af19545
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

### BEGIN /etc/grub.d/41_custom ###
if [ -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###
--------------------------------------------------------------------------------

=============================== sde3/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sde3 during installation
UUID=49c2e7ff-5bfa-4dfd-8b81-8df04af19545 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sde2 during installation
UUID=a3c70d7f-1d71-4a0e-940a-bf4874f80455 none            swap    sw              0       0
/dev/scd0       /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
/dev/sda1  /mydata/hda1  ext3  usrquota  0  1
/dev/sda2  /mydata/hda2  ext3  usrquota  0  1
/dev/sdb1  /mydata/hdb1  ext3  usrquota  0  1
/dev/sdb2  /mydata/hdb2  ext3  usrquota  0  1
/dev/sdc1  /mydata/hdc1  ext3  usrquota  0  1
/dev/sdc2  /mydata/hdc2  ext3  usrquota  0  1
/dev/sdd1  /mydata/hdd1  ext3  usrquota  0  1
/dev/sdd2  /mydata/hdd2  ext3  usrquota  0  1
--------------------------------------------------------------------------------

=================== sde3: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

   4.626174927 = 4.967317504    boot/grub/core.img                             1
   6.602558136 = 7.089442816    boot/grub/grub.cfg                             1
 137.483985901 = 147.622305792  boot/initrd.img-2.6.38-10-server               2
 137.479614258 = 147.617611776  boot/initrd.img-2.6.38-8-server                2
   0.915401459 = 0.982904832    boot/vmlinuz-2.6.38-10-server                  1
 136.759151459 = 146.844020736  boot/vmlinuz-2.6.38-8-server                   1
 137.483985901 = 147.622305792  initrd.img                                     2
 137.479614258 = 147.617611776  initrd.img.old                                 2
   0.915401459 = 0.982904832    vmlinuz                                        1
 136.759151459 = 146.844020736  vmlinuz.old                                    1

=============================== StdErr Messages: ===============================

To be able to see for which directory Grub2 (v1.99) looks for, install "unlzma".
To be able to see for which directory Grub2 (v1.99) looks for, install "unlzma".
To be able to see for which directory Grub2 (v1.99) looks for, install "unlzma".


```

---

### Post by lessblue on 2011-08-04
Hmmm, fdisk shows info for all of my  drives but not in order?

sda
sdb
sde (boot/install drive)
sdd
sdc

The sde part of the fdisk results:

```
Disk /dev/sde: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000a2ba1

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1               1          61      487424   83  Linux
Partition 1 does not end on cylinder boundary.
/dev/sde2           18822       19458     5109760   82  Linux swap / Solaris
/dev/sde3              61       18822   150691840   83  Linux

Partition table entries are not in disk order
```

---

### Post by lessblue on 2011-08-04
Due to the nature and limitations of the sata ports within the HP Proliant Microserver, if I wanted to attempt a complete reinstall, is there a proper way to manually partition a disk other than sda? Meaning Grub seems to always look to /dev/sda to install to (I think, I'm a linux newbie).

In my case, I want to install to my 160 GB drive which is /dev/sde.

Based on the boot info script and fdisk results, the /dev/sde install seems to be a little off. Which may or may not be related to my blank screen issue. 

I would rather do a reinstall properly if someone would kindly point me in the right direction in terms of installing Grub/boot to a drive other than /dev/sda.

---

### Post by lessblue on 2011-08-04
Thank you Wim, I now have some idea what ***quiet splash*** does. I removed it and left ***nomodeset ***and this time I saw the boot process after which the login prompt did appear.

> **Wim Sturkenboom said:**
> I doubt it. Your system boots fine, so there is actually nothing wrong with grub. I would take the _quiet splash_ out and leave _nomodeset_ in. That would show the boot process on tty1.

Not sure why you don't end up with a login prompt on tty1. <alt><F2> gives you tty2. If that works properly, it's no train smash, just an annoyance ;) You propapbly still have tty3 (<alt><F3>).. tty6 (<alt><F6>) as well.

That seems to be solved. Now I'm a little concerned about my /dev/sde installation and am considering doing a reinstall (won't take much time and the drives are all empty) to sort it out. Hopefully someone can take a peek at my boot info script and fdisk info, is it something I can fix within the current installation?

---

### Post by lessblue on 2011-08-04
Just to continue documenting my attempts, I am running Recovery Mode and the drives are being checked for errors with this showing up:

/dev/sde3: 98508/9420800 files (0.1% non-contiguous), 983919/37672960 blocks

Hopefully fsck fixes it, it does seem to be taking a while.


From the boot info script regarding **/dev/sde** which is what is worrying me a bit now. Seems like boot info/files are on two different partions (sde1 and sde3)??:

```
sde1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub2 (v1.99)
    Boot sector info:   Grub2 (v1.99) is installed in the boot sector of sde1 
                       and looks at sector 9701736 of the same hard drive for 
                       core.img. core.img is at this location and looks for 
                       ?? on this drive.
    Mounting failed:   mount: wrong fs type, bad option, bad superblock on /dev/sde1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so


sde2: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sde3: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img
```

---

### Post by lessblue on 2011-08-08
I know a lot of threads die without anything significant that might help others so just to conclude this thread:

The problem summarized:

The way I had installed the drives in my Proliant was in a manner that caused my Ubuntu Server installation to wind up on a drive other than /dev/sda.

Initially: 
/dev/sda/   - 2TB drive split into two partitions 
/dev/sdb/   - 2TB drive split into two partitions
/dev/sdc/   - 2TB drive split into two partitions
/dev/sdd/   - 2TB drive split into two partitions
/dev/sde/   - 160GBB drive for Ubuntu Server installation 

The install to /dev/sde was fine but a few glitches like the blank screen issue (depending on how I fiddled with *nomodeset* it would load fully and leave a blank screen, or it would just hang with a blinking cursor). Tried a few things and several re-installs.

Including manual partitioning where I created a 500MB /boot partition, a / partition and a 6GB swap partition on /dev/sde (160GB drive). I tried grub-install /dev/sde1 (sde1 being the 500MB boot partition) but loading was never quite right. During one re-install I choose not to install GRUB to the MBR. The install at this point gave me the option to choose where to install and I choose /dev/sde1 naturally. Still wasn't quite right.


The final solution:

Finally I gave up and rearranged the hard drives (which will be a little problematic down the line when I decide to add another drive to the Proliant server).

For the last re-install, I installed the 160GB drive where it would be /dev/sda.

I then installed and I then let GRUB write to the MBR and voila, everything has been fine since. No need to mess with nomodeset or anything. 

I noticed that during the Grub part of the install, it said grub-install /dev/sda which seems to be the default and I think in the end that was the problem for me.

Now I know there must be a way to install Ubuntu Server on a drive other than /dev/sda and I tried to find various solutions via google but my limited knowledge never found a clean working solution.

In conclusion everything is fine now, but only after I rearranged the drives so that the install drive was /dev/sda instead of /dev/sde. So this is solved but somewhat incomplete as I never really got to the bottom of it.

---

