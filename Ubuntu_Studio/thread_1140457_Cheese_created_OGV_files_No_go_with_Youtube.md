---
title: "Cheese created OGV files No go with Youtube"
date: 2009-04-27
forum: Ubuntu Studio
---

### Post by ctsdownloads on 2009-04-27
I have tried direct uploads with Cheese created saved OGV files and Mencoder and FFMPEG as well fail across the board. Not okay, folks. Surely Cheese can save to something USABLE, right?

Tried five different methods with Mencoder - it's not a fault with Mencoder, it is Cheese and how ever it is encoding....really pissed off with this, because WXCam is not really a viable alternative with its OSS usage and all.

Sigh...

:(

---

### Post by ctsdownloads on 2009-04-27
So, this is not working:

mencoder -idx video-1.ogv -ovc lavc -oac mp3lame -o video-1.avi

I end up with....
[INDENT][I]
MEncoder 2:1.0~rc2-0ubuntu17 (C) 2000-2007 MPlayer Team
CPU: AMD Athlon(tm) 64 Processor 3700+ (Family: 15, Model: 4, Stepping: 10)
CPUflags: Type: 15 MMX: 1 MMX2: 1 3DNow: 1 3DNow2: 1 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
success: format: 0  data: 0x0 - 0xef9fbc
[Ogg] stream 0: video (Theora v3.2.1), -vid 0
[Ogg] stream 1: audio (Vorbis), -aid 0
Ogg file format detected.
VIDEO:  [theo]  352x288  24bpp  30.000 fps    0.0 kbps ( 0.0 kbyte/s)
[V] filefmt:18  fourcc:0x6F656874  size:352x288  fps:30.00  ftime:=0.0333
==========================================================================
Opening audio decoder: [ffmpeg] FFmpeg/libavcodec audio decoders
AUDIO: 44100 Hz, 1 ch, s16le, 80.0 kbit/11.34% (ratio: 10000->88200)
Selected audio codec: [ffvorbis] afm: ffmpeg (FFmpeg Vorbis decoder)
==========================================================================
Opening video filter: [expand osd=1]
Expand: -1 x -1, -1 ; -1, osd: 1, aspect: 0.000000, round: 1
==========================================================================
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
[theora @ 0x88433b0]Missing extradata!
Could not open codec.
VDecoder init failed :(
Opening video decoder: [theora] Theora/VP3
VDec: vo config request - 352 x 288 (preferred colorspace: Planar YV12)
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is undefined - no prescaling applied.
videocodec: libavcodec (352x288 fourcc=34504d46 [FMP4])
Selected video codec: [theora] vfm: theora (Theora (free, reworked VP3))
==========================================================================
MP3 audio selected.
Ogg : bad packet in stream 1
Ogg : bad packet in stream 1

Too many audio packets in the buffer: (4096 in 468944 bytes).
Maybe you are playing a non-interleaved stream/file or the codec failed?
For AVI files, try to force non-interleaved mode with the -ni option.

Flushing video frames.
Writing index...
Writing header...
ODML: Aspect information not (yet?) available or unspecified, not writing vprp header.

Video stream:      nan kbit/s  (-2147483648 B/s)  size: 0 bytes  0.000 secs  0 frames

Audio stream:   93.452 kbit/s  (11681 B/s)  size: 6103 bytes  0.522 secs[/I][/INDENT]

---

### Post by ctsdownloads on 2009-04-27
Looks like it Cheese with the issues...

[http://ubuntuforums.org/showthread.php?p=7113301](http://ubuntuforums.org/showthread.php?p=7113301)

Awesome

---

### Post by cariboo on 2009-04-28
Did you try avidemux to convert the video?

---

### Post by ctsdownloads on 2009-04-28
> **cariboo907 said:**
> Did you try avidemux to convert the video?

Yeah, I sure did - no go. Just fails to convert it. As it turns out, it is an outstanding bug with Cheese itself creating funkiness. Oh well, thank goodness for Ustream with YouTube's API. :)

---

### Post by eye208 on 2009-04-28
If you just want to record from the webcam (i.e. without the special FX of Cheese), use MEncoder with tv:// as input. You can specify additional parameters using the -tv option, if necessary.

---

### Post by ctsdownloads on 2009-04-28
> **eye208 said:**
> If you just want to record from the webcam (i.e. without the special FX of Cheese), use MEncoder with tv:// as input. You can specify additional parameters using the -tv option, if necessary.

Good point, I could just create a quick bash script for this as well. Thanks for the thought.

---

