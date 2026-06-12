---
title: "I think I've made a breakthrough!"
date: 2006-10-09
forum: The Cafe
---

### Post by alecjw on 2006-10-09
Anyone here at their wit's end with Annoying Audio Coding (AAC)? Fed up of having to use MP3 instead for your iPod because sound juicer can't encode AAC?

I think I've found a solution.Nero offer free command line AAC encoding utilities for windows here: [http://www.nero.com/nerodigital/eng/Nero_Digital_Audio.html](http://www.nero.com/nerodigital/eng/Nero_Digital_Audio.html)

Presumably we could make a gstreamer pipelinee by running neroAacEnc.exe under wine? Unfortunately, I know nothing about gstramer pipelines. Can anyone help me?

---

### Post by .t. on 2006-10-09
Or... you could install RockBox and use Ogg! That's not very helpful, I know...

---

### Post by darkhatter on 2006-10-09
then I could upload all those oggs on my ipod and look at it all day.

---

### Post by .t. on 2006-10-10
Or... have RockBox play them...

---

### Post by alecjw on 2006-10-10
> **.t. said:**
> Or... have RockBox play them...

As far as I know, there is no audio support for 5g iPods. Or TV-out. Or OGG theora.

So is there any way of making a gstreamer plugin from this program?

---

### Post by darkhatter on 2006-10-10
I have ipod Linux on right now, I use it to watch my "The Office US" episodes.

---

### Post by alecjw on 2006-10-10
> **darkhatter said:**
> I have ipod Linux on right now, I use it to watch my "The Office US" episodes.

iPod linux doesn't work on 5g either.

---

### Post by DoctorMO on 2006-10-10
yet...

it's only a matter of tine before it's supported. although I hear odd vorbis drains the batteries some what because it uses floating point maths; this also means it won't work on some basic mp3 players simply because of the cpus being used in them.

---

### Post by alecjw on 2006-10-10
But would it be possible to make an audio codec with the program? Can somone explain how to make gstreamer pipelines?

---

### Post by alecjw on 2006-10-10
Do you guys think that this could be right?:
```
audio/x-raw-int,rate=44100,channels=2 ! wine "C:\Program Files\path_to_encoder.exe"
```

---

### Post by alecjw on 2006-10-11
Hello? Anyone know if that's right?

---

