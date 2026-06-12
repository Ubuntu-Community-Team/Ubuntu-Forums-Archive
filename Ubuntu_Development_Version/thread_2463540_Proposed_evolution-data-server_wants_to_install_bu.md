---
title: "Proposed evolution-data-server wants to install budgie-desktop"
date: 2021-06-13
forum: Ubuntu Development Version
---

### Post by Yahoé on 2021-06-13
In the regular Ubuntu Gnome, the evolution-data-server 3.40.2-1 in impish-proposed wants to uninstall chrome-gnome-shell, gdm3, gnome-shell, ubuntu-desktop, etc. and install budgie-desktop and related in its stead. Does anyone know why, what is happening there?

---

### Post by Frogs Hair on 2021-06-14
I just installed UB impish and don't see the Budgie DE as a dependency of evolution-data-server. I do not enable proposed updates due to partial upgrade issues and problems like the one you are experiencing. Proposed updates often come as incomplete clusters of packages and installing one may remove others until all necessary dependencies are available.

---

### Post by Yahoé on 2021-06-14
Thanks Frogs Hair. I’m quite aware of what the proposed channel is and of its shortcomings. Still, I’m curious to find out why.

---

### Post by Frogs Hair on 2021-06-15
Asking a question on launchpad.net  may be the best way to get your question answered. This may also be a bug the developer is unaware of.

---

### Post by Yahoé on 2021-06-16
Thanks Frogs Hair, I did just that &#128578;

---

### Post by xyz-t on 2021-07-03
The problem appears to be in Synaptic that shows many packages to upgrade including budgie-desktop. I've lost the install with the July second ISO (Ubuntu) after upgrading the Synaptic Packages. That was after downloading the Proposed content.

Second fresh install was OK, but did not touch Synaptic.

---

