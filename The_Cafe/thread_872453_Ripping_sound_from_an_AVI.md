---
title: "Ripping sound from an AVI"
date: 2008-07-28
forum: The Cafe
---

### Post by Riffer on 2008-07-28
Is there an app that I can rip music from an avi file?

---

### Post by vikramaditya on 2008-07-28
If you like a GUI, I've done this using Avidemux.  Been awhile, but it was fairly simple to use.

System > Administration > Synaptic Package Manager > Search "avidemux"

---

### Post by Bachstelze on 2008-07-28
```
ffmpeg -i foo.avi -vn -acodec copy bar.mp3
```

Assuming the audio is MP3, of course..

---

### Post by Masoris on 2008-07-28
Convert it to ogg audio file by 'Sound Converter'.

---

### Post by Bachstelze on 2008-07-28
> **Masoris said:**
> Convert it to ogg audio file by 'Sound Converter'.

No. Just... no. Converting from a lossy codec to another will sound horrible.

---

### Post by qazwsx on 2008-07-28
```
mplayer file.avi -identify -vo null -ao null -frames 0 |grep ID_AUDIO_CODEC
```
gives you audio codec information.
you can use ffmpeg as above or harder way
```
mplayer -dumpaudio file.avi -dumpfile fileout
```
File is sometimes playable depending on audio format (but should be reusable with mencoder at least and might be even remuxable... with ffmpeg :lolflag:).

---

