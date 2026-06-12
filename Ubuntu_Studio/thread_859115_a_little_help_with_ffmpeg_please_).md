---
title: "a little help with ffmpeg please? :)"
date: 2008-07-14
forum: Ubuntu Studio
---

### Post by scoobymad555 on 2008-07-14
hey peeps

pretty new to playing with ffmpeg and am trying to re-encode a mov file to mpg (dvd compatible).

the mov files internals are h264, yuv420p for the video and aac for the audio according to ffmpeg.

command line i'm using is :

ffmpeg -i {infile.mov} -target dvd-pal {outfile.mpg} 

it may not be the most complicated command line but it's successfully worked on other formats with no problems.

i'm getting this error (screens worth of the same thing):

[aac @ 0xb7e5a9a8]FAAD library: cannot resolve faacDecGetErrorMessage in libfaad.so.0!

and as a result all i'm getting is an empty container file at the end of it.

I'm assuming its something to do with the aac codec but i don't know where to go from here or how to fix it and haven't really found much from scrounging round on google :( any help would be greatly appreciated cos its doing my head in! lol! 

should maybe mention, currently i'm using devede instead to re-encode it but a 45min long file is taking the better part of 2 hours to rework and considering it starts out life at around 180mb, its a little shocking that devede spits out something that usually caps the 1gig mark! lol! 

help!!! :)

---

### Post by kostkon on 2008-07-14
First of all, are you using the version of *FFmpeg* provided by the [*Medibuntu* repository]("http://medibuntu.org/") (and has the support for restricted formats enabled)?

---

### Post by Creative2 on 2008-07-14
+1 kostkon

version of ffmpeg is wrong

---

### Post by jac0b on 2008-07-14
It could be this also.
[https://bugs.launchpad.net/medibuntu/+bug/225060](https://bugs.launchpad.net/medibuntu/+bug/225060)

---

