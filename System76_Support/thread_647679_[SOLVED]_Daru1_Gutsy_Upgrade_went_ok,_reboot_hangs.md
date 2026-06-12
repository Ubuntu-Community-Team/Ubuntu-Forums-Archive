---
title: "[SOLVED] Daru1 Gutsy Upgrade went ok, reboot hangs to busybox"
date: 2007-12-22
forum: System76 Support
---

### Post by PanopticChaos on 2007-12-22
I just upgraded my Daru1 to Gutsy, the install seemed to go well - when the system rebooted it got to the Ubuntu splash screen and then hung.  

After a few seconds it goes to a busybox prompt. 

I'm really not sure what I can do from there any suggestions would be really appreciated...

---

### Post by PanopticChaos on 2007-12-23
My search-fu was weak, I found the solution to my issue in this thread:

[http://ubuntuforums.org/showthread.php?t=590442](http://ubuntuforums.org/showthread.php?t=590442)

Basically, GRUB was pointing at the wrong kernel (the old one) after the upgrade

---

