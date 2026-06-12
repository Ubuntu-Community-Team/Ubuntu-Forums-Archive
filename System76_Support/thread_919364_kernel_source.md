---
title: "kernel source"
date: 2008-09-13
forum: System76 Support
---

### Post by andrewdied on 2008-09-13
I tried to install VirtualBox 2.0.2, but it needs the kernel sources to compile a piece.  I didn't see kernel sources in package manager when I searched for "kernel".  Does anyone know what that package is called?  (Yeah, I'm sure there are variants.)  I'm runing 64 bit ubuntu 8.04 on a serval performance laptop.

Thanks for the help.

---

### Post by gaussian on 2008-09-14
I think it suffices to install linux-headers-generic. You typically don't need the actual source unless you want to recompile the kernel.

---

### Post by Yannick Le Saint kyncani on 2008-09-14
And the kernel sources package is linux-source.

---

### Post by thomasaaron on 2008-09-15
I did not have to do all of that to install Virtual Box. I just downloaded the .deb from Sun and installed it. It took care of everything else.

I've installed it from the Repos the same way (however, the one from the repos did not support USB, so I went to Sun's version).

---

### Post by andrewdied on 2008-09-15
> **thomasaaron said:**
> I did not have to do all of that to install Virtual Box. I just downloaded the .deb from Sun and installed it. It took care of everything else.

I've installed it from the Repos the same way (however, the one from the repos did not support USB, so I went to Sun's version).

Huh.  I downloaded the 2.0.2 deb file, but I get this error:

VirtualBox will not start until this problem is fixed. Please consult /var/log/vbox-install.log to find out why the kernel module does not compile. Most probably the kernel sources were not found. Install them and execute

  /etc/init.d/vboxdrv setup

as root.


andrew@ubuntu:~$ cat /var/log/vbox-install.log 
Makefile:142: *** Error: unable to find the sources of your current Linux kernel. Specify KERN_DIR=<directory> and run Make again.  Stop.


So I'm doing something a little funky somewhere.  I'll look around and see what it is --maybe export a variable or something.

---

### Post by thomasaaron on 2008-09-15
try...

sudo apt-get install linux-source-2.6.24
sudo /etc/init.d/vboxdrv setup

---

### Post by andrewdied on 2008-09-15
> **thomasaaron said:**
> try...

sudo apt-get install linux-source-2.6.24
sudo /etc/init.d/vboxdrv setup

andrew@ubuntu:~$ cat /var/log/vbox-install.log 
Makefile:142: *** Error: unable to find the sources of your current Linux kernel. Specify KERN_DIR=<directory> and run Make again.  Stop.
andrew@ubuntu:~$ export KRN_DIR=/usr/src/linux-headers-2.6.24-19
linux-headers-2.6.24-19/         linux-headers-2.6.24-19-generic/
andrew@ubuntu:~$ export KRN_DIR=/usr/src/linux-headers-2.6.24-19
andrew@ubuntu:~$ sudo /etc/init.d/vboxdrv setup
 * Stopping VirtualBox kernel module                                               *  done.
 * Recompiling VirtualBox kernel module                                           
 * Look at /var/log/vbox-install.log to find out what went wrong
andrew@ubuntu:~$ cat /var/log/vbox-install.log 
Makefile:142: *** Error: unable to find the sources of your current Linux kernel. Specify KERN_DIR=<directory> and run Make again.  Stop.

I also tried the generic headers.

andrew@ubuntu:~$ export KERN_DIR=/usr/src/linux-headers-2.6.24-19-generic/
andrew@ubuntu:~$ sudo /etc/init.d/vboxdrv setup
 * Stopping VirtualBox kernel module                                               *  done.
 * Recompiling VirtualBox kernel module                                           
 * Look at /var/log/vbox-install.log to find out what went wrong
andrew@ubuntu:~$ cat /var/log/vbox-install.log 
Makefile:142: *** Error: unable to find the sources of your current Linux kernel. Specify KERN_DIR=<directory> and run Make again.  Stop.


I must be missing something obvious.  I have the .26 linux-headers installed in the package manager, though.

---

### Post by andrewdied on 2008-09-15
Figured out part. I'm running 2.26.24-17, but the latest package I have installed is 2.26.24-19. Of course, -17 is the one set of headers I don't have installed.

How do I get ubuntu to use the later kernel version?  I'm really clueless with ubuntu.  I'd figured out the voodoo on slackware 3.0 back in the day, but the easy things mystify me now.

---

### Post by gaussian on 2008-09-15
> **andrewdied said:**
> Figured out part. I'm running 2.26.24-17, but the latest package I have installed is 2.26.24-19. Of course, -17 is the one set of headers I don't have installed.

How do I get ubuntu to use the later kernel version?  I'm really clueless with ubuntu.  I'd figured out the voodoo on slackware 3.0 back in the day, but the easy things mystify me now.

Install linux-image-generic and linux-headers-generic, they will point to the latest stable version always.

---

### Post by andrewdied on 2008-09-16
I already have those two packages installed.  Is it ok to force a reinstall of those packages?

---

### Post by gaussian on 2008-09-17
> 
I already have those two packages installed. Is it ok to force a reinstall of those packages? 


I don't think you have to do a reinstall of those packages. If you have them the only thing you need to do to make sure you are running the greatest and latest is to reboot after every Kernel update.

---

### Post by andrewdied on 2008-09-17
> **gaussian said:**
> I don't think you have to do a reinstall of those packages. If you have them the only thing you need to do to make sure you are running the greatest and latest is to reboot after every Kernel update.

I've rebooted several times, and according to the module compiler for vbox, I'm still running the older kernel.  

I've done a little grub searching, and ran grub-update (with sudo).  While it found the 19 kernel, it's still using the 17 one:

$ sudo update-grub

Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /boot/vmlinuz-2.6.24-19-generic
Found kernel: /boot/vmlinuz-2.6.24-18-generic
Found kernel: /boot/vmlinuz-2.6.24-17-generic
Found kernel: /boot/memtest86+.bin
Updating /boot/grub/menu.lst ... done

But /boot/grub/menu.lst still has 17:
## ## End Default Options ##

title		Ubuntu 8.04, kernel 2.6.24-17-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-17-generic root=UUID=6c814527-5db0-4129-b3bc-f41a16213147 ro quiet splash
initrd		/boot/initrd.img-2.6.24-17-generic
quiet

I tried update-grub in a full root shell, too, but it still left 17 in place.  How do I force grub to use the new kernel?

---

### Post by benjo316 on 2008-09-18
> **andrewdied said:**
> How do I force grub to use the new kernel?There should be a menu with a list of kernels when you boot(you may have to press a key to see it).

If you can't find that, you could manually remove the option for the 2.6.24-17 kernel from '/boot/grub/menu.lst', but I wouldn't recommend that approach.

---

### Post by thomasaaron on 2008-09-18
sudo gedit /boot/grub/menu.lst

Then comment out the ones you don't want, save and reboot.

---

### Post by andrewdied on 2008-09-18
> **thomasaaron said:**
> sudo gedit /boot/grub/menu.lst

Then comment out the ones you don't want, save and reboot.

The issue is the update-grub script isn't adding the new kernel.  I have a few in /boot:

andrew@ubuntu:~$ ls /boot
abi-2.6.24-17-generic             initrd.img-2.6.24-18-generic.bak
abi-2.6.24-18-generic             initrd.img-2.6.24-19-generic
abi-2.6.24-19-generic             initrd.img-2.6.24-19-generic.bak
config-2.6.24-17-generic          memtest86+.bin
config-2.6.24-18-generic          System.map-2.6.24-17-generic
config-2.6.24-19-generic          System.map-2.6.24-18-generic
grub                              System.map-2.6.24-19-generic
initrd.img-2.6.24-17-generic      vmlinuz-2.6.24-17-generic
initrd.img-2.6.24-17-generic.bak  vmlinuz-2.6.24-18-generic
initrd.img-2.6.24-18-generic      vmlinuz-2.6.24-19-generic

But they're not in /boot/grub/menu.lst:

## ## End Default Options ##

title           Ubuntu 8.04, kernel 2.6.24-17-generic
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.24-17-generic root=UUID=6c814527-5db0-4129-b3bc-f41a16213147 ro quiet splash
initrd          /boot/initrd.img-2.6.24-17-generic
quiet

title           Ubuntu 8.04, kernel 2.6.24-17-generic (recovery mode)
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.24-17-generic root=UUID=6c814527-5db0-4129-b3bc-f41a16213147 ro single
initrd          /boot/initrd.img-2.6.24-17-generic

title           Ubuntu 8.04, memtest86+
root            (hd0,0)
kernel          /boot/memtest86+.bin
quiet


So, with grub, do I just add the -19 kernel above the -17 ones, using the same UUID and different file names, then reboot?

---

### Post by jdb on 2008-09-18
So, with grub, do I just add the -19 kernel above the -17 ones, using the same UUID and different file names, then reboot?[/QUOTE]

Yes, just change the 17s to 19s.
The first line labeled title is what is printed in the grub menu when you boot.
It isn't used for anything else so you can put whatever you want there.

Everything but the title line & the 19s should be the same as the entry for kernel 17.

jdb

---

### Post by gaussian on 2008-09-18
> **andrewdied said:**
> 
But they're not in /boot/grub/menu.lst:

## ## End Default Options ##

title           Ubuntu 8.04, kernel 2.6.24-17-generic
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.24-17-generic root=UUID=6c814527-5db0-4129-b3bc-f41a16213147 ro quiet splash
initrd          /boot/initrd.img-2.6.24-17-generic
quiet

title           Ubuntu 8.04, kernel 2.6.24-17-generic (recovery mode)
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.24-17-generic root=UUID=6c814527-5db0-4129-b3bc-f41a16213147 ro single
initrd          /boot/initrd.img-2.6.24-17-generic

title           Ubuntu 8.04, memtest86+
root            (hd0,0)
kernel          /boot/memtest86+.bin
quiet


So, with grub, do I just add the -19 kernel above the -17 ones, using the same UUID and different file names, then reboot?

Is this the whole content of your menu.lst? It should have commented directions above those lines that make the update-grub script work.

---

### Post by andrewdied on 2008-09-18
> **gaussian said:**
> Is this the whole content of your menu.lst? It should have commented directions above those lines that make the update-grub script work.

That's just the end.  Here's the whole thing:

```

andrew@ubuntu:~$ cat /boot/grub/menu.lst
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
# kopt=root=UUID=6c814527-5db0-4129-b3bc-f41a16213147 ro

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

title		Ubuntu 8.04, kernel 2.6.24-17-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-17-generic root=UUID=6c814527-5db0-4129-b3bc-f41a16213147 ro quiet splash
initrd		/boot/initrd.img-2.6.24-17-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-17-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-17-generic root=UUID=6c814527-5db0-4129-b3bc-f41a16213147 ro single
initrd		/boot/initrd.img-2.6.24-17-generic

title		Ubuntu 8.04, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

```

---

### Post by andrewdied on 2008-09-18
> **jdb said:**
> 

Yes, just change the 17s to 19s.
The first line labeled title is what is printed in the grub menu when you boot.
It isn't used for anything else so you can put whatever you want there.

Everything but the title line & the 19s should be the same as the entry for kernel 17.


I tried copying the 17 slice, changed 17 to 19, and left the 19 entry at the top.  While the laptop booted, there were some quick errors about not finding / being able to load the image.  The .img file is there, though.  I checked and it has the same line breaks as the working 17 version.  This is what I put in:

```

title		Ubuntu 8.04, kernel 2.6.24-19-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=6c814527-5db0-4129-b3bc-f41a16213147 ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

```

I've tried grepping various logs for "image", but can't find any specific errors.  Dmesg was unhelpful (at least to me).

---

### Post by gaussian on 2008-09-18
Based on your menu.lst I really don't understand why the new kernels are not being automatically added to menu.lst. One thing you could try is to reinstalling the kernel: e.g. 

```

sudo dpkg-reconfigure linux-image-2.6.24-19-generic

```

to see if that adds it to the menu.

---

### Post by andrewdied on 2008-09-18
> **gaussian said:**
> Based on your menu.lst I really don't understand why the new kernels are not being automatically added to menu.lst. One thing you could try is to reinstalling the kernel: e.g. 

```

sudo dpkg-reconfigure linux-image-2.6.24-19-generic

```

to see if that adds it to the menu.

Definitely worth a try.  Results:
andrew@ubuntu:~$ sudo dpkg-reconfigure linux-image-2.6.24-19-generic
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.24-19-generic
Not updating initrd symbolic links since we are being updated/reinstalled 
(2.6.24-19.41 was configured last, according to dpkg)
Not updating image symbolic links since we are being updated/reinstalled 
(2.6.24-19.41 was configured last, according to dpkg)
Running postinst hook script /sbin/update-grub.
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /boot/vmlinuz-2.6.24-19-generic
Found kernel: /boot/vmlinuz-2.6.24-18-generic
Found kernel: /boot/vmlinuz-2.6.24-17-generic
Found kernel: /boot/memtest86+.bin
Updating /boot/grub/menu.lst ... done

BREAK
Unfortunately, it didn't get added.  I've had issues with smime-keys for mutt not editing files, but that was a perl error in the package.  update-grub looks like a bash script.

---

### Post by jdb on 2008-09-18
> **andrewdied said:**
> I tried copying the 17 slice, changed 17 to 19, and left the 19 entry at the top.  While the laptop booted, there were some quick errors about not finding / being able to load the image.  The .img file is there, though.  I checked and it has the same line breaks as the working 17 version.  This is what I put in:

```

title		Ubuntu 8.04, kernel 2.6.24-19-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=6c814527-5db0-4129-b3bc-f41a16213147 ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

```

I've tried grepping various logs for "image", but can't find any specific errors.  Dmesg was unhelpful (at least to me).

Remove the word splash from the line that starts with root, copy down the exact error you get & post it.
The menu.lst entry looks correct.

jdb

---

### Post by gaussian on 2008-09-18
What I would recommend, at least as a test is to figure out why the update-grub does not generate new entries. Otherwise you are going to be in the same boat fairly soon (having to manually edit menu.lst)

I would:
> 
cd /boot/grub
mv menu.lst menu.lst.backup
update-grub


This should generate a fresh menu.lst. Then based on that adjust the "kopt=" line to get the right stuff there (and running update-grub every time you adjust something).

---

### Post by andrewdied on 2008-09-19
> **gaussian said:**
> What I would recommend, at least as a test is to figure out why the update-grub does not generate new entries. Otherwise you are going to be in the same boat fairly soon (having to manually edit menu.lst)

I would:


This should generate a fresh menu.lst. Then based on that adjust the "kopt=" line to get the right stuff there (and running update-grub every time you adjust something).

Good idea.  I tried that, and a new menu.lst was generated with the -18 and -19 kernels.  The -19 kernel setup looked just like what I had put in by hand, but still didn't boot right.  For grins I booted the -18 kernel, and that _does_ work.  Maybe the -19 kernel has an error in my install that causes update-grub to silently fail?

---

### Post by andrewdied on 2008-09-19
> **jdb said:**
> Remove the word splash from the line that starts with root, copy down the exact error you get & post it.
The menu.lst entry looks correct.

jdb

This is the error I got on the first terminal (Alt-F1 type):

Loading, please wait...
kinit: name_to_dev_t(/dev/disk/by_uuid/3d...(big UID).../ = sda2(8,2)
kinit: trying to resume from /dev/disk/(UID)
kinit: No resume image, doing normal boot...

I then get a popup saying that X isn't configured properly, with options to reboot or go into an 800x600 style.  Oddly, the -18 kernel boots correctly, so I think I have some error in my -19 kernel install.

---

### Post by gaussian on 2008-09-19
Is this a machine with Nvidia-card? I never had one, but this could maybe explain the 800x600 stuff. I would in that case try to boot to 800x600 mode and then do whatever is needed to install the Nvidia-drivers needed for this Kernel.

---

### Post by lazarouk on 2008-09-19
> **andrewdied said:**
> I tried to install VirtualBox 2.0.2, but it needs the kernel sources to compile a piece.  I didn't see kernel sources in package manager when I searched for "kernel".  Does anyone know what that package is called?  (Yeah, I'm sure there are variants.)  I'm runing 64 bit ubuntu 8.04 on a serval performance laptop.

Thanks for the help.

When I tried to install virtualBox I got a similar problem, but I just downloaded the correct deb from here...
[http://dlc.sun.com/virtualbox/vboxdownload.html](http://dlc.sun.com/virtualbox/vboxdownload.html)
be careful when selecting deb Linux 64-bit Platforms

---

### Post by thomasaaron on 2008-09-19
It's getting a little difficult to track progress on this issue.
But, I've seen a couple of instances lately of people with nvidia machines running proposed kernels and nvidia not working correctly.

What is the output of...
uname -r

Do you have an nvidia machine?

---

### Post by andrewdied on 2008-09-19
> **thomasaaron said:**
> It's getting a little difficult to track progress on this issue.
But, I've seen a couple of instances lately of people with nvidia machines running proposed kernels and nvidia not working correctly.

What is the output of...
uname -r

Do you have an nvidia machine?

uname -r gives me :  2.6.24-18-generic

Yes, I have an nvidia.  I bought the serval performance, which has the Graphics: nVidia 512 MB GeForce 8600M GT.

The original issue was when I tried to install virtualbox 2.0.2, the .deb couldn't compile the kernel module.  Then I discovered I was running the -17 kernel, instead of the -19 kernel.  Both were installed, but the -19 kernel wasn't in menu.lst.  When I hand-jammed the -19 kernel in menu.lst, boot complained about the X setup.  

I've just forced a reinstall of linux-generic and the -19 kernel, and am going to try a reboot now.

---

### Post by andrewdied on 2008-09-19
Nuts -- same issue with the -19 kernel.  The exact error I see after X fails to load is:

Ubuntu is running in low-graphics mode.

Your screen and graphics card could not be detected correctly.  To use higher resolutions, visual effects or multiple screens, you have to configure the display yourself.


I wonder if this is part of the nvidia issue mentioned earlier?  The -18 and -17 kernels both run ok.

---

### Post by andrewdied on 2008-09-19
> **thomasaaron said:**
> try...

sudo apt-get install linux-source-2.6.24
sudo /etc/init.d/vboxdrv setup

And back to virtualbox...

Running the -18 kernel, which I do have the sources for, vboxdrv setup does actually work!  

$ sudo /etc/init.d/vboxdrv setup
[sudo] password for andrew: 
 * Stopping VirtualBox kernel module                                             *  done.
 * Recompiling VirtualBox kernel module                                          *  done.
 * Starting VirtualBox kernel module                                             *  done.


I'm going to putter around and see why the -19 kernel isn't working, but I'm not sure I'll find anything.

---

