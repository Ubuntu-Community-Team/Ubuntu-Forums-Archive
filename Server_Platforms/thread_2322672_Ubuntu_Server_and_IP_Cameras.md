---
title: "Ubuntu Server and IP Cameras?"
date: 2016-04-29
forum: Server Platforms
---

### Post by Mike_Burt on 2016-04-29
Hi I have a ubuntu server running raid 1 and my plex server that is headless. I have two security cameras and would like to know if I can attached them to my network and use some kind of software on my server machine - Lenovo TS140 to record the video. Also a way the remotely view it on a mobile device in this case an iPhone. Thanks

---

### Post by volkswagner on 2016-04-29
Zoneminder works with most ip cameras (need to send mpeg stream). 

There is a paid app (zmNija) in Android an Apple app stores, that integrates well with ZM.

You'll want to use the [Ubuntu PPA]("http://zoneminder.readthedocs.io/en/latest/installationguide/index.html") for use of zmNija.

---

### Post by izznogooood on 2016-05-02
I dont know about the software but I do know you should find one that supports the h264 (Sorry but mpeg is ollllld) codec and the Onvif protocol (90% of cameras).

This is very interesting :). I´ll be sure to let you know what i find.

---

### Post by houstonbofh on 2016-05-05
> **izznogooood said:**
> I dont know about the software but I do know you should find one that supports the h264 (Sorry but mpeg is ollllld) codec and the Onvif protocol (90% of cameras).

It may be old, but it is far less patent encumbered then h264!  :)  And zoneminder also does mjpeg if you do not like mpeg.

---

