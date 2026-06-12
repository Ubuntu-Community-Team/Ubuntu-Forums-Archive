---
title: "FFMPEG MKV to DivX - Video too fast!"
date: 2009-01-06
forum: Ubuntu Studio
---

### Post by jcr1 on 2009-01-06
I am using ffmpeg to convert a mkv containing h264 video and 5.1 aac into mpeg4 divx and 5.1 ac3 audio.

This is my command:

```

ffmpeg -i original.mkv -vcodec mpeg4 -vtag divx -vb 5000k -aspect 2.424 -r 23.976 -acodec ac3 -ac 6 -ab 384k output.avi

```

There are a few errors during transcoding, such as:

```

...
[matroska @ 0xb7ef6110]Ignoring seekhead entry for ID=0x114d9b74
[matroska @ 0xb7ef6110]Unknown entry 0x73a4 in info header
[matroska @ 0xb7ef6110]Unknown track header entry 0x55aa - ignoring
...

...
[h264 @ 0xb7e049a8]AVC: nal size 909323312 bitrate=4659.8kbits/s    
[h264 @ 0xb7e049a8]no frame!
Error while decoding stream #0.0
...

```

but it finishes and the output.avi is playable, but the problem is that the video stream seems to be about 3x too fast. The audio is normal, but the video is super fast.

What am I doing wrong?

Here are the MediaInfo's of the original.mkv and output.avi:

Original.mkv:
```

Format               : Matroska
File size            : 26.5 MiB
PlayTime             : 1mn 3s
Bit rate             : 3506 Kbps
Encoded date         : UTC 2007-07-31 13:16:07
Writing application  : mkvmerge v2.0.2 ('You're My Flame') built on Feb 21 2007 23:40:55
Writing library      : libebml v0.7.7 + libmatroska v0.8.1

Video #0
Codec                : MPEG-4 AVC
Codec/Info           : MPEG4 ISO advanced profile
PlayTime             : 1mn 3s
Width                : 936 pixels
Height               : 528 pixels
Aspect ratio         : 2.424
Frame rate           : 23.976 fps
Language             : English

Audio #0
Codec                : A_AAC
Channel(s)           : 6 channels
Sampling rate        : 24 KHz

Text #0
Codec                : ***
Codec/Info           : Advanced Sub Station Alpha

```

and output.avi:
```

Format               : AVI
Format/Info          : Audio Video Interleave
Format/Family        : RIFF
File size            : 40.9 MiB
PlayTime             : 1mn 3s
Bit rate             : 5405 Kbps
StreamSize           : 120 KiB
Writing application  : Lavf1d.51.10.0

Video #0
Codec                : DivX
Codec/Family         : MPEG-4
Codec/Info           : Mainly used by Google
Codec settings/Packe : No
Codec settings/BVOP  : No
Codec settings/QPel  : No
Codec settings/GMC   : 0
Codec settings/Matri : Default
PlayTime             : 1mn 3s
Bit rate             : 5016 Kbps
Width                : 936 pixels
Height               : 528 pixels
Aspect ratio         : 2.424
Frame rate           : 23.976 fps
Resolution           : 8 bits
Chroma               : 4:2:0
Interlacement        : Progressive
Bits/(Pixel*Frame)   : 0.423
StreamSize           : 37.9 MiB
Writing library      : Lavc1d.51.38.0

Audio #0
Codec                : AC3
PlayTime             : 1mn 3s
Bit rate             : 382 Kbps
Bit rate mode        : CBR
Channel(s)           : 6 channels
Sampling rate        : 48 KHz
Resolution           : 16 bits
StreamSize           : 2.89 MiB
ChannelPositions     : Front: L C R, Rear: L R, Subwoofer

```

Video frame rate seems the same, so why the high speed video?

Many thanks in advance.

---

### Post by jcr1 on 2009-01-06
Ok something important...

I am streaming this avi to my xbox (please no comments about just putting h264 in mp4) it streams but plays fast as stated... if I play this on my computer with say vlc, it plays fine!!

So why is my xbox 360 cocking it up?!?

---

### Post by jcr1 on 2009-01-06
Just to rule more out, putting the avi on a memory stick and into the xbox results in the same thing, so its not the streaming bit of it... its definately the xbox.

---

### Post by jcr1 on 2009-01-08
Can anyone suggest anything on this please?

---

### Post by M_JaGuar on 2009-04-28
just rename the file from video.mkv to video.m4v

---

