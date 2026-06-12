---
title: "x264/mencoder/ffmpeg on a dual quad core"
date: 2008-05-05
forum: Ubuntu Studio
---

### Post by toodiesel on 2008-05-05
Hey all:

Does anyone have any benchmarks for running 720p encodings (from similar source material) using ffmpeg/mencoder/x264 on a dual quad core xeon 5400 system (with Ubuntu 8.04 server 64 edition)?

I am using threads=auto on x264 and mencoder and can only get around 30fps for each.

Here is what I've used to configure x264:
./configure --enable-pthread --enabled-shared

I use the following command to get ouput video:

X264:
x264 --bitrate 500 --threads auto --thread-input --progress -o test.avi input.avi 1280x720

MENCODER:
mencoder -ovc x264 -x264encopts threads=auto:bitrate=250:subq=7:partitions=all:8x8dct:me=umh:frameref=4:bframes=3:b_pyramid:weight_b  -vf scale=1280:720,noise=8a:4a -nosound -ofps 22  -o test.avi -endpos 15 NBA.2007.Finals.G4.Spurs_Cavaliers.x264.HE-AAC.720p.SAMPLE.mp4


Here is my output:

x264 [info]: using cpu capabilities: MMX MMX2 SSE SSE2 SSE3 SSSE3 Cache64
x264 [info]: slice I:1 Avg QP:51.00 size:172070 PSNR Mean Y:11.76 U:22.63 V:22.63 Avg:13.35 Global:13.35
x264 [info]: slice P:9 Avg QP:51.00 size:172083 PSNR Mean Y:11.69 U:22.59 V:22.60 Avg:13.28 Global:13.28
x264 [info]: mb I I16..4: 99.7% 0.0% 0.3%
x264 [info]: mb P I16..4: 98.7% 0.0% 0.0% P16..4: 1.0% 0.3% 0.0% 0.0% 0.0% skip: 0.0%
x264 [info]: final ratefactor: 100.55
x264 [info]: SSIM Mean Y:0.3806576
x264 [info]: PSNR Mean Y:11.698 U:22.598 V:22.599 Avg:13.286 Global:13.286 kb/s:34416.36

encoded 10 frames, 11.12 fps, 48013.24 kb/s

I'm unsure if anything looks wrong, but the input file isn't ever only 10 frames ( input is usually 720p or 1080i minute-2minutes in length ).

One more question: I've been unable to find any methods of sending piped data to x264. If I leave out the input filename I always get errors.

Thanks for any help, and this is a great forum

---

### Post by kaiataris on 2008-05-06
According to [_this thread_]("http://ubuntuforums.org/showthread.php?t=782317"), you probably want to change threads to "threads=4" in order to use all 4 cores.

---

### Post by toodiesel on 2008-05-07
> **kaiataris said:**
> According to [_this thread_]("http://ubuntuforums.org/showthread.php?t=782317"), you probably want to change threads to "threads=4" in order to use all 4 cores.

hey, thanks for the response, but threads=4 would only use 4 cores, and I have 8 (a dual quad core xeon 5400 system), and have passed in threads=x, where x is any number less than 9, in addition to using 'auto' (which detects the 8 cores properly)...

I was creating this post because I am disappointed in the rendering time that this system is giving me, you'd think 8 processors could encode much quicker than ~30fps !

Also, top reports each core is being used at about 95% when running x264, and only 65% when using mencoder, so that was a little disappointing.

thanks all, any suggestions?

---

### Post by FakeOutdoorsman on 2008-05-07
I'm not completely sure here, but I think the x264/libx264 in the Ubuntu Hardy repos was compiled with support for yasm >0.5, but only yasm 0.5.0 is in the repos resulting in x264 complaining about not finding yasm and thus uberslowness.  I would try to either compile a [new yasm]("http://www.tortall.net/projects/yasm/wiki/Download") or try the [x264]("http://packages.ubuntu.com/gutsy/x264")/[libx264]("http://packages.ubuntu.com/gutsy/libx264-dev") deb package from Gutsy, which works with yasm 0.5.0.

---

### Post by FakeOutdoorsman on 2008-05-07
I did some unscientific tests using x264-git with nasm from repo, compiled yasm 0.7.0, and no assembler:

**x264**
```
./configure --enable-pthread --enable-mp4-output --enable-shared
```
```
#!/bin/bash

time ffmpeg -y -i frontwheeldrive.flv -pass 1 -threads auto -s 640x480 -vcodec libx264 -b 384k -bt 192k -f mp4 -flags +loop -cmp +chroma -partitions 0 -me_method epzs -subq 1 -trellis 0 -refs 1 -coder 0 -me_range 16 -g 300 -keyint_min 30 -sc_threshold 40 -i_qfactor 0.71 -maxrate 10M -bufsize 10M -rc_eq 'blurCplx^(1-qComp)' -qcomp 0.6 -qmin 10 -qmax 51 -qdiff 4 -level 30 -aspect 4:3 -an -vframes 1200 /dev/null

time ffmpeg -y -i frontwheeldrive.flv -pass 2 -threads auto -s 640x480 -vcodec libx264 -b 384k -bt 192k -f mp4 -flags +loop -cmp +chroma -partitions +parti4x4+partp4x4+partp8x8+partb8x8 -me_method umh -subq 7 -trellis 2 -refs 1 -coder 0 -me_range 16 -g 300 -keyint_min 30 -sc_threshold 40 -i_qfactor 0.71 -maxrate 10M -bufsize 10M -rc_eq 'blurCplx^(1-qComp)' -qcomp 0.6 -qmin 10 -qmax 51 -qdiff 4 -level 30 -aspect 4:3 -acodec libfaac -ab 96k -ac 1 -vframes 1200 temp.mp4
```
Times for 2nd passes:
**nasm**
real 1m43.936s
user 1m35.666s
sys 0m1.948s

**yasm 0.7.0**
real 1m40.3888s
user 1m35.390s
sys 0m1.740s

**no assembler** (no yasm or nasm installed)
real 4m24.042s
user 4m15.576s
sys 0m2.084s

These times are from a standard Ubuntu Hardy install inside VirtualBox.

Since nasm is in the repos already, you can just use that instead of compiling yasm 0.7.0, unless you are encoding many long videos and want the absolute fastest encode possible.

---

