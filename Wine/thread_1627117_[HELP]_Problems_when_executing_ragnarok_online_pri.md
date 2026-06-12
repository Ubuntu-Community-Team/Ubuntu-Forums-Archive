---
title: "[HELP] Problems when executing ragnarok online private server with wine."
date: 2010-11-21
forum: Wine
---

### Post by glory90 on 2010-11-21
Hi.. i have this error in terminal when executing a ragnarok online with wine in ubuntu 10.10 and the game only show a white screen but the game sound still there. 

> fixme:shdocvw:PersistStorage_InitNew (0x161728)->(0x47fec0)
fixme:urlmon:URLMoniker_BindToObject use running object table
fixme:shdocvw:bind_to_object BindToObject failed: 80004005
feathree@feathree:~/Games/1MalaysiaRO/RO$ fixme:dsalsa:IDsDriverBufferImpl_SetVolumePan (0x1affa0,0x1aff10): stub
fixme:dsalsa:IDsDriverBufferImpl_SetVolumePan (0x1affa0,0x1aff10): stub
fixme:d3d_caps:select_card_intel_mesa Card selection not handled for Mesa Intel driver
fixme:d3d_caps:init_driver_info Unhandled vendor 8086.
fixme:win:EnumDisplayDevicesW ((null),0,0x33f2c4,0x00000000), stub!
fixme:x11drv:X11DRV_desktop_SetCurrentMode Cannot change screen BPP from 32 to 16
fixme:d3d:swapchain_init Add OpenGL context recreation support to context_validate_onscreen_formats
fixme:d3d_surface:surface_download_data Read back converted textures unsupported, format=WINED3DFMT_B5G6R5_UNORM
fixme:d3d_surface:surface_download_data Read back converted textures unsupported, format=WINED3DFMT_B5G6R5_UNORM
fixme:d3d_surface:surface_download_data Read back converted textures unsupported, format=WINED3DFMT_B5G6R5_UNORM
fixme:dinput:SysMouseAImpl_Acquire Clipping cursor to (0,0)-(800,600)
can anyone help me solve it. i already spend days searching for a solution in google and for your infomation i am using acer 3684, intel celeron m 1.86ghz, mobile intel 940 gml express chipset.

---

### Post by WienerWuerstel on 2010-11-21
The Problem is probably your Intel Graphics Chip. Intel is not the best Solution for Gaming (Especially if you keep in Mind that the Open Source Drivers make it even worse)

---

