---
title: "Fsx"
date: 2009-08-26
forum: Wine
---

### Post by Lucretius on 2009-08-26
Anyone tried running flight simulator X on wine recently?

I looked at the wine HQ and the last attempts are very old (circa July 2008 )

I would attempt it myself but my ubuntu machine is down at the moment with some hardware issues.

---

### Post by skykooler on 2009-11-19
Just tried it; it doesn't even start up - no idea why

---

### Post by Xog on 2009-11-19
> **skykooler said:**
> Just tried it; it doesn't even start up - no idea why

that's usually caused by a permission denial. To allow permission for you, go into your c:/Program Files and right click the folder the game is in. go to properties, go to permissions, and change all of the permissions to "Create and Delete files" and then click Enable Permissions and then click OK. Then try opening it again.

---

### Post by skykooler on 2009-11-23
okay, I tried opening it from the command line and here is what I got:
```
win@Ubuntu:~/.wine/drive_c/Link to Program Files/Microsoft Games/Microsoft Flight Simulator X$ wine fsx.exe
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC80.MFC"
err:module:import_dll Library MFC80.DLL (which is needed by L"Z:\\media\\F074DE1D74DDE5FE\\Program Files\\Microsoft Games\\Microsoft Flight Simulator X\\fsx.exe") not found
err:module:import_dll Library MSVCR80.dll (which is needed by L"Z:\\media\\F074DE1D74DDE5FE\\Program Files\\Microsoft Games\\Microsoft Flight Simulator X\\fsx.exe") not found
err:module:LdrInitializeThunk Main exe initialization for L"Z:\\media\\F074DE1D74DDE5FE\\Program Files\\Microsoft Games\\Microsoft Flight Simulator X\\fsx.exe" failed, status c0000135

```

Any ideas?

---

### Post by MdMax on 2010-04-28
> **skykooler said:**
> Any ideas?

No ideas and I even have no hope on this. I tried [FS2004 on Wine](http://appdb.winehq.org/objectManager.php?sClass=version&iId=2819) without any success.

Try a native Linux flight simulator:
[http://ubuntuforums.org/showthread.php?t=1360724](http://ubuntuforums.org/showthread.php?t=1360724)

Happy flying !

---

### Post by cogadh on 2010-04-28
> **skykooler said:**
> okay, I tried opening it from the command line and here is what I got:
```
win@Ubuntu:~/.wine/drive_c/Link to Program Files/Microsoft Games/Microsoft Flight Simulator X$ wine fsx.exe
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC80.MFC"
err:module:import_dll Library MFC80.DLL (which is needed by L"Z:\\media\\F074DE1D74DDE5FE\\Program Files\\Microsoft Games\\Microsoft Flight Simulator X\\fsx.exe") not found
err:module:import_dll Library MSVCR80.dll (which is needed by L"Z:\\media\\F074DE1D74DDE5FE\\Program Files\\Microsoft Games\\Microsoft Flight Simulator X\\fsx.exe") not found
err:module:LdrInitializeThunk Main exe initialization for L"Z:\\media\\F074DE1D74DDE5FE\\Program Files\\Microsoft Games\\Microsoft Flight Simulator X\\fsx.exe" failed, status c0000135

```

Any ideas?

Try using [winetricks]("http://wiki.winehq.org/winetricks") to install those missing DLLs.

EDIT - Of course *now* I notice the date on that post...

---

### Post by asdfoo on 2010-04-28
it also looks like you're running this from your windows partition?  what is the z:\media\F... path?

---

