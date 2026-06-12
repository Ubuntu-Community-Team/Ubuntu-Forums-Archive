---
title: "Boot into windows."
date: 2010-11-11
forum: Server Platforms
---

### Post by ElMoshe on 2010-11-11
Does anyone know how I can boot into windows? I have NO IDEA what to do, so I'm gonna need like a step-by-step. Thanks

---

### Post by Jetso on 2010-11-11
Can you please provide more details? I'm having a gard time understanding what you want:confused:

---

### Post by laurenbanjo on 2010-11-11
Are you on a dual-boot, or did you completely override Windows?

It should give you an option at start up.

---

### Post by ElMoshe on 2010-11-12
> **Jetso said:**
> Can you please provide more details? I'm having a gard time understanding what you want:confused:

I'd like to run windows on my laptop really quick to go get some files. I mean, it's not the end of the world if I can't, but if I can, I'd like to!

Thanks =]

---

### Post by oldfred on 2010-11-12
So we can see what is where:

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the post's menu and then paste the contents between the generated [ code][ /code] tags.

If you can boot Ubuntu or from liveCD you should be able to copy files from your windows partition.

---

### Post by arrrghhh on 2010-11-12
> **ElMoshe said:**
> I'd like to run windows on my laptop really quick to go get some files. I mean, it's not the end of the world if I can't, but if I can, I'd like to!

Thanks =]

We need a lot more info.  So are you saying you have Windows installed and can't access it?  Or you want to install Windows to access some files...?  That doesn't make sense, if you only have Ubuntu on your laptop, why would you need to install Windows to access any files?  Ubuntu can see Windows partitions without a problem.

---

### Post by ElMoshe on 2010-11-12
> **oldfred said:**
> So we can see what is where:

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the post's menu and then paste the contents between the generated [ code][ /code] tags.

If you can boot Ubuntu or from liveCD you should be able to copy files from your windows partition.
 

                ```
Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/menu.lst /boot/grub/grub.cfg /etc/fstab 
                       /boot/grub/core.img

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048   306,626,559   306,624,512  83 Linux
/dev/sda2         306,628,606   312,580,095     5,951,490   5 Extended
/dev/sda5         306,628,608   312,580,095     5,951,488  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        515e14bb-d72a-4bd3-b729-9bb9656340bd   ext4                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        5b1af2a7-c5fb-476e-a94b-d5e8f0b8dd34   swap                                     
/dev/sda: PTTYPE="dos" 
error: /dev/sdb: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda1        /                        ext4       (rw,errors=remount-ro,commit=600)


=========================== sda1/boot/grub/menu.lst: ===========================

# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-legacy-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default        0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout        3

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
# title        Windows 95/98/NT/2000
# root        (hd0,0)
# makeactive
# chainloader    +1
#
# title        Linux
# root        (hd0,1)
# kernel    /vmlinuz root=/dev/hda2 ro
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
# kopt=root=UUID=515e14bb-d72a-4bd3-b729-9bb9656340bd ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=515e14bb-d72a-4bd3-b729-9bb9656340bd

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

## specify if running in Xen domU or have grub detect automatically
## update-grub will ignore non-xen kernels when running in domU and vice versa
## e.g. indomU=detect
##      indomU=true
##      indomU=false
# indomU=detect

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

title        Ubuntu 10.10, kernel 2.6.35-22-generic
uuid        515e14bb-d72a-4bd3-b729-9bb9656340bd
kernel        /boot/vmlinuz-2.6.35-22-generic root=UUID=515e14bb-d72a-4bd3-b729-9bb9656340bd ro quiet splash 
initrd        /boot/initrd.img-2.6.35-22-generic

title        Ubuntu 10.10, kernel 2.6.35-22-generic (recovery mode)
uuid        515e14bb-d72a-4bd3-b729-9bb9656340bd
kernel        /boot/vmlinuz-2.6.35-22-generic root=UUID=515e14bb-d72a-4bd3-b729-9bb9656340bd ro  single
initrd        /boot/initrd.img-2.6.35-22-generic

title        Ubuntu 10.10, kernel 2.6.32-25-generic
uuid        515e14bb-d72a-4bd3-b729-9bb9656340bd
kernel        /boot/vmlinuz-2.6.32-25-generic root=UUID=515e14bb-d72a-4bd3-b729-9bb9656340bd ro quiet splash 
initrd        /boot/initrd.img-2.6.32-25-generic

title        Ubuntu 10.10, kernel 2.6.32-25-generic (recovery mode)
uuid        515e14bb-d72a-4bd3-b729-9bb9656340bd
kernel        /boot/vmlinuz-2.6.32-25-generic root=UUID=515e14bb-d72a-4bd3-b729-9bb9656340bd ro  single
initrd        /boot/initrd.img-2.6.32-25-generic

title        Ubuntu 10.10, kernel 2.6.32-24-generic
uuid        515e14bb-d72a-4bd3-b729-9bb9656340bd
kernel        /boot/vmlinuz-2.6.32-24-generic root=UUID=515e14bb-d72a-4bd3-b729-9bb9656340bd ro quiet splash 
initrd        /boot/initrd.img-2.6.32-24-generic

title        Ubuntu 10.10, kernel 2.6.32-24-generic (recovery mode)
uuid        515e14bb-d72a-4bd3-b729-9bb9656340bd
kernel        /boot/vmlinuz-2.6.32-24-generic root=UUID=515e14bb-d72a-4bd3-b729-9bb9656340bd ro  single
initrd        /boot/initrd.img-2.6.32-24-generic

title        Ubuntu 10.10, kernel 2.6.32-21-generic
uuid        515e14bb-d72a-4bd3-b729-9bb9656340bd
kernel        /boot/vmlinuz-2.6.32-21-generic root=UUID=515e14bb-d72a-4bd3-b729-9bb9656340bd ro quiet splash 
initrd        /boot/initrd.img-2.6.32-21-generic

title        Ubuntu 10.10, kernel 2.6.32-21-generic (recovery mode)
uuid        515e14bb-d72a-4bd3-b729-9bb9656340bd
kernel        /boot/vmlinuz-2.6.32-21-generic root=UUID=515e14bb-d72a-4bd3-b729-9bb9656340bd ro  single
initrd        /boot/initrd.img-2.6.32-21-generic

title        Chainload into GRUB 2
root        515e14bb-d72a-4bd3-b729-9bb9656340bd
kernel        /boot/grub/core.img

title        Ubuntu 10.10, memtest86+
uuid        515e14bb-d72a-4bd3-b729-9bb9656340bd
kernel        /boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST

=========================== sda1/boot/grub/grub.cfg: ===========================

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
search --no-floppy --fs-uuid --set 515e14bb-d72a-4bd3-b729-9bb9656340bd
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
search --no-floppy --fs-uuid --set 515e14bb-d72a-4bd3-b729-9bb9656340bd
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
insmod ext2
set root='(hd0,1)'
search --no-floppy --fs-uuid --set 515e14bb-d72a-4bd3-b729-9bb9656340bd
insmod png
if background_image /usr/share/images/desktop-base/moreblue-orbit-grub.png ; then
  set color_normal=black/black
  set color_highlight=magenta/black
else
  set menu_color_normal=white/black
  set menu_color_highlight=black/light-gray
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.32-25-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 515e14bb-d72a-4bd3-b729-9bb9656340bd
    linux    /boot/vmlinuz-2.6.32-25-generic root=UUID=515e14bb-d72a-4bd3-b729-9bb9656340bd ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-25-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 515e14bb-d72a-4bd3-b729-9bb9656340bd
    echo    'Loading Linux 2.6.32-25-generic ...'
    linux    /boot/vmlinuz-2.6.32-25-generic root=UUID=515e14bb-d72a-4bd3-b729-9bb9656340bd ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 515e14bb-d72a-4bd3-b729-9bb9656340bd
    linux    /boot/vmlinuz-2.6.32-24-generic root=UUID=515e14bb-d72a-4bd3-b729-9bb9656340bd ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 515e14bb-d72a-4bd3-b729-9bb9656340bd
    echo    'Loading Linux 2.6.32-24-generic ...'
    linux    /boot/vmlinuz-2.6.32-24-generic root=UUID=515e14bb-d72a-4bd3-b729-9bb9656340bd ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 515e14bb-d72a-4bd3-b729-9bb9656340bd
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=515e14bb-d72a-4bd3-b729-9bb9656340bd ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 515e14bb-d72a-4bd3-b729-9bb9656340bd
    echo    'Loading Linux 2.6.32-21-generic ...'
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=515e14bb-d72a-4bd3-b729-9bb9656340bd ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 515e14bb-d72a-4bd3-b729-9bb9656340bd
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 515e14bb-d72a-4bd3-b729-9bb9656340bd
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
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

=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sda1       /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=5b1af2a7-c5fb-476e-a94b-d5e8f0b8dd34 none            swap    sw              0       0

=================== sda1: Location of files loaded by Grub: ===================


 146.1GB: boot/grub/core.img
 129.3GB: boot/grub/grub.cfg
 146.1GB: boot/grub/menu.lst
 146.1GB: boot/initrd.img-2.6.32-21-generic
 146.3GB: boot/initrd.img-2.6.32-24-generic
 146.8GB: boot/initrd.img-2.6.32-25-generic
   2.7GB: boot/initrd.img-2.6.35-22-generic
 146.1GB: boot/vmlinuz-2.6.32-21-generic
 146.3GB: boot/vmlinuz-2.6.32-24-generic
 146.3GB: boot/vmlinuz-2.6.32-25-generic
 146.9GB: boot/vmlinuz-2.6.35-22-generic
   2.7GB: initrd.img
 146.8GB: initrd.img.old
 146.9GB: vmlinuz
 146.3GB: vmlinuz.old
=======Devices which don't seem to have a corresponding hard drive==============

sdb 
```

---

### Post by ElMoshe on 2010-11-12
> **arrrghhh said:**
> We need a lot more info.  So are you saying you have Windows installed and can't access it?  Or you want to install Windows to access some files...?  That doesn't make sense, if you only have Ubuntu on your laptop, why would you need to install Windows to access any files?  Ubuntu can see Windows partitions without a problem.

And also-- honestly, get files was instead of my ten-million paragraph reason. Still, I'd like to know how to boot into windows.

Thanks!!

---

### Post by arrrghhh on 2010-11-12
> **ElMoshe said:**
> And also-- honestly, get files was instead of my ten-million paragraph reason. Still, I'd like to know how to boot into windows.

Thanks!!

Doesn't look like you have Windows installed, so you'll never be able to boot it.  I only see Linux partitions in that output you posted...

---

### Post by Jetso on 2010-11-12
I do believe you will have to buy windows?

---

