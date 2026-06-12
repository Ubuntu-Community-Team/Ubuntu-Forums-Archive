---
title: "Interesting Wine problem, WoW related"
date: 2009-07-06
forum: Wine
---

### Post by DiscoStu570 on 2009-07-06
Sooooo, I'm trying to use Wine in Ubuntu 9.04 to run world of warcraft.  Video card is an Nvidia GeForce 6800, i have all the right drivers and all installed.  Wine seems to be installed properly and to start up properly.  If I start with having Wine launch Launcher.exe, the launcher appears perfectly; when I hit play, the launcher goes away, but nothing else shows up.  The system monitor indicates that both wine and wow.exe are running, somewhere, but nothing is displayed.  When I go into wineconfig and tell it to emulate a virtual desktop or whatever the option is (sorry, writing this from a windows comp), the wine window, when wow.exe is running, is flat blue, with nothing going on.  Everything else Ive seen and read has WoW either giving error messages or causing system crashes, mine seems to be running, but its just not displaying.  Anybody have any ideas?  Ill update this post to be more accurate in a bit, if anybody wants any further details on xorg.conf readouts or anything like that I can look that stuff up, thanks in advance for your attention.

---

### Post by X-BANE on 2009-07-06
Are you running compiz while trying to play WoW?

---

### Post by DiscoStu570 on 2009-07-06
It's installed, but not doing anything.  Does it have to be uninstalled for WoW to run?  I have system>preferences>appearance>visual effects set to none, I don't have any crazy cube action or anything like that going on.

---

### Post by X-BANE on 2009-07-06
No it's just recommended to disable it when running things under Wine. You don't need to uninstall anything.

On the main issue, which driver are you using?

---

### Post by DiscoStu570 on 2009-07-06
The most recent release off nvidia's website,  [NVIDIA-Linux-x86_64-185.18.14-pkg2.run]("http://us.download.nvidia.com/XFree86/Linux-x86_64/185.18.14/NVIDIA-Linux-x86_64-185.18.14-pkg2.run").

---

### Post by X-BANE on 2009-07-06
Oh your using 64 bit?

---

### Post by DiscoStu570 on 2009-07-06
yea, its a recent install, nothing i read about the 64 bit suggested its a bad idea, so... im hoping it wasn't a bad idea.

Now that you said that though.  Thats it I guess?  A quick google search reveals that there are different builds of wine for 64 and 32, the 64 being apparently not entirely stable, and the 32 bit requiring some doing to work on a 64 bit install. 

Not entirely sure what to do, but at least I'm on the right page at this point, thanks for the help so far

---

### Post by X-BANE on 2009-07-06
Ok well I always use 32 bit. 64 bit is getting better, but it still has issues. I also have a GeForce FX card that has too use the 173.xx series of drivers (currently 173.14.20) and that works great with everything.

I would suggest returning to the bog standard 32 bit. It may be boring, but Wine has less isues with it.

Oh and by the way, which version of Wine are you using?

---

### Post by DiscoStu570 on 2009-07-06
Having poked around this issue quite a bit, I'm fairly certain that theres no reason my 32 bit Wine install should have problems running in a 64 bit ubuntu environment.

Im currently running wine 1.1.25, and have no idea why world of warcraft doesn't work with it.

---

### Post by Laids on 2009-07-06
I had the same exact problem.  The issue from what I could gather from hours of troubleshooting was that WINE + WoW + OpenGL did not like the 64bit Nvidia drivers.  WoW being a 32 bit application I think that is why it is crashing.  When you run WoW.exe check out your process list, I bet its sitting at the top eating up 100% CPU while not loading...  I tried to install the Nvidia 32 bit libraries but I still could not get it to work.  The only solution I could come up with was to install the 32 bit version of Ubuntu and after that WoW worked like a champ.

See [http://ubuntuforums.org/showthread.php?t=1204693](http://ubuntuforums.org/showthread.php?t=1204693)

---

### Post by Rody on 2009-07-07
have you tried to run Wow.exe and see what errors you get? I have no problem running wow in 64bit.

rody

---

