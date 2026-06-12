---
title: "Getting good looking fonts with fonts.conf tweaks and google fonts"
date: 2013-06-12
forum: Ubuntu, Linux and OS Chat
---

### Post by silv3rm00n on 2013-06-12
Hi

I played around with some settings in the .fonts.conf file and used free google fonts like droid, noto sans
they give excellent rendering results on ubuntu. not talking about any patches to freetype

check out the details here

[Gorgeous looking fonts on ubuntu]("http://www.binarytides.com/gorgeous-looking-fonts-ubuntu-linux/")

Should give considerable improvement on LCDs. Laptops/tablets might not give any difference.

Let me know

Regards
Silver

---

### Post by ajgreeny on 2013-06-12
I have never had any font problems in Ubuntu with gnome, but recently after changing to Xubuntu 12.04, then making some changes in KDE system-settings package, as I hasve k3b, kmymoney and digikam installed, I found that font rendering was dreadful, everything looking thin and spindly whatever I did in the xubuntu appearance settings.

Contrary to what you are suggesting, I found, quite by accident, that deleting the .fonts.conf file made by kde system-settings, made everything look terrific and back to normal again, and much better than fonts ever looked on WinXP.

I did download the .fonts.conf file that you link to in order to try it out, just for interest, and it made absolutely no difference to the great font rendering on my system, so I have deleted it again, but at least it produced a look that was very much better than the kde version of the file made of my system's looks.

For your information I have Ubuntu Regular, at size 11, as my system font for the desktop, and Dejavu Sans Mono Book size 12 as my terminal font.

---

### Post by BubuXP on 2013-06-12
Probably you know about Infinality. Have you checked his work while doing your fonts.conf file? I looked briefly at it and seems like doing a job similar to fontconfig-infinality. Probably a comparison between the two configurations could lead to better results in one or both sides...

---

### Post by buzzingrobot on 2013-06-13
If the configuration you set in KDE or Gnome is at odds with the configuration set in .fonts.conf, then the result may be less than optimal.  Plus, with recent freetype releases, putting .font.conf in ~ is deprecated and will generate a warning. I always adjust my desktop font settings to match .fonts.conf.

Infinality produces a different look than standard Ubuntu, and is probably more aligned with standards.  It's also much more configurable, but it presupposes knowledge that doesn't exist in most users.

I tried SilverMoon's very large .fonts.conf file and, frankly, noticed no changes.

---

### Post by silv3rm00n on 2013-07-04
yeah, for many users it does not make any noticeable difference specially on laptop/tablets with large font sizes.
but on lcd monitors with small font size, it makes huge difference in clarity and shapes.

---

