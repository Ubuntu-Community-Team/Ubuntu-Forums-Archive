---
title: "HOWTO: Super Meat Boy + Game Controller"
date: 2010-12-04
forum: Wine
---

### Post by Sugi on 2010-12-04
Super Meat Boy 1.0.u3 + Game Controller
[IMG]http://www.uluga.ubuntuforums.org/attachment.php?attachmentid=177416&stc=1&d=1291515567[/IMG]

**Install wine**
[IMG]http://www.uluga.ubuntuforums.org/attachment.php?attachmentid=177417&stc=1&d=1291515567[/IMG]
sudo apt-get install wine
[For best results use version 1.3.7.]

**Install steam**
[IMG]http://www.uluga.ubuntuforums.org/attachment.php?attachmentid=177418&stc=1&d=1291515567[/IMG]
[IMG]http://www.uluga.ubuntuforums.org/attachment.php?attachmentid=177419&stc=1&d=1291515567[/IMG]
wget [http://steampowered.com/download/SteamInstall.msi](http://steampowered.com/download/SteamInstall.msi)
wine msiexec /i SteamInstall.msi

**Install Super Meat Boy**
Use steam to download & install Super Meat Boy which includes the directx files.

**Apply the fixes**
wine regedit
> HKEY_CURRENT_USER > Software > Wine > AppDefaults > SuperMeatBoy.exe > Direct3D
[IMG]http://www.uluga.ubuntuforums.org/attachment.php?attachmentid=177420&stc=1&d=1291515567[/IMG]
DirectDrawRenderer = opengl
VideoMemorySize = 896
[VideoMemorySize = Your video card ram]

**Login and Run Super Meat Boy**
wine 'C:\Program Files\Steam\Steam.exe'
Enjoy
[You may need to run wine within an emulated desktop]
wine explorer /desktop=Steam,1920x1080 Steam.exe

[IMG]http://www.uluga.ubuntuforums.org/attachment.php?attachmentid=177423&stc=1&d=1291516200[/IMG]

**Game Controllers [Gamepads]**
Most game controllers will be auto detected within Linux and the game should auto-detect it as well.

Game Controllers reported to work within Windows' box:
Logitech Chillstream [Confirmed]
Xbox 360 Controller
Logitech F710
Streetfighter gamepad
Logitech F310
Logitech Wireless Rumblepad 2
[http://forums.steampowered.com/forums/showthread.php?t=1626320]("http://forums.steampowered.com/forums/showthread.php?t=1626320")

**Note:**
You may want to increase the idle time, because the game controller won't active the game or your desktop.
System > Preferences > Screensaver
"Regard the Computer as idle after"
[IMG]http://www.uluga.ubuntuforums.org/attachment.php?attachmentid=177422&stc=1&d=1291516200[/IMG]

Youtube Trailer:
[http://www.youtube.com/watch?v=MzNKe_nQ1As]("http://www.youtube.com/watch?v=MzNKe_nQ1As")

Super Meat Boy 1.0.u3
Wine Version 1.3.7
Ubuntu 10.10 x64
Nvidia Drivers 260.19.06

Cheers,
Sugi

---

### Post by Sugi on 2010-12-04
Troubleshooting:
 - The Regedit may not be needed for everyone, as others have reported getting the game to work without it.
 - I have tried versions 1.0 and 1.0.1 stand-alones [non-steam], but I couldn't get the game to load. I believe it was linked to a directX issue.
 - "Emulated desktop" fixes the problem of the black screen with music.

---

### Post by Kimos on 2010-12-05
Do you have speed issues? My game loads and runs but it seems to be running at about double speed.

I'm using wine 1.2 so that might be the problem. I'll try that.

Also, "HKEY_CURRENT_USER > Software > Wine > AppDefaults" does not exist so I cannot edit the video memory size.

---

### Post by Sugi on 2010-12-05
Hello Kimos,
Oops, I should have made a note about that. In the regedit, if it doesn't exist, you either have to create it yourself and auto make one. winecfg > "Add an Application" and navigate to your ~/.wine/drive_c/Program Files/Steam/steamapps/common/SuperMeatBoy.exe

I have also woundered if my start menu within Super Meat Boy was a bit fast, but ingame results with normal speed.

Sugi

---

### Post by HellHitZ on 2010-12-07
I tried the method described and it works fine. But some levels don't show up correctly sometimes, which is weird because it seems to happen randomly. And I can atest to the fact that the menu is really fast, but in game it's all fine.

---

### Post by Sugi on 2010-12-07
Here, try some of these regedit tweaks. I have not gotten any of these graphical errors.  I have only gotten 2 crashes within 10 hours of play.

> HKEY_CURRENT_USER > Software > Wine > AppDefaults > SuperMeatBoy.exe > Direct3D 
> Multisampling
enabled
> DirectDrawRenderer
gdi
opengl
> RenderTargetLockMode
disabled
readdraw
readtex
> StrictDrawOrdering
enabled
> OffscreenRenderingMode
backbuffer
fbo
> UseGLSL
enabled
> VideoPciDeviceID
lspci -n [To find your video]

**For more information, check out winehq wiki:**
[http://wiki.winehq.org/UsefulRegistryKeys]("http://wiki.winehq.org/UsefulRegistryKeys")

Please keep us informed about your findings.
Sugi

---

### Post by geoovani on 2010-12-16
i need help
i cannot play super meat boy [IMG]http://img26.imageshack.us/img26/6240/pantallazops.png[/IMG]
thanks

---

### Post by Kimos on 2010-12-16
> **geoovani said:**
> i need help
i cannot play super meat boy 
thanks

That's almost no information to go on. No configuration, error output, version numbers, install method, or anything. Not much anyone can do for you.

Start here:
[http://appdb.winehq.org/objectManager.php?sClass=version&iId=22148&iTestingId=59410](http://appdb.winehq.org/objectManager.php?sClass=version&iId=22148&iTestingId=59410)

---

### Post by andrex316 on 2010-12-21
I could not find either "AppDefaults" or /Program Files/Steam

when i get to Program Files the only two folders that are available are Common Files and Internet Explorer

I am running winecfg as the root user btw

also, when i start thee game through steam, all that is shown are the white letters and a completely black screen

---

### Post by Sugi on 2010-12-23
andrex316, You can NOT run wine EVER as root.  You must uninstall wine and reinstall wine.  You did not install steam or super meat boy as well or you installed it to somewhere else other your wine/drive_c/Program Files.

```
sudo apt-get remove wine
```

Then follow the guide again and you should be set.

Sugi

---

### Post by guiocm on 2011-01-07
Hello!

I'm trying to run SMB, but something is going wrong.
Tested with and without emulated desktop. The wine version is 1.3.10, and super meat boy is the latest steam version.

When the game starts, it shows the first screen with the xbox360 controller and the message below. Then, the controller disappears, but the message remains. Pressing enter some times shows the "press start" message on a black screen. The menus are also displayed on a black screen.

[IMG]http://img24.imageshack.us/img24/7551/screenshotum.png[/IMG]
[IMG]http://img41.imageshack.us/img41/4709/screenshot1ef.png[/IMG]

I'm using a notebook with i5-430M, and intel integrated graphics (maybe my graphics card can't handle this...), ubuntu 10.10.

---

### Post by guiocm on 2011-01-07
Going through the menus until i was in the first level, I could see the graphics correctly for less than one second, then i got a black screen in which a white diagonal occasionally appeared. Completing the level brought something like this:

[IMG]http://img507.imageshack.us/img507/153/screenshot2s.png[/IMG]

---

### Post by guiocm on 2011-01-07
If i change the screen resolution to 1366x768 in-game, it all starts to work properly. Any way i found to force a screen resolution on launch wouldn't work, and the game apparently sets it to 1024x768 (at least the menu shows this value, although the fonts on the menu appear to be on the correct size for native resolution).

---

### Post by R33D3M33R on 2011-04-06
There seems to be a linux port in the works: [http://supermeatboy.com/85/Super_Meat_Boy_ultra_edition_is_out_/#b](http://supermeatboy.com/85/Super_Meat_Boy_ultra_edition_is_out_/#b)

So you just might wait for it and play it later without the need for wine.

---

### Post by Kimos on 2011-04-06
I haven't had any more success with WINE so I'll just wait for the port at this point.

---

### Post by Sugi on 2011-04-11
They have been back and fourth with the linux port.  If you guys can post logs, and wine version, video card and such. I'll be able to help out.

Sugi

---

### Post by freeball1 on 2011-04-14
The game runs fine for me, but when i enter Super Meat World the game won't respond to anything but the escape key which brings me back to the World Selection Screen.
Any ideas what might be wrong / am I missing something?

---

### Post by Sugi on 2011-04-18
freeball1, Please post wine version, wine output, video card, and maybe even a screen shot.

Sugi

---

### Post by freeball1 on 2011-04-18
I just found the problem, it seems you have to navigate with the mouse on the SuperMeatWorld selection screen. I had mouse warp override enabled in wine, so the pointer (in fullscreen mode invisible) got always warped to the center (which makes it impossible to choose a level set).

---

### Post by Sugi on 2011-04-18
Thanks for the feedback, sounds more like a workaround.  But oh well progress none the less.

Sugi

---

