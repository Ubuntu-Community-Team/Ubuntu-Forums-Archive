---
title: "did shotwell lock my sim card - can't take pictures anymore?"
date: 2013-09-10
forum: Ubuntu Development Version
---

### Post by miobrad on 2013-09-10
dear forum,
i used shotwell to load a view pictures from my sim card (through my sim card reader on my thinkpad x201i).
today i tried to take more pictures but found that it is protected, the camera can't do anything about it, it seems.
i tried formatting it with gparted, but that also failed, with a 'can't format read only filesystem' error message.
thanks for any hints/comments!!!

---

### Post by dragynbane222 on 2013-09-10
okay, 2 things are wrong and most likely due to misinformation:
1. what you're regarding as a SIM card is actually a Secure Digital (SD) card, SIM cards only have enough room for phone account info, and a few numbers, that's it, no room for photos.
2. you can't lock an SD card with software, that's a mechanism controlled ONLY by a visible switch on the card itself, Shotwell can't lock an SD card

what you're likely seeing is a corrupt/bad SD card and/or filesystem (or both)

---

### Post by miobrad on 2013-09-11
alright, you are right, sorry for getting the name wrong, thanks for the clarification. also - you are right about that switch. it was by coincidence that it moved/locked the card the first time i plugged it into my laptop after installing 13.10. thanks!!
this is solved and should not be even in this thread..

---

