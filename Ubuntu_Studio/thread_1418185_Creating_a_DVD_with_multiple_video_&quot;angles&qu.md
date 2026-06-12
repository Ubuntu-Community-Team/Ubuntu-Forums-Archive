---
title: "Creating a DVD with multiple video &quot;angles&quot; (streams)"
date: 2010-02-28
forum: Ubuntu Studio
---

### Post by Ferrat on 2010-02-28
This is the problem, I have two video sources I want to convert to a DVD with multiple video streams that can switch while playing or from a menu and use the same audio stream. 

The problem is one source is 16:9 and the other 4:3 so I've tried using first mencoder to make both sources to DVD compliant mpgs then using avidemux to add black borders to the 4:3 source to 16:9 (yes I want the black sides) and to strip the audio from the 16:9 source, after that I've found that it seems only ffmpeg can create a MPG with multiple streams but doing all this tends to create what seems a broken mpg. 

The file works in both mplayer and VLC but VLC plays both video streams at the same time and mplayer restarts it and the indexing seems faulty and I get a pixel warning in mplayer.

```
ffmpeg -f dvd -i source-1-with-audio.mpg -g 12 -vcodec mpeg2video -b 4000K -acodec copy -ab 448 -ar 48000 -i source-2-without-audio.mpg -g 12 -vcodec mpeg2video -b 4000K -f dvd output.mpg -newvideo
```

This is the ffmpeg line I use but it seems to work sort of but as I said it's not really flawless and haven't yet had the nerv to try it on a DVD.

Does anyone know a better easier way to do this ect? would be really happy for any help in doing this, been searching all over but most multiple stream discussions are aimed at multiple audio. 

How good is ffmpeg at encoding compared to mencoder? mostly used mencoder for my other movies, also sources are 24FPS and I want 25FPS (PAL) end result mencoder does the speed up really nice, can ffmpeg do the same?

---

### Post by Ferrat on 2010-02-28
Oh noticed ffmpeg has padding so going to try and do everything in one sweap with ffmpeg :) but still any help / tips would be great :)

---

### Post by Ferrat on 2010-02-28
Okey, got it almost working now

```
ffmpeg -i input-source1 -i input-source2

-map 0:0 -map 0.1 -map 1.0 -map 0.3 -map 0.2 

-vcodec mpeg2video -pass 1 -padleft 120 -padright 120 -padcolor 000000 -r 25 -s 480x576
 -aspect 16:9 -b 4000K -maxrate 8100K -bufsize 9800K -qmax 5 -g 12 -mbd 2 

-acodec ac3 -ar 48000 -ab 448K -ac 6 testOUTPUT.mpg 

-vcodec mpeg2video -pass 1 -padleft 0 -padright 0 -r 25 -s 720x576
 -aspect 16:9 -b 4000K -maxrate 8100K -bufsize 9800K -qmax 5 -g 12 -mbd 2 -newvideo 

-scodec copy -slang swe -newsubtitle 

-scodec copy -slang eng -newsubtitle


```
(in one line, just broken up for more "readability")

Well the problem is that the first source doesn't get the black padded lines that it should even though it does get the extra sixze but filles it with the image. 

OUTPUT
```

Seems stream 0 codec frame rate differs from container frame rate: 47.95 (54042/1127) -> 23.98 (24000/1001)
Input #0, matroska, from 'input-source1.mkv':
  Duration: 00:54:43.94, start: 0.000000, bitrate: N/A
    Stream #0.0: Video: h264, yuv420p, 960x720, PAR 1:1 DAR 4:3, 23.98 tbr, 1k tbn, 47.95 tbc
    Stream #0.1(eng): Audio: dca, 48000 Hz, 5.1, s16
    Stream #0.2(eng): Subtitle: 0x0000
    Stream #0.3: Subtitle: 0x0000

Seems stream 0 codec frame rate differs from container frame rate: 47.95 (48000/1001) -> 24.00 (24/1)
Input #1, matroska, from 'input-source2.mkv':
  Duration: 00:54:43.10, start: 0.000000, bitrate: N/A
    Stream #1.0(eng): Video: h264, yuv420p, 1920x1080, PAR 1:1 DAR 16:9, 24 tbr, 1k tbn, 47.95 tbc
    Stream #1.1(eng): Audio: ac3, 48000 Hz, stereo, s16

```

And encoding pre-out
```
Output #0, mpeg, to 'testOUTPUT.mpg':
    Stream #0.0(eng): Video: mpeg2video (hq), yuv420p, 720x576 [PAR 64:45 DAR 16:9], q=2-5, pass 1, 4000 kb/s, 90k tbn, 25 tbc
    Stream #0.1(eng): Audio: ac3, 48000 Hz, 5.1, s16, 448 kb/s
    Stream #0.2(eng): Video: mpeg2video (hq), yuv420p, 720x576 [PAR 64:45 DAR 16:9], q=2-5, pass 1, 4000 kb/s, 90k tbn, 25 tbc
    Stream #0.3(swe): Subtitle: 0x0000
    Stream #0.4(eng): Subtitle: 0x0000
Stream mapping:
  Stream #0.0 -> #0.0
  Stream #0.1 -> #0.1
  Stream #1.0 -> #0.2
  Stream #0.3 -> #0.3
  Stream #0.2 -> #0.4
Press [q] to stop encoding

```

As stated everything seems to work except that the first source doesn't get padded as I want, any ideas??

Edit: padding works if I only use one of the video streams but I really want both

---

### Post by Ferrat on 2010-02-28
Ok update, if I just remove the padding that might work, there shouldn't be a problem having a 4:3 and a 16:9 stream in the same mpg from what I can understand but now I face another problem, there isn't a speed option for ffmpeg like for mencoder?? 

the sources are 23.98 and 24 FPS as you can see and output is 25 FPS, but I get duplication of frames (which I hate) I much rather have the 4% speed change instead of freezing frames, seems [COLOR="Red"]-vsync 0[/COLOR] should be able to do this but I can't seem to find any good explaination on using it? I always get 

```
[mpeg2video @ 0x6bdf20]Error, Invalid timestamp=1, last=4
```

Any ideas??

---

### Post by Ferrat on 2010-03-02
ok, after much fighting I managed to create VOBs with two video tracks and one audio that works in mplayer and vlc, how ever it seems that genisoimage can't handle VOBs with multiple video streams that well, I managed to make it in to VOBs and they work in VLC and mplayer but no program seems able to make them in to a ISO or burn them? anyone have any idea? 
k3b complains that it can't see the end of the size, genisoimage doesn't see the VIDEO_TS as it should saying it has invalid content..

anyone have any ideas?

EDIT. I think the problem is the IFO file only showing 1 video stream not two

---

### Post by DrewBlay on 2010-10-30
thanks
 
_________________________
 
[maths games]("http://www.free-training-tutorial.com/math-games.html")
[free interactive angles games]("http://www.free-training-tutorial.com/angles-games.html")

---

