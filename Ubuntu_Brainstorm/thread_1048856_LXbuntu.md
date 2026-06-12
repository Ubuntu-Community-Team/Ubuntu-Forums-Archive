---
title: "LXbuntu"
date: 2009-01-23
forum: Ubuntu Brainstorm
---

### Post by yanom on 2009-01-23
Why don't we make a Ubuntu variant that uses LXDE as it's desktop enviroment?

---

### Post by smartboyathome on 2009-01-24
Do it, no one is stopping you. Right now, I think it isn't needed officially, though.

---

### Post by Sorivenul on 2009-01-24
Done:
[PUD GNU/Linux]("http://distrowatch.com/?newsid=04826")

I also believe [U-lite]("http://u-lite.org/"), formerly Ubuntulite, uses LXDE, but I could be wrong on that.

Both are Ubuntu-based.

---

### Post by Cato2 on 2009-01-31
Both Crunchbang and U-Lite (formerly Ubuntulite) are LXDE-based derivatives of Ubuntu - not sure if they use all LXDE components, but U-Lite certainly uses lxpanel, lxde-settings, lxsession, lxterminal, with Openbox as the WM.

Crunchbang is much easier to install as it has a proper live CD and installer, but the theme may require some customizing unless you like a dark theme with a right-click desktop menu for all apps.  Also the font sizes were all over the place and it was hard to configure them all.   It does come preconfigured with Firefox, Java and Flash.  It can run well in 200 MB RAM, whereas I find Xubuntu is constantly thrashing pages in and out of swap in that size of PC.

U-Lite involves a longer install process starting with the Ubuntu mini CLI install, but it's not that hard.  Its emphasis is more on being ultra light weight, down to 100 MB RAM.

If you do edit the LXDE panel in U-Lite, be sure to copy all files from the central lxpanel directory to under your home directory, otherwise a panel may disappear - for example, ```
   cp /usr/share/lxpanel/profile/LXDE/top /home/yourusername/.config/lxpanel/LXDE/panels/
``` to copy the Top panel.

I also had to edit xorg.conf in U-Lite to get the resolution and mouse wheel working.  However, I now have a very nice looking lightweight system with font sizes that work.

If your PC has 200 MB or more, I would try Crunchbang first, otherwise try U-Lite. Links: [http://crunchbang.org/](http://crunchbang.org/) and [http://u-lite.org/](http://u-lite.org/)

---

