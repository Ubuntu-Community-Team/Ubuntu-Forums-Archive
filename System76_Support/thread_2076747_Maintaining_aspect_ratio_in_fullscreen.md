---
title: "Maintaining aspect ratio in fullscreen"
date: 2012-10-26
forum: System76 Support
---

### Post by ShadowMage on 2012-10-26
Hi,

I have a System76 Wild Dog Performance with an NVidia GeForce GTX 560 Ti. I'm trying to figure out how I can make fullscreen apps (games) maintain proper aspect ratio. I'm using a monitor with 1920x1080 resolution (16:9), and some games appear stretched because they are for example 1024x768 (4:3). What I would like is to have black bars on the sides of the game so that the aspect ratio is maintained.

I'm using Ubuntu 12.04 64-bit. I tried looking in NVIDIA X Server Settings but can't find anything? If anyone can help, it would be greatly appreciated.

---

### Post by bakelitedoorbell on 2012-10-31
Which game?
Are you running a windows game in wine?

---

### Post by ShadowMage on 2012-11-01
Hi, thanks for the reply! Yeah, in this case it is a Windows game in Wine. I imagine it would do the same thing either way, but haven't been able to test that so I'm not sure. Also, I don't know if I'm asking this in the right forum, so mods please feel free to move the thread if not. I'm just hoping I can get this figured out. Any ideas?

---

### Post by isantop on 2012-11-02
> **ShadowMage said:**
> Hi, thanks for the reply! Yeah, in this case it is a Windows game in Wine. I imagine it would do the same thing either way, but haven't been able to test that so I'm not sure. Also, I don't know if I'm asking this in the right forum, so mods please feel free to move the thread if not. I'm just hoping I can get this figured out. Any ideas?

I would recommend changing the resolution to a widescreen resolution. That would prevent stretching and allow you to use the whole screen without issues.

---

### Post by ShadowMage on 2012-11-02
Hi, thanks for replying! I hate to sound picky, but here's why I need the black bars:

[LIST]
[*]The main game I'm trying to get to maintain aspect ratio is Warcraft III.
[*]If I change the in-game resolution to anything that isn't 4:3, the game is actually still stretched because it seems they never truly added widescreen support.
[*]If I change my desktop resolution using "xrandr -s 1920x1080" after launching the game, the game goes crazy.
[*]Some games do not have widescreen resolutions at all - for example, Diablo II. But the thing is, in Diablo II it's fine because I can just play in a window. I can't play Warcraft III in a window because (well I "can", but) the camera is moved around by moving the mouse to the edge of the screen, so it's really unplayable in a window (because the cursor is not trapped inside).
[/LIST]
On other computers with widescreen display, black bars has always been how I solve this issue because, with black bars, the aspect ratio is maintained and the cursor is trapped inside (can't mouse over the black bars, which is good).

I know it's probably more of an Nvidia/drivers/linux question than a System76 one, so again apologies if this is the wrong forum to ask, but does anyone know if there's any way to get the black bars on this system?

Desktop Model: Wild Dog Performance
Operating System: Ubuntu 12.04 64-bit
Graphics card: GeForce GTX 560 Ti
NVIDIA Driver Version: 304.43
Native Resolution: 1920x1080

---

### Post by isantop on 2012-11-05
> **ShadowMage said:**
> Hi, thanks for replying! I hate to sound picky, but here's why I need the black bars:

[LIST]
[*]The main game I'm trying to get to maintain aspect ratio is Warcraft III.
[*]If I change the in-game resolution to anything that isn't 4:3, the game is actually still stretched because it seems they never truly added widescreen support.
[*]If I change my desktop resolution using "xrandr -s 1920x1080" after launching the game, the game goes crazy.
[*]Some games do not have widescreen resolutions at all - for example, Diablo II. But the thing is, in Diablo II it's fine because I can just play in a window. I can't play Warcraft III in a window because (well I "can", but) the camera is moved around by moving the mouse to the edge of the screen, so it's really unplayable in a window (because the cursor is not trapped inside).
[/LIST]
On other computers with widescreen display, black bars has always been how I solve this issue because, with black bars, the aspect ratio is maintained and the cursor is trapped inside (can't mouse over the black bars, which is good).

I know it's probably more of an Nvidia/drivers/linux question than a System76 one, so again apologies if this is the wrong forum to ask, but does anyone know if there's any way to get the black bars on this system?

Desktop Model: Wild Dog Performance
Operating System: Ubuntu 12.04 64-bit
Graphics card: GeForce GTX 560 Ti
NVIDIA Driver Version: 304.43
Native Resolution: 1920x1080

AFAIK, there isn't a way to add letterboxing to the screen when the resolution is wrong. The system is programmed to handle mismatched resolutions one specific way, and you can't change that.

---

### Post by ShadowMage on 2012-11-06
Hi guys,

After lots and lots of digging, I think I've found a solution! I will explain it below, but let me start by mentioning a couple of points that made this problem what I consider a somewhat unique problem to solve. Readers can feel free to skip ahead if it does not interest them but I would like to include this information at least for my own reference as it will help me solve these types of resolution mismatch problems again in the future.

[LIST]
[*]Warcraft III allows you to select widescreen resolutions, but they appear stretched even if the selected resolution matches your monitor's native resolution. The game was designed to be 4:3 and only looks good in 4:3 (unless you don't care about stretching)
[*]I'm using NVIDIA Driver Version 304.43. The results of my digging have lead me to believe that certain older versions did allow you to automatically letterbox different resolutions by setting the scaling to "aspect-scaled" or something similar. However, this automatic scaling feature appears to no longer be there in the newer versions, so yeah: it looks like this feature has been removed from the driver, sadly.
[*]However, the scaling feature seems to have been taken out due to a replacement feature that deals with "ViewPortIn" and "ViewPortOut". While this does seem to allow for more control, it is not automatic: you need to specify the input and output resolutions instead of just saying "aspect-scaled". Also, we're kind of forcing it to just "do it now": it doesn't care about fullscreen or not, or what the resolutions are, it just faithfully applies the specified mapping.
[*]This "ViewPortIn/ViewPortOut" capability is also currently not exposed in the GUI for NVIDIA X Server Settings. Maybe they plan to include it in the future? But I've looked through every option in my version of the GUI and I don't see it. However, I found the command-line capability in the [README]("http://us.download.nvidia.com/XFree86/Linux-x86_64/304.43/README/") of the driver, in [Chapter 13]("http://us.download.nvidia.com/XFree86/Linux-x86_64/304.43/README/configtwinview.html").
[*]An additional obstacle to deal with was the fact that Warcraft III seems to cancel out the ViewPortIn/ViewPortOut when it changes my desktop resolution on launch, so I had to launch the game first and then enter the command. Since I need to wait for Warcraft III to "do its thing" before I can run the command and get the desired result, it's not easily automated but that's ok, this is good enough for me.
[/LIST]
Alright, with that all out of the way now, let's get to the solution, shall we?

==========================

_**SOLUTION:**_

NOTE: THIS SOLUTION WORKS FOR ME BUT YOUR MILEAGE MAY VARY! ALSO, PLEASE NOTE THAT IF YOU'RE NOT USING NVIDIA DRIVERS, YOU WILL PROBABLY FIND THESE INSTRUCTIONS PRETTY USELESS. THE SOLUTION BEING USED IS TO SEND COMMANDS DIRECTLY TO THE NVIDIA DRIVER. PLEASE ALSO REMEMBER THAT WINE IS BEING USED AS WELL. IT IS POSSIBLE THAT NOT  EVERYTHING WILL DISPLAY PERFECTLY BUT ON MY SYSTEM THIS  SOLUTION IS GOOD ENOUGH FOR ME.

[B]Step 0:
[/B]First, we need to make sure Warcraft III's resolution is set to 4:3. To do this, you can go to Options -> Video in Warcraft III and change the resolution. I am using 1024x768 and will assume this Warcraft III resolution in the following steps. Also, my monitor's native resolution is 1920x1080 and will assume this monitor resolution in the following steps.

[B]Step 1:
[/B]Launch Warcraft III (using Wine) and wait for it to finish resizing your desktop.

[B]Step 2:
[/B]Open a terminal and enter the following command:
```
nvidia-settings --assign CurrentMetaMode="DFP-0: 1920x1080 { ViewPortIn=1024x768, ViewPortOut=1440x1080+240+0 }"
```_What's going on here?_
1920x1080: this is the native resolution of my monitor.
ViewPortIn: 1024x768 is the resolution of the game.
ViewPortOut: 1440x1080 is the highest 4:3 resolution that fits on my monitor. Offset (X, Y)=(240, 0) centers this resolution on my monitor.
[B]
Step 3:
[/B]Enjoy playing Warcraft III in 4:3 (YAY!)

[B]Step 4:
[/B]When you're done, exit the game and notice you will still have the black bars. To get rid of them, enter the following command:
```
nvidia-settings --assign CurrentMetaMode="DFP-0: nvidia-auto-select"
```

---

