---
title: "Create Flash FLV Movies with Ubuntu"
date: 2006-10-19
forum: The Cafe
---

### Post by mtron on 2006-10-19
Since Adobe finally released the beta of the Flash Player 9 some days ago, it's finally time for me to digg in this stuff ;)

The Version 7 was totally unuseable, the video and audio sync was totally broken, firefox crashed quite often, the cpu went up to over 80 %... but now it seems ok, so let's start to create a flash movie. :D 
[B]
First you need an unrestricted version of ffmpeg:[/B]

you need to get the [svn version]("http://ffmpeg.mplayerhq.hu/download.html") and compile it for yourself, cause the ubuntu 6.06 build has no lame & xvid encoding enabled, or get my package [here]("http://michael.hoertnagl.googlepages.com/ffmpeg_31.cvs20061020-ubuntu1_i386.deb"). 

My compiling options:

[INDENT]FFmpeg version SVN-r6738, Copyright (c) 2000-2006 Fabrice Bellard, et al.

configuration:  --extra-cflags=-fomit-frame-pointer --enable-xvid --enable-pp --enable-vorbis --enable-libogg --enable-dc1394 --enable-libgsm --disable-debug --enable-mp3lame --enable-faadbin --enable-faad --enable-faac --enable-xvid --prefix=/usr --enable-gpl

ffmpeg SVN-r6738
built on Oct 20 2006 00:29:57, gcc: 4.0.3 (Ubuntu 4.0.3-1ubuntu5)
libavutil version: 49.0.1
libavcodec version: 51.20.0
libavformat version: 50.6.0[/INDENT]
[B]
now get the latest release from [FLVtool2]("http://rubyforge.org/frs/?group_id=1096")[/B]

It's a ruby script which adds metadata to the FLV file to make the progress bar work and letting you skip between bits of the file. The install is easy, just follow the README.

The source video file in this example ("input.mpg") is a DVB-S Transport Stream (generic PES Container 720x576) , recorded with mythtv and converted to a MPG2 video with [ProjectX]("http://sourceforge.net/projects/project-x").

**ok. it's time to fire up a terminal and start the encoding with ffmpeg**

```
ffmpeg -y -i input.mpg -r 20 -s 360x288 -deinterlace -ar 22050 output.flv

```

**Next we need to add the metadata to the flv movie:**
```

cat output.flv | flvtool2 -U stdin final.flv
```

Now we have the finished seek-able flv movie. You can test it with mplayer (seeking doesn't work with mplayer though). To embed it in a webpage, grab yourself a copy of the very good "[flvplayer]("http://pyg.keonox.com/tests/flash_flv_player/flvplayer.swf")", written by joern wijering, and place it in the same directory as the webpage you plan to embed the movie 

here is the html code:
```

<object type="application/x-shockwave-flash" width="360" height="288" wmode="transparent"
data="flvplayer.swf?file=movies/final.flv&autoStart=false&showFs=true">
<param name="movie" value="flvplayer.swf?file=movies/final.flv&autoStart=false&showFs=true" />
<param name="wmode" value="transparent" />
</object>
```

E Voila :KS Have fun! 

Sources for this howto:
- [Flash FLV Player]("http://pyg.keonox.com/tests/flash_flv_player/") by jeroen wijering
- [FLVtool2 documentation]("http://inlet-media.de/")
- [convert mpg - flv in myth]("http://www.mythtv.org/wiki/index.php/Stream_mythtv_recordings_from_mythweb_using_flash_video")
- [ffmpeg documentation]("http://ffmpeg.mplayerhq.hu/documentation.html")

---

### Post by coffeebaron on 2006-11-06
Thanks for the package. Works great.

---

### Post by vayu on 2006-11-07
Very cool, thanks!

---

### Post by mtron on 2006-11-07
Thanks! 

It would be cool if a ffmpeg guru can tell me how to use a 2 pass encoding for the mpg. i didn't find it in the documentation. The rest works very well. i'm using a script to convert my myth recordings to flv and have them streamable on demmand. 

Not that i use it, but nice to have the possibility... :mrgreen:

---

### Post by msumurph on 2006-12-05
Great How-To.  I compiled my own on Edgy, installed FLVTool2, and am now happily converting movies with sound to flv!

Thanks!

---

### Post by dbbolton on 2006-12-05
[http://www.ubuntuforums.org/showthread.php?t=300526](http://www.ubuntuforums.org/showthread.php?t=300526)

---

### Post by mtron on 2006-12-06
> **dbbolton said:**
> [http://www.ubuntuforums.org/showthread.php?t=300526](http://www.ubuntuforums.org/showthread.php?t=300526)

So what? i don't really get your point here...

The commands posted here convert movies to the flv format used in flash.

ah, btw: this can be used to create a live stream (pseudo live, it's about 5 sec behind) from a tv / camera live recording. did this for a discussion @ my university. much cheaper and easier to handle than a streaming server...

---

### Post by liquidpele on 2009-11-19
You'll probably want to up the bitrate though....  the default for ffmpeg is 200 kb/s which is pretty low.  I use a 450x360 size with a 350k bitrate.  You can set the bitrate with "-b 350k" in there.  Just in case others need their output video better quality.

---

