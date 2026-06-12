---
title: "Wine not restoring resolution when exiting."
date: 2009-09-16
forum: Wine
---

### Post by pieman711 on 2009-09-16
I've just installed the original red faction game in wine and after a quick play everything with the game seems to be working fine. 
While I'm playing the game in full screen mode the Gnome panel at the top and bottom of my screen are still visible. It doesn't affect the game play but is quite irritating. 
Also when I quit the game the resolution stays at 1280x1024 and I have to put it back to 1680x1050 manually.
Does anyone know of anything I can do to fix these problems?
I'm currently running wine v 1.1.21 on ubuntu 8.10
Thank you very much

---

### Post by hikaricore on 2009-09-16
Have you tried disabling desktop effects?

---

### Post by pieman711 on 2009-09-16
That's sorted the problem with the panels still being visible (I've set "allow the window manager to decorate the windows" but unchecked "allow the window manager to control the windows" in the wine configuration program)
The resolution is still set to the games resolution when I exit the game though.

---

### Post by hikaricore on 2009-09-16
I used to have a similar issue with one of the GTA titles, the problem was that when the game closed WINE actually crashed leaving the resolution unchanged.
If you run this game from a terminal is there any indication that WINE is actually crashing when you exit?
Also you may want to try updating to a newer version of WINE if at all possible.

---

### Post by pieman711 on 2009-09-17
This is the readout I get when I run it from terminal:

fixme:d3d:IWineD3DImpl_FillGLCaps OpenGL implementation supports 32 vertex samplers and 32 total samplers
fixme:d3d:IWineD3DImpl_FillGLCaps Expected vertex samplers + MAX_TEXTURES(=8) > combined_samplers
fixme:win:EnumDisplayDevicesW ((null),0,0x32f468,0x00000000), stub!
fixme:d3d:IWineD3DDeviceImpl_EvictManagedResources (0x1884a8) : stub
fixme:d3d:IWineD3DDeviceImpl_EvictManagedResources (0x1884a8) : stub
fixme:d3d:IWineD3DDeviceImpl_EvictManagedResources (0x1884a8) : stub
fixme:d3d:IWineD3DDeviceImpl_EvictManagedResources (0x1884a8) : stub
fixme:d3d:IWineD3DDeviceImpl_EvictManagedResources (0x1884a8) : stub
fixme:d3d_draw:drawPrimitive Using software emulation because manual fog coordinates are provided
fixme:d3d:IWineD3DDeviceImpl_EvictManagedResources (0x1884a8) : stub
fixme:d3d:IWineD3DDeviceImpl_EvictManagedResources (0x1884a8) : stub
fixme:d3d:IWineD3DDeviceImpl_EvictManagedResources (0x1884a8) : stub
fixme:d3d:IWineD3DDeviceImpl_EvictManagedResources (0x1884a8) : stub
fixme:dsound:DllCanUnloadNow (void): stub
pieman@pieman-desktop:~$

---

