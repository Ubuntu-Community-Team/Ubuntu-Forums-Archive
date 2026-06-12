---
title: "Starling Update Broke Machine"
date: 2011-07-17
forum: System76 Support
---

### Post by wacole on 2011-07-17
The latest Ubuntu update 10.10 that I applied to my Starling notebook now prevents the machine from completing a boot.  [This update included a kernel update and required a reboot.  There may have been other updates applied as well, but I don't know what they are.]

After the BIOS load finishes, the cursor sits in the upper left corner of a blank screen just blinking.

Would appreciate clues as to how to get life back to normal.

Thanks very much,

Bill Cole

---

### Post by Tank Jr on 2011-07-17
I would try to boot from a live CD(USB drive if CD drive not available) and try to reinstall grub.
[http://knowledge76.com/index.php/Restore_Grub_Bootloader]("http://knowledge76.com/index.php/Restore_Grub_Bootloader")
This is the instructions from a live CD, and I am guessing (perhaps naively) that they will work in a USB drive too.
Good luck.

---

### Post by isantop on 2011-07-18
I concur, and those instructions will work flawlessly in a USB as well as a CD. You'll need to press F1 during the System76 logo page to enter the boot menu and select the USB drive.

---

### Post by noSelf on 2011-07-21
i'm having the same problem with my cute little starling. Sigh.

UPDATE: i had to google  boot error on my bootable flash drive (i used 10.10 to make a startup drive with 10.4 on it, and there's a bug and workaround), but otherwise the Master Boot Record repair process worked fine.

---

