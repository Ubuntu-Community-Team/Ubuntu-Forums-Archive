---
title: "JACK and Hydrogen audio issues"
date: 2009-09-10
forum: Ubuntu Studio
---

### Post by Rog-Mahal on 2009-09-10
I'm running Ubuntu Studio 9.04 64 bit with the rt kernel on a Macbook 2,1. I've set jack and my audio group to have realtime access to the kernel. Unfortunately, when I start my jack server, all my audio cuts out. When I start hydrogen, I get the following error:

```
Hydrogen comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions. See the file COPYING for details

Using data path: /usr/share/hydrogen/data
[LadspaFX::getPluginList] reading directory: /usr/lib/ladspa
[LadspaFX::getPluginList] reading directory: /usr/lib/hydrogen/plugins
[LadspaFX::getLadspaFXGroup]
[LadspaFX::getPluginList] reading directory: /usr/lib/ladspa
[LadspaFX::getPluginList] reading directory: /usr/lib/hydrogen/plugins
[ERROR]     AlsaAudioDriver   	ALSA: cannot open audio device hw:0: Device or resource busy
[WARNING]   AlsaAudioDriver   	[connect] Using alsa device: default

```

It seems like jack ties up my audio output somehow. As soon as I stop it, everything reverts to working fine (except for the horrible latency I get). 
Any thoughts? It seems like there's just one wrong value in a configuration somewhere...

Cheers!

---

### Post by g-raf on 2009-09-13
How did you set jack and the audio group to have realtime access to the kernel?

---

### Post by Rog-Mahal on 2009-09-14
I edited /etc/security/limits.conf to include the following options:

```
    @audio     - rtprio 99
    @audio     - memlock 512000
    @audio     - memlock 1000000
    @audio     - nice -10
```


I think that I'm ultimately trying to get pulseaudio to run as a jack client, but I'm still not sure how.

---

