---
title: "Porblems with Eve Online"
date: 2010-03-21
forum: Wine
---

### Post by xtjacob on 2010-03-21
I'm trying to install Eve in wine by following this guide: [http://wiki.eveonline.com/en/wiki/Install_EVE_on_linux_with_wine](http://wiki.eveonline.com/en/wiki/Install_EVE_on_linux_with_wine) I'm currently on the part where I have to patch it. When I try to start it to get the number it shows the splash screen, then the screen goes dark and it crashes. The output from the terminal is: ```
jacob@jacob-desktop:~/Desktop/wine-1.1.39$ wine '/home/jacob/.wine/drive_c/Program Files/CCP/EVE/eve.exe' 
err:ole:CoGetClassObject class {9a5ea990-3034-4d6f-9128-01f3c61022bc} not registered
err:ole:CoGetClassObject no class object {9a5ea990-3034-4d6f-9128-01f3c61022bc} could be created for context 0x1
fixme:heap:HeapSetInformation 0x7c9000 0 0x33fc6c 4
Allocating 16 x 16 radeon RBO (pitch 16)
Allocating 16 x 16 radeon RBO (pitch 16)
Allocating 16 x 16 radeon RBO (pitch 16)
Allocating 16 x 16 radeon RBO (pitch 16)
Allocating 16 x 16 radeon RBO (pitch 16)
Allocating 16 x 16 radeon RBO (pitch 16)
Allocating 16 x 16 radeon RBO (pitch 16)
Allocating 16 x 16 radeon RBO (pitch 16)
Allocating 16 x 16 radeon RBO (pitch 16)
Allocating 16 x 16 radeon RBO (pitch 16)
Allocating 16 x 16 radeon RBO (pitch 16)
Allocating 16 x 16 radeon RBO (pitch 16)
Allocating 16 x 16 radeon RBO (pitch 16)
Allocating 16 x 16 radeon RBO (pitch 16)
Allocating 16 x 16 radeon RBO (pitch 16)
Allocating 16 x 16 radeon RBO (pitch 16)
Allocating 16 x 16 radeon RBO (pitch 16)
Allocating 16 x 16 radeon RBO (pitch 16)
Allocating 16 x 16 radeon RBO (pitch 16)
Allocating 16 x 16 radeon RBO (pitch 16)
fixme:win:EnumDisplayDevicesW ((null),0,0x338d9c,0x00000000), stub!
err:threadpool:iocp_poller NtRemoveIoCompletion failed: 0xc0000008
err:threadpool:iocp_poller NtRemoveIoCompletion failed: 0xc0000008
err:threadpool:iocp_poller NtRemoveIoCompletion failed: 0xc0000008
err:threadpool:iocp_poller NtRemoveIoCompletion failed: 0xc0000008
err:threadpool:iocp_poller NtRemoveIoCompletion failed: 0xc0000008
err:threadpool:iocp_poller NtRemoveIoCompletion failed: 0xc0000008
err:threadpool:iocp_poller NtRemoveIoCompletion failed: 0xc0000008
err:threadpool:iocp_poller NtRemoveIoCompletion failed: 0xc0000008
err:threadpool:iocp_poller NtRemoveIoCompletion failed: 0xc0000008
err:threadpool:iocp_poller NtRemoveIoCompletion failed: 0xc0000008
fixme:wtsapi:WTSRegisterSessionNotification Stub 0x30078 0x00000000
fixme:dsalsa:IDsDriverBufferImpl_SetVolumePan (0x8240f70,0x8241480): stub
jacob@jacob-desktop:~/Desktop/wine-1.1.39$ fixme:imm:ImmDisableTextFrameService Stub
fixme:imm:ImmReleaseContext (0x30078, 0x16a630): stub
fixme:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glTexImage2D @ surface.c / 602
fixme:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glCompressedTexSubImage2DARB @ surface.c / 532
fixme:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glTexImage2D @ surface.c / 602
fixme:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glCompressedTexSubImage2DARB @ surface.c / 532
fixme:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glTexImage2D @ surface.c / 602
fixme:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glCompressedTexSubImage2DARB @ surface.c / 532
fixme:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glTexImage2D @ surface.c / 602
fixme:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glCompressedTexSubImage2DARB @ surface.c / 532
fixme:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glTexImage2D @ surface.c / 602
fixme:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glCompressedTexSubImage2DARB @ surface.c / 532
fixme:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glTexImage2D @ surface.c / 602
fixme:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glCompressedTexSubImage2DARB @ surface.c / 532
fixme:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glTexImage2D @ surface.c / 602
fixme:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glCompressedTexSubImage2DARB @ surface.c / 532
fixme:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glTexImage2D @ surface.c / 602
fixme:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glCompressedTexSubImage2DARB @ surface.c / 532
fixme:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glTexImage2D @ surface.c / 602
fixme:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glCompressedTexSubImage2DARB @ surface.c / 532
fixme:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glTexImage2D @ surface.c / 602
fixme:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glCompressedTexSubImage2DARB @ surface.c / 532
fixme:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glTexImage2D @ surface.c / 602
fixme:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glCompressedTexSubImage2DARB @ surface.c / 532
fixme:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glTexImage2D @ surface.c / 602
fixme:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glCompressedTexSubImage2DARB @ surface.c / 532
fixme:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glTexImage2D @ surface.c / 602
fixme:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glCompressedTexSubImage2DARB @ surface.c / 532
r300VertexProgUpdateParams:Params exhausted
```
I have ubuntu 9.10 with wine 1.1.39 installed and my kernel version is 2.6.33.1. Also my graphics card is an ATI X600 with the open source driver.

---

