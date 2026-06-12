---
title: "Heads up, Kudu NetworkManager/Wifi Users!"
date: 2022-09-29
forum: Ubuntu Development Version
---

### Post by 3vi1 on 2022-09-29
I just rebooted this morning and found my wifi no longer worked.  I run Ubuntu (devel branch) with the KDE plasma desktop.

Upon investigation, I found that this was caused by the move the devel branch is making from wpa_supplicant to iwd.  This should be a very good thing in the end, but if your like me you did *not* have the iwd package installed (nor is it currently part of a meta package).  Recent updates have updated the NetworkManager config to use iwd for wifi... so you'll find no connectivity after you reboot.

To get online again, temporarily edit your /usr/lib/NetworkManager/conf.d/10-globally-managed-devices.conf file.  You'll want to remove ",except:type:wifi" and then restart the NetworkManager service.

After that, you should be back online so that you can actually install iwd.  Don't forget to undo your edits afterward - there's no reason to avoid progress!

Later friends!

---

### Post by PilotPaul on 2022-09-29
Bug already reported ([https://bugs.launchpad.net/bugs/1990891](https://bugs.launchpad.net/bugs/1990891)) - current fix is to delete /etc/NetworkManager/conf.d/iwd.conf and reboot...

---

### Post by grahammechanical on 2022-09-29
This perhaps explains why when I booted into 22.10 early on today there were no updates. Which is most unusual for a development version.

P.S. Things like this happening are the reason why I dual boot the development version with on older LTS version.

Regards

---

### Post by luckyknight on 2022-10-01
Was about to ask about this, what a major bug! Hopefully the above fix works for me.

---

