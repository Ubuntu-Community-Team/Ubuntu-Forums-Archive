---
title: "nullsoft video"
date: 2009-01-11
forum: Ubuntu Studio
---

### Post by rfrayer on 2009-01-11
hello im not sure if i posted in the right area but here goes anyways. I installed winamp via wine and it works fairly flawless with shoutcast dsp etc.

what im trying to figure out is if there is a way to convert some videos i have intil nsv format to stream them.

---

### Post by rylleman on 2009-01-12
My ffmpeg claims to support the nsv format so it should probably be as easy as "ffmpeg -i input_file.end output_file.nsv".

---

### Post by FakeOutdoorsman on 2009-01-12
NSV can be decoded by ffmpeg (vp3 video, mp3 audio), but it can't encode it:
```
ffmpeg -formats | grep nsv
D  nsv             NullSoft Video format
ffmpeg -formats | grep vp3
D V    vp3
```
The "D" indicates that the format/codec can be decoded.  An "E" would indicate encoding ability.

---

### Post by rylleman on 2009-01-14
Oh, sorry. Just ignore my answer then.

---

