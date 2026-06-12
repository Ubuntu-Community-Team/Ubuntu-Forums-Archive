---
title: "JACK kills all other audio?"
date: 2013-01-27
forum: Ubuntu Studio
---

### Post by lcooper145 on 2013-01-27
If I run jack (```
jackd & qjackctl
``` or ```
jackd & patchage
```), sometimes it starts up and sometimes it can't connect to the server, but that's another story. Usually I can get it running as long as I don't have any other applications open using the sound card.

Anyway, the problem is that after I quit jack, programs such as rhythmbox or youtube (aka programs that don't use jack) won't play audio anymore. Actually, the position marker doesn't even move to start playing. I have to restart my computer to get them working again.

Does this happen to anyone else?

I'm using ubuntu 12.10 with an ATI soundcard and ALSA.

---

### Post by Sylos on 2013-01-27
This sounds like perfectly normal behavior. Jack needs to control the soundcard, which means that the normal pulseaudio sound server (if its installed) cant be in control of it. The same happens to me. If you have problems getting control back from jack once you have stopped Jack, try the following:

```
sudo alsa force-reload
```

Also, if you are using pulseaudio then you try installing the pulseaudio jack-sink. That should then give you an input in jack connections window to allow sound from pulseaudio devices (web browser etc) to play through jack.

If you already removed pulseaudio and are just running straight into alsa then Im not sure if you have any way of making it run into jack.

Cheers

---

### Post by jejeman on 2013-01-27
>  after I quit jack,
Is jackd really dead?

---

### Post by AstroLlama on 2013-01-29
some applications, for example audacious, and skype, need to be set in their configuration options to use the jack server, or else their sound output won't reach jack server. this had me stumped for a long time then when i discovered it it was a "d'oh!" moment.

---

### Post by ttoine on 2013-01-31
The best is simply to install the Pulse Audio to Jack package:
pulseaudio-module-jack, using Software center, Synaptic or a command line like this one.

sudo apt-get install pulseaudio-module-jack

Then restart.

Any time you start jack, pulse audio will create a jack virtual sound card, just select it in sound preferences as the default output. It means that all desktop application (Firefox, Totem, Skype, ...) could be used on Jack, via Pulse Audio.

When you stop jack, all should become "normal" already.

---

