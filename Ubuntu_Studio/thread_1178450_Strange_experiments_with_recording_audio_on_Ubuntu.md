---
title: "Strange experiments with recording audio on Ubuntu 9.04 (ALSA vs. OSS)"
date: 2009-06-04
forum: Ubuntu Studio
---

### Post by igorzwx on 2009-06-04
Strange experiments with recording audio on Ubuntu 9.04 (ALSA vs. OSS)

In short, if you record on PC from iMic USB, 
ALSA and OSS seem to produce similar quality (normal quality)

$ sudo apt-get install bplay

$ brec -d /dev/audio1 -S -s 44100 -b 16 -w mumu-alsa-usb.wav

$ brec -d /dev/dsp1 -S -s 44100 -b 16 -w mumu-oss-usb.wav

Test was performed on an old PC (Terra, 2001)

However, the best quality is achieved when recording on notebook
(running on accu) from iMic USB (excellent quality).

But what is really strange it that recording from ALSA on notebook
produces very bad quality
(IBM ThinkPad R40 of 2003 - Ubuntu 9.04, Dell notebook of 2008 - Ubuntu 8.04)

Very strange!

I have no idea...

see also:
[http://n2.nabble.com/How-to-record-sound-on-Ubuntu-8.04%2C-8.10%2C-9.04-tp2988982p2988982.html](http://n2.nabble.com/How-to-record-sound-on-Ubuntu-8.04%2C-8.10%2C-9.04-tp2988982p2988982.html)

---

