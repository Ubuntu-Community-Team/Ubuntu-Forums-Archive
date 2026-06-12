---
title: "Strange camera problems with 9.04, WoW, and Wine + Touchpad"
date: 2009-07-13
forum: Wine
---

### Post by artemisgallow on 2009-07-13
Alright, I'm having an incredibly surreal problem, and I've hit the limits of my ability to find out what is causing it.

I've been running Ubuntu on both my machines (one Desktop, one Laptop) since the release of 8.04. Not yet had a problem that hadn't been asked and fixed by the time I found it. Finally, I find one.

Running WoW on Wine on 8.04 worked beautifully. 8.10 also ran beautifully, though Pulse Audio caused me some grief and required some dodgyness to make sound work correctly in game. Those were both clean installs, not upgrades from another version.

With 9.04 I decided to try to see how well the upgrade would work. I went ahead and let the system update from 8.10 to 9.04, and aside from a few issues here and there, it was all good.

Then yesterday I decided to log back into WoW. It had been a while since I'd been on the laptop for gaming, but I was at a friends house and they wanted me to play, so I fired it up, still proud of how I could play my windows  game on my LINUX LAPTOP WOO!

Except it didn't work right. Sound was dodgy again, and more importantly, mouse look was totally fragged. I spent a while pushing and prodding and nothing worked, so I decided today to just totally wipe the machine and reinstall fresh.

Everything nice and shiny and new, I fired up WoW again. Unfortunately, I'm still having the problem. Whenever you click to move the camera (nay, even just clicking and NOT moving the cursor) causes the camera to jump suddenly to a new position. Usually straight up in the sky. Its -only- when using the touchpad however. I plugged in a USB mouse, and everything works beautifully, exactly as it did in 8.04/8.10.

More experimenting, and it became even stranger, as I realised it was only fullscreen mode, or maximised windows and certain resolutions that were broken. Some more so than others.

See my tests below.
Key:
Works Perfectly - As Expected, camera is quick, transitions around the character smoothly.
Sort of Works - Camera freezes,and then jumps to a new location. I can sort of "guide" it into position, as it moves approximate to the way it should have, if the transition were there.
Completely Useless - Camera freezes, then jumps to a new location. Pointing straight up. Subsequent moves result in rotation around the vertical axis. Continues to point to the sky, just at a random number of degrees rotated.

Non Native Resolutions, Windowed, Non Maximised Windows
800x600 - Completely Useless
960x600(wide) - Completely Useless
1024x768 - Works Perfectly
1360x768(wide) - Works Perfectly
1280x960 - Sort of works
1440x900 - Completely Useless
1280x1024 - Sort of Worls
1400x1050 - Sort of Works
1600x1024(wide) - Works Perfectly
1680x1050(Wide) - Sort of Works
1600x1200 - Works Perfectly
1920x1080 (Wide) - Sort of Works

All maximised windows instantly move to "completely useless"

1920x1200 Native Resolution Tests
Windowed, Non Maximised  - Works Perfectly
Windowed, Maximised - Completely Useless
Full Screen - Completely Useless

Machine Specs:
Dell Inspiron 9300 running 9.04 Jaunty
1GB Ram
Intel Pentium M Processor 2.00GHz
NVidia GeForce Go 6800

I was using wine-1.1.25. I then downgraded back to 1.0.1 from the Ubuntu Repos, removed my .wine folder, recreated it and registry, etc , moved WoW back into this new drive_c and problem remained.

I'm using the native NVidia drivers, most recent version 180. All Window effects are turned off. Using Gnome 2.26.1. My xorg.conf is nearly totally empty, apparently thats to do with the changes to 9.04, so I don't know if the Touchpad isn't being "loaded" correctly or not, but it does work perfectly well for everything else.

My config.wtf is set to use:
SET gxApi "OpenGL"
Removing this and using D3D doesn't actually cause any difference, aside from some rendering "noise" when the window initially loads.


I'm well and truly stumped, and beg for your assistance oh Ubuntu Gurus. How may I fix this? My preferred way of WoWing on the laptop is a 1920x1200 Maximised Window, so the game covers the full screen, but I can pop easily between it and other windows, and not have to wait for Window mode changes. At least now after testing I've found resolutions I -can- play in, but I would like to find out why this is happening and hopefully find a fix.

Thank you all in advance. ^_^

---

### Post by cdegroot on 2009-07-28
I have the same problem. First of all - thanks for going through all the trouble, at least it allows me to select a mode that's playable. No more rebooting into Windows!

Dell D830 with Nvidia Quadro 140M, Ubuntu 9.04, Nvidia 185.18.14 drivers.

---

### Post by artemisgallow on 2009-07-28
I'm glad it's not just me then! I was thinking I was going crazy, lol.

I still haven't found a solution, I've not had any time to play lately, so I haven't bothered trying to fix it any more.

---

### Post by NightMKoder on 2009-07-28
MouseWarpOverride may help, but until xinput 2 is out wine doesn't handle mice in games well.

---

### Post by cdegroot on 2009-08-11
FYI - CrossOver Office (which I installed today to run Outlook 2007 for our corporate mail) has the same issue. [http://www.codeweavers.com/support/tickets/browse/?ticket_id=754499](http://www.codeweavers.com/support/tickets/browse/?ticket_id=754499)

---

### Post by me1234 on 2009-11-01
I've found that this problem isn't with wine, it happens with any game where the mouse is hidden, for example in savage 2 when I go into a game the camera starts moving in exactly the same way it does in WoW when you hold down the mouse button, the only difference being that it does it all the time because the mouse is hidden all the time instead of when you are just holding down the mouse button

---

