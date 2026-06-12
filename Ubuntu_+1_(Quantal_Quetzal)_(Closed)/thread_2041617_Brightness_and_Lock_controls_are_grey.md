---
title: "Brightness and Lock controls are grey"
date: 2012-08-13
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by mdurham on 2012-08-13
I want to un-set "Require my password when waking from suspend" but I can't because all the "Lock" controls are... er... locked.
Any suggestions?
Cheers, Mike

---

### Post by robtygart on 2012-08-13
Sorry Ignor! Wrong Thinking. :confused:

---

### Post by mc4man on 2012-08-13
Sometimes things get messed up locally & can be  hard to figure, if you were to try as a different user likely would be fine.
What happens if you adjust in dconf?
```
gsettings set org.gnome.desktop.screensaver ubuntu-lock-on-suspend false
```
or as in screen (dconf-editor

---

### Post by mdurham on 2012-08-14
> **mc4man said:**
> Sometimes things get messed up locally & can be  hard to figure, if you were to try as a different user likely would be fine.
What happens if you adjust in dconf?
```
gsettings set org.gnome.desktop.screensaver ubuntu-lock-on-suspend false
```
or as in screen (dconf-editor
Thanks mc4man, that led me to solving the problem.

---

