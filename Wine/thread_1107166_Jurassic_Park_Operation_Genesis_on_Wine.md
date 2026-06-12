---
title: "Jurassic Park Operation Genesis on Wine"
date: 2009-03-26
forum: Wine
---

### Post by pipposanta on 2009-03-26
Hi,
I installed Jurassic Park Operation Genesis on Ubuntu 8.10 with Wine but when I start it displays only colored boxes on the screen and the only way to quit is Ctrl+Alt+Backspace. I tried this game because it was one of the few old games I have and it was classified on the AppDB as Platinum.
I use wine version 1.0.1 on a Atom 1.6ghz with 1gb RAM and Intel GMA 950 without proprietary drivers.
I don't know how to post terminal output because the application runs in fullscreen mode and blocks all the system!!
I don't have library overrides.

EDIT:
Here is the terminal output:
```
fixme:win:EnumDisplayDevicesW ((null),0,0x32f93c,0x00000000), stub!
fixme:d3d:WineD3D_ChoosePixelFormat Add OpenGL context recreation support to SetDepthStencilSurface
err:d3d:WineD3D_ChoosePixelFormat Can't find a suitable iPixelFormat
fixme:d3d:WineD3D_ChoosePixelFormat Add OpenGL context recreation support to SetDepthStencilSurface
fixme:dinput:SysMouseAImpl_Acquire Clipping cursor to (0,0)-(640,480)
fixme:d3d:IWineD3DVolumeImpl_LockBox (0xa4ffb78) : pBox=(nil) stub
fixme:d3d:IWineD3DVolumeImpl_LockBox (0xa4ffc30) : pBox=(nil) stub
fixme:d3d:IWineD3DVolumeImpl_LockBox (0xa4ffce8) : pBox=(nil) stub
fixme:d3d:IWineD3DVolumeImpl_LockBox (0xa4ffda0) : pBox=(nil) stub
fixme:d3d:IWineD3DVolumeImpl_LockBox (0xa4ffe70) : pBox=(nil) stub
fixme:d3d:IWineD3DVolumeImpl_LockBox (0xa4fff28) : pBox=(nil) stub
fixme:d3d:IWineD3DVolumeImpl_LockBox (0xa2de348) : pBox=(nil) stub
fixme:d3d:IWineD3DVolumeImpl_LockBox (0xa5f7e40) : pBox=(nil) stub
fixme:d3d:IWineD3DVolumeImpl_LockBox (0xa7124e0) : pBox=(nil) stub
fixme:d3d:IWineD3DVolumeImpl_LockBox (0xa5f7ef8) : pBox=(nil) stub
fixme:d3d:IWineD3DVolumeImpl_LockBox (0xa2ded20) : pBox=(nil) stub
fixme:d3d:IWineD3DVolumeImpl_LockBox (0xa712598) : pBox=(nil) stub
fixme:d3d:IWineD3DVolumeImpl_LockBox (0xa2df710) : pBox=(nil) stub
fixme:d3d:IWineD3DVolumeImpl_LockBox (0xa2df7c8) : pBox=(nil) stub
fixme:d3d:IWineD3DVolumeImpl_LockBox (0xa2df880) : pBox=(nil) stub
fixme:d3d:IWineD3DVolumeImpl_LockBox (0xa2df938) : pBox=(nil) stub
err:d3d_surface:IWineD3DSurfaceImpl_LoadLocation Reading back render target but SFLAG_INDRAWABLE not set
err:d3d_surface:IWineD3DSurfaceImpl_LoadLocation Reading back render target but SFLAG_INDRAWABLE not set
err:d3d_surface:IWineD3DSurfaceImpl_LoadLocation Reading back render target but SFLAG_INDRAWABLE not set
err:d3d_surface:IWineD3DSurfaceImpl_LoadLocation Reading back render target but SFLAG_INDRAWABLE not set
err:d3d_surface:IWineD3DSurfaceImpl_LoadLocation Reading back render target but SFLAG_INDRAWABLE not set
err:d3d_surface:IWineD3DSurfaceImpl_LoadLocation Reading back render target but SFLAG_INDRAWABLE not set
err:d3d_surface:IWineD3DSurfaceImpl_LoadLocation Reading back render target but SFLAG_INDRAWABLE not set
err:d3d_surface:IWineD3DSurfaceImpl_LoadLocation Reading back render target but SFLAG_INDRAWABLE not set
err:d3d_surface:IWineD3DSurfaceImpl_LoadLocation Reading back render target but SFLAG_INDRAWABLE not set
err:d3d_surface:IWineD3DSurfaceImpl_LoadLocation Reading back render target but SFLAG_INDRAWABLE not set
Mesa 7.2 implementation error: i915_program_error: Exceeded max nr indirect texture lookups
Please report at bugzilla.freedesktop.org
```

Thanks in advance for the help!!

---

