---
title: "Why is ALSA broken?"
date: 2005-05-10
forum: Repositories &amp; Backports
---

### Post by mtbeedee on 2005-05-10
I just installed Hoary.

I set the gnome volume control to control my realtek nforce2 (ALSA mixer)'s PCM device and I am able to control the volume of my system sounds just fine.

I then installed mplayer-586 and xmms.

xmms didnt work... I went into the config and made sure it was using alsa as the output method and even played with the device stuff.  It wouldnt work.  I switched it to esound and it worked.  Which I guess is good for xmms, but what about mplayer?  by default it tries to use the default alsa device as it should, but which doesnt work.

am I going to have to play with the settings of every program that I want to hear sound from to make it work?  Or is there something I am missing?

---

### Post by mtbeedee on 2005-05-10
I get this message in the console when trying to play to the alsa output thing:

** WARNING **: alsa_setup(): Failed to open pcm device (default): Device or resource busy

---

### Post by mtbeedee on 2005-05-11
Has anyone else heard a weird lightsaber like noise that accompanies mouse movement? Or a weird pulsing noise that accompany's a keypress?

How do I get rid of that?

---

