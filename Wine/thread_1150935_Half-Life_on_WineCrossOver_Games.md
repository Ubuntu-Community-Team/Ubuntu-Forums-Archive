---
title: "Half-Life on Wine/CrossOver Games"
date: 2009-05-06
forum: Wine
---

### Post by andddlay on 2009-05-06
Hello.  Could somebody please help me with a problem I am having?

I had a .mdf file, which I mounted, and copied 'n' pasted everything on it on my desktop.  Everything with worked fine when setting up Sierra and Half-Life, but then when I go to play the game, it does not open (I did install DirectX through winetricks because it said I had to have it).

On CrossOver Games, it showed me a lot better results than Wine.  I successfully installed the game.  When I open it, the Half-Life logo is all messed up (which isn't a big deal), but then when I go to play the game, it stays on the Loading screen, but I can hear the sound of the game as if it were working normally.  I tried turning off Compiz to see if that worked, but it didn't.

Could somebody please help me?  I am running Jaunty Jackalope if that is needed information...

Thank you!

---

### Post by NightMKoder on 2009-05-06
The game works in wine just fine (and dont install native directx unless you REALLY need to - wine has its own directx), you just need to start it in opengl mode, ie:

hl.exe -opengl

(or just -gl, don't remember right now)

---

### Post by andddlay on 2009-05-06
Thank you so much for the speedy response!  I am somewhat new to this kind of thing.  When I type hl.exe -opengl (and hl.exe -gl) into the terminal, it says:  -bash: hl.exe: command not found

So I then went into my .wine folder and found hl.exe and dragged and dropped that onto my terminal and then did -opengl.  It then asked for the key to the game, which I then entered, but it then popped up a screen saying that I need service pack 3 or higher installed.

---

### Post by NightMKoder on 2009-05-06
> **andddlay said:**
> Thank you so much for the speedy response!  I am somewhat new to this kind of thing.  When I type hl.exe -opengl (and hl.exe -gl) into the terminal, it says:  -bash: hl.exe: command not found

So I then went into my .wine folder and found hl.exe and dragged and dropped that onto my terminal and then did -opengl.  It then asked for the key to the game, which I then entered, but it then popped up a screen saying that I need service pack 3 or higher installed.

That is just confusing.

Open a terminal, and cd to the folder where hl.exe is. Something like

```

cd "~/.wine/drive_c/Program Files/Sierra/Half-Life"

```

Or something like that. You can type pwd and ls to see where you are and what files/folders are in the current location. Once you find hl.exe, (ie it shows up when you do ls), run the following:

```
wine hl.exe -opengl
```

---

### Post by andddlay on 2009-05-06
> **NightMKoder said:**
> That is just confusing.

Open a terminal, and cd to the folder where hl.exe is. Something like

```

cd "~/.wine/drive_c/Program Files/Sierra/Half-Life"

```

Or something like that. You can type pwd and ls to see where you are and what files/folders are in the current location. Once you find hl.exe, (ie it shows up when you do ls), run the following:

```
wine hl.exe -opengl
```

Once doing all of that it pops up a window reading, "Half-Life requires Service Pack 3 or above."  :confused:

---

### Post by NightMKoder on 2009-05-06
Make sure you're using the latest version of wine (1.1.20), and try setting your windows version to 2000.

Also what half-life are you running? Is this steam or the old version?

---

### Post by andddlay on 2009-05-06
> **NightMKoder said:**
> Make sure you're using the latest version of wine (1.1.20), and try setting your windows version to 2000.

Also what half-life are you running? Is this steam or the old version?

I think I"m running the old one.  It is published by Sierra.

I just went to the game's settings and changed it to "run in window," and it is working perfectly. I will fool with the settings a little more, but I am ok with it running in a window.  

Thank you so very much!!!! :D

---

### Post by YokoZar on 2009-05-06
Just run it through steam and put -opengl as one of the launch options (right click the game name).

---

