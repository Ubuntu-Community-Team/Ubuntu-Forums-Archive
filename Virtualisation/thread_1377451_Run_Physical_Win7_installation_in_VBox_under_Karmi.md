---
title: "Run Physical Win7 installation in VBox under Karmic"
date: 2010-01-10
forum: Virtualisation
---

### Post by Raditude on 2010-01-10
I tried this tutorial, but it doesn't work for Karmic Koala: [http://ubuntuforums.org/showthread.php?t=984437](http://ubuntuforums.org/showthread.php?t=984437)

My computer came preinstalled with Windows 7 64bit.

I installed Ubuntu 9.10 Karmic Koala from the installer inside Windows, on the same partition.


My 320GB hard drive has 3 partitions:
---->System Reserved (105 MB)
---->PQService (13 GB)
---->Acer (the partition that has Windows 7 and Ubuntu installed) (307GB)


It currently dual boots with two boot menus:
----> First menu: Choose between Windows 7 and Ubuntu, with Windows 7 as default. If you choose Ubuntu, you're taken to the second boot menu.
----> Second menu: GNU GRUB version 1.97~beta4
---------->Ubuntu Linux 2.6.31-14-generic
               ---------->Ubuntu Linux 2.6.31-14-generic (recovery mode)
               ---------->Windows Vista (loader) (on /dev/sda1)
               ---------->Windows 7 (loader) (on /dev/sda2)
               ---------->Windows 7 (loader) (on /dev/sda2)

Vista isn't installed on my computer, the Vista loader takes you to a place to restore the computer to factory defaults

I am using Sun VirtualBox 3.1.2.

I want to run my native Windows 7 as a guest inside Ubuntu.

I want the computer to startup directly with Ubuntu, instead of a Boot Menu. I don't need to boot to Windows 7 Natively.

(I am very new to Linux, especially Ubuntu)

---

### Post by fouadatmeh on 2010-01-10
Hello,

I don't think the tutorial would work since you seem to have installed linux using wubi (started the installation from within windows)..

If you have the original win7 DVD, I would say the easiest way to go is to do a clean Ubuntu installation on the harddisk (installing from boot cd, not from inside windows), and then install virtualbox and then install windows 7 inside it...

the other way is to also install linux in a separate partition using the live cd and boot win7 from its partition using virtualbox.

Or maybe someone out there might know an easier way to do it :)

Hope that helps..

---

### Post by Raditude on 2010-01-10
I just got this computer, and it didn't come with a Windows 7 disc.

I used Wubi to install Linux, because I couldn't figure out how to add a partition. I almost formatted my whole harddrive in the process.

I can't figure out how to partition the hard drive in Linux.

I'm open for copying my current Windows 7 installation to a Disk Image, but I don't know how to do that, or if it's even possible.

I have a blank external USB Hard Drive at my disposal, if I could use that to copy/transfer the Windows 7 OS into a disk image.

---

### Post by fouadatmeh on 2010-01-11
Hello,
This is a really tough one :).. 
The way I would go with it is like this:
- Sysprep the current windows 7 installation (which will enable you to re-install it with all installed applications inside it once the computer reboots, much like the restore on a new laptop), a quick googling gave me this site:
 [http://blog.brianleejackson.com/sysprep-a-windows-7-machine-start-to-finish](http://blog.brianleejackson.com/sysprep-a-windows-7-machine-start-to-finish)
- when the computer shuts down, boot from a utility cd and make an image from the windows partition with a utility such as norton ghost and put the image on the USB drive (or any other of your choice; I think there is a cd called hiren boot cd that has several such utilities, or if u want to use ubuntu live cd, you might use partimage)
- now start ubuntu from the live cd ,format the windows partition and do a clean install of ubuntu in it; (you can use the GParted utility if you want to make or resize partitions).
- install virtualbox inside ubuntu, make a virtual machine with its drive as big as your old windows partition partition so you would be able to restore the image inside it.. don't worry, vbox will not reserve all the space at once, it will only use what it needs.
- start the virtual machine and mount the USB drive inside it, boot from whatever cd you used to create the image and restore the image from the USB drive to the virtual drive. 

Hope the above works for u [I haven't tried partimage, nor the sysprep for win7 (I tried sysprep for XP once and it worked Great, but I just remembered that it will remove all user profiles on windows)]
so be extra careful.. 

** a very easy exit is to use 7 as host and ubuntu as guest if that can work for you..

---

### Post by Raditude on 2010-01-11
> **fouadatmeh said:**
> Hello,
This is a really tough one :).. 
The way I would go with it is like this:
- Sysprep the current windows 7 installation (which will enable you to re-install it with all installed applications inside it once the computer reboots, much like the restore on a new laptop), a quick googling gave me this site:
 [http://blog.brianleejackson.com/sysprep-a-windows-7-machine-start-to-finish](http://blog.brianleejackson.com/sysprep-a-windows-7-machine-start-to-finish)
- when the computer shuts down, boot from a utility cd and make an image from the windows partition with a utility such as norton ghost and put the image on the USB drive (or any other of your choice; I think there is a cd called hiren boot cd that has several such utilities, or if u want to use ubuntu live cd, you might use partimage)
- now start ubuntu from the live cd ,format the windows partition and do a clean install of ubuntu in it; (you can use the GParted utility if you want to make or resize partitions).
- install virtualbox inside ubuntu, make a virtual machine with its drive as big as your old windows partition partition so you would be able to restore the image inside it.. don't worry, vbox will not reserve all the space at once, it will only use what it needs.
- start the virtual machine and mount the USB drive inside it, boot from whatever cd you used to create the image and restore the image from the USB drive to the virtual drive. 

Hope the above works for u [I haven't tried partimage, nor the sysprep for win7 (I tried sysprep for XP once and it worked Great, but I just remembered that it will remove all user profiles on windows)]
so be extra careful.. 

** a very easy exit is to use 7 as host and ubuntu as guest if that can work for you..

This is the idea I kind of what I thought about doing, but I didn't know the exact way to go about it.

I haven't done much with my Windows 7 installation, only deleted some programs that came with the computer.

My Ubuntu has a lot of customization done to it though, mainly with Compiz. I want to use Ubuntu as my host OS, so I can have multiple OS's in their own workspaces, and switch among them with Compiz. Is there any way I can backup the settings I have in Ubuntu to transfer it over to the new installation?

I'll give this a try.

EDIT: I just looked at that link. It needs a Windows 7 Disc. My computer didn't come with one. Is there a way to make one? I'm sure I could "acquire" one though, but I don't know how the activation would work.

---

