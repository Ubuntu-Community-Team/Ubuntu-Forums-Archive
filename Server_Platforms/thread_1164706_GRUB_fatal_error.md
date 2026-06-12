---
title: "GRUB fatal error"
date: 2009-05-19
forum: Server Platforms
---

### Post by dearmrdear on 2009-05-19
So, I'm setting up a new server. I tried installing it on my new system using the LVM manager option and grub boot loader installation failed (?). I used Ubuntu live disk and deleted the partitions so the next install would be clean. Tried again, no go, wiped the partitions again and installed without LVM , just use largest area option no go.. what am I doing wrong?

---

### Post by dearmrdear on 2009-05-20
No one? Did I post this in the wrong category?

---

### Post by koetjesreep on 2009-05-30
I have the same problem. No respons yet :(

---

### Post by dearmrdear on 2009-05-30
I realize that gurus help out of the kindness of their heart, but I wish someone would say something like "here's a thread on that topic" or even RTFM! That way I'd know it wasn't a bug it was just me!

Anyway, I think I fixed it by using the desktop live disk and partitioning sda. I then installed Xubuntu, configured things the way I like, Samba, openssh etc, then shutdown xwindow/xfce.

---

### Post by juxtatux on 2009-06-07
Keep getting the same issue here. Installed Jaunty 5 times now. Grub displays GRUB GRUB GRUB GRUB GRUB GRUB GRUB GRUB GRUB GRUB GRUB GRUB GRUB GRUB GRUB GRUB GRUB GRUB GRUB GRUB, etc.

Updated to Grub-PC which displays just one GRUB

Booting with SuperGrub disk I am able to access to MBR and load the kernel, with an INITRAMS prompt, but exit continues the boot. It appears to be complaining about an inaccessible volume, maybe the UUID, or the multiple drives but I'm not sure.

My setup has 3 scsi drives
/dev/sda 9GB
/dev/sda1 -boot
/dev/sda2 -swap
/dev/sda3 -LVM system

/dev/sdb 9GB
/dev/sdb1 -swap
/dev/sdb2 -LVM system

/dev/sdc 50GB
/dev/sdc1 -lvm well

Here is my FSTAB

> # Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/mapper/system-r00t during installation
UUID=f93dd173-d118-477f-b957-42689cdc87c4 /               ext4    noatime,relatime,errors=remount-ro 0       1
# /boot was on /dev/sda1 during installation
UUID=7139259a-bf2c-4d10-ae08-05124dc459b6 /boot           ext2    noatime,relatime 0       2
# /home was on /dev/mapper/well-home during installation
UUID=1cc941fa-92fe-4360-bfaf-d545551066a0 /home           ext4    noatime,relatime 0       2
# swap was on /dev/sda2 during installation
UUID=b2a5429a-bf32-4768-8db3-69de6620b2c3 none            swap    sw              0       0
# swap was on /dev/sdb1 during installation
UUID=4d15ee3f-1bb3-44f4-8523-2abe7769fa05 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0


Here is my menu.lst

> ## BEGIN AUTOMAGIC KERNELS LIST
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
# kopt=root=/dev/mapper/system-r00t ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=7139259a-bf2c-4d10-ae08-05124dc459b6

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
##      altoptions=(single-user) single
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

title           Chainload into GRUB 2
root            7139259a-bf2c-4d10-ae08-05124dc459b6
kernel          /grub/core.img

title           &#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;
&#65533;root

title           When you have verified GRUB 2 works, you can use this command to
root

title           complete the upgrade:  upgrade-from-grub-legacy
root

title           &#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;
&#65533;root

title           Debian GNU/Linux, kernel 2.6.28-11-server
root            7139259a-bf2c-4d10-ae08-05124dc459b6
kernel          /vmlinuz-2.6.28-11-server root=/dev/mapper/system-r00t ro quiet splash
initrd          /initrd.img-2.6.28-11-server

title           Debian GNU/Linux, kernel 2.6.28-11-server (recovery mode)
root            7139259a-bf2c-4d10-ae08-05124dc459b6
kernel          /vmlinuz-2.6.28-11-server root=/dev/mapper/system-r00t ro single
initrd          /initrd.img-2.6.28-11-server

title           Debian GNU/Linux, kernel memtest86+
root            7139259a-bf2c-4d10-ae08-05124dc459b6
kernel          /memtest86+.bin


Fdisk also shows the partition with a boot flag.

Anything else? I guess there is LiLo...

Thanx!
~Juxtatux

---

