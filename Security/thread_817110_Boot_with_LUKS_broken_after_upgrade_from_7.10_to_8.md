---
title: "Boot with LUKS broken after upgrade from 7.10 to 8.04"
date: 2008-06-03
forum: Security
---

### Post by stukov on 2008-06-03
Hello,

    I built a laptop with Ubuntu 7.10 + encrypted hard disk. I followed the steps in this beautiful and simple tutorial: [https://help.ubuntu.com/community/EncryptedFilesystemHowto8?highlight=(encryptedfilesystem](https://help.ubuntu.com/community/EncryptedFilesystemHowto8?highlight=(encryptedfilesystem))

I've recently upgrade to 8.04, the upgrade went fine. However, when I boot the system, instead of prompting me the passphrase to unlock my LUKS keys, I get 5/6 screens of error messages telling me that /dev/sda6 is not found (my root partition). After 2/3 minutes of timeout delay, I get a prompt where I can unlock my keys with "cryptsetup" and then exit. The machine then boots correctly.

Searching the forums and Google, I've came up with the option of rebuilding my initramfs (update-initramfs -u `uname -r`) without success.

Any ideas?

Thanks!

---

### Post by hyper_ch on 2008-06-03
When I manually encrypted on 7.04 and updated to 7.10 it was no problem at all...

From 7.10 you have encryption available in the alternate install cd... and have also upgraded to 8.04 without an issue... BUT I did not use any LVM.

Could it be that the drives are referenced wrongly? I noticed that sometimes sda and sdc change on my system.... so I use the UUID.

---

### Post by kevdog on 2008-06-03
How do you use luks/dm-crypt without LVM?  Is this a switch in the installation?

---

### Post by hyper_ch on 2008-06-04
Just don't select to use lvm encrypted....

I normally let only / encrypted by installatin and set then the other up later (including swap)... I don't use a seperate home anymore and moutn my othe drives in /media

---

### Post by stukov on 2008-06-04
All right I'm going to try this with UUID. Is there only /etc/crypttab I should change to do this?

Thanks for the replies!

---

### Post by hyper_ch on 2008-06-05
only crypttab

---

### Post by stukov on 2008-06-05
OK I tried with the UUID in /etc/crypttab. I found the UUID with "vol_id /dev/sda6" and still got these error messages at boot:

```
cryptsetup: Source device /dev/sda6 not found
Setting up cryptographic volume root (based on /dev/sda6)
/scripts/local-top/cryptroot: /scripts/local-top/cryptroot: 286: /sbin/udevsettle: not found
```
Then
```
cryptsetup: Source device UUID=<UUID> not found
Setting up cryptographic volume root (based on UUID=<UUID>)
/scripts/local-top/cryptroot: /scripts/local-top/cryptroot: 286: /sbin/udevsettle: not found
```

Any ideas?

---

### Post by hyper_ch on 2008-06-05
what's the entry in the crypttab for you?

and can you open the crypt devices manually?

---

### Post by stukov on 2008-06-05
```
$ cat /etc/crypttab
# <target name> <source device>         <key file>      <options>
swap            /dev/sda5               /dev/random     swap
root            UUID=7c7a994d-9be2-41e7-9a77-b51b5d39cebf       none            luks
```

And yes, when I enter manually the "cryptsetup" line in the busybox shell that appears after a 5 minutes timeout the systems boots.

Thanks for the reply!

---

### Post by hyper_ch on 2008-06-05
ah :) use this:

```

sdd1_crypt      /dev/disk/by-uuid/247ad289-dbe5-4419-9965-e3cd30f0b080  none  luks

```

---

### Post by stukov on 2008-06-05
hyper_ch, thanks for the reply.

I changed my file according to yours (only the /dev/disk/by-uuid/... part). However, I still have the very same errors, except the drive name changed for dev/disk/by-uuid/...

I did ran:
# cd /boot
# update-initramfs -u ALL

after the change.

Anything else I am missing?

---

### Post by hyper_ch on 2008-06-05
post your crypttab, fstab and grub menu.lst

---

### Post by stukov on 2008-06-05
fstab:
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/mapper/root /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda2
UUID=719db5c2-d41a-4e29-865f-ade77fb7bbab /boot           ext3    defaults        0       2
# /dev/sda6
# /dev/sda5
/dev/mapper/swap none           swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
/dev/scd0       /media/floppy1  auto    rw,user,noauto  0       0

# disk1 (500 Go)
/dev/mapper/disk1       /media/disk1    ext3    rw,user,noauto  0       0
/dev/mapper/disk2       /media/disk2    ext3    rw,user,noauto  0       0
/dev/mapper/disk3       /media/disk3    ext3    rw,user,noauto  0       0
/dev/mapper/disk4       /media/disk4    ext3    rw,user,noauto  0       0
```

crypttab:
```
# <target name> <source device>         <key file>      <options>
swap            /dev/sda5               /dev/random     swap
root            /dev/disk/by-uuid/7c7a994d-9be2-41e7-9a77-b51b5d39cebf  none            luks
```

menu.lst
```
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
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
# array will desync and will not let you boot your system.
default         0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout         10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

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
# title         Windows 95/98/NT/2000
# root          (hd0,0)
# makeactive
# chainloader   +1
#
# title         Linux
# root          (hd0,1)
# kernel        /vmlinuz root=/dev/hda2 ro
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
# kopt=root=/dev/mapper/root ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,1)

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
# defoptions=

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

title           Ubuntu 8.04, kernel 2.6.24-17-generic
root            (hd0,1)
kernel          /vmlinuz-2.6.24-17-generic root=/dev/mapper/root ro quiet nosplash
initrd          /initrd.img-2.6.24-17-generic
quiet

title           Ubuntu 8.04, kernel 2.6.24-17-generic (recovery mode)
root            (hd0,1)
kernel          /vmlinuz-2.6.24-17-generic root=/dev/mapper/root ro single
initrd          /initrd.img-2.6.24-17-generic

title           Ubuntu 8.04, kernel 2.6.22-14-generic
root            (hd0,1)
kernel          /vmlinuz-2.6.22-14-generic root=/dev/mapper/root ro
initrd          /initrd.img-2.6.22-14-generic
quiet

title           Ubuntu 8.04, kernel 2.6.22-14-generic (recovery mode)
root            (hd0,1)
kernel          /vmlinuz-2.6.22-14-generic root=/dev/mapper/root ro single
initrd          /initrd.img-2.6.22-14-generic

title           Ubuntu 8.04, kernel 2.6.20-16-generic
root            (hd0,1)
kernel          /vmlinuz-2.6.20-16-generic root=/dev/mapper/root ro
initrd          /initrd.img-2.6.20-16-generic
quiet

title           Ubuntu 8.04, kernel 2.6.20-16-generic (recovery mode)
root            (hd0,1)
kernel          /vmlinuz-2.6.20-16-generic root=/dev/mapper/root ro single
initrd          /initrd.img-2.6.20-16-generic

title           Ubuntu 8.04, kernel 2.6.20-15-generic
root            (hd0,1)
kernel          /vmlinuz-2.6.20-15-generic root=/dev/mapper/root ro
initrd          /initrd.img-2.6.20-15-generic
quiet

title           Ubuntu 8.04, kernel 2.6.20-15-generic (recovery mode)
root            (hd0,1)
kernel          /vmlinuz-2.6.20-15-generic root=/dev/mapper/root ro single
initrd          /initrd.img-2.6.20-15-generic

title           Ubuntu 8.04, memtest86+
root            (hd0,1)
kernel          /memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title           Microsoft Windows XP Professionnel
root            (hd0,0)
savedefault
makeactive
chainloader     +1
```

---

### Post by hyper_ch on 2008-06-05
strange, that works for me :(

the only difference is that I don't have the "defaults" options in fstab for my root partition

---

### Post by stukov on 2008-06-05
Yes. It is really weird. As if the drivers were detected only after the system tried to decrypt the drives automatically. And all of that came with the upgrade to 8.04... I am going to try without "defaults".

Thanks!

---

### Post by stukov on 2008-06-05
No use... hyper_ch, can you please post/PM your working config?

Thank you very much for your help.

---

### Post by hyper_ch on 2008-06-05
```

sda4_crypt	/dev/disk/by-uuid/7db6b61a-eab4-4451-a410-d7108c355191	none	luks

#sdb1_crypt	/dev/sdb1	/root/root.key	luks
sdb1_crypt	/dev/disk/by-uuid/6a636e05-c562-4d4b-b3fa-54dc3d3dda3c	/root/root.key	luks
#sdc1_crypt	/dev/sdc1	/root/root.key	luks
sdc1_crypt	/dev/disk/by-uuid/f9ceb1b0-e084-4383-be4f-fc49b8f15545	/root/root.key	luks
#sdd1_crypt	/dev/sdd1	/root/root.key	luks
sdd1_crypt	/dev/disk/by-uuid/247ad289-dbe5-4419-9965-e3cd30f0b080	/root/root.key	luks

#cswap		/dev/sda3	/dev/random	swap
#cswap	/dev/disk/by-uuid/96b92d0b-97fb-48d3-95af-984558c4460b	/dev/random	swap

```

```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/mapper/sda4_crypt /               ext3    errors=remount-ro 0       1
# /dev/sda2
UUID=24875c07-ce8a-4099-8cb8-88e56a6e6d29 /boot           ext3    relatime        0       2
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

# Crypto Drives
/dev/mapper/sdb1_crypt  /media/sdb1     ext3    defaults        0       2
/dev/mapper/sdc1_crypt  /media/sdc1     ext3    defaults        0       2
/dev/mapper/sdd1_crypt  /media/sdd1     ext3    defaults        0       2

#/dev/mapper/swap	none	swap	sw	0	0

```


```

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
timeout		10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

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
# kopt=root=/dev/mapper/sda4_crypt ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,1)

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

title		Ubuntu 8.04, kernel 2.6.24-18-generic
root		(hd0,1)
kernel		/vmlinuz-2.6.24-18-generic root=/dev/mapper/sda4_crypt ro quiet splash
initrd		/initrd.img-2.6.24-18-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-18-generic (recovery mode)
root		(hd0,1)
kernel		/vmlinuz-2.6.24-18-generic root=/dev/mapper/sda4_crypt ro single
initrd		/initrd.img-2.6.24-18-generic

title		Ubuntu 8.04, kernel 2.6.24-17-generic
root		(hd0,1)
kernel		/vmlinuz-2.6.24-17-generic root=/dev/mapper/sda4_crypt ro quiet splash
initrd		/initrd.img-2.6.24-17-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-17-generic (recovery mode)
root		(hd0,1)
kernel		/vmlinuz-2.6.24-17-generic root=/dev/mapper/sda4_crypt ro single
initrd		/initrd.img-2.6.24-17-generic

title		Ubuntu 8.04, kernel 2.6.24-16-generic
root		(hd0,1)
kernel		/vmlinuz-2.6.24-16-generic root=/dev/mapper/sda4_crypt ro quiet splash
initrd		/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root		(hd0,1)
kernel		/vmlinuz-2.6.24-16-generic root=/dev/mapper/sda4_crypt ro single
initrd		/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04, memtest86+
root		(hd0,1)
kernel		/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1

```

---

### Post by stukov on 2008-06-06
I've opened the following bug report: [https://bugs.launchpad.net/ubuntu/+source/cryptsetup/+bug/237716](https://bugs.launchpad.net/ubuntu/+source/cryptsetup/+bug/237716)

---

