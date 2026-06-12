---
title: "Boot process"
date: 2012-11-12
forum: System76 Support
---

### Post by jpfle on 2012-11-12
I have a recent Ratel Performance. The BIOS is the default one shipped with the computer. I didn't change any settings.

My problem is that if I used a live CD and then I reboot the computer, the BIOS seems to try to boot only on the CD drive, so if the CD was removed, the boot process will end on a black screen with a blinking underscore, instead of booting from the internal hard disk. Here's an example:

Say there's a live CD on the CD drive. I start the computer. I see the system76 splash screen, then the computer boots from the live CD. I can reboot and the computer will always boot from the live CD. There's no problem for now.

The problem is if I remove the CD from the drive and then reboot the computer, I see the system76 splash screen, but then I see a black screen with a blinking underscore. I must press on the reset button in the front of the computer, but the boot process will always end on a black screen with a blinking underscore.

It's as if the BIOS remembers that the last successfully boot was from the live CD and tries the live CD (it will fail because there's no CD on the drive) without trying to boot from the internal hard disk.

To solve the problem, I must press F10 to display the boot menu and manually choose the internal hard disk in the menu, so the computer boots from the system installed on the internal hard disk. The next time I reboot the computer, it will be OK because it's as if the BIOS remembered that the last successfully boot was not from the CD drive, so it will boot from the internal hard disk.

How to solve this problem?

Thanks.

---

