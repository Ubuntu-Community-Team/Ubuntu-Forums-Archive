---
title: "Right click on file kills dolphin 15.10"
date: 2015-08-30
forum: Ubuntu Development Version
---

### Post by buzzmandt on 2015-08-30
for the past several updates (am current up to date rtm) dolphin dies when i right click on any file. Anyone know if there is a bug report or needs to be?
Running in terminal spits out the following:

dolphin 
QLayout: Attempting to add QLayout "" to PhononWidget "", which already has a layout 
KServiceTypeTrader: serviceType "KonqPopupMenu/Plugin" not found 
QThread: Destroyed while thread is still running 
Segmentation fault (core dumped)

---

### Post by SeijiSensei on 2015-08-31
All bets are off when it comes to non-LTS versions of Ubuntu.  Kubuntu 15+ is even more problematic since KDE5 is known to have bugs.  If this is a persistent, replicable problem, you should file a bug report if one doesn't already exist.

---

### Post by Rustan on 2015-08-31
I have no problems here

---

### Post by lee295012-gmail on 2015-08-31
Seen the same fault in plasma 5.4 on arch.

---

