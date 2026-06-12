---
title: "err:d3d_surface in NFS Most Wanted"
date: 2011-04-25
forum: Wine
---

### Post by Dezfor on 2011-04-25
[LIST]
[*]NFS Most Wanted version 1.3
[*]wine-1.3.17
[*]ubuntu 10.04
[/LIST]
After I launch speed.exe I don't have any textures in game and mouse cursor. Terminal's output:
> $ wine speed.exe 
fixme:win:EnumDisplayDevicesW ((null),0,0x32f77c,0x00000000), stub!
fixme:dsalsa:IDsDriverBufferImpl_SetVolumePan (0x1e4f158,0x1e4f598): stub
fixme:dsalsa:IDsDriverBufferImpl_SetVolumePan (0x1e4f158,0x1e4f598): stub
err:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glCompressedTexImage2DARB @ surface.c / 1087
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glCompressedTexSubImage2DARB @ surface.c / 992
err:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glCompressedTexImage2DARB @ surface.c / 1087
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glCompressedTexSubImage2DARB @ surface.c / 992
err:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glCompressedTexImage2DARB @ surface.c / 1087
err:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glCompressedTexImage2DARB @ surface.c / 1087
err:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glCompressedTexImage2DARB @ surface.c / 1087
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glCompressedTexSubImage2DARB @ surface.c / 992
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glCompressedTexSubImage2DARB @ surface.c / 992
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glCompressedTexSubImage2DARB @ surface.c / 992
In wine I activated Vitual desktop: 800x600 and installed d3dx9
Screens:
main game menu
[[IMG]http://img687.imageshack.us/img687/3088/gameex.png[/IMG] ](http://img687.imageshack.us/i/gameex.png/)
first race with Razor:
[[IMG]http://img576.imageshack.us/img576/7639/game1j.png[/IMG]](http://img576.imageshack.us/i/game1j.png/)

---

### Post by cogadh on 2011-04-25
Video card make/model?

---

### Post by Dezfor on 2011-04-25
> **cogadh said:**
> Video card make/model?
Intel HD
> $ lspci |grep VGA
00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 02)
Direct rendering works
> glxinfo |grep render
direct rendering: Yes
OpenGL renderer string: Mesa DRI Intel(R) IGDNG_M GEM 20091221 2009Q4 x86/MMX/SSE2

---

### Post by cogadh on 2011-04-25
Most likely the error is due to a lack of functionality in either the Linux driver for that chipset, or the chipset itself. The integrated Intel graphics solutions are really not the best for gaming, especially on Linux through Wine. If you have the option of replacing that with a dedicated graphics card, preferably one from Nvidia (their Linux drivers are the best and easiest to work with), or running it on a different machine that already has a dedicated graphics card, I'd highly recommend it.

---

### Post by Dezfor on 2011-04-25
**cogadh**, thanks for reply. I can't replace it because it is integrated one.
So, I suggest that problem is solved. I know at least the reason of problem

---

### Post by cogadh on 2011-04-25
You most certainly can replace an integrated graphics card, unless this machine is a laptop. Assuming this is a desktop, all you need to do is install a dedicated graphics card, then disable the integrated one in your machine's BIOS.

---

### Post by Dezfor on 2011-04-25
> **cogadh said:**
> You most certainly can replace an integrated graphics card, **unless this machine is a laptop**. Assuming this is a desktop, all you need to do is install a dedicated graphics card, then disable the integrated one in your machine's BIOS.
I have laptop Lenovo thinkpad edge 14 ;)

---

### Post by FerroPower on 2012-01-01
Working in my Intel integrated GM45 card, 

previously it use to give me the similar output the like OP, I tried installing some various stuffs like mesa, S3 texture compression, Pixel support libs, etc etc., I dont exactly which one did the trick but I can now Play NFS most wanted 1.3 on my laptop that too much faster then my windows 7 which is installed on other partition.

If anyone can help me please how to know which libs are currently in use by wine while playing NFS mw ??

---

### Post by FerroPower on 2012-01-07
SOLUTION !! I found what worked for me just enable the S3 texture compression and NFS most wanted works Fantastically in my low quality GM45 Intel Graphics 

just the change the  <option name="force_s3tc_enable" value="true" /> in .drirc file in your home folder. if you dont know how to set .drirc file just download app driconf it will install a app known as 3D acceleration. in it you have to change the Force S3tc settings to TRUE. just save the rest settings as it is. and now NFS Mw should be working but you need to Override some dll files better still install Directx9 via winetricks.

---

