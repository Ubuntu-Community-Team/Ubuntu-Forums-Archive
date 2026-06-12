---
title: "WoW causes gnome logout"
date: 2009-02-12
forum: Wine
---

### Post by Ollock on 2009-02-12
I've tried searching this but I can't figure out if it's not out there or I just can't find the right search terms.  I've been trying to get WoW running and right now, and for some reason whatever i did that fixed the scrambled graphics seems to me causing me to get logged out of my desktop as soon as WoW starts.  The last time it happened, Nautilus crashed when I got logged back in.

Is this issue known anywhere?

---

### Post by hikaricore on 2009-02-12
That sounds like a video hardware/driver issue.

Please provide more info and ensure that your video drivers are properly installed.

---

### Post by Ollock on 2009-02-12
I'm using "Intel Corporation 8295G/GZ Integrated Graphics Controller".  When I look at Hardware Drivers it says "no proprietary drivers installed".

I pulled the Config.wtf from the Wow wiki and did some suggested modifications.  This problem really only happened when I was dealing with the WINE configuration (particularly disabling pixel shaders, which I have to do in order to get any kind of decent picture).

---

