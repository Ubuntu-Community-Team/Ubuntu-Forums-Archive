---
title: "how to extract video meta information in a bash or PHP script?"
date: 2009-03-06
forum: Ubuntu Studio
---

### Post by abadr on 2009-03-06
Hi, 

Any ideas on how to extract video meta information (resolution, bit rate, codec, etc..) and assign them to variables in a bash or PHP script? 

I need the info to store in a database for a video content application. 

Thanks.

---

### Post by clubsoda on 2009-03-31
Should be something like ```
mplayer -vo null -vc null -ao null -identify videofile
```but mplayer still wants to play the file even though no outputs are requested.
There seem to be a few CODEC conversion tools (ffmpeg, transcode) but nothing to just extract the stream info.

---

### Post by andrew.46 on 2009-03-31
Hi,

The source code for the svn MPlayer has a wrapper script for the -identify option of MPlayer called midentify.sh (located in TOOLS/) which might be what you are after. It produces the following output:

```

andrew@skamandros~/movies$ midentify.sh hotel_california_ra5.1_640x480_30s.rmvb 
ID_VIDEO_ID=0
ID_AUDIO_ID=1
ID_FILENAME=hotel_california_ra5.1_640x480_30s.rmvb
ID_DEMUXER=real
ID_VIDEO_FORMAT=RV40
ID_VIDEO_BITRATE=0
ID_VIDEO_WIDTH=640
ID_VIDEO_HEIGHT=480
ID_VIDEO_FPS=30.000
ID_VIDEO_ASPECT=0.0000
ID_AUDIO_FORMAT=cook
ID_AUDIO_BITRATE=0
ID_AUDIO_RATE=44100
ID_AUDIO_NCH=6
ID_LENGTH=30.00
ID_SEEKABLE=1
ID_CHAPTERS=0
ID_VIDEO_CODEC=ffrv40
ID_AUDIO_BITRATE=183288
ID_AUDIO_RATE=44100
ID_AUDIO_NCH=6
ID_AUDIO_CODEC=ra10cook
ID_EXIT=EOF

```

But there must be dedicated tools out there somewhere?

Andrew

---

### Post by andrew.46 on 2009-03-31
Hi clubsoda,

> **clubsoda said:**
> Should be something like 

```
mplayer -vo null -vc null -ao null -identify videofile
```

but mplayer still wants to play the file even though no outputs are requested.

Try adding '-frames 0' or pretty it up a little with the midentify.sh script as I mention above. All the details can be found in the man page, which I give here so as not to appear churlish:-).

> 

       -identify
              Shorthand for -msglevel identify=4.  Show file parameters in  an
              easily  parseable format.  Also prints more detailed information
              about subtitle and audio track languages and IDs.  In some cases
              you can get more information by using -msglevel identify=6.  For
              example, for a DVD it will list the chapters and time length  of
              each  title,  as well as a disk ID.  Combine this with -frames 0
              to suppress all output.  The wrapper  script  TOOLS/midentify.sh
              suppresses the other MPlayer output and (hopefully) shellescapes
              the filenames.



All the best,

Andrew

---

### Post by benjjo on 2009-03-31
Try Hachoir, it seems to do the job well enough for my needs:

```

$ hachoir-metadata file.avi
- Duration: 51 min 40 sec 141 ms
- Image width: 624 pixels
- Image height: 352 pixels
- Frame rate: 24.0 fps
- Bit rate: 928.1 Kbit/sec
- Producer: Nandub v1.0rc2
- Comment: Has audio/video index (3.1 MB)
- MIME type: video/x-msvideo
- Endian: Little endian
Video stream:
- Duration: 51 min 40 sec 141 ms
- Image width: 624 pixels
- Image height: 352 pixels
- Bits/pixel: 12
- Compression: XviD MPEG-4 (fourcc:"XviD")
- Frame rate: 24.0 fps
Audio stream:
- Duration: 51 min 40 sec 80 ms
- Channel: stereo
- Sample rate: 48.0 kHz
- Compression rate: 12.6x
- Compression: MPEG Layer 3
- Bit rate: 121.6 Kbit/sec
$

```

---

### Post by clubsoda on 2009-04-01
> **andrew.46 said:**
> ... the man page, which I give here so as not to appear churlish:-).Not at all, I'm just glad you didn't quote the entire 320 odd pages. :)
[quote=benjjo]Try Hachoir[/quote]Thanks for the tip.  This would be my choice, although it doesn't appear to support MPEG video yet.

---

### Post by andrew.46 on 2009-04-01
**Edit:** Oops!! Just realised you were speaking of hachoir :-). My apologies.

Hi clubsoda,

> **clubsoda said:**
> Thanks for the tip.  This would be my choice, although it doesn't appear to support MPEG video yet.

I was not aware of that. It certainly recognises *mpeg4 *video as I converted some to test it:

```

andrew@skamandros~/movies$ midentify.sh test.mp4 
ID_VIDEO_ID=0
ID_AUDIO_ID=1
ID_FILENAME=test.mp4
ID_DEMUXER=lavfpref
**[COLOR="Red"]ID_VIDEO_FORMAT=mp4v[/COLOR]**
ID_VIDEO_BITRATE=0
ID_VIDEO_WIDTH=352
ID_VIDEO_HEIGHT=234
ID_VIDEO_FPS=25.000
ID_VIDEO_ASPECT=1.5043
ID_AUDIO_FORMAT=255
ID_AUDIO_BITRATE=0
ID_AUDIO_RATE=44100
ID_AUDIO_NCH=2
ID_LENGTH=234.10
ID_SEEKABLE=1
ID_CHAPTERS=0
ID_VIDEO_CODEC=ffodivx
ID_AUDIO_BITRATE=128000
ID_AUDIO_RATE=44100
ID_AUDIO_NCH=2
**[COLOR="Red"]ID_AUDIO_CODEC=faad[/COLOR]**
ID_EXIT=EOF

```

So I converted to mpeg and mp3:

```

andrew@skamandros~/movies$ midentify.sh test.mpg 
ID_VIDEO_ID=0
ID_AUDIO_ID=0
ID_FILENAME=test.mpg
ID_DEMUXER=mpegps
**[COLOR="Red"]ID_VIDEO_FORMAT=0x10000001[/COLOR]**
ID_VIDEO_BITRATE=0
ID_VIDEO_WIDTH=352
ID_VIDEO_HEIGHT=264
ID_VIDEO_FPS=25.000
ID_VIDEO_ASPECT=0.0000
ID_AUDIO_FORMAT=80
ID_AUDIO_BITRATE=0
ID_AUDIO_RATE=0
ID_AUDIO_NCH=0
ID_LENGTH=213.08
ID_SEEKABLE=1
ID_CHAPTERS=0
ID_VIDEO_CODEC=mpegpes
ID_AUDIO_BITRATE=128000
ID_AUDIO_RATE=44100
ID_AUDIO_NCH=2
**[COLOR="Red"]ID_AUDIO_CODEC=mp3[/COLOR]**
ID_EXIT=EOF

```

and you have certainly hit the nail on the head there. But I thought the software benjjo suggested looked much more impressive? And of course FFmpeg identifies files quite neatly as well. I ran it over the last file just for a demonstration:

```

andrew@skamandros~/movies$ ffmpeg -i test.mpg 
FFmpeg version SVN-r18299, Copyright (c) 2000-2009 Fabrice Bellard, et al.
  configuration: --prefix=/usr --mandir=/usr/man --disable-debug -
-enable-shared --disable-static --enable-postproc --enable-avfilter 
--enable-pthreads --enable-libtheora --enable-libvorbis --enable-x11grab 
--enable-libmp3lame --enable-libx264 --enable-libschroedinger 
--enable-libfaac --enable-libfaad --enable-libamr-wb --enable-libamr-nb 
--enable-libgsm --enable-libspeex --enable-nonfree --enable-gpl
  libavutil     50. 2. 0 / 50. 2. 0
  libavcodec    52.22. 3 / 52.22. 3
  libavformat   52.32. 0 / 52.32. 0
  libavdevice   52. 1. 0 / 52. 1. 0
  libavfilter    0. 5. 0 /  0. 5. 0
  libswscale     0. 7. 1 /  0. 7. 1
  libpostproc   51. 2. 0 / 51. 2. 0
  built on Apr  1 2009 13:18:02, gcc: 4.2.4
[B][COLOR="Red"]Input #0, mpeg, from 'test.mpg':
  Duration: 00:03:45.82, start: 0.500000, bitrate: 335 kb/s
    Stream #0.0[0x1e0]: Video: mpeg1video, yuv420p, 352x264 [PAR 1:1 DAR 4:3], 104857 kb/s, 25 tbr, 90k tbn, 25 tbc
    Stream #0.1[0x1c0]: Audio: mp3, 44100 Hz, stereo, s16, 128 kb/s[/COLOR][/B]

```

Fascinating stuff!!

Andrew

---

