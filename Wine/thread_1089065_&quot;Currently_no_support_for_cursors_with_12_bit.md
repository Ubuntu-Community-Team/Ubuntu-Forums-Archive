---
title: "&quot;Currently no support for cursors with 12 bits per pixel&quot; wha?"
date: 2009-03-06
forum: Wine
---

### Post by inanutshellus on 2009-03-06
Wine-noob here. I dug up an old Myst 1 CD and tried to install it using wine, but when I do I get this error:

```
$ wine install.exe
fixme:cursor:create_cursor_image Currently no support for cursors with 12 bits per pixel
```

I tried changing the plaform via winecfg to various versions of windows ('95, '98, 2000, Millenium, etc) but it didn't seem to matter. Am I fuggled?

I'm using Wine 1.1.10 on Ubuntu 7.10.

(Google didn't help)

---

### Post by cogadh on 2009-03-06
Looks like only the "Masterpiece Edition" of Myst works with Wine. The original 16 and 32 bit versions don't really work at all:
[http://appdb.winehq.org/objectManager.php?sClass=application&iId=91](http://appdb.winehq.org/objectManager.php?sClass=application&iId=91)

---

