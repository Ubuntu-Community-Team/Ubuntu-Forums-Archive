---
title: "install vb6"
date: 2010-05-23
forum: Wine
---

### Post by croccio on 2010-05-23
how can i install visual basic 6 on wine??? i read the guide on wine's site, but i can't use text are label, picturebox etc... how can i run it on wine???

---

### Post by croccio on 2010-05-23
i installed electronic workbench, i can't read the text into the dropbox!

---

### Post by dino99 on 2010-05-23
add this ppa to the sources.list: [https://launchpad.net/~ubuntu-wine/+archive/ppa](https://launchpad.net/~ubuntu-wine/+archive/ppa)

then update and install winetricks (install vb6 with it by running "winetricks" in a console)

[http://appdb.winehq.org/objectManager.php?sClass=version&iId=1325](http://appdb.winehq.org/objectManager.php?sClass=version&iId=1325)

---

### Post by dino99 on 2010-05-23
> **croccio said:**
> i installed electronic workbench, i can't read the text into the dropbox!

you probably need to add some fonts with winetricks

---

### Post by croccio on 2010-05-23
i read that guide but vb6 doesn't work!

---

### Post by croccio on 2010-05-23
> **dino99 said:**
> you probably need to add some fonts with winetricks
how can i see wht font should i have?

---

### Post by dino99 on 2010-05-23
> **croccio said:**
> i read that guide but vb6 doesn't work!

from the winetricks dev: [http://www.kegel.com/wine/isv/tips.html](http://www.kegel.com/wine/isv/tips.html)

with some apps we need to add "the microsoft fonts" into the wine fonts folder too.

[http://us.generation-nt.com/answer/vb6-ide-linux-wine-help-136319791.html](http://us.generation-nt.com/answer/vb6-ide-linux-wine-help-136319791.html)

---

### Post by croccio on 2010-05-23
thank u i'm going to try it tomorrow!

---

### Post by dino99 on 2010-05-23
an other workaround is to use something else like .NET and Mono

---

### Post by croccio on 2010-05-23
i study vb6 at school i can't use other program =(

---

