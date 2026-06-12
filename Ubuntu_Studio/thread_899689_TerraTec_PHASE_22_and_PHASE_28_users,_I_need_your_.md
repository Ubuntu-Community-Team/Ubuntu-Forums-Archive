---
title: "TerraTec PHASE 22 and PHASE 28 users, I need your help."
date: 2008-08-24
forum: Ubuntu Studio
---

### Post by RIV@NVX on 2008-08-24
This is the probably the biggest community of Linux users on the internet, so I thought it would be best chance to find someone who has one of these cards here, as they aren't that common.

Here is the deal. Those cards (PHASE 22 and PHASE 28, that is) use Envy 24 HT-S chip, which doesn't support MPU-401 standard (in other words, thay have a non-standard MIDI). Until ALSA 1.0.17, MIDI was broken and accessing MIDI device of that card would hang the system.

(PHASE 88 is a different story, it uses Envy 24 and MIDI worked good for a while for it.)

But, thanks to work of Clemens Ladisch, Pavel Hofman and Takashi Iwai, this is now [solved]("http://mailman.alsa-project.org/pipermail/alsa-devel/2008-May/007624.html"). They say it works great. However, on TerraTec PHASE 22, I still have no MIDI devices listed at all. That is, "amidi -l" shows:
```
vedran@kalopsia:~$ amidi -l
Dir Device    Name
vedran@kalopsia:~$
```

All I want you to is to post details about your card, along with output of "lspci -vv" (only relevant part) and "amidi -l". I would like to make sure that my card isn't broken before I start messing with source.

Thanks in advance!

[SIZE="1"]Fingers crossed! Hope that some people still have these cards...[/SIZE]

---

