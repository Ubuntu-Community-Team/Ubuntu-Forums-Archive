---
title: "No Longer boot"
date: 2006-11-22
forum: The Cafe
---

### Post by VirginGeek on 2006-11-22
I mistakenly modified the /etc/x11/xorg.conf file to change my screen resolution to hopefully stop firefox from crashing and now I cannot boot. I'm wondering how to get into the system folder to correct this. I still have the original boot cd to boot from. I guess mistakes creates knowledge. Thanks guys.

---

### Post by aidanr on 2006-11-22
reboot and when grub is loading press escape and choose the second option - recovery mode. then when it's done booting type in ```
nano /etc/X11/xorg.conf
``` undo the changes you made, then hit ctrl-o to save and ctrl-x to exit, and then type reboot to reboot

---

### Post by rjwood on 2006-11-22
> **VirginGeek said:**
> I mistakenly modified the /etc/x11/xorg.conf file to change my screen resolution to hopefully stop firefox from crashing and now I cannot boot. I'm wondering how to get into the system folder to correct this. I still have the original boot cd to boot from. I guess mistakes creates knowledge. Thanks guys.Your correct, it's the only way to learn. Just don't panic, there is nothing that can't be fixed! Good luck and welcome to ubuntu:D

---

### Post by VirginGeek on 2006-11-23
Fixed!!!! Thank you!!!!:)

---

