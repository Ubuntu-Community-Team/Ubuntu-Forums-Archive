---
title: "Issue with Half-Life 2 and Half-Life 2 Deathmatch - Stuck on Loading screen"
date: 2009-04-17
forum: Wine
---

### Post by Noise... on 2009-04-17
I installed Wine earlier today and then installed Steam, Half-Life 2, and Half-Life 2: Deathmatch. 

Steam works fine, and updated both games without issue. Both games start perfectly, but once they get to the "Loading..." Screen, they get stuck there. I left HL2 for about 30 minutes just to be sure that it wasn't just taking a long time to load.

How can I fix this? According to WineHQ's AppDB, both should run flawlessly.

Edit; I just checked the "About" tab in Wine Configuration, and it shows that it's only version 1.0. How can I update it to the latest release?

---

### Post by NightMKoder on 2009-04-17
Sticky on top [http://ubuntuforums.org/showthread.php?t=871535](http://ubuntuforums.org/showthread.php?t=871535)

---

### Post by Noise... on 2009-04-18
Thanks - I'm updated now. However, I'm still getting stuck at the loading screen. Any ideas?

---

### Post by NightMKoder on 2009-04-18
Make sure the game is in opengl mode and that desktop effects are off.

If neither help, what is your graphics card/driver version, and console output up to freeze?

---

### Post by jacksaff on 2009-04-18
I had problems with the valve-guy video which prevented the game launching. In steam right click on the game. Go to 'properties'. Select 'launch options' and type -novid into the box. Game will now bypass the video at the start.
Also I use the option -dxlevel81 on the source games which seems to work best.

---

### Post by Noise... on 2009-04-18
> **jacksaff said:**
> I had problems with the valve-guy video which prevented the game launching. In steam right click on the game. Go to 'properties'. Select 'launch options' and type -novid into the box. Game will now bypass the video at the start.
Also I use the option -dxlevel81 on the source games which seems to work best.

Thanks - I'll test that now. 

So, in the launch options it should look like this?

```
-novid -dxlevel81
```

---

### Post by Noise... on 2009-04-18
^nope - that didn't work. Skipped the video, but still froze at the loading screen.

Also, my graphics chip is an Intel X3100 with the default Ubuntu 8.04 driver. 

I just read another thread that said something about the X3100 being much more limited in Linux due to the drivers not being very advanced yet. If that's true, I'll just keep Windows for now, I guess.

---

### Post by NightMKoder on 2009-04-18
This is true, Intel drivers (pre-GEM) are really bad for 3D. Thankfully, intel invested some money into linux and redesigned the driver stack. In a couple of months UXA acceleration should be stable and intel 3D should be usable again.

---

### Post by Noise... on 2009-04-18
> **NightMKoder said:**
> This is true, Intel drivers (pre-GEM) are really bad for 3D. Thankfully, intel invested some money into linux and redesigned the driver stack. In a couple of months UXA acceleration should be stable and intel 3D should be usable again.

Great. Hopefully it will be on par with the Windows drivers - Which are quite impressive for an integrated chip. I even had Unreal Tournament 3 running on it - albeit with low settings.

I guess that the drivers lacking in terms of 3D would definitely cause the freezing/crashing

Oh well. Windows for a few more months then. :)

Thanks for the info guys.

---

