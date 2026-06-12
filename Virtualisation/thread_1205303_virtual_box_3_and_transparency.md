---
title: "virtual box 3 and transparency"
date: 2009-07-05
forum: Virtualisation
---

### Post by Mia1990 on 2009-07-05
Hi all

i have virtual box 3 installed running win xp pro when windows loads there is transparency in the window it opens in is there a way to stop this i can't see all the words for it thanks

---

### Post by andrea000 on 2009-07-06
had that problem before if your talking about when windows
starts it's transparent right click on the desktop icon and
replace the command to launch with this

env XLIB_SKIP_ARGB_VISUALS=1 VirtualBox

reboot and it should be fixed   :p

---

### Post by Mia1990 on 2009-07-06
Thank you andrea000 it works great just what i was looking for

---

