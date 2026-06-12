---
title: "cloning a hard disk"
date: 2005-11-19
forum: The Cafe
---

### Post by abandoned_hussam on 2005-11-19
What exactly would happen if I clone the hard disk on my P3 machine at home to another hard disk and place the other hard disk in a P4 machine at office?
How would kubuntu act? will it auto detect the new hardware? 
The only similar thing between the two machines is that they have the same Nvidia VGA card model and same monitor model.
Just a stupid question :)

---

### Post by magicfab on 2005-11-22
Don't know 'til you try it. I would say the worse would be to loose graphic display, but you say you have the same hardware. I'd say at least change the video driver to vesa generic so you're sure you'll boot in graphic mode.

Also look at /boot/grub/menu.lst for kernel boot parameters that look machine-specific.

By all means, report back here :)

---

### Post by wrtrdood on 2005-11-22
One thing GNU/Linux is good at, especially the way the default (K)Ubuntu kernel is built, is moving around on hardware.  Modules are defined that handle just about anythng you throw at it.  I've moved drives between machines of completely different hardware before (several times) and had little trouble booting and using the system wherever it went.  Based on that, I'd have to say that the OS will hardly notice the difference...

---

### Post by Mr. Electric Wizard on 2005-11-22
Definatly try it.
I have been wondering this for a while now...

---

### Post by gord on 2005-11-22
when your computer boots up it has to learn your hardware all over again, thats why if you take out your graphics card and replace it with another, it will detect it and carry on as normal (provided it knows what the card is in the first place). same for motherboard, processor, sound card... etc, etc.

---

