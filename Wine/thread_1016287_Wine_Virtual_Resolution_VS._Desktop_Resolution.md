---
title: "Wine Virtual Resolution VS. Desktop Resolution"
date: 2008-12-19
forum: Wine
---

### Post by Pat L.I. on 2008-12-19
Hello, 

I am currently running wine-0.9.15 (needed to play Fallout 1) on my EEPC. I have winecfg set to emulate a virtual desktop at 640 x 480 in order for the game to run properly. Not setting this causes the game to crash (and X) and log me out of ubuntu.

This setting makes my entire ubuntu desktop resolution change to 640 x 480. 

therefore, while playing the game, if I pause the game, and change desktops or applications, perhaps to browse the internet or use some other application. My resolution is stuck at 640 x 480.

is there any way for me to use the 640 x 480 resolution ONLY for the game window (application). And when I switch desktops or applications my resolution would be that of my normal ubuntu desktop settings?

---

### Post by cogadh on 2008-12-19
The virtual desktop setting should not behave like that at all. If that is set correctly, it should be running the game in a 640X480 window on your normal desktop resolution. Are you certain you have set it correctly?

---

### Post by Pat L.I. on 2008-12-19
yeah, I have the emulate a virtual desktop box checkmarked and set to 640 x 480.

when running winecfg the window is opened in the appropriate size. 
however when running the game it first opens in a window, then jumps to full screen and changes my entire desktop resolution.

---

### Post by cogadh on 2008-12-19
That's really odd. How are you running the game (App menu shortcut, terminal command)?

---

### Post by Pat L.I. on 2008-12-20
cogadh thank you for your replies,

The problem happens no matter how I run the game. I use the following methods

i have created a script called runfallout which does the following
```

cd ~/Games/Fallout
WINEPREFIX=~/.wine-fallout /home/patrick/wine/usr/bin/wine "/home/patrick/Games/Fallout/Falloutw.exe"
```

then I run the script using
```
 padsp runfallout 
```

the padsp allows me to have sound.
I have created a launcher that will run the script as above and can also launch the game that way.

perhaps its an issue with the game itself? would the game be able to control the resolution somehow?

---

### Post by YokoZar on 2008-12-21
For starters you could try using Wine 1.0 - 0.9.15 is way way way way out of date by about 35 releases or so.  There was a considerable rewrite of the window manager done in that time that likely fixed your problem.

---

### Post by Pat L.I. on 2008-12-22
I am using 0.9.15 because this allows the game to play properly on my eeepc. apparently there is a problem that was introduced after 0.9.15 that causes the mouse to move sluggishly and choppy making the game close to unplayable.

---

