---
title: "troble getting game to work with wine"
date: 2009-10-12
forum: Wine
---

### Post by HPspectre3 on 2009-10-12
hey ive tried 1.1.25, 1.1.26, 1.1.30 and 1.1.17 under advice from other forums. once i install the game and enter "wine ~/Desktop/Client.exe to run the client to play the game, the screen flickers and i get this error:

```
hpspectre3@ubuntu:~$ wine ~/Desktop/Client.exe
err:menubuilder:WinMain unknown option -a
err:menubuilder:WinMain unknown option -r
Could not load Mozilla. HTML rendering will be disabled.
wine: configuration in '/home/hpspectre3/.wine' has been updated.
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC80.CRT"
err:module:import_dll Library xerces-c_2_8.dll (which is needed by L"Z:\\home\\hpspectre3\\Desktop\\Client.exe") not found
err:module:import_dll Library libcurl.dll (which is needed by L"Z:\\home\\hpspectre3\\Desktop\\Client.exe") not found
err:module:import_dll Library CrashRpt.dll (which is needed by L"Z:\\home\\hpspectre3\\Desktop\\Client.exe") not found
err:module:import_dll Library MSVCP80.dll (which is needed by L"Z:\\home\\hpspectre3\\Desktop\\Client.exe") not found
err:module:import_dll Library mss32.dll (which is needed by L"Z:\\home\\hpspectre3\\Desktop\\Client.exe") not found
err:module:import_dll Library MSVCR80.dll (which is needed by L"Z:\\home\\hpspectre3\\Desktop\\Client.exe") not found
err:module:LdrInitializeThunk Main exe initialization for L"Z:\\home\\hpspectre3\\Desktop\\Client.exe" failed, status c0000135
```im not sure what it means but i know this game works for other people as a backup i they dont have windows or its not working on thier windows, wich is my problem. also, i checked, all my dlls are in their directory.
if someone could tell me what this means it would be awesome, i just got an email from the developers support team stating "at this time we are unable to solve your issue, we appoligize for any inconvienience, Frogster Team"
anyways thanks for any who try, lol i ish i just knew more about linux, 3 days ago was my first time!
alright thanks

EDIT 2 things, im running 9.04 if that helps and ALSO, i tryed running another exe, i imprted mspaint from another computer. i get a similar error. when i dont do the command and just click on a exe i get :an error has occured while opening this archive, but i think thats normal right?

---

### Post by Giblet5 on 2009-10-12
It means you're missing a bunch of .DLL (dynamically linked libraries) that Client.exe expects to find - but did not.

In other words, Client.exe was built against, and depends on, a lot of other Windows stuff that you have not provided.

Xerces XML processing library...
MS C runtime, etc.

Find them (presumably on the system you copied Client.exe from) and copy those files to the Windows/system32 folder in your ~/.wine folder.

You'll probably discover lots more as you resolve these missing pieces.

---

### Post by HPspectre3 on 2009-10-12
alright nice. that gave me something new at leaced. lol. now i get this error:

```
hpspectre3@ubuntu:~$ wine ~/Desktop/Client.exe
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC80.CRT"
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC80.CRT"
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC80.CRT"
err:menubuilder:WinMain unknown option -a
err:menubuilder:WinMain unknown option -r
err:module:attach_process_dlls "MSVCR80.dll" failed to initialize, aborting
err:module:LdrInitializeThunk Main exe initialization for L"Z:\\home\\hpspectre3\\Desktop\\Client.exe" failed, status c0000142
```

and i get a popup-attached

---

