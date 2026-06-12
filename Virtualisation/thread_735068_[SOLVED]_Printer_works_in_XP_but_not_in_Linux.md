---
title: "[SOLVED] Printer works in XP but not in Linux"
date: 2008-03-25
forum: Virtualisation
---

### Post by LeeU on 2008-03-25
I am using a Brother HL 2040 printer and it has worked fine in Ubuntu 7.10. I have since installed VirtualBox and run XP Home, which works great also. The problem is that, when I run XP, the printer (connected via USB) works fine in XP but then Ubuntu doesn't recognize it. It says that it is disconnected. If I then shut down VB, I have to re-start Ubuntu to get the printer to work again.

Anyone have this problem and/or know of a solution?

---

### Post by luisromangz on 2008-03-25
The printer can be conected to just one machine, the real one or the virtual. So if you use the usb emulation in the virtual machine, you lose the printer in the host machine.

I would try keep the printer connected to ubuntu, and share the printer through Samba.

---

### Post by LeeU on 2008-03-25
> **luisromangz said:**
> I would try keep the printer connected to ubuntu, and share the printer through Samba.

Ah, makes sense. Thanks! And it works too!

---

