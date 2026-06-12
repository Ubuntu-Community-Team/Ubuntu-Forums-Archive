---
title: "EVE online with Newest WINE and drivers running REALLY SLOW"
date: 2010-09-10
forum: Wine
---

### Post by jhonnyas on 2010-09-10
Ok so here's my problem:
I ve installed a Clean Ubuntu 10.04 64 bit, but when i tried to install nvidia driver 256 from nvidia.com the fracking nouveau came up (seriously why integrate such crap in and enable by default?) 
Anyways after hours of googling I finally managed to permanetly disable nouveau, which FINALLY allowed me to install nvidia driver 256 from their website, I read that 195 can cause GPU burnouts, and i was concerned especially since i have a 9800M GS in my notebook. 

Anyways, frustration after frustration, i finally managed to get NVIDIA propertiary drivers intalled and intsalled the newest wine 1.3 through repo. 

Downloaded EVE online offline installer, complete clean fresh reinstall, added mscorefonts and d3dx9 through winetricks. 

When I thought finally its up and running, I launch the game and after 5 minutes the EULA comes up. WTH? After 10 minutes of waiting i finally managed to open settings just to see that everything is set to high, and EVE recognizes my 9800M GS as a Geforce FX5600 ...

Here is the terminal output:


/.wine/drive_c/Program Files/CCP/EVE$ wine eve.exe
fixme:gameux:GameExplorerImpl_VerifyAccess stub
fixme:heap:HeapSetInformation 0x480000 0 0x33fc40 4
EVE Client version 6.3 build 177290 starting  22:25:37
Multi-Language System: Client using language [EN]
err:winediag:X11DRV_WineGL_InitOpenglInfo The Mesa OpenGL driver is using software rendering, most likely your OpenGL drivers haven't been installed correctly
fixme:d3d_caps:wined3d_guess_card No card selector available for GL vendor 4 and card vendor 0000.
fixme:win:EnumDisplayDevicesW ((null),0,0x338cfc,0x00000000), stub!
EVE Client version 6.3 build 177290 started  22:25:40
Starting services
Replacing service 'machoNet' with 'eveMachoNet'
Service machoNet: 0.001s
Replacing service 'dataconfig' with 'eveDataconfig'
Service dataconfig: 0.007s
Replacing service 'photo' with 'evePhoto'
Replacing service 'objectCaching' with 'eveObjectCaching'
Service objectCaching: 0.000s
Replacing service 'browserHostManager' with 'eveBrowserHostManager'
Replacing service 'calendar' with 'eveCalendar'
Service addressbook: 0.000s
Service counter: 0.000s
Service clientStatsSvc: 0.000s
Service invCache: 0.000s
Service godma: 0.000s
Service photo: 0.000s
Service mailSvc: 0.000s
Service notificationSvc: 0.000s
Service LSC: 0.000s
Service patch: 0.000s
Service inv: 0.000s
Service michelle: 0.000s
Service pwn: 0.000s
Service focus: 0.000s
Service debug: 0.000s
Service jumpQueue: 0.000s
Service scanSvc: 0.000s
Service browserHostManager: 0.000s
Service jumpMonitor: 0.000s
Service calendar: 0.000s
Starting services - Done
Service moonScan: 0.000s
Service gameui: 0.000s
Replacing service 'device' with 'eveDevice'
Service device: 0.001s
Service make: 0.000s
Service event: 0.000s
Service font: 0.005s
Service registry: 0.000s
Replacing service 'audio' with 'eveAudio'
fixme:wtsapi:WTSRegisterSessionNotification Stub 0x20074 0x00000000
fixme:dsalsa:IDsDriverBufferImpl_SetVolumePan (0x218220,0x21fcb8): stub
Service audio: 0.519s
fixme:imm:ImmDisableTextFrameService Stub
fixme:imm:ImmReleaseContext (0x20074, 0x13f9c8): stub
[email]jhon@ASUS-NEXUS-NOTEBOOK:~/.wine[/email]/drive_c/Program Files/CCP/EVE$ Service log: 0.000s
Replacing service 'cmd' with 'eveCmd'
Service ime: 0.103s
Service cmd: 0.003s
Service loading: 0.000s
Replacing service 'connection' with 'eveConnection'
Replacing service 'vivox' with 'evevivox'
Service connection: 0.000s
Service damage: 0.000s
Service logger: 0.001s
Service vivox: 0.000s
Service ownerprimer: 0.000s
Service petition: 0.000s
Service fonts: 0.009s
Service ui: 0.000s
Service form: 0.000s
Service window: 0.000s
Service z: 0.000s
Service war: 0.000s
Service consider: 0.000s
Service webtools: 0.000s
Service draw: 0.000s
Service browserCache: 0.001s
fixme:imm:NotifyIME NI_CLOSECANDIDATE
Replacing service 'jukebox' with 'eveJukebox'
Service jukebox: 0.001s
err:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glTexImage2D @ surface.c / 860
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glCompressedTexSubImage2DARB @ surface.c / 763
err:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glTexImage2D @ surface.c / 860
err:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glTexImage2D @ surface.c / 860
err:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glTexImage2D @ surface.c / 860
err:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glTexImage2D @ surface.c / 860
err:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glTexImage2D @ surface.c / 860
err:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glTexImage2D @ surface.c / 860
err:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glTexImage2D @ surface.c / 860
err:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glTexImage2D @ surface.c / 860
err:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glTexImage2D @ surface.c / 860
err:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glTexImage2D @ surface.c / 860
err:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glTexImage2D @ surface.c / 860
err:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glTexImage2D @ surface.c / 860
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glCompressedTexSubImage2DARB @ surface.c / 763
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glCompressedTexSubImage2DARB @ surface.c / 763
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glCompressedTexSubImage2DARB @ surface.c / 763
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glCompressedTexSubImage2DARB @ surface.c / 763
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glCompressedTexSubImage2DARB @ surface.c / 763
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glCompressedTexSubImage2DARB @ surface.c / 763
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glCompressedTexSubImage2DARB @ surface.c / 763
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glCompressedTexSubImage2DARB @ surface.c / 763
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glCompressedTexSubImage2DARB @ surface.c / 763
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glCompressedTexSubImage2DARB @ surface.c / 763
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glCompressedTexSubImage2DARB @ surface.c / 763
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glCompressedTexSubImage2DARB @ surface.c / 763
err:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glTexImage2D @ surface.c / 860
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glCompressedTexSubImage2DARB @ surface.c / 763
err:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glTexImage2D @ surface.c / 860
err:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glTexImage2D @ surface.c / 860
err:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glTexImage2D @ surface.c / 860
err:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glTexImage2D @ surface.c / 860
err:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glTexImage2D @ surface.c / 860
err:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glTexImage2D @ surface.c / 860
err:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glTexImage2D @ surface.c / 860
err:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glTexImage2D @ surface.c / 860
err:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glTexImage2D @ surface.c / 860
err:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glTexImage2D @ surface.c / 860
err:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glTexImage2D @ surface.c / 860
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glCompressedTexSubImage2DARB @ surface.c / 763
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glCompressedTexSubImage2DARB @ surface.c / 763
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glCompressedTexSubImage2DARB @ surface.c / 763
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glCompressedTexSubImage2DARB @ surface.c / 763
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glCompressedTexSubImage2DARB @ surface.c / 763
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glCompressedTexSubImage2DARB @ surface.c / 763
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glCompressedTexSubImage2DARB @ surface.c / 763
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glCompressedTexSubImage2DARB @ surface.c / 763
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glCompressedTexSubImage2DARB @ surface.c / 763
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glCompressedTexSubImage2DARB @ surface.c / 763
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glCompressedTexSubImage2DARB @ surface.c / 763
err:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glTexImage2D @ surface.c / 860
err:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glTexImage2D @ surface.c / 860
err:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glTexImage2D @ surface.c / 860
err:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glTexImage2D @ surface.c / 860
err:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glTexImage2D @ surface.c / 860
err:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glTexImage2D @ surface.c / 860
err:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glTexImage2D @ surface.c / 860
err:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glTexImage2D @ surface.c / 860
err:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glTexImage2D @ surface.c / 860
err:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glTexImage2D @ surface.c / 860
err:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glTexImage2D @ surface.c / 860
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glCompressedTexSubImage2DARB @ surface.c / 763
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glCompressedTexSubImage2DARB @ surface.c / 763
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glCompressedTexSubImage2DARB @ surface.c / 763
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glCompressedTexSubImage2DARB @ surface.c / 763
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glCompressedTexSubImage2DARB @ surface.c / 763
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glCompressedTexSubImage2DARB @ surface.c / 763
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glCompressedTexSubImage2DARB @ surface.c / 763
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glCompressedTexSubImage2DARB @ surface.c / 763
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glCompressedTexSubImage2DARB @ surface.c / 763
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glCompressedTexSubImage2DARB @ surface.c / 763
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glCompressedTexSubImage2DARB @ surface.c / 763
err:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glTexImage2D @ surface.c / 860
err:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glTexImage2D @ surface.c / 860
err:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glTexImage2D @ surface.c / 860
err:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glTexImage2D @ surface.c / 860
err:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glTexImage2D @ surface.c / 860
err:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glTexImage2D @ surface.c / 860
err:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glTexImage2D @ surface.c / 860
err:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glTexImage2D @ surface.c / 860
err:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glTexImage2D @ surface.c / 860
err:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glTexImage2D @ surface.c / 860
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glCompressedTexSubImage2DARB @ surface.c / 763
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glCompressedTexSubImage2DARB @ surface.c / 763
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glCompressedTexSubImage2DARB @ surface.c / 763
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glCompressedTexSubImage2DARB @ surface.c / 763
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glCompressedTexSubImage2DARB @ surface.c / 763
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glCompressedTexSubImage2DARB @ surface.c / 763
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glCompressedTexSubImage2DARB @ surface.c / 763
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glCompressedTexSubImage2DARB @ surface.c / 763
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glCompressedTexSubImage2DARB @ surface.c / 763
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glCompressedTexSubImage2DARB @ surface.c / 763
err:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glTexImage2D @ surface.c / 860
err:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glTexImage2D @ surface.c / 860
err:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glTexImage2D @ surface.c / 860
err:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glTexImage2D @ surface.c / 860
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glCompressedTexSubImage2DARB @ surface.c / 763
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glCompressedTexSubImage2DARB @ surface.c / 763
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glCompressedTexSubImage2DARB @ surface.c / 763
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glCompressedTexSubImage2DARB @ surface.c / 763
err:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glTexImage2D @ surface.c / 860
err:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glTexImage2D @ surface.c / 860
err:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glTexImage2D @ surface.c / 860
err:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glTexImage2D @ surface.c / 860
err:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glTexImage2D @ surface.c / 860
err:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glTexImage2D @ surface.c / 860
err:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glTexImage2D @ surface.c / 860
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glCompressedTexSubImage2DARB @ surface.c / 763
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glCompressedTexSubImage2DARB @ surface.c / 763
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glCompressedTexSubImage2DARB @ surface.c / 763
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glCompressedTexSubImage2DARB @ surface.c / 763
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glCompressedTexSubImage2DARB @ surface.c / 763
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glCompressedTexSubImage2DARB @ surface.c / 763
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glCompressedTexSubImage2DARB @ surface.c / 763
err:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glTexImage2D @ surface.c / 860
err:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glTexImage2D @ surface.c / 860
err:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glTexImage2D @ surface.c / 860
err:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glTexImage2D @ surface.c / 860
err:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glTexImage2D @ surface.c / 860
err:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glTexImage2D @ surface.c / 860
err:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glTexImage2D @ surface.c / 860
err:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glTexImage2D @ surface.c / 860
err:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glTexImage2D @ surface.c / 860
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glCompressedTexSubImage2DARB @ surface.c / 763
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glCompressedTexSubImage2DARB @ surface.c / 763
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glCompressedTexSubImage2DARB @ surface.c / 763
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glCompressedTexSubImage2DARB @ surface.c / 763
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glCompressedTexSubImage2DARB @ surface.c / 763
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glCompressedTexSubImage2DARB @ surface.c / 763
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glCompressedTexSubImage2DARB @ surface.c / 763
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glCompressedTexSubImage2DARB @ surface.c / 763
err:d3d_surface:surface_upload_data >>>>>>>>>>>>>>>>> GL_INVALID_ENUM (0x500) from glCompressedTexSubImage2DARB @ surface.c / 763

IF ANYbody can make any sense of this, or any suggestions, please, i am all ears

---

