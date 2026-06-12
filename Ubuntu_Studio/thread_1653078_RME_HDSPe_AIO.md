---
title: "RME HDSPe AIO"
date: 2010-12-26
forum: Ubuntu Studio
---

### Post by solo16 on 2010-12-26
Hi,

Anyone has successfully playing songs with Hdspe AIO under Ubuntu Studio 10.10? Using the alsamixer to config my card however i couldn't see any output selection, it only has the input preference and only have two options, coaxial or optical. However i'm only using AES output to my DAC only but in the alsamixer there is no option for output or aes. It works perfectly on windows, so the card is not defected.

i used aplay -l and it shows my card as HDSPM MADI, not AIO.
also i used, cat /proc/asound/card0/hdspm, it shows nothing about any kind of output information. 

So, is AIO supported by Alsa? And is that possible to be the firmware problem since i never upgrade the firmware since i bought the card? 

Cheers!

---

### Post by cchhrriiss121212 on 2010-12-26
According to [this page]("http://www.spinics.net/linux/fedora/alsa-user/msg09549.html"), it is not fully supported:
> > i would like to run a rme hdspe aio on linux,
> is the Card supported ?

Not fully yet, only 1024 period operation for the moment.This dates from only a few months ago so I doubt much has changed. You can check the [ALSA database]("http://www.alsa-project.org/main/index.php/Matrix:Main") for supported cards.

---

### Post by solo16 on 2010-12-27
Thx!!!!

---

### Post by solo16 on 2010-12-29
Ok i've been googling around and seems like in order to get the AIO works, the new hdspe driver need to be installed, but i'm really a newbie to linux. So is anyone could show me step by step of how to install it?

Any help is greatly appreciated!!! Thanks in advance!!!

---

### Post by obuben on 2010-12-30
Hi, 
I have the same problem with installing the driver and the mixer.
Anybody help us !

disable the snd_hdspm module is this below ?
"sudo modprobe -r snd_hdspm"

---

### Post by cchhrriiss121212 on 2010-12-30
If you link to the driver you are talking about, someone might be able to suggest how to install.

---

