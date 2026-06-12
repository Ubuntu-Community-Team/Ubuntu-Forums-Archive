---
title: "Strange font problem (Ubuntu 12.04 beta2)"
date: 2012-04-12
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by Forux on 2012-04-12
Text displayed incorrectly
for example in the "H" left stick is different from the right, it is displayed on the subpixels
It is a native resolution of the monitor (1360:768 SyncMaster 943SN)

Ubuntu 12.04 beta2
KDE
(in the ubuntu one looks even worse)

How i can solve this (help me pls)?
P.S. hard to look in to this monitor all day

UPD:
screen from ubuntu one 2D
[http://www.image-share.com/ipng-1414-65.html](http://www.image-share.com/ipng-1414-65.html)

UPD: reinstalled OS to ubuntu 12.04 LTS to solve this problem.

---

### Post by philinux on 2012-04-12
Moved to testing forum.

---

### Post by NHclimber on 2012-04-12
> **Forux said:**
> Text displayed incorrectly
for example in the "H" left stick is different from the right, it is displayed on the subpixels
It is a native resolution of the monitor (1360:768 SyncMaster 943SN)

Ubuntu 12.04 beta2
KDE
(in the ubuntu one looks even worse)

How i can solve this (help me pls)?
P.S. hard to look in to this monitor all day

It would be more helpful if you post a screenshot.

---

### Post by Forux on 2012-04-12
[http://www.image-share.com/ipng-1414-65.html](http://www.image-share.com/ipng-1414-65.html)

---

### Post by NHclimber on 2012-04-12
I see what you mean. Can you post the output of:
```
xrdb -query
```

Also, did you change the stock font/size with ubuntu-tweak?

---

### Post by Forux on 2012-04-13
```
xrdb -query
*customization: -color
Xft.dpi:        96
Xft.antialias:  1
Xft.hinting:    1
Xft.hintstyle:  hintslight
Xft.rgba:       rgb
Xft.lcdfilter:  lcddefault
```

i do not use ubuntu-tweak
and i did not change font parameters manually

---

### Post by NHclimber on 2012-04-13
When I set the system font back to the default (Ubuntu 11), I get *exactly* the same glyph rendering as you.  I've attached a blow-up (which was zoomed unfiltered) so you can see why the glyph 'legs' seem different -- because they are!  The situation may be somewhat exaggerated by your particular lcd but I agree it still looks nasty.

Until freetype implements ClearType, the easiest solution is to either change the font or font size. MyUnity will allow you to do this; it's in the repositories.  I'm not a fan of its UI design though. Personally, I still use ubuntu-tweak.

---

