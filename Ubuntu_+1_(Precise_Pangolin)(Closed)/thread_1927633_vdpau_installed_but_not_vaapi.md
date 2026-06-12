---
title: "vdpau installed but not vaapi"
date: 2012-02-18
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by williammanda on 2012-02-18
I was just looking and saw that libvdpau1 is installed by default. I'm using intel sandy bridge and I had to install the i965 driver to get vaapi. Is vaapi going to be installed in the future?

---

### Post by mc4man on 2012-02-18
libvdpau1 is not included by default, ck any manifest
[http://cdimage.ubuntu.com/daily-live/current/](http://cdimage.ubuntu.com/daily-live/current/)

---

### Post by williammanda on 2012-02-18
Interesting....I don't have any video hardware that requires vdpau...all I have is intel. I didn't install it.

---

### Post by mc4man on 2012-02-18
Did you install mplayer, mplayer2 or a xine based player?

---

### Post by williammanda on 2012-02-18
> **mc4man said:**
> Did you install mplayer, mplayer2 or a xine based player?

The only media player I installed was mythtv. I guess that could be a possiblity but one would need to install nvidia drivers to use a nvidia card which I don't have.

---

### Post by Yellow Pasque on 2012-02-18
Installing mythtv will install libvdpau1 (libmyth depends on it) as well as libva1.

---

