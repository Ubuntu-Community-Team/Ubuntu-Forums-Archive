---
title: "Gnome / Nautilus extensions"
date: 2020-03-26
forum: Ubuntu Development Version
---

### Post by philippun on 2020-03-26
Hello,

there is no package for rabbitcs in Focal at the moment. Is it planned there to be one on release?
Also I've noticed that there are packges for Gnome extensions dash-to-panel and arc-menu. But they are a bit outdated. Will there be an update before final release?

I tried the latest rabbitvcs version, installed it manually and it works with the daily focal image. Would be very cool if it would be in the final release. I failed miserably at packaging it myself, so I sadly am no help for that. :(

Greetings

---

### Post by dino99 on 2020-03-26
Extensions are always the latest updated packages when they are maintained by the upstream gnome team. Others can be ready earlier or not , depending on the author(s).

But rabbitvcs seems abandonned from the ubuntu archive. [https://launchpad.net/ubuntu/+source/rabbitvcs](https://launchpad.net/ubuntu/+source/rabbitvcs)

---

### Post by P-I H on 2020-03-27
Dash to panel supports Gnome 3.36, but you have to do some work to get everything to work
- for settings to work gnome-shell-extension-prefs must be installed
- for the applications menu button to work "Show App Menu must be enabled". Before you were able to do that in gnome-tweaks, but this isn't available now. It will be enable with **sudo apt install gnome-shell-extensions gnome-tweaks**, however this will install other extensions you may not want.

---

### Post by mc4man on 2020-03-27
The latest rabbitvcs (python3/gtk3) just showed up in debian sid , likely too late for 20.04
If you wish to package just mod the debian source/packaging

---

### Post by philippun on 2020-04-05
rabbitvcs made it into focal, which makes me super happy. 20.04 will be the best release ever. :)

Also dash-to-panel got updated, arc menu sadly not. But that's ok, you can always use it form the gnome extensions webiste.

---

