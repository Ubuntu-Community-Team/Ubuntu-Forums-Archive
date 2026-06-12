---
title: "Warcraft III - sloooooo"
date: 2009-04-09
forum: Wine
---

### Post by Laeys on 2009-04-09
I just hopped on ubuntu 8.10 due to windows problems so I don't know anything and would appreciate things explained in detail.  

I installed wine 1.1.18 and copied my w3 folder with w3l.exe, I don't have the cd. I have ATI/AMD proprietary FGLRX graphics driver. 

It starts up with no immediate problems but it is slow enough that I wouldn't consider playing as is.  I have some weird patch or something someone gave me in order to play on a different network but I'm hoping this doesn't affect the standard procedure.  I get this before frozen throne starts up:

```
peter@peter-laptop:~/Desktop/Warcraft III/DotA at NTU$ wine w3l.exe --opengl
peter@peter-laptop:~/Desktop/Warcraft III/DotA at NTU$ err:ole:CoCreateInstance apartment not initialised
fixme:advapi:SetSecurityInfo stub
fixme:win:EnumDisplayDevicesW ((null),0,0x33f2cc,0x00000000), stub!
fixme:d3d:test_pbo_functionality >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from Loading the PBO test texture
 @ directx.c / 3882
fixme:win:EnumDisplayDevicesW ((null),0,0x33f6a4,0x00000000), stub!
fixme:d3d:test_pbo_functionality >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from Loading the PBO test texture
 @ directx.c / 3882
fixme:win:EnumDisplayDevicesW ((null),0,0x33f2b0,0x00000000), stub!
fixme:d3d:test_pbo_functionality >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from Loading the PBO test texture
 @ directx.c / 3882
fixme:xrandr:X11DRV_XRandR_SetCurrentMode Cannot change screen BPP from 32 to 16
fixme:d3d:WineD3D_ChoosePixelFormat Add OpenGL context recreation support to SetDepthStencilSurface

```

This means nothing to me.  I think all I did was install wine and delete the movies so maybe I missed a step?  Help please?

---

### Post by khelben1979 on 2009-04-09
> **Laeys said:**
> I just hopped on ubuntu 8.10 due to windows problems so I don't know anything and would appreciate things explained in detail.  

I installed wine 1.1.18 and copied my w3 folder with w3l.exe, I don't have the cd. I have ATI/AMD proprietary FGLRX graphics driver. 

It starts up with no immediate problems but it is slow enough that I wouldn't consider playing as is.  I have some weird patch or something someone gave me in order to play on a different network but I'm hoping this doesn't affect the standard procedure.  I get this before frozen throne starts up:

[CODE]peter@peter-laptop:~/Desktop/Warcraft III/DotA at NTU$ wine w3l.exe --opengl

Try to replace the --opengl parameter with -opengl to see if it get's better.

---

### Post by Laeys on 2009-04-09
I'm amazed at how big a difference such a small change made; thanks a lot!

---

### Post by hikaricore on 2009-04-09
Just another example to remember, a typo can make or break you in a command line world.

---

### Post by khelben1979 on 2009-04-09
> **Laeys said:**
> I'm amazed at how big a difference such a small change made; thanks a lot!

Glad that it worked! Is it playable now?

---

### Post by anjilslaire on 2009-04-09
Just checking in. Are the single-player story cutscenes playable ingame in WC3 now? Last I tried/checked, you had to watch them manually, which broke the atmosphere a bit for me :(

If its fixed, I'll install it again and get back into the game.

Thanks, and sorry for thread-jacking; seeing this made me remember this issue ;)

---

