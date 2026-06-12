---
title: "What is an Xrun anyway?"
date: 2009-04-14
forum: Ubuntu Studio
---

### Post by bolex100 on 2009-04-14
There are a few fixes on the forum none of them have worked yet.  Jack says that I still get them ( every 10 seconds or so), but I'll keep trying.
What IS an xrun?.

---

### Post by thorgal on 2009-04-14
it's a buffer under-or-overrun, X stands for under or over. It's a sign that your system did not process some buffers in time, so some data is missed. It is particularly true when you run at very low buffer size where the sound card should process incoming buffers very fast (overrun). Some chips cannot cope with small buffer sizes, so you have to increase the buffer length to ease the work done by the sound chip. 

It could also well be that you are applying way too many software plugins on the audio signal and your CPU cannot keep up with the real time requirement. You will then deliver buffers too late to the audio chip (underrun).

I may be wrong but that's my understanding of the whole shebang.

The jackd options allow you to change the buffer size:

buffer size = number of frames per period x number of periods per buffer. In terms of command line options: buf_size = n x p. So if p = 1024 and n = 2, buf_size = 2048 frames.

---

### Post by bolex100 on 2009-04-14
This is without running any other programs.  only jack!
> loading driver ..
apparent rate = 44100
creating alsa driver ... hw:0|hw:0|128|3|44100|0|0|nomon|swmeter|-|32bit
control device hw:0
configuring for 44100Hz, period = 128 frames (2.9 ms), buffer = 3 periods
ALSA: final selected sample format for capture: 32bit little-endian
ALSA: use 3 periods for capture
ALSA: final selected sample format for playback: 32bit little-endian
ALSA: use 3 periods for playback
15:34:48.531 ALSA connection change.
15:34:50.598 Server configuration saved to "/home/dave/.jackdrc".
15:34:50.599 Statistics reset.
15:34:50.600 Client activated.
15:34:50.603 JACK connection change.
15:34:50.638 JACK connection graph change.
**** alsa_pcm: xrun of at least 1239717882363.904 msecs
15:34:50.662 XRUN callback (1).
15:34:53.109 XRUN callback (2).
**** alsa_pcm: xrun of at least 1239717882363.904 msecs
**** alsa_pcm: xrun of at least 1239717882363.904 msecs
15:34:55.050 XRUN callback (3).
**** alsa_pcm: xrun of at least 1239717882363.904 msecs
15:35:00.918 XRUN callback (4).
**** alsa_pcm: xrun of at least 1239717882363.904 msecs

---

### Post by thorgal on 2009-04-14
no no, you have plenty of other stuff running in the background, you just don't see it. The kernel is doing all sorts of things, the graphics card is busy showing you what you see, your network card sending the message you just typed, etc.

There are other things to consider: IRQ conflicts for example, kernel tuning, CPU speed-stepping, user RT privileges, etc, and I am not talking about a well written driver for your sound card.

Causes for xruns are legions.

I forgot to add: you seem to use an old version of jack, by looking at the estimated time for your xruns :lol:

---

