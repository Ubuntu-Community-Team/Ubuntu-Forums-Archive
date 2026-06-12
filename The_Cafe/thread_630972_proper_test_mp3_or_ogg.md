---
title: "proper test mp3 or ogg"
date: 2007-12-03
forum: The Cafe
---

### Post by mouseboyx on 2007-12-03
ok this is a proper test of the previous
Both files riped from cd quality using sound juicer
ogg = audio/x-raw-float,rate=44100,channels=2 ! vorbisenc name=enc quality=0.5 ! oggmux

mp3 = audio/x-raw-int,rate=44100,channels=2 ! lame name=enc mode=0 vbr-quality=6 ! id3v2mux

quality adjusted for same file size.

[http://mouseboyx.ath.cx/music/](http://mouseboyx.ath.cx/music/)

---

