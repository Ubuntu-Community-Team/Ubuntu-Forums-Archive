---
title: "Help with getting a high quality video conversion into flv"
date: 2009-02-11
forum: Ubuntu Studio
---

### Post by dmizer on 2009-02-11
My cell phone takes exceptionally high quality video. It plays very well with VLC, but I'd like to share the video on the web, and many of my visitors are still using IE which doesn't play the video correctly.

What I want to do is figure out how to convert the video into flv with as little loss as possible.

My first problem is that I realize the .asf extension is nothing more than a wrapper for the underlying codecs in the video. I have no idea how to determine what codecs the video was actually recorded in.

I have seen this output when attempting to convert with ffmpeg:
```
Stream #0.0: Video: mpeg4, yuv420p, 640x480, 30.00 fps(r)
Stream #0.1: Audio: g726, 8000 Hz, mono, 32 kb/s
```

But, I am unsure if this is accurate information, and if so ... how do I use this information to convert the video into a high quality flv?

---

### Post by FakeOutdoorsman on 2009-02-11
I'll offer an alternative to flv.  You can use [JW Player](http://www.longtailvideo.com/players/jw-flv-player/) or [Flowplayer](http://flowplayer.org/) to play H264 mp4 video encoded by x264 through FFmpeg.  You'll get superior quality at a lower bitrate than any flv specific encoder.  These web players are both free for personal use and not that expensive for commercial use.  I recommend using the libx264 encoding presets that are available with a recent FFmpeg, but you will have to compile it yourself, but that isn't hard to do:

[HOWTO: Install and use the latest FFmpeg and x264](http://ubuntuforums.org/showthread.php?t=786095)

You can use **ffmpeg** and the **libavcodec-unstripped-51** packages from the repository, but no presets are available for them and development for x264 and FFmpeg is quite active.  Now all you have to do is decide what frame size to use for your output and the presets will take care of the rest:
```
ffmpeg -i input.foo -s 480x360 -acodec libfaac -ab 32k -ac 1 -vcodec libx264 -vpre hq -crf 22 -threads 0 ffmpegoutput.mp4

```
Play around with the CRF value.  A higher number results in a lower quality video, but will be smaller in file size and generally encode faster.  CRF 15 is considered almost lossless I think, but I've never even gone close to that value.  You can also use two-pass encoding explained in the link above if you want to target a specific file size/bitrate instead of using CRF to target a specific quality.

If the output file is long you can use MP4Box from the **gpac** package to prepare it, otherwise the video will have to download completely before playing, but I may be wrong:
```
MP4Box -add ffmpegoutput.mp4 newoutput.mp4
```

---

### Post by dmizer on 2009-02-12
Thank you very much for that suggestion. I'm more concerned about integrating the video into my site (which has a handy embedded flash player). Though research indicates I may be able to integrate JW Player into it, I would prefer a flash solution simply for ease of implementation.

Should I simply expect to have extreme visual quality loss when encoding into flv?

---

### Post by FakeOutdoorsman on 2009-02-12
Adobe Flash 9 Update 3+ can play H264 mp4.  Most users should have this version.  If you definately need a flv video:
```
ffmpeg -i input.asf -b 256k -ac 1 -ar 44100 output.flv
```
This is a basic conversion.  I'm not sure of how good the quality will be since I never use flv (I encode with libx264 almost exclusively).  Try adjusting the bitrate (-b).  Once you get a satisfactory file, you will have to run it through flvtool2 to prepare the metadata:
```
flvtool2 -U input.flv
```

---

### Post by dmizer on 2009-02-12
Well, I tried that but something is seriously wrong. I get an incomplete video, video quality is horrible, and sound is not in sync. Here's the output from the encoding:
```
$ ffmpeg -i taiko.ASF -b 256k -ac 1 -ar 44100 tako.flv
FFmpeg version SVN-rUNKNOWN, Copyright (c) 2000-2007 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-pp --enable-swscaler --enable-pthreads --enable-libvorbis --enable-libtheora --enable-libogg --enable-libgsm --enable-dc1394 --disable-debug --enable-libmp3lame --enable-libfaadbin --enable-libfaad --enable-libfaac --enable-xvid --enable-x264 --enable-liba52 --enable-amr_nb --enable-amr_wb --enable-shared --prefix=/usr
  libavutil version: 1d.49.3.0
  libavcodec version: 1d.51.38.0
  libavformat version: 1d.51.10.0
  built on Jul 29 2008 18:21:25, gcc: 4.2.3 (Ubuntu 4.2.3-2ubuntu7)
[asf @ 0xb7fb3110]freeing incomplete packet size 31570, new 129
[asf @ 0xb7fb3110]packet fragment position invalid 9794,9802 not in 129
[asf @ 0xb7fb3110]ff asf bad header bd  at:12935
[asf @ 0xb7fb3110]invalid packet_length -69100189 at:12947
[asf @ 0xb7fb3110]ff asf bad header eb  at:13841
[asf @ 0xb7fb3110]invalid padsize 58265 at:13846
[asf @ 0xb7fb3110]ff asf bad header 81  at:15639
[asf @ 0xb7fb3110]invalid padsize 1411081671 at:15647
[asf @ 0xb7fb3110]ff asf bad header c7  at:19241
[asf @ 0xb7fb3110]invalid padsize 23882 at:19245
[asf @ 0xb7fb3110]freeing incomplete packet size 129, new 129
[asf @ 0xb7fb3110]packet fragment position invalid 19596,10217 not in 129
[asf @ 0xb7fb3110]ff asf bad header 9a  at:22345
[asf @ 0xb7fb3110]invalid packet_length -929376440 at:22351
[asf @ 0xb7fb3110]ff asf bad header 83  at:22409
[asf @ 0xb7fb3110]invalid packet_length -359262762 at:22415
[asf @ 0xb7fb3110]ff asf bad header 6d  at:22537
[asf @ 0xb7fb3110]packet_obj_size invalid
[asf @ 0xb7fb3110]ff asf bad header 86  at:33037
[asf @ 0xb7fb3110]packet_obj_size invalid
[asf @ 0xb7fb3110]ff asf bad header db  at:43803
[asf @ 0xb7fb3110]invalid padsize 265228448 at:43811
[asf @ 0xb7fb3110]ff asf bad header 4e  at:55067
[asf @ 0xb7fb3110]packet_obj_size invalid
[asf @ 0xb7fb3110]ff asf bad header f8  at:68629
[asf @ 0xb7fb3110]packet_obj_size invalid
[asf @ 0xb7fb3110]freeing incomplete packet size 129, new -981418104
[asf @ 0xb7fb3110]packet fragment position invalid 5863,2037 not in 0
[asf @ 0xb7fb3110]packet_obj_size invalid
[asf @ 0xb7fb3110]packet fragment position invalid 1058,5193 not in 0
[asf @ 0xb7fb3110]packet_obj_size invalid
[asf @ 0xb7fb3110]ff asf bad header df  at:104095
[asf @ 0xb7fb3110]invalid padsize 37955 at:104098
[asf @ 0xb7fb3110]ff asf bad header b2  at:114031
[asf @ 0xb7fb3110]ff asf bad non zero
[asf @ 0xb7fb3110]ff asf bad header de  at:123657
[asf @ 0xb7fb3110]invalid padsize -1426412898 at:123663
[asf @ 0xb7fb3110]ff asf bad header eb  at:132681
[asf @ 0xb7fb3110]packet_obj_size invalid
[asf @ 0xb7fb3110]ff asf bad header 91  at:175361
[asf @ 0xb7fb3110]invalid padsize -173392368 at:175367
[asf @ 0xb7fb3110]packet fragment position invalid 1578,4314 not in 0
[asf @ 0xb7fb3110]packet_obj_size invalid
[asf @ 0xb7fb3110]packet fragment position invalid 5471,1219 not in 0
[asf @ 0xb7fb3110]packet_obj_size invalid
[asf @ 0xb7fb3110]packet fragment position invalid 1010,6126 not in 0
[asf @ 0xb7fb3110]packet_obj_size invalid
[asf @ 0xb7fb3110]ff asf bad header 83  at:245589
[asf @ 0xb7fb3110]packet_obj_size invalid
[asf @ 0xb7fb3110]packet fragment position invalid 7076,927 not in 0
[asf @ 0xb7fb3110]packet_obj_size invalid
[asf @ 0xb7fb3110]packet fragment position invalid 1922,4146 not in 0
[asf @ 0xb7fb3110]packet_obj_size invalid
[asf @ 0xb7fb3110]packet fragment position invalid 6054,10217 not in 0
[asf @ 0xb7fb3110]ff asf bad header fc  at:278345
[asf @ 0xb7fb3110]packet_obj_size invalid
[asf @ 0xb7fb3110]ff asf bad header f6  at:336717
[asf @ 0xb7fb3110]freeing incomplete packet size 115295458, new 8084

Seems stream 0 codec frame rate differs from container frame rate: 1000.00 (1000/1) -> 30.00 (30/1)
Input #0, asf, from 'taiko.ASF':
  Duration: 00:05:38.3, start: 3.000000, bitrate: 2041 kb/s
  Stream #0.0: Video: mpeg4, yuv420p, 640x480, 30.00 fps(r)
  Stream #0.1: Audio: g726, 8000 Hz, mono, 32 kb/s
Output #0, flv, to 'tako.flv':
  Stream #0.0: Video: flv, yuv420p, 640x480, q=2-31, 256 kb/s, 30.00 fps(c)
  Stream #0.1: Audio: mp3, 44100 Hz, mono, 64 kb/s
Stream mapping:
  Stream #0.0 -> #0.0
  Stream #0.1 -> #0.1
Press [q] to stop encoding
[mpeg4 @ 0xb7ec19a8]warning: first frame is no keyframe
[asf @ 0xb7fb3110]freeing incomplete packet size 7321, new 1its/s    
[asf @ 0xb7fb3110]packet fragment position invalid 72,7249 not in 1
[asf @ 0xb7fb3110]packet_obj_size invalid
[asf @ 0xb7fb3110]ff asf bad header 4a  at:919183
[asf @ 0xb7fb3110]invalid padsize 60156 at:919188
[asf @ 0xb7fb3110]freeing incomplete packet size 1, new 365810243
[asf @ 0xb7fb3110]freeing incomplete packet size 365810243, new 7308
[asf @ 0xb7fb3110]freeing incomplete packet size 7190, new 1its/s    
[asf @ 0xb7fb3110]packet fragment position invalid 55,7135 not in 1
[asf @ 0xb7fb3110]packet_obj_size invalid
[asf @ 0xb7fb3110]ff asf bad header 46  at:1636211
[asf @ 0xb7fb3110]invalid packet_length 1243161201 at:1636216
[asf @ 0xb7fb3110]freeing incomplete packet size 1, new 44934235
[asf @ 0xb7fb3110]freeing incomplete packet size 44934235, new 8649
[asf @ 0xb7fb3110]freeing incomplete packet size 8298, new 1its/s    
[asf @ 0xb7fb3110]packet fragment position invalid 13,8285 not in 1
[asf @ 0xb7fb3110]packet_obj_size invalid
[asf @ 0xb7fb3110]ff asf bad header bd  at:1961591
[asf @ 0xb7fb3110]invalid padsize -16027117 at:1961597
[asf @ 0xb7fb3110]freeing incomplete packet size 1, new 309205616
[asf @ 0xb7fb3110]freeing incomplete packet size 309205616, new 8545
[asf @ 0xb7fb3110]freeing incomplete packet size 8354, new 1its/s    
[asf @ 0xb7fb3110]packet fragment position invalid 40,8314 not in 1
[asf @ 0xb7fb3110]packet_obj_size invalid
[asf @ 0xb7fb3110]ff asf bad header 3  at:2473533
[asf @ 0xb7fb3110]invalid padsize 431000405 at:2473538
[asf @ 0xb7fb3110]freeing incomplete packet size 1, new 1419163450
[asf @ 0xb7fb3110]freeing incomplete packet size 1419163450, new 8989
[asf @ 0xb7fb3110]freeing incomplete packet size 8925, new 1its/s    
[asf @ 0xb7fb3110]packet fragment position invalid 36,8889 not in 1
[asf @ 0xb7fb3110]packet_obj_size invalid
[asf @ 0xb7fb3110]ff asf bad header 20  at:2933183
[asf @ 0xb7fb3110]invalid packet_length -1905689499 at:2933190
[asf @ 0xb7fb3110]ff asf bad header c1  at:2938239
[asf @ 0xb7fb3110]packet_obj_size invalid
[asf @ 0xb7fb3110]freeing incomplete packet size 1, new -1520433793
[asf @ 0xb7fb3110]packet fragment position invalid 5865,1907 not in 0
[asf @ 0xb7fb3110]packet_obj_size invalid
[asf @ 0xb7fb3110]freeing incomplete packet size 67726432, new 7532
[asf @ 0xb7fb3110]freeing incomplete packet size 7667, new 1bits/s    
[asf @ 0xb7fb3110]packet fragment position invalid 77,7590 not in 1
[asf @ 0xb7fb3110]packet_obj_size invalid
[asf @ 0xb7fb3110]ff asf bad header 79  at:3447781
[asf @ 0xb7fb3110]invalid padsize 864089383 at:3447788
[asf @ 0xb7fb3110]freeing incomplete packet size 1, new 815364233
[asf @ 0xb7fb3110]freeing incomplete packet size 815364233, new 7104
[asf @ 0xb7fb3110]freeing incomplete packet size 7161, new 1
[asf @ 0xb7fb3110]packet fragment position invalid 48,7113 not in 1
[asf @ 0xb7fb3110]packet_obj_size invalid
[asf @ 0xb7fb3110]ff asf bad header ee  at:3520415
[asf @ 0xb7fb3110]invalid packet_length -1196250143 at:3520424
[asf @ 0xb7fb3110]freeing incomplete packet size 1, new 1622169089
[asf @ 0xb7fb3110]freeing incomplete packet size 1622169089, new 6705
[asf @ 0xb7fb3110]freeing incomplete packet size 6141, new 1bits/s    
[asf @ 0xb7fb3110]packet fragment position invalid 54,6087 not in 1
[asf @ 0xb7fb3110]packet_obj_size invalid
[asf @ 0xb7fb3110]ff asf bad header ad  at:5959587
[asf @ 0xb7fb3110]packet_obj_size invalid
[asf @ 0xb7fb3110]freeing incomplete packet size 1, new -367107711
[asf @ 0xb7fb3110]packet fragment position invalid 913,9367 not in 0
[asf @ 0xb7fb3110]packet_obj_size invalid
[asf @ 0xb7fb3110]ff asf bad header 33  at:5973507
[asf @ 0xb7fb3110]invalid padsize 44427 at:5973510
[asf @ 0xb7fb3110]ff asf bad header 78  at:5976987
[asf @ 0xb7fb3110]invalid padsize -918703232 at:5976992
[asf @ 0xb7fb3110]packet fragment position invalid 833,8795 not in 0
[asf @ 0xb7fb3110]packet_obj_size invalid
[asf @ 0xb7fb3110]ff asf bad header 65  at:5984891
[asf @ 0xb7fb3110]invalid padsize 120464771 at:5984898
[asf @ 0xb7fb3110]ff asf bad header ca  at:5990667
[asf @ 0xb7fb3110]invalid packet_length 1406082216 at:5990675
[asf @ 0xb7fb3110]freeing incomplete packet size 600348811, new 6889
[asf @ 0xb7fb3110]freeing incomplete packet size 9538, new 1bits/s    
[asf @ 0xb7fb3110]packet fragment position invalid 26,9512 not in 1
[asf @ 0xb7fb3110]packet_obj_size invalid
[asf @ 0xb7fb3110]ff asf bad header 90  at:7304417
[asf @ 0xb7fb3110]packet_obj_size invalid
[asf @ 0xb7fb3110]ff asf bad header 74  at:7316157
[asf @ 0xb7fb3110]packet_obj_size invalid
[asf @ 0xb7fb3110]ff asf bad header 16  at:7329397
[asf @ 0xb7fb3110]packet_obj_size invalid
frame=  859 q=31.0 Lsize=    2131kB time=27.2 bitrate= 641.2kbits/s    
video:1794kB audio:213kB global headers:0kB muxing overhead 6.167071%
```
Is ffmpeg even the right tool for this?

---

### Post by FakeOutdoorsman on 2009-02-12
FFmpeg is the perfect tool for this.  Another good one is MEncoder, but I'm not very familiar with it's options.  I've never seen your error before, but it should be tested with a recent FFmpeg before troubleshooting otherwise we may be chasing old and resolved bugs.  Either make a sample video available and I'll run it through svn FFmpeg, or compile FFmpeg following the guide I mentioned from my first post.

---

### Post by dmizer on 2009-02-12
> **FakeOutdoorsman said:**
> FFmpeg is the perfect tool for this.  Another good one is MEncoder, but I'm not very familiar with it's options.  I've never seen your error before, but it should be tested with a recent FFmpeg before troubleshooting otherwise we may be chasing old and resolved bugs.  Either make a sample video available and I'll run it through svn FFmpeg, or compile FFmpeg following the guide I mentioned from my first post.

I've successfully encoded with this version of ffmpeg before, but I lost my notes on how to do it, and video quality was terrible. Here's a link to the video in question: [http://dmizer.dnsdojo.net/images/taiko.ASF](http://dmizer.dnsdojo.net/images/taiko.ASF)

Thanks for your help.

Edit:
Please excuse the terrible audio. While the phone takes great video, audio is severely lacking.

---

### Post by FakeOutdoorsman on 2009-02-13
I looked at this briefly and got a few errors/warnings in FFmpeg, but unfortunately my sound didn't initialize correctly at bootup so I could not hear anything.  I'll look into this more, but I may not be able to do so until after the weekend.

---

### Post by dmizer on 2009-02-13
I'll be otherwise occupied this weekend myself, so no worries. This has been an ongoing niggle for me, so I'm not in any huge rush or anything, just reached a point where I couldn't get any more forward progress.

---

### Post by andrew.46 on 2009-02-16
Hi,

I attempted conversion with FFmpeg of this file and found a bewildering range of error messages relating to asf headers. However a degree of repair seemed possible with:

```
$ ffmpeg -i taiko.ASF -vcodec copy -acodec copy taiko_repaired.asf
```

The 'repaired' file seemed to convert easily enough and it is simply a matter of deciding on your settings. But most conversions I tried to flv did not look or sound that good :(.

Andrew

---

### Post by dmizer on 2009-02-17
I can't even get the direct copy to convert.

Is there a possibility that this could be related to the fact that the video was taken with a Japanese phone with Japanese characters?

---

### Post by andrew.46 on 2009-02-17
Hi dmizer,

> **dmizer said:**
> I can't even get the direct copy to convert.

Is there a possibility that this could be related to the fact that the video was taken with a Japanese phone with Japanese characters?

You might be best to try a more recent copy of FFmpeg, I used the most recent svn. My knowledge of asf (= zero) does not really qualify me to comment on why the headers are 'damaged' :-).

Andrew

---

### Post by dmizer on 2009-02-17
Well, I guess this is why nothing I have on any of my boxes will play the video other than VLC (thank you VLC) ... lol. I'll see what I can do with SVN tonight. Perhaps this will turn into a ffmpeg bug report :(

---

### Post by FakeOutdoorsman on 2009-02-17
Building on Andrew's suggestion:
```
ffmpeg -i taiko_repaired.asf -ar 44100 -ac 1 -croptop 120 -cropbottom 120 -cropleft 160 -cropright 160 -b 384k taiko.flv
flvtool2 -U taiko.flv
```
This crops out the crowd and makes a 320x240 video.  Adjust the bitrate as neccessary.  I don't have much experience with flv, so I don't know how to optimize it beyond this, excluding playing around with qmin and qmax.  I used svn FFmpeg.

---

### Post by dmizer on 2009-02-23
Thanks again for your help, I finally got around to installing svn version of ffmpeg so I could test this on my own. I'm beginning to think that this particular video might be particularly troublesome for some reason. After converting to flv, the sound timing is way off for this video.

Other videos from the same phone seem to be converting much better though. Thank you.

---

