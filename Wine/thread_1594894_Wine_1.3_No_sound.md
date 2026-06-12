---
title: "Wine 1.3 No sound"
date: 2010-10-12
forum: Wine
---

### Post by tristan8276 on 2010-10-12
Hey all,

I just installed Maverick and it seems awesome so far.  The only thing I noticed is that now Wine can't find any usable audio drivers.

I get this message when I go to the audio tab after running winecfg:

ALSA lib seq_hw.c:457:(snd_seq_hw_open) open /dev/snd/seq failed: No such file or directory

Any ideas?

Thanks in advance.

---

### Post by s.fox on 2010-10-12
Thread moved to Wine

---

### Post by Half-Left on 2010-10-12
Try installing alsa oss packages

---

### Post by 68pontiac on 2010-10-15
I can confirm that installing alsa-oss from Synaptic solves the problem. :-)

---

