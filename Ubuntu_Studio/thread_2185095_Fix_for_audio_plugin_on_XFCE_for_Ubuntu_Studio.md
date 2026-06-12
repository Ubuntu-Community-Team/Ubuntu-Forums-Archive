---
title: "Fix for audio plugin on XFCE for Ubuntu Studio"
date: 2013-11-01
forum: Ubuntu Studio
---

### Post by leor-bi-otti-flor-b on 2013-11-01
Hi all, I found a fix for the audio plugin. The sound works but the audio plugin don't display the volume when is being changed. To fix this follow this 2 way with 4 steps

WAY 1
1. Open the **terminal**
2. Type **sudo gedit /usr/share/dbus-1/services/indicator-sound.service** and type your password
3. Change the last line to look like this **Exec=/usr/lib/indicator-sound-gtk2/indicator-sound-service**
4. **Log off** or **reboot**

WAY 2
1. Press **Alt + F2** and type **gksu thunar**
2. Go to **/usr/share/dbus-1/services** and open **indicator-sound.service**
3. Change the last line to look like this **Exec=/usr/lib/indicator-sound-gtk2/indicator-sound-service**
4. **Log off** or **reboot**


Enjoy =)

---

### Post by Toz on 2013-11-01
Hello and welcome to the forums.

The official bug report can be [found here]("https://bugs.launchpad.net/ubuntu/+source/indicator-sound/+bug/1208204"). Keep in mind that the "workaround" is only a workaround and that those changes may be lost if that package gets updated (meaning that you may have to re-do the workaround). Hopefully a real fix will come soon so the workaround won't be needed.

---

