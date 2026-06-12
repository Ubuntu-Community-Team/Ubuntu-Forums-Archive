---
title: "what is the difference between bios and chipset drivers?"
date: 2010-08-03
forum: The Cafe
---

### Post by nerdy_kid on 2010-08-03
so this has always nagged me, what is the difference between flashing the BIOS and installing a chipset driver?  (see chipset drivers for windows computers all the time)

sorry for what is no doubt a very stupid question...

---

### Post by pricetech on 2010-08-03
Actually it's a perfectly legitimate question.

When you flash the BIOS, you update the firmware, which is the code the BIOS uses to find your basic hardware, like your hard drive, your optical drive, your keyboard and mouse, etc.  Updating the firmware usually adds some functionality to your BIOS, though you often don't see it in the menus.

The Chipset Driver, on the other hand, is like any driver.  It allows your operating system to better address the motherboard's chipset, which includes high level functionality of USB ports, parallel ports, and so on.  Best practice is to install the chipset driver first so your OS can better utilize the drivers for the other hardware.

I hope that helps.

---

### Post by nerdy_kid on 2010-08-03
> **pricetech said:**
> Actually it's a perfectly legitimate question.

When you flash the BIOS, you update the firmware, which is the code the BIOS uses to find your basic hardware, like your hard drive, your optical drive, your keyboard and mouse, etc.  Updating the firmware usually adds some functionality to your BIOS, though you often don't see it in the menus.

The Chipset Driver, on the other hand, is like any driver.  It allows your operating system to better address the motherboard's chipset, which includes high level functionality of USB ports, parallel ports, and so on.  Best practice is to install the chipset driver first so your OS can better utilize the drivers for the other hardware.

I hope that helps.

helped a bunch, thanks :)

---

### Post by Tibuda on 2010-08-03
You don't need a BIOS when you are using Linux, because GRUB replaces it during the boot. That's what I heard in the forums.

---

### Post by KiwiNZ on 2010-08-03
> **danielrmt said:**
> You don't need a BIOS when you are using Linux, because GRUB replaces it during the boot. That's what I heard in the forums.

Hrmmmm well , we will ignore this .

---

### Post by KiwiNZ on 2010-08-03
You may find these links a useful read.

[http://en.wikipedia.org/wiki/BIOS](http://en.wikipedia.org/wiki/BIOS)

[http://en.wikipedia.org/wiki/Chipset](http://en.wikipedia.org/wiki/Chipset)

---

### Post by Old_Grey_Wolf on 2010-08-03
> **danielrmt said:**
> You don't need a BIOS when you are using Linux, because GRUB replaces it during the boot. That's what I heard in the forums.

> **KiwiNZ said:**
> Hrmmmm well , we will ignore this .

I was struggling with a tactful way of replying to that post myself. Like asking the poster to boot the computer and notice if it said "Press [some key] for Setup", or "Press [some key] for Temporary Boot Order", etc. If it did then there was indeed a BIOS present despite what he heard. 

However, I decided to let someone else have a go at it.

---

