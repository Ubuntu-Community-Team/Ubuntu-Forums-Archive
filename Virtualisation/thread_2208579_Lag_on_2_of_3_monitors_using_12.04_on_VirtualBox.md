---
title: "Lag on 2 of 3 monitors using 12.04 on VirtualBox"
date: 2014-03-01
forum: Virtualisation
---

### Post by yenic on 2014-03-01
I have a VM of 12.04 with 3 monitors, and the center, primary, screen always runs well and for the most part lag-free. The side monitors are very slow to react, and freeze for long periods of time when attempting to use applications on them. Things such as entering text into any application (IRC, gedit, etc).
It works fine when I only use 1 monitor with Vbox and if I use all 3 and don't attempt to use the other 2 screens, it also never fails to work well.

Has this been seen before or is it a known issue? 

Ubuntu 12.04 LTS all latest updates (as of 03/01/2014)
VBox with extensions all latest updates (as of 03/01/2014)
Core2Quad 9450 (1core allocated to VM), 8GB RAM (4GB allocated to VM), Intel G2 160GB SSD

---

### Post by ajgreeny on 2014-03-01
I am not certain but I think is is the result of VB using its own virtualised graphics system, not the hardware that you have on the host box.

If I'm correct I don't think there is any way you can make things better apart from making sure that the display settings in the guest are set to use as much graphics memory as is available, which I think is 128MB.

---

### Post by yenic on 2014-03-03
Thanks for the response. I was able to get this resolved, but not in the way I wanted to. I switched from VirtualBox to VMWare. I had to setup a new install/VM but it has none of the issues. Much faster, fast enough I don't need to even run Unity 2D.

---

