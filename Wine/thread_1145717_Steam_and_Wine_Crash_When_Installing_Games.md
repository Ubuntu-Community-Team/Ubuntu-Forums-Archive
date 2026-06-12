---
title: "Steam and Wine Crash When Installing Games"
date: 2009-05-01
forum: Wine
---

### Post by Tinfoilpain on 2009-05-01
Hi, I just installed wine and steam on top of it on ubuntu 8.10, and I loaded it up and it works fine until I hit the install game button for L4D.
Then it just crashes, no message, no error displayed just gone.
I currently have an AMD Sempron 2800+ and an ATI Radeon X1600 AGP with fglrx drivers installed. If you guys have any answers on how to fix this please let me know. Thanks :)

---

### Post by Kareeser on 2009-05-01
Sounds like a bug I'm experiencing, heh. Are you running the AMD64 version of Ubuntu?

As a test, run steam under a terminal session, so you can see what's going on in the background.

```
cd ~/.wine/drive_c/Program\ Files/Steam
wine steam.exe
```

---

### Post by asdfoo on 2009-05-02
The problem is most likely the linux ATI drivers, they do not work as well as NVIDIA as they have not really been a priority over the years for ATI.

You can try setting the OffscreenRenderingMode key to fbo

Open regedit

HKCU, Software, Wine, create a key called Direct3D, create a string entry called OffscreenRenderingMode, set the value to fbo.

You'll be lucky if it starts.

At the moment, L4D with my 8800 GTS gets about 42fps and I've completed all the campaigns and most of the survival scenarios, probably had 3-4 crashes since L4D was released.

---

### Post by Kareeser on 2009-05-06
The differece is that Steam is crashing even before the program is installed... I'm thinking that he just presses "Install", and the program freezes.

Which is what happens to me when I try to install CS 1.6.

---

### Post by jamesmorad on 2009-05-15
I'm having the same problem with Ubuntu 64 bit and Nvidia 9800GTX x 2 in SLI. 

Any update on how to get games to install in steam without crashing wine and steam?

---

### Post by jamesmorad on 2009-05-18
Also, in case this would help solving the issue, this is the output I get after Steam crashes on game install:

```
fixme:shdocvw:InPlaceActiveObject_TranslateAccelerator (0x1a31e0)->(0x32cbc4)
err:ole:CoGetClassObject class {9a5ea990-3034-4d6f-9128-01f3c61022bc} not registered
err:ole:CoGetClassObject no class object {9a5ea990-3034-4d6f-9128-01f3c61022bc} could be created for context 0x1

```

---

### Post by thisnamestoolong on 2009-05-24
I am having the same problem -- Steam locks up hard, greys out, and I need to Force Quit to get out of it. When I try to run in the terminal it outputs the code:

err:ole:CoGetClassObject class {9a5ea990-3034-4d6f-9128-01f3c61022bc} not registered
err:ole:CoGetClassObject no class object {9a5ea990-3034-4d6f-9128-01f3c61022bc} could be created for context 0x1[/font]

---

### Post by Duckter on 2009-05-29
I have had much the same problem by the sounds of it but I think I have sorted my issue.

I am using 8.10 x64 on a Toshiba Satellite A215-S4747 - AMD64 (Turion TL-56) with a Radeon X1200 and the latest drivers installed from the ATI site.

Everytime I tried to install a game on Steam, X would crash and send me straight back to the login screen. The same happened trying any other application through WINE. I tried Wine Doors but that didnt make any difference.

I remembered a few other posts about other things saying ATI drivers were to blame for a number of problems so I tried disabling them (which tends to give u the answer straight away if its the app or drivers to blame) and after messing it up completely I found that I can get everything working crash free after fiddling with the Catalyst Control Centre and turning off Xinerama and turning off my second display.

I haven't actually played CS:Source yet as it is still downloading but here is hoping all goes well :)

Hopefully that should be some info to help you latest drivers, try wine doors and turn off extra displays (if any)

---

### Post by Duckter on 2009-05-30
Well it installed but after the splash screen I get a messed up main menu. I can hear the sound of the options clicking but I cant see a damn thing. Tried it in windowed mode too but no luck. Shall look around the forums and see if i can find a solution but at least I'm one step closer.

EDIT: Spoke too soon. using -dxlevel 70 seems to have fixed it :D

EDIT: Spoke too soon again. it only half solved the problem. 3d gfx in game are totally borked! everything else is fine though

---

### Post by Evontroy on 2009-06-13
I'm having the same issue as everyone else; Steam closes while trying to install a game. Has anyone figured out a resolution?

---

### Post by Evontroy on 2009-06-13
Okay I fixed the issue. Apparently the issue stemmed from using a beta version of wine. So I reverted to an older version and "problem-fixed".

---

### Post by Deacon Blues on 2009-06-13
I've been having the exact same issues: Steam acts fine until it's time to install something, then it crashes and takes wine with it.  I'm running 9.04 x64 on a Phenom II 720 with Radeon HD4770 (I know, I know, bleeding edge GPU).  I'm using the latest Wine beta because I couldn't get WoW to install with the stable version.  It sounds like I need to revert; I just hope it doesn't break WoW. 8-[

---

### Post by Sephoroth on 2009-06-15
Mind if I asked what version of WINE are you guys (with it working) using?  I'm having the same bug on my GeForce 9400M G (Steam won't install games or launch ones that I transfered from a Windows partition).  It isn't working for me with what is available on the repositories (1.1.23).

---

