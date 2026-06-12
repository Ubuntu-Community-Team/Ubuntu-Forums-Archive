---
title: "ClearChat usb headset and wine dmix"
date: 2009-09-07
forum: Wine
---

### Post by Macchia on 2009-09-07
I just bought this logitech cordless set and works out of the box but.. playing world of warcraft in wine i got a weird audio problem:
i know that alsa has dmix enabled by default now (i removed pulseaudio because too many problems) and multiple audio in firefox on youtube works.
Opening first world of warcraft makes my audio playing only form it, playing mp3 in audacious results in no audio (even configured to alsa).

but there's another catch that makes me think that dmix isn't enabled, since if i play mp3 and watch a video on youtube or in vlc, the same result happens (first audio plays only)
What's wrong?

---

### Post by Macchia on 2009-09-07
ok, found the problem, dmix has to be specified to use it (dunno why, on alsa site they say it's the default) in .asoundrc
But for those like me that uses teamspeak: no way, ts won't support dmix for now.

---

