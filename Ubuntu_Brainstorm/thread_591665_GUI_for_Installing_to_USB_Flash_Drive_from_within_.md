---
title: "GUI for Installing to USB Flash Drive from within Ubuntu"
date: 2007-10-25
forum: Ubuntu Brainstorm
---

### Post by scottfinman on 2007-10-25
As discussed here:

[http://www.pendrivelinux.com/2007/09/28/usb-ubuntu-710-gutsy-gibbon-install/](http://www.pendrivelinux.com/2007/09/28/usb-ubuntu-710-gutsy-gibbon-install/)

And similar to the way it's done on Puppy Linux, for those familiar with that setup.

---

### Post by snickers295 on 2007-10-25
i don't see why people want Linux on a pen drive.
its flash memory, so a few thousand read and writes later your pen drive is dead.

---

### Post by scottfinman on 2007-10-25
Primarily for portability reasons - one can take their entire operating system with them, plug it in, reboot, and they're good to go. Better yet, one can even run the operating system from within an installed Windows or Linux session with QEMU:

[http://fabrice.bellard.free.fr/qemu/](http://fabrice.bellard.free.fr/qemu/)

Damn Small Linux is the best out there that I know of that takes advantage of QEMU:

[http://damnsmalllinux.org/](http://damnsmalllinux.org/)

---

### Post by snickers295 on 2007-10-26
what i would do is get a livecd and put the system on the CD and use the pen drive for memory.

---

### Post by Twintop on 2007-10-26
> **snickers295 said:**
> i don't see why people want Linux on a pen drive.
its flash memory, so a few thousand read and writes later your pen drive is dead.

This is an old and untrue myth that keeps being passed around. When flash memory first came out, each sector had about 10,000 read/write cycles on it before it went bad. Now though, solid state drives are much more durable. Check out [this article]("http://www.storagesearch.com/ssdmyths-endurance.html") about this topic. In short: a 64GB solid state drive would take **51 years** to use its maximum read/write cycles if in constant use.

---

### Post by The Jinx on 2007-10-26
is this a fully operating Ubuntu OS on the flash drive or is it like an image where one can install the Ubuntu from. What im basically asking is it like a "Live USB" version of the Live CD or does it mean that you fully install the OS on the flash drive itself and can do all your tweaks on it

---

### Post by smartboyathome on 2007-10-26
> **The Jinx said:**
> is this a fully operating Ubuntu OS on the flash drive or is it like an image where one can install the Ubuntu from. What im basically asking is it like a "Live USB" version of the Live CD or does it mean that you fully install the OS on the flash drive itself and can do all your tweaks on it

It is basically a live cd image with persistance enabled and a partition enabled. So no changes are saved until you log out, but it runs faster than a live cd. I have one of these on a USB drive, and it helps a lot when you have emergencies and don't have a cd.

---

### Post by snickers295 on 2007-10-26
i said i didn't like it, not that i don't know how to do it.
what i do is download a livecd iso and extract it to my pendrive, then i change the name of isolinux.cfg to syslinux.cfg and then download syslinux and go to that directory and type ./syslinux /dev/sdb1 and then unmount it and reboot and there, i have a bootable pendrive.
i'm trying out SLAX on it and it works pretty good.

---

### Post by belovedmonster on 2008-02-01
A GUI for installing a live persistent to USB is number one on my wish list. Please make it happen!

---

### Post by smartboyathome on 2008-02-01
Like I said in the other thread, I am trying to put together a guide for this. :)

---

### Post by belovedmonster on 2008-02-01
Wooo! If you are ever in England I'll buy you a beer.

---

### Post by smartboyathome on 2008-02-01
It is done, see [here]("http://ubuntuforums.org/showthread.php?t=647587").

---

### Post by that1guyty on 2008-02-05
I tried using a similar tutorial for using a similar tutorial, but now my usb stick is useless.  Don't ask me what happened, because i honestly can't tell you. but i do know that neither ubuntu or XP can mount the USB stick.  ubuntu sees it, and when i click on the icon, it says, "unable to mount flash drive.  There may be no media on the drive".  any help?  
     I don't even mind just wiping the whole thing and using it as it was intended for: Storage.  thanks in advance!

-ty-

---

### Post by smartboyathome on 2008-02-05
Try installing GParted from the repos and checking it out using that. I have a feeling it may be a corrupted partition.

---

