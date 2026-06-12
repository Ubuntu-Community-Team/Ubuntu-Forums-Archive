---
title: "merge images to animation or video"
date: 2009-04-28
forum: Ubuntu Studio
---

### Post by diamantis13 on 2009-04-28
Hi,
I have a large number of plots and I would like to merge them in order to show the change through time. Ideally I would like to be able to pause or search through the output animation, so I would like to avoid an animated giff file. The input images can be postscript, pngs or jpgs.
Does anybody know What software should I use for such a task and what is an appropriate video format?
Thank you very much

---

### Post by lukeiamyourfather on 2009-04-29
I use FFMPEG to make videos out of PNG sequences. Its pretty quick too. Supports many input and output formats. The -r is for the frame rate of the output, -b is the bitrate, -i is the input file(s). Note the padding syntax at the end of the input.

```
ffmpeg -r 24 -b 16777216 -i /home/luke/scenes/nodeParameters/preview/preview%05d.png /home/luke/Desktop/test.mp4
```

If there's a better option I'd be curious for that too. Cheers!

---

### Post by diamantis13 on 2009-04-30
Thank you very much!
it seems to work fine. Is there another way of determining the input files order (e.g. for images 001.png 002.png 005.png 011.png 101.png).

---

### Post by lukeiamyourfather on 2009-04-30
> **diamantis13 said:**
> Thank you very much!
it seems to work fine. Is there another way of determining the input files order (e.g. for images 001.png 002.png 005.png 011.png 101.png).

I'd probably remove the unnecessary frames and then rename the sequence to conform. If there is another way to specify the input frames then its probably in the FFMPEG documentation (man ffmpeg). Cheers!

---

### Post by PeterVR on 2010-06-16
```
peter@viking:~/pics$ ffmpeg -r 24 -b 16777216 -i * test.mp4
FFmpeg version SVN-r0.5.1-4:0.5.1-1ubuntu1, Copyright (c) 2000-2009 Fabrice Bellard, et al.
  configuration: --extra-version=4:0.5.1-1ubuntu1 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --disable-stripping --disable-vhook --enable-runtime-cpudetect --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --enable-libdc1394 --enable-shared --disable-static
  libavutil     49.15. 0 / 49.15. 0
  libavcodec    52.20. 1 / 52.20. 1
  libavformat   52.31. 0 / 52.31. 0
  libavdevice   52. 1. 0 / 52. 1. 0
  libavfilter    0. 4. 0 /  0. 4. 0
  libswscale     0. 7. 1 /  0. 7. 1
  libpostproc   51. 2. 0 / 51. 2. 0
  built on Mar  4 2010 12:41:55, gcc: 4.4.3
Input #0, image2, from '0000.png':
  Duration: 00:00:00.04, start: 0.000000, bitrate: N/A
    Stream #0.0: Video: png, rgb24, 1680x1050, 24 tbr, 24 tbn, 24 tbc
Segmentation fault
peter@viking:~/pics$ 
```

Huh?

---

### Post by FakeOutdoorsman on 2010-06-16
> **PeterVR said:**
> ```
peter@viking:~/pics$ ffmpeg -r 24 -b 16777216 -i * test.mp4
FFmpeg version SVN-r0.5.1-4:0.5.1-1ubuntu1, Copyright (c) 2000-2009 Fabrice Bellard, et al.
  configuration: --extra-version=4:0.5.1-1ubuntu1 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --disable-stripping --disable-vhook --enable-runtime-cpudetect --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --enable-libdc1394 --enable-shared --disable-static
  libavutil     49.15. 0 / 49.15. 0
  libavcodec    52.20. 1 / 52.20. 1
  libavformat   52.31. 0 / 52.31. 0
  libavdevice   52. 1. 0 / 52. 1. 0
  libavfilter    0. 4. 0 /  0. 4. 0
  libswscale     0. 7. 1 /  0. 7. 1
  libpostproc   51. 2. 0 / 51. 2. 0
  built on Mar  4 2010 12:41:55, gcc: 4.4.3
Input #0, image2, from '0000.png':
  Duration: 00:00:00.04, start: 0.000000, bitrate: N/A
    Stream #0.0: Video: png, rgb24, 1680x1050, 24 tbr, 24 tbn, 24 tbc
Segmentation fault
peter@viking:~/pics$ 
```

Huh?

FFmpeg does not take a * as input.  You need to give it something like:
```
ffmpeg -r 24 -i %04d.png -vcodec libx264 -vpre hq -crf 24 -threads 0 output.mp4
```
See the FFmpeg FAQ: 3.2 [How do I encode single pictures into movies?](http://www.ffmpeg.org/faq.html#SEC14)

---

### Post by PeterVR on 2010-06-17
> **FakeOutdoorsman said:**
> FFmpeg does not take a * as input.  You need to give it something like:
```
ffmpeg -r 24 -i %04d.png -vcodec libx264 -vpre hq -crf 24 -threads 0 output.mp4
```
See the FFmpeg FAQ: 3.2 [How do I encode single pictures into movies?](http://www.ffmpeg.org/faq.html#SEC14)

Thanks for your response FakeO.

Let me go RTFM.

---

### Post by tom17 on 2011-06-16
So for some reason this does not work for me. What am I doing wrong??

$ ls
IMG_2526.JPG  IMG_2529.JPG  IMG_2532.JPG  IMG_2535.JPG  IMG_2538.JPG  IMG_2541.JPG  IMG_2544.JPG  IMG_2547.JPG

$ ffmpeg -r 10 -b 1800 -i IMG_%04d.JPG -s 800x600 test.mp4
FFmpeg version 0.6-4:0.6-2ubuntu6.1, Copyright (c) 2000-2010 the FFmpeg developers
  built on Mar 31 2011 18:43:47 with gcc 4.4.5
  configuration: --extra-version=4:0.6-2ubuntu6.1 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-vaapi --enable-pthreads --enable-zlib --enable-libvpx --disable-stripping --enable-runtime-cpudetect --enable-gpl --enable-postproc --enable-x11grab --enable-libdc1394 --enable-shared --disable-static
  libavutil     50.15. 1 / 50.15. 1
  libavcodec    52.72. 2 / 52.72. 2
  libavformat   52.64. 2 / 52.64. 2
  libavdevice   52. 2. 0 / 52. 2. 0
  libavfilter    1.19. 0 /  1.19. 0
  libswscale     0.11. 0 /  0.11. 0
  libpostproc   51. 2. 0 / 51. 2. 0
IMG_%04d.JPG: No such file or directory


Why isn't it doing the padding correctly?

Thanks,

Tom...

Edit: Ohhhhhhhh you have to start from 1! :)

---

### Post by FakeOutdoorsman on 2011-06-16
How many input images do you have? Although your images appear to be in sequential order, and if I remember correctly, FFmpeg requires the inputs to start with 1 as in *IMG_0001.JPG*.

---

### Post by Flaggmann on 2011-06-18
Use a video editor NLE application and create a project file. Add your images to the project then just drag and drop them in whatever order you want and render out a video file in whatever format you want. Viewing it in a video player will allow you to adjust the slider manually to view specific spots paused.

If you need to change the order, just open the project and drag and drop the image files to where you want them and re-output a new video file.

---

