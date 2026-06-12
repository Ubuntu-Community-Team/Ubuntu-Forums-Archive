---
title: "Ratel/8.10 boot from usb stick"
date: 2010-06-16
forum: System76 Support
---

### Post by BuggyFunBunny on 2010-06-16
I've got to upgrade, and 10.04 seems the best bet.  Found that booting from "Live CD" on usb stick is supposed to work.  I used usb-creator to move the .iso to the stick.  Reset the two lines in BIOS:  boot from USB, boot from USB first.  But I still get the HDD 8.10.  Grub does come up, so it is not seeing the stick, I guess.  Any other setting in need of setting?

---

### Post by C.S.Cameron on 2010-06-16
Depending on the type of BIOS sometimes the USB stick needs to be selected as the first HDD.

---

### Post by BuggyFunBunny on 2010-06-16
> **C.S.Cameron said:**
> Depending on the type of BIOS sometimes the USB stick needs to be selected as the first HDD.

Tried that (after I posted), and said the stick had no operating system.  I didn't run a format on the stick, but didn't think that was an issue, since usb-creator said it did its thing, and the files are there.  Does a linux format have to be done?

---

### Post by BuggyFunBunny on 2010-06-16
answer:  need to run  install-mbr /dev/sdX

---

