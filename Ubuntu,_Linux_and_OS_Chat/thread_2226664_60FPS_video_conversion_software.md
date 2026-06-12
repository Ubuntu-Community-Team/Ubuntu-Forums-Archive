---
title: "60FPS video conversion software"
date: 2014-05-28
forum: Ubuntu, Linux and OS Chat
---

### Post by ggodone on 2014-05-28
I'd like to make my videos 60FPS, because they look much better at that framerate than at 24/30 FPS. However, [SVP]("http://www.svp-team.com/") is Windows only and I had no luck installing it through Wine. Is there any software that does the same thing that's on Linux?

---

### Post by ssam on 2014-05-29
There is work in gstreamer to do smooth video interpolation (they are using it for smooth slow-mo, but I think its the same technique). I'm not sure that its packaged up and ready to use yet though. 
[http://fundraiser.pitivi.org/blog/2014/02/26/using-gstreamer-make-smooth-slow-motion/](http://fundraiser.pitivi.org/blog/2014/02/26/using-gstreamer-make-smooth-slow-motion/)

---

