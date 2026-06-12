---
title: "Foobar2000 with wineasio?"
date: 2008-12-28
forum: Ubuntu Studio
---

### Post by chaozh on 2008-12-28
I have AudioFire2 1394 sound card. I installed ffado and jack server and they can works well. I can play music or movie through mplayer with audiofire2. But I have many ape/flac music. So I want to use foobar2000 under wine and hope foobar200 can play through audiofire2. From google. seems wineasio can do it. I installed it but foobar200 also can not work on audiofire2. Anybody can help me or have a good idea? Thanks a lot!

I don't want to use Bill's baby.:P

---

### Post by thorgal on 2008-12-28
don't know close to anything about ffado but wine is using ALSA (or OSS). Someone can speak up if ffado can be used as WINE's audio backend but I doubt it. Jack can use ffado as its backend but now you see that if WINE can only use ALSA, you're screwed. You can try to open winecfg from a terminal, select the Audio tab and see if you can use the JACK backend but I doubt it will work.

---

### Post by Stochastic on 2008-12-28
You'll need to setup alsa to send an output to jack.  FFADO only works with jack as far as I know, so you need wine to send to something that can route into the jack server.  

Aren't there any media players in Linux that can do ape/flac playback (probably just some codecs you need to download) - ask in the Multimedia & Video forums.  (actually, a quick google search tells me XMMS will do the trick)  That'd be much simpler.

---

