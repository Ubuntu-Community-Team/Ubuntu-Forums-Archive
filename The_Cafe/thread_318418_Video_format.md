---
title: "Video format?"
date: 2006-12-13
forum: The Cafe
---

### Post by Pyro MX on 2006-12-13
Hi,

I need to encode a video in a format that would be viewable for the most PCs. It would need to be playable in Windows Media Player, but I don't want the video to be limited to only this player. I tryed with XVid (which worked pretty well), but WMP needs to download a codec for it.

I tryed to encode in MPEG format, but I don't have an MPEG encoder that works well (on Linux or Windows). Any suggestions? :-k :-D

---

### Post by pay on 2006-12-14
Try libavc codec (I think that is the name) It is included in ffmpeg and mencoder. It is an mpeg1/2 codec.

---

### Post by DoctorMO on 2006-12-14
The problem your going to have is that windows media player doesn't really support very many codecs at all. for instance mpeg 1/2 is what DVDs are encoded to. if you want 3GB video movies than this is the format because it works on all platforms.

What microsoft has done is very clever, they don't support Real Media, H.264, QuickTime, Mpeg4 DivX, Ogg Theora or any other good format for encoding video into small files or streams.

What they do support is wmv which is a propritory, windows only monopolised format which I would recomend against using at all costs.

You may end up forcing users to download a client or plugin to play your content, but in the end they only need to do that once. and if you can make it rediculasly easy to install; no one will complain even if it's the vlc or mplayer for windows (which support loads of things, so you'll be helping support more formats)

Does this video want to be embeded in a webpage? perhaps flash video is the anwser? or java video (a bit slow) but at least you don't need to worry about codecs because you can send the codec along with the video in java.

The best anwser I think is to try and compramise a little, your not going to get a good video format to work on a blank windows xp or windows vista install without selling out to the devil. you might as well get a decent codec or player installed that the user can use for other things.

---

### Post by Sluipvoet on 2006-12-14
A very good Windows Video Converter is WinAvi, it has very easy GUI, unfortunately it is not freeware.
Mencoder is a good Linux converter but you will have to work with the command line.
Both of them can easily convert to Mpeg

---

### Post by Kimm on 2006-12-14
I have a script for converting Any video format to mpeg2, I dont have it right now since I'm at school, but I can post it when I get back home :)

My script uses mencoder btw...
You could also experiment with Transcode in VLC :)

---

### Post by hanzomon4 on 2006-12-14
I use ffmpeg for all of my conversions... It looks difficult at first but once you learn it it's super easy, I use it to convert my videos to something compatible with my ipod. I did have to compile it myself because the repo version(at least in dapper) isn't compiled with support for all of the formats ffmpeg can play with.... legal issues I think

---

### Post by Pyro MX on 2006-12-14
> **DoctorMO said:**
> The problem your going to have is that windows media player doesn't really support very many codecs at all. for instance mpeg 1/2 is what DVDs are encoded to. if you want 3GB video movies than this is the format because it works on all platforms.

What microsoft has done is very clever, they don't support Real Media, H.264, QuickTime, Mpeg4 DivX, Ogg Theora or any other good format for encoding video into small files or streams.

What they do support is wmv which is a propritory, windows only monopolised format which I would recomend against using at all costs.

You may end up forcing users to download a client or plugin to play your content, but in the end they only need to do that once. and if you can make it rediculasly easy to install; no one will complain even if it's the vlc or mplayer for windows (which support loads of things, so you'll be helping support more formats)

Does this video want to be embeded in a webpage? perhaps flash video is the anwser? or java video (a bit slow) but at least you don't need to worry about codecs because you can send the codec along with the video in java.

The best anwser I think is to try and compramise a little, your not going to get a good video format to work on a blank windows xp or windows vista install without selling out to the devil. you might as well get a decent codec or player installed that the user can use for other things.

The video is to be distributed on a CD - and maybe not everybody that is going to have it have internet. Right now the best results came from the XVid encoder - it had great quality and the codec downloaded seamlessly on WMP. And the video worked on other media players. However, it needs the user to have an internet connection. And I don't know if all the versions of WMP download the codecs automatically. Don't worry, WMV is not an option. :mrgreen: The video won't be larger than 200mb. I'll try the MPG1/2. I'll give you news on this. 

Of course Kimm, if you have a script, you can show me that I'll be happy to try it out! :)

---

### Post by shining on 2006-12-14
> **Pyro MX said:**
> The video is to be distributed on a CD - and maybe not everybody that is going to have it have internet. Right now the best results came from the XVid encoder - it had great quality and the codec downloaded seamlessly on WMP. And the video worked on other media players. However, it needs the user to have an internet connection. And I don't know if all the versions of WMP download the codecs automatically. Don't worry, WMV is not an option. :mrgreen: The video won't be larger than 200mb. I'll try the MPG1/2. I'll give you news on this. 


Couldn't you include MPlayer or VLC on the CD ?
If the video is only 200mb, that should let you some free space.

---

### Post by Kimm on 2006-12-14
Here is the script I was talking about! :D

Save it as "transcode" (or whatever you like) in /usr/bin or /usr/local/bin

```

#!/bin/bash

mencoder -channels 6 -oac lavc -ovc lavc -of mpeg -mpegopts format=dvd -vf harddup -srate 48000 -lavcopts vcodec=mpeg2video:vrc_buf_size=1835:vrc_maxrate=9800:vbitrate=6000:keyint=15:acodec=ac3:abitrate=192:aspect=16/9 -ofps 30000/1001 "$1" -o "$2" 

```

The syntax for using it is (in terminal):
transcode <original file> <output file>

Edit:
I should mention that this requires mencoder and possibly w32codecs

---

### Post by Pyro MX on 2006-12-16
The script worked like magic! Thanks a lot! If I want to change the video bitrate, is that the vrc_maxrate parameter that I must change?

---

### Post by user1397 on 2006-12-16
let me introduce you to the wonders of [tovid]("http://tovid.org")!

tovid is a program (or more correctly a collection of scripts) that let you 
convert video files from almost every format to mpeg, using mplayer/mencoder, or ffmpeg if you wish.

i have a guide in my sig that is based on tovid, so if you want to try that...

at least for future movies that you'll want to make, you should try tovid, it really is an amazing application.

btw, you don't have to burn the mpeg to a dvd if you don't want to, you could simply just encode the video file to mpeg and leave it on your computer.[U][URL="http://plaza.ufl.edu/nebreuer/tovid_sample.bmp"]
[/URL][/U]

---

### Post by Pyro MX on 2006-12-17
I'll look it out! thanks! :)

---

