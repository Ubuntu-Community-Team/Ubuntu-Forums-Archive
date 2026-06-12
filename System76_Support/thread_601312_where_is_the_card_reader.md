---
title: "where is the card reader?"
date: 2007-11-03
forum: System76 Support
---

### Post by muzcuk on 2007-11-03
I have a daru2 (or something identical, at least) and I hear that card reader works just fine with gutsy..

Well, I have gutsy and the card reader and they don't seem to work, in fact, gutsy knows all about my card reader (I can see it in lspci and it is recognized as a card reader) but nothing happens when I stick in a card (no automount) and because I don't know where the reader is (/dev/?) I can't mount 't myself.. What to do..? If only I knew where the device is, I believe I could handle the rest.. How do I figure that out?

Hence the lspci out, the funny thing is my card reader supports mmc, sd and ms, I don't think it supports SM or Xd (or does it?), I don't have any xd or sm cards to try by the way, I'm not even sure what they look like, there is only one slot in the card reader. 

01:04.0 FLASH memory: ENE Technology Inc ENE PCI Memory Stick Card Reader Controller
01:04.1 Generic system peripheral [0805]: ENE Technology Inc ENE PCI SmartMedia / xD Card Reader Controller
01:04.2 FLASH memory: ENE Technology Inc Unknown device 0720
01:04.3 FLASH memory: ENE Technology Inc ENE PCI Secure Digital / MMC Card Reader Controller

---

### Post by palintheus on 2007-11-04
Huh, mine automounted just fine with a  vanilla Gutsy install. Did you upgrade from Feisty or do a fresh-install? I have only tested with an SD card.

---

### Post by tedrampart on 2007-11-04
I think it only support 4 formats .. I can't remember which, but I've only used SD, and a sony card (which wasn't supported).. it could be that the card you're trying to use is one that isn't supported..

if you can get a hold of an SD card (which SHOULD work), then you might be able to see where its mounting it, and compare..

in my logs  see /dev/mmcblk0p1 gets mounted to /media/disk if that helps (its on a gazelle though, but I don't think it'd be much different)..

---

### Post by thomasaaron on 2007-11-05
We've run into this in tech support on a few occasions. If it was formatted by a palm device, it probably will not work. And there are some other incompatible formats.

You can format it using gparted.
sudo apt-get install gparted

then...

System > Administration > Gnome Partition Manager

---

