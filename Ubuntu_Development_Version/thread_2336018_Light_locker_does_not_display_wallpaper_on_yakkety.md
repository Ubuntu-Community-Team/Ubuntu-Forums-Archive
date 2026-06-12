---
title: "Light locker does not display wallpaper on yakkety"
date: 2016-09-03
forum: Ubuntu Development Version
---

### Post by Pablo_San_Martn on 2016-09-03
So the xorg issue with the pointer disappearing has been solved and that is absolutely great!

However, I still seem to have a problem with light locker. After suspend, locking the screen or logging out, I see my wallpaper for a second or so, then there is a glitch and turns to the default light blue background. When I change the user to Guest and then back to my account, my wallpaper appears and stays for good. 

Any ideas as to what might be causing this and/or how to fix it?

---

### Post by Frogs Hair on 2016-09-05
Moved to *Ubuntu Development Version.*

---

### Post by pqwoerituytrueiwoq on 2016-09-10
This issue is present for me on xubuntu 16.04, upgraded from 14.04
after boot up when lightdm loads the wallpaper fades in then the screen flickers 1 time and the wallpaper is gone
i turned the user wallpaper feature off but the flicker is still there

---

### Post by Pablo_San_Martn on 2016-09-25
Should we report this as a bug? Where?

---

### Post by pqwoerituytrueiwoq on 2016-09-28
run this command to report it 
```
ubuntu-bug [package_name]
```
example
```
ubuntu-bug lightdm
ubuntu-bug systemd
ubuntu-bug xubuntu-desktop
```
not sure which package to blame

---

