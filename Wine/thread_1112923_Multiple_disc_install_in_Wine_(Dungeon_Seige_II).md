---
title: "Multiple disc install in Wine (Dungeon Seige II)"
date: 2009-04-01
forum: Wine
---

### Post by coffeeaddict22 on 2009-04-01
I didn't google a straightforward answer when I looked for this today, so here's my $0.02.

Multidisc install is possible in wine; although I suspect there's an easier way this is how I managed it.  I'm using wine 1.0.1 on Ubuntu 8.10 .  My job today was to install Dungeon Siege II (the kids found it, and it's making them boot back into another OS...).
winetricks was a prerequisite before the installation(to add in mfc42.dll); if you don't have it, the installer complains it can't find PID.dll.

Wine has reasonable instructions on getting a second disc in, but they aren't complete.  Start the installer from the command line- usually something along the lines of 

```
wine /media/cdrom0/Setup.Exe
```
and you should be away.  Don't switch into the CD folder ( e.g. cd /media/cdrom/) to do the Setup, or when you remove the first disc the installation will fold.
At the end of the first disc, find a new terminal, and enter
```
wine eject
```
Put in your second disc, and then (the ugly hack) open the winecfg utility through the Applications/Wine/Configure Wine menu, find the 'drives' page, and autosearch for drives.  Once the CD ROM is recognised, hit OK or APPLY, and you're away.  Remounting in a Linux terminal didn't seem to help me; however, when it's remounted in the winecfg menu the "continue" button in the installer worked fine, and game is now installed and working fine.  With any subsequent discs, just do it all again.
I may well be wrong, but I couldn't find a command line alternative to the winecfg remount, or a GUI alternative to the eject solution.

Happy hunting!

---

### Post by Jarkycat on 2009-05-28
Thanks for the tip on getting the multi-disc installation going!  I was able to install it on Ubuntu 8.04 with Wine 1.0 following the above advice.

---

### Post by dyerbods on 2009-07-10
I've just attempted installing DS II under Ubuntu 9.04, Wine 1.1.19 (after using winetricks to install mfc42). The installer starts and gets to the screen with the installation options (express, normal, register, ...) but I cannot select any of them; though I can close the installer in the normal way. Any ideas on how to proceed?

---

### Post by delabeaux on 2009-11-04
Thank you.  This worked for Visual Link Spanish, Level I (2 disks) and Level II (2 disks)! 

Thanks again! :D

---

