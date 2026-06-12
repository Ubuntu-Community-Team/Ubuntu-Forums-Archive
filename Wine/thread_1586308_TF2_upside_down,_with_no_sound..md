---
title: "TF2 upside down, with no sound."
date: 2010-10-01
forum: Wine
---

### Post by Dukenukemx on 2010-10-01
Title says it.  I'm using 10.04 64-bit with Wine 1.3.

---

### Post by Dukenukemx on 2010-10-03
No one can help me?

---

### Post by X1R1 on 2010-10-03
See if this helps, its meant for 64 bit arch, but you can use it still (with some differences obviously). Also check the steam launch options part there. That might help.

Im pretty sure your sound problem its because you dont have the lib32 alsa (again, check link).

Link:
[http://snott.net/software/installing-steam-and-team-fortress-2-on-64-bit-archlinux/](http://snott.net/software/installing-steam-and-team-fortress-2-on-64-bit-archlinux/)

EDIT: let me explain a little bit, pacman (and yaourt) is arch package manager, so instead of pacman use apt-get install, maybe packages differ a bit in name but you should be able to identify them.

And 1 question: your video card drivers work well? What video card are you using?

---

### Post by Dukenukemx on 2010-10-04
I noticed this when I tried to test the sound in the wine config.  I had Terminal open, and saw this appear.

```

err:alsa:ALSA_CheckSetVolume Could not find 'PCM Playback Volume' element
err:alsa:ALSA_CheckSetVolume Could not find 'PCM Playback Volume' element
fixme:mixer:ALSA_MixerInit No master control found on HDA ATI HDMI, disabling mixer
fixme:mixer:ALSA_MixerInit No master control found on HDA ATI HDMI, disabling mixer

```

As for sound, I typed "sudo apt-get install lib32-alsa-lib" and got this as a result.

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package lib32-alsa-lib

```

I have a ATI Radeon 4670, and I think it's built in sound is interfering with my Realtek HD sound on my motherboard.  So far I haven't been able to select 5.1 sound output, as I don't have that option in Ubuntu. Maybe it's the same reason why I get no sound in TF2?

---

