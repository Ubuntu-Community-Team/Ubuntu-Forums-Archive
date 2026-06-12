---
title: "freecad and adwaita full icon set are gone?"
date: 2024-03-17
forum: Ubuntu Development Version
---

### Post by Claus7 on 2024-03-17
Hello,

as the title suggests I cannot find the aforementioned packages to install:
1) freecad is gone for some time now and it hasn't returned
2) adwaita full icon theme disappeared just a couple of days ago

For the first one I found out that an appimage is available. For the second one I found this: [https://bugs.launchpad.net/ubuntu/+source/xubuntu-meta/+bug/2052867](https://bugs.launchpad.net/ubuntu/+source/xubuntu-meta/+bug/2052867), yet it is for xubuntu. Does this mean that all icons from full were trasferred to regular?

Regards!

---

### Post by jbicha on 2024-03-17
> **Claus7 said:**
> Does this mean that all icons from full were trasferred to regular?


Yes, but also there aren't nearly as many Adwaita icons as there used to be. Ubuntu 24.04 LTS's adwaita-icon-theme package with every upstream icon is a smaller file than Ubuntu's streamlined package in previous Ubuntu releases.

---

### Post by Claus7 on 2024-03-17
Hello,

> **jbicha said:**
> Yes, but also there aren't nearly as many Adwaita icons as there used to be. Ubuntu 24.04 LTS's adwaita-icon-theme package with every upstream icon is a smaller file than Ubuntu's streamlined package in previous Ubuntu releases.

thank you for your response. I had some icons under synaptic changed to symbolic, which I thought might be related, since this package was the only icon set I think that changed when I noticed this difference. Yaru icon theme was unaffected though, at least for synaptic.

I hope that not all icons will turn out to be symbolic, because it is hard to change them back to regular, since almost always the places that they are stored are different from version to version, unless there is a simple command to change them back. 

One such command is the following:
/* Global Values */
* {
  -st-icon-style: regular !important; }

placed under the gnome-shell theme of choice, yet it doesn't change all of them. Anyway, until gnome 46 arrives, I think that I will have to wait and see the changes taking place.

Regards!

---

### Post by jbicha on 2024-03-17
Many icons were dropped. The GNOME designers expect app developers to bundle their own icons now.

This isn't new to GNOME 46. Ubuntu just had been using an old version of adwaita-icon-theme before those icons were dropped. But we can't indefinitely keep an old version and people were complaining about the Adwaita icon theme being outdated.

Unfortunately, Synaptic is approximately unmaintained so I wouldn't expect someone else to fix the issue. However, Synaptic is included in the default Ubuntu Cinnamon, Ubuntu Unity, and Xubuntu installs so maybe someone there might be interested if it also affects their default theme.

---

### Post by Claus7 on 2024-03-17
Hello,

> **jbicha said:**
> Many icons were dropped. The GNOME designers expect app developers to bundle their own icons now.

This isn't new to GNOME 46. Ubuntu just had been using an old version of adwaita-icon-theme before those icons were dropped. But we can't indefinitely keep an old version and people were complaining about the Adwaita icon theme being outdated.

Unfortunately, Synaptic is approximately unmaintained so I wouldn't expect someone else to fix the issue. However, Synaptic is included in the default Ubuntu Cinnamon, Ubuntu Unity, and Xubuntu installs so maybe someone there might be interested if it also affects their default theme.

as long as synaptic is working, a couple of icons will get fixed by finding the right path and changing them accordingly, I suppose. This is not the case for all the icons, since some regular ones are ugly, when trying to replace symbolic ones. The thing is that synaptic in some other themes is ok, e.g. humanity, and in the theme I was using only a couple of them changed, the rest were ok.

Regards!

---

### Post by Claus7 on 2024-07-25
Hello,

FreeCAD_weekly-builds-36904-2024-04-19-conda-Linux-x86_64-py311.AppImage is working fine under ubuntu 24.04 and it showed up under under synaptic using ubuntu 24.10.

Regards!

---

