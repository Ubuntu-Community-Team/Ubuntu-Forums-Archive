---
title: "All KDE QT software is giving network certificate issues as of today (daily live ISO)"
date: 2021-12-01
forum: Ubuntu Development Version
---

### Post by pqwoerituytrueiwoq on 2021-12-01
Date: 21-12-1
Discover (KDE style app store), downloading widgets online via the panel, weather report applet/widget, browser integration, adding new tabs to the system monitor from online sources all results in errors

no issues with apt, curl, wget

Screenshots of the weather applet one [https://imgur.com/a/7Kyt8U6](https://imgur.com/a/7Kyt8U6) (you will get 3 of these to click through)

---

### Post by pqwoerituytrueiwoq on 2021-12-01
the package causing the issue is [FONT=monospace][COLOR=#000000]libqt5network5[/COLOR][/FONT]

[https://bugs.launchpad.net/ubuntu/+source/qtbase-opensource-src/+bug/1952977](https://bugs.launchpad.net/ubuntu/+source/qtbase-opensource-src/+bug/1952977)

---

