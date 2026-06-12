---
title: "Unistalling COD4 modern warefare"
date: 2009-02-26
forum: Wine
---

### Post by invincibletoviruses on 2009-02-26
i went to Applications>wine>programs>activision>cod4>uninstall, i did what it prompted me to do and then i rebooted my computer and it was still under wine.i was wondering is i could check if its fully removed from my computer or how to fully remove it.thanks

-Rubin


ubuntu 8.10
wine version 1.0.1-ubuntu2

---

### Post by Bölvaður on 2009-02-26
this is the location
~/.wine/dosdevices/c:

```
nautilus ~/.wine/dosdevices/c:
```

you can find the register ~/.wine/dosdevices/c:/windows/regedit.exe
and the game is probably under programs.. or what ever it was called in windwos.

This works just like in windows, so I cannot be of any help.

---

### Post by invincibletoviruses on 2009-02-26
thanks!

-Rubin

---

