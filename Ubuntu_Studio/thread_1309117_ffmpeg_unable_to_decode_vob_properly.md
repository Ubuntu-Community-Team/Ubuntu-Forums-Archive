---
title: "ffmpeg unable to decode vob properly"
date: 2009-11-01
forum: Ubuntu Studio
---

### Post by phenest on 2009-11-01
I'm using ffmpeg to decode vob files (plus cropping etc) and pipe them to x264 for encoding, but I've found one video that gives errors that produce unwanted results.

The video is [Blondie - Heart Of Glass]("http://www.vip-files.net/10082/Heart_Of_Glass.html"). The ffmpeg decoder gives errors (MV not available) and one frame (@ about 52 secs) is particularly bad.

The video play fine using Totem or mplayer, but not with ffplay. Avidemux has problems too but only if it uses libavcodec MPEG-2 decoder.

I'd prefer to pipe to x264 as it gives good results, so is there a way to get ffmpeg to use a different decoder, or to pipe with something else?

---

### Post by phenest on 2009-11-01
I've found I can create a raw yuv file with mplayer and then use ffmpeg to pipe to x264, et voila! Side effects are that the original vob is about 200MB and the yuv file is 3.3GB! So, how can I pipe the output from mplayer straight to x264?

```
mplayer blondie-heart_of_glass.vob -vo yuv4mpeg:file=stream.yuv -ao null -nosound -noframedrop
```

---

### Post by FakeOutdoorsman on 2009-11-01
You can use named pipes.  Here's an example from my notes.  FFmpeg had trouble decoding a buggy huffyuv file from Adobe Premiere Pro 3 so I used MPlayer to decode and pipe the output to FFmpeg/libx264.
```
$ mkfifo stream.yuv
$ mkfifo stream.wav
$ mplayer buybackamerica-huffyuv.avi -vo yuv4mpeg:file=stream.yuv -nosound -ao null -noframedrop -ni
$ mplayer buybackamerica-huffyuv.avi -ao pcm:file=stream.wav -noframedrop -quiet -ni -vo null
```
I then opened another terminal session and ran FFmpeg:
```
$ ffmpeg -f yuv4mpegpipe -i stream.yuv -i stream.wav -acodec libfaac -ab 192k -ac 2 -vcodec libx264 -vpre hq -crf 20 -threads 0 buybackamerica-hd-redo.mp4
```

---

### Post by phenest on 2009-11-01
That solution didn't even occur to me, nor did I know how to do it. Thanks.

Incidentally, the stream.yuv pipe cannot be fed to x264 directly. I used ffmpeg to pipe it to x264, which is ok as I can use ffmpeg to provide filters.

---

