---
title: "Video production for an MP4 player"
date: 2010-01-02
forum: Ubuntu Studio
---

### Post by tkrisz on 2010-01-02
My niece got a cheap MP4 player. Seems like it recognises video only in a very specific format. It came with a mini CD, that should have contain a small exe file for Windows, that produces such videos, but that file was missing from the CD.
Fortunately there's a sample file on the MP4 player. So i decided to reproduce the same file format. I have partial success, finally it recognises the file i produced, but it stops after a few milliseconds. Any idea, what can i do more and with which (ubuntu or XP) program?
I attach details provided by win kmplayer on the sample file (1st) and the file i produced (2nd).

---

### Post by FakeOutdoorsman on 2010-01-03
Can you install [mediainfo](http://mediainfo.sourceforge.net/en/Download) and paste the output of:
```
mediainfo football.avi
```
This may provide more information on the video.  If you don't want to install mediainfo, could you upload *football.avi*?  What is the model of this MP4 player?

---

### Post by tkrisz on 2010-01-04
The story has a happy end. After several days of googling and trying different settings of many programs, i've found a great application that was written exactly for these MP4 players. It's name is **viDrop**.
Actually it has a Rock USB Chipset or something like that, the MP4 player is basically noname, "Concorde" is the only name written on it.

So my interest is rather theoretical now, i would like to know more about media files. I'm interested what makes some files good and others wrong and maybe would be nice to produce a good file in Ubuntu (viDrop is win only at the moment, but the developer plans to make it cross platform). So i post what mediainfo says for the original football.avi, then for a wrong file made by another program, then for a good file made by viDrop. I know that bitrate does not make the difference, i tested and the MP4 player accepts files of a wide range of bitrate.

```
mediainfo football.avi 

General
Complete name                    : football.avi
Format                           : AVI
Format/Info                      : Audio Video Interleave
File size                        : 18.7 MiB
Duration                         : 3mn 0s
Overall bit rate                 : 868 Kbps
Writing application              : MEncoder Sherpya-MinGW-20060312-4.1.0
Writing library                  : MPlayer

Video
ID                               : 0
Format                           : MPEG-4 Visual
Codec ID                         : XVID
Codec ID/Hint                    : XviD
Duration                         : 3mn 0s
Bit rate                         : 794 Kbps
Width                            : 176 pixels
Height                           : 220 pixels
Display aspect ratio             : 0.800
Frame rate                       : 18.000 fps
Bits/(Pixel*Frame)               : 1.139
Stream size                      : 17.0 MiB (91%)

Audio
ID                               : 1
Format                           : MPEG Audio
Format version                   : Version 1
Format profile                   : Layer 2
Codec ID                         : 50
Duration                         : 3mn 0s
Bit rate mode                    : Constant
Bit rate                         : 64.0 Kbps
Channel(s)                       : 2 channels
Sampling rate                    : 44.1 KHz
Stream size                      : 1.38 MiB (7%)
Alignment                        : Split accross interleaves
Interleave, duration             : 26 ms (0.47 video frame)
Interleave, preload duration     : 522 ms

```

```
mediainfo proba2.avi 

General
Complete name                    : proba2.avi
Format                           : AVI
Format/Info                      : Audio Video Interleave
File size                        : 10.8 MiB
Duration                         : 3mn 57s
Overall bit rate                 : 383 Kbps

Video
ID                               : 0
Format                           : MPEG-4 Visual
Codec ID                         : XVID
Codec ID/Hint                    : XviD
Duration                         : 3mn 57s
Bit rate                         : 312 Kbps
Width                            : 176 pixels
Height                           : 220 pixels
Display aspect ratio             : 0.800
Frame rate                       : 18.000 fps
Bits/(Pixel*Frame)               : 0.448
Stream size                      : 8.82 MiB (81%)

Audio
ID                               : 1
Format                           : MPEG Audio
Format version                   : Version 1
Format profile                   : Layer 2
Codec ID                         : 50
Duration                         : 3mn 56s
Bit rate mode                    : Constant
Bit rate                         : 64.0 Kbps
Channel(s)                       : 2 channels
Sampling rate                    : 44.1 KHz
Stream size                      : 1.80 MiB (17%)
Alignment                        : Aligned on interleaves
Interleave, duration             : 56 ms (1.00 video frame)

```

```
mediainfo Garbage\ -\ I\'m\ Happy\ Only\ When\ It\ Rains.avi 

General
Complete name                    : Garbage - I'm Happy Only When It Rains.avi
Format                           : AVI
Format/Info                      : Audio Video Interleave
File size                        : 25.3 MiB
Duration                         : 3mn 57s
Overall bit rate                 : 895 Kbps
Writing application              : MEncoder dev-SVN-r27958-4.2.2
Writing library                  : MPlayer

Video
ID                               : 0
Format                           : MPEG-4 Visual
Codec ID                         : XVID
Codec ID/Hint                    : XviD
Duration                         : 3mn 57s
Bit rate                         : 788 Kbps
Width                            : 176 pixels
Height                           : 220 pixels
Display aspect ratio             : 0.800
Frame rate                       : 18.000 fps
Bits/(Pixel*Frame)               : 1.130
Stream size                      : 22.3 MiB (88%)

Audio
ID                               : 1
Format                           : MPEG Audio
Format version                   : Version 1
Format profile                   : Layer 2
Codec ID                         : 50
Duration                         : 3mn 56s
Bit rate mode                    : Constant
Bit rate                         : 96.0 Kbps
Channel(s)                       : 2 channels
Sampling rate                    : 44.1 KHz
Stream size                      : 2.71 MiB (11%)
Alignment                        : Aligned on interleaves
Interleave, duration             : 26 ms (0.47 video frame)
Interleave, preload duration     : 522 ms

```

I mark the thread SOLVED, but if you have ideas do not hesitate to post it.

---

### Post by rayoncena on 2010-07-02
I was having same issue and was not able to find the solution but finally found the solution. It was great to use the viDrop , it has resolved my problem too.

---

### Post by littlepeon on 2010-07-06
taken from the author:

" the encoding itself is made in mencoder. viDrop is just a GUI frontend to mencoder (which is only command line application). And the installer is so big, because it includes mplayer and mencoder"

given that, u can use any linux friendly gui frontends to mencoder/mplayer (available in the restricted repositories) to produce the same results.

personally, i use ffmpeg and its frontend winff to produce my transcodes for various mp4 players.

you just have to tinker around and see what the limits are to your particular player and what limitations they have placed on your chipset.

i would suggest just transcoding a 2-3 minute file and seeing what your best/worst quality limits are.

have fun
-Peon

---

