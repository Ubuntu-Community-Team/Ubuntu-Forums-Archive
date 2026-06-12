---
title: "Civ V refuses to start"
date: 2011-02-19
forum: Wine
---

### Post by mail2345 on 2011-02-19
When I try to start Civ V, it takes a while to load, and then a black screen which goes away. There is a lingering, defunct application bar entry.

I have installed vcrun2008, dx3dx9, devenum.
OS set as XP(tried changing it, no difference).

System Info:
Maverick Meerkat 
Wine 1.3.14
GeForce 6150SE nForce 430 with proprietary drivers.

Console:
```

fixme:heap:HeapSetInformation 0x110000 0 0x32fe08 4
fixme:system:SystemParametersInfoW Unimplemented action: 55 (SPI_SETMOUSEKEYS)
fixme:system:SystemParametersInfoW Unimplemented action: 59 (SPI_SETSTICKYKEYS)
fixme:heap:HeapSetInformation 0x8611000 0 0x32fda8 4
fixme:win:EnumDisplayDevicesW ((null),0,0x32f280,0x00000000), stub!
fixme:wtsapi:WTSRegisterSessionNotification Stub 0x30020 0x00000000
fixme:heap:HeapSetInformation 0xb6b3000 0 0x32fc78 4
fixme:win:EnumDisplayDevicesW ((null),0,0x32f1f8,0x00000000), stub!
fixme:d3d:swapchain_init The application requested more than one back buffer, this is not properly supported.
Please configure the application to use double buffering (1 back buffer) if possible.
fixme:d3d:swapchain_init Add OpenGL context recreation support to context_validate_onscreen_formats
err:ole:CoGetClassObject class {b87beb7b-8d29-423f-ae4d-6582c10175ac} not registered
err:ole:CoGetClassObject no class object {b87beb7b-8d29-423f-ae4d-6582c10175ac} could be created for context 0x1
fixme:dsalsa:IDsDriverBufferImpl_SetVolumePan (0x817da68,0x817df68): stub
fixme:dsalsa:IDsDriverBufferImpl_SetVolumePan (0x817da68,0x817df68): stub
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
err:ole:create_server class {6d18ad12-bde3-4393-b311-099c346e6df9} not registered
err:ole:CoGetClassObject no class object {6d18ad12-bde3-4393-b311-099c346e6df9} could be created for context 0x4
Checking availability
Initializing the GameSpy Core
Starting up GS Mod Cloud. 
err:mmtime:TIME_MMTimeStop Timer still active?!

```

---

### Post by r2ramos on 2011-05-20
Having the same problem


fixme:gstreamer:Gstreamer_transform_Cleanup 0x7d699e8 stub
fixme:gstreamer:Gstreamer_transform_Cleanup 0x7d4ab48 stub
mmap() failed: No se pudo asignar memoria
mmap() failed: No se pudo asignar memoria
mmap() failed: No se pudo asignar memoria
mmap() failed: No se pudo asignar memoria
mmap() failed: No se pudo asignar memoria
mmap() failed: No se pudo asignar memoria
mmap() failed: No se pudo asignar memoria
mmap() failed: No se pudo asignar memoria
mmap() failed: No se pudo asignar memoria
mmap() failed: No se pudo asignar memoria
err:wave:wodOpen Error open: Error de entrada/salida
fixme:dsound:mmErr Unknown MMSYS error 3
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
err:ole:create_server class {6d18ad12-bde3-4393-b311-099c346e6df9} not registered
err:ole:CoGetClassObject no class object {6d18ad12-bde3-4393-b311-099c346e6df9} could be created for context 0x4
Checking availability
Initializing the GameSpy Core
Starting up GS Mod Cloud. 


...and then it crashes

---

