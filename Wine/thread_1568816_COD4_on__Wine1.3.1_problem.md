---
title: "COD4 on  Wine1.3.1 problem"
date: 2010-09-05
forum: Wine
---

### Post by uceee on 2010-09-05
[COLOR=Red]UBUNTU 9.1[/COLOR]

/media/1844ED5644ED36E2/Program Files/Activision/Call of Duty 4 - Modern Warfare$ sudo wine iw3mp.exe 
wine: /home/sts/.wine is not owned by you
sts@ubuntu:/media/1844ED5644ED36E2/Program Files/Activision/Call of Duty 4 - Modern Warfare$ sudo wine iw3mp.exe 
wine: /home/sts/.wine is not owned by you
sts@ubuntu:/media/1844ED5644ED36E2/Program Files/Activision/Call of Duty 4 - Modern Warfare$ wine iw3mp.exe 
fixme:win:EnumDisplayDevicesW ((null),0,0x32f63c,0x00000000), stub!
fixme:dsalsa:IDsDriverBufferImpl_SetVolumePan (0x167470,0x1673b8): stub
fixme:dsalsa:IDsDriverBufferImpl_SetVolumePan (0x167470,0x1673b8): stub
fixme:dsalsa:IDsDriverBufferImpl_SetVolumePan (0x1339c0,0x1802f0): stub
fixme:win:EnumDisplayDevicesW ((null),0,0x32f5bc,0x00000000), stub!
fixme:d3d:debug_d3dformat Unrecognized 0x41415353 (as fourcc: SSAA) WINED3DFORMAT!
fixme:d3d:getFormatDescEntry Can't find format unrecognized (0x41415353) in the format lookup table
fixme:d3d:swapchain_init Add OpenGL context recreation support to context_validate_onscreen_formats
fixme:d3d:query_init Event query: Unimplemented, but pretending to be supported.
fixme:d3d:query_init Event query: Unimplemented, but pretending to be supported.
fixme:d3d:query_init Event query: Unimplemented, but pretending to be supported.
fixme:d3d:query_init Event query: Unimplemented, but pretending to be supported.
fixme:d3d:query_init Event query: Unimplemented, but pretending to be supported.
fixme:d3d:query_init Event query: Unimplemented, but pretending to be supported.
fixme:d3d:query_init Event query: Unimplemented, but pretending to be supported.
fixme:d3d:query_init Event query: Unimplemented, but pretending to be supported.
fixme:d3d:query_init Event query: Unimplemented, but pretending to be supported.
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x18526328) : pBox=(nil) stub
fixme:win:EnumDisplayDevicesW ((null),0,0x32f450,0x00000000), stub!
err:d3d:resource_init Out of adapter memory
Terminated

---

### Post by MisterLambda on 2010-09-08
Remember never to run WINE with sudo!

---

