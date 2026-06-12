---
title: "HowTo:  Two Worlds"
date: 2009-04-04
forum: Wine
---

### Post by sir_cheats_a_lot on 2009-04-04
after a long wait some has finally figured it out(no not me) I do not take credit for this just making it known that it is possible to do. this was quite a bit of downloading to do on a dialup connection. i realize these steps were done under the polish version 1.4, but they do work just as well under US version 1.7, so here we go:
I found this info in a recently submitted test result at wineHQ.org. I've just modified out the original 3rd step (Direct X) as its not needed for newer versions of wine.

[http://appdb.winehq.org/objectManage...sion&iId=16103](http://appdb.winehq.org/objectManage...sion&iId=16103)

You'll need the "winetricks" script.  To get the game working do the following steps:
1. install game
2. download X3DAudio1_1.dll and extract it to .wine/drive_c/windows/system32 folder (this can be found quite easily on google)
3. winetricks wmp9 and wmp10 (wmp9 alone will get it working but i assume there was a good reason for getting wmp10 as well *shrugs*)

the only problem is an occasional graphical glitch.(picture inverts for a second and gots back to normal, etc.) nothing game stopping that i've seen **_yet_**. but online play seems to be working as well. not sure how well the movies are working if at all, i do know the intro movies aren't. may need to add winetricks allcodecs.

again.. its not my work so please don't credit me with it. enjoy ):P

---

### Post by TwistedGhost on 2009-09-09
so every time i try to open two worlds i get a error message saying "Failed to change to directory '/home/twistedghost/.wine/dosdevices/c:/windows/temp/nsp1ea1.tmp' (No such file or directory)"

---

### Post by sir_cheats_a_lot on 2009-09-09
> **TwistedGhost said:**
> so every time i try to open two worlds i get a error message saying "Failed to change to directory '/home/twistedghost/.wine/dosdevices/c:/windows/temp/nsp1ea1.tmp' (No such file or directory)"

very odd.  there shouldn't be any changing of the directories going on, let alone any errors.  Does it crash out, even start, or does it let you continue on playing? 
  i know one WINE update, i think two versions ago broke it, but was fixed again with the one before this last one.   i'd suggest reinstalling Two Worlds, if that doesn't help, then update WINE.  i have yet to test this last WINE update, will take a look, and let you know.

*update*
Alright, i've tested it and it works with the current WINE version...that is, so long as i have nothing else open. otherwise it seems to freeze the computer.  I have no idea what nsplea1.tmp reffers to, only result from  google, comes up with this thread, which is even more confusing.:confused:
 I'm assuming you have 3d rendering enabled on your graphics card.  if not then you need to get the driver for it.  the ones that come with from the Ubuntu repository don't seem work properly, so you might have to go to the manufacturer's website and download and install them.   and DO read the instructions carefully. you'll of course will have to blacklist the open source driver, or it'll repeatedly try loading it instead of the proprietary one, if you are using a nvidia card.

---

