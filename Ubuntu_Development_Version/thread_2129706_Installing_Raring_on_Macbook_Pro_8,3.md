---
title: "Installing Raring on Macbook Pro 8,3"
date: 2013-03-27
forum: Ubuntu Development Version
---

### Post by ta7p on 2013-03-27
Hi just invested in a 17" MBP before they disappear forever  as a desktop replacement. Want to use Ubuntu as my primary OS, and have  been trying to install 13.04. It installs fine off a dvd and boots up.  when I run the first upgrade the kernel updates to 3.8..4 from 3.8..2  and I get a black screen when trying to reboot.


  What information do I need to provide and anyone have any experience on how I might fix this? FWIW I've successfully updated my imac and macbook air to raring without any problems.


  Thanks

---

### Post by buzzingrobot on 2013-03-27
I'd look first at video driver problems.

Hold down the left shift key as you reboot and see if it brings up the Grub menu.  If it does, add "nomodeset" to the kernel boot line, continue the boot, and see if it that's successful. If it is, you will likely want to install a proprietary driver. 

I don't know if an 8,3 uses Nvidia or AMD, or if it also has an Intel video chip on the motherboard.  OS X can dynamically switch between the two GPU's as processing demands change.  Linux can't.  My 8,2 MacBook Pro has the Intel and an AMD.  I was never able to get Ubuntu to see the Intel.

Also, be aware that MacBooks have two different modes in which on OS can be installed.  One, EFI mode, is the standard OS X installation mode. The other is a BIOS compatibility mode Apple cooked up to facilitate installing Windows under Bootstrap. (Macs don't have a BIOS. Windows on x86 expects a BIOS.) The method used to install Linux can impact which GPU's are visible to the system. Pretty sure that Ubuntu installs in the BIOS compatibility mode, left to its own devices.

---

