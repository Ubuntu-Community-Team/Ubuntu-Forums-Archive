---
title: "Maplestory in wine, an idea."
date: 2009-12-03
forum: Wine
---

### Post by AllRadioisDead on 2009-12-03
Hi everyone. We all know that Maplestory currently doesn't run in wine. The official client uses Hackshield, a hacking prevention system that won't run in wine. Private servers also do not work, but I have an idea.
 
Currently, the problem with private servers consists of a blank screen after seeing the Nexon/Wizet logo and a crash.
It spits out these errors:
```
fixme:d3d:IWineD3DImpl_CreateDevice (0x4043a730) Incomplete stub for d3d8
fixme:d3d_caps:IDirect3D8Impl_FillGLCaps found GL_VERSION  ("1.5.3 NVIDIA
71.74")->(0x00471c06)
fixme:d3d_caps:IDirect3D8Impl_FillGLCaps found GL_RENDERER ("GeForce2
MX/AGP/SSE2")->(0x0250)
fixme:d3d:IDirect3DDevice8Impl_SetRenderState (0x4043bdd0)->(40,0) not handled yet
fixme:d3d:IDirect3DDevice8Impl_SetRenderState (0x4043bdd0)->(128,0) not handled yet
fixme:d3d:IDirect3DDevice8Impl_SetRenderState (0x4043bdd0)->(129,0) not handled yet
fixme:d3d:IDirect3DDevice8Impl_SetRenderState (0x4043bdd0)->(130,0) not handled yet
fixme:d3d:IDirect3DDevice8Impl_SetRenderState (0x4043bdd0)->(131,0) not handled yet
fixme:d3d:IDirect3DDevice8Impl_SetRenderState (0x4043bdd0)->(132,0) not handled yet
fixme:d3d:IDirect3DDevice8Impl_SetRenderState (0x4043bdd0)->(133,0) not handled yet
fixme:d3d:IDirect3DDevice8Impl_SetRenderState (0x4043bdd0)->(134,0) not handled yet
fixme:d3d:IDirect3DDevice8Impl_SetRenderState (0x4043bdd0)->(135,0) not handled yet
fixme:d3d:IDirect3DDevice8Impl_SetRenderState (0x4043bdd0)->(156,0) not handled yet
fixme:d3d:IDirect3DDevice8Impl_SetRenderState (0x4043bdd0)->(161,1) not handled yet
fixme:d3d:IDirect3DDevice8Impl_SetRenderState (0x4043bdd0)->(162,-1) not handled yet
fixme:d3d:IDirect3DDevice8Impl_SetRenderState (0x4043bdd0)->(163,0) not handled yet
fixme:d3d:IDirect3DDevice8Impl_SetRenderState (0x4043bdd0)->(164,1065353216) not
handled yet
fixme:d3d:IDirect3DDevice8Impl_SetRenderState (0x4043bdd0)->(165,1) not handled yet
fixme:d3d:IDirect3DDevice8Impl_SetRenderState (0x4043bdd0)->(172,3) not handled yet
fixme:d3d:IDirect3DDevice8Impl_SetRenderState (0x4043bdd0)->(173,1) not handled yet
fixme:d3d:IDirect3DDevice8Impl_GetDeviceCaps (0x4043bdd0) : stub, calling
idirect3d for now
err:msacm:MSACM_GetRegistryKey No alias needed for registry entry
fixme:imm:ImmGetDefaultIMEWnd (0x10024 - (nil) 0x4041c100 ): semi-stub
fixme:imm:ImmGetContext (0x10024): stub
fixme:imm:ImmReleaseContext (0x10024, 0x53b46598): stub
fixme:imm:ImmGetContext (0x10024): stub
fixme:imm:ImmReleaseContext (0x10024, 0x53b46598): stub
fixme:imm:ImmGetContext (0x10024): stub
fixme:imm:ImmReleaseContext (0x10024, 0x53b46598): stub

```
Games such as Diablo and Worms armageddon suffer from similar problems. A bug is reported here: [http://bugs.winehq.org/show_bug.cgi?id=2082](http://bugs.winehq.org/show_bug.cgi?id=2082)
A patch was also provided to remedy the issue:
[http://bugs.winehq.org/show_bug.cgi?id=2082#c51](http://bugs.winehq.org/show_bug.cgi?id=2082#c51)
 
If someone could compile wine with the patch, install directx 9 in wine via winetricks, I have a strong feeling a private server will be good run. That's the first step, if we can accomplish this we can pressure Nexon to switch to an alternative means to protect their game.
Set the DirectDrawRenderer registry key to "gdi".

[HKEY_CURRENT_USER\Software\Wine\AppDefaults\wa.exe\Direct3D]
DirectDrawRenderer = "gdi"
 
 
 
tldr; Can someone please patch wine with the above link, install directx, and try running a private server. Post results please. As much as I'd love to, I don't have ubuntu installed on this machine and I won't get access to an ubuntu machine for a while. Thanks.

---

### Post by SmittyJensen on 2009-12-03
i'll try and get back to you in an hour or two.

---

### Post by AllRadioisDead on 2009-12-03
Sweet, thanks. Best of luck.

---

### Post by SmittyJensen on 2009-12-04
just an fyi:

I've applied the patch to wine 1.1.33 successfully and am building the deb(s) now to test. if all goes well (i.e., the patch worked), then i'll upload the deb(s) for others to use.

---

### Post by AllRadioisDead on 2009-12-04
> **SmittyJensen said:**
> just an fyi:
 
I've applied the patch to wine 1.1.33 successfully and am building the deb(s) now to test. if all goes well (i.e., the patch worked), then i'll upload the deb(s) for others to use.
 Great news, have you been able to test the patch with Maplestory yet?
In the worst case scenerio that it doesn't work, this should still be pleasant news for worms armageddon players.

---

### Post by SmittyJensen on 2009-12-05
> **ihermit said:**
> Great news, have you been able to test the patch with Maplestory yet?
In the worst case scenerio that it doesn't work, this should still be pleasant news for worms armageddon players.
It didn't work so I deleted the debs. :(

when running maplestory private server exe (such as EternalMS.exe) it didn't launch, it just hanged. as in, nothing popped up, no window, nothing, and no terminal output whatsoever, except sometimes it would spam something about mmap (which is related to sound it seems).

it wasn't hard, just took quite a while to compile. so if anyone really wants the debs ill be glad to rebuild them.

---

### Post by AllRadioisDead on 2009-12-05
That's unfortunate, thanks for trying. Weird that there was no terminal output, usually it spits out errors about ddraw.

---

### Post by SmittyJensen on 2009-12-05
> **ihermit said:**
> That's unfortunate, thanks for trying. Weird that there was no terminal output, usually it spits out errors about ddraw.
Yes, definitely weird. maybe i just built it wrong. i welcome someone else to try it.

---

### Post by AllRadioisDead on 2009-12-05
Hmm, do you think you can try one more time using this ddraw.dll?
[http://rapidshare.com/files/269050151/ddraw.dll_for_wine_1.1.27.bz2](http://rapidshare.com/files/269050151/ddraw.dll_for_wine_1.1.27.bz2)
I believe that was required for worms armageddon to work.

---

### Post by SmittyJensen on 2009-12-05
> **ihermit said:**
> Hmm, do you think you can try one more time using this ddraw.dll?
[http://rapidshare.com/files/269050151/ddraw.dll_for_wine_1.1.27.bz2](http://rapidshare.com/files/269050151/ddraw.dll_for_wine_1.1.27.bz2)
I believe that was required for worms armageddon to work.
Fine.

This time I'll upload the debs anyway. :P

---

### Post by AllRadioisDead on 2009-12-05
> **SmittyJensen said:**
> Fine.
 
This time I'll upload the debs anyway. :P
 Thanks, you may wish to make a new thread for the Deb files for the worms people.

---

