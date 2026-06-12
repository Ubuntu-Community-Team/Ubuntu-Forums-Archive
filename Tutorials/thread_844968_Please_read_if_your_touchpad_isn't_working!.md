---
title: "Please read if your touchpad isn't working!"
date: 2008-06-30
forum: Tutorials
---

### Post by kessaris on 2008-06-30
Having installed linux on a bunch of machines, you run into hardware that doesn't work out of the box.  It is very commonplace and to be expected, of course.  It's quite surprising, however, to install the latest ubuntu on a laptop only to discover that the touchpad isn't working!

This is exactly what happened to me just last week, when I installed Hardy Heron on my Sharp laptop.

I managed to find the solution strewn across the internet and on these forums, so I'd like to share my findings with you in case you're having the same problem.

First of all, my solution.  It may work for you if you have the same problem as I did.

**Symptoms:** kernel 2.6, synaptics style touchpad, doesn't work, or jumps around like crazy.  Possibly detected by the system, possibly not.

You can try adding these options to your kernel boot parameters.

```
i8042.nomux=1 i8042.noloop=1
```

How to do this?  You can select the option to edit the boot commands through GRUB at boot time, or you can manually edit the /boot/grub/menu.lst file, so this option will be persistent.

What's going on?  The i8042 chip is a common ps/2 keyboard and mouse controller.  For some reason it isn't working as we would expect with the the current line of 2.6 kernels.  Because of the way this chip interacts with the operating system, the mouse portion of the input can be lost in the shuffle.

The synaptics style touchpads are supposed to default to regular ps/2 style mouse operation if a special driver isn't present.  Because of this interaction with the i8042 controller chip and the kernel, the touchpads can become inoperational.

This would be the first option I would try in the case of any inoperational touchpad, ALPS, Synaptic or generic.

Just some details about the menu.lst file, here is my menu.lst file as an example.  The changes are in red:

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
timeout		9

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
# kopt=root=UUID=bd2ae7b9-80d5-457a-a953-fdcdb8c557c0 ro **[COLOR="Red"]i8042.nomux=1 i8042.noloop=1[/COLOR]**

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

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

title		Ubuntu 8.04, kernel 2.6.25.9
root		(hd0,0)
kernel		/vmlinuz-2.6.25.9 root=UUID=bd2... ro quiet splash **[COLOR="Red"]i8042.nomux=1 i8042.noloop=1[/COLOR]**
initrd		/initrd.img-2.6.25.9
quiet

title		Ubuntu 8.04, kernel 2.6.25.9 (recovery mode)
root		(hd0,0)
kernel		/vmlinuz-2.6.25.9 root=UUID=bd2... ro **[COLOR="Red"]i8042.nomux=1 i8042.noloop=1[/COLOR]** single
initrd		/initrd.img-2.6.25.9

title		Ubuntu 8.04, kernel 2.6.24-19-generic
root		(hd0,0)
kernel		/vmlinuz-2.6.24-19-generic root=UUID=bd2... ro quiet splash **[COLOR="Red"]i8042.nomux=1 i8042.noloop=1[/COLOR]** 
initrd		/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,0)
kernel		/vmlinuz-2.6.24-19-generic root=UUID=bd2ae... ro single **[COLOR="Red"]i8042.nomux=1 i8042.noloop=1 [/COLOR]**
initrd		/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04, kernel 2.6.24-16-generic
root		(hd0,0)
kernel		/vmlinuz-2.6.24-16-generic root=UUID=bd2... ro quiet splash **[COLOR="Red"]i8042.noloop=1 i8042.nomux=1 [/COLOR]**
initrd		/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root		(hd0,0)
kernel		/vmlinuz-2.6.24-16-generic root=UUID=bd2ae... ro  single **[COLOR="Red"]i8042.nomux=1 i8042.noloop=1[/COLOR]**
initrd		/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04, memtest86+
root		(hd0,0)
kernel		/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST
```

The order doesn't matter.  Please add the boot options to the commented section at the top under default options.  This will ensure it gets added every time the menu.lst file is regenerated (ie when you install a new kernel).  Then you can manually add the parameters to each of your boot entries, as I have outlined in red.  

I know this file gets regenerated whenever you install a new kernel.  You can also regenerate it by calling update-grub from the command line as a super user.  I preferred to just insert all the options by hand, just in case something else would break in an automatic update.

By the way you have to be a super user to edit the /boot/grub/menu.lst file.

Rebooting you may well have a working touchpad.

If there are any comments or criticisms of this method, I would be very glad to revise the instructions.  I do believe that this can quite likely fix an inoperational touchpad, and it does no harm if it is added to the kernel parameters.

It would be wise to back up the menu.lst file, or test it out by manually adding the boot parameters to grub at boot time.

Hope this saves someone the trouble of searching it out on the internet!

Best wishes,

Alexandros

---

### Post by kessaris on 2008-06-30
Here is another link that deals with issues related to scrolling:
[http://ubuntuforums.org/showthread.php?t=840596](http://ubuntuforums.org/showthread.php?t=840596)

---

### Post by wladicus on 2008-09-12
[COLOR="Navy"]Hi kessaris[/COLOR]
My problem is that the touchpad is identified as [COLOR="Red"]Synaptics[/COLOR] while it is actually a [COLOR="Red"]Logitech[/COLOR] and as a result I have no control over it whatsoever.  I actually want to turn the Touchpad OFF because it is an interfering nuisance when I type and I have a USB mouse plugged in anyway.  Therefore, I tried the changes you suggested.  I am running [COLOR="Blue"]Kubuntu[/COLOR] 8.04 LTS (Hardy Heron) in Wubi mode.  Before I started to tackle this Touchpad problem, the number lock would not come on automatically - then it came but the indicator light was off when it came on - then finally I found out how to make it work properly.  Now the thing that I would love to have fixed is the annoyance caused by the touchpad.  Below is the menu.lst file for Kubuntu with the changes you suggested. It is a bit different from the Ubuntu file you posted.  I rebooted with these changes and NOTHING. There was no difference, so I put the original menu.lst file back.  I still cannot in anyway access or control the Touchpad behaviour.  I have tried many approaches suggested in various forums, and still nothing.  Can you help!- Thank you for your time [COLOR="Blue"]kessaris[/COLOR]. - walt
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
# kopt=root=UUID=185480615480440A loop=/ubuntu/disks/root.disk ro [COLOR="Red"]i8042.nomux=1 i8042.noloop=1
[/COLOR]
## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=()/ubuntu/disks

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

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		()/ubuntu/disks
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=185480615480440A loop=/ubuntu/disks/root.disk ro quiet splash [COLOR="Red"]i8042.nomux=1 i8042.noloop=1[/COLOR]

initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		()/ubuntu/disks
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=185480615480440A loop=/ubuntu/disks/root.disk ro [COLOR="Red"]i8042.nomux=1 i8042.noloop=1[/COLOR] single


initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, memtest86+
root		()/ubuntu/disks
kernel		/boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows Vista/Longhorn (loader)
root		(hd0,0)
savedefault
chainloader	+1
```

---

### Post by kessaris on 2008-09-14
Hello,

It is indeed true that the touchpad can be annoying.

I'm afraid I don't know enough about the subject to make a full diagnosis of your situation.  

I do believe however, there may be an option to deactivate the touchpad from the bios.

---

### Post by wladicus on 2008-09-15
*** SOLVED FINALLY ***
From a terminal enter the following:
To disable the Touchpad -
```
sudo rmmod psmouse
``` 
To re-enable a disabled Touchpad -
```
sudo modprobe psmouse
``` 
I suppose this can be automated in a file somehow or even attached to a function key probably if someone has the knowhow.
I received this solution from the following link:

[http://ubuntuforums.org/showpost.php?p=5694509&postcount=13](http://ubuntuforums.org/showpost.php?p=5694509&postcount=13)

I managed to work out a detailed HOW TO for setting up **a shortcut key version of this** can be found in the last post at the following link:
>    [http://forums.techguy.org/unix-linux/746623-solved-deactivating-touchpad-kibuntu.html](http://forums.techguy.org/unix-linux/746623-solved-deactivating-touchpad-kibuntu.html)  

---

### Post by zombrax on 2009-08-09
Mate, I don't know how to thank you but this has saved my life on my new S42 BENQ laptop!! Thanks so much for putting up this tutorial and thanks for giving and helping the Ubuntu community out! 

You rock my friend :) Many thanks once again!

---

### Post by procco on 2012-09-25
Fantastic.  Hard to believe the solution to my touchpad problem would be found in a post from 2008.  But it was.

Just in case anyone else runs into this problem, I installed 11.04 64bit on a Panasonic CF-31 Toughbook and the touchpad would not work.  I tried 10.10, 11.10, 12.10 and even Fedora 16 - all with the same result: no touchpad.  After entering the boot parameters in the original post the touchpad worked.  Note: you have to power cycle the Toughbook before you enter these parameters the first time.  Rebooting doesn't work.

Thanks for posting this.:guitar:

---

