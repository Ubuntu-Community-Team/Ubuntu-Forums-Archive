---
title: "Trying to play Oblivion"
date: 2011-01-27
forum: Wine
---

### Post by sudo_chop on 2011-01-27
I have never used wine before, I installed it just to try playing Oblivion on my laptop. I installed wine and the game with no problems, the game is all patched up and everything.

When I start the game, and finally get to the main menu after not being able to esc out of the intro videos, I click new game and then the game freezes and then finally I get a wine error: 

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=182072&stc=1&d=1296134098[/IMG]

I loaded up some savegames and tried it that way too, same thing happens.

Hoping someone can give me a hand figuring this out.

I didn't want to list out a bunch of specs and them be irrelevant, so please let me know if any more information is required, and you'll probably have to tell me how to get it if its software related, it's been a while since I have used linux. I can at least tell you its Oblivion GOTY v1.2.0416 and my wine is v1.2.2. I actually can't figure out how to get my ubuntu version, when I go to system->about, it tells me I have 11.04, which can't be right...

Thanks.

---

### Post by ronnielsen1 on 2011-01-27
Follow the how to at the bottom of the page in the following link and see if that helps

[http://appdb.winehq.org/objectManager.php?sClass=version&iId=7506](http://appdb.winehq.org/objectManager.php?sClass=version&iId=7506)

> HOWTO  [SIZE=2]**If  you're using WINE version 1.3.x or above,  you can launch the game without any native DirectX DLLs, but bug #20074  is still actual for now, therefore installing DirectX9 or just placing  d3dx9_27.dll to your drive_c/windows/system32 directory would be  preferable.**[/SIZE]     

   _Since stable release 1.2.1 Oblivion Game of the year works stable on many popular distros._
   Although, if you're running older WINE or have some regression issues, you can use some tips listed below.
   Prior running the game,you will need to obtain **d3dx9_27.dll**. You can obtain it using [winetricks]("http://wiki.winehq.org/winetricks")


---

### Post by sudo_chop on 2011-01-27
Thanks, but the dx9 thing didn't make a difference.

---

### Post by sudo_chop on 2011-01-28
bump

---

### Post by DoktorSeven on 2011-01-29
Oblivion works well enough here with latest Wine on Ubuntu 10.10 -- what graphics card are you using, and if you're using AMD/ATi or NVidia, are you using the binary drivers or open-source ones (installed drivers via the Additional Drivers tool)?

---

### Post by sudo_chop on 2011-01-30
I am using the proprietary nvidia driver with the 9600M GS in my laptop. 

Do you have wine 1.2.2 or 1.3?

---

### Post by DoktorSeven on 2011-01-30
Wine 1.3.12

With the proprietary nvidia driver, you shouldn't have a problem, though you might want to try updating to Wine 1.3 -- I seem to remember being able to run Oblivion in 1.2 as well though.

It's also possible that something in your Wine prefix is conflicting -- try a fresh Wine prefix as a test -- something like:
(change to Oblivion directory from a terminal)
```
mkdir ~/.wineoblivion/
WINEPREFIX=~/.wineoblivion/ wine Oblivion.exe

```

If it runs fine, you might consider just running it that way -- I've had issues like this before where I try to "fix" one program to run in Wine and end up messing up others.

---

