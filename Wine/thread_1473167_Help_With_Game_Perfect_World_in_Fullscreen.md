---
title: "Help With Game Perfect World in Fullscreen"
date: 2010-05-04
forum: Wine
---

### Post by NT2015 on 2010-05-04
OK, I have the mmo Perfect World installed, everything runs smoothly except one thing. When I run the game in full screen, it runs just fine unless I try to switch to a different window like Pidgin or Firefox. When I do this the entire game will move down and to the right, and I can still interact with it as if it was any other window, but the game no longer responds to my mouse, and its impossible to get it back to full screen without restarting the game. Now my first thought was "ok so I just wont switch windows while im playing" but this problem also occurs when anything steals focus from it, such as if I get a call in skype, the notification will cause the game to do it, any notification's from any other programs as well. So for now im playing in windowed mode, but this is less than desirable. I play WOW and Battlezone II all the time with no problems what so ever.

Also, not a big deal, but if anyone has some ideas, there is a small graphical issue, the male Tideborns  right ear stretches to infinity, as does the untamed males right eyebrow. lol not a big issue for me but I thought ide mention it.

I have tried different windows versions, and emulating a virtual  desktop, aswell as not allowing the window manager to decorate or  control the windows. Nothing has worked thus far. 

Ubuntu 10.04 LTS 64bit
nVidia GeForce 7900GS (Driver Version: 195.36.15)
Wine Version 1.1.42
Game Version: 316

Any thoughts on this?, In WOW I can run the game in "Maximized windowed mode" where the game is "technically" running in windowed mode, but appears to be running in normal fullscreen. I love this feature because it allows wow to interact beautifully with Compiz. Is it possible to "force" such a mode in other games? that would be awesome.

But I really hope to get this solved one way or the other, because this game has pretty unique graphics, but having to run it in a window kinda takes away from that. 

I can submit screen shots or any other info if anybody thinks that it would help.

---

### Post by NT2015 on 2010-05-07
bump

---

### Post by Zireth ZH on 2010-05-08
Ur lucky that u can play perfect world without problems.. just that... i cant even last more than 5 mins playing it.. the whole OS seems to freeze and i gotta reboot manually... Can u tell me how did u installed it? used any tricks or tweaks?

i dun even noe how to minimize the game!!! lol

---

### Post by NT2015 on 2010-05-12
> **Zireth ZH said:**
> Ur lucky that u can play perfect world without problems.. just that... i cant even last more than 5 mins playing it.. the whole OS seems to freeze and i gotta reboot manually... Can u tell me how did u installed it? used any tricks or tweaks?

i dun even noe how to minimize the game!!! lol

I really didn't do anything, I have the file "elementclient.exe" set to run under XP in winecfg. and I installed some files through wine tricks.

Here is a list of everything I installed through winetricks, but keep in mind that I had all this installed prior to installing perfect World. So not all of these may have anything to do with the game at all, hell its possible that none of them have anything to do with the game, im just listing them so you can get a similar config to mine, and maybe it will work. Besides everything im about to list are things that I personally consider to be necessary for most programs and games.

atmlib (atmlib is for adobe apps like Photoshop)
d3dx9
d3dx9_28
d3dx9_36
d3dx10
dinput8
vcrun2003
vcrun2005
vcrun2008
vcrun6
vcrun6sp6
allfonts

Just incase you dont have winetricks installed just paste the following into your terminal

```
wget http://www.kegel.com/wine/winetricks
```then to execute the program run the following command in your terminal

```
sh winetricks
```then its just as simple as put a check mark next to what you want installed and hit ok, depending on what your installing it can take a little while.

Hope this helps

Also now that I think about it, the last time my rig was doing that it was because my video card was over heating. If what I said before doesn't help, then make sure nothing is over heating and definitely run a memory check

---

