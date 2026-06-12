---
title: "how a comptuer ends up loading the os"
date: 2010-12-26
forum: The Cafe
---

### Post by flyingsliverfin on 2010-12-26
I've picked up that to get a computer to load, the BIOS loads the mbr, which points to a bootloader, which points to a FS kernel? I just want to confirm so i can understand at what point my USB drive isn't booting properly  :)

---

### Post by tgalati4 on 2010-12-26
There are a lot of things that can cause a USB drive not to boot.  Is this an external USB hard disk drive or a USB Flash drive (or thumb drive)?

Booting problems can often be resolved by booting from the CD using Ultimate Boot CD and using SuperGrub or any of the other boot-selector tools.

---

### Post by LowSky on 2010-12-26
it could also be that the BIOS  down't have USB booting set to allowable, or the boot priority is to boot other devices first, or that the motherboard is so old that it doesn't support booting from USB at all.

It could be the usb device wasn't set up correctly or it was damaged.


it could be any number of factors.

---

### Post by flyingsliverfin on 2010-12-26
its a thumb drive, it used to work with syslinux that loaded the first partition (incidentally, UBCD), that displays a menu that has an option to chainload the ubuntu partition.

it stopped working while i was repairing my brothers ubuntu and i accidentally installed grub on the wrong drive (oops!) which turned out to be my flash drive with the ubcd. I've managed to get it back to syslinux somehow, but now its just giving me a "boot: " (for the kernel) prompt, not the menu its supposed to... i'm stumped.
Maybe i should start a new thread for that

---

