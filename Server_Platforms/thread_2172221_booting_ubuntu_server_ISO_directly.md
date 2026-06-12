---
title: "booting ubuntu server ISO directly?"
date: 2013-09-03
forum: Server Platforms
---

### Post by JdPBFKT on 2013-09-03
I've mainly been trying to do this by pxe using the latest pxelinux with memdisk.

I've spent I don't know how many hours/weeks/months trying to figure if this was possible. It's extremely hard to find information on this because all the search results seem to point to doing this from the a regular ubunu desktop sort of ISO rather than the server ISO.

I've been mainly trying with server 12.04 LTS 32/64-bit. So to re-iterate I'm not trying to boot from a ubuntu desktop ISO that includes x-windows and a "live CD" environment, only from the server ISO.

I found [this thread over on reboot.pro]("http://reboot.pro/topic/17410-ask-install-ubuntu-from-usb-using-grub4dos/") from 2012 that describes exactly the issue I was having: it gets so far and prompts to insert a CD. The thread then goes on to point out some ISO strangeness that happens during the bootup.

Since the thread over on reboot is kind of old (ok a year as I write this) I figured I would ask the community if any thing had changed or anybody knew specifically how to make this work with any boot loader? I've tried grub4dos as well as syslinux on a flash drive with same results.

Also, sorry about the user name, I don't seem to be able to change it (and was never given the option to specify).

---

### Post by oldfred on 2013-09-03
I filed a bug on the alternative installer several versions ago. I also had issue with server.
 Grub does not loopmount alternate
[https://bugs.launchpad.net/ubuntu/+source/debian-installer/+bug/914926](https://bugs.launchpad.net/ubuntu/+source/debian-installer/+bug/914926)

Someone posted this but i never tried it:


 With Debian Installer(Which is text/ncurses based) ,it asks to Mount Ubuntu CD when booted from hard disk iso.What I did was ,to symlink(symbolic Linking) Lucid Alternate cd ISO to /dev/sr0(Which is the device file for dvd drive) .Then If I ask debian-installer to retry to mount cd ,it got mounted!
Code:

   ln -sf /yourubuntuisodirectory/ubuntu.iso /dev/sr0

I saw some other posts where they go to the terminal cntl-alt-f1 in the middle and change mount point to match.

---

