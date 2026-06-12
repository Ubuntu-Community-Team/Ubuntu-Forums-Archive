---
title: "PSP + Mencoder"
date: 2008-05-04
forum: Ubuntu Studio
---

### Post by EMCGFX on 2008-05-04
I am currently using Avidemux, see my post at [http://ubuntuforums.org/showthread.php?t=782245](http://ubuntuforums.org/showthread.php?t=782245)

I would like to use mencoder instead of avidemux.

Video Codec: x264
Audio Codec: AAC

I've tried this >
```
mencoder video_in.avi -sws 9 \
-vf scale=480:-10,harddup,unsharp=l3x3:0.7,expand=480:272 \
-oac faac -faacopts br=128:mpeg=4:object=2:raw -ovc x264 \
-x264encopts bitrate=650:global_header:partitions=all:trellis=1:vbv_maxrate=768:vbv_bufsize=2000:level_idc=30 \
-of lavf -lavfopts format=psp -o video.mp4
```

Its way longer then Avidemux, is there any way to speed up this process to convert in 15min ? Avidemux takes 30min.

---

### Post by Creative2 on 2008-05-05
you can use of course fuoco tools... that use or ffmpeg or mencoder as you want... example 

i prefer xvid for faster encoding... with dual  core you can improve speed with x264 too...

[B]xvid 
aac[/B]

if you have only 1 cpu

mencoder INPUT -oac lavc -ovc lavc -of lavf -lavcopts aglobal=1:vglobal=1:vcodec=mpeg4:vbitrate=900:acodec=libfaac -af lavcresample=24000 -vf scale=368:208,harddup -lavfopts format=psp -ofps 30000/1001 -o OUTPUT

if you have dual core cpu

mencoder INPUT -oac lavc -ovc lavc -of lavf -lavcopts aglobal=1:vglobal=1:vcodec=mpeg4:vbitrate=900:threads=2:acodec=libfaac -af lavcresample=24000 -vf scale=368:208,harddup -lavfopts format=psp -ofps 30000/1001 -o OUTPUT

---

### Post by EMCGFX on 2008-05-05
What if I have four ;-) Is there workaround for that ? I have Core2Quad.

Edited: I found this option "threads=auto", this supposed to detect my cpu's.

This should work, for four processors aka Core2Quad ;)

mencoder INPUT -oac lavc -ovc lavc -of lavf -lavcopts aglobal=1:vglobal=1:vcodec=mpeg4:vbitrate=900:threads=auto:acodec=libfaac -af lavcresample=24000 -vf scale=368:208,harddup -lavfopts format=psp -ofps 30000/1001 -o OUTPUT

---

### Post by Creative2 on 2008-05-05
mm i have dual core and with "=auto" i have had some problem ,with =2 i haven't.
anyway it's nice if it works for your computer

---

### Post by EMCGFX on 2008-05-05
Yeah, you are rign. It give an error: "Error parsing option on the command line: =lavcopts" But when I use threads=4, it uses all four processors ;-)

This is my modified command that I use, converts how I like it with original psp screen size of 480x272 with 1000 vbitrate. 400mb file in under 5min, oh yeah ;-) It beats that Avidemux by 25min.

```
mencoder -ovc lavc -oac lavc -of lavf \
-lavcopts aglobal=1:vglobal=1:vcodec=mpeg4:\
vbitrate=1000:threads=4:acodec=libfaac -af \
lavcresample=24000 -vf scale=480:272,harddup \
-lavfopts format=psp -ofps 30000/1001 \
<file_in.avi> -o <file_out.mp4>
```

Now breaking this commands into parts:
-ovc = video codec
-ova = audio codec
-of lavf ????
-lavcopts = lavc codec options
aglobal=1 same as vglobal for audio headers. (default)
vglobal=1 to control writing global video headers. (default)
vcodec=mpeg4
vbitrate=1000, in my experience it can be anywhere between 500~1000
threads=4, to use all four processors for Core2Quad.
threads=2, to use two processors for Core2Duo.
acodec=libfaac for AAC audio.
-af to setup a chain of audio filters. (lavcresample=24000)
-vf scale=480:272,harddup set the original psp screen size, that can be changed to smaller and "harddup" to force duplicate frames to be encoded in the output.
-lavfopts format=psp
-ofps 30000/1001, framerate.

What I need to know is ??? and if its possible to use "-ofps 24000/1001" for psp encoding? Also is it possible to convert the whole folder of *.avi to *.mp4 ?

---

### Post by EMCGFX on 2008-05-05
OK, half an hour and I came up with my own avi2mp4 bash script, big thanks to "Steel_J"'s script at [http://www.linuxquestions.org/linux/answers/Applications_GUI_Multimedia/Batch_convert_MPEG_files_to_AVI_0](http://www.linuxquestions.org/linux/answers/Applications_GUI_Multimedia/Batch_convert_MPEG_files_to_AVI_0)

By looking on his script, it helped me create avi2mp4. Of course it can be inproved in time, I will post updated version here ;) But here is a durty hack of his script.

```

#!/bin/bash

# avi2mp4 v0.1 script by EMCGFX <emcgfx[@]gmail.com>
# avi2mp4 (Convert avi files into mp4 for psp, using MPEG4 video and AAC audo codecs)

# Original mpeg2avi v0.2b script by By Steel_J <www.linuxquestions.org>
# mpg2avi (Convert mpeg streams into high quality mpeg4 avi with mp3 audio)

#requirements: mplayer/mencoder

#Begin
clear

current_directory=$( pwd )

# video bitrate (1100 = around 500 MB movie size)

# remove spaces
for i in *.[Aa][Vv][Ii]; do mv "$i" `echo $i | tr ' ' '_'`; done > /dev/null 2>&1 &

# remove uppercase
for i in *.[Aa][Vv][Ii]; do mv "$i" `echo $i | tr '[A-Z]' '[a-z]'`; done > /dev/null 2>&1 &

# convert avi movies into mp4's with mencoder
for i in *.[Aa][Vv][Ii];
do nice -n 10 mencoder -ovc lavc -oac lavc -of lavf \
-lavcopts aglobal=1:vglobal=1:vcodec=mpeg4:vbitrate=800:\
threads=4:acodec=libfaac -af lavcresample=24000 \
-vf scale=480:272,harddup -lavfopts format=psp \
-ofps 30000/1001 $i -o "'basename "$i"'.mp4";
echo "finished feah";
done
exit;
```

I have this save some time for some one who is tryingn to convert whole directory of avi files to mp4 files to play on psp ;-) Have fun, if you improve it please post it here.

---

### Post by EMCGFX on 2008-05-05
Here is improved version of avi2mp4 and another script to convert avi files to archos 404.

avi2mp4 (for psp)
```
#!/bin/bash

# avi2mp4 v0.2 by EMCGFX <emcgfx[@]gmail.com>
# Convert avi files to mp4 for psp.
# Using MPEG4 video and AAC audio codecs.

# Original Script mpg2avi By Steel_J
# Convert mpeg streams into high quality mpeg4 avi with mp3 audio.

# requirements: mplayer/mencoder

# Usage:
# 0. chmod +x avi2mp4.sh
# 1. copy this script to any folder with avi files.
# 2. execute the script, ./avi2mp4.sh *

# v0.2
# changed: replaced _ with . character in filenames.
# changed: -o "'basename "$i"'.mp4" to -o ""$i".mp4";
# removed: current_directory=$( pwd )

# v0.1 -- first release.

# Begin
clear

# remove spaces
for i in *.[Aa][Vv][Ii];
  do mv "$i" `echo $i | tr ' ' '.'`;
done > /dev/null 2>&1 &

# remove uppercase
for i in *.[Aa][Vv][Ii];
  do mv "$i" `echo $i | tr '[A-Z]' '[a-z]'`;
done > /dev/null 2>&1 &

# convert avi movies into mp4's with mencoder
for i in *.[Aa][Vv][Ii];
do nice -n 10 mencoder -ovc lavc -oac lavc -of lavf \
-lavcopts aglobal=1:vglobal=1:vcodec=mpeg4:vbitrate=800:\
threads=4:acodec=libfaac -af lavcresample=24000 \
-vf scale=480:272,harddup -lavfopts format=psp \
-ofps 30000/1001 $i -o ""$i".mp4";
echo "Finished";
done
exit;

```

avi to archos 404
```
#!/bin/bash

# avi2archos v0.1 by EMCGFX <emcgfx[@]gmail.com>
# Convert avi files to archos 404.
# Using XviD video and MP3 audio codecs.

# Original Script mpg2avi By Steel_J
# Convert mpeg streams into high quality mpeg4 avi with mp3 audio.

#requirements: mplayer/mencoder

# Usage:
# 0. chmod +x avi2archos.sh
# 1. copy this script to any folder with avi files.
# 2. execute the script, ./avi2archos.sh *

#Begin
clear

# remove spaces
for i in *.[Aa][Vv][Ii];
  do mv "$i" `echo $i | tr ' ' '.'`;
done > /dev/null 2>&1 &

# remove uppercase
for i in *.[Aa][Vv][Ii];
  do mv "$i" `echo $i | tr '[A-Z]' '[a-z]'`;
done > /dev/null 2>&1 &

# convert avi movies into archos avi's with mencoder
for i in *.[Aa][Vv][Ii];
do nice -n 10 mencoder -ovc xvid -oac mp3lame \
-xvidencopts bitrate=500 $i -o ""$i".avi";
echo "Finished";
done
exit;

```

---

### Post by loongye on 2009-03-11
Does this work with core i7? like what if i changed threads to 16..

---

### Post by inobe on 2009-03-11
looks good fella's

---

### Post by binbash on 2009-03-12
thanks for the scrip it looks good

---

### Post by rfrayer on 2009-10-14
here is what i use 

```
mencoder mouth-hole.avi -oac lavc -ovc lavc -of lavf -lavcopts aglobal=1:vglobal=1:vcodec=mpeg4:vbitrate=384:acodec=libfaac -af lavcresample=24000 -vf scale=368:208,harddup -lavfopts format=psp -ofps 15 -o butt-hole.mp4
```replace mouth-hole with the input file and butt-hole with the output file makes a nice 15 fps psp movies around 200-350 mb depending on length

---

### Post by mapache326 on 2012-04-03
hi I've been trying to convert video files for my psp but so far i havent succeeded this is what i have as mencoder settings 

mencoder -ofps 30000/1001 -af lavcresample=24000 -vf harddup -oac lavc \     -ovc lavc -lavcopts aglobal=1:vglobal=1:vcodec=mpeg4:acodec=libfaac \     -of lavf -lavfopts format=psp \     *input.video* -o *output.psp*

but when i use these settings i get an error with the Audio **LAVC, couldn't find encoder for codec libfaac.**
I tried changing to -oac faac instead of -oac lavc but then i get an error saying that **MPlayer was compiled without libfaac. See README or DOCS.**

thanks for the help!

---

