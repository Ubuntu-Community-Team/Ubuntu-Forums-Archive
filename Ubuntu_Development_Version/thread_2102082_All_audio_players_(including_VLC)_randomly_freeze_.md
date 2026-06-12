---
title: "All audio players (including VLC) randomly freeze when playing mp3s."
date: 2013-01-06
forum: Ubuntu Development Version
---

### Post by rolandixor on 2013-01-06
I'm having a rather annoying (and weird) problem with audio players when playing mp3s. I don't get the problem with videos, only mp3s, and I can't seem to find the source of the problem. :mad:

[https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/1096589](https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/1096589)

If anyone else has this problem, I'd appreciate if you could add anything useful to this bug report or mark it as affecting you.

---

### Post by mc4man on 2013-01-06
Don't have any issue here with vlc (other than an ambiance theming issue when  libgnome2-common isn't installed.

As far as gstreamer players do see 'unresponsive windows' quite often, particularly with totem.
Found that [removing the gst pulse]("https://bugs.launchpad.net/ubuntu/+source/totem/+bug/1085342") audio plugin helped greatly with gst players.
(really only the 1.0 needs removal though I do away with both

```
sudo apt-get purge gstreamer1.0-pulseaudio gstreamer0.10-pulseaudio
```

---

### Post by ronacc on 2013-01-06
no problem here with the embedded player in google chrome playing streaming mp3's .

---

