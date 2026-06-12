---
title: "WoW Error #132 - wine complains about GDI32.dll"
date: 2009-04-04
forum: Wine
---

### Post by Lego Dragon Rider on 2009-04-04
I don't know if this is a WoW problem or a wine problem, hence the long title. ;)

I looked for other posts on the subject of Error #132 and none solved my problem. 

Here's what I did:

I copied my WoW install from a Vista 32 bit partition. This is what I get when I run it: ( Note the second-to-last line )

```
$ wine WoW.exe

fixme:advapi:SetSecurityInfo stub
archive Data\enUS\patch-enUS.MPQ opened
archive Data\patch.MPQ opened
archive Data\enUS\patch-enUS-2.MPQ opened
archive Data\patch-2.MPQ opened
archive Data\expansion.MPQ opened
archive Data\lichking.MPQ opened
archive Data\common.MPQ opened
archive Data\common-2.MPQ opened
archive Data\enUS\locale-enUS.MPQ opened
archive Data\enUS\speech-enUS.MPQ opened
archive Data\enUS\expansion-locale-enUS.MPQ opened
archive Data\enUS\lichking-locale-enUS.MPQ opened
archive Data\enUS\expansion-speech-enUS.MPQ opened
archive Data\enUS\lichking-speech-enUS.MPQ opened
fixme:powrprof:DllMain (0x7d330000, 1, (nil)) not fully implemented
fixme:ntdll:NtPowerInformation Unimplemented NtPowerInformation action: 11
fixme:powrprof:DllMain (0x7d330000, 0, (nil)) not fully implemented
fixme:win:EnumDisplayDevicesW ((null),0,0x39edbc,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x39ea7c,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),1,0x39ea7c,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x39ea7c,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),1,0x39ea7c,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x39e890,0x00000000), stub!
wine: Call from 0x13d42ad to unimplemented function GDI32.dll.GdiEntry1, aborting
fixme:dbghelp:dump_system_info fill in CPU vendorID and feature set
```This leads me to suspect that WoW is trying to use GDI and failing. I tried replacing the wine gdi32.dll with a Vista gdi32.dll but no luck.

I get the exact same results under different graphics modes ( d3d, opengl, shaders on/off ) and the following windows modes:

2008, Vista, 2003, XP, 2000, ME, 98

Haven't tried 95 and lower.

Wine version is 1.0.

WowError log and a screenshot of the alert box are attached.

Thanks! :D

---

### Post by NightMKoder on 2009-04-04
Update your wine. (Latest is 1.1.18) There's a sticky up top on how to get the latest development release. Also check the appdb, they will usually have instructions on how to get something to work (overrides and whatnot).

---

### Post by Lego Dragon Rider on 2009-04-04
OK, I updated wine to 1.1.18, and I still get the error.

Couldn't find anything about it on AppDB so I made a new comment. Still waiting for a workaround.

---

### Post by NightMKoder on 2009-04-04
Then you must have installed native ddraw/d3d. Make sure that your native override list is clean of d3d8/d3d9.

---

### Post by Lego Dragon Rider on 2009-04-04
That worked! :D Thank you! I am so happy now. :D

---

