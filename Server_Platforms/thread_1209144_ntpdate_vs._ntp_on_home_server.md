---
title: "ntpdate vs. ntp on home server"
date: 2009-07-10
forum: Server Platforms
---

### Post by memilanuk on 2009-07-10
Any opinions one way or another?

Machine in question is an older desktop PC turned server box - basic family file server (mainly for backups and common storage), maybe some amateur web development, etc.  I've heard the arguments about keeping precise time for log analysis in the event of a break-in, etc.  In what I would hope is a low-risk environment... is running ntpdate once a day (or even once an hour) sufficient to keep things running without the overhead of setting up and running ntp?  How far off is it really going to get just using ntpdate instead of ntp?

TIA,

Monte

---

### Post by slugmax on 2009-07-10
I would think once per day would be fine. That being said, ntp really isn't that much overhead on your server or network. I prefer the package 'openntpd', which won't need any config for basic use once you install it.

---

