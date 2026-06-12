---
title: "How to compress an mp3 for playback on my phone"
date: 2009-12-22
forum: The Cafe
---

### Post by Yvan300 on 2009-12-22
Ok so i've been reading around and i wish to know what properties i should change so that the mp3 is compressed and it still plays on my phone pretty well. I read that since it is a small speaker you could set the output to mono because you won't see a difference. Any other ideas?

---

### Post by koleoptero on 2009-12-22
Start lowering the bitrate and stop when you see you've reached your limit. If you'll be listening from the phones speaker then 64kbit will be more than enough. If it can play mp4 files then use mp4.

---

### Post by pwnst*r on 2009-12-22
use audacity and change to mono. change bitrates depending on how crappy you can/can't stand it.

---

### Post by garryknight on 2009-12-22
I use lame for this. Two examples:

Downsample to 32-bit stereo (assuming original is stereo)
lame -b 32 tune.mp3 tune-resampled.mp3

Downsample to 32-bit and output as mono
lame -a -b 32 tune.mp3 tune-resampled.mp3

---

### Post by Groucho Marxist on 2009-12-22
> **Yvan300 said:**
> Ok so i've been reading around and i wish to know what properties i should change so that the mp3 is compressed and it still plays on my phone pretty well. I read that since it is a small speaker you could set the output to mono because you won't see a difference. Any other ideas?

MP3 files are already compressed; you would be compressing a compression, with the resultant audio sounding terrible. Furthermore, you will most definitely hear a difference between mono and stereophonic modes on such a file.

---

### Post by Yvan300 on 2009-12-22
Ah i see, i guess i'll just get a memory stick, btw do high capacity memory sticks slow down your phone?

---

### Post by Gizenshya on 2009-12-22
^^^ no.  Just make sure whatever size you get is supported by your phone.  Most of them are MicroSD cards.  Regular ones go up to 2GB, but MicroSD-HC (which stands for High-Capacity) are in sizes over 4GB.  All MicroSD cards do work in MicroSD-HC devices... but no MicroSD-HC cards work in Micro-SD devices.

koleoptero's method is probably the best.  It is what I do.  Finding the file-size, bitrate, stereo/mono, file format, and any other requirements are basically impossible to find.  I've tried with my phone, and with others.  For all of them, I had to use trial and error to get them in the right size and format.

Ringtones usually have different requirements for any given phone.  Where my phone plays basically any MP3 (even some over an hour), my ringtone can only be below a certain filesize or time length (most are 20-25 seconds).  Maybe a combination of both, actually... but I still haven't figured it out the limits exactly.  Customer support just sits and stutters, they have no idea... even though they designed the phones.  Ugh! lol

---

### Post by pwnst*r on 2009-12-22
> **Groucho Marxist said:**
> Furthermore, you will most definitely hear a difference between mono and stereophonic modes on such a file.

no you won't. it's going to be played back on a shitty phone speaker which is typically mono anyway.  no need for two channels and a resulting larger file.

---

### Post by koleoptero on 2009-12-22
> **Yvan300 said:**
> Ah i see, i guess i'll just get a memory stick, btw do high capacity memory sticks slow down your phone?

That actually happened to me with a sony ericsson w350i, that supports 4GB m2 micro memory sticks, but when I used one it was not as responsive as without (not to mention it took ~5 minutes to turn on). But with other phones I had no such problem.

---

### Post by Yvan300 on 2009-12-22
Ah i see, hope it doesn't happen to me, oh and does anyone know why the phone slows down in these situations?

---

