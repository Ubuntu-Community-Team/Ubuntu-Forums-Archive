---
title: "Start to Game on Radeon Xpress 1150"
date: 2009-12-28
forum: Wine
---

### Post by Boulemans on 2009-12-28
I managed (like in: installed PoL) to install GTA: Vice City on my laptop.

When I run it it can happen that i see a blue Wine-ish screen, but the window closes after 3 seconds. 

Sometimes the wine-screen stays, and it does load a Vice City menu. BUT: It isn't stable: Blue screen of wine keeps on showing with flashes of vice city in between. I just managed to be in game only once.

When I start Playonlinux from the terminal, I get a pop-up: no 3D acceleration. I thought that I uninstalled fglrx and installed Xserver-xorg-video-ati. Don't know if its important, but with my activated driver I can do Skydome and other visial effects. In the terminal I get:
```

$ glxinfo | grep vendor
server glx vendor string: SGI
client glx vendor string: SGI
OpenGL vendor string: DRI R300 Project 
```


Now - the question: eventually I want to play vice, but I think I first need to do:

How to activate 3D acceleration With a Radeon Xpress 1150?

---

### Post by Boulemans on 2009-12-29
more detail information:

   1. Wine version - 1.01
   2. Terminal output - 
   3. Wine configuration -
          * OS version - Windows XP
          * Library overrides - none
          * Graphics settings - 
      Allow DirectX apps to stop the mouse leaving their window: Checked
      Allow the window manager to decorate the windows checekd
      Allow the window manager to control the windows checked
      Emulate a virtual desktop: 800 x 600 checked
      Vertex Shader support: hardware, allow pixel shader: checked

          * Registry edits- none that I know of (perhaps PoL
   4. Hardware specs/drivers - just like in last massage: Radeon Xpress 1150, driver: I don't really know ...


ERRORS AND OTHER:
 while running PoL in the terminal, I get the message 
"You don't seem to have 3D acceleration !"

3D TEST
Viewing PoL settings, I see that the "3D Test" of the "System" menu gets 2100 - 2300 frames per 5 second, while my Laptop screen is set on 60 hz Is that normal? Because the 3D test also has a bit of flashy-screen-problem.

TERMINAL OUTPUT:

```
PlayOnLinux v3.6

Checking python : 				[ Ok ]
Running configuration of Grand Theft Auto : Vice City
err:menubuilder:WinMain unknown option -a
err:menubuilder:WinMain unknown option -r
fixme:iphlpapi:NotifyAddrChange (Handle 0x7d0239b8, overlapped 0x7d02399c): stub
fixme:shell:DllCanUnloadNow stub
wine: configuration in '/home/filip/.PlayOnLinux/wineprefix/GTAVC' has been updated.
err:menubuilder:WinMain unknown option -a
err:menubuilder:WinMain unknown option -r
Running Grand Theft Auto : Vice City
wine: configuration in '/home/filip/.PlayOnLinux/wineprefix/GTAVC' has been updated.
X Error of failed request:  GLXBadDrawable
  Major opcode of failed request:  154 (GLX)
  Minor opcode of failed request:  5 (X_GLXMakeCurrent)
  Serial number of failed request:  412
  Current serial number in output stream:  412
## now, about 3 seconds after the wine window popped up, that window is 
## closed.

```

---

