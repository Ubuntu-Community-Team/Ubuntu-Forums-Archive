---
title: "Totem wmv support"
date: 2006-03-01
forum: The Cafe
---

### Post by cro.smiley on 2006-03-01
I'm having problem with playing some *.wmv movie files in Totem 1.2.1
(Movie Player using xine-lib version 1.0.1)

I get the following error:
```
Video codec 'MS WMV 8 (win32)' is not handled.
You might need to install additional plugins to be able to play some types of movies
```

But some *.wmv files i can play with no problems.
Codec of those files is Microsoft MPEG-4 v3 (ffmpeg).

What plugins should i download to play MS WMV 8 files?

---

### Post by Bragador on 2006-03-01
You should call Microsoft and ask them to support Linux more. I bet the tech support guy would remember this day forever.

;)

---

### Post by Bandit on 2006-03-01
[QUOTE=cro.smiley]I'm having problem with playing some *.wmv movie files in Totem 1.2.1
(Movie Player using xine-lib version 1.0.1)

I get the following error:
```
Video codec 'MS WMV 8 (win32)' is not handled.
You might need to install additional plugins to be able to play some types of movies
```

But some *.wmv files i can play with no problems.
Codec of those files is Microsoft MPEG-4 v3 (ffmpeg).

What plugins should i download to play MS WMV 8 files?[/QUOTE]
No WMP 8 codecs? I thought they all worked up to version 9.
Download totem and xine from my website and install them and see if that helps. 
I know all mine were working up to version 8. ver9 and above are not supported by Xine.
Cheers,
Joey

---

### Post by gord on 2006-03-01
make sure to [install the win32codec's](https://wiki.ubuntu.com/RestrictedFormats), allthough if they are encoded with DRM then you won't be able to play them.

---

### Post by cro.smiley on 2006-03-01
[QUOTE=gord]make sure to [install the win32codec's](https://wiki.ubuntu.com/RestrictedFormats), allthough if they are encoded with DRM then you won't be able to play them.[/QUOTE]

How can i see if they are encoded with DRM?

---

### Post by gord on 2006-03-01
use windows with windows media player. unfortunatly the DRM technology is not a nice one, maybe you can get windows media player working with wine, but i wouldn't expect so.

---

