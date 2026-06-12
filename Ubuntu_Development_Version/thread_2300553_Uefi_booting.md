---
title: "Uefi booting"
date: 2015-10-26
forum: Ubuntu Development Version
---

### Post by Chanath on 2015-10-26
I don't have a uefi system, but one of my pals has. Is Wily live iso bootable in an uefi system?  I'd like to show how Ubuntu works. I have to know, if the live iso would boot and it could be installed in a uefi system. Has anyone an idea?

---

### Post by oldfred on 2015-10-26
Since version 12.04.2 Ubuntu has been UEFI bootable with secure boot on.
So yes with some possible issues. Some vendors are more friendly to letting another system boot. And some very new hard ware needs the very newest Ubuntu version and even then may need more updates to software not yet in the standard distribution.

What brand/model system. What are specs?

See link in my signature for lots more info:

---

### Post by Chanath on 2015-10-26
Thanks!:D

---

### Post by jerrylamos on 2015-10-27
I've two laptops and a desktop, all with Win 10 in the internal drive.

The two laptops boot Ubuntu fine from external usb drives.  Different boot keyboard sequence.

The Desktop has a miserable time booting ubuntu complains about unauthorized bios modification attempt, much beeping and F2 to proceed.
After it's up runs fine.  Note it's a recon 3 ghz dual processor Lenovo with bios written a few months after Microsoft started with their "secure boot" changes.

Note was no problem with Win 7.  The grief started with Win 10.  So far it's bearable.  I could pop open the case and unplug the internal drive, however I do update Win 10 from time to time.  Always reminds me why I'm using Ubuntu.  My wife uses Win 10 and XP supporting a couple websites with software only available on Microsoft.

Oh, I'm usually using whatever is in Ubuntu development.  This one boots Wily or Xenial or LTS on different partitions, the others are on Wily and have been since the first development code dribbled out.

Of course in Development bugs do occur.  Crash.  SNAFU.

---

### Post by fjgaude on 2015-10-27
> **Chanath said:**
> I don't have a uefi system, but one of my pals has. Is Wily live iso bootable in an uefi system?  I'd like to show how Ubuntu works. I have to know, if the live iso would boot and it could be installed in a uefi system. Has anyone an idea?

I've had UEFI motherboards for about three years... It's easy to make a USB drive putting Ubuntu on it which has a EFI partition. I have three versions running on Z87, Z97 MBs without issue. I don't have any Windows to boot, only on VirtualBox.

A UEFI installed Ubuntu will boot about twice as fast as a BIOS installed one. Both 15.10 and 16.04 are working fine UEFI installed.

Now, the issue: if you try to reuse a USB drive that has EFI on it you may have trouble. The clean way I've found to do it is to use **mkusb**, as it will erase the UFI and then it uses **dd** to copy over the .iso file.

Have fun!

---

