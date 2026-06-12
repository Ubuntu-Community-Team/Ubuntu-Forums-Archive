---
title: "Amarok kept back?"
date: 2005-06-16
forum: Ubuntu Backports
---

### Post by spacemonkey on 2005-06-16
I tried upgrading tonight from staging to get the new amarok, but it said that the packages are being kept back.  I did smart upgrade, but it still isn't upgrading.  Any clue what the problem is?  I'm sure it's with my system, but how do I fix it?

---

### Post by Mez on 2005-06-16
I suggest adding the following line to your /etc/apt/sources.list - this will make sure you can have the latest version of kubuntu Libraries (which amaroK is dependent on)

```
deb http://kubuntu.org/hoary-kde341 hoary-updates main
```

---

### Post by spacemonkey on 2005-06-16
That did it, thanks.  I don't use KDE but I do use a few KDE programs in gnome.  I didn't realize I wouldn't get KDE upgrades from the regular repos.

---

### Post by Paulus on 2005-06-16
I'd like to second that thanks. :)   

/often wonders how some people know so much!

---

### Post by jdong on 2005-06-16
Amarok is currently being recompiled so that it doesn't need the new KDE updates.

---

### Post by Mez on 2005-06-16
uploading to staging now!

---

