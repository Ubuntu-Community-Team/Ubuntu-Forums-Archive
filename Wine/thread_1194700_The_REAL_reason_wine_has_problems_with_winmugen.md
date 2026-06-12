---
title: "The REAL reason wine has problems with winmugen"
date: 2009-06-22
forum: Wine
---

### Post by sonicfactor on 2009-06-22
Ok i Tried Carbkings idea and it would of work but i got these errors:
-----------------
ALSA lib seq_hw.c:457:sad:snd_seq_hw_open) open /dev/snd/seq failed: No such file or directory
fixme:win:EnumDisplayDevicesW ((null),0,0x32ea68,0x00000000), stub!
fixme:d3d:IWineD3DDeviceImpl_Release (0x12b4f:cool: Device released with resources still bound, acceptable but unexpected
fixme:d3d:dumpResources Leftover resource 0x12bb70 with type 1,WINED3DRTYPE_SURFACE
Loading button config for P1 joystick win.
Loading button config for P2 joystick win.
fixme:d3d:IWineD3DDeviceImpl_Release (0x12dbe0) Device released with resources still bound, acceptable but unexpected
fixme:d3d:dumpResources Leftover resource 0x12b950 with type 1,WINED3DRTYPE_SURFACE
Initializing keyboard.
Initializing sound...ok
Initializing graphics.
fixme:dsalsa:IDsDriverBufferImpl_SetVolumePan (0x132838,0x32f120): stub
Killed

----------------
So how is this fixed? and i guessing these are the reasons why mugen.cfg wouldnt work.

---

### Post by sonicfactor on 2009-06-23
New Update i got it to work but the music isnt working and some of the screens doesnt fit to the mugen screen.And heres what i got from using carbkings idea from the old thread:
---------------------------------
ALSA lib seq_hw.c:457:(snd_seq_hw_open) open /dev/snd/seq failed: No such file or directory
fixme:win:EnumDisplayDevicesW ((null),0,0x32ea68,0x00000000), stub!
fixme:d3d:IWineD3DDeviceImpl_Release (0x12b4d0) Device released with resources still bound, acceptable but unexpected
fixme:d3d:dumpResources Leftover resource 0x12bb48 with type 1,WINED3DRTYPE_SURFACE
Loading button config for P1 joystick win.
Loading button config for P2 joystick win.
fixme:d3d:IWineD3DDeviceImpl_Release (0x12dbd8) Device released with resources still bound, acceptable but unexpected
fixme:d3d:dumpResources Leftover resource 0x12e3a0 with type 1,WINED3DRTYPE_SURFACE
Initializing keyboard.
Initializing sound...ok
Initializing graphics.
fixme:dsalsa:IDsDriverBufferImpl_SetVolumePan (0x132478,0x32f120): stub
fixme:dsalsa:IDsDriverBufferImpl_SetVolumePan (0x132478,0x32d6f4): stub
fixme:dsalsa:IDsDriverBufferImpl_SetVolumePan (0x132478,0x32d6b4): stub
fixme:dsalsa:IDsDriverBufferImpl_SetVolumePan (0x132478,0x32ac68): stub
fixme:dsalsa:IDsDriverBufferImpl_SetVolumePan (0x132478,0x32d6f4): stub
fixme:dsalsa:IDsDriverBufferImpl_SetVolumePan (0x132478,0x32d6b4): stub
M.U.G.E.N test ver 2002.04.14                                   (c)2002 Elecbyte

BG load time: 0.0 ms
Player load time: 0.0 ms, 0.0 ms
Total load time: 0.0 ms
Pal groups in background: 0

fixme:dsalsa:IDsDriverBufferImpl_SetVolumePan (0x132478,0x32f478): stub
-------------------------------------
i suppose no one knows what to do up to this point i guess but eh

---

