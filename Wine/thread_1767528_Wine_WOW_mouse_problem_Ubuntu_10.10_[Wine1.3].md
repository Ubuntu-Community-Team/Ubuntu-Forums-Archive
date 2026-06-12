---
title: "Wine: WOW mouse problem Ubuntu 10.10 [Wine1.3]"
date: 2011-05-25
forum: Wine
---

### Post by ahiung on 2011-05-25
I tried to play WOW using Ubuntu, I followed all the instruction and went well.
Until I went in-game, basically everything looks fine but the only problem is the mouse.

Problem:
[Left Click] function was to choose/Select/targeting, but now is included "move the camera to certain point depends where you click at, not if you click spells, options, and menu"

[Right Click] function was to Select/Target/Stick the camera(if hold), but now the problem is same as above.

Practical problem:
-When I choose a target using [Left click], my camera is following the Centre where I clicked at.
-When I'm running/walking + clicking above or other free area, My monitor will be a "Yo-Yo".
-When I'm running straight using [W], and turn 180 degree using [Hold Right-click], then release it, my player will turn back again where I was facing (similar to when get strike by Rogue's [Distract] skill]). So, I was playing uncomfortably by only using WASD+skills.

The last effort I tried is: playing WOW using Fluxbox, It's the only solution I can find in Wine:WOW Troubleshoots. But, the problem still there.

Please help me, Thanks for Advance.

---

### Post by cwwilson721 on 2011-05-25
The issue is the 'latest' version of wine in the repos:
1.3.20

If you uninstall that, and get 1.3.19, you'll be OK. I'd wait on using the wine repos to update your wine install until this issue is resolved.

---

### Post by ahiung on 2011-05-26
Thanks Wilson, but I don't know how to get to 1.3.19 because I only allowed to download the last one(BETA) 1.3.20, also the version before that 1.2.0, so now I try to download 1.2.0.
if you know the command to download 1.3.19 please tell me. I only know in command there is wine1.2 and 1.3 but no 1.3.19 or something detail.

---

### Post by ahiung on 2011-05-26
omg, I installed 1.2, I just can't accept this version because I experienced this version before, only get 7 FPS(it's like a huge lag). I just want to get to 1.3.19 :(

I dont have any option....
see what i typed in terminal
===============================================
berenditih@oxFalcon:/usr/share$ sudo apt-get install wine1.3.19
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package wine1.3.19
E: Couldn't find any package by regex 'wine1.3.19'
===============================================

Then I only have 1 option left:

===============================================
berenditih@oxFalcon:/usr/share$ sudo apt-get install wine1.3
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  wine1.2
The following NEW packages will be installed:
  wine1.3
0 upgraded, 1 newly installed, 1 to remove and 1 not upgraded.
Need to get 0B/12.2MB of archives.
After this operation, 15.3MB of additional disk space will be used.
Do you want to continue [Y/n]?

---

### Post by cwwilson721 on 2011-05-26
A very quick 
Google Search tells how:
[http://ubuntuforums.org/showthread.php?t=871535](http://ubuntuforums.org/showthread.php?t=871535)

Look in the binary files for the 1.3.19 package for you (32 or 64bit), and the other relevant packages (like wine gecko)

---

### Post by ahiung on 2011-05-26
At last my problem solved, Thanks to cwwilson721
I'll make a summary so those who visit this post will understand

#1 Uninstall your wine1.2 or wine1.3 using 3 method(MUST)

1st Method: Code
> sudo apt-get remove wine
2nd Method: Code again
> whereis wine
after that it will list all location where the wine is
remove one by one using rm code
example:
> rm usr/lib/wine
if it shows "usr/lib/wine(or other address) is not a directory"
use this code > rm -r usr/lib/wine remember to login using ROOT using [sudo su]
3rd Method: Ubuntu Software Center
Open Ubuntu Software Center, click the TAB "Installed Software", type in "wine" and remove it.

Note: all those 3 methods must be done.
If you done that, It's already perfect. You can also remove the wine menu in Applications, but I don't recommend it because you'll have to open your C: manually using [xdg-open ~/.wine/drive_c] and this is not work in my launcher, however It's work when I input it in Terminal under sudo(not root).

#2 Download all packet you need from [http://wine.budgetdedicated.com/archive/binary/](http://wine.budgetdedicated.com/archive/binary/)
amd64 that's mean it's for 64 bit PC
i386 that's mean it's for 32 bit PC
download all that contain 1.3.19 (ttf, deb, dev, and wine1.3_1.3.19)
you don't have to download the gecko one, once you set it up wine will download and Install instantly for you.
after you downloaded all the packets, all you have to do is run it(will be in Ubuntu Software Center) and Install.
1st install the wine1.3_1.3.19
2nd dev
3rd deb
after that you can run your wine using terminal or menu :D

you can also check the wine version after you installed it to make sure, type in terminal: wine --version

note: IF you deleted the menu before and you want to do something about it, here is the code:
Configure wine : winecfg
open drive_C   : xdg-open ~/.wine/drive_c

GOOD LUCK !

---

