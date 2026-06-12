---
title: "Booting to SD card using Legacy BIOS Mode"
date: 2023-03-14
forum: Ubuntu/Debian BASED
---

### Post by Crsh on 2023-03-14
I've been using an old laptop (2012) for Linux and booting from a USB drive, but my plan is to switch to an SD card. I'd prefer to leave the hard drive as-is. The problem is that the old BIOS doesn't support booting from SD. I thought that I could just install GRUB to the MBR and boot that way, but nothing I've tried has worked. GRUB4DOS, AIO Boot, and Ultimate Boot CD either don't work or can't find the SD card. I was able to select the hard drive as the location to install the bootloader during the Parrot setup, but when I boot, GRUB shows the grub rescue prompt and the unknown filesystem error. SD card partitions do not appear when running ls in grub rescue.

Would the Clover bootloader be a good alternative?

---

### Post by C.S.Cameron on 2023-03-14
Some older computers that will boot USB flash drives will not boot SD cards. 
I believe that a flash drive running Ubuntu will last longer than an SD card running Ubuntu.

---

