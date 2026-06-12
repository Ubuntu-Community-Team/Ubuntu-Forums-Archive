---
title: "Linux Multimedia and GStreamer"
date: 2005-09-20
forum: The Cafe
---

### Post by peteog on 2005-09-20
I recently ripped some clips from DVDs to ogg files using thoggen 0.4 then tried playing them back using totem-gstreamer in breezy (0.8). I found that the AV sync was a little off. I then decided to install gstreamer 0.9 and totem from cvs and wow, it looks like video under linux will eventually get there.

I just wanted to get some feedback to see how well the following oggs play on your computers...

right click save or they should play directly in the browser by clicking on them if you have the totem mozilla plugin installed.

[XFiles.ogg](http://www.peteogrady.com/video/xfiles.ogg) (2mb)
[MIB](http://www.peteogrady.com/video/mib.ogg) (4mb)
[Layer Cake](http://www.peteogrady.com/video/layercake.ogg) (7mb)

---

### Post by rubinstein on 2005-09-22
I downloaded your files an they play perfectly here with the newest breezy and totem-xine. With totem-gstreamer however there is a noticable lag between sound and video. Maybe with ubuntu 6.04 I don't need to install totem-xine instead of totem-gstreamer :-)

---

### Post by poofyhairguy on 2005-09-22
[QUOTE=rubinstein]Maybe with ubuntu 6.04 I don't need to install totem-xine instead of totem-gstreamer :-)[/QUOTE]

Totem Xine is so awesome though in Breezy. 

Does Totem gstreamer play nice with the w32codecs?

---

### Post by doclivingston on 2005-09-23
[QUOTE=poofyhairguy]Does Totem gstreamer play nice with the w32codecs?[/QUOTE]

It will use some of the codecs from it (including wmv9) if you install gstreamer0.8-pitfdll from universe.

---

### Post by rjstevens3 on 2005-09-23
maybe that gstreamer0.8-pitfdll will solve all my problems!

i'm going to try it out. do i need any other packages to play anything i find on the web or on a disk?

---

### Post by doclivingston on 2005-09-23
You just need the gstreamer0.8-pitfdll package from Breezy universe, and w32codecs. It only supports a few codecs (wmv9, qd music 2 and indeo video 5) at the moment, but I've heard that it shouldn't be too hard to add support for others.

---

### Post by benplaut on 2005-09-23
grrr... i've never gotten codecs to work  :mad:

---

