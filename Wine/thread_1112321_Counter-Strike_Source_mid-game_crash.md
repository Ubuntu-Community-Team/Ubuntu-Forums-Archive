---
title: "Counter-Strike Source mid-game crash"
date: 2009-03-31
forum: Wine
---

### Post by creative blank on 2009-03-31
Once I realized that WINE was far out-of-date (default Ubuntu installer), I went through all the necessary steps to update it, and decided to reinstall Counter-Strike Source on my computer.  After browsing the forums (something I've been doing constantly since I installed Ubuntu two days ago - this is my first post ;) ), I have tried running CSS with the "metacity --replace" command in order to hide the gnome panels at boot.  Once I get in a game, it only takes about 10 minutes or so before the game completely crashes and boots me to the desktop with absolutely no error message.  After this occurs, I use the "compiz --replace" command, and reboot X in order to get everything back to normal.

...That's if I'm lucky.  I've tried this process three or four times, and once it even had to put me in low graphics mode until i ran nvidia-xconfig...  seems that something went wrong with my driver configuration!  A few more details regarding my computer set-up:

XFX nForce 750a SLI motherboard (still need to figure out the SLI part :-k )
NVIDIA GeForce 6800 PCI-E video card
2GB DDR2 RAM
Athlon 64 2.1GHz processor

CSS setting are in the medium-to-low range, with trilinear filtering and no anti-aliasing.  Recommended specs are all in the high range, with anisopteric 4x filtering and 2x AA.  Using the same settings, Team Fortress 2 runs close to completely fine, with only occasional stutters.  Is there something I'm missing here?  How would I go about getting an error log for this, if it even exists?

---

### Post by asdfoo on 2009-04-01
> **creative blank said:**
> Once I realized that WINE was far out-of-date (default Ubuntu installer), I went through all the necessary steps to update it, and decided to reinstall Counter-Strike Source on my computer.  After browsing the forums (something I've been doing constantly since I installed Ubuntu two days ago - this is my first post ;) ), I have tried running CSS with the "metacity --replace" command in order to hide the gnome panels at boot.  Once I get in a game, it only takes about 10 minutes or so before the game completely crashes and boots me to the desktop with absolutely no error message.  After this occurs, I use the "compiz --replace" command, and reboot X in order to get everything back to normal.

...That's if I'm lucky.  I've tried this process three or four times, and once it even had to put me in low graphics mode until i ran nvidia-xconfig...  seems that something went wrong with my driver configuration!  A few more details regarding my computer set-up:

XFX nForce 750a SLI motherboard (still need to figure out the SLI part :-k )
NVIDIA GeForce 6800 PCI-E video card
2GB DDR2 RAM
Athlon 64 2.1GHz processor

CSS setting are in the medium-to-low range, with trilinear filtering and no anti-aliasing.  Recommended specs are all in the high range, with anisopteric 4x filtering and 2x AA.  Using the same settings, Team Fortress 2 runs close to completely fine, with only occasional stutters.  Is there something I'm missing here?  How would I go about getting an error log for this, if it even exists?

I had this problem but after upgrading to 180.44 and compiling the latest Wine from git, it seems stable.

---

### Post by creative blank on 2009-04-01
I have tried to install 180.44 several times today, and have had nothing but bad results.  SLI suddenly works but GNOME only takes up a quarter of the screen, xorg.conf has 4 X screens configured with two monitors (I only have one), and freezing and crashing seemed to be around every corner in the boot-up process.  Manually editing xorg.conf seemed to either not help or crash the process entirely.  Currently I'm on my third reinstall of the day and giving up after being too frustrated to continue :-|

obviously I am a complete newbie with this.

---

