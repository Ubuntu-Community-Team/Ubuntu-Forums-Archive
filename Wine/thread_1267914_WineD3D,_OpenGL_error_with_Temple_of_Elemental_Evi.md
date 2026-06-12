---
title: "WineD3D, OpenGL error with Temple of Elemental Evil"
date: 2009-09-16
forum: Wine
---

### Post by aniruddha on 2009-09-16
Evening all. I am currently trying to run an old-ish rpg from Troika: Temple of Elemental Evil. As per the AppDB, this has a pretty high rating for most systems. However, on my Ubuntu 9.04 (Jaunty) 64bit system I get the following error:

fixme:win:EnumDisplayDevicesW ((null),0,0x32f60c,0x00000000), stub!
fixme:d3d:WineD3D_ChoosePixelFormat Add OpenGL context recreation support to SetDepthStencilSurface
fixme:d3d8:IDirect3DDevice8Impl_GetTexture Call to get texture  (0) failed ((nil))
fixme:d3d8:IDirect3DDevice8Impl_GetTexture Call to get texture  (1) failed ((nil))
fixme:d3d8:IDirect3DDevice8Impl_GetTexture Call to get texture  (2) failed ((nil))
fixme:d3d8:IDirect3DDevice8Impl_GetTexture Call to get texture  (3) failed ((nil))

Further system details:

NVIDIA GeForce 9500M G with driver version 185.18.36, Jaunty 64bit, Wine 1.1.29. All Hardware option (pixel shader etc.) are enable, I am using ALSA drivers and there are no native over-rides being used in the libraries.

Any ideas? Any help would be greatly appreciated guys. Thanks a ton...

---

