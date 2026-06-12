---
title: "ffmpeg timelapse duration always 26 seconds"
date: 2011-02-19
forum: Ubuntu Studio
---

### Post by Sezmeralda on 2011-02-19
I have 659 images labelled sequentially, and use the following command to turn them into video with ffmeg:

```
ffmpeg -f image2 -i Trailor_%04d.JPG -r 24 -s 1920x1080 saturday3.avi
```But the duration always comes out as 26.36 seconds.  If I change the frame rate it just uses less frames to make the same length video.  I tried using -t but with no change.  The output does look good, but I want to add another 300 pictures yet, and have the video last at least a minute.  What am I doing wrong?

Here's the output:

> sez@linux-desktop:~/2011-02 Trailer Build/TimeLapse$ ffmpeg -f image2 -i Trailor_%04d.JPG -r 24 -s 1920x1080 saturday3.avi
FFmpeg version SVN-r25242, Copyright (c) 2000-2010 the FFmpeg developers
  built on Sep 28 2010 20:01:32 with gcc 4.4.3
  configuration: --enable-gpl --enable-version3 --enable-nonfree --enable-postproc --enable-libfaac --enable-libopencore-amrnb --enable-libopencore-amrwb --enable-libtheora --enable-libvorbis --enable-libx264 --enable-libxvid --enable-x11grab --enable-libmp3lame --enable-libvpx
  libavutil     50.31. 0 / 50.31. 0
  libavcore      0. 9. 0 /  0. 9. 0
  libavcodec    52.91. 1 / 52.91. 1
  libavformat   52.78. 5 / 52.78. 5
  libavdevice   52. 2. 2 / 52. 2. 2
  libavfilter    1.47. 1 /  1.47. 1
  libswscale     0.11. 0 /  0.11. 0
  libpostproc   51. 2. 0 / 51. 2. 0
Input #0, image2, from 'Trailor_%04d.JPG':
  Duration: 00:00:26.36, start: 0.000000, bitrate: N/A
    Stream #0.0: Video: mjpeg, yuvj422p, 2352x1568, 25 fps, 25 tbr, 25 tbn, 25 tbc
[buffer @ 0x24760f0] w:2352 h:1568 pixfmt:yuvj422p
[scale @ 0x27a47c0] w:2352 h:1568 fmt:yuvj422p -> w:1920 h:1080 fmt:yuv420p flags:0xa0000004
Output #0, avi, to 'saturday3.avi':
  Metadata:
    ISFT            : Lavf52.78.5
    Stream #0.0: Video: mpeg4, yuv420p, 1920x1080, q=2-31, 200 kb/s, 24 tbn, 24 tbc
Stream mapping:
  Stream #0.0 -> #0.0
Press [q] to stop encoding
frame=  633 fps= 10 q=31.0 Lsize=    6725kB time=26.38 bitrate=2088.9kbits/s dup=0 drop=26    
video:6705kB audio:0kB global headers:0kB muxing overhead 0.308966%I am using Ubuntu 10.04 LTS and I don't really know what I'm doing.  Most of the time I trawl forums to work out how to get something to work but I can't find anything like this problem.  Any help would be appreciated.

---

### Post by FakeOutdoorsman on 2011-02-19
This sort of thing can be confusing, but you're on the right track. Are you going to add 300 more images to the initial 659? What would you like the output duration to be?

---

### Post by Sezmeralda on 2011-02-19
I'm guessing about 300 photos or so - the guys are going to do more work today as the project we're documenting isn't finished.
The project leader wants a time lapse video of about a minute duration, but he can be flexible if he has to.

Thanks for the encouragement :D

---

### Post by FakeOutdoorsman on 2011-02-19
With ~960 images / 60 second duration = ~15 fps for the input:
```
ffmpeg -r 15 -i input -vf scale=1920:-1 -qscale 3 -r foo output.avi
```
I don't have access to FFmpeg right now, and I like to test any suggestion I give, so this may not work as expected.

Replace *-r foo* with whatever frame rate you want the output to be. Or omit it entirely if you want it to inherit the input frame rate of *-r 15*. Not all encoders will accept arbitrary output frame rates however, but the encoder will tell you if it doesn't like it. If you do not declare a frame rate for the input when making a movie from single images like this then FFmpeg will use a default of 25 fps.

I added *-qscale 3* so the output quality should be better than the default of 200 kilobits per second, and *-vf scale=1920:-1* will automatically scale the height relative to your width (or vise versa).

Also, do you require AVI for some reason? I generally rarely use that container format.

---

### Post by Sezmeralda on 2011-02-19
Thanks, I'll give this a go.
There's no special reason for avi, you recommend something else?

---

### Post by Sezmeralda on 2011-02-20
FakeOutdoorsman, your solution worked a treat!  We ended up with about 1300 photos and still made a very good looking 1min video.  Thank you for the extra tips on quality and WxH, they were super too.

As to the .avi format, I really only chose that because I guess I see it around a lot.  The Project Leader doesn't like it either as he can't play my output on his Vista laptop.  What would you recommend here?

---

### Post by FakeOutdoorsman on 2011-02-21
I recommend that the Project Leader install a capable media player such as [VLC](http://videolan.org/"). I'm not sure what tye of device or playback method you will use for these videos or if you have any limitations such as file size.

Generally though you can't go wrong with H.264 video. Since you already compiled FFmpeg I would use a command such as:
```
ffmpeg -r 15 -i input -vcodec libx264 -vpre medium -crf 22 -threads 0 -vf scale=1920:-1 -r foo -metadata title="Example Title" output.mp4
```
See the [FFmpeg x264 encoding guide]("http://rob.opendot.cl/index.php/useful-stuff/ffmpeg-x264-encoding-guide/") for more examples.

---

### Post by Sezmeralda on 2011-02-21
Ha! Yeah I use VLC myself.  Thank you for all your help, you've been such a boon.  I have a lot of stuff I can study now to improve my understanding too.

All the best,
~Sez

---

