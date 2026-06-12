---
title: "lmms audio in recordmydesktop"
date: 2008-07-14
forum: Ubuntu Studio
---

### Post by neu2buntu on 2008-07-14
hi.every1!.. love ubuntu by the way (think il kill off windows)

heres the prob..i have been making videos of tunes ive made in lmms(using alsa through wine) on gtk-record my desktop ,but the audio it records in on my external laptop mic, i wish to record the audio as digital but i dont know how to or what to type in record my desktop.. (hw:0 is my ext mic)

id be well happy if any1 can help cheers

---

### Post by Stochastic on 2008-07-15
You may find it easiest to record the music into a wave editor (through Jack) or even just do a audio mixdown export (if lmms has that ability - I'm not an lmms user), then taking the video you've grabbed through recordmydesktop and pasting the audio file in as a soundtrack with a tool like ffmpeg, or a video editor.

---

### Post by neu2buntu on 2008-11-07
> **chrissy.mc.1@hotmail.co.u said:**
> hi.every1!.. love ubuntu by the way (think il kill off windows)

heres the prob..i have been making videos of tunes ive made in lmms(using alsa through wine) on gtk-record my desktop ,but the audio it records in on my external laptop mic, i wish to record the audio as digital but i dont know how to or what to type in record my desktop.. (hw:0 is my ext mic)

id be well happy if any1 can help cheers
solved my prob (some time later).. got it working using qjackctl(gui for jackd)  and a lot of googling on how to set it up properly,but as always all the info is out there you just have to find it...

---

