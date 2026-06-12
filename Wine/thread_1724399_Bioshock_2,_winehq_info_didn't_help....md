---
title: "Bioshock 2, winehq info didn't help..."
date: 2011-04-08
forum: Wine
---

### Post by Arpage on 2011-04-08
Hey folks,

I've been googling the web and can't seem to find anything about the problem I'm having with Bioshock 2. 
-Installation went fine as well as the update to v1.3
-Copied xlive.dll into the Binaries directory of the game

Here's where it goes wrong... I recieve the message: 

> ERROR [-2]  Bioshock2.exe cannot be launched directly. Please launch using Bioshock2Launcher.exe...funny thing is, I am trying to launch the game using Bioshock2Launcher.exe NOT Bioshock2.exe :rolleyes:

The nocd crack is tested in WinXP and Win7 and works so I presume it's not the .exe itself..

Any idea's?

using Wine1.3, Winetricks vcrun2008, d3dx9

on 

Ubuntu 10.10x86_64

---

### Post by sakuramboo on 2011-04-08
Sometimes Wine just doesn't work.

Another reason to play only native games.

---

### Post by Dlambert on 2011-04-08
Try [PlayonLinux]("http://www.playonlinux.com/en"). :)

---

### Post by scraze on 2011-04-09
I'm having the same problem, though on Debian Wheezy. Posted this on [WineHQ]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=19342")  :

> Running into a seemingly different problem. Downloading in Steam & unlocking game with serial through Steam went fine with wine 1.3.17 (from git) on Debian Wheezy / x86-64. Launching however produces the following error:

ERROR [-2]
BioShock2.exe cannot be launched directly. Please launch using BioShock2Launcher.exe

The same error appears when following the suggestion to launch using BioShock2Launcher.exe. Installing the xlive dll from timeslip also didn't change the situation.

So far only tried rzr-bio2f.7z with md5sum 742739efded5d8ef17fa857f898e8abb, replaced some files in SP/Builds/Binaries/ (after a backup). When executing Bioshock2Launcher.exe, an animated Razor 1911 splash pops up, then Bioshock 2's tiny splash, and then a maximized window is created with a cross-shaped cursor, and instantly the program crashes. This happens with wine-1.3.17 as well as wine-1.3.14.

Tried to create a sensible log file but am unsure as to the proper WINEDEBUG options. A log of WINEDEBUG=+tid,+seh with razor's Bioshock2Launcher.exe can be found here: [http://pastebin.com/jnDm9JhW](http://pastebin.com/jnDm9JhW) . The same command for the original Bioshock2Launcher.exe creates a log file of 34Mb, so I'll refrain from posting that until I've found the correct WINEDEBUG options. Not sure whether it's any good to anyone in this format :}.

I've installed Bioshock 2 in my main wine prefix, which has a number of specific settings for libraries for different games; I could very well be causing the problem in that way. Will test with a clean prefix asap.

P.S. : FWIW, a thread on Ubuntu forums describes the same problem: [http://ubuntuforums.org/showthread.php?p=10653250](http://ubuntuforums.org/showthread.php?p=10653250) 

I'll let you know if I can figure out anything else.

---

### Post by scraze on 2011-04-23
Bully Bull just posted this on WineHQ:
> 
Please test !!!
copy your alsoft.conf in your home directory
e.g.
cp /etc/openal/alsoft.conf ~/.alsoftrc
then open the file with kwrite or gedit .alsoftrc
change
#drivers = pulse,alsa,oss,solaris,dsound,winmm,port,wave
to
drivers = alsa
The game should start now!!!
the problem is that in the menu I have a keyboard but
when I start a new game and press the space bar nothing happens
XMODIFIERS trick don't work for me!
I have the DVD version!
wine version 1.3.14 till 1.3.18 always the same :(
It doesn't solve the "ERROR [-2] BioShock2.exe cannot be launched directly." from the original Bioshock2Launcher.exe, but it allows the game to start with the Razor1911 files. Apparently, OpenAL can get in the way of the device initialisation of certain games. 

Unfortunately, like Bully Bull I run into the problem that Bioshock 2 loses its input as soon as a new game is started. The keyboard works fine in the menu, allows controls to be configured - but when starting a new game & after waiting for it to load, it says "PRESS -SPACE- TO CONTINUE" yet doesn't seem to receive keypresses. On WineHQ, kf reported having success with prefixing the wine command with variable declaration XMODIFIERS='', i.e.
```

XMODIFIERS='' wine Bioshock2Launcher

```It didn't work for me - I'm still looking for a solution. However, this problem seems a lot less complicated than not getting the game to start at all. Here's hoping XMODIFIERS='' will work for you!

---

