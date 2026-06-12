---
title: "World of Warcraft 3.3.3 Crash Issues - Ubuntu/Wine/ATI Graphics"
date: 2010-05-20
forum: Wine
---

### Post by BlueInkAlchemist on 2010-05-20
Greetings all, 

I have been trying like crazy to get World of Warcraft running on my somewhat antiquated laptop, a Dell Inspiron 8600 with an onboard ATI Mobility Radeon 9600 GPU.  This laptop used to run Windows, but after a series of unfortunate events it now runs Ubuntu.  World of Warcraft ran fine under Windows.  I've loaded the latest version of the OS, updated all its libraries, loaded and updated the Wine emulator, and Warcraft is downloaded, installed and patched.

I am able to log in to the game, select a server & character and load the game world.  However, as soon as the world loads, a critical error occurs and the game crashes.  I've tried a variety of solutions, including an old addon (which I have since removed) and editing the Wine registry, but nothing so far has worked.  

Can anybody help or point me in the right direction?  Thanks in advance!

Technical information follows:

==============================================================================
World of WarCraft (build 11723)

Exe:      C:\Program Files\World of Warcraft\Wow.exe
Time:     May 20, 2010  1:04:44.435 AM
User:     josh
Computer: josh-laptop
------------------------------------------------------------------------------

This application has encountered a critical error:

ERROR #132 (0x85100084) Fatal Exception
Program:	C:\Program Files\World of Warcraft\Wow.exe
Exception:	0xC0000005 (ACCESS_VIOLATION) at 0073:00642C40

The instruction at "0x00642C40" referenced memory at "0x00000000".
The memory could not be "written".


WoWBuild: 11723
Realm: Twisting Nether [63.241.255.49:3724]
Local Zone: Deathknell, Tirisfal Glades
Local Player: Thanasis, 0480000003F55689, (1861.13,1566.54,94.3123)
Total lua memory: 11235KB
Current Addon: (null)
Current Addon function: UNKNOWN
Current Addon object: (null)
Settings: 
SET locale "enUS"
SET movie "0"
SET SoundOutputSystem "1"
SET SoundBufferSize "100"
SET showToolsUI "1"
SET realmList "us.logon.worldofwarcraft.com"
SET patchlist "us.version.worldofwarcraft.com"
SET coresDetected "1"
SET hwDetect "0"
SET gxAPI "OpenGL"
SET gxResolution "1280x800"
SET gxRefresh "60"
SET gxMultisampleQuality "0.000000"
SET gxFixLag "0"
SET videoOptionsVersion "3"
SET Gamma "1.000000"
SET Sound_OutputDriverName "System Default"
SET Sound_MusicVolume "0.40000000596046"
SET Sound_AmbienceVolume "0.60000002384186"
SET farclip "397"
SET specular "1"
SET groundEffectDensity "24"
SET textureFilteringMode "2"
SET spellEffectLevel "5"
SET groundEffectDist "90"
SET environmentDetail "0.75"
SET ffxDeath "0"
SET ffxGlow "0"
SET readTOS "1"
SET readEULA "1"
SET readScanning "-1"
SET readContest "-1"
SET readTerminationWithoutNotice "-1"
SET installType "Retail"
SET accounttype "LK"
SET projectedTextures "1"
SET realmName "Twisting Nether"
SET gameTip "6"
SET mouseSpeed "1"
SET VoiceActivationSensitivity "0.39999997615814"
SET ChatMusicVolume "0.29999998211861"
SET ChatSoundVolume "0.39999997615814"
SET ChatAmbienceVolume "0.29999998211861"

----------------------------------------
               GxInfo
----------------------------------------
GxApi: OpenGL
Vendor: DRI R300 Project
Renderer: Mesa DRI R300 (RV350 4E50) 20090101 x86/MMX/SSE2 TCL DRI2
Version: 1.5 Mesa 7.7.1

------------------------------------------------------------------------------

~ registers, traces, modules & dump snipped ~

======================================================================
Hardware/Driver Information:
Processor:              0x0
Page Size:              4096
Min App Address:        0x10000
Max App Address:        0x7ffeffff
Processor Mask:         0x1
Number of Processors:   1
Processor Type:         586
Allocation Granularity: 65536
Processor Level:        6
Processor Revision:     3334
Os Version:             5.1
Os Service Pack:        4.0

Percent memory used:    55
Total physical memory:  785850368
Free Memory:            346304512
Page file:              3105337344
Total virtual memory:   2147352575

* * * * *

Dell Inspiron 8600
ATI Mobility Radeon 9600
Ubuntu 10.10 
Wine 1.1.44
World of Warcraft 3.3.3

Thanks again. :)

---

### Post by MaximB on 2010-05-20
Please post such stuff at the WINE section.

---

### Post by cmileto on 2010-05-20
And also, figured Id let ya know, I have that card as a desktop version and it wont play wow. It used to, however sometime after burning crusade it will no longer. Blame ATI or Blizzard, but not ubuntu or wine.

---

### Post by BlueInkAlchemist on 2010-05-20
> **MaximB said:**
> Please post such stuff at the WINE section.

Thank you for moving it.  I was having trouble finding the Wine section.  Of course, it was something like 1:30 in the AM...

> **cmileto said:**
> And also, figured Id let ya know, I have that card as a desktop version and it wont play wow. It used to, however sometime after burning crusade it will no longer. Blame ATI or Blizzard, but not ubuntu or wine.

Did you experience the same crash that I'm describing?  Or would it simply not boot?

---

### Post by BlueInkAlchemist on 2010-05-21
Me again.  Ran into a bigger issue in trying to fix the video problems and install something that supports my video card.  I posted this issue [here]("http://ubuntuforums.org/showthread.php?t=1489581").  I'll return to this after I get the video behaving properly again.

Thanks again for your help.

---

### Post by BlueInkAlchemist on 2010-05-24
Okay, so. 

I've now replaced the ATI proprietary driver with the open-source "Radeon" one. I made a few updates to the laptop's desktop environment (Gnome & Xserver) but WoW still throws the same error as above. 

I downloaded "extremetuxracer" and it runs fine. I get sound at the login screen, and if I wait a bit after getting the error I hear music in WoW. 

Relevant bits of glxinfo: 

```
name of display: :0.0

display: :0  screen: 0

direct rendering: Yes

server glx vendor string: SGI

server glx version string: 1.2

client glx vendor string: Mesa Project and SGI

client glx version string: 1.4

GLX version: 1.2

OpenGL vendor string: DRI R300 Project

OpenGL renderer string: Mesa DRI R300 (RV350 4E50) 20090101 x86/MMX/SSE2 TCL DRI2

OpenGL version string: 1.5 Mesa 7.7.1
```


As a refresher: 


```
Gathering information about your system... 

 Distribution:          Ubuntu 10.04

 Desktop environment:   GNOME

 Graphics chip:         ATI Technologies Inc RV350 [Mobility Radeon 9600 M10]

 Driver in use:         radeon

 Rendering method:      AIGLX
```

---

