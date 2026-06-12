---
title: "Backintime verrrry slow to start on 1910."
date: 2019-09-29
forum: Ubuntu Development Version
---

### Post by rbmorse on 2019-09-29
Installed the 19.10 beta and things are generally working well.  One particular issue I can't solve:

When starting the user-mode GUI interface for backintime (from repo) it requires somewhere between 25 and 30 seconds before it appears on the desktop. In fact, the spinning wheel "wait" indicator will run it's course and it will appear the program has crashed, but it hasn't.  Once the interface appears, the application runs normally. 

The root-mode GUI interface operated normally, as do all of the background operations that actually perform the file manipulations. 

Backintime still uses qt4.  Could that be the cause of the issue?

---

### Post by rbmorse on 2019-09-30
Installing the package:

appmenu-gtk2-module

from repository solved the problem

---

