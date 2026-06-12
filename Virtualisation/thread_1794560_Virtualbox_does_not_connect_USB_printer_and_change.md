---
title: "Virtualbox does not connect USB printer and changes VirtualBox.xml permissions"
date: 2011-07-01
forum: Virtualisation
---

### Post by wkoell on 2011-07-01
Hi!

On Ubuntu machine i have to run an application which works only in Win. So user who is logged in Ubuntu should once in a day launch WinXP in Virtualbox. For that i linked .Virtualbox-directory from my home to every other user homes. And got it working pretty fine. No worries.

Now I upgraded Ubuntu from 8.04 to 10.10 and also Virtualbox to 4.0. After that after WinXP launching you must enable USB-printer under Devices/USB-devices/ and so every time. Ho to make it permanent?

And much bigger problem. VirtualBox.xml and win.xml (vm settings) have permissions 666 (so every user could read write it), but after running under particular user Virtualbox changes them to 600 and chowns them to this last user, too. So, for every time, new user has to launch WinXP, there is need to change permissions again to 666. How could i avoid it?

TIA!

---

### Post by mister_p_1998 on 2011-07-01
Had this problem with ALL usb devices in VirtualBox,All USB devices were greyed out & I couldnt right-button and select them, I temporarily fixed it by running VirtualBox as root. I noticed the latest update of  VirtualBox (4.0.10  revision 72479) fixes this and USB now works without resortin to running as root. Im running it now in Ubuntu 10.04.

---

