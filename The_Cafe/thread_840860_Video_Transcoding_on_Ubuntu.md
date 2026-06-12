---
title: "Video Transcoding on Ubuntu?"
date: 2008-06-25
forum: The Cafe
---

### Post by BattleGnome on 2008-06-25
I want to transcode a lot of my family DVD's to h.264 format. On the windows side I have an excellent commercial application called DvdFab Platinum. I am wondering if there is a Linux equivalent to this?

I have DVD::RIP on my Ubuntu install but it does not offer H.264 encoding.

I am not necessarily after a 'free' solution, interested in commercial applications as well. I have a Geforce 9800GTX and would be very interested in an app that offers GPU assisted transcoding on the Linux side (there are a couple coming out soon on windows).

---

### Post by madjr on 2008-06-26
these links should help you (i just did a google search)



[http://www.linux.com/feature/125623](http://www.linux.com/feature/125623)

[http://www.zunerama.com/forum/index.php?topic=6623.0](http://www.zunerama.com/forum/index.php?topic=6623.0)

---

### Post by reyfer on 2008-06-26
Doesn't Avidemux support h.264?

---

### Post by billgoldberg on 2008-06-26
Try ffmpeg and it's gui, winff (google for it) to convert the rips.

It might be neccesary to install the ffmpeg version from medibuntu instead of the normal repo's.

---

### Post by Nepherte on 2008-06-26
HOWTO: Rip DVDs in MPEG-4 AVC (x264), multi audio, subtitles, Matroska: [http://ubuntuforums.org/showthread.php?t=273635](http://ubuntuforums.org/showthread.php?t=273635)

---

### Post by mysoogal on 2009-05-04
sudo apt-get install Avidemux 


video codec =x264
audio = AC3 

output container mkv or ogm which ever suits your needs

its a shame it doesnt have a auto watch folder feature :KS

---

### Post by .Maleficus. on 2009-05-04
MEncoder (from the guys that brought you MPlayer).  Use CLI if you're comfortable, otherwise Acidrip is a supposed to be an awesome front-end for it.

---

### Post by Brainy142 on 2009-05-04
+1 for FFMPEG

---

### Post by RD1 on 2009-05-04
[HANDBRAKE!!]("http://handbrake.fr/?article=download") :P

---

### Post by 3rdalbum on 2009-05-05
I've already done this exact project.

I used Acidrip to rip the main titles of the discs into straight copies, and then just before I went to bed there was an ffmpeg script that converted the files to h.264 with multithreading enabled.

The ffmpeg script really just goes like this (for instance) for each title:

```
/usr/bin/ffmpeg -i "tora tora tora-cache" -b 2000000 -vcodec libx264 -deinterlace -ab 128k -ac 2 -ar 44100 -acodec libmp3lame -threads 2 "tora_tora_tora.avi"
```

In the morning I dragged the finished movies to the appropriate folders on my hard disk. Rinse and repeat.

---

### Post by Hallvor on 2009-05-05
> **BattleGnome said:**
> I want to transcode a lot of my family DVD's to h.264 format. On the windows side I have an excellent commercial application called DvdFab Platinum. I am wondering if there is a Linux equivalent to this?

I have DVD::RIP on my Ubuntu install but it does not offer H.264 encoding.

I am not necessarily after a 'free' solution, interested in commercial applications as well. I have a Geforce 9800GTX and would be very interested in an app that offers GPU assisted transcoding on the Linux side (there are a couple coming out soon on windows).

I think DVDFab runs in Wine, so you can also use it on Ubuntu if you like.

The best native application I have used is DVD:Rip

---

### Post by Gryphen on 2010-02-20
[check out my dvd ripping tutorial]("http://ubuntuforums.org/showthread.php?p=8828232#post8828232")

---

### Post by arnab_das on 2010-02-20
handbrake is good, but remember that it doesnt allow you to change resolutions.

i was a big fan of winff, but my lg dvd player simply refuses to play anything coded/converted with it. since then i have switched to devede.

---

### Post by JohnAStebbins on 2010-02-20
> handbrake is good, but remember that it doesnt allow you to change resolutions
I don't know where you got that.  The gui has a picture settings window that is dedicated to tweaking (you guessed it) picture settings. Resolution, aspect ratio, cropping, and filters are all controlled there.

---

### Post by yester64 on 2010-02-20
Try handbrake. It transcodes to H264 very well.
You can't edit video's but it will transcode and encode pretty well.

[http://handbrake.fr/downloads.php](http://handbrake.fr/downloads.php)

---

### Post by Gryphen on 2010-02-20
I've try'd other dvd rippers and handbrake works best for me.

---

### Post by arnab_das on 2010-02-20
> **JohnAStebbins said:**
> I don't know where you got that.  The gui has a picture settings window that is dedicated to tweaking (you guessed it) picture settings. Resolution, aspect ratio, cropping, and filters are all controlled there.

just checked. i was wrong. sorry.

but i guess its still pretty much useless for me coz it cant convert a video into something playable by dvd players. (eg avi, etc.)

---

### Post by Gryphen on 2010-02-23
> **arnab_das said:**
> just checked. i was wrong. sorry.

but i guess its still pretty much useless for me coz it cant convert a video into something playable by dvd players. (eg avi, etc.)
Try devede

---

### Post by tagnu on 2010-10-19
Thank you for the settings.   > **mysoogal said:**
> sudo apt-get install Avidemux 


video codec =x264
audio = AC3 

output container mkv or ogm which ever suits your needs

its a shame it doesnt have a auto watch folder feature :KS

---

### Post by Paqman on 2010-10-19
Sod playing about with settings. Get Arista Transcoder from the repos, hit the preset for "Computer" and feed it the DVD, it'll produce an H.264 file. It's also multi-threaded, which I don't believe Avidemux is. Handbrake is multithreaded, but the stable release of it doesn't work with recent versions of Ubuntu.

Avidemux and Handbrake are powerful apps, but for a simple repetitive task like this they're overkill, and can be confusing.  Arista is a fantastic little app for straightforward transcoding jobs.

---

### Post by NCLI on 2010-10-19
Arista is a great little application. You can find it in the Software Center.

---

### Post by sandyd on 2012-12-19
**Necromancing - thread closed**
As per the Ubuntu Forums Code of Conduct, please do not post in threads more than one year old. 

Thanks!

---

