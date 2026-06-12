---
title: "Photoshop 5.5 used to work, but just stopped working"
date: 2009-03-25
forum: Wine
---

### Post by justanotherhandle on 2009-03-25
I've been using Wine to run photoshop 5.5 (yeah, it's old, but it works for me). It just stopped working as in it won't open the program. But the included ImageReady does still work. The only other program I installed under Wine is NotePad. I've also reinstalled Photoshop just in case that was the problem, but no change. Photoshop still not working.

I have Hardy, Wine 1.0.0, and Photoshop 5.5. 

Opening ImageReady using a terminal:
```
~$ wine .wine/drive_c/Program\ Files/Adobe/Photoshop\ 5.5/ImageReady.exe 
fixme:font:WineEngRemoveFontResourceEx :stub
fixme:shell:IShellLinkA_fnGetPath (0x1da7a0): WIN32_FIND_DATA is not yet filled.
fixme:shell:IShellLinkA_fnGetPath (0x1da7a0): WIN32_FIND_DATA is not yet filled.
fixme:shell:IShellLinkA_fnGetPath (0x1da970): WIN32_FIND_DATA is not yet filled.
fixme:shell:IShellLinkA_fnGetPath (0x1da970): WIN32_FIND_DATA is not yet filled.
fixme:font:WineEngRemoveFontResourceEx :stub
fixme:shell:DllCanUnloadNow stub
```

And then opening the non-working Photoshop:
```
~$ wine .wine/drive_c/Program\ Files/Adobe/Photoshop\ 5.5/Photoshp.exe 
fixme:msg:pack_message msg 14 (WM_ERASEBKGND) not supported yet
fixme:win:EnumDisplayDevicesW ((null),0,0x33dabc,0x00000000), stub!
fixme:win:EnumDisplayDevicesW (L"\\\\.\\DISPLAY1",0,0x33dabc,0x00000000), stub!
fixme:mscms:MSCMS_match_profile ET_DEVICENAME: L""
[multiple duplicate lines]
fixme:mscms:MSCMS_match_profile ET_DEVICENAME: L""
lcms: Error #12288; Corrupted memory profile

~$ fixme:ntdll:RtlNtStatusToDosErrorNoTeb no mapping for 8000000a

```

---

### Post by Dark Aspect on 2009-03-25
Install the latest version of wine, which is wine 1.1.17. follow the instructions [here]("http://www.winehq.org/download/deb"). It may not make a difference seeing as how photoshop 5.5 is old(er), its probably a regression sadly.

Is there a reason you can't use a native image editor such as GIMP?

---

### Post by justanotherhandle on 2009-03-26
Upgrading to Wine 1.1.17 worked, thanks!

> ...its probably a regression sadly.
What's a regression?

I attempt to use Gimp on a regular basis, but I know Photoshop so well and even with two Gimp books and multitudes of online Gimp tutorials, I just cannot get past a (to me) clunky and confusing interface.

---

### Post by Meow27 on 2009-03-26
regression
noun
A return to a former, usually worse condition:

---

### Post by Dark Aspect on 2009-03-26
> **justanotherhandle said:**
> What's a regression?
In terms of wine, a regression is when a piece of software worked on wine. But, a later version broke the application with new bugs. Technically, Wine 1.0 which is what you had was supposed to be the "stable" release.

I am glad to hear the update worked.

---

