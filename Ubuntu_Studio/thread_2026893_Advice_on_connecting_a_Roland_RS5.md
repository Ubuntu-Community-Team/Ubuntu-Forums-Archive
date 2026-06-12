---
title: "Advice on connecting a Roland RS5"
date: 2012-07-15
forum: Ubuntu Studio
---

### Post by gdesilva on 2012-07-15
Hi, I have been using Ubuntu for some time but starting to explore some of the multimedia packages and would like some advice or pointers to get started.

I have a Roland RS5 Synth and an Edirol UM-2. 

There are many packages included in Ubuntu Studio 12.04 and just wondering what would be the easiest and simplest way to connect the Roland via UM-2 so that I can record and playback midi files?

Many thanks

---

### Post by jejeman on 2012-07-16
UM-2 is usb device, so ALSA should recognize it as MIDI device.
You can check right away if it is recognized
```
amidi -l
```

---

### Post by gdesilva on 2012-07-16
@jejeman, no problems with UM-2 - system recognizes it as a midi device. What I am looking for is the simplest and easiest app to play and record midi via RS5. Thanks.

---

### Post by jejeman on 2012-07-16
Okay, first I wanted to be shure that UM-2 is supported.
I don't know about simplest and easiest, but with MusE or Rosegarden you can record and play MIDI. Personaly, I use MusE.

---

### Post by gdesilva on 2012-07-16
Many thanks.

---

