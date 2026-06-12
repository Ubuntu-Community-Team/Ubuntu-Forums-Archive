---
title: "Halo: Combat Evolved Fatal Error"
date: 2009-10-11
forum: Wine
---

### Post by apb2390 on 2009-10-11
Hey,

Running wine 1.1.3 here.  A friend gave me the installed files for Halo: CE on a flash drive. I copied it onto my Windows computer, worked fine. I just ran the haloce.exe file and it ran like a charm. However, when I tried to run it under Wine on my primary Ubuntu box, wine gave me a fatal error.
```
A problem Occured initializing DirectInput.
```In an error box. I ran it through the Terminal, and here's the output:
```
File '/home/andrew/.local/share/applications/wine-extension-wxpr.desktop' contains invalid MIME type 'Wax Preset' that contains invalid characters
fixme:mixer:ALSA_MixerInit No master control found on MPU-401 UART, disabling mixer
fixme:win:EnumDisplayDevicesW ((null),0,0x33d358,0x00000000), stub!
err:ole:COMPOBJ_DllList_Add couldn't load in-process dll L"dxdiagn.dll"
err:ole:CoGetClassObject no class object {a65b8071-3bfe-4213-9a5b-491da4461ca7} could be created for context 0x1
fixme:win:EnumDisplayDevicesW ((null),0,0x33d5a8,0x00000000), stub!

```And it brings up the fatal error box. I'm a bit confused, as the wine app database gives it s "Platinum" rating. Any help?

Thanks in advance, apb

---

### Post by Meow27 on 2009-10-11
1.1.3 or 1.1.30?

---

