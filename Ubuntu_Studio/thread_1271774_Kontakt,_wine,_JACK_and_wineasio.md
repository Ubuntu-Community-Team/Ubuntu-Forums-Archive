---
title: "Kontakt, wine, JACK and wineasio"
date: 2009-09-21
forum: Ubuntu Studio
---

### Post by Platonov on 2009-09-21
Hi all,

I'm trying to run Kontakt player under wine. Installation went fine, I get the graphics, but no sound. Wineasio is installed, and there are no other running apps, but JACK says: 
```

loading driver ..
apparent rate = 48000
creating alsa driver ... hw:0,0|hw:0,0|1024|2|48000|0|0|nomon|swmeter|-|32bit
control device hw:0
the playback device "hw:0,0" is already in use. 
Please stop the application using it and run JACK again
cannot load driver module alsa
no message buffer overruns

``` 
Any experiences?

In winecfg the ALSA-driver is the only one selected (emulation). I'm running wine-1.0.1.

Best regards,

Jethro.

---

### Post by Platonov on 2009-09-21
Ah, nevermind. This fixed the issue...

```

/sbin/alsa force-reload

```

Then restart with qjacktl.

---

### Post by thorgal on 2009-09-21
try in a terminal

```

fuser -v /dev/snd/pcmC*

```

you will see what has a grip on your soundcard(s).
Once you know, you can either kill it or terminate it gracefully, depending on your mood :)

---

### Post by Platonov on 2009-09-21
Great tip, thank you!

---

