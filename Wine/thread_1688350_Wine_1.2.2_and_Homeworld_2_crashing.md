---
title: "Wine 1.2.2 and Homeworld 2 crashing"
date: 2011-02-15
forum: Wine
---

### Post by zyrex on 2011-02-15
Hi,

Ok im pretty new to wine.  I have installed a fresh install of wine, and winetricks.  Notepad runs smoothly no hiccups.

I then installed steam works hundreds and so does CS-source, but when running Homeworld 2 i constantly get the following:

fixme:ntoskrnl:KeInitializeMutex stub: 0x1112d0, 1
fixme:ntoskrnl:KeInitializeMutex stub: 0x1112f0, 1
fixme:ntoskrnl:KeInitializeEvent stub: 0x111320 1 0
fixme:win:EnumDisplayDevicesW ((null),0,0x32f0b0,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x32e934,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x32e9e4,0x00000000), stub!
fixme:mixer:ALSA_MixerInit No master control found on MPU-401 UART, disabling mixer
fixme:devenum: DEVENUM_ICreateDevEnum_CreateClassEnumerator Category {cc7bfb41-f175-11d1-a392-00e0291f3959} not found
fixme:devenum: DEVENUM_ICreateDevEnum_CreateClassEnumerator Category {cc7bfb46-f175-11d1-a392-00e0291f3959} not found

tried running with the -nopbuffer and noVDM and video errors switch...  nothing still crashes after a black screen.  Tried to run it with  -opengl  same problem. Its also set to run in an emulated window of  1152x860.

can someone help me here as to where i can fix this and get it running?

running Ubuntu 10.04

---

### Post by zyrex on 2011-02-17
ok after messing with a few direct x overrides.. the output of the terminal reads as follows:

fixme:ntoskrnl:KeInitializeMutex stub: 0x1112d0, 1
fixme:ntoskrnl:KeInitializeMutex stub: 0x1112f0, 1
fixme:ntoskrnl:KeInitializeEvent stub: 0x111320 1 0
err: ole:COMPOBJ_DllList_Add couldn't load in-process dll L"dxdiagn.dll"
err: ole:CoGetClassObject no class object {a65b8071-3bfe-4213-9a5b-491da4461ca7} could be created for context 0x1
fixme:mixer:ALSA_MixerInit No master control found on MPU-401 UART, disabling mixer
fixme:dsalsa:IDsDriverBufferImpl_SetVolumePan (0x16a228,0x16a148 ): stub
fixme:dbghelp_dwarf:compute_location Only supporting one breg (18 -> 24)


game, still not running, and "$wine dxdiag.exe"  does not open a thing at all....

any ideas?

---

