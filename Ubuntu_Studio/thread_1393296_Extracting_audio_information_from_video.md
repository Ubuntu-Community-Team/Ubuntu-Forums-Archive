---
title: "Extracting audio information from video"
date: 2010-01-29
forum: Ubuntu Studio
---

### Post by Mustache Villain on 2010-01-29
Hello.

I'm trying to extract audio information from a Flash video file, specifically audio bitrate information. I tried using ffmpeg2theora and ffmpeg but both only return limited information about the audio. Listing only audio codec, channel, and samplerate. Are there any other tools available in GNU/Linux that will give me a bit more detailed information?

---

### Post by ron999 on 2010-01-29
Hi
I use **mediainfo**.
There's a gui version too.
In Ubuntu's repo.
This is a typical result:-
> General
Complete name                    : rpico.flv
Format                           : Flash Video
File size                        : 8.72 MiB
Duration                         : 4mn 27s
Overall bit rate                 : 274 Kbps

Video
Format                           : VP6
Duration                         : 4mn 27s
Bit rate                         : 190 Kbps
Width                            : 504 pixels
Height                           : 284 pixels
Display aspect ratio             : 16:9
Frame rate mode                  : Variable
Stream size                      : 6.06 MiB (69%)

Audio
Format                           : MPEG Audio
Format version                   : Version 1
Format profile                   : Layer 3
Duration                         : 4mn 27s
Bit rate mode                    : Constant
Bit rate                         : 64.0 Kbps
Channel(s)                       : 1 channel
Sampling rate                    : 44.1 KHz
Resolution                       : 16 bits
Stream size                      : 2.04 MiB (23%)



---

### Post by Mustache Villain on 2010-01-29
> **ron999 said:**
> Hi
I use **mediainfo**.
There's a gui version too.
In Ubuntu's repo.
This is a typical result:-

Thank you for replying. This is exactly what I was looking for. Thanks again.

This is just for anyone else who's looking for it:

[LIST]
[*] Main site: [URL="http://mediainfo.sourceforge.net/"]http://mediainfo.sourceforge.net/

[/URL]
[*] PPA: [https://launchpad.net/~shiki/+archive/mediainfo]("https://launchpad.net/%7Eshiki/+archive/mediainfo")
[/LIST]

---

