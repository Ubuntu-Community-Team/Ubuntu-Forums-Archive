---
title: "VMware Server + Usb 2.0 (Zune)"
date: 2008-08-25
forum: Virtualisation
---

### Post by Fallz on 2008-08-25
I think I posted this in the wrong place last time..I hope this is more correct.

In theory, I was thinking since VMware server has USB 2.0 support, it would also support the zune over usb 2.0. As you all know on the Stable version of VMware server, if you don't unload your USB 2.0 drivers you'll get a BSOD in windows.

So, I install the new VMware server 2, plug in the Zune - still BSOD. Works with usb 1.1, but it's really, really, really slow. Is this even worth my while?

Also..I already unloaded the USB 2.0 drivers..how do I put those back on afterwards..if anyone knows.

---

### Post by fjgaude on 2008-08-25
AFAIK, vmware server doesn't support USB 2.0 yet. I think that VirtualBox does. You might give that a try.

---

### Post by Fallz on 2008-08-25
Vmware server 2 beta is supposed to
[http://www.vmware.com/beta/server/](http://www.vmware.com/beta/server/)

---

### Post by fjgaude on 2008-08-26
It seems you load drivers while in Windows, huh? Yes! I don't know anything about Zune. Maybe someone else can help.

---

### Post by Fallz on 2008-08-27
I dunno, I wasn't getting a whole lot of feedback so I've just switched to virtual box. the only problem now is I've done too many windows re-installs with my computer and it's not accepting my product key.

---

### Post by maphilli14 on 2008-09-01
I've found USB 2.0 on VMWare-Server 2.0 RC2 slower than I think USB 2.0 should be.  I've got an iTouch that works syncing to iTunes on a WinXP guest with a Hardy host on my Lenovo T61 (isn't virtualization great?!).
I've also tooled around with some DSLR control/capture software (MaxDSLR) and I feel it's slower than native USB 2.0, but I could be wrong.

FWIW, I've never gotten my iTouch to work with VirtualBox 1.5 or 1.6 and have moved to VMWare as a result.

Mike

---

### Post by Fallz on 2008-09-01
currently I still haven't gotten virtualbox up yet, but that's window's product key problems. When it was working (But not validated) the Zune was being recognized and XP wasn't BSOD right away - but I also didn't have the zune software up.

As for Vmware server 2, I still haven't gotten usb 2 to work correctly (as in, it still BSOD) That's a bummer..

---

### Post by deputy on 2008-12-15
I was able to get a Zune 80gb working using Vmware Server 2.0. Under vmware I installed XP with SP2, and downloaded the latest Zune software. I connected my Zune, enabled it in virtual XP and the Zune software picked it up. I am able to sync music, pictures, videos. I can connect to Marketplace and download stuff. Basically everything works as if it were on a real XP machine. The reason I used Vmware Server 2.0 is because it supports USB 2.0. I might also add that I'm using 64 bit version of Vmware, but that should not matter. The latest version of Vmware seems to take care of the USB 2.0 issues and BSOD. I'm finally able to get rid of Vista!!!!!!!

---

