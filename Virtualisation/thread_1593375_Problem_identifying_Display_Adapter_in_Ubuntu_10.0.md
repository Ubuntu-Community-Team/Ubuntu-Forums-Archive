---
title: "Problem identifying Display Adapter in Ubuntu 10.04.1 on VMWare 7"
date: 2010-10-11
forum: Virtualisation
---

### Post by nukunu on 2010-10-11
Hello, I am running **Ubuntu 10.04.1 **in **VMWare 7 **installed on a Toshiba L555 (Windows 7 x64) (using  Intel Graphics Media Acceleration HD card). Installation completed successfully but when I go the the **System ---> Monitor**, I get the notification,** MONITOR UNKNOWN**. Also when i run **lspci | greg VGA** I get **00:0f.0 VGA compatible controller: VMware SVGA II Adapter**
Thus when I try enabling Visual Effects, the system searches for available drivers and Prompts Me: **Desktop Effects Could Not Be Enabled**. 
How can I update the available drivers to Display the appropriate Monitor settings.
Thank you.

---

### Post by Lumb on 2010-10-11
Also looking for a solution to this problem.

---

### Post by fjgaude on 2010-10-11
ASAIK, WS 7 uses a virtual display driver for any video board it detects. So you can't load a driver for your board.

---

