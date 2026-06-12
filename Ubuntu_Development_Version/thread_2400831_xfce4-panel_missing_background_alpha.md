---
title: "xfce4-panel missing background alpha"
date: 2018-09-10
forum: Ubuntu Development Version
---

### Post by VMC on 2018-09-10
[bug report]("https://bugs.launchpad.net/ubuntu/+source/xfce4-panel/+bug/1791849")

The "Alpha" is missing on Cosmic, but on Bionic and all previous editions. See bug report.

---

### Post by PJs Ronin on 2018-09-11
Not exactly missing, deprecated.   I mentioned it here [https://ubuntuforums.org/showthread.php?t=2400337](https://ubuntuforums.org/showthread.php?t=2400337)

---

### Post by VMC on 2018-09-11
Thanks for the reply. I somehow missed you post. That is an unfortunate decision in my opinion. I don't know what prompted that, but "Enter/Leave transparency" are not the same thing as panel transparency.

---

### Post by PJs Ronin on 2018-09-12
> **VMC said:**
> ... but "Enter/Leave transparency" are not the same thing as panel transparency.

Fully support your comment.   However, in the changelog it mentions using "[COLOR=#000000]*Add separator and hide window list handle for cleaner panel *[/COLOR][COLOR=#000000]*appearance" *[/COLOR]as (I assume) a method of achieving the same result as the alpha channel.   I have not yet had success.

Another thing I tried was to *apt-mark hold xfce4-panel* to version 4.12 in my bionic install, clone that into a new partition and then dist-upgrade to cosmic.   Once this was done I confirmed that in cosmic the xfce4-panel was still 4.12 and not 4.13, but alas the panels were non-transparent.   Additionally, my VinDSL/Conkywx conky in the cosmic partition had also lost it's transparency, so perhaps bigger issues are at play.

Just thought of something.   Whilst messing in the new recalcitrant panel I did notice a "transparent" tag come up on a sub-element of the panel settings but at the time thought this was of no interest/consequence.    I'll have another look see, but without resolution this is really a killer for me and xfce4 on Ubuntu.

Regards.

---

### Post by VMC on 2018-09-12
I think this is all upstream and not ubuntu related as noted [here]("https://github.com/xfce-mirror/xfce4-panel/blob/master/NEWS"), and [here(manjaro)]("https://forum.manjaro.org/t/manjaro-xfce-v18-0-3rd-beta-build-testing/50561/74"). If you confirmed the bug report, then maybe a developer will comment.

edit: someone noted in that manjaro link that they created a small file " " and used that to have full transparency.

---

### Post by VMC on 2018-09-12
> **PJs Ronin said:**
> ...but without resolution this is really a killer for me and xfce4 on Ubuntu.

Regards.
Sadly, its also going to be elsewhere not just ubuntu. Hopefully there will be a work around.

---

### Post by PJs Ronin on 2018-09-13
A-HUH!   Got it.

Right click on a panel and select Panel > Panel Preferences > Appearance > Background > Style > Solid Colour then select the Colour button to choose a colour.   Select the "+" to select a custom colour.   On the bottom of the colour chart that pops up is the alpha channel slider.   Slide to the left, save your way out and voila, transparent background on the panel.

---

### Post by VMC on 2018-09-13
> **PJs Ronin said:**
> A-HUH!   Got it.

Right click on a panel and select Panel > Panel Preferences > Appearance > Background > Style > Solid Colour then select the Colour button to choose a colour.   Select the "+" to select a custom colour.   On the bottom of the colour chart that pops up is the alpha channel slider.   Slide to the left, save your way out and voila, transparent background on the panel.
So the Alpha is hidden?! That's confusing. I'll try it out this weekend to see for myself. Thanks for the heads up.

edit: I couldn't wait. Per your instructions, it works! Great find. I hope it stays that way.

---

