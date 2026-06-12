---
title: "Octodad"
date: 2010-11-12
forum: Wine
---

### Post by Quadunit404 on 2010-11-12
Anybody got this game working under Wine? From my experience, it installs fine, but if you start it it crashes on startup.

If you want to screw around with it and see if you can come up with a working solution you can download it from [here.]("http://octodadgame.com/download.php")

---

### Post by borateen on 2010-11-13
I get this error:
```

fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC90.CRT" (9.0.21022.8)
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC90.CRT" (9.0.21022.8)
err:module:import_dll Library MSVCP90.dll (which is needed by L"C:\\Program Files\\Octodad\\libtheoraplayer.dll") not found
err:module:import_dll Library libtheoraplayer.dll (which is needed by L"C:\\Program Files\\Octodad\\octodad.exe") not found
err:module:import_dll Library MSVCP90.dll (which is needed by L"C:\\Program Files\\Octodad\\octodad.exe") not found
err:module:LdrInitializeThunk Main exe initialization for L"C:\\Program Files\\Octodad\\octodad.exe" failed, status c0000135
```

So I downloaded the MSVCP90.dll off of dll-files.com and extracted it into ~/.wine/dosdevices/c:/windows/system32

The program will now launch. I get the loading screen, intro graphics, then a black screen with only an octopus mouse cursor. I assume this is the game's selection cursor but clicking around and hitting keys does nothing. Must be something with the graphics. I will mess around and see what I can find in the wine configuration.

---

### Post by borateen on 2010-11-13
I made sure all the wine configuration settings were set back to default. The game now gets through the selection screen, the first cut scene, then crashes on the help/controls screen.

I got this error:
```

content\models\house\furniture\shelvingunit.obj
wine: Call from 0x7b836a42 to unimplemented function msvcr90.dll._itoa_s, aborting
wine: Unimplemented function msvcr90.dll._itoa_s called at address 0x7b836a42 (thread 001c), starting debugger...
err:mmdevapi:ACR_ReleaseBuffer Starting from 1014
Unhandled exception: unimplemented function msvcr90.dll._itoa_s called in 32-bit code (0x7b836a42).
Register dump:
then a bunch of content\models\house\furniture\shelvingunit.obj
wine: Call from 0x7b836a42 to unimplemented function msvcr90.dll._itoa_s, aborting
wine: Unimplemented function msvcr90.dll._itoa_s called at address 0x7b836a42 (thread 001c), starting debugger...
err:mmdevapi:ACR_ReleaseBuffer Starting from 1014
Unhandled exception: unimplemented function msvcr90.dll._itoa_s called in 32-bit code (0x7b836a42).
Register dump:
```

I wonder if it is the msvcr90.dll or the msvcp90.dll which I downloaded from that sketchy web site?

---

### Post by borateen on 2010-11-13
It works. I installed the latest beta version of wine (1.3.6) which reports to fix issues with MSVCR. Install it  and then play Octodad! (Jeez this game is ridiculous.)

[http://www.winehq.org/download/deb](http://www.winehq.org/download/deb)

---

### Post by Quadunit404 on 2010-11-13
Yeah, I do have Wine 1.3.6 installed, but when I try to run the game, it says "The program Octodad.exe has encountered a serious problem and needs to close" RIGHT after the game launches and sets my resolution to 1024x768 (see attachment)

---

### Post by djvonfunkin on 2010-11-15
I am one of the developers. Are you guys using the 1.0.6 version? There were some issues with Windows Vista & 7 using XInput.lib that is only included as a directx 9.0c extra (which is why it is included with the installer) that causes the same crash. Wine may have the same issue, but I know some users have gotten it to work. We took out this support in the new version as the xbox360 controller support was not implemented yet anyways.

---

### Post by Quadunit404 on 2010-11-18
> **djvonfunkin said:**
> I am one of the developers. Are you guys using the 1.0.6 version? There were some issues with Windows Vista & 7 using XInput.lib that is only included as a directx 9.0c extra (which is why it is included with the installer) that causes the same crash. Wine may have the same issue, but I know some users have gotten it to work. We took out this support in the new version as the xbox360 controller support was not implemented yet anyways.

Yep, I downloaded OctodadInstallerV1.0.6.exe, which gives me Octodad 1.0.6. I'll see what telling Octodad it's running on Vista does.

UPDATE: Just noticed the new version, 1.1.0. Downloading right now.

---

### Post by Peepsalot on 2011-01-13
Quadunit404, did you ever get this running?  I am attempting to run Octodad 1.1.0, using wine 1.3 from the ppa.  

I am seeing the same error as the screenshot you posted.  The last few lines from the console show this:
```

Backtrace:
=>0 0x7b839652 in kernel32 (+0x29652) (0x0033fb18)
  1 0x7e4b50c8 in msvcp90 (+0x350c7) (0x0033fb48)
  2 0x7e49035d in msvcp90 (+0x1035c) (0x0033fcac)
  3 0x003e1549 in libtheoraplayer (+0x11548) (0x0033fd9c)
wine: Call from 0x7b839652 to unimplemented function msvcp90.dll.??$?HDU?$char_traits@D@std@@V?$allocator@D@1@@std@@YA?AV?$basic_string@DU?$char_traits@D@std@@V?$allocator@D@2@@0@ABV10@PBD@Z, aborting
wine: Call from 0x7b839652 to unimplemented function msvcp90.dll.??$?HDU?$char_traits@D@std@@V?$allocator@D@1@@std@@YA?AV?$basic_string@DU?$char_traits@D@std@@V?$allocator@D@2@@0@ABV10@PBD@Z, aborting

```

---

