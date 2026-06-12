---
title: "Another New X Session Question"
date: 2010-11-27
forum: Wine
---

### Post by Sugi on 2010-11-27
I am trying to add a new session / section to my xorg.conf for running StarCraft II in wine, but I am having issues with some of the fine details.

How should I change the "ModeLine" line and is "DefaultDeapth" correct?
> 
Section “ServerLayout”
Identifier “SC2Layout”
Screen 0 “StarCraft II Screen”
InputDevice “Keyboard0&#8243; “CoreKeyboard”
InputDevice “Mouse0&#8243; “CorePointer”
EndSection

Section “Screen”
Identifier “StarCraft II Screen”
Device “Device0&#8243;
Monitor “StarCraft II Monitor”
DefaultDepth 24
SubSection “Display”
Virtual 1920 1080
Depth 24
Modes “1920×1080@60&#8243;
EndSubSection
EndSection

Section “Monitor”
Identifier “StarCraft II Monitor”
VendorName “Plug ‘n’ Play”
ModelName “Plug ‘n’ Play”
Gamma 1
ModeLine “1920×1080@60&#8243; 25.2 640 656 752 800 480 490 492 525 -hsync -vsync
EndSection

And [Next Method]

Then I have tried to run this bash file, but it will not work.
> #!/bin/sh
X :2 -ac &
DISPLAY=:2
WINEPREFIX=/home/sugi/.wine-1.3.7/ /home/sugi/.wine-1.3.7/wine 'C:\Program Files\StarCraft II\StarCraft II.exe'
It returned with this output:

> fixme:wgl:wglGetProcAddress :stub
Application tried to create a window, but no driver could be loaded.
Make sure that your X server is running and that $DISPLAY is set correctly.
err:d3d_caps:WineD3D_CreateFakeGLContext Failed to create a window.
err:d3d:InitAdapters Failed to get a gl context for default adapter
Direct3D9 is not available without OpenGL.
Application tried to create a window, but no driver could be loaded.
Make sure that your X server is running and that $DISPLAY is set correctly. 

I don't understand the problem, please someone help me out.

Sugi

---

### Post by Sugi on 2010-12-10
Still need help, bump.

---

