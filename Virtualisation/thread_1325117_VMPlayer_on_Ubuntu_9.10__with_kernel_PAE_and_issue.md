---
title: "VMPlayer on Ubuntu 9.10  with kernel PAE and issue with Module Updater"
date: 2009-11-13
forum: Virtualisation
---

### Post by pi4r0n on 2009-11-13
Hello ALL

I got Ubuntu 9.10 installed on my laptop with latest VMPlayer.

VMPlaer was working perfectly OK with kernel version 2.6.31-14-generic, but today I have updated kernel to version 2.6.31-14-generic-**pae** so that I can have 4 GB of RAM on it 

Unfortunately after that VMPlaer its says

**kernel Header 2.6.31-14-generic-pae not fould**

Any idea how to fix this issue.

Ta

pi4r0n

---

### Post by pi4r0n on 2009-11-13
Managed to find resolution for that :) and it was so simple :)

> sudo apt-get install build-essential linux-headers-`uname -r`

Sorry for unnecessary post

pi4r0n

---

