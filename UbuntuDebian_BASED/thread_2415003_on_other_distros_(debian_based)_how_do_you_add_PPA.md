---
title: "on other distros (debian based) how do you add PPA repositories?"
date: 2019-03-18
forum: Ubuntu/Debian BASED
---

### Post by jebi on 2019-03-18
hi

on other distros (debian based) how do you add PPA repositories

PPA repositories i think are the apps available to download via the store and apt-get / apt?

could someone tell me all the methods, /etc/something file breaks some releases..

also what are the app repositories for all extras in ubuntu?


i do not need ubuntu os update repositories


thx

---

### Post by Frogs Hair on 2019-03-18
A personal package archive (PPA) is usually created an individual or group of users for different reasons including app development,testing,or out of need. Even if you download a .deb package from PPA archive page which is possible when only one package is needed it may cause dependency problems in other Debian based distributions. The restricted and Canonical partners repositories are for 3rd party applications and codecs. 

There are also snap and flatpack applications available that are intended to run on different distros. Adding official repositories from another distribution will likely lead to a broken package system and update problems as well.

---

### Post by Frogs Hair on 2019-03-18
Moved to *Ubuntu Debian Based*.

---

