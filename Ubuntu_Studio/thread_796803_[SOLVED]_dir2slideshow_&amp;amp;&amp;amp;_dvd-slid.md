---
title: "[SOLVED] dir2slideshow &amp;amp;&amp;amp; dvd-slideshow error????"
date: 2008-05-16
forum: Ubuntu Studio
---

### Post by shane2peru on 2008-05-16
Ok, I'm trying to make a slideshow from pictures, and want the nice fading effects.  I have this line ```
image2raw -n -a -r 95 *.JPG > file.dv 
```  That gives me a large raw dv file that can be edited and used by Kino.  It is quick and gets the job done, but no fading effects between the pictures.  Sooo, I kept looking and found the dir2slideshow and the dvd-slideshow which has crossfading option!  I ran the dir2slideshow no problem got the text file, then tried the dvd-slideshow and keep running into an error!!!  Here is the error:

```

[dvd-slideshow] mpeg2enc process=8665
[dvd-slideshow] output from ps=  PID TTY      STAT   TIME COMMAND
 8665 pts/1    S+     1:46 mpeg2enc -v 0 -a 2 -q 4 -4 2 -2 1 -s -M 0 -f 8 -o /home/shan/temp/Starred Photos/dvd-slideshow_temp_4287/video_0.mpg
COMMAND        PID   USER   FD   TYPE DEVICE     SIZE     NODE NAME
dvd-slideshow 4287 shan    3w  FIFO    8,2          14107295 /home/shan/temp/Starred Photos/dvd-slideshow_temp_4287/dvdss-pipe-4287
mpeg2enc      8665 shan    3w   REG    8,2 63078400 14107300 /home/shan/temp/Starred Photos/dvd-slideshow_temp_4287/video_0.mpg
[dvd-slideshow] waiting for mpeg2enc to finish...
[dvd-slideshow]#####################################
[dvd-slideshow] Processing command-line audio...
[dvd-slideshow] Working on track 1 audio file 0
[dvd-slideshow] 2003/06Nocturne.ogg
[dvd-slideshow] fade_in_time=0:0:3.000 fade_out_time=0:0:3.000
[dvd-slideshow] total_audio_length=0:0:0.000
[dvd-slideshow] ###############
[dvd-slideshow] Buffering end of audio file with silence for 0:12:32.751
[dvd-slideshow] Creating ac3 audio for 2003/06Nocturne.ogg...
FFmpeg version SVN-rUNKNOWN, Copyright (c) 2000-2007 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-pp --enable-swscaler --enable-pthreads --enable-libvorbis --enable-libtheora --enable-libogg --enable-libgsm --enable-dc1394 --disable-debug --enable-shared --prefix=/usr
  libavutil version: 1d.49.3.0
  libavcodec version: 1d.51.38.0
  libavformat version: 1d.51.10.0
  built on Mar 12 2008 15:36:03, gcc: 4.2.3 (Ubuntu 4.2.3-2ubuntu4)
/home/shan/temp/Starred Photos/dvd-slideshow_temp_4287/audio1.wav: I/O error occured
Usually that means that input file is truncated and/or corrupted.
[dvd-slideshow] ERROR during ffmpeg execution!
[dvd-slideshow] see /home/shan/temp/Starred Photos/dvd-slideshow.log for details
[dvd-slideshow] cleanup...

```

Ok, here is the logfile: 
> 
 cat dvd-slideshow.log 
[dvd-slideshow] Fri May 16 16:45:03 PET 2008
[dvd-slideshow] Command line was:
[dvd-slideshow] /usr/bin/dvd-slideshow -L -a 2003/06Nocturne.ogg -n 2004Pictures -f Pictures_2004.txt
[dvd-slideshow] dvd-slideshow version 0.7.5
[dvd-slideshow] Linux serbuntu 2.6.24-16-generic #1 SMP Thu Apr 10 12:47:45 UTC 2008 x86_64 GNU/Linux
[dvd-slideshow] Output directory=/home/shan/temp/Starred Photos
[dvd-slideshow] Using /bin/bash version GNU bash, version 3.2.33(1)-release (x86_64-pc-linux-gnu)
[dvd-slideshow] Found mjpegtools version 1.8.0
[dvd-slideshow] Using mjpegtools subsampling -S 420mpeg2
[dvd-slideshow] Found sox version v14.0.0
[dvd-slideshow] Found ImageMagick version 6.3.7
[dvd-slideshow] Found dvdauthor version 0.6.14.
FFmpeg version SVN-rUNKNOWN, Copyright (c) 2000-2007 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-pp --enable-swscaler --enable-pthreads --enable-libvorbis --enable-libtheora --enable-libogg --enable-libgsm --enable-dc1394 --disable-debug --enable-shared --prefix=/usr
  libavutil version: 1d.49.3.0
  libavcodec version: 1d.51.38.0
  libavformat version: 1d.51.10.0
  built on Mar 12 2008 15:36:03, gcc: 4.2.3 (Ubuntu 4.2.3-2ubuntu4)
ffmpeg      SVN-rUNKNOWN
libavutil   3212032
libavcodec  3352064
libavformat 3344896
[dvd-slideshow] Font=-font /usr/share/fonts/type1/gsfonts/n019004l.pfb
[dvd-slideshow] ####################################
[dvd-slideshow] Parsing input .txt file Pictures_2004.txt
[dvd-slideshow]############################################################
[dvd-slideshow] Found 186 images.
[dvd-slideshow] Found 1 audio files.
[dvd-slideshow] Found 2 background slides.
[dvd-slideshow] Found 1 title slides.
[dvd-slideshow] Found 188 transitions (fadein/fadeout/crossfade).
[dvd-slideshow] Video: NTSC  Audio: AC3
[dvd-slideshow] Debug=0  Autocrop=0 Subtitles=render
[dvd-slideshow] WARNING: Using low-quality mode.
[dvd-slideshow]   This mode is for testing only.
[dvd-slideshow]   output resolution is x
[dvd-slideshow]   Ignore [mpeg2enc] warnings (usually)
[dvd-slideshow] Decoding command-line passed audio files...
[dvd-slideshow] Decoding ogg audio: 2003/06Nocturne.ogg
[dvd-slideshow] Total video length = 0:12:31.000
[dvd-slideshow] Temp dir is /home/shan/temp/Starred Photos/dvd-slideshow_temp_4287
COMMAND        PID   USER   FD   TYPE DEVICE SIZE     NODE NAME
dvd-slideshow 4287 shan    3w  FIFO    8,2      14107295 /home/shan/temp/Starred Photos/dvd-slideshow_temp_4287/dvdss-pipe-4287
[dvd-slideshow] Creating black background
[dvd-slideshow]############################################################
[dvd-slideshow] Creating black background
[dvd-slideshow]############################################################
[dvd-slideshow] Title 0:0:3.000
[dvd-slideshow]         Title=Pictures_2004
++ WARN: [mpeg2enc] Frame height won't split into two equal field pictures...
++ WARN: [mpeg2enc] forcing encoding as progressive video
[dvd-slideshow]############################################################
[dvd-slideshow] Fadeout 0:0:1.000
[dvd-slideshow]############################################################
[dvd-slideshow] background 0:0:1.000
[dvd-slideshow] Displaying background image black
[dvd-slideshow]############################################################
[dvd-slideshow] Fadein 0:0:1.000
[dvd-slideshow]############################################################
[dvd-slideshow] 1/186 2004/2004011221_58_32.JPG 0:0:3.000
[dvd-slideshow]############################################################
[dvd-slideshow] Crossfade 0:0:1.000
[dvd-slideshow]############################################################
...
... **I cut this part to spare you the 186 picture conversion :)**
...
[dvd-slideshow] Crossfade 0:0:1.000
[dvd-slideshow]############################################################
[dvd-slideshow] 185/186 2004/2004122517_14_47.JPG 0:0:3.000
[dvd-slideshow]############################################################
[dvd-slideshow] Crossfade 0:0:1.000
[dvd-slideshow]############################################################
[dvd-slideshow] 186/186 2004/2004122517_14_59.JPG 0:0:3.000
[dvd-slideshow]############################################################
[dvd-slideshow] Fadeout 0:0:1.000
[dvd-slideshow]############################################################
[dvd-slideshow] background 0:0:1.000
[dvd-slideshow] Displaying background image black
[dvd-slideshow]############################################################
[dvd-slideshow] mpeg2enc process=8665
[dvd-slideshow] output from ps=  PID TTY      STAT   TIME COMMAND
 8665 pts/1    S+     1:46 mpeg2enc -v 0 -a 2 -q 4 -4 2 -2 1 -s -M 0 -f 8 -o /home/shan/temp/Starred Photos/dvd-slideshow_temp_4287/video_0.mpg
COMMAND        PID   USER   FD   TYPE DEVICE     SIZE     NODE NAME
dvd-slideshow 4287 shan    3w  FIFO    8,2          14107295 /home/shan/temp/Starred Photos/dvd-slideshow_temp_4287/dvdss-pipe-4287
mpeg2enc      8665 shan    3w   REG    8,2 63078400 14107300 /home/shan/temp/Starred Photos/dvd-slideshow_temp_4287/video_0.mpg
[dvd-slideshow] waiting for mpeg2enc to finish...
[dvd-slideshow]#####################################
[dvd-slideshow] Processing command-line audio...
[dvd-slideshow] Working on track 1 audio file 0
[dvd-slideshow] 2003/06Nocturne.ogg
[dvd-slideshow] fade_in_time=0:0:3.000 fade_out_time=0:0:3.000
[dvd-slideshow] total_audio_length=0:0:0.000
[dvd-slideshow] ###############
[dvd-slideshow] Buffering end of audio file with silence for 0:12:32.751
[dvd-slideshow] Creating ac3 audio for 2003/06Nocturne.ogg...
FFmpeg version SVN-rUNKNOWN, Copyright (c) 2000-2007 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-pp --enable-swscaler --enable-pthreads --enable-libvorbis --enable-libtheora --enable-libogg --enable-libgsm --enable-dc1394 --disable-debug --enable-shared --prefix=/usr
  libavutil version: 1d.49.3.0
  libavcodec version: 1d.51.38.0
  libavformat version: 1d.51.10.0
  built on Mar 12 2008 15:36:03, gcc: 4.2.3 (Ubuntu 4.2.3-2ubuntu4)
/home/shan/temp/Starred Photos/dvd-slideshow_temp_4287/audio1.wav: I/O error occured
Usually that means that input file is truncated and/or corrupted.
[dvd-slideshow] ERROR during ffmpeg execution!
[dvd-slideshow] see /home/shan/temp/Starred Photos/dvd-slideshow.log for details
[dvd-slideshow] cleanup...

I have tried this without an audio file and get the same error, I have tried a different audio file, same error.  It really appears there is a problem with ffmpeg.  If you have any ideas on this, I would greatly appreciate the info. Working on Hardy Heron of course. :D  Thanks

Shane

---

### Post by shane2peru on 2008-05-16
PS -  All the things I have dug up, tell me to install the svn version of ffmpeg (did that)  Then they tell me to update the dvd-slideshow file from sourceforge (did that)  Then they tell me to edit my /usr/bin/dvd-slideshow file and change the audio_bitrate=128  to audio_bitrate=128k   and one other line that is too long to put here, basically it is $audio_bitrate changed to ${audio_bitrate}k  I have done all this and still have gotten NO WHERE!  Please please please, if you know of a solution, I would greatly appreciate the info.  Thanks!

Shane

---

### Post by shane2peru on 2008-05-16
Ok, I didn't fix the error, I found another way of doing this.  I will post it here in case someone in the future wants to do this too. :)  
1.  Put all the pictures that you want in the slide show in a directory (makes it easier).
2.  Here is the command that I used: 
```

images2mpg -t 10 -f DVD -n NTSC -d 4 -M /usr/bin/ -o newfile.mpg -i *.JPG

```

What does all that mean???  -t is the fading of the pictures in and out, I like 10, other choice is 20 (the fastest effect)  and 1 being the slowest.  The -f is for format, DVD, SVCD etc.  -n well, you got that one, NTSC (format of video used in the USA and much of South America).  The -d is for delay in seconds, and the -M is necessary to tell it where to find the imagemagick and  another program it needs. -o is the output file :)  and -i is the input file, probably easiest to run this right in the directory where the pictures are.  :)  Well I hope that helped someone. 

Shane

PS  If you have an answer to the dvd-slideshow I would still be interested in hearing it, because I think I messed up my ffmpeg file, probably will be re-installing that to fix any attempted fixes I made.  :)  Thanks!

---

### Post by Creative2 on 2008-05-17
fixing slideshow error :

[http://fuocotools.byethost13.com/index.php?topic=90.0](http://fuocotools.byethost13.com/index.php?topic=90.0)

---

### Post by shane2peru on 2008-05-17
> **Creative2 said:**
> fixing slideshow error :

[http://fuocotools.byethost13.com/index.php?topic=90.0](http://fuocotools.byethost13.com/index.php?topic=90.0)

I wish there were three of those Gold Medal 'thankyou' buttons for this info!!!   That is great, it fixed it!  I had tried the medibuntu repos too, I think that file is what I needed!!!  THANK YOU!!!:biggrin:  You made my day!  It is on less step I have to make, it fades out the audio, and everything! Wonderfull!!!

Shane

---

### Post by Creative2 on 2008-05-17
O:) mm try mandvd it should be able to do this ...easly

---

### Post by shane2peru on 2008-05-17
> **Creative2 said:**
> O:) mm try mandvd it should be able to do this ...easly

I have Tovid, and DeVeDe installed, I tried mandvd, but I'm on 64bit, and didn't see a deb.  I'm trying to decide which is better, Tovid, or DeVeDe.  I have seen screenshots of mandvd, and would like to give it a try too, sometime.

Shane

---

