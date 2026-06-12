---
title: "100% for any game in Wine"
date: 2010-01-31
forum: Wine
---

### Post by Spectre5 on 2010-01-31
Any game I start in WINE bring my computer to 100% CPU instantly.  This does NOT happen when I just start the wine configuration tool, but does happen when I start a game.  I have wine-1.1.31 from the repos (I don't remember if this happened with 1.0.1 and I don't care to find out as I made the switch to 1.1.31 since 1.0.1 didn't work for a game or two of mine).  The other "standard" windows applications do NOT seem to make wine go to 100% either (i.e. notepad or regedit).

Here are the games I have (all make the system go to 100%):
Kotor1/Kotor2
Ghost Recon (original)
Left 4 Dead (isn't working anymore for some reason...it used to - some update must have broken it as I haven't tried it in months now)

My computer should be able to play these without must trouble at all - 4 GB of ram, nVidia 9500GT with nvidia drivers (185.18.36), E8400 (3Ghz core 2 duo).

Any hints or ideas?  I've also tried playing with various configuration options in wine.

---

### Post by NightwishFan on 2010-01-31
Generally games are designed to utilize 100% cpu. In my case, games only use 50% since I have AMDx2. You can check on Windows for the same behaviour. The other apps are designed to not need constant CPU, so they remain idle when not in use.

---

### Post by Soulcage on 2010-01-31
Try updating wine to 1.1.37 it might help.

---

### Post by Spectre5 on 2010-02-01
> **NightwishFan said:**
> Generally games are designed to utilize 100% cpu. In my case, games only use 50% since I have AMDx2. You can check on Windows for the same behaviour. The other apps are designed to not need constant CPU, so they remain idle when not in use.

I haven't run windows in years, so I can't really test that.

---

### Post by Spectre5 on 2010-02-01
> **Soulcage said:**
> Try updating wine to 1.1.37 it might help.

This isn't available in the repos, is it?  I try to keep as many packages as possible on my computer from the repos so I don't have to think/remember to upgrade them :)

But I guess I could find a package of it or compile it...

---

### Post by Soulcage on 2010-02-02
Go here and follow the instructions [http://www.winehq.org/download/deb]("http://www.winehq.org/download/deb")
Or you could paste: "sudo add-apt-repository ppa:ubuntu-wine/ppa" into a terminal then "sudo apt-get update"
and "sudo apt-get upgrade".

---

