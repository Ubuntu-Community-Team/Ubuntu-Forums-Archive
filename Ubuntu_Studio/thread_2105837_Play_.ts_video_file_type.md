---
title: "Play *.ts video file type"
date: 2013-01-17
forum: Ubuntu Studio
---

### Post by Exp3rt on 2013-01-17
I have video file with (.ts) extension on my computer. On MS Windows i can play it by VLC Player or Pot Player. but now i can not open it on my Ubuntu with VLC. which player I can use?:confused:

---

### Post by ajgreeny on 2013-01-17
Where did the file come from?

Have you got all codecs installed that are available?

I can play some, but not all .ts files on my old machine with a single core sempron 2400+ cpu; fully HD files seem to be the problem, simply because my machine is not powerful enough.

I can use VLC, which is my main choice for videos, but mplayer works, as do gnome-mplayer, smplayer, and probably others, but not totem or banshee for some reason.

The .ts suffix does not tell you what the file really as it is just a "container" for media files.  Try running **mediainfo** for all details of the files included. As an example, here's the detailed output of one of my .ts files, recorded onto usb on my digital TV from a broadcast by the BBC.
```
user@Lucid:~/Videos/BBC_iPlayer$ mediainfo The\ Story\ of\ Musicals-1.ts 
General
ID                                       : 4171 (0x104B)
Complete name                            : The Story of Musicals-1.ts
Format                                   : BDAV
Format/Info                              : Blu-ray Video
File size                                : 1.93 GiB
Duration                                 : 1h 1mn
Start time                               : UTC 2012-01-05 23:00:04
End time                                 : UTC 2012-01-06 00:02:03
Overall bit rate mode                    : Variable
Overall bit rate                         : 4 458 Kbps
Network name                             : Oxon & Bucks
Original network name                    : UK Digital Terrestrial Television
Country                                  : GBR
Timezone                                 : +00:00:00

Video
ID                                       : 401 (0x191)
Menu ID                                  : 4544 (0x11C0)
Format                                   : MPEG Video
Format version                           : Version 2
Format profile                           : Main@Main
Format settings, BVOP                    : Yes
Format settings, Matrix                  : Custom
Codec ID                                 : 2
Duration                                 : 1h 1mn
Bit rate mode                            : Variable
Bit rate                                 : 4 015 Kbps
Maximum bit rate                         : 15.0 Mbps
Width                                    : 720 pixels
Height                                   : 576 pixels
Display aspect ratio                     : 16:9
Active Format Description                : Letterbox 16:9 image, with alternative 14:9 center
Frame rate                               : 25.000 fps
Standard                                 : PAL
Color space                              : YUV
Chroma subsampling                       : 4:2:0
Bit depth                                : 8 bits
Scan type                                : Interlaced
Scan order                               : Top Field First
Compression mode                         : Lossy
Bits/(Pixel*Frame)                       : 0.387
Stream size                              : 1.74 GiB (90%)

Audio
ID                                       : 402 (0x192)
Menu ID                                  : 4544 (0x11C0)
Format                                   : MPEG Audio
Format version                           : Version 1
Format profile                           : Layer 2
Codec ID                                 : 3
Duration                                 : 1h 1mn
Bit rate mode                            : Constant
Bit rate                                 : 256 Kbps
Channel(s)                               : 2 channels
Sampling rate                            : 48.0 KHz
Compression mode                         : Lossy
Delay relative to video                  : -263ms
Stream size                              : 114 MiB (6%)
Language                                 : English

Text
ID                                       : 405 (0x195)
Menu ID                                  : 4544 (0x11C0)
Format                                   : DVB Subtitle
Codec ID                                 : 6
Duration                                 : 1h 1mn
Delay relative to video                  : 5s 994ms
Language                                 : English

Menu
ID                                       : 400 (0x190)
Menu ID                                  : 4544 (0x11C0)
Duration                                 : 1h 1mn
List                                     : 401 (0x191) (MPEG Video) / 402 (0x192) (MPEG Audio, English) / 405 (0x195) (DVB Subtitle, English)
Language                                 :  / English / English
Service name                             : BBC FOUR
Service provider                         : BBC
Service type                             : digital television
```

---

### Post by Exp3rt on 2013-01-17
> **ajgreeny said:**
> I can play some, but not all .ts files on my old machine with a single  core sempron 2400+ cpu; fully HD files seem to be the problem, simply  because my machine is not powerful enough.My system information is Laptop Dell Inspiron 5010 with Core i 3 cpu & 4 GB system memory.
> **ajgreeny said:**
> I can use VLC, which is my main choice for videos, but mplayer works, as  do gnome-mplayer, smplayer, and probably others, but not totem or  banshee for some reason.Now I had download [COLOR=Red]M player[/COLOR]. I can hear its sound but has no display. It's streaming like an audio file.
> **ajgreeny said:**
>  Try running **mediainfo** for all details of the files included.How i can find these media informations?

---

### Post by jejeman on 2013-01-17
Mediainfo is a program to view media info.
Install it and see the caracteristics of your file.

---

