---
title: "Merge multiple wav files"
date: 2009-01-28
forum: Ubuntu Studio
---

### Post by Dr Small on 2009-01-28
I have about 4 big wav files that I want to merge into one big file as a wav. I've tried piping the input of each file with cat into the stdout as one file. It merged them together alright, but VLC only plays up to the end of the first merge.

Is there any other way to do this? I could just take them into Audacity and input individual tracks, but I wanted to find a simpler way to do this from the command line.

Dr Small

---

### Post by Stochastic on 2009-01-28
Sox is probably the tool you want to use, if memory serves correct the command should look like ```
sox input1.wav input2.wav input3.wav output.wav
```
but Sox's man page will explain it better.

Ecasound will also work if you have troubles with sox.

---

### Post by Dr Small on 2009-01-29
Thanks! Sox was exactly what I needed. I couldn't get it to install on Arch (it was conflicting with ffmpeg-svn) so I installed it on my server, copied the audio files there, and merged them into one. It worked swell!

From there, I converted the wav file to ogg (since it was 1.2GB) and that helped cut the size down considerably, to about 330MBs. Thanks for your help.

:)

Dr Small

---

