---
title: "Trying to get Baldur's Gate 2 to work"
date: 2010-01-17
forum: Wine
---

### Post by fisher8484 on 2010-01-17
I'm having a bit of an issue regarding Wine and Baldur's Gate 2 on Ubuntu.  Here's my set up:  Ubuntu 9.10 Wine Version 1.1.31 Baldur's Gate 4-in-1 pack (with BG2 on one DVD and Throne of Bhaal on the other)  The problem isn't installing these titles, The installation wizard works perfectly and the demo movies work great as well.  Even when trying to initiate the game itself, the main menu works perfectly as well.  It's just that when I fire up the game (while using a DVD Rom) that the screen freezes and I have to CTRL-ALT-DEL to get out of it.  Has anybody gotten BG2 to work in Ubuntu?  Every other Windows based program I have so far (like Fallout 1 & 2) seems to work perfect outside of the BG titles.

---

### Post by fisher8484 on 2010-01-20
Anyone have any ideas on how to get the Baldur's Gate games to work on Linux?  I've tried every OS option in Wine's configuration and still no luck.  According to the Wine Ap Database it should work, but I'm unable to copy the DVD Roms as isos I can use (error says that it isn't in iso 9660 format).  Anyone get these games to work?  It's the reason I continue to keep my Windows partition.

---

### Post by beastrace91 on 2010-01-20
Maybe try a different Wine version? Both [Baldur's Gate 1](http://appdb.winehq.org/objectManager.php?sClass=application&iId=157) and [Baldur's Gate 2](http://appdb.winehq.org/objectManager.php?sClass=application&iId=272) are Platinum ranked by many people using various Wine versions - I know personally I found 1.1.31 had some issues with 3D applications.

~Jeff

---

### Post by fisher8484 on 2010-01-22
> **beastrace91 said:**
> Maybe try a different Wine version? Both [Baldur's Gate 1]("http://appdb.winehq.org/objectManager.php?sClass=application&iId=157") and [Baldur's Gate 2]("http://appdb.winehq.org/objectManager.php?sClass=application&iId=272") are Platinum ranked by many people using various Wine versions - I know personally I found 1.1.31 had some issues with 3D applications.

~Jeff

 I have tried the latest Wine version, reinstalled it, and it now seems to work perfect as long as I have it set to Windows 95.  I've imported all my saves from the Windows partition and they work perfect. Game seems to work better than it did on the Windows 7 side.  Chalk up yet another app I no longer need Windows for.   Just one little hitch, however.  I got an annoying non moving mouse cursor (not mine) that just sits there in the middle of the screen.  I can get rid of it by running Wine in a virtual desktop (no fullscreen) or by running in the lowest resolution possible, but there's got to be a way to get rid of it.  I've spent over an hour playing with the settings on Wine and I can't figure it out.

---

### Post by Toffeeapple on 2010-01-22
HI,

I have it running nicely with wine 1.1.36. IN wine config. I have it set to Windows 2000, and under the Graphics tab, 'Allow the window manager to control the windows' and 'Emulate a virtual desktop' set to 1440x900.

Also I have installed the wide-screen mod found here..

[http://www.gibberlings3.net/readmes/readme-widescreen.html](http://www.gibberlings3.net/readmes/readme-widescreen.html)

and possible a few other of the mods found there, I forget, it's been a while. I only post as I do remember getting that pointer thing you mention a while back but it's not happening now, I just had a quick game and all is still fine.

I'm not sure but I seem to remember it having something to do with some setting that can be adjusted with the config. settings application that comes with the game, bgconfig.exe in the programs folder.

Sorry if it's a bit vague, but good luck as it's still a great game : )

---

