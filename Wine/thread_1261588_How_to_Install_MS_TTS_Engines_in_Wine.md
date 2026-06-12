---
title: "How to Install MS TTS Engines in Wine"
date: 2009-09-08
forum: Wine
---

### Post by RichardGv on 2009-09-08
**I solved the problem myself. **I successfully installed MS TTS Engines with [native MSI Installer]("http://wiki.winehq.org/NativeMsi").

Are there any ways to install Microsoft TTS Engines 5.1 in Wine?

The installation program do run in Wine, but some files are not copied.
Wine Version: 1.1.29 (Clean one)
The installation file I use: [http://dict.hjenglish.com/publish/Microsoft_TTS_51_eng.msi](http://dict.hjenglish.com/publish/Microsoft_TTS_51_eng.msi)
This is the output. 
```

(WinXP Mode)
richard@richard-desktop:~/WineApps$ wine msiexec /i tts.msi
wine: created the configuration directory '/home/richard/.wine'
fixme:system:SetProcessDPIAware stub!
fixme:iphlpapi:NotifyAddrChange (Handle 0x7cd4c9e8, overlapped 0x7cd4c9cc): stub
fixme:shell:DllCanUnloadNow stub
wine: configuration in '/home/richard/.wine' has been updated.
fixme:advapi:LookupAccountNameW (null) L"richard" (nil) 0x32f87c (nil) 0x32f880 0x32f874 - stub
fixme:advapi:LookupAccountNameW (null) L"richard" 0x12e0f8 0x32f87c 0x12e198 0x32f880 0x32f874 - stub
fixme:msi:ACTION_HandleStandardAction unhandled standard action L"SetODBCFolders"
fixme:msi:msi_unimplemented_action_stub UnregisterTypeLibraries -> 3 ignored L"TypeLib" table values
fixme:msi:msi_unimplemented_action_stub UnregisterProgIdInfo -> 72 ignored L"ProgId" table values
fixme:msi:msi_unimplemented_action_stub RemoveFolders -> 1 ignored L"CreateFolder" table values

(Win2K Mode)
richard@richard-desktop:~/WineApps$ wine msiexec /i tts.msi
fixme:advapi:LookupAccountNameW (null) L"richard" (nil) 0x32f7bc (nil) 0x32f7c0 0x32f7b4 - stub
fixme:advapi:LookupAccountNameW (null) L"richard" 0x149908 0x32f7bc 0x133308 0x32f7c0 0x32f7b4 - stub
fixme:msi:msi_unimplemented_action_stub UnregisterTypeLibraries -> 3 ignored L"TypeLib" table values
fixme:msi:msi_unimplemented_action_stub UnregisterProgIdInfo -> 72 ignored L"ProgId" table values
fixme:msi:msi_unimplemented_action_stub RemoveFolders -> 1 ignored L"CreateFolder" table values

(WinMe Mode)
richard@richard-desktop:~/WineApps$ wine msiexec /i tts.msi
fixme:advapi:LookupAccountNameW (null) L"richard" (nil) 0x32f7bc (nil) 0x32f7c0 0x32f7b4 - stub
fixme:advapi:LookupAccountNameW (null) L"richard" 0x149f68 0x32f7bc 0x1497c8 0x32f7c0 0x32f7b4 - stub
fixme:msi:msi_unimplemented_action_stub UnregisterTypeLibraries -> 3 ignored L"TypeLib" table values
fixme:msi:msi_unimplemented_action_stub UnregisterProgIdInfo -> 72 ignored L"ProgId" table values
fixme:msi:msi_unimplemented_action_stub RemoveFolders -> 1 ignored L"CreateFolder" table values

```Thanks.

Update: I copied the lost files in "C:\Program Files\Common Files\Microsoft Shared\Speech" from my Windows XP and it's working right now. But there's no sound. I use ALSA in sound settings, but there's no problem playing other kind of sound in Wine. There are still some part lost in TTS engine, I'm afraid.

---

