---
title: "PWI and a former Macbook"
date: 2009-05-07
forum: Wine
---

### Post by FlamingIfrit on 2009-05-07
So, I have done everything I have seen on any forums to try to get Perfect World International to run on my Macbook which now runs Ubuntu 9.04, but to no avail. I can get the patcher to start, and after I click "start" it will go to the loading screen, and even occasionally it will make it to the Message screen before the login. But, once it gets that far my computer crashes to login. It shows a black screen with blue binary all over it, and then it suddenly pops back up at the ubuntu login screen. If anyone knows what I did wrong, please tell me.

What I did was: 
1)I Downloaded Wine and installed it
2)Downloaded and ran winetricks
3) Got DirectX9.0c
4)configured my registry in Regedit to have more entries under the appropriate Direct3d folder under wine (DirectDrawRenderer, Nonpower2mode, OffscreenRenderingMode, PixelShaderMode, RenderTargetLockMode) with the appropriate data values (opengl, repack, fbo, enabled, and auto respectively)
5) and then I ran the game, which should have worked, but to no avail.

---

### Post by asdfoo on 2009-05-07
> **FlamingIfrit said:**
> So, I have done everything I have seen on any forums to try to get Perfect World International to run on my Macbook which now runs Ubuntu 9.04, but to no avail. I can get the patcher to start, and after I click "start" it will go to the loading screen, and even occasionally it will make it to the Message screen before the login. But, once it gets that far my computer crashes to login. It shows a black screen with blue binary all over it, and then it suddenly pops back up at the ubuntu login screen. If anyone knows what I did wrong, please tell me.

What I did was: 
1)I Downloaded Wine and installed it
2)Downloaded and ran winetricks
3) Got DirectX9.0c
4)configured my registry in Regedit to have more entries under the appropriate Direct3d folder under wine (DirectDrawRenderer, Nonpower2mode, OffscreenRenderingMode, PixelShaderMode, RenderTargetLockMode) with the appropriate data values (opengl, repack, fbo, enabled, and auto respectively)
5) and then I ran the game, which should have worked, but to no avail.

Which video card and drivers?

---

### Post by FlamingIfrit on 2009-05-08
Hey, so I actually got this Macbook for free, which is why i am not 100% sure what is in it, but I am pretty sure it is the following:
Intel Graphics Media Accelerator 950

And I have downloaded the latest drivers for it.

---

