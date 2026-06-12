---
title: "Natty unhandled page fault"
date: 2011-04-13
forum: Wine
---

### Post by briancb on 2011-04-13
I dual boot 10.10 & 11.04 on the same 64 bit computer. When running programs in wine 10.10 it works perfectly. 

When using 11.04 I get Exception Raised: Unhandled page fault on read access to 0x00000000 at address 0xf7509270.

Just run from terminal and got:


brian@brian-O-E-M:~$ '/home/brian/.wine/dosdevices/c:/Program Files/Sid Meier'\''s Civilization V/CivilizationV.exe' 
fixme:ntoskrnl:ExInitializeNPagedLookasideList stub: 0x549db8, (nil), (nil), 0, 256, 1431259202, 0
fixme:ntoskrnl:KeInitializeEvent stub: 0x549e98 1 0
wine: Call from 0x7b8399d2 to unimplemented function hal.dll.KeQueryPerformanceCounter, aborting
wine: Unimplemented function hal.dll.KeQueryPerformanceCounter called at address 0x7b8399d2 (thread 0017), starting debugger...
wine: Call from 0x7b8399d2 to unimplemented function hal.dll.KeQueryPerformanceCounter, aborting
wine: Call from 0x7b8399d2 to unimplemented function hal.dll.KeQueryPerformanceCounter, aborting
fixme:ole:CoInitializeSecurity (0x413ea8,-1,(nil),(nil),1,3,(nil),72,(nil)) - stub!
err:ole:CoGetClassObject class {24e669e1-e90f-4595-a012-b0fd3ccc5c5a} not registered
err:ole:CoGetClassObject no class object {24e669e1-e90f-4595-a012-b0fd3ccc5c5a} could be created for context 0x1
fixme:win:EnumDisplayDevicesW ((null),0,0x328dd4,0x00000000), stub!
Error: API mismatch: the NVIDIA kernel module has version 270.41.03,
but this NVIDIA driver component has version 270.18.  Please make
sure that the kernel module and all NVIDIA driver components
have the same version.
err:winediag:X11DRV_WineGL_InitOpenglInfo Direct rendering is disabled, most likely your OpenGL drivers haven't been installed correctly
Error: API mismatch: the NVIDIA kernel module has version 270.41.03,
but this NVIDIA driver component has version 270.18.  Please make
sure that the kernel module and all NVIDIA driver components
have the same version.
wine: Unhandled page fault on read access to 0x00000000 at address 0xf750e270 (thread 0009), starting debugger...
brian@brian-O-E-M:~$

---

### Post by cogadh on 2011-04-13
It looks like your video card drivers have a problem which is disabling direct rendering. You should update/reinstall the drivers.

---

### Post by briancb on 2011-04-13
Yes I realized this so I did a complete reinstall with a newly downloaded Natty. Solved the problem.

---

