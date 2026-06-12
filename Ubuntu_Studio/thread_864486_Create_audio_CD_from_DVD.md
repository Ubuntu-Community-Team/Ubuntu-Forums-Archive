---
title: "Create audio CD from DVD"
date: 2008-07-19
forum: Ubuntu Studio
---

### Post by jws957 on 2008-07-19
How can I create an audio CD from a DVD?  I can rip an avi or mpg file using acidrip.  I am pretty sure K3b will create an audio CD once I can convert the avi file to a wave file.  There are LOTS of free programs on windows to do this, but I want to use linux.  Presently running Gutsy.

---

### Post by arsenic23 on 2008-07-19
I'd just use ffmpeg.

```
ffmpeg -i yourmoviefile output.wav
```

---

### Post by cotcot on 2008-07-20
Avidemux.
Load the avi. Save audio only using --> Audio --> Save after having set the frequency to 44100 in --> Audio --> Filters --> Resampling.

---

### Post by angelsguitar on 2008-07-20
I not sure if I'm hijacking this thread (moderators please move this post to a different thread if I am, and sorry for that), but I have a very similar question.  Is there a way to rip the audio directly from a DVD, without converting it to a video format first? Maybe using ffmpeg?

---

### Post by alegallo on 2008-07-21
Well, a DVD movie already IS in a video format, so you'll have to open it with some kind of program to do what you need.

The matter is that the DVD structure does not allow you to open its files directly from the disc (or so I guess), therefore you'll have to rip it to your HD and then to do all needed operations.

---

### Post by angelsguitar on 2008-07-21
> **alegallo said:**
> Well, a DVD movie already IS in a video format
...

Well, yes, you are right.  What I mean is to rip the audio from the DVD directly, without having to rip it to another video format then rip again from that file to an audio format.

---

### Post by alegallo on 2008-07-23
Just rip the VOBs and you'll be fine. ;)

Ripping them you don't transcode anything (well, as far as I know), you just "translate" them in an "understandable" container for your PC, but the contents still remain an mpeg-2 file.
Then you can open them and extract the audio part.

---

### Post by thorgal on 2008-07-23
play the DVD section you want through jackd ;) and reroute the output to audacity or ardour. Export the recorded sound to wav, burn your CD.

---

