---
title: "Sound in WINE dissappeared 3 days ago"
date: 2010-12-20
forum: Wine
---

### Post by Deadtrooper on 2010-12-20
[LEFT]Hi,

Sound in WINE/Spotify was working and then it wasn't. 10.10 64 bit. I am presuming an update broke/changed something, any ideas on how to fix this? I don't use Linux very often, so presume I haven't a clue.

Thanks,
Steve
[/LEFT]

---

### Post by Spyderkid on 2010-12-23
You need to go into

Wine > Wine configuration > Audio THEN...

> Tick the ALSA driver
> choose Emulation on Hardware Acceleration
> Make the default sample rate 44100 (IF IT ISN'T ALREADY)
> Make the default bits per sample 16 (IF IT ISN'T ALREADY)

And then try again.
if it doesn't work then you will have to un-install and install again

_________________

And hey presto your dreams come true!

---

