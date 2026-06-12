---
title: "ffmpeg stopping at 130 seconds"
date: 2009-04-24
forum: Ubuntu Studio
---

### Post by daev64 on 2009-04-24
I hope someone can help with this one...

I've got about 12k stills I'm trying to stitch together into a timelapse using ffmpeg in Intrepid using the following command line:

ffmpeg -f image2 -i zz%5d.jpg -s 1080x720 -r 24 -b 2000k video.mp4

My problem is that it stops at 130 seconds and exits. The above settings give me 3119 frames. If I change the framerate to 25, I get 3248 frames. I've tried changing the encoding bitrate, the framerate, the size, etc and removed "-f image2" (what exactly does that do, anyway?) but it always stops at 130 seconds of encoded vid. All of my input files are properly numbered, with no breaks in the sequence (zz00000.jpg to zz11798.jpg).

I've run video-to-video conversions, and that all works as expected. I only see this issue when trying to string together stills.

Any ideas?

dave

---

### Post by FakeOutdoorsman on 2009-04-24
Does FFmpeg give any useful output or error messages?  FFmpeg from the Ubuntu repository (excluding Jaunty Jackalope) is quite old and many bug fixes have been implemented since that revision.  You should try a recent FFmpeg revision to see if it resolves this issue:

[HOWTO: Install and use the latest FFmpeg and x264](http://ubuntuforums.org/showthread.php?t=786095)

---

### Post by daev64 on 2009-04-25
I'll try the re-install tomorrow (today? It's late...). 

Until then, here's the full output from the command:

dave@dave-desktop:~/Desktop/temp$ ffmpeg -i zz%5d.jpg -s 1080x720 -b 2000k -r 24 a.mp4
FFmpeg version r11872+debian_3:0.svn20080206-12ubuntu3.1, Copyright (c) 2000-2008 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-pp --enable-swscaler --enable-x11grab --prefix=/usr --enable-libgsm --enable-libtheora --enable-libvorbis --enable-pthreads --disable-strip --enable-libfaad --enable-libfaadbin --enable-liba52 --enable-liba52bin --enable-libdc1394 --disable-armv5te --disable-armv6 --disable-altivec --disable-vis --enable-shared --disable-static
  libavutil version: 49.6.0
  libavcodec version: 51.50.0
  libavformat version: 52.7.0
  libavdevice version: 52.0.0
  built on Mar 13 2009 17:48:10, gcc: 4.3.2
Input #0, image2, from 'zz%5d.jpg':
  Duration: 00:07:51.9, start: 0.000000, bitrate: N/A
    Stream #0.0: Video: mjpeg, yuvj422p, 1536x1024 [PAR 0:1 DAR 0:1], 25.00 tb(r)
File 'a.mp4' already exists. Overwrite ? [y/N] y
Output #0, mp4, to 'a.mp4':
    Stream #0.0: Video: mpeg4, yuv420p, 1080x720 [PAR 0:1 DAR 0:1], q=2-31, 2000 kb/s, 24.00 tb(c)
Stream mapping:
  Stream #0.0 -> #0.0
Press [q] to stop encoding
frame= 3119 fps= 27 q=19.4 Lsize=   31879kB time=130.0 bitrate=2009.5kbits/s    
video:31852kB audio:0kB global headers:0kB muxing overhead 0.084314%
dave@dave-desktop:~/Desktop/temp$

---

### Post by daev64 on 2009-04-26
FO, first I want to thank you for taking the time to put together the above-linked tutorial for us n00bs. Someday when I get a clue I'll try to do likewise when the need arises. I realised I had a lot of things disabled in my setup.

I took this as an opportunity to rebuild clean with Jaunty. The bad news is that even after following the steps to get a properly compiled version of ffmpeg and codecs, I've still got the exact same issue. Output follows:

ffmpeg -f image2 -i zz%5d.jpg -cropleft 4 -cropright 4 -s 1072x720 -r 24 -vcodec libx264 -vpre hq -crf 22 -threads 0 a.mp4
FFmpeg version SVN-r18693, Copyright (c) 2000-2009 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-postproc --enable-pthreads --enable-libfaac --enable-libfaad --enable-libmp3lame --enable-libtheora --enable-libx264 --enable-libxvid
  libavutil     50. 3. 0 / 50. 3. 0
  libavcodec    52.27. 0 / 52.27. 0
  libavformat   52.32. 0 / 52.32. 0
  libavdevice   52. 2. 0 / 52. 2. 0
  libswscale     0. 7. 1 /  0. 7. 1
  libpostproc   51. 2. 0 / 51. 2. 0
  built on Apr 25 2009 22:40:56, gcc: 4.3.3
Input #0, image2, from 'zz%5d.jpg':
  Duration: 00:07:51.96, start: 0.000000, bitrate: N/A
    Stream #0.0: Video: mjpeg, yuvj422p, 1536x1024, 25 tbr, 25 tbn, 25 tbc
File 'a.mp4' already exists. Overwrite ? [y/N] y
[libx264 @ 0x9574e90]using cpu capabilities: MMX2 SSE2Fast FastShuffle SSEMisalign LZCNT
[libx264 @ 0x9574e90]profile High, level 3.1
Output #0, mp4, to 'a.mp4':
    Stream #0.0: Video: libx264, yuv420p, 1072x720, q=10-51, 200 kb/s, 24 tbn, 24 tbc
Stream mapping:
  Stream #0.0 -> #0.0
Press [q] to stop encoding
frame=   15 fps=  0 q=-1.0 size=       0kB time=10000000000.00 bitrate=   0.0kbiframe=   18 fps= 15 q=23.0 size=       0kB time=10000000000.00 bitrate=   0.0kbiframe= 3118 fps=  8 q=-1.0 Lsize=   70811kB time=129.83 bitrate=4467.9kbits/s    
video:70763kB audio:0kB global headers:1kB muxing overhead 0.066999%
[libx264 @ 0x9574e90]slice I:68    Avg QP:17.81  size: 50469
[libx264 @ 0x9574e90]slice P:1138  Avg QP:19.69  size: 30130
[libx264 @ 0x9574e90]slice B:1912  Avg QP:21.05  size: 18171
[libx264 @ 0x9574e90]consecutive B-frames:  6.9% 21.7% 31.2% 22.7% 17.5%
[libx264 @ 0x9574e90]mb I  I16..4: 16.8% 63.6% 19.7%
[libx264 @ 0x9574e90]mb P  I16..4:  4.4% 20.7%  5.7%  P16..4: 46.3% 12.5%  6.4%  0.0%  0.0%    skip: 4.0%
[libx264 @ 0x9574e90]mb B  I16..4:  0.5%  7.1%  2.5%  B16..8: 46.2%  3.1%  3.3%  direct: 6.9%  skip:30.5%  L0:48.8% L1:48.5% BI: 2.8%
[libx264 @ 0x9574e90]8x8 transform  intra:67.9%  inter:77.4%
[libx264 @ 0x9574e90]direct mvs  spatial:99.7%  temporal:0.3%
[libx264 @ 0x9574e90]coded y,uvDC,uvAC intra:81.5% 62.3% 17.9% inter:35.3% 37.5% 0.3%
[libx264 @ 0x9574e90]ref P L0  47.9% 21.1% 19.0% 12.0%
[libx264 @ 0x9574e90]ref B L0  61.1% 27.2% 11.7%
[libx264 @ 0x9574e90]ref B L1  82.6% 17.4%
[libx264 @ 0x9574e90]SSIM Mean Y:0.9774610
[libx264 @ 0x9574e90]kb/s:4462.0


At which point I'm returned to the command prompt. I don't get it. I've tried encoding to xvid as well, same results. My gut says it's something to do with using stills, since everything works fine with video as input.

What am I doing wrong?

---

### Post by daev64 on 2009-04-26
Well, I've managed a work-around. Blender to the rescue! Blender had no problems stringing the whole 12K frames into a 100% avi-jpeg, which I then fed through ffmpeg to get the desired compression. posted here: [http://www.youtube.com/watch?v=UFAuoA4JPo0](http://www.youtube.com/watch?v=UFAuoA4JPo0)

I'd sure like to be able to do it in one step, Blender has a lot more overhead going on which slows things down a lot.

---

### Post by FakeOutdoorsman on 2009-04-26
I'm not sure why FFmpeg fails at 130 seconds.  You may want to submit a bug report: [Reporting a Bug To The FFmpeg Project](http://ffmpeg.org/bugreports.html)

---

