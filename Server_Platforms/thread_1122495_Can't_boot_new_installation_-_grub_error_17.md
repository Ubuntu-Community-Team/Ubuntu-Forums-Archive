---
title: "Can't boot new installation - grub error 17"
date: 2009-04-11
forum: Server Platforms
---

### Post by Nixie Pixel on 2009-04-11
I have a brand new server installation and I can't boot, I get an error 17.  Here is the boot info script result:

```
============================= Boot Info Summary: ==============================

 => No boot loader is installed in the MBR of /dev/sda
 => Grub0.97 is installed in the MBR of /dev/sdb and looks on the same drive 
    in partition #2 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Windows is installed in the MBR of /dev/sdc
 => Grub0.97 is installed in the MBR of /dev/sdd and looks on boot drive #2 in 
    partition #2 for /boot/grub/stage2 and /boot/grub/menu.lst.

sdb1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 8.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdc1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdd1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0008d43b

Partition  Boot         Start           End          Size  Id System



Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x91226c1c

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63   300,527,954   300,527,892  83 Linux
/dev/sdb2         300,527,955   312,576,704    12,048,750   5 Extended
/dev/sdb5         300,528,018   312,576,704    12,048,687  82 Linux swap / Solaris


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xb80b1ee3

Partition  Boot         Start           End          Size  Id System

/dev/sdc1                  63   976,768,064   976,768,002  83 Linux


Drive: sdd ___________________ _____________________________________________________

Disk /dev/sdd: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xfa73fa73

Partition  Boot         Start           End          Size  Id System

/dev/sdd1                  63   976,768,064   976,768,002  83 Linux


blkid -c /dev/null: ____________________________________________________________

/dev/sdb1: UUID="f8959aaf-69fe-4228-abae-d95708ee21e9" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdb5: UUID="e095a48a-7bf3-4326-bcf6-664b78bc373c" TYPE="swap" 
/dev/sdc1: LABEL="RAID2" UUID="57deba27-65d4-4b4b-ad82-078fad9cf463" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdd1: LABEL="RAID1" UUID="b7b67b08-f212-42d2-a8ee-f7de39273cce" SEC_TYPE="ext2" TYPE="ext3" 
/dev/loop0: TYPE="squashfs" 

=============================== "mount" output: ===============================

/proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
tmpfs on /lib/modules/2.6.27-7-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/modules/2.6.27-7-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
rootfs on / type rootfs (rw)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
/dev/scd0 on /cdrom type iso9660 (ro,noatime)
/dev/loop0 on /rofs type squashfs (ro,noatime)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)


=========================== sdb1/boot/grub/menu.lst: ===========================

# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		3

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title		Windows 95/98/NT/2000
# root		(hd0,0)
# makeactive
# chainloader	+1
#
# title		Linux
# root		(hd0,1)
# kernel	/vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=f8959aaf-69fe-4228-abae-d95708ee21e9 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=f8959aaf-69fe-4228-abae-d95708ee21e9

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title		Ubuntu 8.10, kernel 2.6.27-7-server
uuid		f8959aaf-69fe-4228-abae-d95708ee21e9
kernel		/boot/vmlinuz-2.6.27-7-server root=UUID=f8959aaf-69fe-4228-abae-d95708ee21e9 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-server

title		Ubuntu 8.10, kernel 2.6.27-7-server (recovery mode)
uuid		f8959aaf-69fe-4228-abae-d95708ee21e9
kernel		/boot/vmlinuz-2.6.27-7-server root=UUID=f8959aaf-69fe-4228-abae-d95708ee21e9 ro  single
initrd		/boot/initrd.img-2.6.27-7-server

title		Ubuntu 8.10, memtest86+
uuid		f8959aaf-69fe-4228-abae-d95708ee21e9
kernel		/boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST

=============================== sdb1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=f8959aaf-69fe-4228-abae-d95708ee21e9 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=e095a48a-7bf3-4326-bcf6-664b78bc373c none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sdb1: Location of files loaded by Grub: ===================


  92.2GB: boot/grub/menu.lst
  92.2GB: boot/grub/stage2
  92.2GB: boot/initrd.img-2.6.27-7-server
  92.3GB: boot/vmlinuz-2.6.27-7-server
  92.2GB: initrd.img
  92.3GB: vmlinuz
```

I am assuming that the problem has something to do with the fact that my first drive, an 80GB SATA drive, was supposed to be my O/S drive, but the server installation kept failing during drive detection if I said YES to the question about whether or not I should enable SATA RAID detection.  I could only continue if I said no.

So I ended up installing to a 160 GB IDE drive.  I would love to at least be able to boot the server today, though if someone can help me figure out how to install the server on the 80GB drive, that would be cool too!

---

### Post by meierfra. on 2009-04-11
> => Grub0.97 is installed in the MBR of /dev/sdb and looks on the same drive 
    in partition #2 for /boot/grub/stage2 and /boot/grub/menu.lst.

The boot files are  on the first partition of /dev/sdb. So you need  reinstall Grub:

```
sudo grub
```
and at the "Grub>" prompt:

```
root (hd1,0)
setup (hd1)
quit
```

Then set your  bios to boot from  the 160GB drive.

---

### Post by Nixie Pixel on 2009-04-12
Thank you again - as always, your suggestions work without any issues.  I now have a server that I can boot into!

(Maybe this is a separate issue, but whenever I "sudo shutdown now," it sends me to a recovery console rather than shutting down the computer - is this intended?)

---

### Post by meierfra. on 2009-04-12
> "sudo shutdown now," it sends me to a recovery console
Same for me.  "sudo poweroff" will turn of the computer.

---

