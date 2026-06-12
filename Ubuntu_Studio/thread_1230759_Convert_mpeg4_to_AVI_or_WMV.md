---
title: "Convert mpeg4 to AVI or WMV"
date: 2009-08-03
forum: Ubuntu Studio
---

### Post by PerfectReign on 2009-08-03
I've been searching, tried avidmux, tried ffmpeg found this ([http://ubuntuforums.org/showthread.php?t=801182](http://ubuntuforums.org/showthread.php?t=801182)) among others but cannot seem to find a way to convert a file to a playable format for Wintendo computers.

I am in a shop using Wintendo XP/Vista/7 computers. I have a video I want to distribute. Most people do not have VLC installed and many don't have quicktime. The video is in quicktime format (producted on an Apple Macintosh using final cut).  

I tried simply ffmpeg -i myvideo.mpg myvideo.avi or ffmpeg -i myvideo.mpg myvideo.wmv but Windows Media Player cannot seem to find the correct codec. (Windows player 1.0 codec apparently.)

Ideas?

---

### Post by -=hazard=- on 2009-08-03
> **PerfectReign said:**
> I've been searching, tried avidmux, tried ffmpeg found this ([http://ubuntuforums.org/showthread.php?t=801182](http://ubuntuforums.org/showthread.php?t=801182)) among others but cannot seem to find a way to convert a file to a playable format for Wintendo computers.

I am in a shop using Wintendo XP/Vista/7 computers. I have a video I want to distribute. Most people do not have VLC installed and many don't have quicktime. The video is in quicktime format (producted on an Apple Macintosh using final cut).  

I tried simply ffmpeg -i myvideo.mpg myvideo.avi or ffmpeg -i myvideo.mpg myvideo.wmv but Windows Media Player cannot seem to find the correct codec. (Windows player 1.0 codec apparently.)

Ideas?

try -r and not -i

-edit-

sry thats not the prob

I can successfully convert mpg videos to avi with this parameters 

-r 29.97 -vcodec libxvid -vtag XVID -s 704x384 -aspect 16:9 -maxrate 1800k -b 1500k -qmin 3 -qmax 5 -bufsize 4096 -mbd 2 -bf 2 -flags +4mv -trellis -aic -cmp 2 -subcmp 2 -g 300 -acodec libmp3lame -ar 48000 -ab 128k -ac 2

this is a default one for xvid 16:9

or try this codec for wmv:    -vcodec wmv2

---

### Post by ArmenianLeader4 on 2009-08-03
[http://media-convert.com/](http://media-convert.com/)

There's you're problem!

---

### Post by -=hazard=- on 2009-08-03
> **ArmenianLeader4 said:**
> [http://media-convert.com/](http://media-convert.com/)

There's you're problem!

Thats the easy way lol

---

### Post by bumanie on 2009-08-05
Try winff which is a graphical version of ffmpeg, might be easier than cli. There is also avidemux which does a good job too - it will at least convert to .avi - not sure about it converting to .wmv - don't use windows, so never tried.

---

### Post by wkulecz on 2009-08-05
Installing the K-lite codec pack is the best way to solve video playback problems on Windows 2000 thru Win7RC1.

I've done some tests creating mp4 video from HD video clips and mp4 "IPOD profile" from Sony Vegas Movie Studio 9 Platnium or KDEnlive in 320x240 or 640x480 are the same or better quality and significantly smaller than the wmv files produced from the same source using Rin7RC1 Windows Movie Maker.

After installing the K-lite codecs on windows these mp4 files play fine.

Use an inferior codec or update windows codecs, can be a tough choice.  I still make a lot of mpeg1 clips simply because if they can't play these, forget-about-it.

--wally.

---

### Post by PerfectReign on 2009-08-06
I gave up.

I'd try and convert to .wmv and it woudl play fine on my Ubuntu system. However the XP or Vista or Win7 systems would all require some codec.

Any .AVI i tried seemed to bomb also. Either I'd get sound an no video or video and no sound.


I just ended up posting on YouTube.  :P

---

### Post by andrew.46 on 2009-08-06
Hi PerfectReign,

> **PerfectReign said:**
> I'd try and convert to .wmv and it woudl play fine on my Ubuntu system. However the XP or Vista or Win7 systems would all require some codec.

If you want to persist for a little longer try this one:

```
ffmpeg -i *infile* -vcodec wmv2 -sameq -acodec wmav2 outfile.asf
```

and I think you will find that this will play on a windows system with no trouble. The only problem might be the age of your version of FFmpeg as I am not sure when these 2 codecs came into use with FFmpeg. Certainly works well with the svn FFmpeg though.

Andrew

---

