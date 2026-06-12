---
title: "Poor Morrowind Performance"
date: 2010-06-28
forum: Wine
---

### Post by Majin Zero on 2010-06-28
Wine 1.2
Ubuntu 10.4 32bit

2.0 Dual Core Pentium
2 gigs DDR2 RAM
Intel GMA 4500HDm

On windows, it runs poorly, but it's at least playable, 20ish FPS.

Via Wine though, I'm getting about 5-10 FPS, completely unplayable, and this is while still on the boat while naming your new character.

any ideas on how to increase performance?

---

### Post by hikaricore on 2010-06-28
It's your "video" hardware.
You're never going to get good perfomance from it on linux especially if it runs that badly in windows.

You may have to just get a real card like nvida (or ati).

---

### Post by Majin Zero on 2010-06-28
That's too bad, it's a laptop, so I can't upgrade the video card. I really didn't want to consider a dual boot just for one game...

---

### Post by asdfoo on 2010-06-28
> **Majin Zero said:**
> That's too bad, it's a laptop, so I can't upgrade the video card. I really didn't want to consider a dual boot just for one game...

You could look into trying ubuntu edgers.  It's a way of getting closer to development versions of some parts of the system that deal with your video hardware.

---

### Post by NightwishFan on 2010-07-31
I have a Mobile 4 Series Chipset Integrated Graphics Controller, and I find Morrowind is pretty much unplayable on the stock Ubuntu Wine Beta. It runs better on Wine 1.0, but has a few issues there as well. Wine 1.2 seems to handle it the best. Perhaps try Wine 1.0 if you have not already.

---

### Post by Progressive on 2010-08-01
Be sure you have the [absolute latest]("https://launchpad.net/~xorg-edgers/+archive/ppa") drivers for your video card and be sure you have the most recent version of Wine (currently 1.2)

Also make sure you have turned off all other processes on your computer that are running in the background. If you are using KDE, look in your system tray and stop strigi from indexing your files.

You could also look into getting certain native dlls for Wine... MSVCP60 is one of them that used to be necessary. Experiment with others like d3d8, dinput8, dinput, ntdll, and binkw32.

Perhaps most promisingly, there actually are ways to improve performance of Morrowind itself without reducing the gameplay experience.

Try the following:

1) Run [Pyffi]("http://cs.elderscrolls.com/constwiki/index.php/Nif_Optimization") on your entire Mesh directory, to optimize the meshes. This takes a long time, but it is worth it. No loss of quality. 

The linux console commands are about the same as the windows ones that are listed. You can even use the native linux version of pyffi, for maximum performance.

2) [Tweak the INI file]("http://www.uesp.net/wiki/Morrowind:Ini_Settings").

3) Try the Morrowind [Exe Optimizer]("http://timeslip.users.sourceforge.net/exeopt.html")

4) The [Morrowind FPS Optimizer]("http://planetelderscrolls.gamespy.com/View.php?view=utilities.detail&id=22"). 

5) If you're really gung ho, you could install the ubuntu version of the [Linux Unified Kernel]("http://www.longene.org"). Supposedly this can have speed increases of up to 80 percent, but it is currently based on Wine 1.0

---

