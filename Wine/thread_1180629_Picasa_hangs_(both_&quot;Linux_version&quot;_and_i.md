---
title: "Picasa hangs (both &quot;Linux version&quot; and install through Wine)"
date: 2009-06-07
forum: Wine
---

### Post by BatPenguin on 2009-06-07
I'm trying to run Picasa (tried 2.7 and 3.0) on 64-bit Jaunty and it keeps hanging. It might finish scanning my photos if I don't touch it while it does, but at the latest when I try to edit a photo, it hangs.

I've tried the version from repositories (2.7), downloading 3.0 from google and even running the Windows 3.0 through wine myself (I have WineHQ repositories installed). The error is the same. This is it from ~/.google/picasa/3.0/picasa.log (running Linux version 3.0): 

```
fixme:mixer:ALSA_MixerInit No master control found on QuickCam Pro 9000, disabling mixer
fixme:wininet:InternetGetConnectedStateExW always returning LAN connection.
fixme:ole:CoResumeClassObjects stub
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:file:MoveFileWithProgressW MOVEFILE_WRITE_THROUGH unimplemented
fixme:wininet:InternetGetConnectedState always returning LAN connection.
fixme:urlmon:ObtainUserAgentString (0, 0x33d1df, 0x33d1e0): stub
fixme:urlmon:ObtainUserAgentString (0, 0x134f98, 0x33d1e0): stub
fixme:wininet:InternetGetConnectedStateExW always returning LAN connection.
fixme:win:FlashWindowEx 0x337f14
fixme:file:MoveFileWithProgressW MOVEFILE_WRITE_THROUGH unimplemented
fixme:file:MoveFileWithProgressW MOVEFILE_WRITE_THROUGH unimplemented
fixme:file:MoveFileWithProgressW MOVEFILE_WRITE_THROUGH unimplemented
fixme:file:MoveFileWithProgressW MOVEFILE_WRITE_THROUGH unimplemented
fixme:file:MoveFileWithProgressW MOVEFILE_WRITE_THROUGH unimplemented
fixme:file:MoveFileWithProgressW MOVEFILE_WRITE_THROUGH unimplemented
fixme:file:MoveFileWithProgressW MOVEFILE_WRITE_THROUGH unimplemented
fixme:file:MoveFileWithProgressW MOVEFILE_WRITE_THROUGH unimplemented
fixme:file:MoveFileWithProgressW MOVEFILE_WRITE_THROUGH unimplemented
fixme:file:MoveFileWithProgressW MOVEFILE_WRITE_THROUGH unimplemented
fixme:file:MoveFileWithProgressW MOVEFILE_WRITE_THROUGH unimplemented
fixme:file:MoveFileWithProgressW MOVEFILE_WRITE_THROUGH unimplemented
fixme:file:MoveFileWithProgressW MOVEFILE_WRITE_THROUGH unimplemented
fixme:file:MoveFileWithProgressW MOVEFILE_WRITE_THROUGH unimplemented
fixme:file:MoveFileWithProgressW MOVEFILE_WRITE_THROUGH unimplemented
fixme:file:MoveFileWithProgressW MOVEFILE_WRITE_THROUGH unimplemented
fixme:file:MoveFileWithProgressW MOVEFILE_WRITE_THROUGH unimplemented
fixme:file:MoveFileWithProgressW MOVEFILE_WRITE_THROUGH unimplemented
fixme:file:MoveFileWithProgressW MOVEFILE_WRITE_THROUGH unimplemented
fixme:file:MoveFileWithProgressW MOVEFILE_WRITE_THROUGH unimplemented
fixme:file:MoveFileWithProgressW MOVEFILE_WRITE_THROUGH unimplemented
fixme:file:MoveFileWithProgressW MOVEFILE_WRITE_THROUGH unimplemented
fixme:file:MoveFileWithProgressW MOVEFILE_WRITE_THROUGH unimplemented
fixme:file:MoveFileWithProgressW MOVEFILE_WRITE_THROUGH unimplemented
fixme:file:MoveFileWithProgressW MOVEFILE_WRITE_THROUGH unimplemented
fixme:file:MoveFileWithProgressW MOVEFILE_WRITE_THROUGH unimplemented
fixme:file:MoveFileWithProgressW MOVEFILE_WRITE_THROUGH unimplemented
fixme:file:MoveFileWithProgressW MOVEFILE_WRITE_THROUGH unimplemented
fixme:file:MoveFileWithProgressW MOVEFILE_WRITE_THROUGH unimplemented
fixme:file:MoveFileWithProgressW MOVEFILE_WRITE_THROUGH unimplemented
fixme:file:MoveFileWithProgressW MOVEFILE_WRITE_THROUGH unimplemented
fixme:file:MoveFileWithProgressW MOVEFILE_WRITE_THROUGH unimplemented
fixme:file:MoveFileWithProgressW MOVEFILE_WRITE_THROUGH unimplemented
fixme:file:MoveFileWithProgressW MOVEFILE_WRITE_THROUGH unimplemented
fixme:file:MoveFileWithProgressW MOVEFILE_WRITE_THROUGH unimplemented
fixme:file:MoveFileWithProgressW MOVEFILE_WRITE_THROUGH unimplemented
fixme:file:MoveFileWithProgressW MOVEFILE_WRITE_THROUGH unimplemented
fixme:wininet:InternetLockRequestFile STUB
fixme:file:MoveFileWithProgressW MOVEFILE_WRITE_THROUGH unimplemented
fixme:file:MoveFileWithProgressW MOVEFILE_WRITE_THROUGH unimplemented
fixme:file:MoveFileWithProgressW MOVEFILE_WRITE_THROUGH unimplemented
fixme:file:MoveFileWithProgressW MOVEFILE_WRITE_THROUGH unimplemented
fixme:file:MoveFileWithProgressW MOVEFILE_WRITE_THROUGH unimplemented
fixme:file:MoveFileWithProgressW MOVEFILE_WRITE_THROUGH unimplemented
fixme:file:MoveFileWithProgressW MOVEFILE_WRITE_THROUGH unimplemented
fixme:file:MoveFileWithProgressW MOVEFILE_WRITE_THROUGH unimplemented
fixme:file:MoveFileWithProgressW MOVEFILE_WRITE_THROUGH unimplemented
fixme:file:MoveFileWithProgressW MOVEFILE_WRITE_THROUGH unimplemented
fixme:file:MoveFileWithProgressW MOVEFILE_WRITE_THROUGH unimplemented
fixme:file:MoveFileWithProgressW MOVEFILE_WRITE_THROUGH unimplemented
fixme:file:MoveFileWithProgressW MOVEFILE_WRITE_THROUGH unimplemented
fixme:file:MoveFileWithProgressW MOVEFILE_WRITE_THROUGH unimplemented
fixme:file:MoveFileWithProgressW MOVEFILE_WRITE_THROUGH unimplemented
fixme:file:MoveFileWithProgressW MOVEFILE_WRITE_THROUGH unimplemented
fixme:file:MoveFileWithProgressW MOVEFILE_WRITE_THROUGH unimplemented
fixme:file:MoveFileWithProgressW MOVEFILE_WRITE_THROUGH unimplemented
fixme:file:MoveFileWithProgressW MOVEFILE_WRITE_THROUGH unimplemented
fixme:file:MoveFileWithProgressW MOVEFILE_WRITE_THROUGH unimplemented
fixme:file:MoveFileWithProgressW MOVEFILE_WRITE_THROUGH unimplemented
fixme:file:MoveFileWithProgressW MOVEFILE_WRITE_THROUGH unimplemented
fixme:file:MoveFileWithProgressW MOVEFILE_WRITE_THROUGH unimplemented
fixme:file:MoveFileWithProgressW MOVEFILE_WRITE_THROUGH unimplemented
fixme:file:MoveFileWithProgressW MOVEFILE_WRITE_THROUGH unimplemented
fixme:file:MoveFileWithProgressW MOVEFILE_WRITE_THROUGH unimplemented
fixme:file:MoveFileWithProgressW MOVEFILE_WRITE_THROUGH unimplemented
fixme:file:MoveFileWithProgressW MOVEFILE_WRITE_THROUGH unimplemented
fixme:win:FlashWindowEx 0x339bc0
err:ntdll:RtlpWaitForCriticalSection section 0x7ef107e0 "profile.c: PROFILE_CritSect" wait timed out in thread 0025, blocked by 0032, retrying (60 sec)
err:ntdll:RtlpWaitForCriticalSection section 0xba8b14 "?" wait timed out in thread 002f, blocked by 0025, retrying (60 sec)
err:ntdll:RtlpWaitForCriticalSection section 0xba8b14 "?" wait timed out in thread 0032, blocked by 0025, retrying (60 sec)
fixme:advapi:CheckTokenMembership ((nil) 0x1790a0 0x7bafe4f4) stub!
fixme:mixer:ALSA_MixerInit No master control found on QuickCam Pro 9000, disabling mixer
fixme:wininet:InternetGetConnectedStateExW always returning LAN connection.
err:ntdll:RtlpWaitForCriticalSection section 0xba8b14 "?" wait timed out in thread 002f, blocked by 0025, retrying (60 sec)
err:ntdll:RtlpWaitForCriticalSection section 0xba8b14 "?" wait timed out in thread 0032, blocked by 0025, retrying (60 sec)
fixme:advapi:RegisterEventSourceA ((null),"Picasa3"): stub
fixme:advapi:RegisterEventSourceW (L"",L"Picasa3"): stub
fixme:advapi:ReportEventA (0xcafe4242,0x0001,0x0000,0xc0000001,(nil),0x0001,0x00000000,0x339ad4,(nil)): stub
fixme:advapi:ReportEventW (0xcafe4242,0x0001,0x0000,0xc0000001,(nil),0x0001,0x00000000,0x1401c0,(nil)): stub
err:eventlog:ReportEventW L"Picasa has crashed.  A crash dump has been generated: C:\\windows\\temp\\Picasa_090607-090717.dmp\n"
fixme:advapi:DeregisterEventSource (0xcafe4242) stub
err:ntdll:RtlpWaitForCriticalSection section 0x7ef107e0 "profile.c: PROFILE_CritSect" wait timed out in thread 0025, blocked by 0032, retrying (60 sec)
```

This is a program of significant "wife importance factor" :D, so I'd appreciate help in getting it to work. Since Google's Linux version is just the Windows version packaged with Wine, I'd imagine any knowledge of the causes of these "? wait timed out" errors might be helpful. I've tried looking up information, can't seem to find much.

---

