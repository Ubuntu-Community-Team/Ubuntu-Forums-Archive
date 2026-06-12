---
title: "Adding Kali to Ubuntu  makes boot process as well as resume from standby SLOW"
date: 2015-05-17
forum: Ubuntu/Debian BASED
---

### Post by bwanaaa on 2015-05-17
Ubuntu 14.04 on a Lenovo idea pad runs fine. I had the need to run Kali linux so I installed it. Then on reboot, I saw I had the GRUB boot manager, not GRUB2 as before. I muddled around with an app called grub customizer to reset the boot order so that ubuntu was first. I updated the system as well (and it did download a grub update)

Now I have my GRUB2 back. But the boot process takes a long time. It starts to boot (I get some screen glow like the linux is trying to show a black screen) then the screen flickers to totally off and then it's back to the black screen, then I get the MATE screen for login and then I am at the desktop.

When I resume from standby I have another weird behavior. First I get a screen with a few lines of text that flashes, then I get a dialog,I enter my pw, then the screen blinks and I get a different dialog to enter the pw.

Both of these behaviors are new since I confused the boot loader.

How to troubleshoot? I think I need to turn on verbose mode but don't really know WHICH verbose mode to use. Help?

---

