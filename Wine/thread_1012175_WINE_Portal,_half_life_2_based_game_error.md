---
title: "WINE: Portal, half life 2 based game error"
date: 2008-12-15
forum: Wine
---

### Post by Questioneer on 2008-12-15
Hello-
I've installed Steam and The Orange Box using this tutorial:
[http://www.linux-gamers.net/modules/wiwimod/index.php?page=HOWTO+Steam](http://www.linux-gamers.net/modules/wiwimod/index.php?page=HOWTO+Steam)

I just finished beating Half Life 2, Episode 1, and Episode 2. All worked fine, except that I had to put "shadows" and "shader details" to 'low' in the game, or else I would see crazy textures on the ground and in the sky.

I just started playing Portal. In the first chapter, The character GLaDOS says "portal opening in 3... 2... 1..." As soon as the door opens, Everything looks like the below image.
[IMG]http://img60.imageshack.us/img60/7625/screenshotfm3.png[/IMG]


*Important Note: I also saw this strange texture as my screen at rare points in Half Life 2/EP1/EP2.
For example, I was never able to see the gman speaking, but instead I just saw this strange texture. I was also not able to view large gas fires, and a few other rare effects.
As soon as I would turn my screen away in Half Life 2, I would be able to see the game again.

However, in Portal, as soon as the first door opens, I can only see this texture. As I move around, it changes gradients and colors.

Here's the command I'm launching Portal with, and it is basically the same command I launched HL2/EP1/EP2 with.
```
 WINEDEBUG=fixme-all wine C:/Program\ Files/Steam/Steam.exe -width 1280 -height 1024 -applaunch 420 -dxlevel 81 -novid -window -silent
```
ONLY dxlevel 81 and 80 work on my PC. 70 and 90 do not. 


Here's the most terminal output I can get:

```
err:d3d:getColorBits Unsupported format: WINED3DFMT_A32B32G32R32F
err:d3d:IWineD3DImpl_IsPixelFormatCompatibleWithRenderFmt Unable to check compatibility for Format=WINED3DFMT_A32B32G32R32F
err:d3d:getColorBits Unsupported format: WINED3DFMT_A32B32G32R32F
err:d3d:IWineD3DImpl_IsPixelFormatCompatibleWithRenderFmt Unable to check compatibility for Format=WINED3DFMT_A32B32G32R32F
...(more of the same)
err:d3d:CheckTextureCapability Unhandled format=unrecognized
err:d3d:CheckTextureCapability Unhandled format=unrecognized
err:d3d:CheckTextureCapability Unhandled format=unrecognized
err:d3d:CheckTextureCapability Unhandled format=unrecognized
...(more of the same)
err:d3d:WineD3D_ChoosePixelFormat Can't find a suitable iPixelFormat
err:shell:SHGetFileInfoW pidl is null!
err:d3d:WineD3D_ChoosePixelFormat Can't find a suitable iPixelFormat
```

I've tried running this under Windows XP and Windows Vista. Both work for HL2, but neither works for Portal.

I've also tried skipping to later chapters in the game, but in almost every later chapter all I can see is this strange texture.

Can anyone help?
Thanks,
Questioneer

---

### Post by Questioneer on 2008-12-15
Also: I have an ATi X600 with the proprietary drivers enabled.

---

### Post by doorknob60 on 2008-12-15
If it happens in XP and Vista too, It's most likely a hardware problem.

---

