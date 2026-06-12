---
title: "Will grub allowing Windows booting from an M.2 drive?"
date: 2021-03-30
forum: Windows
---

### Post by sinbad196 on 2021-03-30
Hello.

I'm completely unfamiliar with GRUB, but what I'm trying to do is boot Windows 10 from an M.2 drive that is connected to my computer with a PCIe to M.2 adapter. I have successfully cloned the contents of my SATA SSD to the M.2, but my BIOS does not support booting to M.2. Will GRUB solves this problem? Is there anything I should know before proceeding with the GRUB if it will allow the Windows boot off the M.2?

Thank you.

---

### Post by CelticWarrior on 2021-03-30
Welcome.

> [COLOR=#000000]Will GRUB solves this problem?[/COLOR]
No.
Grub isn't a Windows bootloader. It merely chainloads to the Windows bootloader manager in a dual-boot scenario.

If your system is UEFI - extremely likely if not something from ~10 years ago - then you need to learn about and understand how UEFI boots, its own requirements and the OS (Windows) requirements for UEFI booting. Namely you need to understand and account for the location of the ESP (EFI System Partition) so its drive is set as the first priority in the drive boot order in UEFI settings and then the OS boot order, a separated setting but dependent on the first one, obviously, if multi-booting. Generally it doesn't matter where the OSes are installed (except Windows can't be installed in external drives) as long as the system can boot from the drive where the ESP resides. 

It's not clear from your description whether or not you still have the SATA drive nor how Windows was installed originally (proper UEFI mode or Legacy/CSM/"BIOS" mode) nor the destination drive's partitioning table which must be, for Windows, strictly GPT for UEFI mode and MBR ("msdos") for Legacy.

Other then this very generic and broad strokes I'm afraid there isn't much more we can help you with but there are thousands of online resources for Windows out there. Good luck in your endeavors.

---

### Post by sinbad196 on 2021-03-30
Thanks for the reply. 

Ok, so Grub is out of the question.

The computer was custom built 2 years ago. I did find a potential way of doing it with a BIOS flash that someone came up with, but I'm not going to take that risk. I'll just stick with using my SATA SSD:D

---

