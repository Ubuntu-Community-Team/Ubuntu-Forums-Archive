---
title: "Problems booting Live CD/USB Install Media"
date: 2011-05-28
forum: System76 Support
---

### Post by excalq on 2011-05-28
I'm wanting to do a fresh install of 11.04, but I can't get the system to boot a USB drive or a live CD. The GRUB menu of the USB drive and CD both come up fine, however after selecting an option, I just get a black screen with a non-blinking cursor. I suspect this has something to do with either GRUB or the BIOS, but I can't figure out a solution here.

Strangely a 32-bit 11.04 pressed CD will boot and run, but that doesn't really help me much. I've checked the md5sum of the 64-bit ISO I downloaded and it checks out. Also tried the alternate ISO, with the same result.

---

### Post by excalq on 2011-05-28
OK, more data but no closer to an answer. I can get the 32-bit CD to start booting, but it never finishes. The 64-bit server CD sometimes boots but not always. It might work to install with (although it has other issues like not detecting network interfaces.)

The 64-bit desktop CD will sometimes start to boot, but dies when when the splash screen is being displayed. ESC reveals various /dev/sr0 and other errors. 

The USB drive never ever gets beyond its GRUB menu. Unfortunately, System76's BIOS gives very few options, and juggling boot order seems the only relevant options in BIOS.

---

### Post by excalq on 2011-06-01
I think I'm going to extract the install CD ISO to my /home partition and use the HDD's GRUB to boot into that. Wish me luck...

---

### Post by isantop on 2011-06-01
It sounds like the burn was corrupt. Try burning the images again at the slowest speed supported by the burner, then try again.

---

