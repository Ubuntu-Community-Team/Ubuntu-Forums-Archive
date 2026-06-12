---
title: "Minor wine with panel problem"
date: 2011-07-04
forum: Wine
---

### Post by Gfurst on 2011-07-04
Hey there people. I'm a problem with Wine but it isn't about game running per say.

The thing is when I start a full screen game in different resolution, the game opens ok, start running and change the screen resolution, the problem is that when it changes the panels just won't go away, I mean the up/down menu bar panel whatever from Gnome.

I have to rechange resolution inside the game for them to go away, so as you imagine this is very annoying. And it gets a bit more troublesome with smaller resolutions, it seems the screen gets out scaled and some buttons of the game won't work, I had this problem while playing Splinter Cell 1 and other older games.

I'm currently playing The Sims 3, even after quiting the game the resolution gets back to normal as supposed, but still the panels keep showing. By the way, the game window even has "Always on Top" tag.

---

### Post by bobwyajnr on 2011-07-08
> **Gfurst said:**
> 
The thing is when I start a full screen game in different resolution, the game opens ok, start running and change the screen resolution, the problem is that when it changes the panels just won't go away, I mean the up/down menu bar panel whatever from Gnome.

Basically what is happening their is that your Window manager is using graphics card acceleration... Because the menu bars are being rendered this way they can overlay your OpenGL game.
Fix is to temporarily disable GPU acceleration for your normal desktop:
[LIST=1]
[*]KWin (**KDE**): disable desktop effects for fullscreen applications - enable (default)
[*]Compiz Config Settings Manager (**Gnome**): undirect full screen applications setting - enable (*not* default)
[/LIST]
(Compiz setting is buried in the *General* settings option I think - I'm using a newer version of Compiz than you would be).

Also using Metacity will not use your graphics card to render your normal desktop windows/panels...

> **Gfurst said:**
> 
I have to rechange resolution inside the game for them to go away, so as you imagine this is very annoying. And it gets a bit more troublesome with smaller resolutions, it seems the screen gets out scaled and some buttons of the game won't work, I had this problem while playing Splinter Cell 1 and other older games.

The Wine developers refuse to put in any fudges to correct this behaviour (basically since it is difficult to tell when you would want the resolution to 'return to normal' - without breaking other things!)

There are plenty of advanced guides out there that you can *Bing* -on... They basically involve using xrandr after the main commandline shortcut for the game you are running in Wine. This command is used to reset the display resolution back to the default/ previous setting.

Slightly easier you can run games in a *Virtual Desktop* (this can be set in the **winecfg** GUI - in your *Programs/Wine* menu). Set the size of the desktop to the slightly less than your full desktop resolution. Perhaps not as pretty as running fullscreen - but your main display resolution is left unaffected!

If that's all geeky gobidly-gook I'll put it in simpler language and go through the steps! :popcorn:

Bob

---

### Post by Gfurst on 2011-07-08
> **bobwyajnr said:**
> 
If that's all geeky gobidly-gook I'll put it in simpler language and go through the steps! :popcorn:

Bob
Thanks thats not goolibly talk at all heheh, thanks for the answer though, I though no one would answer my questions in this forum.

> **bobwyajnr said:**
> 
Basically what is happening their is that your  Window manager is using graphics card acceleration... Because the menu  bars are being rendered this way they can overlay your OpenGL game.
Fix is to temporarily disable GPU acceleration for your normal desktop:
[LIST=1]
[*]KWin (**KDE**): disable desktop effects for fullscreen applications - enable (default)
[*]Compiz Config Settings Manager (**Gnome**): undirect full screen applications setting - enable (*not* default)
[/LIST]
(Compiz setting is buried in the *General* settings option I think - I'm using a newer version of Compiz than you would be).

Also using Metacity will not use your graphics card to render your normal desktop windows/panels...

Yeah i forgot about that, I used to always switch from compiz to metacity through the "Compiz fusion icon" a good time ago, i guess I should have this habit back, i should give boost to performance too.

> **bobwyajnr said:**
> 
Slightly easier you can run games in a *Virtual Desktop* (this can be set in the **winecfg** GUI - in your *Programs/Wine*  menu). Set the size of the desktop to the slightly less than your full  desktop resolution. Perhaps not as pretty as running fullscreen - but  your main display resolution is left unaffected!

Yeah I've tried that a lot of times, i set the Vdesktop rosolution to the same size, but the game inside the screen still remain their set size, making it use a small portion of the virtual desktop.
I've always though this to be a weird bug, but never anyone mentioning it.

===========
Also I've read somewhere to disable the window manager in winecfg, I tend not to use this because it used to give me weird results, but maybe can also be a solution.

Anyway, I'm playing Sims 3, I've set the resolution to 1680 and surprisingly it seems to have better performance, and the bars don't get in the way anymore.
So i guess this issue is over for now.

Thanks and see ya.

---

