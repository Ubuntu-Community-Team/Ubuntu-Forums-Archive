---
title: "Boot stops at starting CUPS"
date: 2010-09-27
forum: Server Platforms
---

### Post by xtopher.brandt on 2010-09-27
Hi there,

I'm running 8.04 LTS (Hardy) Server Edition with LILO as the bootloader and a desktop interface. I'm running server because this machine is always on and has a pair of RAIDed disks. It has the desktop because I was a newbie to linux when I built it and needed the comfort of a GUI to get me going.

This morning I updated the kernel headers and Google Chrome through the Update Manager. After the update, Chrome would not start so I restarted the box.

Now the boot gets to the point of starting CUPS, then stops. It never times out, but if I push the power button it will shut down the services that had started and power off on its own.

How do I diagnose this and get it running again. It has SAMBA installed and running, but I don't think I'm using CUPS (unless it's linked to SAMBA somehow). Not sure if it's possible to disable it. 

Thanks for any suggestions
Chris.

---

