---
title: "Age of Mythology + Wine = Crash-To-Desktop"
date: 2009-05-09
forum: Wine
---

### Post by mattkenn4545 on 2009-05-09
Here is my problem.

Age Of Mythology - Titans Expansion will crash-to-desktop after playing for ~ 1hr during game-play
-Will stay running all day long if left at menu

-I've only tested during LAN Multi player and happens every time. (assuming we battle long enough)
-Memory Usage is fairly consistent (i.e. doesn't look like it is memory leak issue) usually ~ 100MB
-Several minutes before the crash game objects start 'disappearing' (it the healing well the Norse can get will not render in the game) or the mini map turns black and only the overlays remain (ie the terrain is black but the town centre icons remain)
-Does not matter if I host or other players Windows on Wine.
-Occurs on all computers i've put linux on (AMD64 Desktop with 6800GT 4GB, Pentium M Intel Graphics 1GB, and AMD Athlon XP ATI 9200) on all Ubuntu versions 8.04 to 9.04
-Using the Wine Versions from WINEHQ using the ubuntu repository
-Tried all versions on windows for Wine
-Tried ALSA, OSS, ESD and just about every combo of audio options in wine and the game.
-Other Games work fine and can play for hours on end (Homeworld 2, GuildWars, WarCraft 3, and whatever I might try)
-Last worked in an older version on Wine (can't remember which version) but there was a very serious memory leak (would eventually Bollon to over 2GB memory used for a typical game)
-Searched goggle and this forum many times and haven't found anything helpful
-Installed from CDs and update to latest versions
-Using Cracked EXE for obvious reasons

Please help and hopefully there can be a solution to this.  I don't think I'm the only one who is having this issue.

Thanks in advance

---

### Post by mattkenn4545 on 2009-05-10
Bump :) Anyone?

---

### Post by asdfoo on 2009-05-10
Wine version? backtrace?

---

### Post by mattkenn4545 on 2009-05-10
wine-1.1.20

I'm not sure how to do a backtrace

---

### Post by mattkenn4545 on 2009-05-12
Bump

I sorta fixed it but not really the way I'd like

I downgraded to wine-0.9.53 after several mentions to use that version.

Now the memory leak is back (game crashes unable to allocate memory when process gets to 1.9GB memory used) but the game doesn't have any of the issues I mentioned earlier.

As a side note this version also fixed Age of Empires III crashing during startup and not having to delete the My Games folder on every launch and the mouse no longer disappears in Guild Wars after several hours of play.

Weird

Anyone have any idea how to fix and if there are any patches to get the new version to work like the old one did.

---

### Post by WolfRage on 2009-10-22
I am trying to bring several players of this game together to come up with a best play unified solution so please post back with any updates you have for getting AOM to play.
 
I know it has been awhile sine you were looking into this issue. But I too am now trying to tackle the issue of getting this game to run and run well. SO I will post agian when I have more luck.
 
What I have found to work so far:
1: Copy pidgen.dll from AOM_D1 to C:/windows/system32/
2: Download MFC42.dll (I believe that is the correct name.) and copy that to C:/windows/system32/
3: Install the game.
4: Install MSMXMLenu.msi from AOM_D2.
5: Install the version 1 to version 1.10 patch.
6: Start the game in safe video mode.
 
Alternatives: I tried installing the game using POL (Play On Linux) but this resulted in a problem with MSMXML not being detected.
So the next plan is to install the game normally but apply the patch using POL by importing the game using the POL Plugin.
I am also thinking about installing Directx off the AOM CD before launching the game, but I am not sure if Directx will even install or if it is used in the WINE enviroment.

---

