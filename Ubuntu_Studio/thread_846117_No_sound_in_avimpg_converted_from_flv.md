---
title: "No sound in avi/mpg converted from flv"
date: 2008-07-01
forum: Ubuntu Studio
---

### Post by jag7720 on 2008-07-01
I downloaded a video from youtube and then converted it to an .avi and a .mpg.  In both cases the newly created file has no sound.

I have tried several different players... still nothing.

I have tried several different conversion commands... here is a sample

ffmpeg -i T0YfdmBlTtg.flv -ab 128 -ar 44100 -ac 2  best.mpg

Can someone tell me how to convert .flv files and retain the sound?

Thanks

---

### Post by aquavitae on 2008-07-01
Try avidemux. You'll have to install it, but it has a nice gui and is probably eaier to use for this than the command line. I think ffmpeg only converts video, not audio. To convert both (using the command line) try mencoder or transcode, which uses ffmpeg to convert the video. But I think avidemux is your best bet.

---

### Post by Creative2 on 2008-07-01
search fuoco tools
(NB ADD MEDIBUNTU REPOSITORY TO YOUR REPOSITORY  )

ffmpeg -i INPUT -r 25 -f mpeg -vcodec mpeg2video -ar 48000 -b 900k -ab 256k -s 320x240 -y OUTPUT

---

### Post by penguin007 on 2008-07-03
Try VLC - works for me

---

