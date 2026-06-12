---
title: "Request: VLC 0.8.5 + up to date ffmpeg version"
date: 2006-08-31
forum: Ubuntu Backports
---

### Post by scotty64 on 2006-08-31
The new vlc version 0.8.5 of the videolan multimedia player has so many great new features that 0.8.4 (within Universe) does not have (JACK output, a mosaic wizard for combining multiple streams and and and).
We need a backport of this excellent program!
But looking on my "compiling from source" attempts I think that then ffmpeg would need an update as well, specially with "postprocessing" enabled. The missing postproc forced me to compile ffmpeg as well.

Thanks for all the work!

---

### Post by Anonii on 2006-08-31
Download the source code, and make it a .deb package?
[http://www.videolan.org/vlc/download-sources.html](http://www.videolan.org/vlc/download-sources.html)

---

### Post by scotty64 on 2006-08-31
See my edited message: I tried it and discovered that ffmpeg needs a rebuild as well.

---

### Post by anodizer on 2006-08-31
You can use this repo
#VLC nightlies
deb [http://nightlies.videolan.org/build/dapper-i386](http://nightlies.videolan.org/build/dapper-i386) /

GPG Key: 81CACA84

---

### Post by mlind on 2006-08-31
> **scotty64 said:**
> See my edited message: I tried it and discovered that ffmpeg needs a rebuild as well.

You can get ffmpeg source package from [http://www.debian-multimedia.org](http://www.debian-multimedia.org).
You probably also need to build x264 for ffmpeg.

---

### Post by scotty64 on 2006-09-01
anodizer / mlind: Thanks for your help!

---

### Post by Dillius on 2006-10-05
> **anodizer said:**
> You can use this repo
#VLC nightlies
deb [http://nightlies.videolan.org/build/dapper-i386](http://nightlies.videolan.org/build/dapper-i386) /

GPG Key: 81CACA84

Will this work if you're using an AMD64 build? I'm trying to do it but it's not showing up in the repo's.

---

