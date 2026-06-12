---
title: "virtualbox and having sound on gutsy when virtualbox is running?"
date: 2007-12-09
forum: Virtualisation
---

### Post by lime4x4 on 2007-12-09
Running gutsy with xp in virtualbox. I have sound in xp but if i leave virtualbox running then i don't have sound in gutsy i get the following error

The audio device is busy. Is another application using it?

Is there a way around this?

---

### Post by zyghom on 2007-12-09
I'm note even sure how it happened - mine is ok on both: xp and 7.10
maybe you use oss instead of alsa in vb ?

---

### Post by lime4x4 on 2007-12-27
nope using alsa. If i'm playing a sound file in gutsy then start xp in virtualbox then my virtual xp has no sound

---

### Post by Eck on 2008-01-01
Perhaps it's sound server related.  You could try it with and without the esd sound server turned on.  With it on, make sure you have libesd-alsa and not libesd, as sometimes package managers just install libesd (which hooks into the alsa-oss emulation) because it's one of those libesd | libesd-alsa kind of dependencies.  It just picks the first one on the list which is the oss one and it really isn't as effective at managing multiple sound sources as the alsa based one.

Or just try turning off the esd sound server.  If you have a hardware dsp soundcard like the Creative cards, alsa will use it to give you multiple sound mixing.  If you just have on-board software soundchip's, then you likely are better served using the esd server.  You do lose the system sounds if you turn off esd.

If you're using that new Pulse Audio, I have even less of a clue what to try.

---

### Post by SysFail on 2008-02-13
I have this exact same issue also...I will try some of your suggestions and get back to this thread tonight hopefully...

---

