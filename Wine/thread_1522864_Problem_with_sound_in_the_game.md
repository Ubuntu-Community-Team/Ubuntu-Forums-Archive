---
title: "Problem with sound in the game"
date: 2010-07-02
forum: Wine
---

### Post by ranlid on 2010-07-02
Hey all! When i run [Ragnarok]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=928") in wine sound in all system start distort. Enable\disable sound in game options and wine configuration not support. :( But when i launch ragnarok with windows desktop emulation and max resolution 960x600 sound works ok, but play in this resolution not convenient.. :(
Video card nVidia 9500GT wine version: all.
Help me please!
> $ wine Ragexe.exe -1rag1
fixme:dsalsa:IDsDriverBufferImpl_SetVolumePan (0x17d570,0x17d9b0): stub
fixme:dsalsa:IDsDriverBufferImpl_SetVolumePan (0x17d570,0x17d9b0): stub
fixme:win:EnumDisplayDevicesW ((null),0,0x32f1a0,0x00000000), stub!
fixme:d3d:swapchain_init Add OpenGL context recreation support to context_validate_onscreen_formats
fixme:dinput:SysMouseAImpl_Acquire Clipping cursor to (1,1)-(1159,890)
fixme:imm:ImmReleaseContext (0x10052, 0x12f0f8): stub
fixme:ddraw:IDirectDrawImpl_RestoreAllSurfaces (0x199870): Stub
fixme:ddraw:IDirectDrawImpl_WaitForVerticalBlank (0x199870)->(1,(nil)): Stub


---

### Post by dino99 on 2010-07-03
so have you followed this link:

[http://appdb.winehq.org/objectManager.php?sClass=version&iId=928](http://appdb.winehq.org/objectManager.php?sClass=version&iId=928)

which wine release do you have ?

---

### Post by ranlid on 2010-07-05
> **dino99 said:**
> so have you followed this link:

[http://appdb.winehq.org/objectManager.php?sClass=version&iId=928](http://appdb.winehq.org/objectManager.php?sClass=version&iId=928)

which wine release do you have ?

Wine 1.2-rc6

---

