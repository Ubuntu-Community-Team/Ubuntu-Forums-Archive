---
title: "Clonezilla + Virtualbox"
date: 2008-08-22
forum: Virtualisation
---

### Post by KS1987 on 2008-08-22
Today I switched from Vista as my host OS to Ubuntu. There are some things I do need from my former OS, so I did a complete Vista back-up and used Clonezilla to create an image.

First I had some minor aches to enable usb support for Virtualbox, but then the real problem started. Neither of my back-up's want to restore. I used my Vista back-up and it said my hardware config changed too much and Vista couldn't be booted.

Clonezilla shows my Virtual hdd when I have to select my home folder where to restore from, but after selecting which image to restore, it only shows my external hdd (which has the image, that I selected for the home folder) on which I can restore. When I select this hdd, it shows obviously that the drive is busy.

But I was wondering how I can see my Virtual hdd when I need to select a home folder, but don't see it anymore when I want to put my image on it. Any help is much appreciated!

---

### Post by AClark on 2008-08-23
Because the hardware presented to the operating system installed in the virtual machine isn't real and is undoubtedly different than the actual hardware used by your Vista install even if you could restore your backup it wouldn't work.  

     Just as restoring to a different computer doesn't work unless the hardware is identical.

     There is a thread here: 
[http://ubuntuforums.org/showthread.php?t=769883&highlight=existing+windows+install](http://ubuntuforums.org/showthread.php?t=769883&highlight=existing+windows+install)

     It tells how to use an actual install (as in if you had a dual boot system with Ubuntu & XP) as your virtual machine without dual booting.

     I'm not suggesting that this is what you should do but reading the thread may help you to understand what is going on in virtualBox when you virtualize an operating system and what you are up against.

     The VirtualBox manual explains how the hardware is virtualized.

     If you think about it one of the main reasons many people use a virtual machine is to keep an operating system in a sandbox and unable to damage the host OS.  

     That can explain many of the problems trying to access the VM OS from the outside in a conventional manner.

     Someone else with more knowledge of VirtualBox may be able too give you more specific suggestions but since there haven't been any posts since yesterday I thought I would put in my 2 cents.

     Good luck & let us know how it goes.

---

