---
title: "Can't reset Wine's virtual desktop size."
date: 2009-03-19
forum: Wine
---

### Post by inearlygaveup on 2009-03-19
I have accidentally set wine desktop to 100 x 600 instead of 1000 x 600 consequently I can not access the reset window size box.
Any idea's please.

---

### Post by cogadh on 2009-03-19
Open the /home/<username>/.wine/user.reg file in a text editor (not OpenOffice). Scroll down to the section that looks something like this (it should be at the bottom of the file):
```
[Software\\Wine\\X11 Driver] 1187989190
"Desktop"="100x600"
```
Change that "Desktop" entry to a minimum of "800x600", save the file, then run winecfg again and you should be able to access everything normally.

---

### Post by inearlygaveup on 2009-03-19
> **cogadh said:**
> Open the /home/<username>/.wine/user.reg file in a text editor (not OpenOffice). Scroll down to the section that looks something like this (it should be at the bottom of the file):
```
[Software\\Wine\\X11 Driver] 1187989190
"Desktop"="100x600"
```
Change that "Desktop" entry to a minimum of "800x600", save the file, then run winecfg again and you should be able to access everything normally.

Great - thanks a lot - job done working again =D>

Martin

---

