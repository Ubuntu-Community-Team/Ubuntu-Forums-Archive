---
title: "[Lucid]CoD4:MW launch problem[Wine1.1.42]"
date: 2010-04-11
forum: Wine
---

### Post by kacperpl1 on 2010-04-11
I'm trying to launch the game on my ubuntu desktop but dunno what should i install/patch to get it working in newest wine. The game is installed on my ntfs-3g partition. My hardware is more than enough to play the game, i've installed nvidia 185 drivers, i have generic-pae kernel. I have used winetricks to install d3dx9 and dotnets, corefonts. I get output like this in console:
> fixme:win:EnumDisplayDevicesW ((null),0,0x32f674,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x32f1f4,0x00000000), stub!
fixme:d3d:debug_d3dformat Unrecognized 1094800211 (as fourcc: SSAA) WINED3DFORMAT!
fixme:d3d:getFormatDescEntry Can't find format unrecognized(1094800211) in the format lookup table
fixme:d3d:swapchain_init Add OpenGL context recreation support to context_validate_onscreen_formats
err:ntdll:RtlpWaitForCriticalSection section 0x110060 "heap.c: main process heap section" wait timed out in thread 0021, blocked by 0009, retrying (60 sec)

And additionaly i get the following error
> Fastfile for zone 'common_mp' is corrupt or unreadable.
Does newest wine needs 3dmark patch that some 2 years old tutorials talk about? Anyone playing CoD4 on lucid?

---

### Post by AllRadioisDead on 2010-04-11
Check wineHQ.

---

### Post by kacperpl1 on 2010-04-11
Sure, i checked it the first time i thought about installing the game and it seemed like it should work out of box for lucid.

---

