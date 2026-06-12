---
title: "basic mencoder example please"
date: 2008-05-31
forum: Ubuntu Studio
---

### Post by bayonetblaha on 2008-05-31
I learn by example, and I can't make any sense of the mencoder documentation. I'm really interested in learning how to use mencoder by command line, but I need an example. At the moment I'm trying to resize a .mov from my camera to 320x240 for youtube, any output format. Is there some simple command like:

mencoder input.mov --scale=320x240 output.mov

what is the proper syntax, though?

---

### Post by Creative2 on 2008-06-01
you can find a lots of example on fuoco tools :), you can find it on y signature infact you can see command line...

anyway 

mencoder  INPUT.mov -oac lavc -ovc lavc -of lavf -lavcopts vcodec=mpeg4:vbitrate=700:acodec=ac3:abitrate=192 -ofps 30 -srate 44100  -vf scale=320:240 -o OUTPUT.mov


or this  encoding in flv 

ffmpeg -i INPUT.xxx -b 600k -r 30 -ab 128k -ar 44100 -s 640x480 -ac 2 -y OUTPUT.flv


the same with mencoder 

mencoder  INPUT -oac lavc -ovc lavc -of lavf -lavcopts vcodec=flv:vbitrate=700:acodec=libmp3lame:abitrate=128 -ofps 30 -srate 44100  -o /tmp/OUTPUT.flv

---

