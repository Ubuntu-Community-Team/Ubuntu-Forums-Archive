---
title: "wine + eve online crashes"
date: 2009-03-12
forum: Wine
---

### Post by AthlonMDK on 2009-03-12
Hi

tuesday the new expansion for eve online was launched since then it is unplayable. I run even and when i am out of station it randomly crashes.

It gives the following output:
> 
darkstar@Athlon-DS:/usr/local/games/EVE$ wine eve.exe 
err:ole:CoGetClassObject class {9a5ea990-3034-4d6f-9128-01f3c61022bc} not registered
err:ole:CoGetClassObject no class object {9a5ea990-3034-4d6f-9128-01f3c61022bc} could be created for context 0x1
fixme:heap:HeapSetInformation 0x8d0000 0 0x33fc70 4
err:threadpool:iocp_poller NtRemoveIoCompletion failed: 0xc0000008

and when it crashes it gives:
> 
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0xf490f80) : pBox=(nil) stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0xf491070) : pBox=(nil) stub
fixme:d3d_texture:basetexture_apply_state_changes Unrecognized or unsupported D3DSAMP_MINFILTER value 2 D3DSAMP_MIPFILTER value 3
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0xf18f0b0) : pBox=(nil) stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0xf18f0b0) : pBox=(nil) stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0xf18f148) : pBox=(nil) stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0xf18f148) : pBox=(nil) stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0xf18f1e0) : pBox=(nil) stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0xf18f1e0) : pBox=(nil) stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0xf1972a0) : pBox=(nil) stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0xf1972a0) : pBox=(nil) stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0xf197358) : pBox=(nil) stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0xf197358) : pBox=(nil) stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0xf197838) : pBox=(nil) stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0xf197838) : pBox=(nil) stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0xf197a18) : pBox=(nil) stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0xf197a18) : pBox=(nil) stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0xf197b38) : pBox=(nil) stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0xf197b38) : pBox=(nil) stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0xf197c28) : pBox=(nil) stub
fixme:d3d_texture:basetexture_apply_state_changes Unrecognized or unsupported D3DSAMP_MINFILTER value 2 D3DSAMP_MIPFILTER value 3
wine: Unhandled page fault on read access to 0x0000006c at address 0x1005d3dd (thread 0019), starting debugger...
wineserver crashed, please enable coredumps (ulimit -c unlimited) and restart.



I tried wine 1.1.6 and 1.1.2 still same issue. I tried nvidia driver 1.77 and 1.80 both from ubuntu depository and with both same issue. Before tuesday i played eve with the CCP Linux installer and worked perfectly.

Other games (native linux) play perfect no issues, only with this game.

user.reg:

[Software\\Wine\\Debug] 1236715349
"DirectDrawRenderer"="opengl"
"OffscreenRenderingMode"="fbo"
"PixelShaderMode"="enabled"
"VertexShaderMode"="hardware"
"VideoMemorySize"="640"

My PC:

AMD 4600+ EE
4 GB of memory
8800 GT 640 MB

Does anyone know a solution?

Problem seems to be like:
[http://www.eveonline.com/ingameboard.asp?a=topic&threadID=1020885](http://www.eveonline.com/ingameboard.asp?a=topic&threadID=1020885)

---

