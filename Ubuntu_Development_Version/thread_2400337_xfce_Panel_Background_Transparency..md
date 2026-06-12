---
title: "xfce Panel Background Transparency."
date: 2018-09-05
forum: Ubuntu Development Version
---

### Post by PJs Ronin on 2018-09-05
I've tried an upgrade of Bionic to Cosmic, a new install of 18.10 Xubuntu and a new install of Core xfce and all exhibited the same problem, viz, panel backgrounds can no longer be set to transparent via the 'alpha channel' in Settings Manager > Personal > Panel > Appearance.   I've tried with, and without, the recommended nvidia drivers; no difference.   Finally, I tracked down a comment in the 18.10 [changelog ]("https://launchpad.net/ubuntu/+source/xubuntu-default-settings/+changelog") that says:
> 
  * etc/xdg/xdg-xubuntu/xfce4/panel/default.xml:
    - Replace deprecated background-alpha with {enter,leave}-opacity
      for a semi-transparent panel with xfce4-panel 4.13+
    - Add separator and hide window list handle for cleaner panel
      appearance



Unfortunately, that makes no sense to me and I can't "clean up" the Cosmic xfce4 panels.   Has anyone had any success?

---

### Post by PJs Ronin on 2018-09-13
The alpha channel slider has been relocated and thus panel transparency is still available.
> [COLOR=#000000]Right click on a panel and select Panel > Panel Preferences > Appearance > Background > Style > Solid Colour then select the Colour button to choose a colour. Select the "+" to select a custom colour. On the bottom of the colour chart that pops up is the alpha channel slider. Slide to the left, save your way out and voila, transparent background on the panel.[/COLOR]

---

### Post by AndresC on 2018-11-03
It did work. Thnx. A bit confusing to search for a color and make it alpha, but it works.

Thnx!

---

### Post by cariboo on 2018-11-03
Thread Closed

---

