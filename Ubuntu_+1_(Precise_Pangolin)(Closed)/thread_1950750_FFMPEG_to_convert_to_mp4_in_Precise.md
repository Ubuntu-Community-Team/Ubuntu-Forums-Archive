---
title: "FFMPEG to convert to mp4 in Precise"
date: 2012-04-01
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by subhadip_sky on 2012-04-01
Hi, I have upgraded to Ubuntu 12.04 LTS beta 2 from 11.10. I used to convert videos for my Nokia C2-03 mobile phone ( which is a S40 phone) using the following command

```
ffmpeg -i input.flv -acodec libvo_aacenc -ab 96k -b 96k -s 240x160 output10.mp4
```But after upgrading, the command does convert the video but my phone is not being able to play the video. So what could have gone wrong? Is it a bug or something?

---

### Post by howefield on 2012-04-01
Thread moved to "*Ubuntu +1 (Precise Pangolin)*" forum.

---

### Post by mc4man on 2012-04-01
If you are using the 12.04  ffmpeg, the  binary provided is some version that the Libav people included for the moment to provide compatibility for apps that still use ffmpeg in their command(s).

What version of FFmpeg they've chosen I'm not exactly sure, it was mentioned here [in a nonsense bug I filed]("https://bugs.launchpad.net/ubuntu/+source/libav/+bug/939863")

The intention now & in the future is for users to use avconv instead of ffmpeg- have you tried that.

Otherwise you may get some help here if none is forthcoming from this sub forum, myself don't have a cell phone of any type
[http://ubuntuforums.org/showthread.php?t=786095](http://ubuntuforums.org/showthread.php?t=786095)

---

### Post by FakeOutdoorsman on 2012-04-02
> **subhadip_sky said:**
> 
```
ffmpeg -i input.flv -acodec libvo_aacenc -ab 96k -b 96k -s 240x160 output10.mp4
```But after upgrading, the command does convert the video but my phone is not being able to play the video. So what could have gone wrong? Is it a bug or something?

Can you also show the complete console output? Hopefully it's something obvious, but I'm fairly ignorant of ffake ffmpeg/avconv from libav.

> **mc4man said:**
> myself don't have a cell phone of any type
Same here.

---

### Post by mc4man on 2012-04-02
> **FakeOutdoorsman said:**
>  ignorant of ffake ffmpeg/avconv from libav.

I noticed that the accepted message change has been committed into debian, I guess better than no change 
(would of liked to see some 'punitive damages' so to speak, like acknowledging the existence of FFmpeg but obviously that wasn't going to happen - I think all the Libav guys have disabled cap F's on their keyboards anyway
It looks like making sure that libav-tools is removed prior to building would be prudent though /usr/local/ does trump /usr/

---

### Post by FakeOutdoorsman on 2012-04-02
> **mc4man said:**
> I noticed that the accepted message change has been committed into debian, I guess better than no change 
(would of liked to see some 'punitive damages' so to speak, like acknowledging the existence of FFmpeg but obviously that wasn't going to happen - I think all the Libav guys have disabled cap F's on their keyboards anyway
Thanks for the bug report. I'm glad they actually made a change, but it will be unfortunate if it doesn't make it into 12.04.
> **mc4man said:**
> It looks like making sure that libav-tools is removed prior to building would be prudent though /usr/local/ does trump /usr/
Good point. I didn't think of that. I haven't been able to test Ubuntu+1 yet due to travel, an office move, and other meastspaceings.

---

### Post by subhadip_sky on 2012-04-02
> **FakeOutdoorsman said:**
> Can you also show the complete console output? Hopefully it's something obvious, but I'm fairly ignorant of ffake ffmpeg/avconv from libav.


Here's the console output.

```
ffmpeg -i q.flv -acodec libvo_aacenc -ab 96k -b 96k -s 240x160 q1.mp4
ffmpeg version 0.8.1-4:0.8.1-0ubuntu1, Copyright (c) 2000-2011 the Libav developers
  built on Mar 22 2012 05:29:10 with gcc 4.6.3
This program is not developed anymore and is only provided for compatibility. Use avconv instead (see Changelog for the list of incompatible changes).
[flv @ 0x8757260] Estimating duration from bitrate, this may be inaccurate
Input #0, flv, from 'q.flv':
  Metadata:
    starttime       : 0
    totalduration   : 225
    totaldatarate   : 614
    bytelength      : 17294769
    canseekontime   : true
    sourcedata      : BADC23421MH1322280856255650
    purl            : 
    pmsg            : 
  Duration: 00:03:45.40, start: 0.000000, bitrate: 620 kb/s
    Stream #0.0: Video: h264 (Main), yuv420p, 640x480 [PAR 1:1 DAR 4:3], 521 kb/s, 25 tbr, 1k tbn, 50 tbc
    Stream #0.1: Audio: aac, 44100 Hz, stereo, s16, 99 kb/s
[buffer @ 0x875e8c0] w:640 h:480 pixfmt:yuv420p
[scale @ 0x875ebe0] w:640 h:480 fmt:yuv420p -> w:240 h:160 fmt:yuv420p flags:0x4
[libx264 @ 0x8759e20] using SAR=8/9
[libx264 @ 0x8759e20] using cpu capabilities: MMX2 SSE2Fast SSSE3 Cache64
[libx264 @ 0x8759e20] profile Main, level 1.2
[libx264 @ 0x8759e20] 264 - core 120 r2151 a3f4407 - H.264/MPEG-4 AVC codec - Copyleft 2003-2011 - http://www.videolan.org/x264.html - options: cabac=1 ref=3 deblock=1:0:0 analyse=0x1:0x111 me=hex subme=7 psy=1 psy_rd=1.00:0.00 mixed_ref=0 me_range=16 chroma_me=1 trellis=1 8x8dct=0 cqm=0 deadzone=21,11 fast_pskip=1 chroma_qp_offset=-2 threads=1 sliced_threads=0 nr=0 decimate=1 interlaced=0 bluray_compat=0 constrained_intra=0 bframes=3 b_pyramid=0 b_adapt=1 b_bias=0 direct=1 weightb=0 open_gop=1 weightp=2 keyint=250 keyint_min=25 scenecut=40 intra_refresh=0 rc_lookahead=40 rc=abr mbtree=1 bitrate=96 ratetol=1.0 qcomp=0.60 qpmin=0 qpmax=69 qpstep=4 ip_ratio=1.25 aq=1:1.00
Output #0, mp4, to 'q1.mp4':
  Metadata:
    starttime       : 0
    totalduration   : 225
    totaldatarate   : 614
    bytelength      : 17294769
    canseekontime   : true
    sourcedata      : BADC23421MH1322280856255650
    purl            : 
    pmsg            : 
    encoder         : Lavf53.21.0
    Stream #0.0: Video: libx264, yuv420p, 240x160 [PAR 8:9 DAR 4:3], q=-1--1, 96 kb/s, 25 tbn, 25 tbc
    Stream #0.1: Audio: libvo_aacenc, 44100 Hz, stereo, s16, 96 kb/s
Stream mapping:
  Stream #0.0 -> #0.0
  Stream #0.1 -> #0.1
Press ctrl-c to stop encoding
frame= 5636 fps= 72 q=30.0 Lsize=    5489kB time=225.40 bitrate= 199.5kbits/s    
video:2694kB audio:2641kB global headers:0kB muxing overhead 2.872655%
frame I:61    Avg QP:19.34  size:  4297
[libx264 @ 0x8759e20] frame P:2877  Avg QP:25.63  size:   738
[libx264 @ 0x8759e20] frame B:2698  Avg QP:29.89  size:   138
[libx264 @ 0x8759e20] consecutive B-frames: 18.6% 45.3% 22.6% 13.6%
[libx264 @ 0x8759e20] mb I  I16..4: 30.0%  0.0% 70.0%
[libx264 @ 0x8759e20] mb P  I16..4:  1.2%  0.0%  1.4%  P16..4: 29.2% 16.0%  8.9%  0.0%  0.0%    skip:43.3%
[libx264 @ 0x8759e20] mb B  I16..4:  0.1%  0.0%  0.0%  B16..8: 30.8%  5.0%  1.0%  direct: 0.9%  skip:62.3%  L0:31.3% L1:59.3% BI: 9.4%
[libx264 @ 0x8759e20] final ratefactor: 23.47
[libx264 @ 0x8759e20] coded y,uvDC,uvAC intra: 56.5% 63.1% 44.9% inter: 10.9% 8.4% 1.4%
[libx264 @ 0x8759e20] i16 v,h,dc,p: 43% 34% 15%  9%
[libx264 @ 0x8759e20] i4 v,h,dc,ddl,ddr,vr,hd,vl,hu: 26% 22% 19%  5%  5%  6%  6%  5%  5%
[libx264 @ 0x8759e20] i8c dc,h,v,p: 45% 28% 22%  4%
[libx264 @ 0x8759e20] Weighted P-Frames: Y:2.7% UV:0.8%
[libx264 @ 0x8759e20] ref P L0: 78.6%  9.0%  8.6%  3.7%  0.1%
[libx264 @ 0x8759e20] ref B L0: 91.1%  8.9%
[libx264 @ 0x8759e20] kb/s:97.87
```

---

