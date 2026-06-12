---
title: "Any way to use Wine under Ubuntu Server without GUI?"
date: 2010-11-01
forum: Wine
---

### Post by JeffreyZhao on 2010-11-01
I'm using a VPS with full root privilege but there's no chance to setup any GUI on it. I've a command line program written in C++, which read files from the disk and generate another. It's really simple, maybe it's just some basic calculation and pack algorithm.

Any way to archive that under my Ubuntu Server without GUI?

---

### Post by cogadh on 2010-11-01
I'm not sure I fully understand what you are trying to do, but Wine is a command line application, it doesn't really require the GUI as long as the app you are trying to run also doesn't need a GUI. Since the app you are trying to run is a command line app, then all you should need to do is fire up Wine's command line (run "wine cmd" in a terminal) and run it from there.

---

### Post by usagiakumu on 2010-11-01
Wine relies on x.org so no. You need x.org to run Wine. In effect you "could" run wine without X11 or x.org, but you are going to get a whole bunch of errors.  If you compile ttydrv, you should be able to run Linux and Wine without X, but it is heavily untested.

There is an alternate graphics driver called "ttydrv" (instead of  "x11drv") which you can 
use to run command line programs. This is configured in the  ~/.wine/config file - change 
GraphicsDriver from "x11drv" to "ttydrv". You might want to give this a  go, although 
it just seems to produce errors for me :-).

---

