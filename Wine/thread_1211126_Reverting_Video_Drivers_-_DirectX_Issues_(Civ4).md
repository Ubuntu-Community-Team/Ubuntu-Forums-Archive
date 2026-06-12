---
title: "Reverting Video Drivers - DirectX Issues (Civ4)"
date: 2009-07-12
forum: Wine
---

### Post by damunzy on 2009-07-12
Ubuntu 9.04 AMD 64-bit
Wine 1.1.25
NVIDIA - 180 (also tried 185 which started the problems)

All,

I had DirectX 9.0c (Mar 09) and Civilization IV with all expansions working normally using NVIDIA's 180 driver. I wasn't able  to use a mod (Rise of Mankind) so I figured that maybe if I use a later driver that I could get it to work. Well, I had problems getting driver 185 to work so I reverted back to 180. I got the following error:
```
ERROR

Initialize Renderer failed. Check DirectX Installation, Latest Graphics Drivers and Graphics Settings
Parameters:
- width = 1024
- height = 768
- flags = 0xc
- hwnd = 0x30054
- adaptrid = 0
- deviceid = 3
Error:Creation failed: Could not initialize DirectX9
```I tried to jump around between 173 and 180 and finally settled back to 180- trying to see if I could jostle Wine into work. :)
I tried testing DirectX with dxdiag.exe and got the following errors:
```
DirectX Diagnostic Tool
Test Failed at step 40 (Creating flipping primary surface with one back buffer): HRESULT = 0x8876086c (error code)
```I tried to reinstall DirectX. Leaving the OS set as XP DirectX finished successfully without doing anything. Setting the OS to 2000 the installer fails out with and error that it is missing a file.

Is there somewhere in Wine that could be pointing to a driver that I am no longer using? If so where and how do I go about figuring where to point Wine and how. I'd rather not have to rm -rf .wine and reload everything again. Thanks!

---

### Post by ackanao on 2009-07-12
Read this carefully and try again (This time without DirectX):
[http://wiki.winehq.org/FAQ#head-fbaa851e07d7484640cc10b6d0c48abc741260b2]("http://wiki.winehq.org/FAQ#head-fbaa851e07d7484640cc10b6d0c48abc741260b2")

---

### Post by damunzy on 2009-07-12
> **ackanao said:**
> Read this carefully and try again (This time without DirectX):
[http://wiki.winehq.org/FAQ#head-fbaa851e07d7484640cc10b6d0c48abc741260b2](http://wiki.winehq.org/FAQ#head-fbaa851e07d7484640cc10b6d0c48abc741260b2)
> That said, there are some guides out there which describe how you can install Microsoft's DirectX. I reiterate: It is not recommended nor supported by Wine HQ to attempt this. Furthermore it is considered off topic in Wine HQ support mediums (such as the forums). Please use a clean Wine configuration folder before seeking help. (You may need to rm -rf ~/.wine and re-install your Windows applications.)Great, and yet people on WineHQ suggest installing DirectX to get games working. Frak, here's to loading Civilization...again! :D

Oh, and thanks for the reply. :)

---

### Post by ackanao on 2009-07-12
Pick some other test result with Gold status - there's many of them (if I'm not mistaken).

---

### Post by damunzy on 2009-07-14
> **ackanao said:**
> Pick some other test result with Gold status - there's many of them (if I'm not mistaken).
Thanks - did that. For a "vanilla" Civ4 BtS (Beyond the Sword) install the game works good if a little slow (minor issues that have already been noted for Civ4) - the game should not have Gold status though....Bronze or Silver at best.

Anyways, I got it working- it was an issue with the NVIDIA 185/180 drivers- not sure which exactly, but I purged my system and I now have 190.09 on my system and everything is working fine.

Rock on! :guitar: and thanks for all the fish (help)!

---

