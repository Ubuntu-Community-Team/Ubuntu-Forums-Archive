---
title: "overlay-scrollbar issues"
date: 2016-01-06
forum: Ubuntu Development Version
---

### Post by mc4man on 2016-01-06
Yet again some qt packages affected, most notable is vlc & repo version of calibre. 
Seen here with vlc > open any menu item, window is about 9 times wider than screen & can't load.
[https://bugs.launchpad.net/overlay-scrollbar/+bug/1531516](https://bugs.launchpad.net/overlay-scrollbar/+bug/1531516)

(- for vlc this restores menu use via terminal - 
export LIBOVERLAY_SCROLLBAR=0 && vlc

or in vlc's .desktop edit Exec= line to 
Exec=env LIBOVERLAY_SCROLLBAR=0  vlc %U

---

### Post by ventrical on 2016-01-06
+1

---

