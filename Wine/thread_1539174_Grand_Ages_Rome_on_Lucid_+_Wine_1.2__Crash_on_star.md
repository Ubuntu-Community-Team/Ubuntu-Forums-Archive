---
title: "Grand Ages Rome on Lucid + Wine 1.2 : Crash on startup"
date: 2010-07-26
forum: Wine
---

### Post by RabidFX on 2010-07-26
Hello there fellow Ubuntu users !

As the title suggests, I've been trying to launch "Grand Ages: Rome" with the new Wine 1.2, hoping that it would provide the fixes required for the game to play. 

Sadly, the game refuses to launch, and simply crash, along with an annoying resolution reset to 1024x780 if I launch it in the same X server than the one I'm normally working in.

My graphic card is a Nvidia 8500 GT, run with proprietary drivers.

When launched from a terminal, the output is the following :

```

fixme:win:EnumDisplayDevicesW ((null),0,0x32f194,0x00000000), stub!
err:ole:CoGetClassObject class {9a5ea990-3034-4d6f-9128-01f3c61022bc} not registered
err:ole:CoGetClassObject no class object {9a5ea990-3034-4d6f-9128-01f3c61022bc} could be created for context 0x1
fixme:imagehlp:ImageLoad (C:\Program Files\Kalypso\GrandAgesRome\Rome.exe, (null)): stub
fixme:advapi:RegisterTraceGuidsW (0x3c24d0, 0x3cd6e8, {7c830ece-5fb3-417a-a1bd-508f45277356}, 1, 0x32f614, (null), (null), 0x3cd6f0,)
fixme:win:EnumDisplayDevicesW ((null),0,0x32edbc,0x00000000), stub!
fixme:d3d:debug_d3dformat Unrecognized 1515474505 (as fourcc: INTZ) WINED3DFORMAT!
fixme:d3d:getFormatDescEntry Can't find format unrecognized(1515474505) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 875710020 (as fourcc: DF24) WINED3DFORMAT!
fixme:d3d:getFormatDescEntry Can't find format unrecognized(875710020) in the format lookup table
fixme:wbemprox:wbem_locator_ConnectServer 0x1363d8, L"\\\\.\\root\\cimv2", (null), (null), (null), 0x00000000, (null), (nil), 0x32f48c)
fixme:win:EnumDisplayDevicesW ((null),0,0x32ed5c,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x32e8e4,0x00000000), stub!
err:x11settings:X11DRV_ChangeDisplaySettingsEx No matching mode found 1024x768x32 @60! (XRandR)
fixme:d3d:swapchain_init Add OpenGL context recreation support to context_validate_onscreen_formats
fixme:d3d:debug_d3dformat Unrecognized 1515474505 (as fourcc: INTZ) WINED3DFORMAT!
fixme:d3d:getFormatDescEntry Can't find format unrecognized(1515474505) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 875710020 (as fourcc: DF24) WINED3DFORMAT!
fixme:d3d:getFormatDescEntry Can't find format unrecognized(875710020) in the format lookup table
fixme:d3dx:D3DXCreateEffectCompiler (0x9dc8e48, 2904, 0x32f258, 0x32f244, 0, 0x32f23c, 0x32f234): stub
fixme:d3dx:D3DXCreateEffectCompiler (0x9dc8e98, 581, 0x32f258, 0x32f244, 0, 0x32f23c, 0x32f234): stub
fixme:faultrep:ReportFault 0x32f094 0x0 stub

```

Any idea on what the error may be or how to fix it ?

---

### Post by asdfoo on 2010-07-26
> **RabidFX said:**
> Hello there fellow Ubuntu users !

As the title suggests, I've been trying to launch "Grand Ages: Rome" with the new Wine 1.2, hoping that it would provide the fixes required for the game to play. 

Sadly, the game refuses to launch, and simply crash, along with an annoying resolution reset to 1024x780 if I launch it in the same X server than the one I'm normally working in.

My graphic card is a Nvidia 8500 GT, run with proprietary drivers.

When launched from a terminal, the output is the following :

```

fixme:win:EnumDisplayDevicesW ((null),0,0x32f194,0x00000000), stub!
err:ole:CoGetClassObject class {9a5ea990-3034-4d6f-9128-01f3c61022bc} not registered
err:ole:CoGetClassObject no class object {9a5ea990-3034-4d6f-9128-01f3c61022bc} could be created for context 0x1
fixme:imagehlp:ImageLoad (C:\Program Files\Kalypso\GrandAgesRome\Rome.exe, (null)): stub
fixme:advapi:RegisterTraceGuidsW (0x3c24d0, 0x3cd6e8, {7c830ece-5fb3-417a-a1bd-508f45277356}, 1, 0x32f614, (null), (null), 0x3cd6f0,)
fixme:win:EnumDisplayDevicesW ((null),0,0x32edbc,0x00000000), stub!
fixme:d3d:debug_d3dformat Unrecognized 1515474505 (as fourcc: INTZ) WINED3DFORMAT!
fixme:d3d:getFormatDescEntry Can't find format unrecognized(1515474505) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 875710020 (as fourcc: DF24) WINED3DFORMAT!
fixme:d3d:getFormatDescEntry Can't find format unrecognized(875710020) in the format lookup table
fixme:wbemprox:wbem_locator_ConnectServer 0x1363d8, L"\\\\.\\root\\cimv2", (null), (null), (null), 0x00000000, (null), (nil), 0x32f48c)
fixme:win:EnumDisplayDevicesW ((null),0,0x32ed5c,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x32e8e4,0x00000000), stub!
err:x11settings:X11DRV_ChangeDisplaySettingsEx No matching mode found 1024x768x32 @60! (XRandR)
fixme:d3d:swapchain_init Add OpenGL context recreation support to context_validate_onscreen_formats
fixme:d3d:debug_d3dformat Unrecognized 1515474505 (as fourcc: INTZ) WINED3DFORMAT!
fixme:d3d:getFormatDescEntry Can't find format unrecognized(1515474505) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 875710020 (as fourcc: DF24) WINED3DFORMAT!
fixme:d3d:getFormatDescEntry Can't find format unrecognized(875710020) in the format lookup table
fixme:d3dx:D3DXCreateEffectCompiler (0x9dc8e48, 2904, 0x32f258, 0x32f244, 0, 0x32f23c, 0x32f234): stub
fixme:d3dx:D3DXCreateEffectCompiler (0x9dc8e98, 581, 0x32f258, 0x32f244, 0, 0x32f23c, 0x32f234): stub
fixme:faultrep:ReportFault 0x32f094 0x0 stub

```

Any idea on what the error may be or how to fix it ?

Yeah, looks like you need a native d3dx9_36.dll

```
winetricks d3dx9_36
```

If you don't have winetricks:
wget kegel.com/wine/winetricks
sh winetricks d3dx9_36

---

### Post by RabidFX on 2010-07-27
First of all, thanks a lot, asdfoo !

I obviously made it a step further, as now the game loading screen appears !
I would be curious to know how you spotted that this was a problem of native d3dx9_36.dll in all this mess. 

Problems aren't over thus. Now the games loading screen appears, and after a few minutes, crashes. 
The terminal is flooded with these two lines, repeating several times per second, during all the loading. Then the application crashes.

```

err:d3d:context_apply_draw_buffer >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glDrawBuffers() @ context.c / 1891
err:d3d:context_set_draw_buffer >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glDrawBuffer() @ context.c / 1939

```

Are those symptomatic of the problem, and can it be fixed ?
And if not announcing an imminent crash, these lines spawn so fast that they hide all other terminal output from me, is there a way to avoid this so the real cause of the crash could be revealed ?

---

