---
title: "lunar: cups driver 32bit"
date: 2023-01-19
forum: Ubuntu Development Version
---

### Post by MyMurry on 2023-01-19
Hello,

how can I install old 32bit printer driver? The old way doesn't work anymore.

[https://www.support.xerox.com/en-us/product/phaser-6000/downloads?language=en](https://www.support.xerox.com/en-us/product/phaser-6000/downloads?language=en)

Regrads,

Norbert

---

### Post by MyMurry on 2023-01-19
I got it running:

sudo dpkg --add-architecture i386
sudo apt-get update
sudo apt-get install libc6:i386 libncurses5:i386 libstdc++6:i386 libcupsimage2:i386
sudo dpkg -i xerox-phaser-6000-6010_1.0-1_i386.deb

---

