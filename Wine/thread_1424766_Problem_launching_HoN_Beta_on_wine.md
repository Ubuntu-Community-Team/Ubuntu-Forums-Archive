---
title: "Problem launching HoN Beta on wine"
date: 2010-03-08
forum: Wine
---

### Post by kacperpl1 on 2010-03-08
My notebook has only GMA950 IGP and for now I cannot play Heroes of Newerth Beta on Linux, it works only on windows because the card misses support for implementation of some GLSL classes. On windows Heroes of newerth uses combined DirectX + OpenGL and the game works. Additionally some users reports that game works better on wine then natively on non nvidia cards. That's why I'm trying to launch the game this way.

First of all i used winetricks to install d3dx9 and vcrun2005 as recommended for this game by appdb.
I'd like to know how can i overcome those errors:
```
fixme:d3d_caps:wined3d_guess_card No card selector available for GL vendor 3 and card vendor 8086.
fixme:win:EnumDisplayDevicesW ((null),0,0x32eba0,0x00000000), stub!
fixme:d3d:WineD3D_ChoosePixelFormat Add OpenGL context recreation support to SetDepthStencilSurface
fixme:d3d:debug_d3dformat Unrecognized 1280070990 (as fourcc: NULL) WINED3DFORMAT!
fixme:d3d:getFormatDescEntry Can't find format unrecognized(1280070990) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 909200449 (as fourcc: AL16) WINED3DFORMAT!
fixme:d3d:getFormatDescEntry Can't find format unrecognized(909200449) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 909201952 (as fourcc:  R16) WINED3DFORMAT!
fixme:d3d:getFormatDescEntry Can't find format unrecognized(909201952) in the format lookup table
i915_program_error: Bad inst->DstReg.Index: 2

```
Those are the errors showing continuously when the game runs. It works but frame rate is about one frame per 10 second. Additionally it have problems with textures on buttons. If someone could help I would really appreciate that.

---

### Post by beastrace91 on 2010-03-08
What Wine version?

~Jeff

---

### Post by kacperpl1 on 2010-03-09
Wine 1.1.40 on lucid

---

### Post by Ferrat on 2010-03-09
My guess would be that the drivers for your card isn't enough, WINE only translates the Windows calls in to Linux ones, you might even be using software render that's the problem I think

---

### Post by asdfoo on 2010-03-09
from the log:

i915_program_error: Bad inst->DstReg.Index: 2

This line is from the video driver indicating a problem.  The only thing you can do is make sure you have the most recent i915 dri driver and if it still occurs look to report the problem to the developers.

---

### Post by kacperpl1 on 2010-03-09
I have the same problem on all versions of mesa I can get(7.7 from lucid repo and 7.9 from xorg-edgers). Is there anyone using GMA950 who can try it?

---

### Post by asdfoo on 2010-03-09
> **kacperpl1 said:**
> I have the same problem on all versions of mesa I can get(7.7 from lucid repo and 7.9 from xorg-edgers). Is there anyone using GMA950 who can try it?

I meant you might have to compile manually, rather than use something from a repo, sometimes the latest updates are not yet released as a version/packaged.

---

### Post by kacperpl1 on 2010-03-10
I'm using xorg-edgers PPA so i think ill get most recent mesa drivers. Additionally i don't like compiling this stuff just to check if it gives me something because it takes hours to compile.

---

### Post by asdfoo on 2010-03-10
> **kacperpl1 said:**
> I'm using xorg-edgers PPA so i think ill get most recent mesa drivers. Additionally i don't like compiling this stuff just to check if it gives me something because it takes hours to compile.


ok, then you should take what you have and report the problem to mesa if it hasn't been reported already.

---

### Post by mnml on 2010-05-23
same problem when I try to start eve with the same graphic card

---

