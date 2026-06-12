---
title: "Sound not working in Ubuntu 12.04 (old laptop -- daru1)"
date: 2012-09-25
forum: System76 Support
---

### Post by bogustrumper on 2012-09-25
Hello,

I'm running an older laptop, the Darter Ultra daru1. Just installed Ubuntu 12.04, amd64, fresh installation. Haven't done much to it. The System76 driver says that everything is supported through Ubuntu, so... guessing that's not needed. Anyway, I'm not getting any sound out of this, speakers or headphones.

I've tried going through the sound troubleshooting procedures, but I'm not getting anywhere, so I thought I'd post here and see if anybody has any ideas.

In previous versions of Ubuntu, I'd go in to /etc/modules.d/alsa-base.conf and add options snd-hda-intel model=3stack, then it all works. With 12.04, I get nothing.

lspci:
```
user@laptop:~$ lspci | grep Audio
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 02)
```codec:
```
user@laptop:~$ cat /proc/asound/car*/co* |  grep Codec
Codec: Realtek ALC660
Codec: Motorola Si3054
```One thing I'm noticing is that I get a digital output sound device in Sound Settings. And, well... there's no s/pdif ports on my computer at all. And no matter what I set in alsa-base.conf, I get the s/pdif option. What am I doing wrong?

---

### Post by isantop on 2012-09-26
Try inserting, then removing a headphone plug. It may be that the mute-switch in the jack is stuck, and this should free it.

---

### Post by bogustrumper on 2012-09-27
Tried giving it a little of the old in-out. No change. Nice thought, though. :)

---

### Post by hefny on 2012-09-28
=d>

---

