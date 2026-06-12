---
title: "Ubuntu III Complete: problem with intel graphics?"
date: 2011-04-09
forum: Wine
---

### Post by geckon on 2011-04-09
Hi!

I wanted to play Heroes of Might and Magic III Complete on my Ubuntu 10.10 (wine version 1.2.2). I managed to install the game but when I try to run it all I get is a black screen and the following output:
```
fixme:d3d_caps:select_card_intel_mesa Card selection not handled for Mesa Intel driver
fixme:d3d_caps:init_driver_info Unhandled vendor 8086.
fixme:win:EnumDisplayDevicesW ((null),0,0x32f610,0x00000000), stub!
err:ole:CoGetClassObject class {5959df60-2911-11d1-b049-0020af30269a} not registered
err:ole:CoGetClassObject no class object {5959df60-2911-11d1-b049-0020af30269a} could be created for context 0x1
fixme:dsalsa:IDsDriverBufferImpl_SetVolumePan (0x17b598,0x174f90): stub
fixme:dsalsa:IDsDriverBufferImpl_SetVolumePan (0x17b598,0x174f90): stub
fixme:dplay:IDirectPlayLobby3AImpl_RegisterApplication :stub

```

Maybe there is some problem with the graphics card. lspci outputs this:
```
00:02.0 VGA compatible controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)

```

Can anyone tell me what is wrong? I'll appreciate any ideas. Thank you.

---

### Post by Dlambert on 2011-04-09
Configure wine to use opengl?

Reg-edit

---

