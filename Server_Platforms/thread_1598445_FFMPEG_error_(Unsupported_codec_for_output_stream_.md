---
title: "FFMPEG error (Unsupported codec for output stream #0.0)"
date: 2010-10-16
forum: Server Platforms
---

### Post by nutaa on 2010-10-16
When i try:
```
ffmpeg -i FdxnuPIdF9Y.flv output.mp3
```(FdxnuPIdF9Y.flv being a 20mb youtube video)
i get:
```
Seems stream 0 codec frame rate differs from container frame rate: 50.00 (50/1) -> 25.00 (25/1)
Input #0, flv, from 'FdxnuPIdF9Y.flv':
  Duration: 00:03:14.75, start: 0.000000, bitrate: 711 kb/s
    Stream #0.0: Video: h264, yuv420p, 640x352 [PAR 1:1 DAR 20:11], 711 kb/s, 25 tbr, 1k tbn, 50 tbc
    Stream #0.1: Audio: aac, 44100 Hz, stereo, s16
File 'output.mp3' already exists. Overwrite ? [y/N] y
Output #0, mp3, to 'output.mp3':
    Stream #0.0: Audio: 0x0000, 44100 Hz, stereo, s16, 64 kb/s
Stream mapping:
  Stream #0.1 -> #0.0
Unsupported codec for output stream #0.0

```How ever, i have been googling, and found 
```
ffmpeg -i FdxnuPIdF9Y.flv -acodec output.mp3
```which is all hunky doory it converts it ect BUT it wont allow me to play it.
(Ive tried it on windows MP and VLC player)

im trying this on a [SIZE=1]ubuntu-10.04-x86 VPS, with the latest ffmpeg installed
i have also tryed [/SIZE]```
mplayer -dumpaudio FdxnuPIdF9Y.flv -dumpfile output.mp3
```[SIZE=1] and that doesn't work in wmp or VLC either

Any help would be appreciated 
Thankss
[/SIZE]

---

