---
title: "San Andreas on Wine crashes after startup"
date: 2008-12-28
forum: Wine
---

### Post by ColCommunism on 2008-12-28
Hi.  Whenever I try to run Grand Theft Auto: San Andreas on Wine, the screen turns black, flashes white twice, then turns black again.  If I click or push space, the screen flashes white again, and the application crashes. In the terminal, I get the following error:

```
ALSA lib pcm_dmix.c:935:(snd_pcm_dmix_open) The dmix plugin supports only playback stream
fixme:cursor:CURSORICON_LoadFromFile No support for .ani cursors.
fixme:cursor:SetSystemCursor (0x111e,00007f8a),stub!
fixme:cursor:SetSystemCursor (0x1126,00007f00),stub!
fixme:cursor:SetSystemCursor (0x1136,00007f03),stub!
fixme:cursor:SetSystemCursor (0x113e,00007f01),stub!
fixme:cursor:SetSystemCursor (0x114e,00007f88),stub!
fixme:cursor:SetSystemCursor (0x115e,00007f86),stub!
fixme:cursor:SetSystemCursor (0x116e,00007f83),stub!
fixme:cursor:SetSystemCursor (0x117e,00007f85),stub!
fixme:cursor:SetSystemCursor (0x118e,00007f82),stub!
fixme:cursor:SetSystemCursor (0x119e,00007f84),stub!
fixme:cursor:SetSystemCursor (0x11ae,00007f04),stub!
fixme:cursor:SetSystemCursor (0x11be,00007f02),stub!
fixme:system:SystemParametersInfoW Unimplemented action: 8193 (SPI_SETFOREGROUNDLOCKTIMEOUT)
fixme:win:EnumDisplayDevicesW ((null),0,0x172f0f4,0x00000000), stub!
err:d3d:WineD3D_ChoosePixelFormat Can't find a suitable iPixelFormat
fixme:d3d:IWineD3DDeviceImpl_EvictManagedResources (0x12e190) : stub
fixme:system:SystemParametersInfoW Unimplemented action: 59 (SPI_SETSTICKYKEYS)
err:d3d:WineD3D_ChoosePixelFormat Can't find a suitable iPixelFormat
err:quartz:FilterGraph2_AddSourceFilter Load (80070002)
err:quartz:FilterGraph2_AddSourceFilter Load (80070002)
Initialised SoundManager
fixme:dsound:IDirectSoundBufferImpl_SetFX (0x29ae388,0,(nil),(nil)): stub
fixme:system:SystemParametersInfoW Unimplemented action: 59 (SPI_SETSTICKYKEYS)
```

If I use a NoCD crack, then I get this error:

```
ALSA lib pcm_dmix.c:935:(snd_pcm_dmix_open) The dmix plugin supports only playback stream
fixme:system:SystemParametersInfoW Unimplemented action: 8193 (SPI_SETFOREGROUNDLOCKTIMEOUT)
fixme:win:EnumDisplayDevicesW ((null),0,0x33f754,0x00000000), stub!
err:d3d:WineD3D_ChoosePixelFormat Can't find a suitable iPixelFormat
fixme:d3d:IWineD3DDeviceImpl_EvictManagedResources (0x129440) : stub
fixme:system:SystemParametersInfoW Unimplemented action: 59 (SPI_SETSTICKYKEYS)
err:d3d:WineD3D_ChoosePixelFormat Can't find a suitable iPixelFormat
err:quartz:FilterGraph2_AddSourceFilter Load (80070002)
err:quartz:FilterGraph2_AddSourceFilter Load (80070002)
Initialised SoundManager
fixme:dsound:IDirectSoundBufferImpl_SetFX (0x36518e8,0,(nil),(nil)): stub
fixme:system:SystemParametersInfoW Unimplemented action: 59 (SPI_SETSTICKYKEYS)
```

I'm using Wine 1.0.1 (although I already tried 1.1.11, and it didn't work either), with an Intel 945GM integrated graphics card.  Also, I'm running Metacity.

Thanks in advance!

---

### Post by ColCommunism on 2009-01-02
Well, after upgrading to Wine 1.1.11, installing DirectX 9 through winetricks, and getting rid of my /etc/asound.conf file, I've reduced the errors to this:
```

fixme:win:EnumDisplayDevicesW ((null),0,0x33f694,0x00000000), stub!
fixme:d3d:IWineD3DDeviceImpl_EvictManagedResources (0x12def8) : stub
fixme:system:SystemParametersInfoW Unimplemented action: 59 (SPI_SETSTICKYKEYS)
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80040111
err:ole:CoGetClassObject no class object {da4e3da0-d07d-11d0-bd50-00a0c911ce86} could be created for context 0x1
err:ole:CoGetClassObject class {2721ae20-7e70-11d0-a5d6-28db04c10000} not registered
err:ole:CoGetClassObject no class object {2721ae20-7e70-11d0-a5d6-28db04c10000} could be created for context 0x1
err:ole:CoGetClassObject no class object {71985f4b-1ca1-11d3-9cc8-00c04f7971e0} could be created for context 0x1
err:ole:CoGetClassObject no class object {a2e3074f-6c3d-11d3-b653-00c04f79498e} could be created for context 0x1
err:ddraw:IDirectDrawImpl_QueryInterface (0x3659440) The App is requesting a D3D device, but a non-OpenGL surface type was choosen. Prepare for trouble!
err:ddraw:IDirectDrawImpl_QueryInterface  (0x3659440) You may want to contact wine-devel for help
err:ddraw:IDirectDrawImpl_QueryInterface (0x3659440)->({aca12120-3356-11d1-8fcf-00c04fc29b4e}, 0x36593d8): No interface found
err:ddraw:IDirectDrawImpl_QueryInterface (0x3659440)->({aca12120-3356-11d1-8fcf-00c04fc29b4e}, 0x36584e4): No interface found
err:ddraw:IDirectDrawImpl_QueryInterface (0x3659440)->({aca12120-3356-11d1-8fcf-00c04fc29b4e}, 0x36584e4): No interface found
err:ddraw:IDirectDrawImpl_QueryInterface (0x3659440)->({aca12120-3356-11d1-8fcf-00c04fc29b4e}, 0x36584e4): No interface found
err:ddraw:IDirectDrawImpl_QueryInterface (0x3659440)->({aca12120-3356-11d1-8fcf-00c04fc29b4e}, 0x36584e4): No interface found
err:ddraw:IDirectDrawImpl_QueryInterface (0x3659440)->({aca12120-3356-11d1-8fcf-00c04fc29b4e}, 0x36584e4): No interface found
err:ddraw:IDirectDrawImpl_QueryInterface (0x3659440)->({aca12120-3356-11d1-8fcf-00c04fc29b4e}, 0x36584e4): No interface found
err:ddraw:IDirectDrawImpl_QueryInterface (0x3659440)->({aca12120-3356-11d1-8fcf-00c04fc29b4e}, 0x36584e4): No interface found
err:ddraw:IDirectDrawImpl_QueryInterface (0x3659440)->({aca12120-3356-11d1-8fcf-00c04fc29b4e}, 0x36584e4): No interface found
err:ddraw:IDirectDrawImpl_QueryInterface (0x3659440)->({aca12120-3356-11d1-8fcf-00c04fc29b4e}, 0x36584e4): No interface found
err:ddraw:IDirectDrawImpl_QueryInterface (0x3659440)->({aca12120-3356-11d1-8fcf-00c04fc29b4e}, 0x36584e4): No interface found
err:ddraw:IDirectDrawImpl_QueryInterface (0x3659440)->({aca12120-3356-11d1-8fcf-00c04fc29b4e}, 0x36584e4): No interface found
err:d3d_surface:IWineGDISurfaceImpl_PrivateSetup (0x365e688) Overlays not yet supported by GDI surfaces
err:ddraw:IDirectDrawImpl_CreateNewSurface IWineD3DDevice::CreateSurface failed. hr = 8876086c
err:ddraw:IDirectDrawImpl_CreateSurface IDirectDrawImpl_CreateNewSurface failed with 8876086c
err:d3d_surface:IWineGDISurfaceImpl_PrivateSetup (0x365e8d8) Overlays not yet supported by GDI surfaces
err:ddraw:IDirectDrawImpl_CreateNewSurface IWineD3DDevice::CreateSurface failed. hr = 8876086c
err:ddraw:IDirectDrawImpl_CreateSurface IDirectDrawImpl_CreateNewSurface failed with 8876086c
err:d3d_surface:IWineGDISurfaceImpl_PrivateSetup (0x365eb28) Overlays not yet supported by GDI surfaces
err:ddraw:IDirectDrawImpl_CreateNewSurface IWineD3DDevice::CreateSurface failed. hr = 8876086c
err:ddraw:IDirectDrawImpl_CreateSurface IDirectDrawImpl_CreateNewSurface failed with 8876086c
err:ddraw:IDirectDrawImpl_QueryInterface (0x3659440)->({aca12120-3356-11d1-8fcf-00c04fc29b4e}, 0x36584e4): No interface found
err:ddraw:IDirectDrawImpl_QueryInterface (0x3659440)->({aca12120-3356-11d1-8fcf-00c04fc29b4e}, 0x36584e4): No interface found
err:ddraw:IDirectDrawImpl_QueryInterface (0x3659440)->({aca12120-3356-11d1-8fcf-00c04fc29b4e}, 0x36584e4): No interface found
err:d3d_surface:IWineGDISurfaceImpl_PrivateSetup (0x365ed78) Overlays not yet supported by GDI surfaces
err:ddraw:IDirectDrawImpl_CreateNewSurface IWineD3DDevice::CreateSurface failed. hr = 8876086c
err:ddraw:IDirectDrawImpl_CreateSurface IDirectDrawImpl_CreateNewSurface failed with 8876086c
err:d3d_surface:IWineGDISurfaceImpl_PrivateSetup (0x365efc8) Overlays not yet supported by GDI surfaces
err:ddraw:IDirectDrawImpl_CreateNewSurface IWineD3DDevice::CreateSurface failed. hr = 8876086c
err:ddraw:IDirectDrawImpl_CreateSurface IDirectDrawImpl_CreateNewSurface failed with 8876086c
err:d3d_surface:IWineGDISurfaceImpl_PrivateSetup (0x365f218) Overlays not yet supported by GDI surfaces
err:ddraw:IDirectDrawImpl_CreateNewSurface IWineD3DDevice::CreateSurface failed. hr = 8876086c
err:ddraw:IDirectDrawImpl_CreateSurface IDirectDrawImpl_CreateNewSurface failed with 8876086c
err:ddraw:IDirectDrawImpl_QueryInterface (0x3659440)->({aca12120-3356-11d1-8fcf-00c04fc29b4e}, 0x36584e4): No interface found
err:ddraw:IDirectDrawImpl_QueryInterface (0x3659440)->({aca12120-3356-11d1-8fcf-00c04fc29b4e}, 0x36584e4): No interface found
err:ddraw:IDirectDrawImpl_QueryInterface (0x3659440)->({aca12120-3356-11d1-8fcf-00c04fc29b4e}, 0x36584e4): No interface found
err:ddraw:IDirectDrawImpl_QueryInterface (0x3659440)->({aca12120-3356-11d1-8fcf-00c04fc29b4e}, 0x36584e4): No interface found
err:ddraw:IDirectDrawImpl_QueryInterface (0x3659440)->({aca12120-3356-11d1-8fcf-00c04fc29b4e}, 0x36584e4): No interface found
err:ddraw:IDirectDrawImpl_QueryInterface (0x3659440)->({aca12120-3356-11d1-8fcf-00c04fc29b4e}, 0x36584e4): No interface found
err:ddraw:IDirectDrawImpl_QueryInterface (0x3659440)->({aca12120-3356-11d1-8fcf-00c04fc29b4e}, 0x36584e4): No interface found
err:ddraw:IDirectDrawImpl_QueryInterface (0x3659440)->({aca12120-3356-11d1-8fcf-00c04fc29b4e}, 0x36584e4): No interface found
err:d3d_surface:IWineGDISurfaceImpl_PrivateSetup (0x1448f0) Overlays not yet supported by GDI surfaces
err:ddraw:IDirectDrawImpl_CreateNewSurface IWineD3DDevice::CreateSurface failed. hr = 8876086c
err:ddraw:IDirectDrawImpl_CreateSurface IDirectDrawImpl_CreateNewSurface failed with 8876086c
err:d3d_surface:IWineGDISurfaceImpl_PrivateSetup (0x144b40) Overlays not yet supported by GDI surfaces
err:ddraw:IDirectDrawImpl_CreateNewSurface IWineD3DDevice::CreateSurface failed. hr = 8876086c
err:ddraw:IDirectDrawImpl_CreateSurface IDirectDrawImpl_CreateNewSurface failed with 8876086c
err:d3d_surface:IWineGDISurfaceImpl_PrivateSetup (0x144f08) Overlays not yet supported by GDI surfaces
err:ddraw:IDirectDrawImpl_CreateNewSurface IWineD3DDevice::CreateSurface failed. hr = 8876086c
err:ddraw:IDirectDrawImpl_CreateSurface IDirectDrawImpl_CreateNewSurface failed with 8876086c
err:ddraw:IDirectDrawImpl_QueryInterface (0x3659440)->({aca12120-3356-11d1-8fcf-00c04fc29b4e}, 0x36584e4): No interface found
err:ddraw:IDirectDrawImpl_QueryInterface (0x3659440)->({aca12120-3356-11d1-8fcf-00c04fc29b4e}, 0x36584e4): No interface found
err:ddraw:IDirectDrawImpl_QueryInterface (0x3659440)->({aca12120-3356-11d1-8fcf-00c04fc29b4e}, 0x36584e4): No interface found
err:ddraw:IDirectDrawImpl_QueryInterface (0x3659440)->({aca12120-3356-11d1-8fcf-00c04fc29b4e}, 0x36584e4): No interface found
err:ddraw:IDirectDrawImpl_QueryInterface (0x3659440)->({aca12120-3356-11d1-8fcf-00c04fc29b4e}, 0x36584e4): No interface found
err:ddraw:IDirectDrawImpl_QueryInterface (0x3659440)->({aca12120-3356-11d1-8fcf-00c04fc29b4e}, 0x36584e4): No interface found
err:ddraw:IDirectDrawImpl_QueryInterface (0x3659440)->({aca12120-3356-11d1-8fcf-00c04fc29b4e}, 0x36584e4): No interface found
err:d3d_surface:IWineGDISurfaceImpl_PrivateSetup (0x145c30) Overlays not yet supported by GDI surfaces
err:ddraw:IDirectDrawImpl_CreateNewSurface IWineD3DDevice::CreateSurface failed. hr = 8876086c
err:ddraw:IDirectDrawImpl_CreateSurface IDirectDrawImpl_CreateNewSurface failed with 8876086c
err:d3d_surface:IWineGDISurfaceImpl_PrivateSetup (0x145e80) Overlays not yet supported by GDI surfaces
err:ddraw:IDirectDrawImpl_CreateNewSurface IWineD3DDevice::CreateSurface failed. hr = 8876086c
err:ddraw:IDirectDrawImpl_CreateSurface IDirectDrawImpl_CreateNewSurface failed with 8876086c
err:d3d_surface:IWineGDISurfaceImpl_PrivateSetup (0x1460d0) Overlays not yet supported by GDI surfaces
err:ddraw:IDirectDrawImpl_CreateNewSurface IWineD3DDevice::CreateSurface failed. hr = 8876086c
err:ddraw:IDirectDrawImpl_CreateSurface IDirectDrawImpl_CreateNewSurface failed with 8876086c
err:ddraw:IDirectDrawImpl_QueryInterface (0x3659440)->({aca12120-3356-11d1-8fcf-00c04fc29b4e}, 0x36584e4): No interface found
err:ddraw:IDirectDrawImpl_QueryInterface (0x3659440)->({aca12120-3356-11d1-8fcf-00c04fc29b4e}, 0x36584e4): No interface found
err:ddraw:IDirectDrawImpl_QueryInterface (0x3659440)->({aca12120-3356-11d1-8fcf-00c04fc29b4e}, 0x36584e4): No interface found
fixme:dsound:DSPROPERTY_Description1 (pPropData=0x33ee54,cbPropData=40,pcbReturned=0x33ee7c) GUID_NULL not implemented!
fixme:d3d:IWineD3DDeviceImpl_Release (0x3659560) Device released with resources still bound, acceptable but unexpected
fixme:d3d:dumpResources Leftover resource 0x1460d0 with type 1,WINED3DRTYPE_SURFACE
fixme:d3d:dumpResources Leftover resource 0x145e80 with type 1,WINED3DRTYPE_SURFACE
fixme:d3d:dumpResources Leftover resource 0x145c30 with type 1,WINED3DRTYPE_SURFACE
fixme:d3d:dumpResources Leftover resource 0x144f08 with type 1,WINED3DRTYPE_SURFACE
fixme:d3d:dumpResources Leftover resource 0x144b40 with type 1,WINED3DRTYPE_SURFACE
fixme:d3d:dumpResources Leftover resource 0x1448f0 with type 1,WINED3DRTYPE_SURFACE
fixme:d3d:dumpResources Leftover resource 0x365f218 with type 1,WINED3DRTYPE_SURFACE
fixme:d3d:dumpResources Leftover resource 0x365efc8 with type 1,WINED3DRTYPE_SURFACE
fixme:d3d:dumpResources Leftover resource 0x365ed78 with type 1,WINED3DRTYPE_SURFACE
fixme:d3d:dumpResources Leftover resource 0x365eb28 with type 1,WINED3DRTYPE_SURFACE
fixme:d3d:dumpResources Leftover resource 0x365e8d8 with type 1,WINED3DRTYPE_SURFACE
fixme:d3d:dumpResources Leftover resource 0x365e688 with type 1,WINED3DRTYPE_SURFACE
fixme:ddraw:IDirectDrawImpl_GetScanLine (0x148288)->(0x7756283c): Semi-Stub
err:ddraw:IDirectDrawImpl_QueryInterface (0x51cb0e0) The App is requesting a D3D device, but a non-OpenGL surface type was choosen. Prepare for trouble!
err:ddraw:IDirectDrawImpl_QueryInterface  (0x51cb0e0) You may want to contact wine-devel for help
err:ddraw:IDirectDrawImpl_QueryInterface (0x51cb0e0)->({aca12120-3356-11d1-8fcf-00c04fc29b4e}, 0x51c2a58): No interface found
err:ddraw:IDirectDrawImpl_QueryInterface (0x51cb0e0)->({aca12120-3356-11d1-8fcf-00c04fc29b4e}, 0x51c1bec): No interface found
err:ddraw:IDirectDrawImpl_QueryInterface (0x51cb0e0)->({aca12120-3356-11d1-8fcf-00c04fc29b4e}, 0x51c1bec): No interface found
err:ddraw:IDirectDrawImpl_QueryInterface (0x51cb0e0)->({aca12120-3356-11d1-8fcf-00c04fc29b4e}, 0x51c1bec): No interface found
err:ddraw:IDirectDrawImpl_QueryInterface (0x51cb0e0)->({aca12120-3356-11d1-8fcf-00c04fc29b4e}, 0x51c1bec): No interface found
err:ddraw:IDirectDrawImpl_QueryInterface (0x51cb0e0)->({aca12120-3356-11d1-8fcf-00c04fc29b4e}, 0x51c1bec): No interface found
err:ddraw:IDirectDrawImpl_QueryInterface (0x51cb0e0)->({aca12120-3356-11d1-8fcf-00c04fc29b4e}, 0x51c1bec): No interface found
err:ddraw:IDirectDrawImpl_QueryInterface (0x51cb0e0)->({aca12120-3356-11d1-8fcf-00c04fc29b4e}, 0x51c1bec): No interface found
err:ddraw:IDirectDrawImpl_QueryInterface (0x51cb0e0)->({aca12120-3356-11d1-8fcf-00c04fc29b4e}, 0x51c1bec): No interface found
err:ddraw:IDirectDrawImpl_QueryInterface (0x51cb0e0)->({aca12120-3356-11d1-8fcf-00c04fc29b4e}, 0x51c1bec): No interface found
err:ddraw:IDirectDrawImpl_QueryInterface (0x51cb0e0)->({aca12120-3356-11d1-8fcf-00c04fc29b4e}, 0x51c1bec): No interface found
err:ddraw:IDirectDrawImpl_QueryInterface (0x51cb0e0)->({aca12120-3356-11d1-8fcf-00c04fc29b4e}, 0x51c1bec): No interface found
err:d3d_surface:IWineGDISurfaceImpl_PrivateSetup (0x51cfea8) Overlays not yet supported by GDI surfaces
err:ddraw:IDirectDrawImpl_CreateNewSurface IWineD3DDevice::CreateSurface failed. hr = 8876086c
err:ddraw:IDirectDrawImpl_CreateSurface IDirectDrawImpl_CreateNewSurface failed with 8876086c
err:d3d_surface:IWineGDISurfaceImpl_PrivateSetup (0x51d00f8) Overlays not yet supported by GDI surfaces
err:ddraw:IDirectDrawImpl_CreateNewSurface IWineD3DDevice::CreateSurface failed. hr = 8876086c
err:ddraw:IDirectDrawImpl_CreateSurface IDirectDrawImpl_CreateNewSurface failed with 8876086c
err:d3d_surface:IWineGDISurfaceImpl_PrivateSetup (0x51d0348) Overlays not yet supported by GDI surfaces
err:ddraw:IDirectDrawImpl_CreateNewSurface IWineD3DDevice::CreateSurface failed. hr = 8876086c
err:ddraw:IDirectDrawImpl_CreateSurface IDirectDrawImpl_CreateNewSurface failed with 8876086c
err:ddraw:IDirectDrawImpl_QueryInterface (0x51cb0e0)->({aca12120-3356-11d1-8fcf-00c04fc29b4e}, 0x51c1bec): No interface found
err:ddraw:IDirectDrawImpl_QueryInterface (0x51cb0e0)->({aca12120-3356-11d1-8fcf-00c04fc29b4e}, 0x51c1bec): No interface found
err:ddraw:IDirectDrawImpl_QueryInterface (0x51cb0e0)->({aca12120-3356-11d1-8fcf-00c04fc29b4e}, 0x51c1bec): No interface found
err:d3d_surface:IWineGDISurfaceImpl_PrivateSetup (0x51d0598) Overlays not yet supported by GDI surfaces
err:ddraw:IDirectDrawImpl_CreateNewSurface IWineD3DDevice::CreateSurface failed. hr = 8876086c
err:ddraw:IDirectDrawImpl_CreateSurface IDirectDrawImpl_CreateNewSurface failed with 8876086c
err:d3d_surface:IWineGDISurfaceImpl_PrivateSetup (0x51d07e8) Overlays not yet supported by GDI surfaces
err:ddraw:IDirectDrawImpl_CreateNewSurface IWineD3DDevice::CreateSurface failed. hr = 8876086c
err:ddraw:IDirectDrawImpl_CreateSurface IDirectDrawImpl_CreateNewSurface failed with 8876086c
err:d3d_surface:IWineGDISurfaceImpl_PrivateSetup (0x51d0a38) Overlays not yet supported by GDI surfaces
err:ddraw:IDirectDrawImpl_CreateNewSurface IWineD3DDevice::CreateSurface failed. hr = 8876086c
err:ddraw:IDirectDrawImpl_CreateSurface IDirectDrawImpl_CreateNewSurface failed with 8876086c
err:ddraw:IDirectDrawImpl_QueryInterface (0x51cb0e0)->({aca12120-3356-11d1-8fcf-00c04fc29b4e}, 0x51c1bec): No interface found
err:ddraw:IDirectDrawImpl_QueryInterface (0x51cb0e0)->({aca12120-3356-11d1-8fcf-00c04fc29b4e}, 0x51c1bec): No interface found
err:ddraw:IDirectDrawImpl_QueryInterface (0x51cb0e0)->({aca12120-3356-11d1-8fcf-00c04fc29b4e}, 0x51c1bec): No interface found
err:ddraw:IDirectDrawImpl_QueryInterface (0x51cb0e0)->({aca12120-3356-11d1-8fcf-00c04fc29b4e}, 0x51c1bec): No interface found
err:ddraw:IDirectDrawImpl_QueryInterface (0x51cb0e0)->({aca12120-3356-11d1-8fcf-00c04fc29b4e}, 0x51c1bec): No interface found
err:ddraw:IDirectDrawImpl_QueryInterface (0x51cb0e0)->({aca12120-3356-11d1-8fcf-00c04fc29b4e}, 0x51c1bec): No interface found
err:ddraw:IDirectDrawImpl_QueryInterface (0x51cb0e0)->({aca12120-3356-11d1-8fcf-00c04fc29b4e}, 0x51c1bec): No interface found
err:ddraw:IDirectDrawImpl_QueryInterface (0x51cb0e0)->({aca12120-3356-11d1-8fcf-00c04fc29b4e}, 0x51c1bec): No interface found
err:d3d_surface:IWineGDISurfaceImpl_PrivateSetup (0x51d4c38) Overlays not yet supported by GDI surfaces
err:ddraw:IDirectDrawImpl_CreateNewSurface IWineD3DDevice::CreateSurface failed. hr = 8876086c
err:ddraw:IDirectDrawImpl_CreateSurface IDirectDrawImpl_CreateNewSurface failed with 8876086c
err:d3d_surface:IWineGDISurfaceImpl_PrivateSetup (0x51d4e88) Overlays not yet supported by GDI surfaces
err:ddraw:IDirectDrawImpl_CreateNewSurface IWineD3DDevice::CreateSurface failed. hr = 8876086c
err:ddraw:IDirectDrawImpl_CreateSurface IDirectDrawImpl_CreateNewSurface failed with 8876086c
err:d3d_surface:IWineGDISurfaceImpl_PrivateSetup (0x51d5290) Overlays not yet supported by GDI surfaces
err:ddraw:IDirectDrawImpl_CreateNewSurface IWineD3DDevice::CreateSurface failed. hr = 8876086c
err:ddraw:IDirectDrawImpl_CreateSurface IDirectDrawImpl_CreateNewSurface failed with 8876086c
err:ddraw:IDirectDrawImpl_QueryInterface (0x51cb0e0)->({aca12120-3356-11d1-8fcf-00c04fc29b4e}, 0x51c1bec): No interface found
err:ddraw:IDirectDrawImpl_QueryInterface (0x51cb0e0)->({aca12120-3356-11d1-8fcf-00c04fc29b4e}, 0x51c1bec): No interface found
err:ddraw:IDirectDrawImpl_QueryInterface (0x51cb0e0)->({aca12120-3356-11d1-8fcf-00c04fc29b4e}, 0x51c1bec): No interface found
err:ddraw:IDirectDrawImpl_QueryInterface (0x51cb0e0)->({aca12120-3356-11d1-8fcf-00c04fc29b4e}, 0x51c1bec): No interface found
err:ddraw:IDirectDrawImpl_QueryInterface (0x51cb0e0)->({aca12120-3356-11d1-8fcf-00c04fc29b4e}, 0x51c1bec): No interface found
err:ddraw:IDirectDrawImpl_QueryInterface (0x51cb0e0)->({aca12120-3356-11d1-8fcf-00c04fc29b4e}, 0x51c1bec): No interface found
err:ddraw:IDirectDrawImpl_QueryInterface (0x51cb0e0)->({aca12120-3356-11d1-8fcf-00c04fc29b4e}, 0x51c1bec): No interface found
err:d3d_surface:IWineGDISurfaceImpl_PrivateSetup (0x51d63f8) Overlays not yet supported by GDI surfaces
err:ddraw:IDirectDrawImpl_CreateNewSurface IWineD3DDevice::CreateSurface failed. hr = 8876086c
err:ddraw:IDirectDrawImpl_CreateSurface IDirectDrawImpl_CreateNewSurface failed with 8876086c
err:d3d_surface:IWineGDISurfaceImpl_PrivateSetup (0x51d6878) Overlays not yet supported by GDI surfaces
err:ddraw:IDirectDrawImpl_CreateNewSurface IWineD3DDevice::CreateSurface failed. hr = 8876086c
err:ddraw:IDirectDrawImpl_CreateSurface IDirectDrawImpl_CreateNewSurface failed with 8876086c
err:d3d_surface:IWineGDISurfaceImpl_PrivateSetup (0x51d69d0) Overlays not yet supported by GDI surfaces
err:ddraw:IDirectDrawImpl_CreateNewSurface IWineD3DDevice::CreateSurface failed. hr = 8876086c
err:ddraw:IDirectDrawImpl_CreateSurface IDirectDrawImpl_CreateNewSurface failed with 8876086c
err:ddraw:IDirectDrawImpl_QueryInterface (0x51cb0e0)->({aca12120-3356-11d1-8fcf-00c04fc29b4e}, 0x51c1bec): No interface found
err:ddraw:IDirectDrawImpl_QueryInterface (0x51cb0e0)->({aca12120-3356-11d1-8fcf-00c04fc29b4e}, 0x51c1bec): No interface found
err:ddraw:IDirectDrawImpl_QueryInterface (0x51cb0e0)->({aca12120-3356-11d1-8fcf-00c04fc29b4e}, 0x51c1bec): No interface found
fixme:dsound:DSPROPERTY_Description1 (pPropData=0x33ee54,cbPropData=40,pcbReturned=0x33ee7c) GUID_NULL not implemented!
fixme:d3d:IWineD3DDeviceImpl_Release (0x51cb200) Device released with resources still bound, acceptable but unexpected
fixme:d3d:dumpResources Leftover resource 0x51d69d0 with type 1,WINED3DRTYPE_SURFACE
fixme:d3d:dumpResources Leftover resource 0x51d6878 with type 1,WINED3DRTYPE_SURFACE
fixme:d3d:dumpResources Leftover resource 0x51d63f8 with type 1,WINED3DRTYPE_SURFACE
fixme:d3d:dumpResources Leftover resource 0x51d5290 with type 1,WINED3DRTYPE_SURFACE
fixme:d3d:dumpResources Leftover resource 0x51d4e88 with type 1,WINED3DRTYPE_SURFACE
fixme:d3d:dumpResources Leftover resource 0x51d4c38 with type 1,WINED3DRTYPE_SURFACE
fixme:d3d:dumpResources Leftover resource 0x51d0a38 with type 1,WINED3DRTYPE_SURFACE
fixme:d3d:dumpResources Leftover resource 0x51d07e8 with type 1,WINED3DRTYPE_SURFACE
fixme:d3d:dumpResources Leftover resource 0x51d0598 with type 1,WINED3DRTYPE_SURFACE
fixme:d3d:dumpResources Leftover resource 0x51d0348 with type 1,WINED3DRTYPE_SURFACE
fixme:d3d:dumpResources Leftover resource 0x51d00f8 with type 1,WINED3DRTYPE_SURFACE
fixme:d3d:dumpResources Leftover resource 0x51cfea8 with type 1,WINED3DRTYPE_SURFACE
Initialised SoundManager
fixme:dsound:IDirectSoundBufferImpl_SetFX (0x36555b8,0,(nil),(nil)): stub

```

I think the problem is the very last two lines, since the game now loads the logo and credits in the beginning just fine (sound working and everything).  After that, though, the screen turns white and the game crashes, and it's at that point that the last two lines show up.  Any help would be greatly appreciated.

---

### Post by JPtja on 2009-04-10
Got the same problem here... Also with a intel 945... :P I think Intel just don't work very well in Ubuntu... :( With an other computer (nVidia), the game works. :p

---

