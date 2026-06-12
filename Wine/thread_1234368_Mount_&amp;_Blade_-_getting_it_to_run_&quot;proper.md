---
title: "Mount &amp; Blade - getting it to run &quot;properly&quot;"
date: 2009-08-07
forum: Wine
---

### Post by del_diablo on 2009-08-07
Mount & Blade, 1.011
Wine 1.25
Amd Turion 70 RM, ATI Radeon 34**
Ubuntu 9.04, Catalyst 9.7

What works:
*The game runs

Modifications:
*A altered dininput.dll(found at the appdb page for 1.011)

Problems
*Mouse cursor does not get alpah(it got a gigantic white box around it)
*Windowed equals mouse leaving the application, known bug thats unfixed for ages
*Running with export WINEFORCEMOUSEWARP=yes; fixes point of view and looking around, but only in combat. It forces the cursor back into the middle of the screen when not in combat(which results in making all buttons on the edge of the screen hard to reach)
*Just running it(fullscreen) results in the known screwd over rotation, with it randomly the "cursors" position or what it is but it can takes ages

So please, help me getting this to run  properly <.<

---

### Post by del_diablo on 2009-08-10
*bump*

---

### Post by cyprys on 2009-11-18
I totally get you because I suffer the same problem. When I move mouse to the left to rotate the perspective of a camera the cursor sooner or later goes out of the screen, changes it's icon to the standard Ubuntu one (instead of the Mount&Blade cursor) and further movement of the mouse doesn't affect the movement of the camera perspective any more. It happens in fullscreen display just like the "fullscreen" wouldn't cover the FULL screen. I didn't even tried to force the usage of the mouse wrapper because then I wouldn't be able to use menus in game.

The thing is wine doesn't allow to dynamically enable/disable mouse wrapper with a key. If it would, pressing the TAB key would switch between the Fight Mode (mouse wrapped on the centre of the screen) and the Menus Mode (mouse moved freely).

BTW. new wine (1.33) makes it worse because the sound goes crappy with repetitive manner and some moments of silence. Also there's pink colour in menus instead of transparency - it worked with wine 1.32.

Oh, and the game works better when it's installed with clean wine and not with Play On Linux.

---

### Post by beastrace91 on 2009-11-18
The mousing issue you describe sounds like this one [here](http://bugs.winehq.org/show_bug.cgi?id=6971). If it is indeed this same issue I detail a fix for it [here](http://ubuntuforums.org/showpost.php?p=7297474&postcount=7) for Killing Floor - but it should work the same regardless of game.

Cheers,
~Jeff

---

### Post by cyprys on 2010-01-02
Yes, I checked that out long time ago when there was dinput.dll for 1.1.30 and back then I was using 1.1.32 - it didn't work. Now I use wine 1.1.35 and the newest dinput.dll is for 1.1.32 and it doesn't work either. I'm not going to downgrade since I had bad experiences with Oblivion usage of pixel shader 2.0 instead of 3.0 - anyways, I wait until wine devs get it right. It has to work with either native or wine library. Third party is not an option.

But you're right - this is the very same issue.

---

### Post by suzenon on 2010-02-17
bump.

did anyone managed to make mouse work in m&b ?

the fix from [here]("http://ubuntuforums.org/showpost.php?p=7297474&postcount=7") is working, but mouse pointer is stuck to middle of the screen and you can't do anything in menus (like managing troop for example) so in fact, id does fix one problem (360 degree looking) but breaks other thing (navigating menus)

when i follow instructions from [here]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=14670") (dling this dinput and export WINEFORCEMOUSEWARP=yes; wine ./mount\&blade.exe) i can view the strategic map fine, but in the battle there's only 180 degree view angle when i move mouse (can't look what's behind me) mice dosen't get stuck on screen borders tho

---

### Post by realac0 on 2010-02-20
my M&B installation work perfectly on Ubuntu 9.10 64 with ATI hd5850.
will try to help:

with playonlinux (i always use it because i am pretty noob on linux and is useful for different versione of wine and auto create wineprefix) try like this:

download wine version 1.1.13
put windows 98 mode on wine config panel
and install the game

then

download the dll file, this is the one i used:

[http://www.webalice.it/aconet/dinput.dll.so](http://www.webalice.it/aconet/dinput.dll.so)

and put into your PlayOnLinux M&B prefix on win32 folder

then go on PlyOnLinux folder and check:
configurations/installed

find the file with the script for start M&B from PlayOnLinux and modify similar this:

```
#!/bin/bash
PATH="/home/realac0/.PlayOnLinux/WineVersions/1.1.13/usr/bin/:$PATH"
export WINEPREFIX="/home/realac0/.PlayOnLinux/wineprefix/Mount & Blade"
export WINEDEBUG="-all"
export WINEFORCEMOUSEWARP="yes"
cd "/home/realac0/.PlayOnLinux/wineprefix/Mount & Blade/drive_c/Programmi/Mount&Blade"
wine "/home/realac0/.PlayOnLinux/wineprefix/Mount & Blade/drive_c/Programmi/Mount&Blade/mount&blade.exe"  $@
```is clear, change the dir for your computer/installation

for me run perfectly, no problems at all and i can install differents mods too.

i have installed the texture HD and other mods, no problems at all

sorry for my english, let me know if work

cya
realac0

---

### Post by revoice on 2010-05-15
> **realac0 said:**
> my M&B installation work perfectly on Ubuntu 9.10 64 with ATI hd5850.
will try to help:

with playonlinux (i always use it because i am pretty noob on linux and is useful for different versione of wine and auto create wineprefix) try like this:

download wine version 1.1.13
put windows 98 mode on wine config panel
and install the game

then

download the dll file, this is the one i used:

[http://www.webalice.it/aconet/dinput.dll.so](http://www.webalice.it/aconet/dinput.dll.so)

and put into your PlayOnLinux M&B prefix on win32 folder

then go on PlyOnLinux folder and check:
configurations/installed

find the file with the script for start M&B from PlayOnLinux and modify similar this:

```
#!/bin/bash
PATH="/home/realac0/.PlayOnLinux/WineVersions/1.1.13/usr/bin/:$PATH"
export WINEPREFIX="/home/realac0/.PlayOnLinux/wineprefix/Mount & Blade"
export WINEDEBUG="-all"
export WINEFORCEMOUSEWARP="yes"
cd "/home/realac0/.PlayOnLinux/wineprefix/Mount & Blade/drive_c/Programmi/Mount&Blade"
wine "/home/realac0/.PlayOnLinux/wineprefix/Mount & Blade/drive_c/Programmi/Mount&Blade/mount&blade.exe"  $@
```is clear, change the dir for your computer/installation

for me run perfectly, no problems at all and i can install differents mods too.

i have installed the texture HD and other mods, no problems at all

sorry for my english, let me know if work

cya
realac0

Still I get only 180 degree camera rotation, and the mouse looks with a white box.
Even with the config you suggested.

any help is thankful

---

