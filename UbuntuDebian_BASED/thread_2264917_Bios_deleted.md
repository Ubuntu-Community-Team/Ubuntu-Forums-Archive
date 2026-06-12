---
title: "Bios deleted"
date: 2015-02-11
forum: Ubuntu/Debian BASED
---

### Post by Eugen_Koslowski on 2015-02-11
hey people,

somehow i managed to delete my bios on my ideapad u410 during installing ubuntu. is there a possibility to install this [http://support.lenovo.com/us/en/products/laptops-and-netbooks/ideapad-u-series-laptops/ideapad-u410/downloads/DS101011](http://support.lenovo.com/us/en/products/laptops-and-netbooks/ideapad-u-series-laptops/ideapad-u410/downloads/DS101011) under ubuntu (elementary os)?

thanks

---

### Post by howefield on 2015-02-11
Thread moved to the "*Ubuntu/Debian BASED*" forum.

---

### Post by Habitual on 2015-02-11
> **Eugen_Koslowski said:**
> is there a possibility to install this [http://support.lenovo.com/us/en/products/laptops-and-netbooks/ideapad-u-series-laptops/ideapad-u410/downloads/DS101011](http://support.lenovo.com/us/en/products/laptops-and-netbooks/ideapad-u-series-laptops/ideapad-u410/downloads/DS101011) under ubuntu (elementary os)?Not unless you dual boot Windows 8 or 8.1 says that page.
**Supported Operating Systems**
Windows 8 (32-bit, 64-bit), Windows 8.1 (32-bit, 64-bit)

I highly doubt installing any Linux has deleted your BIOS, but I have seen issues where the informational messages from the BIOS have been suppressed. The options exist, but just aren't shown.
Can you not press Delete or F[1-12] during boot whether you "see" an option to do so or not?

---

### Post by buzzingrobot on 2015-02-11
> **Habitual said:**
> I highly doubt installing any Linux has deleted your BIOS...

Agreed. BIOS code is burned into the motherboard. It's firmware.

I've seen various howto's claiming to outline a way to update a BIOS under Linux.  I haven't tested any of them, and don't intend to.  A failed BIOS update can brick a machine, since the BIOS is the code that is responsible for initializing the components and peripherals and then passing control to the bootloader that boots the operating system.

If you can't do the update from Windows, I once did an update on a Linux machine by booting into FreeDOS.

Lenovo's README's about their BIOS update packages explain what's being updated.  Be sure you actually need the update.

(Also, if you're using Win8, is the machine actually powered down when you try to get to the BIOS configuration screen?  Win8's "fast reboot" gizmo doesn't actually power down all the way.)

---

### Post by SL0ltMJGyh on 2015-02-19
I found this for fixing the fast boot on Win8: [http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html](http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html) Hope this helps- I don't know much about windows but it should work...

---

