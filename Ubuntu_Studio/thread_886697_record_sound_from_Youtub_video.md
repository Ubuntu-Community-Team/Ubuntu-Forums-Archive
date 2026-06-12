---
title: "record sound from Youtub video"
date: 2008-08-11
forum: Ubuntu Studio
---

### Post by Chris11 on 2008-08-11
I tried with XVidCap but it records only video, no sound...I tried with Audacity, but I think there is no feature to record sound from a stream..

Any ideas how to do that?


Chris

---

### Post by eggdeng on 2008-08-11
A sweet little app called Utube-ripper lets you rip the audio to mp3. 

Download & How-to at
[http://maketecheasier.com/ubuntu-how-to-extract-audio-from-youtube-video/2008/06/30](http://maketecheasier.com/ubuntu-how-to-extract-audio-from-youtube-video/2008/06/30)

---

### Post by Chris11 on 2008-08-11
Thanks that's great - exactly what I was looking for...

Chris

---

### Post by MaindotC on 2008-08-22
I was using [_Catch And Convert_](http://sourceforge.net/projects/cac/) but recently its stopped working - maybe Youtube wised up or something.  Converttube.com is always slow and I've had difficulty getting it to completely finish a job :(

---

### Post by Creative2 on 2008-08-22
there is a simple way to do this :

or use fuoco tools for multiple youtube video

or by command line

youtube-dl INPUTLINK -o 'TEMP.FLV' ; ffmpeg -i  'TEMP.FLV' -vn -ac 2 -acodec copy  -y   'OUTPUTNAME.mp3' 

That can give you the same quality of youtube if you convert you will lost quality

---

### Post by MaindotC on 2008-08-22
Sweet, I followed Creative's command and it worked!  2.7mb file for a song - I think that's pretty decent :)  Thanks bro!

---

### Post by bigdee973 on 2008-08-22
another simplier way to do it (for all those challenged) is to use SOUND RECORDER in Applications>sound & video...and in "record from input" use "MIX" hit record and whatever comes out of your speakers will be recorded i use this method all the time

---

### Post by maschicago on 2008-08-30
I use the download helper add-on for firefox to get an FLV file, then use ffmpeg to rip the audio.

---

