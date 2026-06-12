---
title: "Interface/Hardware set up for Ubuntu Studio."
date: 2013-01-14
forum: Ubuntu Studio
---

### Post by R3K4CE on 2013-01-14
Beforehand, I would like to mention that I am a Linux beginner. I do however have some years of experience using Ubuntu for regular tasks (web browsing, listening to tunes, etc). Recently I picked up a book on learning how to use the command line and am still learning. With that said, I can follow instructions properly. 
 
I produce electronic music on a Windows machine. Using Fruity Loops, Adobe Audition and a Tascam USB Interface to hook up my keyboard, decks, drum machine and do some recordings. This is the basic set up I use in my room, as I mostly use soft synths and inside the box components. 
 
Since I've been introduced to Ubuntu I instantly fell in love, but I never settled in on deciding to dedicate it to music production. Until recently that is. I bought a Sable Complete system from System 76 with enough specs to handle my duties, I installed Ubuntu Studio on it, and my god was I impressed with the choice of apps haha! I gave away my windows machine with all of the peripherals I had to a good friend of mine who has begun producing music so basically I'm starting from zero on hardware. 
 
I want to know what's compatible/supported by Ubuntu Studio when it comes to outboard hardware, specifically an interface. Either USB or PCI (prefer USB). The specs it would have to meet, very basic. I need to hook up a MIDI controller to it, as well as two mics.

---

### Post by tgalati4 on 2013-01-14
I've always like the older, M-Audio products, like the Delta66 card.  You can find used ones on craigslist.  Decent linux support:

tgalati4@Dell600m-mint14 ~ $ apt-cache search envy
alsa-tools-gui - GUI based ALSA utilities for specific hardware
mudita24 - ALSA GUI control tool for Envy24 (ice1712) soundcards
mudita24-dbg - Debugging symbols for mudita24

---

### Post by Sylos on 2013-01-15
I'll second the call for an M-audio DELTA card. They are nice little units. If you get the regular card then you'll need a couple of pre-amps for the mics. If you can find one with an OMNI breakout box they have a couple of pre-amps built in and will do you proud with no additional expenditure (but they are rare!).

Other than that have a look on the alsa compatability list [http://www.alsa-project.org/main/index.php/Matrix:Main](http://www.alsa-project.org/main/index.php/Matrix:Main)  if its not on the list - be very wary! And have a good look at the notes on what works for each card and what doesnt. Some cards have parial support so not all features will work.

Happy hunting. :D

---

### Post by tgalati4 on 2013-01-15
I have the omni breakout box and it's clean.  Good for semipro recording.  I will not sell it, sorry. (But keep looking!)

---

### Post by cub on 2013-01-16
The Edirol ua25-ex external usb sound card seems to be quite popular.

---

