---
title: "Counter strike source not running"
date: 2009-07-01
forum: Wine
---

### Post by thehellboy on 2009-07-01
I tried running counter strike source in wine in terminal mode..
its not running i displayed below the terminal output.. please tell what am i doing wrong

************* TERMINAL OUTPUT*******************

$ wine /media/H3LLBoY/CSS/cstrike.exe
^[[D^[[Dfixme:system:SetProcessDPIAware stub!
fixme:dwmapi:DwmIsCompositionEnabled 0x33cf94
0[19d828]: nsNativeModuleLoader::LoadModule("C:\windows\gecko\0.9.1\wine_gecko\nss3.dll") - Symbol NSGetModule not found
0[19d828]: nsNativeModuleLoader::LoadModule("C:\windows\gecko\0.9.1\wine_gecko\ssl3.dll") - Symbol NSGetModule not found
0[19d828]: nsNativeModuleLoader::LoadModule("C:\windows\gecko\0.9.1\wine_gecko\plc4.dll") - Symbol NSGetModule not found
fixme:iphlpapi:NotifyAddrChange (Handle 0x3fae908, overlapped 0x3fae910): stub
0[19d828]: nsNativeModuleLoader::LoadModule("C:\windows\gecko\0.9.1\wine_gecko\nssutil3.dll") - Symbol NSGetModule not found
0[19d828]: nsNativeModuleLoader::LoadModule("C:\windows\gecko\0.9.1\wine_gecko\nspr4.dll") - Symbol NSGetModule not found
0[19d828]: nsNativeModuleLoader::LoadModule("C:\windows\gecko\0.9.1\wine_gecko\freebl3.dll") - Symbol NSGetModule not found
0[19d828]: nsNativeModuleLoader::LoadModule("C:\windows\gecko\0.9.1\wine_gecko\nssdbm3.dll") - Symbol NSGetModule not found
0[19d828]: nsNativeModuleLoader::LoadModule("C:\windows\gecko\0.9.1\wine_gecko\xul.dll") - Symbol NSGetModule not found
0[19d828]: nsNativeModuleLoader::LoadModule("C:\windows\gecko\0.9.1\wine_gecko\xpcom.dll") - Symbol NSGetModule not found
0[19d828]: nsNativeModuleLoader::LoadModule("C:\windows\gecko\0.9.1\wine_gecko\nssckbi.dll") - Symbol NSGetModule not found
0[19d828]: nsNativeModuleLoader::LoadModule("C:\windows\gecko\0.9.1\wine_gecko\js3250.dll") - Symbol NSGetModule not found
0[19d828]: nsNativeModuleLoader::LoadModule("C:\windows\gecko\0.9.1\wine_gecko\plds4.dll") - Symbol NSGetModule not found
0[19d828]: nsNativeModuleLoader::LoadModule("C:\windows\gecko\0.9.1\wine_gecko\plugins\npnul32.dll") - Symbol NSGetModule not found
0[19d828]: nsNativeModuleLoader::LoadModule("C:\windows\gecko\0.9.1\wine_gecko\sqlite3.dll") - Symbol NSGetModule not found
0[19d828]: nsNativeModuleLoader::LoadModule("C:\windows\gecko\0.9.1\wine_gecko\softokn3.dll") - Symbol NSGetModule not found
0[19d828]: nsNativeModuleLoader::LoadModule("C:\windows\gecko\0.9.1\wine_gecko\smime3.dll") - Symbol NSGetModule not found
fixme:shell:DllCanUnloadNow stub
wine: configuration in '/home/dheen/.wine' has been updated.
err:module:import_dll Library MSVBVM60.DLL (which is needed by L"Z:\\media\\H3LLBoY\\CSS\\cstrike.exe") not found
err:module:LdrInitializeThunk Main exe initialization for L"Z:\\media\\H3LLBoY\\CSS\\cstrike.exe" failed, status c0000135

****************************************************************

---

### Post by beastrace91 on 2009-07-01
What Wine version are you running and what GFX card and driver version?

~Jeff

---

### Post by beastrace91 on 2009-07-01
Sorry for the double post, but also just to confirm this is the Steam version of CSS right? Also does at start to load at all (see any output on the screen) or does it just dump right away when you try to load it?

~Jeff

---

### Post by thehellboy on 2009-07-01
I use ATI radeon 1100 Xpress
non proprietary driver..
when i try to run the cstrike.exe in wine from the terminal.. it gives output like this.. and game is not starting

---

### Post by beastrace91 on 2009-07-02
> non proprietary driver So you are using an open source driver then instead of the ATI provided ones? What Wine version are you running and this is the Steam (retail) copy of CSS and not a crack right?

~Jeff

---

### Post by Barky on 2009-07-02
> **thehellboy said:**
> I use ATI radeon 1100 Xpress
non proprietary driver..
when i try to run the cstrike.exe in wine from the terminal.. it gives output like this.. and game is not starting

why don't you just find the dll it asks for?

---

### Post by thehellboy on 2009-07-03
I use a cracked one.. is there any problem.. i use open driver not the ati provided one

---

### Post by Th3_uN1Qu3 on 2009-07-03
Hahahahaha, a CS launcher written in Visual Basic... What n00b wrote that? At least if you are going to use a cracked version use the right one damn it. And as far as i know discussion about cracked software is forbidden here.

Type in the terminal: wine hl2.exe -steam -game cstrike -dxlevel 81 and if 10 million other things that could be broken in your version aren't broken, it should run.

As with the open driver, don't expect more than 2fps with it.

---

### Post by beastrace91 on 2009-07-03
I figured you where trying to run a cracked copy - do yourself a favor and go buy the game, the steam version works fine through wine. And yes, the OpenSource drive for GFX cards are notoriously crappy.

~Jeff

---

### Post by Leopardson on 2009-07-03
Steam version works fine for me.

It's $20. I can find $20 in my couch.

---

