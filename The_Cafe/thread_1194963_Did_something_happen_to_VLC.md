---
title: "Did something happen to VLC?"
date: 2009-06-23
forum: The Cafe
---

### Post by ZarathustraDK on 2009-06-23
I've had trouble getting fluid playback on 720p-stuff (on an old p4).

I don't have that no longer. What happened? From what I can see they still haven't done VDPAU yet.

---

### Post by jono2009 on 2009-06-23
> **ZarathustraDK said:**
> I've had trouble getting fluid playback on 720p-stuff (on an old p4).

I don't have that no longer. What happened? From what I can see they still haven't done VDPAU yet.


I had a problem playing VLC. After installing Jaunty, codecs, etc, etc. Current VLC after installing crashed, broke-up. Remembered the following help from this forum...    open VLC/tools/preferences/video(symbol)/output...change defaults to X11 video output/save.
hope it helps:P

---

### Post by snek on 2009-06-23
Hmm this is quite interresting, I will try tonight on my Sempron 3400+ because I've also had problems with HD videos in the past. However, I haven't really used VLC in a while because I just use Totem these days.

---

### Post by kalmahlk on 2009-06-23
> **snek said:**
> Hmm this is quite interresting, I will try tonight on my Sempron 3400+ because I've also had problems with HD videos in the past. However, I haven't really used VLC in a while because I just use Totem these days.

Single cores shouldn't really be used for HD content.

---

### Post by snek on 2009-06-23
> **kalmahlk said:**
> Single cores shouldn't really be used for HD content.

That's why I have 3 more machines with multicore cpu's.. ):P

---

### Post by CharmyBee on 2009-06-23
> **kalmahlk said:**
> Single cores shouldn't really be used for HD content.

My Sempron 2600 handled HD h264 1080p video fine. VLC just has some weird bottleneck in there that slugs the playback down.

---

### Post by LowSky on 2009-06-23
> **kalmahlk said:**
> Single cores shouldn't really be used for HD content.

says who... 

All you need is a graphics chip that supports at least 720P, and anything from ATI and Nvidia made in the last 2-3 years should just fine.

---

