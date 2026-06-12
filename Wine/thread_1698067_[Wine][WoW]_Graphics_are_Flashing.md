---
title: "[Wine][WoW] Graphics are Flashing"
date: 2011-03-01
forum: Wine
---

### Post by Vorfin on 2011-03-01
I'm launching WoW in OpenGL Mode on Ubuntu 10.10 64Bit, however the graphics seem to be flashing rather uncontrollably rather than drawing Animations and NPCs, it is unplayable.

My PC uses an integrated Intel Chipset which I have read can have trouble with OpenGL Graphics, however if I try to launch WoW using Direct3D I get a Fatal Error and it crashes.

Has anyone encountered/fixed this issue before? Thanks.

---

### Post by Vorfin on 2011-03-01
Attached is a picture of it running in OpenGL Mode, and the Error Log of D3D Mode.

OpenGL:

[Large Image!]
[http://i.imgur.com/ujcxA.png](http://i.imgur.com/ujcxA.png)
[http://i.imgur.com/syLb1.png](http://i.imgur.com/syLb1.png)
[Large Image!]

Direct3D:
```

==============================================================================
World of WarCraft: Retail Build (build 13623)

Exe:      C:\Program Files\World of Warcraft\Wow.exe
Time:     Mar  1, 2011 11:53:28.925 PM
User:     peter
Computer: Inspiron-560
------------------------------------------------------------------------------

This application has encountered a critical error:

ERROR #132 (0x85100084) Fatal Exception
Program:    C:\Program Files\World of Warcraft\Wow.exe
Exception:    0xC0000005 (ACCESS_VIOLATION) at 0023:F7547D6A

The instruction at "0xF7547D6A" referenced memory at "0x0000000C".
The memory could not be "read".


WoWBuild: 13623
Settings: 
SET readTOS "1"
SET readEULA "1"
SET readScanning "-1"
SET readContest "-1"
SET locale "enGB"
SET showToolsUI "1"
SET accounttype "CL"
SET readTerminationWithoutNotice "1"
SET installType "Retail"
SET patchlist "enGB.patch.battle.net:1119/patch"
SET AllMPQLocal "0"
SET hwDetect "0"
SET gxRefresh "60"
SET gxMultisampleQuality "0.000000"
SET gxFixLag "0"
SET videoOptionsVersion "4"
SET textureFilteringMode "0"
SET Sound_MusicVolume "0.40000000596046"
SET Sound_AmbienceVolume "0.60000002384186"
SET farclip "185"
SET particleDensity "40"
SET reflectionMode "0"
SET weatherDensity "1"
SET playIntroMovie "4"
SET gxWindow "1"
SET gxResolution "1920x1080"
SET Gamma "1.000000"
SET baseMip "1"
SET environmentDetail "50"

----------------------------------------
               GxInfo
----------------------------------------
GxApi: D3D9
Shader Model: 3_0
  Vertex: vs_3_0
  Pixel: ps_3_0
Adapter Count: 1

Adapter 0 (primary):
  Driver: Display
  Version: 6.15.0008.0006
  Description: Direct3D HAL
  DeviceName: \\.\DISPLAY1

------------------------------------------------------------------------------

----------------------------------------
    x86 Registers
----------------------------------------

EAX=00000000  EBX=F7547D6A  ECX=00000010  EDX=7D6440C0  ESI=7D6440C0
EDI=00000000  EBP=0033F430  ESP=0033F3F0  EIP=F7547D6A  FLG=00210287
CS =0023      DS =002B      ES =002B      SS =002B      FS =0063      GS =006B

```

---

### Post by cwwilson721 on 2011-03-02
Search this forum for "WoW+Intel"

You would then know that with your older intel integrated graphics, ***if*** you can even get it to play under wine, will be horrible, under opengl, and can forget about D3D (because wine will 'translate' all D3D to opengl anyway).

Search first.

---

### Post by damonVT on 2011-03-05
Vorfin, I was having crashes until I tried [this]("http://translate.google.com.br/translate?hl=pt-BR&langpair=pt|en&u=http://www.ladolinuxdaforca.com.br/linux/jogos/instalando-world-of-warcraft-linux-intel&prev=/translate_s%3Fhl%3Dpt-BR%26q%3Dwww.ladolinuxdaforca.com.br/linux/jogos/instalando-world-of-warcraft-linux-intel%26sl%3Den%26tl%3Dpt"). It's not perfect now, with black polygons under the characters, but it's definitely playable.

I have the same OpenGL problem as you, but d3d mode is acceptable.

---

