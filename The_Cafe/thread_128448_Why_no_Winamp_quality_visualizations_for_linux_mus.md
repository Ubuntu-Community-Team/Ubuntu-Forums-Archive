---
title: "Why no Winamp quality visualizations for linux music players?"
date: 2006-02-11
forum: The Cafe
---

### Post by MetalMusicAddict on 2006-02-11
"Goom" IMHO doesnt cut it. One thing I truly miss from my switch is visualizations for our music apps.
Especially with my Dell 2405FPW. :)

Why do you think this is lacking?

---

### Post by Lord Illidan on 2006-02-11
Have you checked out the Infinite plugin for Amarok and XMMS? It is also available for Beep Media Player.

It is part of libvisual : [http://localhost.nl/~synap/libvisual/](http://localhost.nl/~synap/libvisual/)

---

### Post by MetalMusicAddict on 2006-02-11
Ahh.. Cool. So devs need intigrate this into their players? Cant be something installed seperately and used with any music app? Do these go fullscreen? I gonna try with Amarok now. Where can I get the Infinite plug-in for Amarok?

---

### Post by MetalMusicAddict on 2006-02-11
Cant find a **amarok-libvisual** DEB. Just a RPM.

---

### Post by Lord Illidan on 2006-02-11
Just install package xmms-infinity from synaptic.

It will be added to amarok, since amarok uses xmms vis

---

### Post by MetalMusicAddict on 2006-02-11
I got it, thanx. Doesnt seem to be a GL vis. Hardware accellerated and all. Seems to be all CPU.

Is libvisual slated to work with your GFX card in the future? I cant find any info on that.

This looks to be a great project. I hope it takes off more.

---

### Post by johannes on 2006-02-11
Try out [ProjectM]("http://d072.apm.etc.tu-bs.de/~jluebbe/debian/unstable/"). Install with:
```

sudo dpkg -i projectm-common_0.97.5-1_all.deb projectm-vis_0.97.5-1_i386.deb projectm-xmms_0.97.5-1_i386.deb
```

---

### Post by potrick on 2006-03-18
So how do you get Infinity to work with Beep Media Player? Just wondering because you said it could be done

---

