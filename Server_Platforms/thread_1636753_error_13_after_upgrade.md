---
title: "error 13 after upgrade"
date: 2010-12-03
forum: Server Platforms
---

### Post by mjetpax on 2010-12-03
Hi,

I run a small home/hobby server. I attempted to upgrade it this morning. It was previously using 8.04 lts. I followed the instructions found here, [https://help.ubuntu.com/community/LucidUpgrades#Network](https://help.ubuntu.com/community/LucidUpgrades#Network) Upgrade for Ubuntu Servers (Recommended)

I followed the on-screen instructions. After the installation was complete, I rebooted the server. On start up, I was greeted by this message "error 13: Invalid or unsupported executable format."

I have since tried booting into every 10.04 kernel listed. However, the results are the same. I have attempted to find a solution via web search, but have had difficulty finding a solution that is appropriate for my situation.

Any advise would be greatly appreciated.

~ Thanks

---

### Post by sikander3786 on 2010-12-03
Please boot an Ubuntu Desktop Live CD/USB and post the output of bootinfoscript as per instructions here.

[http://bootinfoscript.sourceforge.net](http://bootinfoscript.sourceforge.net)

It would provide us with lots of details regarding your current problem.

Wrap your output with proper code # tags from post menu. [/code] at the end and [code] at the beginning of your text.

---

### Post by mjetpax on 2010-12-03
Thanks for the reply. I followed the steps you outlined and below is the boot info.

```

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

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

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   487,653,074   487,653,012  83 Linux
/dev/sda2         487,653,075   488,392,064       738,990   5 Extended
/dev/sda5         487,653,138   488,392,064       738,927  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        b68e1e67-8f04-48c1-9388-e5fabd7145d0   ext3                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        6174ef1c-aebf-478e-b538-d041e94f556b   swap                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


=========================== sda1/boot/grub/menu.lst: ===========================

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
default        2

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
# kopt=root=UUID=b68e1e67-8f04-48c1-9388-e5fabd7145d0 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,0)

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

title        Ubuntu 10.04 LTS, kernel 2.6.32-21-generic-pae
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.32-21-generic-pae root=UUID=b68e1e67-8f04-48c1-9388-e5fabd7145d0 ro quiet splash 
initrd        /boot/initrd.img-2.6.32-21-generic-pae
quiet

title        Ubuntu 10.04 LTS, kernel 2.6.32-21-generic-pae (recovery mode)
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.32-21-generic-pae root=UUID=b68e1e67-8f04-48c1-9388-e5fabd7145d0 ro  single
initrd        /boot/initrd.img-2.6.32-21-generic-pae

title        Ubuntu 10.04 LTS, kernel 2.6.24-16-server
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.24-16-server root=UUID=b68e1e67-8f04-48c1-9388-e5fabd7145d0 ro quiet splash 
initrd        /boot/initrd.img-2.6.24-16-server
quiet

title        Ubuntu 10.04 LTS, kernel 2.6.24-16-server (recovery mode)
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.24-16-server root=UUID=b68e1e67-8f04-48c1-9388-e5fabd7145d0 ro  single
initrd        /boot/initrd.img-2.6.24-16-server

title        Ubuntu 10.04 LTS, kernel 2.6.22-14-server
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.22-14-server root=UUID=b68e1e67-8f04-48c1-9388-e5fabd7145d0 ro quiet splash 
initrd        /boot/initrd.img-2.6.22-14-server
quiet

title        Ubuntu 10.04 LTS, kernel 2.6.22-14-server (recovery mode)
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.22-14-server root=UUID=b68e1e67-8f04-48c1-9388-e5fabd7145d0 ro  single
initrd        /boot/initrd.img-2.6.22-14-server

title        Ubuntu 10.04 LTS, memtest86+
root        (hd0,0)
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=b68e1e67-8f04-48c1-9388-e5fabd7145d0 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=646007ff-4ecc-4de4-b34a-80b368ebbc78 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0

=================== sda1: Location of files loaded by Grub: ===================


   4.2GB: boot/grub/menu.lst
   3.9GB: boot/grub/stage2
   3.9GB: boot/initrd.img-2.6.22-14-server
   3.9GB: boot/initrd.img-2.6.22-14-server.bak
 208.1GB: boot/initrd.img-2.6.24-16-server
   4.1GB: boot/initrd.img-2.6.24-16-server.bak
 208.0GB: boot/initrd.img-2.6.32-21-generic-pae
   3.9GB: boot/vmlinuz-2.6.22-14-server
 208.1GB: boot/vmlinuz-2.6.24-16-server
 208.0GB: boot/vmlinuz-2.6.32-21-generic-pae
 208.0GB: initrd.img
 208.1GB: initrd.img.old
 208.0GB: vmlinuz
 208.1GB: vmlinuz.old

```

---

### Post by sikander3786 on 2010-12-04
I don't know much about Grub Legacy. The error you are receiving is definitely recoverable. And you may be able to boot using your existing Grub Legacy.

The only solution that comes to my mind is to chroot your Ubuntu partition from a live CD/USB and upgrade to Grub2 (the default for 9.10 and above).

You'll need to follow steps 1 and 2 from this guide by drs305.

[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)

And then upgrade to Grub2 as mentioned here.

[https://help.ubuntu.com/community/Grub2#Upgrading%20to%20GRUB%202](https://help.ubuntu.com/community/Grub2#Upgrading%20to%20GRUB%202)

I would advise to hang in there and let some other experienced mate answer this question more appropriately than I did. Or at least, let the consensus to develop ;-)

---

### Post by mjetpax on 2010-12-04
Thanks so much for your help. I really appreciate your expertise in this matter. I have sometime later today and will give your suggestion a shot. I will let you know how it goes.

~ Thanks

---

