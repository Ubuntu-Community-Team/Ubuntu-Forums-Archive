---
title: "Need a way to backup ubuntu servers and restore"
date: 2010-12-07
forum: Server Platforms
---

### Post by egandt on 2010-12-07
My current method of using Acronis does not work as the UUID is broken upon restore and then I can do nothing (95% of my restores are due to drive failures), I need a backup solution preferable free (as I've already spent $700 per server on Acronis which is not working) to backup and restore Ubuntu servers 100% of the time after boot drive failures.  An attempt by me to use traballs has failed (which annoys me greatly, by the way as it works for RH5 and SuSE10), but with Ubuntu it does does not work and the down time of reconstructing the install is to long.

Ideas?
ERIC

---

### Post by CharlesA on 2010-12-07
I use clonezilla to make an image of my Ubuntu installs, works like a charm.

The only hitch you'll run into is that you'll need to boot off a livecd to image the machine.

---

### Post by HermanAB on 2010-12-08
Howdy,

The better way to handle servers is to virtualize them.  That ensures that the server function is hardware independent and can be copied to and run on anything.

---

