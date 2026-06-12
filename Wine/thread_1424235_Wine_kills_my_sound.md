---
title: "Wine kills my sound"
date: 2010-03-07
forum: Wine
---

### Post by Cleveland Rock on 2010-03-07
A [similar, unsolved problem]("http://ubuntuforums.org/showthread.php?t=1355323") seems to have been posted already.

I am using Ubuntu 9.10 32-bit and Wine 1.1.40.

Every time I open something using Wine, it kills my audio. Closing Wine doesn't help; the only way to get my audio back is to log out and log back in. This is a major inconvenience for me, as I need Wine for audio production in LMMS.

The ALSA driver is currently selected in my WINE configuration, but I've tried the OSS driver and had the same problem.

Sometimes, something as simple as opening Steam with Wine will kill my sound, but not always.

Please help if you can. I am a n00b, so keep that in mind. Thanks.

---

### Post by Soulcage on 2010-03-08
People say that the problem is pulse audio and that you should uninstall it.
Personally I haven't had any problem with any wine game, though I did have a problem with a native game (tremulous) the sollution was to install libsdl1.2debian-pulseaudio then restart which fixed it. Give this a try and post back.

---

### Post by Cleveland Rock on 2010-03-08
Earlier today, Ubuntu needed to update, so I updated. Afterwards, it screwed several things up, including my graphics and sound settings. After I enabled my NVIDIA graphics driver, I switched my audio output device to "CA0106 Soundblaster Analog Stereo", and now I'm not having the same problem anymore. Weird.

How do I mark this thread as solved?

---

### Post by Soulcage on 2010-03-09
Assuming it hasn't been disabled click on thread tools.

---

### Post by Ferrat on 2010-03-09
start winecfg if you haven't and first try ALSA if that doesn't work try OSS, I've noticed that sometimes the sound can crash when using ALSA and starts up again but crackels but all you have to do is stop WINE and restart pulse and it should work again without the cracks in the sound

---

