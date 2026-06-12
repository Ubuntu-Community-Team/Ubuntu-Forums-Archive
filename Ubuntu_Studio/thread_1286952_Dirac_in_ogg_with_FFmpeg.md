---
title: "Dirac in ogg with FFmpeg?"
date: 2009-10-09
forum: Ubuntu Studio
---

### Post by Madspyman on 2009-10-09
I'd like to encode Dirac video with Vorbis audio to an ogg container. I've tried it with ffmpeg and it doesn't work, I have both libdirac and libschroedinger enabled as well as libvorbis, libtheora, and most others. 

Theora/Vorbis output to ogg is a go, but Dirac/Vorbis output throws back an error message.

Here's my ffmpeg input-

ffmpeg -i input.avi -vcodec libdirac -b 9000k -acodec libvorbis -ab 128k -s 1920x1080 -r 24 output.ogg

Here's the error-

Could not write header for output file #0 (incorrect codec parameters ?)

I get the same error when using libschroendinger in the place of libdirac

So far Dirac has been the only codec I've had trouble encoding with, I'm interested in oss alternatives to codecs like x264/h264, but have not been to impressed with Theora (I really wanted to like Theora). 

From what I've seen Dirac is a better choice, and while I can watch it, I can't find any complete documentation on how to encode it or how to mux it with audio to an ogg file. 

I'd really like to give Dirac a try so any help is greatly appreciated.

---

### Post by FakeOutdoorsman on 2009-10-09
I've never used Dirac/libschroedinger before, but one of the x264 developers doesn't think it will ever succeed:
[ffmpeg libschroedinger quality](http://forum.doom9.org/showthread.php?t=147319) [doom9.org]

You can see some x264, Dirac, Snow, Theora, Xvid comparisons:
[Open source codec comparison](http://saintdevelopment.com/media/)

---

### Post by Madspyman on 2009-10-09
Yeah x264 is the best around, Theora fails at lower bit-rates and Dirac support is practically non existent. Being oss they've got the right idea, but good intentions don't win any awards. Or do they? Anyway I'll just stick with the mainstream, for now x264 support is unmatched.

---

