---
title: "command line tool to discover file types"
date: 2009-04-22
forum: Ubuntu Studio
---

### Post by Yadda on 2009-04-22
Hello,

I'd like to know if a command line tool exists to dump the properties of a video file. mime type, aspect ratio, encoder etc.
I am responsible for a script to convert video files server side based on a number of presets that depend on the file properties. I've tried FFMPEG for this but the output is not verbose or consistent enough for my needs. Any ideas?

Thanks!

---

### Post by FakeOutdoorsman on 2009-04-22
Try [mediainfo](http://mediainfo.sourceforge.net/en/Download#Ubuntu):
```
$ mediainfo 00009.MTS
General
ID                               : 1
Complete name                    : 00009.MTS
Format                           : BDAV
Format/Info                      : BluRay Video
File size                        : 2.80 GiB
Maximum Overall bit rate         : 24.0 Mbps

Video
ID                               : 4113 (0x1011)
Menu ID                          : 1 (0x1)
Format                           : AVC
Format/Info                      : Advanced Video Codec
Format profile                   : High@L4.0
Format settings, CABAC           : Yes
Format settings, ReFrames        : 4 frames
Width                            : 1 280 pixels
Height                           : 720 pixels
Display aspect ratio             : 16/9
Frame rate                       : 59.940 fps
Resolution                       : 24 bits
Colorimetry                      : 4:2:0
Scan type                        : Progressive

Audio
ID                               : 4352 (0x1100)
Menu ID                          : 1 (0x1)
Format                           : AC-3
Format/Info                      : Audio Coding 3
Bit rate mode                    : Constant
Bit rate                         : 384 Kbps
Channel(s)                       : 2 channels
Channel positions                : L R
Sampling rate                    : 48.0 KHz
Video delay                      : -50ms
```

---

