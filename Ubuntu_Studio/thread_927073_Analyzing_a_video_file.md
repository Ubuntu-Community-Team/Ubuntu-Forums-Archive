---
title: "Analyzing a video file?"
date: 2008-09-22
forum: Ubuntu Studio
---

### Post by khughitt on 2008-09-22
Anyone have any suggestions for a quick way to get some meta-information about a video file? (codec, etc).

Something like ImageMagick's "identify" command would be wonderful.

Thanks!
Keith

---

### Post by JEDIDIAH on 2008-09-22
> **pwnedd said:**
> Anyone have any suggestions for a quick way to get some meta-information about a video file? (codec, etc).

Something like ImageMagick's "identify" command would be wonderful.

Thanks!
Keith

Something like...

   mplayer -identify -vo null -ao null -frames 0 -v mymovie.avi

---

### Post by rsambuca on 2008-09-22
How about you just 'right-click' the file, then select Audio/Video Properties?

---

### Post by FakeOutdoorsman on 2008-09-22
FFmpeg does this well:
```
ffmpeg -i input.avi
```

---

### Post by binbash on 2008-09-27
[http://www.getdeb.net/app/TheMonoSpot](http://www.getdeb.net/app/TheMonoSpot)

---

### Post by cotcot on 2008-09-28
Open it in VLC. Go to --> View --> Stream and Media info. (or crtl I)

---

### Post by khughitt on 2008-09-29
Thanks everyone for the suggestions. All of the methods have worked out pretty well :)

---

