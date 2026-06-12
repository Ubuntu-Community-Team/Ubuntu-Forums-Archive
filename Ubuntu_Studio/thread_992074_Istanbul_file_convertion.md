---
title: "Istanbul file convertion"
date: 2008-11-24
forum: Ubuntu Studio
---

### Post by kdiggity317 on 2008-11-24
I just started to use Istanbul to record my desktop to show friends how to do some simple setup stuff. The only problem is he watchs the vids from his laptop which is Windows while he is doing the stuff on his desktop which is Linux. Im wondering if there is a way to get those files from the .ogg format to .avi

---

### Post by rylleman on 2008-11-24
FFmpeg will do the job.
Open up the terminal in the folder where you have the ogg and type;
ffmpeg -i input_file.ogg output_file.avi
That will do a straight conversion.

---

### Post by kdiggity317 on 2008-11-24
Okay I installed the ffmpeg program and typed in the command:
ffmpeg -i vid test.avi <-- I had to leave the .ogg off cuz it didnt work with that on there.

This is the what it gave me in the terminal:

FFmpeg version r11872+debian_3:0.svn20080206-12ubuntu3, Copyright (c) 2000-2008 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-pp --enable-swscaler --enable-x11grab --prefix=/usr --enable-libgsm --enable-libtheora --enable-libvorbis --enable-pthreads --disable-strip --enable-libfaad --enable-libfaadbin --enable-liba52 --enable-liba52bin --enable-libdc1394 --disable-armv5te --disable-armv6 --disable-altivec --disable-vis --enable-shared --disable-static
  libavutil version: 49.6.0
  libavcodec version: 51.50.0
  libavformat version: 52.7.0
  libavdevice version: 52.0.0
  built on Oct  3 2008 22:40:31, gcc: 4.3.2
[theora @ 0xb7d6b2f0]Theora bitstream version 30201
[theora @ 0xb7d6b2f0]344 bits left in packet 81
[theora @ 0xb7d6b2f0]7 bits left in packet 82
Input #0, ogg, from 'vid2':
  Duration: 00:02:11.9, start: 0.400000, bitrate: 538 kb/s
    Stream #0.0: Video: theora, yuv420p, 1280x1024 [PAR 1:1 DAR 5:4], 10.00 tb(r)
Output #0, avi, to 'test.avi':
    Stream #0.0: Video: 0x0000, yuv420p, 1280x1024 [PAR 1:1 DAR 5:4], q=2-31, 200 kb/s, 10.00 tb(c)
Stream mapping:
  Stream #0.0 -> #0.0
Unsupported codec for output stream #0.0
kasey@Linux:~/Videos$ 

it did give me a .avi file but it didnt have any info in it. Anything I did wrong? If so plz let me know what thanks for the suggestion. :guitar:

---

### Post by rylleman on 2008-11-24
You left the input file out, that's what went wrong. Or rather output file since -i means input file. So,
ffmpeg -i input_file.ogg output_file.avi should convert from ogg to avi.
What happens if you run it with the ogg there?

---

### Post by kdiggity317 on 2008-11-24
FFmpeg version r11872+debian_3:0.svn20080206-12ubuntu3, Copyright (c) 2000-2008 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-pp --enable-swscaler --enable-x11grab --prefix=/usr --enable-libgsm --enable-libtheora --enable-libvorbis --enable-pthreads --disable-strip --enable-libfaad --enable-libfaadbin --enable-liba52 --enable-liba52bin --enable-libdc1394 --disable-armv5te --disable-armv6 --disable-altivec --disable-vis --enable-shared --disable-static
  libavutil version: 49.6.0
  libavcodec version: 51.50.0
  libavformat version: 52.7.0
  libavdevice version: 52.0.0
  built on Oct  3 2008 22:40:31, gcc: 4.3.2
vid.ogg: no such file or directory

This is what I get when i run it as:
ffmpeg -i vid.ogg test.avi

I know the file is there how would i find out for sure what kind of file it is?

---

### Post by rylleman on 2008-11-24
Are you in the right folder?
Type ls, do you see the file then?

---

### Post by kdiggity317 on 2008-11-24
yup sure am and when I type in ls i get the file name there too. How do I check the file type? I just want to make sure i have the extention correct.

---

### Post by nowardev on 2008-11-24
mencoder  -forceidx  -ofps 25  -oac mp3lame   -lameopts abr:br=128  -srate 48000  -vf scale=720:576,harddup -ovc xvid -xvidencopts bitrate=900 INPUT -o OUTPUT

---

### Post by kdiggity317 on 2008-11-25
Okay I just saw there was an add on this post is that something you want me to type in the terminal and if so do I need to be in the folder where the video is located? I would assume so but just want to make sure.

---

