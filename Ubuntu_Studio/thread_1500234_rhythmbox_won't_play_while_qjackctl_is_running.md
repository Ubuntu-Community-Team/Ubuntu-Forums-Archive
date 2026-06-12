---
title: "rhythmbox won't play while qjackctl is running?"
date: 2010-06-02
forum: Ubuntu Studio
---

### Post by asuastrophysics on 2010-06-02
Hi all,

I'm trying to play my electric bass along to some music on rhythmbox. My bass is hooked into the microphone port, and audacity plays what I play on bass out through the speakers. Qjackctl ensures there's no latency delay in audacity's playback.

The problem is, anytime qjackctl is running *at all*, whether it's started or not, rhythmbox won't play anything. I hit play and the slider won't move.

How do I get rhythmbox to play through JACK? 

Thanks in advance!

---

### Post by thorgal on 2010-06-03
can rhythmbox use gstreamer as its audio backend ?
if it can, then I suggest you follow this link:

[http://www.goplexian.com/2010/02/setting-up-jack-audio-for-gstreamer.html](http://www.goplexian.com/2010/02/setting-up-jack-audio-for-gstreamer.html)

There's a paragraph describing how to connect gstreamer to jack. Note that if you go this route, any app using gstreamer as its audio backend (like GNOME system sound ?) will try to use jack. I don't know if failing to find jack working, it can fall back to another sound server (ALSA or pulse).

An alternative, *if you use pulseaudio* when jack is not working, is to load the PA jack modules (sink and source). There are tons of threads and howtos around here, just need a bit of googling.

---

### Post by luctor on 2010-06-03
thq qjackctl is actually a script that halts pulseaudio (pasuspend) and then run qjacktl.bin
So even if you don't start the jack server pulseaudio is suspenden till you quit qjackctl

---

### Post by thorgal on 2010-06-03
you're not kidding ?? is that how this is done on ubuntu ??

---

### Post by luctor on 2010-06-03
> **thorgal said:**
> you're not kidding ?? is that how this is done on ubuntu ??

```
cat /usr/bin/qjackctl
```

---

### Post by cchhrriiss121212 on 2010-06-03
Simple solution: download alsa player from synaptic and set it to use jack audio output.

---

### Post by thorgal on 2010-06-03
or amarok using the xine backend.
But maybe the latest amarok (2.3) is too tied to KDE and phonon ?

---

### Post by sawtdk on 2010-06-03
Just run qjackctl.bin instead of qjackctl, then pulseaudio wont be suspended.

---

