---
title: "Dragon NaturallySpeaking: Problem with &quot;AutoTranscribe Folder Agent&quot;"
date: 2009-12-07
forum: Wine
---

### Post by bademeister on 2009-12-07
Dear all,

I am using Dragon Natural Speaking 10.1 Preferred on the most recent Wine (1.1.33, amd64-deb from the Wine PPA). DNS is working mostly fine, however, when I want to use the "NaturallySpeaking AutoTranscribe Folder Agent" I always get the error "Error: failed to initialize the engine" and transcription won't work. Has anyone else had this problem and found a remedy for it?

Thank you
Paul

---

### Post by bademeister on 2009-12-08
Ok, instead of just bumping, I'll post the output when I try to run the "AutoTranscribe Folder Agent" from the terminal:

Command:
```
env WINEPREFIX="/home/paul/.wine" wine "C:\Program Files\Nuance\NaturallySpeaking10\ogram\tagent.exe"

```

Output:
```
env WINEPREFIX="/home/paul/.wine" wine "C:\Program Files\Nuance\NaturallySpeaking10\Program\tagent.exe"
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC80.MFCLOC" (8.0.50608.0)
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC80.MFCLOC" (8.0.50608.0)
fixme:mountmgr:harddisk_ioctl unsupported ioctl 560000
fixme:mountmgr:harddisk_ioctl unsupported ioctl 560000
fixme:mountmgr:harddisk_ioctl unsupported ioctl 560000
fixme:mountmgr:harddisk_ioctl unsupported ioctl 560000
fixme:mountmgr:harddisk_ioctl unsupported ioctl 560000
fixme:mountmgr:harddisk_ioctl unsupported ioctl 560000
fixme:mountmgr:harddisk_ioctl unsupported ioctl 560000
fixme:mountmgr:harddisk_ioctl unsupported ioctl 560000
fixme:mountmgr:harddisk_ioctl unsupported ioctl 560000
fixme:reg:RegSetKeySecurity :(0x54,4,0xc25a50): stub
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC80.MFCLOC" (8.0.50608.0)
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC80.MFCLOC" (8.0.50608.0)
fixme:winstation:GetUserObjectInformationW not supported index 4
err:ntdll:NtQueryInformationToken Unhandled Token Information class 12!
fixme:reg:GetNativeSystemInfo (0x33eda0) using GetSystemInfo()
fixme:process:WTSGetActiveConsoleSessionId stub
err:module:import_dll Library REGAPI.dll (which is needed by L"C:\\Program Files\\Nuance\\NaturallySpeaking10\\Program\\wfapi.dll") not found
err:module:import_dll Library WINSTA.dll (which is needed by L"C:\\Program Files\\Nuance\\NaturallySpeaking10\\Program\\wfapi.dll") not found
fixme:process:WTSGetActiveConsoleSessionId stub
fixme:wtsapi:WTSRegisterSessionNotification Stub 0x10078 0x00000000
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC80.MFCLOC" (8.0.50608.0)
fixme:psapi:GetProcessImageFileNameA (0x26c, 0x27ee118, 520) stub
err:ole:CoGetClassObject class {edb0e980-90bd-11d4-8599-0008c7d3b6f8} not registered
err:ole:CoGetClassObject no class object {edb0e980-90bd-11d4-8599-0008c7d3b6f8} could be created for context 0x1
err:ntdll:RtlpWaitForCriticalSection section 0x7bc9e784 "loader.c: loader_section" wait timed out in thread 0009, blocked by 003f, retrying (60 sec)
err:ntdll:RtlpWaitForCriticalSection section 0x7bc9e784 "loader.c: loader_section" wait timed out in thread 003a, blocked by 003f, retrying (60 sec)
err:ntdll:RtlpWaitForCriticalSection section 0x7bc9e784 "loader.c: loader_section" wait timed out in thread 0035, blocked by 003f, retrying (60 sec)

```

upon which the dialog "Error: failed to initialize the engine" appears.

Closing that dialog and trying to start transcription gives the following output on the command line:

```

fixme:mountmgr:harddisk_ioctl unsupported ioctl 560000
fixme:mountmgr:harddisk_ioctl unsupported ioctl 560000
fixme:mountmgr:harddisk_ioctl unsupported ioctl 560000
fixme:mountmgr:harddisk_ioctl unsupported ioctl 560000
fixme:mountmgr:harddisk_ioctl unsupported ioctl 560000
fixme:mountmgr:harddisk_ioctl unsupported ioctl 560000
fixme:mountmgr:harddisk_ioctl unsupported ioctl 560000
fixme:mountmgr:harddisk_ioctl unsupported ioctl 560000
fixme:mountmgr:harddisk_ioctl unsupported ioctl 560000
fixme:reg:RegSetKeySecurity :(0x54,4,0xc25a50): stub
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC80.MFCLOC" (8.0.50608.0)
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC80.MFCLOC" (8.0.50608.0)
fixme:winstation:GetUserObjectInformationW not supported index 4
err:ntdll:NtQueryInformationToken Unhandled Token Information class 12!
fixme:reg:GetNativeSystemInfo (0x33eda0) using GetSystemInfo()
fixme:process:WTSGetActiveConsoleSessionId stub
err:module:import_dll Library REGAPI.dll (which is needed by L"C:\\Program Files\\Nuance\\NaturallySpeaking10\\Program\\wfapi.dll") not found
err:module:import_dll Library WINSTA.dll (which is needed by L"C:\\Program Files\\Nuance\\NaturallySpeaking10\\Program\\wfapi.dll") not found
fixme:process:WTSGetActiveConsoleSessionId stub
fixme:wtsapi:WTSRegisterSessionNotification Stub 0x50092 0x00000000
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC80.MFCLOC" (8.0.50608.0)
fixme:psapi:GetProcessImageFileNameA (0x26c, 0x27ee118, 520) stub
err:ole:CoGetClassObject class {edb0e980-90bd-11d4-8599-0008c7d3b6f8} not registered
err:ole:CoGetClassObject no class object {edb0e980-90bd-11d4-8599-0008c7d3b6f8} could be created for context 0x1
err:ntdll:RtlpWaitForCriticalSection section 0x7bc9e784 "loader.c: loader_section" wait timed out in thread 0009, blocked by 001b, retrying (60 sec)

```

And that ugly comes up again... anyone? please?

thank you
Paul

---

### Post by bademeister on 2009-12-11
Ok, nevermind, I have found a workaround using the non-free virtualbox from Sun and running DNS in there. Anyway, I think I have set up something pretty cool, if somebody is interested I could write a how-to:

I record voicenotes on my mobile phone, copy them to the computer at my office, there the DNS autotranscribe feature automatically transcribes them to text. Once transcription is done, the text files are copied back to my laptop and imported into tomboy notes. All I have to do is plug in my mobile phone and call ./transcribe-voicenotes (even this could be automated, I guess). In moments like this, I never want to move to any other OS.

cheers
Paul

---

### Post by KenDiPietro on 2009-12-12
> **bademeister said:**
> Ok, nevermind, I have found a workaround using the non-free virtualbox from Sun and running DNS in there. Anyway, I think I have set up something pretty cool, if somebody is interested I could write a how-to:

I record voicenotes on my mobile phone, copy them to the computer at my office, there the DNS autotranscribe feature automatically transcribes them to text. Once transcription is done, the text files are copied back to my laptop and imported into tomboy notes. All I have to do is plug in my mobile phone and call ./transcribe-voicenotes (even this could be automated, I guess). In moments like this, I never want to move to any other OS.

cheers
Paul

I would definitely be interested in an how to.

Seriously.

---

