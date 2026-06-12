---
title: "No sound coming from speakers when using JACK"
date: 2011-10-26
forum: Ubuntu Studio
---

### Post by Tallguitarguy on 2011-10-26
I finally setup JACK, at least well enough to get a visible signal in Ardour and Rakarrack, but the problem is I cannot hear any sound from them. If you would like a screenshot of anything on qjackctl, please just say which thing and I will post it. Also, I know my mic works with audacity. Any help would be greatly appreciated.
Details: Dell Inspiron 1501, Alesis LineLink USB cable, Shure sm57, Ubuntu 11.04.

---

### Post by jejeman on 2011-10-26
I supose that you have connected all in qjackctl. Maybe you choose wrong card for playback.
give us the output from
```
aplay -l
```

---

### Post by sgx on 2011-10-26
> **Tallguitarguy said:**
> I finally setup JACK, at least well enough to get a visible signal in Ardour and Rakarrack, but the problem is I cannot hear any sound from them. If you would like a screenshot of anything on qjackctl, please just say which thing and I will post it. Also, I know my mic works with audacity. Any help would be greatly appreciated.
Details: Dell Inspiron 1501, Alesis LineLink USB cable, Shure sm57, Ubuntu 11.04.
Hi the 4th and 8th (last) links have qjackctl screenshots and
configuration info.

[http://en.wikipedia.org/wiki/Qjackctl](http://en.wikipedia.org/wiki/Qjackctl)

Youtube videos about ardour, hydrogen, zynaddsubfx,
and ubuntu studio often start with connections in qjackctl.
Cheers

---

### Post by Tallguitarguy on 2011-10-27
**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: default [C-Media USB Audio Device   ], device 0: USB Audio [USB Audio]
  Subdevices: 0/1
  Subdevice #0: subdevice #0

I know it's not C-media, because that is my microphone. If I select STAC92XX... as my output device, (instead of default), then JACK will not start.

---

### Post by Tallguitarguy on 2011-10-27
here's a screenshot of my current setup anyway.

---

### Post by sgx on 2011-10-27
Try these in qjackctl

Frames/Period  512
Periods/Buffer 3
un-select Force 16bit, and Hardware Monitor

Choose your devices by clicking the  > widgets in

Input Device >
Output Device >

Interface > choose default

Cheers

---

