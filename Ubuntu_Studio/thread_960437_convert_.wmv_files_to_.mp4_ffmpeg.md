---
title: "convert .wmv files to .mp4 ffmpeg"
date: 2008-10-27
forum: Ubuntu Studio
---

### Post by KanineN on 2008-10-27
Hello! When I am trying to convert a .wmv file with ffmpeg i get this error message


```
Seems stream 1 codec frame rate differs from container frame rate: 1000.00 (1000/1) -> 30.00 (30/1)
Input #0, asf, from 'msm1136_widescreen.wmv':
  Duration: 00:18:24.3, start: 4.000000, bitrate: 1158 kb/s
    Stream #0.0: Audio: wmav2, 48000 Hz, stereo, 128 kb/s
    Stream #0.1: Video: wmv3, yuv420p, 854x480 [PAR 0:1 DAR 0:1], 1024 kb/s, 30.00 tb(r)
File 'msm1136.mp4' already exists. Overwrite ? [y/N] y
Output #0, mp4, to 'msm1136.mp4':
    Stream #0.0: Video: 0x0000, yuv420p, 854x480 [PAR 0:1 DAR 0:1], q=2-31, 200 kb/s, 30.00 tb(c)
    Stream #0.1: Audio: 0x0000, 48000 Hz, stereo, 64 kb/s
Stream mapping:
  Stream #0.1 -> #0.0
  Stream #0.0 -> #0.1
Unsupported codec for output stream #0.0
```


looks like I have to install a codec, where can I find it?

---

### Post by FakeOutdoorsman on 2008-10-27
Post the complete ffmpeg command and the full ffmpeg output.  What version of Ubuntu are you using?

---

### Post by nowardev on 2008-10-27
Unsupported codec for output stream #0.0

-------> ffmppeg is not from medibuntu

---

