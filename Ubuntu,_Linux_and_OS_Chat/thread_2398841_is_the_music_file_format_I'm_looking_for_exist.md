---
title: "is the music file format I'm looking for exist?"
date: 2018-08-17
forum: Ubuntu, Linux and OS Chat
---

### Post by ardouronerous on 2018-08-17
Hello,
I'm looking for a music file format that is similar quality to mp3, as in 128kbps, but smaller file size than mp3.
Preferably a format supported by VLC because that's my default music player on my smartphone.

---

### Post by TheFu on 2018-08-18
Vorbis or Opus.  Both are higher quality than MP3 for the same bitrate.  VLC plays either fine. So will all Android devices.
[https://opus-codec.org/comparison/](https://opus-codec.org/comparison/)
and
[https://xiph.org/vorbis/](https://xiph.org/vorbis/)

---

### Post by ardouronerous on 2018-08-18
Thanks :)
After converting my mp3 to different formats with this command:

```
ffmpeg -i filename.mp3 newfilename.ogg newfilename.aac newfilename.opus
```

Opus seems to be the smallest size format and the same 128kbps bit rate.

---

### Post by TheFu on 2018-08-18
bitrate doesn't tell the whole story. 

If you use the opus tools directly, then you can better control the quality. For a voice recording, that is less important and for converting bad mp3, it probably doesn't matter either, but if you really care about the quality, re-rerip the audio from the source and then use the WAV or FLAC as the source for high quality opus/vorbis/ogg.

---

### Post by silverslimer on 2018-08-19
Opus also has the best quality for low bitrates whereas you're better off with OGG Vorbis at higher bitrates according to HydrogenAudio tests.

---

