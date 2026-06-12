---
title: "Unreal Anthology problem with cursor"
date: 2009-08-02
forum: Wine
---

### Post by d_3us on 2009-08-02
hi! I am running 9.04, with Wine 1.1.26. And i have problem with unreal anthology. Exactly with unreal tournament 2004 there is no installer for linux so I used  WINE and the game works almost well  but cursor of mouse moves in small area and not in whole window of game. The same happens when turn off compiz and emerald. When i run ut2k4 in terminal it shows 
```
fixme:process:GetProcessWorkingSetSize (0xffffffff,0x32e5bc,0x32e5b8): stub
fixme:system:SystemParametersInfoW Unimplemented action: 59 (SPI_SETSTICKYKEYS)
err:ole:CoGetClassObject class {96749377-3391-11d2-9ee3-00c04f797396} not registered
err:ole:CoGetClassObject class {96749377-3391-11d2-9ee3-00c04f797396} not registered
err:ole:create_server class {96749377-3391-11d2-9ee3-00c04f797396} not registered
err:ole:CoGetClassObject no class object {96749377-3391-11d2-9ee3-00c04f797396} could be created for context 0x7
fixme:win:EnumDisplayDevicesW ((null),0,0x32bc10,0x00000000), stub!
fixme:dsalsa:IDsDriverBufferImpl_SetVolumePan (0x14a980,0x14b010): stub
fixme:d3d:WineD3D_ChoosePixelFormat Add OpenGL context recreation support to SetDepthStencilSurface
fixme:imm:ImmReleaseContext (0x20034, 0x1dec88): stub
fixme:dsound:DllCanUnloadNow (void): stub
```i don't know what to do with this errors. Can someone help me?

---

### Post by Brebs on 2009-08-03
> **d_3us said:**
> no installer for linux
An installer can be written - examples:  [UT2004](http://bugs.gentoo.org/show_bug.cgi?id=159164) and [Quake4](http://forums.fedoraforum.org/showthread.php?t=189064).

---

### Post by PureLoneWolf on 2009-08-03
Try the Loki website for the native install script.

[http://www.liflg.org/](http://www.liflg.org/)

---

### Post by d_3us on 2009-08-03
thanks for answer. But i must say that this installer do not work with my CD "Unreal Anthology" and pop-up message "Please insert installation disc ut2k4"

I read in FAQ WINE solution for OLE errors. I installed DCOM98 they disappear but problem with cursor not. so i can undo this change. Probably nothing comes out with native version...

---

### Post by PureLoneWolf on 2009-08-03
There is a "How To" on the loki forums for using the Unreal Anthology disc.

[http://www.liflg.org/forum/viewtopic.php?t=810](http://www.liflg.org/forum/viewtopic.php?t=810)

Hope that helps.

---

