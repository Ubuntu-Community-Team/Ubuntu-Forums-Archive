---
title: "How to record audio clip from video files?"
date: 2009-04-19
forum: Ubuntu Studio
---

### Post by Dusenberg on 2009-04-19
Hi,
Does anyone know how I can record audio clips from .wmv, .ram and other video formats?  I've tried Sound Recorder and Audacity but they don't seem to have the facility. I just want to play the vid in MoviePlayer and click 'record' in another package and pick up the vid sound track.

---

### Post by SuperSonic4 on 2009-04-19
You could use an ffmpeg script to do an audio rip of the video

---

### Post by Dusenberg on 2009-04-19
> **SuperSonic4 said:**
> You could use an ffmpeg script to do an audio rip of the video

Thanks SuperSonic4 - but that's a bit beyond me, however I'm willing to learn! Can you suggest a ffmpeg package I could use to do this?

---

### Post by Dusenberg on 2009-04-19
DONE IT! 

After using my brain (!) I installed ffmpeg (what else...) and using this code extracted the audio stream.

```
ffmpeg -i <inputfile> -vn -acodec libmp3lame <outputfile>.mp3
```

Thanks again SuperSonic4 :D

---

### Post by andrew.46 on 2009-04-19
Hi Dusenberg,

> **Dusenberg said:**
> DONE IT! 

After using my brain (!) I installed ffmpeg (what else...) and using this code extracted the audio stream.

```
ffmpeg -i <inputfile> -vn -acodec libmp3lame <outputfile>.mp3
```


Good on you for working it all out :-). The only fine tuning that might be required is that I believe the default bitrate for encoding with FFmpeg and libmp3lame is quite low at 64kb/s so you might be best to add something like -ab 128k to your string. Depends a little on the quality of the input sound and the quality of your ears :-).

All the best,

Andrew

---

