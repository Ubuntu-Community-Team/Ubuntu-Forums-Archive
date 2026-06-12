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

