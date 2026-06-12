---
title: "Problems running SWAT4 &amp; NFSMW"
date: 2011-05-18
forum: Wine
---

### Post by TurtleKing on 2011-05-18
SWAT 4 does not work (it seems to crash after hitting play) and in the terminal it gives the following output:
 	Code:
 	fixme:mountmgr:harddisk_ioctl unsupported ioctl 2d4800 
NFSMW runs in full-screen thanks to that recommendation about  running metacity, however, the intro plays but none of the mouse button  respond (or keyboard if you could use that to skip the intro). I have to  use my shortcut key to close it, and then reset the resolution back to  normal. Any suggestions for a possible fix?

---

### Post by bobwyajnr on 2011-05-18
> **TurtleKing said:**
> SWAT 4 does not work (it seems to crash after hitting play) and in the terminal it gives the following output:
 	Code:
 	fixme:mountmgr:harddisk_ioctl unsupported ioctl 2d4800 


Hi [B]TurtleKing
[/B]
WINE cannot circumvent some copy protection schemes:
[WINE Wiki Copy Protection]("http://wiki.winehq.org/CopyProtection")

SWAT 4 uses Securom 5.x.

That could be the cause of your error. I had to use a no-CD/DVD patch on mine to get it to launch...

Welcome to sad state of WINE/ Windows gaming. :mad:

Sadly this issue (in general) is going to **block** WINE ever supporting more than a handful of Windows games. For example the online DRM verifyer **PunkBuster** service randomly makes Windows API calls in the background - failing if it doesn't get an expected response. This is nearly impossible to circumvent in WINE. [There's actually an online petition to EvenBalance (the evil DRM developers) to make **PunkBuster** cross-platform...]("http://www.petitionspot.com/petitions/PunkBusterforWINE") I even signed up with FriendFace(TM) so I could sign it (I'm on the *500* page)!

Bob

---

### Post by bobwyajnr on 2011-05-18
> **ms2011 said:**
> Also having this problem with punkbuster on battlefield. Any way of minimizing its sensitivity online?



[-X Don't thread hi-jack!! (I was merely giving background to the DRM problems Linux users experience when running Windows using WINE.)

As for your problem the reports on getting Punkbuster working (with certain versions of WINE, patches, etc.) - these are akine to Astrology and Witchcraft. WINE+BF2 only fully works for single-player mode.

You can only get extended online multiplayer sessions with the (2??) BF2 Non-Punkbuster Linux-based BF2 servers.

There are PunkBuster hacks, out there in the wild, for BF2... Bear in mind these maybe outdated and not work with the latest Punkbuster versions and/or only work on Windows. You risk getting your IP/game serial bricked if do try to play online with a hacked Punkbuster service... Also you won't be able to get any support from the WINE Developers with this problem...

Bob

---

### Post by TurtleKing on 2011-05-18
Update:
SWAT: I still have not tweaked or researched on a fix (feels like time wasted).

NFSMW: I switched back to the stable version of wine (1.2.2) and it is now running well. However, I can only get the game to launch properly (working mouse + keyboard) by going into the folder through terminal and running the speed.exe file with wine. I tried using the wineprefix suggestion (giving nfsmw its own wine files) but the program would crash after changing my resolution. So I then moved the NFSMW installed files back to .wine and it is working. I decided to make a shortcut, so I wouldn't have to keep moving into the folder where speed.exe is located but none of the different shortcuts respond well. Usually, the result was that most of the shortcuts would crash after changing my resolution and reading CD Tray briefly. Here is a list of what I tried so far:
1. script in home folder
2. application in desktop (application to run in terminal & without it)
3. application in application/games (application to run in terminal & without it)
4. (threw a dollar at the monitor)

Shortcut Command that actually works in terminal without crashing:
```
cd '/home/replaced/.wine/drive_c/Program Files/EA GAMES/Need for Speed Most Wanted/' ; wine speed.exe
```Any suggestions?

---

### Post by bobwyajnr on 2011-05-19
> **TurtleKing said:**
> 
...

Shortcut Command that actually works in terminal without crashing:
```
cd '/home/replaced/.wine/drive_c/Program Files/EA GAMES/Need for Speed Most Wanted/' ; wine speed.exe
```Any suggestions?

Arrrrrrrrrrrrrggg!! :lolflag:

It is not obvious that you need to post what shortcuts you tried that didn't work! ](*,)

BTW (I guess you didn't get around to reading the WINE FAQ yet?) You **CAN** move and copy whole WINEPREFIXs around. You **CANNOT** just move an installed program over into a **NEW** WINEPREFIX when you feel like it - sorry! :popcorn:

Bob

---

### Post by TurtleKing on 2011-05-21
> **bobwyajnr said:**
> Arrrrrrrrrrrrrggg!! :lolflag:

It is not obvious that you need to post what shortcuts you tried that didn't work! ](*,)

BTW (I guess you didn't get around to reading the WINE FAQ yet?) You **CAN** move and copy whole WINEPREFIXs around. You **CANNOT** just move an installed program over into a **NEW** WINEPREFIX when you feel like it - sorry! :popcorn:

Bob
Yeah I read the main points on the WINE FAQ, but I guess I missed that one. By the way, what do you mean by, "you can move whole WINEPREFIX"? I was following the instructions on creating a WINEPREFIX from a google search, but the terminal asked me to install the program (and according to wine this is not necessary any more in latest versions). Which will explain why I tried moving the wine files over to NFSMW folder.

---

### Post by bobwyajnr on 2011-05-21
> **TurtleKing said:**
> Yeah I read the main points on the WINE FAQ, but I guess I missed that one. By the way, what do you mean by, "you can move whole WINEPREFIX"? I was following the instructions on creating a WINEPREFIX from a google search, but the terminal asked me to install the program (and according to wine this is not necessary any more in latest versions). Which will explain why I tried moving the wine files over to NFSMW folder.

Sorry I mentioned WINEPREFIX's now!! :popcorn:

I find them useful but it's probably worth reading the Wine user guide carefully first and doing some expermentation (with a program you know that works OK in Wine).

When using prefixes you do either copy/move the whole WINEPREFIX root folder and uninstall applications you don't want using:
```
wine uninstaller
```
Or you can install the application(s) again in a fresh WINEPREFIX folder. 

Basically if you just move the application (e.g. NFSMW) over to a fresh WINEPREFIX you end up with a broken virtual Windows registry for that WINEPREFIX. Have a poke in your **~/.wine** folder (you can do this in Nautilus if you enable hidden files - in the options/preferences menu) and you'll see what I mean. The **.reg** files are registry files. _Every_ WINEPREFIX has **unique** registry files that are created when you run **winecfg** or created automatically when you launch your first Windows application (with that WINEPREFIX specified in your Environment).

Seriously don't get sidetracked/bogged down trying to get familiar with WINEPREFIX's. It is an advanced topic and not necessarily for the new user! You'll be ready to tackle it soon enough! It's always best to gradually pickup how these things work over a period of time! Don't walk before you can run :D

Bob

---

