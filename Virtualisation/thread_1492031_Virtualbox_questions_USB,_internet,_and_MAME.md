---
title: "Virtualbox questions: USB, internet, and MAME"
date: 2010-05-24
forum: Virtualisation
---

### Post by inverseroom on 2010-05-24
Hope you guys can help me--I've been troubleshooting this for days.

I'm running 32-bit Lucid 10.4 on an HP dv3 laptop connected wirelessly to the internet.  I recently installed Virtualbox PUEL, the latest version, and am successfully running XP pro in my virtual machine.  Shared folders are working.  I have installed the Guest Additions.

First, I can't get USB or internet to work.  For internet, I have tried PCI II and FAST III, as well as Intel PRO/1000 MT Desktop, and none of them show a connection.  Bridged networking also doesn't work.  When I go into device manager in XP, the onboard ethernet adapter is shown, but no virtual adapters.  In vb, I have this enabled and the "cable connected" box checked.  I have googled the living daylights out of this problem and everyone says it's supposed to "just work," but I can't get it to do so.  I am using a stripped-down XP...perhaps it lacks a necessary driver?  If so, what?

USB I have not tested extensively, just my USB flash drive.  The drive opens in Ubuntu but not in the virtual XP.  Not sure what's up with that, either.

Any insights?

Thank you.

---

### Post by inverseroom on 2010-05-24
Edit, solved the MAME video issue and removed it from the thread title.

---

### Post by inverseroom on 2010-05-24
OK, getting closer.  That's not my hardware adapter in the device manager, it's the VMware PCnet adapter!  XP can't find a driver for it.  How do I fix this?

---

### Post by inverseroom on 2010-05-24
OK--found the driver on the system.  Marking solved, thanks.

---

### Post by flyfishingphil on 2010-05-24
Inverscom, maybe you could post what you did to correct the problems so others can use this thread in the future if they have the same problems?

---

