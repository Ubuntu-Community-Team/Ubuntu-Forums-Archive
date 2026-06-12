---
title: "LMMS produces no sound output"
date: 2010-01-01
forum: Ubuntu Studio
---

### Post by northrup on 2010-01-01
I installed LMMS 0.4.5 on my computer (Ubuntu 9.10), but I'm getting no sound output from the program on ALSA, and whenever I try one of the other options (PulseAudio, OSS, etc.) it reverts to dummy audio.  I tried installing JACK to correct the problem, but JACK seems to be giving errors and quitting, and in the past I've always used ALSA for LMMS and it's worked just fine.

The problem is local to LMMS, even after a reinstall.  My audio output is fine for all other programs I've tested the problem for so far.

What could be causing this issue?

Also, I just noticed that my instances of LMMS are not being terminated after the windows are being closed...

Notable system info:

Ubuntu 9.10 x86 (kernel 2.6.31-16-generic) installed via Wubi
LMMS 0.4.5 (installed via Ubuntu Software Centre)
3.06 GHz Pentium IV (it looks like dual core)
432 MiB RAM
ATI IXP 584x0 High Definition Audio Controller (according to the lshw command)

---

### Post by AutoStatic on 2010-01-02
Hello northrup, PulseAudio already claimed the ALSA backend so if you try to use ALSA as the Audio Interface in LMMS you will not get any sound out of it. You could try setting the Audio Interface on PulseAudio and restart LMMS. Another thing you could try is to open a terminal and do a **aplay -l** to list your soundcards:
```
jeremy@soushi:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

As you can see my soundcard is called 'Intel' (the part after 'card 0:'), if you set ALSA as the Audio Interface in LMMS and in SETTINGS FOR ALSA you put 'hw:Intel' and then quit LMMS you should have sound if you restart LMMS with the command **pasuspender -- lmms** in a terminal. This is just one way to do it but works best for me.
If LMMS is closed unexpectedly the instance of LMMS doesn't get killed properly. I find this very annoying too. A **killall -9 lmms** in a terminal should get rid of all the zombified instances.

---

