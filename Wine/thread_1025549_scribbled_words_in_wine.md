---
title: "scribbled words in wine"
date: 2008-12-30
forum: Wine
---

### Post by insanecrazy4 on 2008-12-30
i cannot read the words in wine and other games in wine when i try to conifgure options.

[http://img519.imageshack.us/my.php?image=screenshotwineconfiguraql8.png](http://img519.imageshack.us/my.php?image=screenshotwineconfiguraql8.png)

---

### Post by OrbJinzo on 2008-12-30
install mscorefonts package.

---

### Post by insanecrazy4 on 2008-12-30
i did now what should i do?

---

### Post by OrbJinzo on 2008-12-30
> **vpappas said:**
> Same problem here when using the official NVidia driver (ver 96.43.09-0ubuntu1). (I don't know if that is the case with you .. :) )

Anyway, you can try a workaround found here [https://bugs.launchpad.net/bugs/300476]("https://bugs.launchpad.net/bugs/300476")

Create a file named 'settings.txt' with the following contents :

[HKEY_CURRENT_USER\Software\Wine\X11 Driver]
"ClientSideWithRender"="N"

and then run 'regedit settings.txt'.

I hope it helps.

I guess you can try this I found in searching the wine forum

---

### Post by insanecrazy4 on 2008-12-30
ty i got it to work now :)

---

