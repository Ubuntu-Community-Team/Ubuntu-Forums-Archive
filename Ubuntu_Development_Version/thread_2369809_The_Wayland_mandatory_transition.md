---
title: "The Wayland mandatory transition"
date: 2017-08-27
forum: Ubuntu Development Version
---

### Post by dino99 on 2017-08-27
From the past, ubuntu already have made some transitions, like: gksu/gksudo -> pkexec, policikit -> pkexec.
As pkexec is a no go with wayland, numerous apps need to use policykit to deal with the wayland restriction made by design.

[https://wayland.freedesktop.org/faq.html](https://wayland.freedesktop.org/faq.html)

The already reported troubles:
[https://bugs.launchpad.net/ubuntu/+source/guymager/+bug/1713311](https://bugs.launchpad.net/ubuntu/+source/guymager/+bug/1713311)
[https://bugs.launchpad.net/ubuntu/+source/lightdm-gtk-greeter-settings/+bug/1713313](https://bugs.launchpad.net/ubuntu/+source/lightdm-gtk-greeter-settings/+bug/1713313)
[https://bugs.launchpad.net/ubuntu/+source/synaptic/+bug/1712089](https://bugs.launchpad.net/ubuntu/+source/synaptic/+bug/1712089)
[https://bugs.launchpad.net/gui-ufw/+bug/1713238](https://bugs.launchpad.net/gui-ufw/+bug/1713238)

What gnome says: [https://wiki.gnome.org/Initiatives/Wayland/Applications](https://wiki.gnome.org/Initiatives/Wayland/Applications)

---

### Post by jbicha on 2017-08-27
You can find more issues by browsing the [wayland tag]("https://bugs.launchpad.net/ubuntu/+bugs?field.tag=wayland") in LP.

---

### Post by Frogs Hair on 2017-08-28
[https://bugs.launchpad.net/bugs/1686504](https://bugs.launchpad.net/bugs/1686504)

> Eventually there should be no separate “root” and “non-root” versions of
BleachBit, instead having a single launcher and the application asking
for elevated permissions inside it, using PolicyKit instead of GKSu
(deprecated since 2011).


** Changed in: bleachbit (Ubuntu)
   Importance: Undecided => Medium


---

