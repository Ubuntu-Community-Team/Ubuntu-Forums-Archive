---
title: "Unbelievable flexibilty"
date: 2007-06-07
forum: Testimonials &amp; Experiences
---

### Post by eentonig on 2007-06-07
My normal Ubuntu install is on an external USB HD connected to my companies laptop. Works perfect and has the benefit that:
- I keep my personal OS/config when it's time to swap Laptop.
- My professional HD isn't altered in any way because I run Linux (So Desktop support can't blame it on me when things break)



Recently, I bought an old Compaq 510 from work for practically no money. It came with XP installed, but won't be for long ;)

I didn't have the time to reinstall yet, but I did strip the remaining usefull parts from my older (broken) home desktop, install them in the Compaq and did some preliminary checks. That is, I ran the Live CD to see how HW support would turn out.

But then, I started to wonder. What would happen if I'd try to boot it from my USB HD with Ubuntu (Feisty Fawn) already installed? I figured it should work, but some reconfiguration would be required. 

I connected the USB HD, altered the BIOS boot sequence and gave it a go. And soon I was greeted by the ever friendly GDM interface. To give it a fair chance, I selected Failsafe Gnome. The DE launched and I could work as if nothing changed.

(PS. launching my Beryl enabled session didn't work, but that seems rather normal, as I didn't install any specific rendering engines for this graphics card.)


I would love to see Ms or Mac show me just that.

This basically means that anywhere I have a PC (Desktop or Laptop) that supports booting from USB, I can have my own PC. Awsome.

---

### Post by naelurec on 2007-06-07
I love the ability to pull a hard drive and boot on a different system. Most of the time, this has worked for me as well. I've done this with servers quite a bit -- run them on white box PCs and in the event one dies, I pull the hard drive, pop it in another box and boot up.

Total down time ends up being like 20 minutes (usually a FSCK is required if the server died w/o warning) and it gives me time to troubleshoot the hardware issue without worrying about availability.

The only time I have been able to do this with Windows was to have virtually identical hardware. I have never tried this with Mac OS X. 

I'll have to try the USB idea... sounds very cool. :-)

---

### Post by eentonig on 2007-06-07
It really is. It allowed me to have a normal, installed Ubuntu without ever touching the internal HD. 

And as an added benefit.

If I start the laptop without the USB HD attached, Windows boots up without grub.
If I start it with the USB HD attached, GRUB offers me the choice to select which OS to boot. (Allthough I did set the timeout to 1s, but you get the idea). To have this behavior, make sure to install grub on the USB. (which is a bit tricky. During install, it's hd1. And then on next boot, interrupt grub and adapt this to hd0). After boot, adapt menu.lst accordingly to avoid having to do this everytime.

---

### Post by seba-baires on 2007-06-07
Yes, this is amazing !!
I've also installed Ubuntu on an USB Hard disk, and it allows me to boot almost anything. I've even booted that drive inside a VMware Virtual machine and it works fine, with the only exception of having to recofigure the GUI as the X-server somehow doesn't find an appropiated driver for the virtual display.

---

### Post by cprofitt on 2007-06-07
Microsoft does that -- and will even redetect all of your hardware... though I would recommend at least running a sysprep before doing it.

A better way to do this would be to modify a "Live CD image" to go on your HD or Memory Stick -- the boot would take a bit longer, but you would not have hardware issues.

---

