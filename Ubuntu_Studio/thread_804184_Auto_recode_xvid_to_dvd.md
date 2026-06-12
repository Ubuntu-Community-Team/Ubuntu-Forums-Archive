---
title: "Auto recode xvid to dvd"
date: 2008-05-22
forum: Ubuntu Studio
---

### Post by mhouston100 on 2008-05-22
Hey guys, once again I turn to the forum for help...

Basically I have many many xvid / divx /avi etc files that I need to convert to DVD, all of different sizes/bitrates etc

Now the problem I have is that the only program that seems to recode all of them to the max bitrate for burning to a standard DVD is Nerovision (unfortunately).  I have tried all sorts of programs in Linux and windows (DeVeDe, fucco's, ffmpg, menucoder and a few more... as well as x2dvd tmpgenc etc in windows) but the auto settings in all of these seems screwy.

Heres an example:

700MB xvid movie.

Recode using NeroVision 4.68GB (fits perfectly on a DVD, quality perfect)

Recode using DeVeDe 2.8GB (yeah fits on a DVD but noticable lower quality)

Recode Using ffmpg 2.8 - 2.9GB (Noticably lower quality)

etc etc etc

This continues with every program I try that has an auto setting.
Now my problem is that Nerovision is crap for recoding multiple files and dvd's (as well as the fact that its windows and is the only thing stopping me from switching for good), and I have hundreds that I need to recode.  Any of the other programs on Linux would be great, scriptable or has its own built in queue but the quality for the auto conversion is crap!  Now obviously I dont have the resources to manually figure out the bitrate etc for every file that needs to be converted and then recode them one at a time.

So my question is, does anyone have any program / script / information that would allow me to recode multiple videos to DVD while keeping the bitrate at the highest level possible to completely (as close as possible) fill a standard DVD?

---

### Post by Creative2 on 2008-05-23
man of mencoder


14.8.5. Putting it all Together
 This section shows some complete commands for creating VCD/SVCD/DVD compliant videos. 
14.8.5.1. PAL DVD
mencoder -oac lavc -ovc lavc -of mpeg -mpegopts format=dvd:tsaf \
  -vf scale=720:576,harddup -srate 48000 -af lavcresample=48000 \
  -lavcopts vcodec=mpeg2video:vrc_buf_size=1835:vrc_maxrate=9800:vbitrate=5000:\
keyint=15:vstrict=0:acodec=ac3:abitrate=192:aspect=16/9 -ofps 25 \
  -o movie.mpg movie.avi

14.8.5.2. NTSC DVD
mencoder -oac lavc -ovc lavc -of mpeg -mpegopts format=dvd:tsaf \
  -vf scale=720:480,harddup -srate 48000 -af lavcresample=48000 \
  -lavcopts vcodec=mpeg2video:vrc_buf_size=1835:vrc_maxrate=9800:vbitrate=5000:\
keyint=18:vstrict=0:acodec=ac3:abitrate=192:aspect=16/9 -ofps 30000/1001 \
  -o movie.mpg movie.avi

14.8.5.3. PAL AVI Containing AC-3 Audio to DVD
 If the source already has AC-3 audio, use -oac copy instead of re-encoding it. 
mencoder -oac copy -ovc lavc -of mpeg -mpegopts format=dvd:tsaf \
  -vf scale=720:576,harddup -ofps 25 \
  -lavcopts vcodec=mpeg2video:vrc_buf_size=1835:vrc_maxrate=9800:vbitrate=5000:\
keyint=15:vstrict=0:aspect=16/9 -o movie.mpg movie.avi

14.8.5.4. NTSC AVI Containing AC-3 Audio to DVD
 If the source already has AC-3 audio, and is NTSC @ 24000/1001 fps: 
mencoder -oac copy -ovc lavc -of mpeg -mpegopts format=dvd:tsaf:telecine \
  -vf scale=720:480,harddup -lavcopts vcodec=mpeg2video:vrc_buf_size=1835:\
  vrc_maxrate=9800:vbitrate=5000:keyint=15:vstrict=0:aspect=16/9 -ofps 24000/1001 \
  -o movie.mpg movie.avi



you can use fuoco tools with that command line by replacing only the inputfile and output file with 

INPUT OUTPUT 

and remember mpg is the same of vob so you could replace mpg with vob...

---

### Post by aeiah on 2008-05-23
i use a script that involves ffmpeg and i agree, the filesize is usually not the full 4.4gb but somewhere around 3.5gb. when you view the video, is there a noticable difference? does nero attempt to flesh out mp3 stereo into 5.1 for the dvd, or likewise does ffmpeg auto settings strip down ac3 5.1 to stereo on the dvd if left at default?

i dont have nerovision or the time to test these things, but this weekend im going to look into how to get ffmpeg to spit out a higher quality if its possible now i have time.

---

### Post by ZachMan on 2010-09-18
try manDVD.  I'm using it right now to convert and Xvid movie to DVD with deinterlacing for use with high def tv.  pretty simple on ubuntu even for newbies.

---

