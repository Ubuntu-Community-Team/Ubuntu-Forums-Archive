---
title: "How can I make my computer display it's desktop on a TV via S-VIDEO cord?"
date: 2009-03-07
forum: The Cafe
---

### Post by gymophett on 2009-03-07
I have an S-Video cord, a place on the TV and Laptop, and I run Ubuntu 8.10
I have a video on here that I would like to watch with my grandparents, if I hook it up, will it instantly just work or is there more to it?

---

### Post by kevin11951 on 2009-03-07
> **gymophett said:**
> I have an S-Video cord, a place on the TV and Laptop, and I run Ubuntu 8.10
I have a video on here that I would like to watch with my grandparents, if I hook it up, will it instantly just work or is there more to it?

what graphics card, if its an nvidia, then yes, otherwise, i dont know.

---

### Post by xpod on 2009-03-07
I use the DVI/HDMI on our newer TV`s but i had more luck with S-Video to Scart on the older ones than what i did with S-Video to S-video.
All depends on the GFX as already mentioned so you can but try.

---

### Post by warp99 on 2009-03-07
If your running the nvidia or ATI proprietary drivers you can use either the nvidia-settings manager or the ATI manager to enable the TV. With ATI you can also enable the TV out "on the fly" with the following command:

```
aticonfig --enable-monitor=tv --effective=now
```

---

### Post by CarpKing on 2009-03-07
If you are using the free ATI or Intel drivers, you can use XrandR (search for that if you want more information).  After plugging the cable in, enter something like:
```
xrandr --addmode S-video 800x600
xrandr --output S-video --mode 800x600 --crtc 1
```

This will show the upper left 800x600 portion of your screen on the TV (which is enough to fill the TV).  Use Mplayer (with video in a separate window) or the fullscreen might not go to the TV's size.  If you get a black square on the TV where the video is supposed to be, install and use xvattr:

```
sudo apt-get install xvattr
xvattr -a XV_CRTC -v 1
```

The latter sets the Xv video output to the TV instead of the computer (replace the 1 with a zero to switch it back).  

If light parts of the screen are garbled, use gxvattr (in Multimedia and Video menu) to lower the brightness.  This seems to reset itself each time the video window closes.

---

