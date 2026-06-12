---
title: "Warcraft 3 Choppy Sound."
date: 2008-12-12
forum: Wine
---

### Post by fivetwentysix on 2008-12-12
With OSS it's perfect, problem is PulseAudio doesn't mix it.
With ALSA it's choppy. 

So. I need the features of audio mixing and I need to ditch the choppy sound. What's my solution?

My system specs:
ASUS P5B mother board
Q6600 Intel Quad Core @ 2.4ghz CPU
4gb @667mhz
8800gts Nvidia
Ubuntu 8.10
Wine 1.1.9, from the [https://launchpad.net/~starfall87/+archive](https://launchpad.net/~starfall87/+archive) repository

---

### Post by binbash on 2008-12-12
did you try disabling pulseaudio and entering war3?

---

### Post by fivetwentysix on 2008-12-12
pasuspender wine war3.exe
1st test with ALSA: Choppy sound still.
2nd test with OSS: Had music playing in the background, couldn't initialize sound.
3rd test with OSS(no background app): Couldn't initialize sound.
4th test oss with pa on: Sound is perfect, no mixer features...

Still unsolved.

---

### Post by PandaGoat on 2008-12-12
refer to [http://ubuntuforums.org/showpost.php?p=6357282&postcount=90](http://ubuntuforums.org/showpost.php?p=6357282&postcount=90)

---

### Post by Ng Oon-Ee on 2008-12-12
Just install alsa-oss from synaptic.

Then run your app using:-

```
aoss wine <executable>.exe <options>
```

Oh, and don't forget to set the output to OSS first.

---

### Post by fivetwentysix on 2008-12-15
> **Ng Oon-Ee said:**
> Just install alsa-oss from synaptic.

Then run your app using:-

```
aoss wine <executable>.exe <options>
```

Oh, and don't forget to set the output to OSS first.

Still locks up my sound...

---

### Post by hotweiss on 2008-12-31
> **PandaGoat said:**
> refer to [http://ubuntuforums.org/showpost.php?p=6357282&postcount=90](http://ubuntuforums.org/showpost.php?p=6357282&postcount=90)

This did the trick for me.

---

### Post by Ng Oon-Ee on 2008-12-31
> **fivetwentysix said:**
> Still locks up my sound...
I'm aware that this is 2 weeks late, but I haven't been keeping up with this thread =).

If this command locks up sound, then Pulseaudio mustn't be running, or must be misconfigured. What it does is convert your OSS output (which is not choppy, obviously) to ALSA output, in simplistic terms. From then on, your system should be configured so that ALSA output plays through Pulseaudio. There are several good guides in the HOWTOs to this.

---

### Post by PandaGoat on 2008-12-31
Try installing alsa-oss:
```
apt-get install alsa-oss
```

Then run winecfg and make sure the audio is set to alsa and run Warcraft like this: 
```
env WINEDEBUG=-all aoss wine "C:/Program Files/Warcraft III/war3.exe"
```

---

