---
title: "cropping mp3s without recompression?"
date: 2008-06-19
forum: Ubuntu Studio
---

### Post by potiphera on 2008-06-19
Does anyone know if there's any way to crop mp3 files without having to recompress them?  I don't know much about mp3 compression algorithms, so I don't really know if my question even makes sense, as I'm not sure whether recompression of the same material will degrade it further or not.  Thanks!

---

### Post by eye208 on 2008-06-19
> **potiphera said:**
> Does anyone know if there's any way to crop mp3 files without having to recompress them?
You can do that with mp3splt.

---

### Post by potiphera on 2008-06-19
Thanks, it works great!

---

### Post by soxs on 2008-06-21
As far as it goes to logic, recompressing shouldn't hurt quality at all, as .mp3 cuts all frequencies out, which are not hearable for human beings, so if they are onece removed, you will not get quality loss in the respect of frequenzy range. About simple compressing algorithms,.. I do nt really know about that..

---

### Post by portach king on 2008-06-21
How do you install mp3splt-gtk under Hardy?

---

### Post by eye208 on 2008-06-22
> **soxs said:**
> As far as it goes to logic, recompressing shouldn't hurt quality at all, as .mp3 cuts all frequencies out, which are not hearable for human beings, so if they are onece removed, you will not get quality loss in the respect of frequenzy range. About simple compressing algorithms,.. I do nt really know about that..
MP3 encoding does not only remove frequencies. It introduces new frequencies as well. These are called artifacts. Whether you hear them or not depends on the bitrate and your ears. It's true that there are lossy compression schemes that do not degrade a signal any further as long as the same quantizer is used during recompression, but MP3 isn't one of them.

To find out what MP3 encoding adds to a signal, run this simple test with LAME and Audacity:

Make a new folder and copy some WAV file into it. Name the file audio1.wav, then run the following commands:

lame --preset insane audio1.wav audio1.mp3
lame --decode audio1.mp3 audio2.wav
lame --preset insane audio2.wav audio2.mp3
lame --decode audio2.mp3 audio3.wav
lame --preset insane audio3.wav audio3.mp3
lame --decode audio3.mp3 audio4.wav
lame --preset insane audio4.wav audio4.mp3

Now run Audacity and do the following:

File > Import > Audio. Select "audio4.mp3".
Edit > Select > All.
Effect > Invert.
File > Import > Audio. Select "audio3.mp3".
Edit > Select > All.
Tracks > Mix and Render.
Edit > Select > All.
Effect > Normalize.

What you can see and hear now is the generation loss between the 3rd and 4th generation. Note that we used LAME's "insane" preset (320kbps) each time. This is the best quality setting that LAME has to offer. Also note that LAME is considered the best MP3 encoder of all.

The results show that MP3 encoding introduces new artifacts with each generation. These will add up and become audible at some point which depends on encoding quality. At low bitrates artifacts can be heard right after the 1st generation.

---

