---
title: "Dual Monitors, can I make this work?"
date: 2008-02-14
forum: The Cafe
---

### Post by sunexplodes on 2008-02-14
Recently inherited an older PC, which contains an ATI PCI graphics card. I'm currently using a nVidia AGP card. Any way to get 2 monitors rolling, or am I out of luck?

---

### Post by Crooksey on 2008-02-14
Possibly, you would have to compile the kernel with both intel and ATI support.

Then boot into your system with just your monitor plugged into your nvidia card, run "nviida-xconfg", and then save your xorg.conf.

Now reboot with the monitor pligged into the ATI card, run the aticonfig to generate the xorg.conf, then save the xorg.conf file.

Now reboot back into the system with your monitor plugged into the nvidia card, setup xorg.conf to work pefectly.

Now get your ati xorg.conf and copy the device section from the ATI section, into the new xorg.conf. That will make both videocards supported. Now use Xinerama to setup dual displays, you wont be able to use any driver related DualHead system, but Xinerma may work, it may take quite a bit of hacking, but with a lot of work it could work out fine.

You might not need to reboot with monitors plugged into diffrent cards, just might make it easier.

Good Luck!

---

### Post by sunexplodes on 2008-02-14
Jeez louise. Not as easy as I would have hoped, and hardly worth the trouble for my intended uses. Thanks for the info, but it looks like I might wait until I get a new motherboard/matching dual cards.

---

### Post by Jimmey on 2008-02-14
Most newer graphics cards have two video outputs, a VGA and a DVI - I'm not sure, but I don't think you need two graphics cards to have dual monitors. If one of yours cards has both of these, just find a DVI to VGA adapter, and use that.

---

### Post by Crooksey on 2008-02-14
One video card is more than adequate for dual display, works fine.

---

