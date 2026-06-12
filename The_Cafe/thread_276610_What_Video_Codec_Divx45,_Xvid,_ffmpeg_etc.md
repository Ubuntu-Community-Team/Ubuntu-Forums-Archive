---
title: "What Video Codec?? Divx4/5, Xvid, ffmpeg etc"
date: 2006-10-13
forum: The Cafe
---

### Post by ixus_123 on 2006-10-13
Hello. I'm backing up my DVD collection to hard disk so I can put the originals in the attic & free up some shelf space.


I used to Acidrip to encode with lavc & mp3 for sound & have been happy with results.  Last week I finally got dvdrip to work (under root).  I prefer this becuase (hopefully - haven't tested it yet) I can leave the & have commentaries etc).

Thing is I'm not sure what video codec to use?  divx4, dix5, xvid, xvid3, xvid4, ffmpeg etc.

Could someone perhaps explain or link to the pros & cons of each?
Any other codecs worth mentioning?  I don't have H.264 although hear it's good - do I just drop the source somewhere to install or do I have to reinstall dvdrip for it to recognise it?

I'm not concerned with processing time as I usually set up the computer to trascode before I go to bed or go out.

Also a format that a multiplatform media player can read would be ideal - VLC for example

---

### Post by pay on 2006-10-13
When I encode I use x264 video (H264) with Vorbis Audio in a Matroska container with chapters muxed in. H264 offers better comparision than H263. divx 4 and 5 are closed source and I prefer opensource software Xvid and ffmpeg are opensource. Out of those 3 I would pick Xvid.

VLC and most Linux players can play .mkv files and all of them (provided you have the codecs installed and since you are creating the files you would have to have them installed) can play mpeg4 files.

---

### Post by pay on 2006-10-13
heres a comparison of codecs
[http://www.doom9.org/index.html?/codecs-main-105-1.htm](http://www.doom9.org/index.html?/codecs-main-105-1.htm)
also doom9 has alot of information about htis sorta thing.

---

### Post by ago on 2006-10-13
Theora?

---

### Post by ixus_123 on 2006-10-13
Thanks for the link :)

I had googled that site but the only info I could films was a test from 2003 - your link is much better.

I've just installed x264 from svn & installed with the usual ```
./configure && make && sudo make install
```
I hope it works.  Currently transcoding a DVD so can't test it for a few hours but I'm hoping DVDRIP will just recognise it or do you think that would have to be reinstalled?

I used to encode audio at 128kbps MP3 but the original sound track isn't much larger so I decided just to preserve that.  File size isn't really an issue as long as I have hard disk space.  Currently I think around 1 gig is good with 1.5 being my upper limit.

I hadn't really given any thought at all to container formats using .avi - some of the alternatives look interesting especially if the add features like menus etc - I think I need to read up on these

---

### Post by ago on 2006-10-13
> **ago said:**
> Theora?

[http://thoggen.net/](http://thoggen.net/)

---

### Post by zenwhen on 2006-10-13
Theora here too. I am backing them up for me, not for the worlds consumption. I use free standards wherever I can.

---

### Post by M7S on 2006-10-13
What size is needed for a more or less transparent reencoding of a two hour movie with theora in your opinoin? For me a transparent reencoding with xvid takes about a half (4.7 Gb) dvd.

---

### Post by ixus_123 on 2006-10-15
well I've hapily been encoding 40 minute episodes of a TV series at 720pixels wide & x264 turns out a file size of about 184mb - amazing considering the same at 640 wide with xvid was about 480mb!!

I know I said file size wasn't an issue but this is a huge difference.

I have to say though, for quality xvid seems to be better - less blocky in dark scenes or scences of blured out / single colour backgrounds - perhaps becuase I encoded 2 pass in xvid?  Not sure if this is possible in x264.

Totem will happily play the x264 files as will mplayer but weirdly VLC hates them & the window will keep changing sizes or play back like a corrupted file - amazing considering I downloaded the x264 from the VLC website

---

### Post by pay on 2006-10-15
x264 is defintly capable of 2 pass and xivd and x264 at the same file size with the same resolution and options, x264 will look much better.

---

### Post by ixus_123 on 2006-10-19
Really!?  Could you help me?

What would I have to add to this to make it 2 pass?

```
mencoder dvd://3 -dvd-device /dev/dvd  -alang English   -info srcform="DVD ripped by acidrip.sf.net":name="24":genre="TV" -oac copy -af volume=4:sc -ovc x264 -vf pp=de,crop=0:0:0:0,scale=720:-2    -o "/home/kieren/24-se1_ep15.avi"
eject /dev/dvd 2> /dev/null
unlink frameno.avi 2> /dev/null
mencoder dvd://4 -dvd-device /dev/dvd  -alang English   -info srcform="DVD ripped by acidrip.sf.net":name="24":genre="TV" -oac copy -af volume=4:sc -ovc x264 -vf pp=de,crop=0:0:0:0,scale=720:-2    -o "/home/kieren/24-se1_ep16.avi"
eject /dev/dvd 2> /dev/null
```

---

### Post by pay on 2006-10-20
mencoder -ova copy -ovc x264 -x264encopts pass=1 -o video.mp4
mencoder -oac copy -ovc x264 -x264encopts pass=2:bitrate=1200 video -o video.mp4

I think... Can someone verify correct this?

---

### Post by ixus_123 on 2006-10-20
Thanks - haven't tried it yet.

Downloaded OGMrip which is also a frontend to mencoder.  The good thing is it will let me do 3 pass encoding (1*audio 2*video) with x264 & I can rip as many audio tracks as I like so I can finally include directors commnetaries.

Still getting used to it at the moment.  Even though it's just a front end to Acidrip it seems to take about 4* as long to rip - no iea what's going on there?

---

### Post by billl on 2006-11-13
OGMRip is not a frontend to AcidRip. But both are frontends to mencoder. The time it takes to rip depends on the codec and the quality you select. OGMRip uses very high quality settings by defaults and x264 is not a very optimised codec yet.

Cheers,

Olivier

---

### Post by shining on 2006-11-13
I tested a bit encoding in mplayer. With x264, the quality difference was indeed nice (it looked nicer), but the encoding time difference was much bigger (awfully long). I also read x264 decoding is much more resource consuming. But encoding/decoding in x264 are probably not fully optimized yet.
Anyway, I just used xvid or lavc, which gave me both reasonable and comparable results. Though, they are both mpeg-4 codec, which is patented. Same for h264.
So theora is probably worth a try.

---

### Post by jocheem67 on 2006-11-13
I've been investigating on converting dvd for quite a while now.

I'm definitely not an expert on all the details and think that the command-line is way too complicated...

Here are my findings though:

I'm using three programs: acidrip, dvd::rip and avidemux. Mencoder, transcode, and ffmpeg are the backends respectively.
I have the best results  with dvd::rip using xVid, lame and a two-pass encode. ( There is a lot of discussion going on on the net about the advantages of even more passes, there is a point offcourse where 3 or more passes are just not gaining that much anymore. )

Mencoder ( acidrip ) is known for not the best A/V syncing as is avidemux. A point for transcode thus ( dvd::rip )

I'm using xVid because I want to keep the option open to play my files on my standalone dvd/xVid/divX player.

Haven't tried x.264 yet, though it's gonna be the codec for the future, it's compressing like a charm, but I'm afraid my player won't eat the video's...

Dvd::rip also makes nice .sub files which I make into .srt's in XP with subsync.

Last advantage of dvd::rip is the possibilities of usoing all kionds of filters.

Ffmpeg they say is the fastest encoder, but that is not an issue for me.
Funny thing is that my video's done with avidemux are identified as being divX. Don't really know why..

cheers.

---

### Post by Hobbes on 2006-11-16
I'm definitely a noob to the whole dvd ripping and transcoding game... I've just ripeed my dvds in the past with dvdshrink and left it at that..

It's been a while since I tried any of the linux-friendly options, but I've been exclusively in ubuntu for a while, and figured I'd have another go.  Anyway, I tried dvd::rip, and much like my previous attempt in ages past, I ended up with a file whose audio is out of sync.  I left all the default options, ie Xvid encoding, 2-pass, mp3, etc...

Anyway of knowing what I'm doing wrong, or is there a good guide out there for understanding dvd::rip better?

Thanks for any help.

---

### Post by cgreulich on 2006-11-18
I had the same a/v sync issue with my ntsc movies....untill I realized I needed to enable PSU Core.  I have no idea what it is, but it works!

After many, many problems with DVD::rip I settled on using xvid, 2 pass, Smart deinterlacing, PSU core, resolution of 528x304, and I seem to be getting about 18 FPS durring each pass.

---

### Post by ixus_123 on 2006-11-18
Cheers for the correction Bill :)

That was just a typo.  I did say in the first paragraph that OGMrip & Acidrip are frontends to mencoder.

I'm really loving OGMrip now although don't understand the settings fully as I can't be bothered to experiment changing the bit mode.  I encode at high quality x.264 with 3 pass encoding (2 video, one sound). Sound is a copy for 5.1 or converted to ogg for anything in stereo. I limit file sizes to 1024mb.

Currently it takes about 10 hours to transcode a DVD - painfully long so I usually set it to go off when I leave for work.  It would be nice if you could queue things un in OGMrip, the way you can in acidrip.

Also having a problem with subtitles in OGMrip - it conflicts with the defualt subtitle program so I don't know what I use for subs but it get them all wrong with upper & lower case letters, gaps in words, poor spelling etc. :(

> **billl said:**
> OGMRip is not a frontend to AcidRip. But both are frontends to mencoder. The time it takes to rip depends on the codec and the quality you select. OGMRip uses very high quality settings by defaults and x264 is not a very optimised codec yet.

Cheers,

Olivier

---

### Post by JPMaximilian on 2007-02-01
> **pay said:**
> When I encode I use x264 video (H264) with Vorbis Audio in a Matroska container with chapters muxed in. H264 offers better comparision than H263. divx 4 and 5 are closed source and I prefer opensource software Xvid and ffmpeg are opensource. Out of those 3 I would pick Xvid.

VLC and most Linux players can play .mkv files and all of them (provided you have the codecs installed and since you are creating the files you would have to have them installed) can play mpeg4 files.


What software do you use to do this?

---

### Post by mips on 2007-02-01
If file size is not an issue simply write them to the HD as an .iso disk image. You can even mount the image and play it back from hard drive. Also gives you a perfect copy of your original should anything happen to it.

---

### Post by Mateo on 2007-02-01
use xvid, it's the most widely used (along with divx).

---

### Post by Mateo on 2007-02-01
I made a script for ripping to xvid.  I tested with a short track and it seemed to work. if you just want it to rip the movie track, simply press enter at the first question, because it rips the biggest track (usually the movie).

```
#!/bin/bash
echo -n "Which track to rip? "
read tracknum
echo -n "What to name the file? "
read filename
mencoder dvd://$tracknum -ovc xvid -xvidencopts pass=1 -alang en -oac copy -o /dev/null
mencoder dvd://$tracknum -ovc xvid -xvidencopts pass=2:bitrate=192000 -alang en -oac mp3lame -lameopts vbr=3 -o "$filename.avi"
rm -f divx2pass.log
```

edit:  after further testing, that produces bad quality video, needs more tweaking.

---

