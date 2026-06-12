---
title: "[SOLVED] dvd-slideshow error"
date: 2008-07-05
forum: Ubuntu Studio
---

### Post by King_Critter on 2008-07-05
When I run dvd-slideshow, at first everything seems like it's working -- it renders the crossfades without complaint, anyway -- but then it errors out.

Here's the end of the log, where it starts to go screwy:

```
[dvd-slideshow] waiting for mpeg2enc to finish...
[dvd-slideshow]#####################################
[dvd-slideshow] No audio files passed.  Using 0:1:38.098 silence.
[dvd-slideshow] Working on track 1 audio file 0
[dvd-slideshow] silence
[dvd-slideshow] Creating silence audio file for 0:1:38.098
sox soxio: Failed reading `/dev/zero': unknown file type `raw'
[dvd-slideshow] This audio plays in slideshow from 0:0:0.000 to 0:1:38.098
[dvd-slideshow] ###############
[dvd-slideshow] Concatenating all audio files...
cat: /home/critter/photos/church-camp/monday/dvd-slideshow_temp_7522/audio1_????.raw: No such file or directory
sox soxio: Failed reading `-': unknown file type `raw'
[dvd-slideshow] Creating ac3 audio...
[dvd-slideshow] ERROR during ffmpeg execution!
[dvd-slideshow] see /home/critter/photos/church-camp/monday/dvd-slideshow.log for details
[dvd-slideshow] cleanup...
```

It kinda looks like it has something to do with the audio, so I tried adding a sound track to it. No luck -- it did the exact same thing.

Any ideas?

---

### Post by Creative2 on 2008-07-06
hello... you should search in this forum dvd-slideshow issue has many topics...

 there is a problem into dvd-slide ...so i am a bit lazy and i will write this link

your solution can be found here:

[http://fuocotools.byethost13.com/index.php?topic=90.0](http://fuocotools.byethost13.com/index.php?topic=90.0)




bye

---

