---
title: "Problems installing Maschine sotware"
date: 2011-06-17
forum: Wine
---

### Post by sangsterthegangster on 2011-06-17
hello, I am trying to install a windows software from a disk onto my ubuntu using wine. But every time I try, the installer will install a few things just fine, but then wine will display a popup box saying "Please insert Maschine Disk." I tried dragging all the folders from the disk to my hard drive but it still did the same thing.

What do i do?
thanks

---

### Post by bobwyajnr on 2011-06-19
Hi

I would strongly recommend reading the [Wine User documentation]("http://www.winehq.org/documentation") and also the [Wine FAQ]("http://wiki.winehq.org/FAQ") (which is argueably a bit dated now). Basically essential reading for advanced Wine usage!

Because your software is commercial and WineHQ AppDB has no entry you will need to "step up to the plate" yourself! I can only help so much as I don't have access to the installer...

I am sure a lot of folks can help out here on the forums... But at the end of the day you will need to run the installer from the commandline, capture the console output and see if you need to file a bug against Wine.

The problem could be caused by copy protection. Also launching a Windows installer, from a mounted CD/DVD, in Nautilus which can cause problems for Wine (since it can get the wrong working path).

It would be worth running (BASH terminal or Gnome menu):
```
winecfg
```
to check the installer DVD/CD is mounted correctly in Wine (look at the drives tab).

Type in a BASH terminal:
```
wine explorer
```
shows a (rather cruddy :D) implementation of Windows explorer developed for ReactOS (and ported to Wine). Just check that you can see all the files on your DVD/CD for Maschine.

That's enough homework for now!! Post back an update and we will take it from there! :popcorn:

Bob

---

