---
title: "[SOLVED] Wine can't install discs"
date: 2008-12-25
forum: Wine
---

### Post by SonnHalter on 2008-12-25
i'm following this guide [http://www.wine-reviews.net/applicat...with-wine.html](http://www.wine-reviews.net/applicat...with-wine.html)

after i use the wine setup i get an error saying

wine: could not load L"C:\\windows\\system32\\setup.exe": Module not found

---

### Post by cogadh on 2008-12-25
404 error on that link.

That particular error from Wine usually indicates that you did not give it the correct path when running the installation. For example, if your CD is mounted at /media/cdrom and is defined in Wine as the D: drive, then you need to run the install like this:
```
wine /media/cdrom/setup.exe

OR

wine "D:\setup.exe"
```

---

### Post by SonnHalter on 2008-12-26
i tried wine /media/cdrom0/Adobe CS3/Setup.exe
didn't work.

---

### Post by cogadh on 2008-12-26
Its probably the space between "Adobe" and "CS3" in the path. Terminal commands can't "see" spaces in paths, so you need to add an escape character to compensate for it:
```
wine /media/cdrom0/Adobe\ CS3/Setup.exe
```

---

### Post by SonnHalter on 2008-12-26
Holy ****. I love you i love you i love you i love you i love you

---

### Post by SonnHalter on 2008-12-26
i wouldn't really install ps. gui is too messed up. just get virtualbox

---

