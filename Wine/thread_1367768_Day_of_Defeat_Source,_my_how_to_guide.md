---
title: "Day of Defeat Source, my how to guide"
date: 2009-12-29
forum: Wine
---

### Post by sleepysummer on 2009-12-29
Hey guys, just wanted to throw my specs out there so maybe someone who is having problems running this game will solve their issues.

My specs:
Athlon AMD 5200+
Geforce 8500GT (512 MB)
Audigy 2 ZS
2GB DDR3 RAM
Lots of Space
Ubuntu 9.1 Karmic

I played this game years ago and recently wanted to give it another shot, of course the windows installation I tried first was a failure so I want to my increasingly favorite OS: Ubuntu 9.1 Karmic

I'm currently using aptitude to handle packages and I have the basic 3d video drivers (the standard ones that the 3d chess game told me to get) and Python to handle it.

I (re)purchased DoD:S for 7.50 through steam, unfortunately I had to use windows to install steam due to an error during installation process. After that though I simply copied the entire folder from my edit: (windows)harddrive to my (ubuntu)desktop and ran it from there using the latest Wine.

My Wine settings are as follows:
Windows XP Version
Library: Existing override d3d10core (native, bullitin)
Graphics: Checks in Allow windows manager to decor, control
D3D Support Vertex Shader None, Allow Pixel Shader Off

Launch Steam, Install and update DoD:S
Reboot of course for safe measure
Relaunch, go to My Games tab in Steam
Right click DoD:S go to properties and then Set Launch Options
-dxlevel 81
Save it and Launch. 
I configured my Video settings to be acceptable but no Bloom or effects, feel free to set Decal and model detail high
I have mine currently running in widescreen 1680x1050 with good frame rate and ping hovering in the mid 50's with a cable connection and 32 players on the server.

The best way to not crash during the resolution switch is to do it in game, but the graphics level settings are to be done on the start screen

For me, I found that sound is a major issue in performance for games on Karmic at least, I set mine medium and it seems fine. 
Lag only very slightly noticeable when firing fast automatic weapons, a few shots here and there are faster then usual

I noticed that it took a few times for my settings to save properly but they did.

I'm new at Linux so please forgive my lack of Linux speak, hope this helps anyone having issues with the game as I first did with the original instructions on how to run DoD:S

---

