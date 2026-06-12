---
title: "Extract sound from .avi?"
date: 2006-04-25
forum: The Cafe
---

### Post by Kimm on 2006-04-25
I have a song that I want to extract from an AVI movie (downloaded from video.google.com)

I mainly just want to ask a friend that speaks japanese what they are singing xD

Is there any way of doing this? Any help apretiatet

PS.
Tried VLC... but it insists on including the video -.-

---

### Post by GeneralZod on 2006-04-25
avidemux2 has an option to dump out the raw audio stream.

---

### Post by adamkane on 2006-04-25
Open avidemux.

Rebuild index, if asked.

Audio -> Save.

---

### Post by Kimm on 2006-04-27
Thanks, avidemux worked wounderfully! ^^

---

### Post by be4truth on 2008-08-06
Thanks, avidemux worked wounderfully for me too. No Thanks button here...:(

---

### Post by init1 on 2008-08-06
It's a lot easier to use ffmpeg
```

ffmpeg -i youvideo.avi thesoundyouwant.mp3

```
Note that unless you've installed the Medibuntu version, you'll get mp2, rather than mp3.

---

### Post by FakeOutdoorsman on 2008-08-07
ffmpeg can also be used to copy the audio stream without re-encoding:
```
ffmpeg -i input.flv -acodec copy output.mp3
```
If you want to know the audio codec of the original file:
```
[frink@hedron ~]$ ffmpeg -i input.flv
Stream #0.1: Audio: mp3, 22050 Hz, mono, s16, 56 kb/s
```

---

### Post by wilsonmuse on 2008-08-07
for mplayer users:

```

mplayer -dumpaudio video.file -dumpfile output.mp3

```

---

### Post by LookTJ on 2008-08-07
ffmpeg:

```
ffmpeg -i file.avi -vn -acodec mp3 file.mp3
```

fixed!

---

### Post by FakeOutdoorsman on 2008-08-07
> **Taylor said:**
> ffmpeg:

```
ffmpeg -i file.avi -vn -acodec mp3 -o file.mp3
```
"-o" is not an option in ffmpeg and will create an error.

---

### Post by LookTJ on 2008-08-07
> **FakeOutdoorsman said:**
> "-o" is not an option in ffmpeg and will create an error.
Sorry the "-o" isn't supposed to be there. :)

---

### Post by altima on 2012-01-31
the "ffmpeg -i input.avi -acodec copy output.mp3" command worked just fine. thank you!
but my AVI contains several audio tracks, and with this command only the first one gets extracted. how do I modify the command to extract a certain track (I need he last one).


```
 Stream #0.0: Video: mpeg4, yuv420p, 704x400 [PAR 1:1 DAR 44:25], 25 tbr, 25 tbn, 25 tbc
    Stream #0.1: Audio: ac3, 48000 Hz, stereo, s16, 192 kb/s
    Stream #0.2: Audio: ac3, 48000 Hz, stereo, s16, 192 kb/s
    Stream #0.3: Audio: ac3, 48000 Hz, stereo, s16, 192 kb/s
    Stream #0.4: Audio: ac3, 48000 Hz, stereo, s16, 192 kb/s

```

---

### Post by nothingspecial on 2012-01-31
Please don't bump ancient threads to the top.

Make a new one of your own.

Closed.

---

