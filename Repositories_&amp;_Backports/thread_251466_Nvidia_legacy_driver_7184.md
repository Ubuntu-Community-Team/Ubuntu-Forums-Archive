---
title: "Nvidia legacy driver 7184 ?"
date: 2006-09-05
forum: Repositories &amp; Backports
---

### Post by Erwin123 on 2006-09-05
Hello,

the Nvidia legacy driver currently packaged with dapper (7174) has some issues with the "RenderAccel" option: the Xserver suddenly starts to run at 100% CPU and the keyboard is dead, the mouse may move, but you can't click anything... This bug is resolved in the new version of the driver which was released a few week ago. Without the RenderAccel option, the display is extremely slow (at least since some Xorg update and with my ancient GeForce2 card).

It would be very, very helpful if someone could package the latest driver from Nvidia and update "nvidia-glx-legacy" to version 1.0.7184.

Many thanks!
Erwin

---

