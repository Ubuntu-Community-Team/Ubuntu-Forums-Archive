---
title: "System hangs after updating the OS"
date: 2016-02-24
forum: Virtualisation
---

### Post by vijaysinghparmar on 2016-02-24
Hi,

I downloaded the ubuntu-14.04.4-desktop-amd64 and installed it on my VMWare Workstation (11.1.0 build-2496824).

The OS was loaded successfully. After sometime I was prompted for software updated to which I agreed.

When the system rebooted the system is getting hanged ( I waited for 4 hours for the system to come-up).

I then power-off the machine itself and tried to reboot it again but again the same problem.

Attached the following screenshots :-

1. System Screen
2. VMWare Workstation

Please suggest.

---

### Post by bialix on 2016-02-24
vijaysinghparmar - I have similar problem after yesterday's update.

So far, holding Shift key during VM boot (make sure VM catch the input - if needed press Ctrl+G very fast and then hold Shift key) - it can open bootloader menu - select Advanced options for  Ubuntu and then try to select previous kernel version. For me version 3.19.0-51 does not boot, but previous 3.19.0-49 still boots OK.

In my case kernel-51 hangs after "Stopping System V runlevel compatibility", but I didn't wait for 4 hours.

---

### Post by Bucky Ball on 2016-02-24
*Thread moved to **Virtualisation**.*

---

### Post by jrh31 on 2016-02-28
Today correction published
Kernel 3.19.0-51.57 replaced by 3.19.0-51.58
Start on  kernel 3.19.0-49 and apt-get update + upgrade works fine for me

---

