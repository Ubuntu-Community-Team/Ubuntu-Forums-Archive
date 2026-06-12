---
title: "Horrible FPS with EVE Online"
date: 2010-02-13
forum: Wine
---

### Post by Vunutus on 2010-02-13
Granted my computer isn't the best, but I get absolutely HORRIBLE FPS in Wine. It runs smoothly under Windows. When I say horrible FPS I mean maybe 0.5 FPS, completely unplayable. 

Does anyone have any advice for me here?

EDIT: For clarification: The problems all occur when I'm actually in space. The menus work fine and even the 3D graphics in the character creator work smoothly.

---

### Post by Vunutus on 2010-02-13
Alright I played around with the settings for a while. I disabled shadows and that causes it to run smoothly, which is strange because shadows don't affect it under windows.

I haven't played much yet, but after playing for like 15 minutes the game crashed with some generic windows error. I haven't seen anything very similar on the AppDB entry, I'll try running it from a terminal later so I can see any error messages...

---

### Post by Vunutus on 2010-02-13
Apparently I missed part of the AppDB entry. The bug that causes it to crash is only present in the latest version of Wine. Downgrading to the previous version supposedly fixes things.

Here is the terminal output from the time I start to the time it crashes:

```

err:ole:CoGetClassObject class {9a5ea990-3034-4d6f-9128-01f3c61022bc} not registered
err:ole:CoGetClassObject no class object {9a5ea990-3034-4d6f-9128-01f3c61022bc} could be created for context 0x1
fixme:heap:HeapSetInformation 0x8d9000 0 0x33fc6c 4
fixme:win:EnumDisplayDevicesW ((null),0,0x338ea0,0x00000000), stub!
fixme:wtsapi:WTSRegisterSessionNotification Stub 0xa0048 0x00000000
fixme:dsalsa:IDsDriverBufferImpl_SetVolumePan (0x5d4ca28,0x5d4d348): stub
fixme:imm:ImmDisableTextFrameService Stub
fixme:imm:ImmReleaseContext (0xa0048, 0x15db08): stub
[danny@danny_desktop ~]$ fixme:reg:GetNativeSystemInfo (0x33b718) using GetSystemInfo()
fixme:d3d_shader:print_glsl_info_log Error received from GLSL shader #17:
fixme:d3d_shader:print_glsl_info_log     Vertex info
fixme:d3d_shader:print_glsl_info_log     -----------
fixme:d3d_shader:print_glsl_info_log     warning: no vertex attribute is explicitly assigned to vertex attribute zero
fixme:imm:NotifyIME NI_CLOSECANDIDATE
fixme:toolhelp:CreateToolhelp32Snapshot Unimplemented: heap list snapshot
fixme:toolhelp:Heap32ListFirst : stub
fixme:toolhelp:CreateToolhelp32Snapshot Unimplemented: heap list snapshot
fixme:toolhelp:Heap32ListFirst : stub
fixme:winsock:WSAIoctl unsupported WS_IOCTL cmd (c8000014)
fixme:imm:NotifyIME NI_CLOSECANDIDATE
fixme:d3d_draw:drawPrimitive Using software emulation because not all material properties could be tracked
fixme:winsock:WSAIoctl unsupported WS_IOCTL cmd (c8000014)
fixme:winsock:WSAIoctl unsupported WS_IOCTL cmd (c8000014)
fixme:winsock:WSAIoctl unsupported WS_IOCTL cmd (c8000014)
fixme:imm:NotifyIME NI_CLOSECANDIDATE
fixme:imm:NotifyIME NI_CLOSECANDIDATE
fixme:d3d:buffer_PreLoad Too many full buffer conversions, stopping converting
fixme:d3d:buffer_PreLoad Too many full buffer conversions, stopping converting
fixme:d3d:buffer_PreLoad Too many full buffer conversions, stopping converting
fixme:d3d:buffer_PreLoad Too many full buffer conversions, stopping converting
wine: Unhandled page fault on read access to 0x0000eac0 at address 0x2374e1e (thread 0029), starting debugger...

```

I'll probably end up having to downgrade versions but if anyone has any suggestions on how to fix it on the current version I'd appreciate it.

---

