---
title: "Wine errors"
date: 2010-02-10
forum: Wine
---

### Post by Ubu8.04 on 2010-02-10
don't know where to get the open-gl files to make this work...

look

fixme:reg:GetNativeSystemInfo (0x32fd48) using GetSystemInfo()
fixme:win:EnumDisplayDevicesW ((null),0,0x32f5fc,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),1,0x32f5fc,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x32e468,0x00000000), stub!
err:ddraw:IDirectDrawImpl_QueryInterface (0x133248) The App is requesting a D3D device, but a non-OpenGL surface type was choosen. Prepare for trouble!
err:ddraw:IDirectDrawImpl_QueryInterface  (0x133248) You may want to contact wine-devel for help
err:ddraw:IDirectDrawSurfaceImpl_QueryInterface No interface
fixme:d3d:WineD3D_ChoosePixelFormat Add OpenGL context recreation support to SetDepthStencilSurface
err:d3d:WineD3D_ChoosePixelFormat Can't find a suitable iPixelFormat
fixme:d3d:WineD3D_ChoosePixelFormat Add OpenGL context recreation support to SetDepthStencilSurface
Segmentation fault


so wine doesn't have the right open gl something but don't know what to do can someone help me ?

---

### Post by Ubu8.04 on 2010-02-10
but i think it could be a driver issue cuz i just switched this comp from vista to ubuntu and don't have any of the drivers installed but maybe this worked...

---

### Post by hikaricore on 2010-02-10
I hate to be so blunt, but what in the hell are you talking about?

You're going to have to tell us what you're trying to do and what kinda hardware you have before anyone can even consider assisting you.

---

### Post by Ubu8.04 on 2010-02-10
uhmm sorry dude i have an intel m940 card er something like that..its a sucky onboard card..

I am trying to run Tibia. 

When i used to run it in windows I had to download open-gl updates so thats why i knew i had to do something with open-gl plus it said that.. I just want to run that program

Thanks

---

### Post by Ubu8.04 on 2010-02-10
its a intel 945gm

are there drivers for it for ubuntu this is like my second day with ubuntu

---

### Post by Ubu8.04 on 2010-02-11
I am trying to run a game called Tibia on Ubuntu 8.04. From other threads it looked as if the best way to do it was to download the Windows version and then use wine to open it. The issue that i am running into is this:

fixme:reg:GetNativeSystemInfo (0x32fd48) using GetSystemInfo()
fixme:win:EnumDisplayDevicesW ((null),0,0x32f5fc,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),1,0x32f5fc,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x32e778,0x00000000), stub!
fixme:d3d:WineD3D_ChoosePixelFormat Add OpenGL context recreation support to SetDepthStencilSurface
err:d3d:WineD3D_ChoosePixelFormat Can't find a suitable iPixelFormat
fixme:d3d:WineD3D_ChoosePixelFormat Add OpenGL context recreation support to SetDepthStencilSurface
fixme:d3d:WineD3D_ChoosePixelFormat Add OpenGL context recreation support to SetDepthStencilSurface
err:d3d:WineD3D_ChoosePixelFormat Can't find a suitable iPixelFormat
fixme:d3d:WineD3D_ChoosePixelFormat Add OpenGL context recreation support to SetDepthStencilSurface
Segmentation fault

When i try to run it with 
wine Tibia.exe engine 0that is what happens but if i try to run it with

wine Tibia.exe engine 1
then an error pops up and says chose i different graphics or video mode something like that.

I have an intel 945gm graphics card. Do I need to install drivers for it for Ubuntu 8.04?

Not sure what to do from here let me know what I need to do.

Thanks,

---

### Post by cariboo on 2010-02-11
Please don't create multiple threads on the same subject, I have merged your two threads.

---

