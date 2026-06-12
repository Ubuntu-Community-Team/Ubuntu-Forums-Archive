---
title: "Risen on Wine 1.3.7"
date: 2010-11-16
forum: Wine
---

### Post by domis4 on 2010-11-16
hey guys, i have a Problem to start the Game "Risen" on my Ubuntu 10.10 Maverick x64
i installed the game through:
```
sudo su
 
```
```
cd /media/RISEN
```
```
wine setup.exe
```
no error messages during the installation, and everything worked :)

but if i try to start the game, i get a few Errors in the Terminal:
```
fixme:ntoskrnl:KeInitializeTimerEx stub: 0x110fb0 0
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC80.OpenMP" (8.0.50727.762)
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC80.CRT" (8.0.50727.762)
err:module:import_dll Library vcomp.dll (which is needed by L"C:\\Programme\\DeepSilver\\Risen\\bin\\Engine.dll") not found
err:module:import_dll Library Engine.dll (which is needed by L"C:\\Programme\\DeepSilver\\Risen\\bin\\risen.exe") not found
err:module:import_dll Loading library Engine.dll (which is needed by L"C:\\Programme\\DeepSilver\\Risen\\bin\\Game.dll") failed (error c0000018).
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC80.CRT" (8.0.50727.762)
err:module:import_dll Library Game.dll (which is needed by L"C:\\Programme\\DeepSilver\\Risen\\bin\\risen.exe") not found
err:module:import_dll Loading library Engine.dll (which is needed by L"C:\\Programme\\DeepSilver\\Risen\\bin\\Importer.dll") failed (error c0000018).
err:module:import_dll Loading library Game.dll (which is needed by L"C:\\Programme\\DeepSilver\\Risen\\bin\\Importer.dll") failed (error c0000018).
err:module:import_dll Library vcomp.dll (which is needed by L"C:\\Programme\\DeepSilver\\Risen\\bin\\Importer.dll") not found
err:module:import_dll Library Importer.dll (which is needed by L"C:\\Programme\\DeepSilver\\Risen\\bin\\risen.exe") not found
err:module:LdrInitializeThunk Main exe initialization for L"C:\\Programme\\DeepSilver\\Risen\\bin\\risen.exe" failed, status c0000135
root@dominik-EasyNote-TJ65:~/.wine/drive_c/Programme/DeepSilver/Risen/bin#
```

---

### Post by fridelain on 2011-01-13
> **domis4 said:**
> 
i installed the game through:
```
sudo su
 
```

**Never run Wine as root!**
also, for checking the compatibility with Wine and instrunctions for making the applications work in Wine, check the [URL="http://appdb.winehq.org/"]Wine Application Database (AppDB)
[/URL]

---

