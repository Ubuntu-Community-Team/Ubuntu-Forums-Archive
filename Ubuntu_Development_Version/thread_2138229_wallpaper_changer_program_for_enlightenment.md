---
title: "wallpaper changer program for enlightenment"
date: 2013-04-23
forum: Ubuntu Development Version
---

### Post by rburkartjo on 2013-04-23
anyone know of one that will work. i have tried a bunch and none seem to work. also no luck googling . no big deal

---

### Post by Frogs Hair on 2013-04-23
The E17 packages in the repository are missing modules, so unless you install an svn ppa you have a very bare-bones version of E17 that is missing many functions . Check the modules menu and enable it if it is installed . If you choose to  use a PPA be sure to remove all repository packages and the .e configuration folder in hidden folders or you will end up with broken packages.

Bleeding edge with all modules :[https://launchpad.net/~hannes-janetzek/+archive/enlightenment-svn](https://launchpad.net/~hannes-janetzek/+archive/enlightenment-svn)   (13.04 ?)

Stable with limited function and more up to date : [https://launchpad.net/~efl/+archive/trunk](https://launchpad.net/~efl/+archive/trunk)

I used the first PPA on 12.10 and once installed the modules for weather and so on can be located and installed from synaptic.

---

### Post by rburkartjo on 2013-04-23
frog tks

---

