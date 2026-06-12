---
title: "Warcraft 3 Frozen Throne"
date: 2009-08-04
forum: Wine
---

### Post by dtrot55 on 2009-08-04
I did this a little different so this is why I am asking.  I took my warcraft 3 folder from my windows machine and put it in the wine directory.  But I can't seem to get the right path down in the terminal to run the exe.  

This is the url to the folder:  

/home/dtrot/.wine/dosdevices/c:/Program Files/Warcraft III

I tried running it through sudo but realized after reading the wine post to not do that...so just asking for help...still a wine noob :(

---

### Post by goldfish2 on 2009-08-04
something like this might work:
```
env WINEPREFIX="/home/dtrot/.wine/dosdevices/c:/Program Files/Warcraft III" wine "c:/Program Files/Warcraft III/war3.exe"
```

Its not just about running the EXE, Wine has to know the right base directory so it can access the other files required to run warcraft.

Dan

---

### Post by dtrot55 on 2009-08-04
Cool..thanks I will try it out and let you know

---

