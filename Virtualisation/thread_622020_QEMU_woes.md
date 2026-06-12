---
title: "QEMU woes"
date: 2007-11-24
forum: Virtualisation
---

### Post by blippy on 2007-11-24
I wanted to play with various Linux and non-Linux distros under QEMU, Gutsy.

I type:
qemu-img create blah.img 3G

I put Zenwalk in the CD drive

Then I type:
qemu -boot d -cdrom /dev/cdrom -hda blah.img

When I try Zenwalk's autopartition, it says "No target disk selected". I don't think it's considering blah.img to be a disk. Other distros I've tried give problems, too. PC LinuxOS wont install. I even tried installing Ubuntu Gutsy. What happens is that it brings up BusyBox and the prompt
(initramfs)

What's going on?

---

### Post by ruibernardo on 2007-12-05
Hi blippy,

I had some problems with the QEMU package in Gutsy host too. It didn't boot my VM that where working in Feisty.

You can take a look at this: [https://bugs.launchpad.net/ubuntu/+source/qemu/+bug/144368](https://bugs.launchpad.net/ubuntu/+source/qemu/+bug/144368)
or maybe at this too: [https://bugs.launchpad.net/ubuntu/+source/bochs/+bug/123185](https://bugs.launchpad.net/ubuntu/+source/bochs/+bug/123185)
They are not the same bug, but they are related (VM don't boot) and the first one applied to my case.

Cheers.

---

### Post by bodhi.zazen on 2007-12-05
Try formatting the hard drive first, then installing.

I do this with fdisk.

---

### Post by blippy on 2007-12-08
I got bored, and installed virtualbox instead. I installed XP, and now I can run MS Money 2004. :guitar: It's about the only Windows app I really need. Oo, I'm so happy. I never had any luck with MS Money on Wine. To get me going, I ftp'd my old money file from Linux to XP, which is a bit of a cack-handed way of doing it, for sure. I'm going to see if I can get something more scientific sorted.

Virtualisation is fun!

Maybe Heron will fix the QEMU problems. We shall see.

---

### Post by houstonbofh on 2007-12-12
I have been dealing with this for a while and thought it was my hosed version of Gutsy.  I have 2 images, Win2K and FreeBSD, that work fine on several Feisty and Windows systems everywhere.  But not Gutsy...   Both hang midway in boot, about the time graphics come up.  I will be trying the workarounds and posting results here...

---

### Post by houstonbofh on 2008-01-06
It appears to be the VGA bios...  If you get the bochsbios from Hardy, it works.  It does, however, "Find" new hardware in Windows after this.  With bochsbios_2.3.5-1ubuntu1_all.deb I am successful in both Windows and FreeBSD with KDE.

---

