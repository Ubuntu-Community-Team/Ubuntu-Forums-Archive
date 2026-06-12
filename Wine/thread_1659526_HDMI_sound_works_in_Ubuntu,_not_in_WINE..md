---
title: "HDMI sound works in Ubuntu, not in WINE."
date: 2011-01-04
forum: Wine
---

### Post by Psyael on 2011-01-04
Hi all. I own an Nvidia 4xx (Fermi) and had to make some system modifications to Ubuntu in order to use sound in most applications. See [this thread](http://ubuntuforums.org/showthread.php?t=1619995) for details. Basically, ALSA sees a lot of sound hardware, but card 1 device 7 is the only one that produces any noise.

To fix this, I added the following to alsa-base.conf:
```
options snd slots=snd-intel0x7,snd-pcsp
```

Since then, all sound works in Ubuntu apps (browser, video players, etc) by default, but sound isn't working in WINE. I went to WINE-config and the Audio tab was not able to find any hardware. It selected the Alsa tab as a guess, but the sound test failed.

Anything I can do? I'm sorta new (less than two months experience) so I'm afraid I can't go overboard into code/hack territory unless you hold my hand.

---

### Post by Psyael on 2011-01-04
So, a few updates:

1) Going to the audio tab of WINE-config complains that there is no audio driver in the registry.

2) Switching from ALSA to OSS sound makes the sound test work, and I got menu music in TeamFortress 2, but no sounds in the game.

---

