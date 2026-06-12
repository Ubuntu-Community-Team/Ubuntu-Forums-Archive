---
title: "the ffmpeg transcoded video gets bad quality"
date: 2008-08-03
forum: Ubuntu Studio
---

### Post by KanineN on 2008-08-03
Hello! When I transcode a .flv video to my phone that has screen resolution 320x240 I have this as a command line 

```
ffmpeg -i kanye hands.flv -b 4500 -s 320x240 kanye hands.mp4
```

But when I play the video in my cellphone the video is bad. Nothing is round it's just as squares. You can see some pixels that are really big like 1x1 cm. But when I trancode with mediacoder (window$ app, I know :( ) The video is good but not really god but it beats the ffmpeg pretty easy. 



And now the question is, How will I make the video to a good quality so I can see it without my eyes starts to bleed?

---

### Post by Creative2 on 2008-08-03
i have written a lots of command line in fuoco tools see it on my signature

---

### Post by KanineN on 2008-08-03
Sorry, I wont install another converter program. I want to know ffmpeg.

---

### Post by FakeOutdoorsman on 2008-08-03
Are you using ffmpeg from the Ubuntu repository, [Medibuntu]("http://medibuntu.org") repository, or did you compile it yourself?  Depending on which ffmpeg release you are using, you may or may not need to use a "k" in your bitrate, such as "-b 512k".  According to your command, you may be encoding to 4500 bits/s. That would equal to about 4.4 kb/s, which is incredibly small.

Running a second encoding pass will increase the quality of your video, but will increase the encoding time.  A third thing to try is a better video codec.  I prefer h264, but you need to get ffmpeg from Medibuntu or compile it yourself since ffmpeg from the Ubuntu repo hasn't been configured for h264.

This tutorial has a sample two-pass h264 encoding script, but it is written for the compile-it-yourself version of ffmpeg and may not work on your phone if it can't handle h264:    	
[HOWTO: Compile the latest ffmpeg and x264 from source]("http://ubuntuforums.org/showthread.php?t=786095")

I can re-write the script for Medibuntu's ffmpeg if you would rather use that.

---

### Post by KanineN on 2008-08-05
I use the mediubuntu repository. So it I want 400 kb/s I need to type -b 400k or -b 450000?

---

### Post by FakeOutdoorsman on 2008-08-06
FFmpeg's bitrate is in in bits/s, so you would use "-b 400k".  I would guess "-b 409600" would work too, since 1 kilobit = 1024 bits, but I generally just use the "k".

This script should work with the Medibuntu ffmpeg, but I haven't tested it.  Make a text file and dump this in it:
```
#!/bin/bash
# Encoding Script
ffmpeg -y -i $1 -pass 1 -threads 0 -s 640x480 -vcodec h264 -b 384k -bt 192k -f mp4 -flags +loop -cmp +chroma -partitions 0 -me_method epzs -subq 1 -trellis 0 -refs 1 -coder 0 -me_range 16 -g 300 -keyint_min 30 -sc_threshold 40 -i_qfactor 0.71 -maxrate 10M -bufsize 10M -rc_eq 'blurCplx^(1-qComp)' -qcomp 0.6 -qmin 10 -qmax 51 -qdiff 4 -level 30 -an -r ntsc /dev/null

ffmpeg -y -i $1 -pass 2 -threads 0 -s 640x480 -vcodec h264 -b 384k -bt 192k -f mp4 -flags +loop -cmp +chroma -partitions +parti4x4+partp4x4+partp8x8+partb8x8 -me_method umh -subq 7 -trellis 2 -refs 1 -coder 0 -me_range 16 -g 300 -keyint_min 30 -sc_threshold 40 -i_qfactor 0.71 -maxrate 10M -bufsize 10M -rc_eq 'blurCplx^(1-qComp)' -qcomp 0.6 -qmin 10 -qmax 51 -qdiff 4 -level 30 -acodec aac -ab 96k -ac 1 -r ntsc $2
```
Then make it executable:
```
chmod +x 264encode.sh
```
Then run it:
```
./scriptname.sh input.avi output.mp4
```

---

