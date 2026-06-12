---
title: "Daily build nasty bug: Lose background If you change style, icon or font"
date: 2014-04-03
forum: Ubuntu Development Version
---

### Post by spsf2 on 2014-04-03
Well the topic says it all... 
Nvidia GPU here, not sure if it happens with Ati or Intel.
This bug started to happen like 2 or 3 days ago either with daily build or installed/updated to HD.

Just go to: settings / appearance and change ANY item like style, icons or fonts and you lose your background/image.

The only way to revert is log out/in or go to desktop settings and uncheck/check "backgorund tab / aplly to all workspaces"
Hope it gets fixed

---

### Post by cariboo on 2014-04-03
Which Nvidia driver are you using?

---

### Post by spsf2 on 2014-04-03
> **cariboo907 said:**
> Which Nvidia driver are you using?
It happens with both open source or proprietary, in live mode and when installed to HD, just check yourself with today (april 03) daily iso

---

### Post by Elfy on 2014-04-03
known issue - [https://launchpad.net/bugs/1302101](https://launchpad.net/bugs/1302101)

Alt+F2 - then xfdesktop --reload

---

