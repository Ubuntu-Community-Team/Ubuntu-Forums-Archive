---
title: "Working games but no online play"
date: 2009-04-03
forum: Wine
---

### Post by Wilson423 on 2009-04-03
I been messing around with getting different games to work in Wine but there seems to be a problem with getting online for multiplayer games. I started System Monitor on a different desktop and jumped to it when i set the game searching for servers. Not even a bump on network traffic so its just not getting through.

Using:
Wine 1.0.1
Ubuntu 8.10
Game is:
Freelancer and its mod manager.


Oh, and I'm a total Linux noob. I love ubuntu and if i can get the gaming thing straightened out Windows is going bye bye.

Thanks,

---

### Post by Meow27 on 2009-04-04
first off, you may want to try newer version of Wine rather than the old stable.

2nd did you try playing single player yet? you should make sure whether you know sound is working or not.

3rd, you should generate a player ID and cross your fingers, from my experience, multiplayer in Wine for FL is extremely difficult to do :/

---

### Post by Wilson423 on 2009-04-04
Well, I somehow managed to set my self back beyond square one. Now the game crashes/freezes after the splash screen.

I went in to single player once and got impatient during all the video stuff and shut it down before it finished. The sound was working at that point.

I could not get a player ID in original game but got it running BSG - Exodus mod.

FL has a problem with the ingame text (read something of a fix for MS games, but that didnt work for FL). But you can mouse over buttons and get a readable description.

I think I'll try reinstalling the game to see if that fixes it and keep posting what I find here.

Wish me luck, I'm going in!

---

### Post by Meow27 on 2009-04-04
dont reinstall FL, get the latest wine
[http://wine.budgetdedicated.com/archive/index.html](http://wine.budgetdedicated.com/archive/index.html)

question: do you have winemp3.acm in ur system32 folder?

---

### Post by Wilson423 on 2009-04-04
Reinstalling FL didn't help, as you probably know.. =)

Tried to update Wine with Wine 1.1.18 i386 file and received this error message when using GDebi Package Installer:

Error: Dependency is not satisfiable: libasound2

Also, I do not have winemp3.acm in system32 folder.

Thanks for the input.  :D

---

### Post by Meow27 on 2009-04-04
ok, lets make sure single player is playable first.

but even before that, i need to know what version of Ubuntu you are using, and if you downloaded the appropriate Wine backport

you can try using slightly older versions, but i wouldn't go below 1.1.14


back to single player, try playing it, if you have no sound problem, ur in luck, other than that, do the graphics load properly? is the FL user interface readable and usable?

---

### Post by Wilson423 on 2009-04-05
Wine 1.1.18 pretty much broke what i had... lol

Looking for a way to downgrade or revert to an older build (noobness blows :D ).

Ubuntu 
release 8.10 (intrepid) 
kernel linux 2.6.27-11
GNOME 2.24.1

backport? er... see line above about noobness. lol

UPDATE:
i managed to get Wine 1.1.14 installed (likely the wrong way...but it worked.. :D ).
Single player works fine aside from one little sound hickup during intro movie and the mouse is a little sluggish in respect to running in pure windows.
Moving on to backport research.

---

### Post by Meow27 on 2009-04-05
[http://wine.budgetdedicated.com/archive/index.html](http://wine.budgetdedicated.com/archive/index.html)

this has an archive of older Wine versions for different versions of ubuntu, you want the 2nd list which is for ubuntu intrepid (the first list is for jaunty which only has 1 version thus far.)

try Wine 1.1.16 
or this to be more precise
[http://wine.budgetdedicated.com/archive/ubuntu/intrepid/wine_1.1.16~winehq0~ubuntu~8.10-0ubuntu1_i386.deb](http://wine.budgetdedicated.com/archive/ubuntu/intrepid/wine_1.1.16~winehq0~ubuntu~8.10-0ubuntu1_i386.deb)

---

### Post by Wilson423 on 2009-04-05
Ok. Wine 1.1.16 installed and working. FL works in single player but still not even a bump on the network traffic when i try multiplayer.

---

