---
title: "Alsa issue with SiS 7012 on 8.04server"
date: 2008-12-18
forum: Server Platforms
---

### Post by janascii on 2008-12-18
I'm trying to setup alsa on my server box so that I can run mpd.
Alsa doesn't want to work though.  I've got 8.04server installed with all updates and a SiS 7012 chipset.  Everything I've found says that it should use the snd-intel8x0 module but I cannot get it to work.... Anyone know how to force alsa to see a sound card?

---

### Post by janascii on 2009-01-02
After fighting with this for a while... I found out my username wasn't in the audio group.  I'm still waiting to figure out if it actually works, but I have access to alsamixer now so I'm optimiztic.

---

### Post by TestDummy! on 2009-01-02
Sometimes, the main volume control is muted in alsamixer, if I recall, detonated like "00" in a green box.

Edit: Apparently I have that backwards, "MM" detonates mute.

> When a mixer control is turned off, M (mute) appears below the volume bar. When it's turned on, O in green appears instead. You can toggle the switch via m key.

---

### Post by janascii on 2009-01-03
The main was muted as well.  So that is fixed and its playing from the ncurses interface of vlc.  Strangely though the "Headphone" level seems to control the output(maybe because its a laptop).   

Thanks for the suggestion.

---

