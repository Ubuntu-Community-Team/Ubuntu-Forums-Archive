---
title: "virtual sound card"
date: 2009-06-12
forum: Server Platforms
---

### Post by lverl78 on 2009-06-12
I am trying to run firefox with embedded flash player on a server running ubuntu 8.04. I am using Xvfb and that part works fine. Firefox starts fine but the flash player doesn't always play the videos and I see the following in the log:

ALSA lib confmisc.c:768 parse_card) cannot find card '0'
ALSA lib conf.c:3513 _snd_config_evaluate) function snd_func_card_driver returned error: No such file or directory
ALSA lib confmisc.c:392 snd_func_concat) error evaluating strings
ALSA lib conf.c:3513 _snd_config_evaluate) function snd_func_concat returned error: No such file or directory
ALSA lib confmisc.c:1251 snd_func_refer) error evaluating name

There is no sound card on that server for obvious reasons. I tried to create a simple asoundrc but it doesn't help and I still get errors. I also tried to install pulseaudio server but that doesn't work with no audio hardware.

Is there a way to create a virtual sound card similar to Xvfb for the virtual display X server ?

Laurent Luce

---

