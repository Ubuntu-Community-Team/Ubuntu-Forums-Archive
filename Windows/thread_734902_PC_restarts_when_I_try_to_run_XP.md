---
title: "PC restarts when I try to run XP"
date: 2008-03-25
forum: Windows
---

### Post by munch3 on 2008-03-25
I choose XP from GRUB loader and it just restarts.Gets to the booting image.Sometimes it asks me to run safe mode or run normally ec.but never worx.aslo restarts

---

### Post by Calash on 2008-03-25
Will it start if you pick Safe Mode?

It sounds like you are getting a BSOD, but it is set to auto-reboot so you never get to see the screen.  If you can get onto the system at all you can then shut off the auto reboot after the BSOD and hopefully get some real info from it.

Is this a new setup or has it been like this for a while and just stopped working?

---

### Post by munch3 on 2008-03-25
dunno never changed anything, also safe mode dont work

---

### Post by rickyjones on 2008-03-25
You're system is set to automatically reboot if the system crashes. The system is not booting into Windows because Windows is detecting some sort of critical error and is throwing that error which causes the reboot.

Try booting with the Windows XP CD. Enter the recovery console. Run a chkdsk on it and see if it finds any bad sectors or file fragments.

As a last resort you may need to perform a repair installation. Sounds like some boot files are not working correctly.

You might also wish to run a memory test.

-Richard

---

### Post by Battie on 2008-03-26
To see the BSOD, hit f8 after GRUB until you get to the Windows boot menu.  Choose the option to disable the automatic system restart.   Let us know the stop code.

It may or may not help, but it's quick thing to try.

---

