---
title: "Fullscreen with MPlayer ?"
date: 2005-04-08
forum: The Cafe
---

### Post by Sam on 2005-04-08
Hello

I've just installed MPlayer, but when I go to fullscreen mode, only the window goes fullscreen, the content doesn't fit the window.

How to do this ? Thank you.

---

### Post by dusu on 2005-04-08
Hi,

if you're using mplayer from the command line (I guess that's what your doing given what you say), you should specify a video output.
To use xv and watch super.movie, type something like that :
```
mplayer -vo xv super.movie
```
Another way of doing things is to use the gui version, namely gmplayer.
Enjoy  :grin: !

---

### Post by Sam on 2005-04-08
Thank you dusu, it works now ! :-P

---

### Post by dusu on 2005-04-08
You're welcome !
I just installed mplayer yesterday and had the same trouble as you :D

---

### Post by TravisNewman on 2005-04-08
[QUOTE=dusu]You're welcome !
I just installed mplayer yesterday and had the same trouble as you :D[/QUOTE]
 if you're using gmplayer, you may need to go into the video options and use a different video driver as well
(for any others who may have this problem)

---

### Post by Sam on 2005-04-08
[QUOTE=panickedthumb]if you're using gmplayer, you may need to go into the video options and use a different video driver as well
(for any others who may have this problem)[/QUOTE]
Yep, I had x11 driver set by default, and I just changed to xv.

---

### Post by titus on 2005-04-08
useful cli switches are :

-fs (fullscreen)
-zoom (to zoom content when in fullscreen)

These can be (may already be) set in your mplayer prefs (global or local).

Regards,

TS.

---

