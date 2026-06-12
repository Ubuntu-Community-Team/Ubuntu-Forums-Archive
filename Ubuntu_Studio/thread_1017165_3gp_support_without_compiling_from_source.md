---
title: "3gp support without compiling from source?"
date: 2008-12-20
forum: Ubuntu Studio
---

### Post by GargoyleMusic on 2008-12-20
Hi!

I am working on finding a solution for creating DVDs from our family's digital videos. We have a bunch of cameras/camcorders/cellphones, all of which save video in different formats.

I am having problems with the .3gp video format. Neither VLC nor totem will play these videos with audio (they only render the video, but no audio.) I want to be able to edit this video - or, at the very least, I want to convert the .3gp file to something else (.mpg, for example.)

When I try to use Kino for video editing, it attempts to convert the .3gp file but fails. When I try to use ffmpeg, I get ```
"Unsupported codec (id=73728) for input stream #0.0"
```

There are tons of guides on the forums about making this kind of thing work, but all of them require me to compile ffmpeg from source. This is doable, but not really sustainable (as we move computers, etc etc.)

SO: How, or where, can i get 3gp codecs to allow me to view/convert/etc these files in Ubuntu? Do they exist in the normal repositories (I'm running 8.10.) What am I missing? If it isn't possible to do this via "normal" means, that would be good to know too.

Thank you!

---

### Post by andrew.46 on 2008-12-21
Hi,

I have not tested this version myself but I suspect the medibuntu version of MPlayer may be what you need to at least play these files:

[http://packages.medibuntu.org/intrepid/mplayer.html](http://packages.medibuntu.org/intrepid/mplayer.html)

Conversion I suspect is still best done with the svn ffmpeg and compiled amr libraries. However if the Medibuntu MPlayer can play your files Mencoder should be able to convert them. If you are new to Medibuntu details can be seen here:

[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

All the best,

Andrew

---

