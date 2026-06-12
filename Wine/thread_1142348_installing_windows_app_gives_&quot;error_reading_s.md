---
title: "installing windows app gives &quot;error reading setup initialization file&quot;"
date: 2009-04-29
forum: Wine
---

### Post by willem on 2009-04-29
I am running a dual boot pc with intrepid and windows xp home. I am trying to install an application (db/text works) form a shared ms windows folder on another windows pc. The primary program is supposed to be installed on one pc which then acts as the db/text server. You are then supposed to do "workstation installations" on all the pcs which will be connecting to the server. I mounted the shared windows folder and I attempted to run the installation using the command
*wine setup.exe*
This gave me the following error:  **"error reading setup initialization file"**

The setup works perfectly if I run it from ms windows, so the file is intact, complete and functional. I was also able to successfully install the full program directly on my linux pc using the installation disk, so wine doesn't have a problem running the program itself. I suspect that wine doesn't have access to a .dll or some other file needed for the workstation setup. I need to do a workstation installation through wine in order to have everything working as it should however.
Any ideas?

---

### Post by asdfoo on 2009-04-29
> **willem said:**
> I am running a dual boot pc with intrepid and windows xp home. I am trying to install an application (db/text works) form a shared ms windows folder on another windows pc. The primary program is supposed to be installed on one pc which then acts as the db/text server. You are then supposed to do "workstation installations" on all the pcs which will be connecting to the server. I mounted the shared windows folder and I attempted to run the installation using the command
*wine setup.exe*
This gave me the following error:  **"error reading setup initialization file"**

The setup works perfectly if I run it from ms windows, so the file is intact, complete and functional. I was also able to successfully install the full program directly on my linux pc using the installation disk, so wine doesn't have a problem running the program itself. I suspect that wine doesn't have access to a .dll or some other file needed for the workstation setup. I need to do a workstation installation through wine in order to have everything working as it should however.
Any ideas?

Which Wine version? 1.1.20 is the newest beta.

---

### Post by willem on 2009-04-29
> **asdfoo said:**
> Which Wine version? 1.1.20 is the newest beta.

I've got wine  1.0.1 installed - it was the version that synaptic installed.

---

### Post by asdfoo on 2009-04-29
> **willem said:**
> I've got wine  1.0.1 installed - it was the version that synaptic installed.

That was released a very long time ago and there have been substantial bug fixes since... visit [http://winehq.org/download](http://winehq.org/download)

---

### Post by willem on 2009-04-30
> **asdfoo said:**
> That was released a very long time ago and there have been substantial bug fixes since... visit [http://winehq.org/download](http://winehq.org/download)

Thanks. I've added the wine repository and installed wine 1.1.20. I assumed that the Ubuntu repositories would have the latest version of wine.

The first time I tried running the setup again, it gave me a long list of errors in the terminal before showing the same "error reading setup initialization file" error message. Here is what it gave me:

```

err:ole:CoCreateInstance apartment not initialised
err:ole:CoCreateInstance apartment not initialised
err:ole:CoCreateInstance apartment not initialised
err:ole:CoCreateInstance apartment not initialised
err:ole:CoCreateInstance apartment not initialised
err:ole:CoCreateInstance apartment not initialised
err:ole:CoCreateInstance apartment not initialised
err:ole:CoCreateInstance apartment not initialised
err:ole:CoCreateInstance apartment not initialised
err:ole:CoCreateInstance apartment not initialised
err:ole:CoCreateInstance apartment not initialised
err:ole:CoCreateInstance apartment not initialised
err:ole:CoCreateInstance apartment not initialised
err:ole:CoCreateInstance apartment not initialised
err:ole:CoCreateInstance apartment not initialised
err:ole:CoCreateInstance apartment not initialised
err:ole:CoCreateInstance apartment not initialised
err:ole:CoCreateInstance apartment not initialised
err:ole:CoCreateInstance apartment not initialised
err:ole:CoCreateInstance apartment not initialised
err:ole:CoCreateInstance apartment not initialised
err:ole:CoCreateInstance apartment not initialised
err:ole:CoCreateInstance apartment not initialised
err:ole:CoCreateInstance apartment not initialised
err:ole:CoCreateInstance apartment not initialised
err:ole:CoCreateInstance apartment not initialised
err:ole:CoCreateInstance apartment not initialised
err:ole:CoCreateInstance apartment not initialised
err:ole:CoCreateInstance apartment not initialised
err:ole:CoCreateInstance apartment not initialised
fixme:system:SetProcessDPIAware stub!
fixme:dwmapi:DwmIsCompositionEnabled 0x33cf94
fixme:file:MoveFileWithProgressW MOVEFILE_WRITE_THROUGH unimplemented
fixme:advapi:SetNamedSecurityInfoW L"C:\\windows\\gecko\\0.9.1\\wine_gecko\\components\\xpti.dat" 1 536870916 (nil) (nil) 0x33c960 (nil)
fixme:iphlpapi:NotifyAddrChange (Handle 0x3eae898, overlapped 0x3eae8a0): stub
fixme:file:MoveFileWithProgressW MOVEFILE_WRITE_THROUGH unimplemented
fixme:advapi:SetNamedSecurityInfoW L"C:\\windows\\gecko\\0.9.1\\wine_gecko\\components\\compreg.dat" 1 536870916 (nil) (nil) 0x33ca50 (nil)
0[19a4a8]: nsNativeModuleLoader::LoadModule("C:\windows\gecko\0.9.1\wine_gecko\nssckbi.dll") - Symbol NSGetModule not found
0[19a4a8]: nsNativeModuleLoader::LoadModule("C:\windows\gecko\0.9.1\wine_gecko\freebl3.dll") - Symbol NSGetModule not found
0[19a4a8]: nsNativeModuleLoader::LoadModule("C:\windows\gecko\0.9.1\wine_gecko\sqlite3.dll") - Symbol NSGetModule not found
0[19a4a8]: nsNativeModuleLoader::LoadModule("C:\windows\gecko\0.9.1\wine_gecko\ssl3.dll") - Symbol NSGetModule not found
0[19a4a8]: nsNativeModuleLoader::LoadModule("C:\windows\gecko\0.9.1\wine_gecko\xul.dll") - Symbol NSGetModule not found
0[19a4a8]: nsNativeModuleLoader::LoadModule("C:\windows\gecko\0.9.1\wine_gecko\plugins\npnul32.dll") - Symbol NSGetModule not found
0[19a4a8]: nsNativeModuleLoader::LoadModule("C:\windows\gecko\0.9.1\wine_gecko\nssutil3.dll") - Symbol NSGetModule not found
0[19a4a8]: nsNativeModuleLoader::LoadModule("C:\windows\gecko\0.9.1\wine_gecko\nss3.dll") - Symbol NSGetModule not found
0[19a4a8]: nsNativeModuleLoader::LoadModule("C:\windows\gecko\0.9.1\wine_gecko\nspr4.dll") - Symbol NSGetModule not found
0[19a4a8]: nsNativeModuleLoader::LoadModule("C:\windows\gecko\0.9.1\wine_gecko\xpcom.dll") - Symbol NSGetModule not found
0[19a4a8]: nsNativeModuleLoader::LoadModule("C:\windows\gecko\0.9.1\wine_gecko\plds4.dll") - Symbol NSGetModule not found
0[19a4a8]: nsNativeModuleLoader::LoadModule("C:\windows\gecko\0.9.1\wine_gecko\smime3.dll") - Symbol NSGetModule not found
0[19a4a8]: nsNativeModuleLoader::LoadModule("C:\windows\gecko\0.9.1\wine_gecko\js3250.dll") - Symbol NSGetModule not found
0[19a4a8]: nsNativeModuleLoader::LoadModule("C:\windows\gecko\0.9.1\wine_gecko\nssdbm3.dll") - Symbol NSGetModule not found
0[19a4a8]: nsNativeModuleLoader::LoadModule("C:\windows\gecko\0.9.1\wine_gecko\softokn3.dll") - Symbol NSGetModule not found
0[19a4a8]: nsNativeModuleLoader::LoadModule("C:\windows\gecko\0.9.1\wine_gecko\plc4.dll") - Symbol NSGetModule not found
fixme:shell:DllCanUnloadNow stub
wine: configuration in '/home/willem/.wine' has been updated.

```

I noticed that the last line showed that .wine had been updated, so I tried again. This time it didn't bring up the terminal errors, but it still gave me the "error reading setup initialization file" error message like before.

---

