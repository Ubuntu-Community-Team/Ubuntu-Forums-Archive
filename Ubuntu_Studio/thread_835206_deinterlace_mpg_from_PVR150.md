---
title: "deinterlace mpg from PVR150"
date: 2008-06-20
forum: Ubuntu Studio
---

### Post by cotcot on 2008-06-20
I am capturing directly from my pvr150 using ```
cat /dev/video0 > test.mpg 

```(video from composite ; audio from mic in) The resulting file has no audio and needs to be deinterlaced. 
Any suggestion to get the audio in and have deinterlaced ?
(the microphone in works when I record the audio separately with audacity)

---

### Post by Creative2 on 2008-06-20
deinterlacing with mencoder : ideas (never tested)

cubic
```

mencoder -oac lavc -ovc lavc -of mpeg -mpegopts format=dvd:tsaf -vf scale=720:576,harddup -srate 48000 -af lavcresample=48000   -lavcopts vcodec=mpeg2video:vrc_buf_size=1835:vrc_maxrate=9800:vbitrate=4000:keyint=15:vstrict=0:acodec=ac3:abitrate=192:aspect=16/9 -ofps 25    -vf pp=ci  -o OUTPUT.VOB INPUT.XXX
```
(linear blend)----->
```

mencoder -oac lavc -ovc lavc -of mpeg -mpegopts format=dvd:tsaf -vf scale=720:576,harddup   -vf pp=lb -srate 48000 -af lavcresample=48000   -lavcopts vcodec=mpeg2video:vrc_buf_size=1835:vrc_maxrate=9800:vbitrate=4000:keyint=15:vstrict=0:acodec=ac3:abitrate=192:aspect=16/9 -ofps 25  -o OUTPUT.VOB INPUT.XXX


```

another deintelaced string

```
mencoder -oac lavc -ovc lavc -of mpeg -mpegopts format=dvd:tsaf -vf scale=720:576,harddup   -vf pp=fd -srate 48000 -af lavcresample=48000   -lavcopts vcodec=mpeg2video:vrc_buf_size=1835:vrc_maxrate=9800:vbitrate=4000:keyint=15:vstrict=0:acodec=ac3:abitrate=192:aspect=16/9 -ofps 25  -npp ci -o OUTPUT.VOB INPUT.XXX
```


audio issue : NO IDEA :(

---

### Post by Creative2 on 2008-06-20
why you don't use dvgrab? annD  if you have audio track you can add audio file with 


mencoder INPUT -oac copy -ovc copy -audiofile AUDIOTRACK  -o OUTPUT

---

### Post by cotcot on 2008-06-21
Thanks for reply.
I tried your first code. It is OK. (only changed the aspect ratio to 4/3)

For you seond reply : I hoped to get the audio together with the video to avoid synchronising issue by adding a separate audio file.

---

### Post by Creative2 on 2008-06-22
well but i think you have a camcoder microphone right?

you could use that , it looks strange capture video from camcoder and with another mic audio i think dvgrab should work better...

---

