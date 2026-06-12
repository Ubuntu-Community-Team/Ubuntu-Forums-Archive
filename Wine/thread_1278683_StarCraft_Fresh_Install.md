---
title: "StarCraft Fresh Install"
date: 2009-09-29
forum: Wine
---

### Post by vlad1975 on 2009-09-29
Hello,

I yet to have a succesful run to game when it comes to Linux so here we go..

Due to my failure to run any games on my system i thought i try to run one of the classic game to see if if it will work to my computer.
StarCraft Broadwar

Here it goes:

Installation successful on WINE
Using wine 1.1.30
when i try to run Starcraft broadwar.. I head the sound "music" saying its running.

Visual:
It change my resolution then it seems like it freez. It does not show me the game only way i can get out of it is hitting ESC

I am using Nvidia with driver 185.18.36

There must be something i am not doing to make any of this games run on my system.

So far games tried to play on the system are the following:
Starcraft
City Of Heroes
Diablo
AION

PLEASE PLEASE SOMEONE HELP ME!!! I WONT WANT TO GO BACK ON THE EVIL MICROSOFT WINDOWS!!!!! NOOO!!!!

---

### Post by beastrace91 on 2009-09-29
Aion is known not to run as of yet via Wine and I have never personally tried city of heros but be sure to check the [appdb](http://appdb.winehq.org/) for that one.

As for Starcraft and Diablo 2 I have gotten these to run on multiple different Ubuntu systems with Wine with little to-no tweaking. Perhaps open your winecfg and set Starcraft and/or Diablo to run in a "virtual desktop" and see if they load then

~Jeff

---

### Post by vlad1975 on 2009-09-29
Hi Jeff,

tried that..
same issue.. Sounds like the game is running i can even hover the mouse and i can hear the sound when u hover some of the options yet nothing shows on graphic 
see attachment

---

### Post by beastrace91 on 2009-09-29
Can you try running the game from terminal and post the output it gives when the game crashes out? (To run it from terminal change directory to the location of your game.exe and then run ```
wine game.exe
```)

~Jeff

---

### Post by vlad1975 on 2009-09-29
No go same issue

---

### Post by vlad1975 on 2009-09-29
```
ed@ed-desktop:~$ cd "/home/ed/.wine/dosdevices/c:/Program Files/"
ed@ed-desktop:~/.wine/dosdevices/c:/Program Files$ ls
Common Files                            Internet Explorer  StarCraft
InstallShield Installation Information  NCsoft
ed@ed-desktop:~/.wine/dosdevices/c:/Program Files$ cd "/home/ed/.wine/dosdevices/c:/Program Files/StarCraft"
ed@ed-desktop:~/.wine/dosdevices/c:/Program Files/StarCraft$ ls
battle.snp     patch_rt.mpq            SEditITA.loc                StarDat.mpq
BrooDat.mpq    patch.txt               SEditPTB.loc                StarEdit.cnt
BroodWar.mpq   Register Starcraft.url  Smackw32.dll                StarEdit.exe
EditLocal.dll  Riched20.dll            standard.snp                StarEdit.hlp
License.html   SEditDEU.loc            StarCraft.exe               storm.dll
License.txt    SEditENU.loc            StarCraft Install Log.html
Local.dll      SEditESP.loc            StarCraft Manual.pdf
Maps           SEditFRA.loc            Starcraft.mpq
ed@ed-desktop:~/.wine/dosdevices/c:/Program Files/StarCraft$ wine Starctaft.exe
wine: could not load L"C:\\windows\\system32\\Starctaft.exe": Module not found
ed@ed-desktop:~/.wine/dosdevices/c:/Program Files/StarCraft$ wine StarCraft.exe
fixme:advapi:SetSecurityInfo stub
err:wgl:opengl_error No OpenGL support compiled in.
err:d3d_caps:WineD3D_CreateFakeGLContext Can't find a suitable iPixelFormat.
err:d3d:InitAdapters Failed to get a gl context for default adapter
fixme:x11drv:X11DRV_desktop_SetCurrentMode Cannot change screen BPP from 32 to 8

```

---

### Post by sideaway on 2009-09-29
change embedded resolution to 640x400 for starcraft. or 320x240 if that doesn't work. if 640x400 works you can try 800x600.

The resolution hacks do not work in wine either...

---

### Post by vlad1975 on 2009-09-29
I tried that and still no go.. seems like i am missing a pluggin like directX for windows

---

### Post by sideaway on 2009-09-29
have you tried Winetricks with d3dx9?

---

### Post by vlad1975 on 2009-09-29
Sorry still new in linux.. could you guide me on that wine trick? in noobie term :)

---

### Post by Jepic Phail on 2009-10-31
[Winetrick]("http://wiki.winehq.org/winetricks"). :)

---

### Post by myromance123 on 2009-11-01
> err:wgl:opengl_error No OpenGL support compiled in.
err:d3d_caps:WineD3D_CreateFakeGLContext Can't find a suitable iPixelFormat.
err:d3d:InitAdapters Failed to get a gl context for default adapter
fixme:x11drv:X11DRV_desktop_SetCurrentMode Cannot change screen BPP from 32 to 8

Somethings terribly wrong with your graphics. Have you played any Open Source 3D games that can be found in the repositories? Try something like Urban Terror, or Glest or anything 3D so we can know how deep this problem is.

Also, give Nvidia's new Linux Driver 190.42 a go, it improves on performance greatly compared to 185.18.36, I just upgraded and tested a lot of games with it (it might fix your graphics issue here).

Can you also post your computer specs?
Processor, RAM and graphics card.

---

