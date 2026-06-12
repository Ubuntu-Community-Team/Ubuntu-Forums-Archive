---
title: "Where is Unity 3D session?"
date: 2012-02-08
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by velcom on 2012-02-08
after today`s update i no loger have unity 3d
as options on login screen i only have "Ubuntu 2D"

how should i restore unity back?

---

### Post by Pilot6 on 2012-02-08
You probably did not install video drivers.

---

### Post by prusswan on 2012-02-08
See this: [http://ubuntuforums.org/showpost.php?p=11669097&postcount=2](http://ubuntuforums.org/showpost.php?p=11669097&postcount=2)
if that does not help then maybe it is really a hardware problem

---

### Post by philinux on 2012-02-08
> **velcom said:**
> after today`s update i no loger have unity 3d
as options on login screen i only have "Ubuntu 2D"

how should i restore unity back?

I just did an update and I still have Unity and Unity-2d.

Check under additional-drivers

---

### Post by velcom on 2012-02-08
I`m trying to install ubuntu-desktop via Synaptic because i`m behind a proxy and apt-get doesn`t work for me

That`s not the problem i found the package but when i mark it for installation i get this error and i can`t get it to install:

ubuntu-desktop:
 Depends: unity but it is not going to be installed

later edit: i dont`t think it`s a video/hardware problem, the only additional driver i use is for my Broadcom Wireless Adaptor
               if trying to install package unity i get: "unity: Depends: unity-common (=5.2.0-0ubuntu2) but 5.2.0-0ubuntu3 is to be installed" and that is because of the update, should i do a downgrade of package unity-common ? i don`t think it`s a good ideea

---

### Post by velcom on 2012-02-08
ok, i`ve run a system update via synaptic and after that i was able to install "unity" and "ubuntu-desktop" packages, "Ubuntu" and "Ubuntu 2D" sessions appears in the drop-down menu of the loghin screen but when i enter "Ubuntu" session, the top panel and the app launcher does not load, but the desktop with the icons do

i was able to load the panels by opening a terminal with Ctrl+Alt+T and doing a "unity --reset"

how can i resolve this?

---

### Post by prusswan on 2012-02-08
good luck, I hope you did not run into the same problem I did

---

