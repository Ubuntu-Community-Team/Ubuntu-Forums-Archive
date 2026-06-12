---
title: "iPhone deb packages"
date: 2011-04-15
forum: The Cafe
---

### Post by CJay554 on 2011-04-15
Anyone know what the difference is between a iphone deb package and lets say ubuntu debs? I pressume it would be dependencies and other things, all i know is iphone debs can be handled on the device itself through ssh..

---

### Post by stealth. on 2011-04-15
> **CJay554 said:**
> Anyone know what the difference is between a iphone deb package and lets say ubuntu debs? I pressume it would be dependencies and other things, all i know is iphone debs can be handled on the device itself through ssh..


Like on a jailbroken iphone? Nothing AFAIK, login as root and type apt-get update && apt-get upgrade (If you have mobile terminal installed)

I think Cydia uses Debians package manger

---

### Post by doorknob60 on 2011-04-15
DEBs are basically just arhives (like .tar.gz and .zip) with compiled software inside it. Ubuntu debs are compiled for Linux on the x86 (or x86_64) architecture with all the libraries used by Ubuntu. iPhone debs are compiled for Darwin on the ARM architecture, using proprietary libraries only found on iPhones. The sructure of the files and how you work with them is the same, but obviously the binaries inside them won't work on platforms they weren't designed for. I know jailbroken iPhones use many of the same utilities for handling debs, such as dpkg and (I'm pretty sure) apt-get, though Cydia is the main way of handling them.

---

### Post by earthpigg on 2011-04-15
neat. i didn't know any of this.

---

