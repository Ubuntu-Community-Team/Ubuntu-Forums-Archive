---
title: "Virtual Desktop Issue"
date: 2009-03-03
forum: Wine
---

### Post by mrmagpie on 2009-03-03
This is going to sound particularly idiotic, but, with the Emulate Virtual Desktop option enabled, I accidentally set the screen size to something silly, like 8 x 800, and now have no way of accessing any of the information in the Wine Configuration to fix it.

Does anyone know of any other way to access this area, or something I could do to resize the screen so I could change the setting?

---

### Post by cogadh on 2009-03-03
Open the /home/<username>/.wine/user.reg file in a text editor (not OpenOffice). Scroll down to the section that looks something like this (it should be at the bottom of the file):
```
[Software\\Wine\\X11 Driver] 1187989190
"Desktop"="8x800"
```
Change that "Desktop" entry to a minimum of "800x600", save the file, then run winecfg again and you should be able to access everything normally.

---

### Post by mrmagpie on 2009-03-03
Thank you very much! 

I knew there had to be a way of fixing the problem that was just as simple as getting into it in the first place. ;)

---

