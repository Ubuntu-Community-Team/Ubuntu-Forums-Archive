---
title: "afew questions"
date: 2010-05-03
forum: Wine
---

### Post by camdy on 2010-05-03
hi guys i have the odd question or two oh i'm using unbuntu 10.04 in virtualbox .ok i just installed steam but after the update is down i get this in the terminal 


CellID: Fetching server list from CSDS. . .
fixme:process:SetProcessShutdownParameters (00000100, 00000000): partial stub.
X Error of failed request:  BadLength (poly request too large or internal Xlib length error)
  Major opcode of failed request:  65 (X_PolyLine)
  Serial number of failed request:  10758
  Current serial number in output stream:  10759


any ideas what happened:confused:

also i want to install eve online and i get a
 
Validation failed. Expected checksum is 34b4202b71ec6a84676a6347b6aa9b72 but was 272ac4e4cc62c354dadc7085b3f4c17


any help would be great:)

---

### Post by beastrace91 on 2010-05-03
What Wine version?

~Jeff

---

### Post by camdy on 2010-05-05
> **beastrace91 said:**
> What Wine version?

~Jeff

sorry for the late reply just busy the wine version is 1.1.42

---

### Post by beastrace91 on 2010-05-06
Try upgrading to 1.1.43 - the steam beta client just went live recently so odds are it might be bugging in the older Wine version.

~Jeff

---

### Post by camdy on 2010-05-08
have updated to 1.1.43 but still get the same problem with eve.i haven't tried steam yet but i'm thinking if eve is still getting the same problem then steam most likely will


i tried steam on playonlnux but that failed.

---

### Post by odh1412 on 2011-06-20
Hey I'm having trouble running steam in wine (vsn 1.2.2) and Ubuntu (11.04) 64 bit OS.

I have a nvidia gtx460 Graphics card.

Steam loads fine and I can put in my acct name and password. Then A window pops up as if it is advancing then crash.


fixme:process:SetProcessShutdownParameters (00000100, 00000000): partial stub.
fixme:urlmon:CoInternetSetFeatureEnabled 5, 0x00000002, 1, stub
fixme:urlmon:CoInternetSetFeatureEnabled 10, 0x00000002, 1, stub
fixme:toolhelp:CreateToolhelp32Snapshot Unimplemented: heap list snapshot
fixme:toolhelp:Heap32ListFirst : stub
fixme:mixer:ALSA_MixerInit No master control found on HDA NVidia, disabling mixer
err:ole:CoGetClassObject class {77f10cf0-3db5-4966-b520-b7c54fd35ed6} not registered
err:ole:CoGetClassObject no class object {77f10cf0-3db5-4966-b520-b7c54fd35ed6} could be created for context 0x1
fixme:wbemprox:wbem_locator_ConnectServer 0x19de18, L"ROOT\\CIMV2", (null), (null), (null), 0x00000080, (null), (nil), 0x424be50)
fixme:winhttp:WinHttpGetIEProxyConfigForCurrentUser returning no proxy used
fixme:win:RegisterDeviceNotificationA (hwnd=0x100c0, filter=0x32d588,flags=0x00000004) returns a fake device notification handle!
fixme:winhttp:WinHttpGetIEProxyConfigForCurrentUser returning no proxy used
fixme:threadpool:RtlQueueWorkItem Flags 0x4 not supported
fixme:win:EnumDisplayDevicesW ((null),0,0x32ce34,0x00000000), stub!
fixme:threadpool:RtlQueueWorkItem Flags 0x4 not supported
fixme:appbar:handle_appbarmessage SHAppBarMessage(ABM_GETSTATE): stub
fixme:appbar:handle_appbarmessage SHAppBarMessage(ABM_GETAUTOHIDEBAR, hwnd=(nil), edge=3): stub
fixme:appbar:handle_appbarmessage SHAppBarMessage(ABM_GETAUTOHIDEBAR, hwnd=(nil), edge=1): stub
fixme:appbar:handle_appbarmessage SHAppBarMessage(ABM_GETAUTOHIDEBAR, hwnd=(nil), edge=0): stub
fixme:appbar:handle_appbarmessage SHAppBarMessage(ABM_GETAUTOHIDEBAR, hwnd=(nil), edge=2): stub
fixme:appbar:handle_appbarmessage SHAppBarMessage(ABM_GETSTATE): stub
fixme:appbar:handle_appbarmessage SHAppBarMessage(ABM_GETAUTOHIDEBAR, hwnd=(nil), edge=3): stub
fixme:appbar:handle_appbarmessage SHAppBarMessage(ABM_GETAUTOHIDEBAR, hwnd=(nil), edge=1): stub
fixme:appbar:handle_appbarmessage SHAppBarMessage(ABM_GETAUTOHIDEBAR, hwnd=(nil), edge=0): stub
fixme:appbar:handle_appbarmessage SHAppBarMessage(ABM_GETAUTOHIDEBAR, hwnd=(nil), edge=2): stub
fixme:threadpool:RtlQueueWorkItem Flags 0x4 not supported
fixme:threadpool:RtlQueueWorkItem Flags 0x4 not supported
fixme:appbar:handle_appbarmessage SHAppBarMessage(ABM_GETSTATE): stub
fixme:appbar:handle_appbarmessage SHAppBarMessage(ABM_GETAUTOHIDEBAR, hwnd=(nil), edge=3): stub
fixme:appbar:handle_appbarmessage SHAppBarMessage(ABM_GETAUTOHIDEBAR, hwnd=(nil), edge=1): stub
fixme:appbar:handle_appbarmessage SHAppBarMessage(ABM_GETAUTOHIDEBAR, hwnd=(nil), edge=0): stub
fixme:appbar:handle_appbarmessage SHAppBarMessage(ABM_GETAUTOHIDEBAR, hwnd=(nil), edge=2): stub
fixme:appbar:handle_appbarmessage SHAppBarMessage(ABM_GETSTATE): stub
fixme:appbar:handle_appbarmessage SHAppBarMessage(ABM_GETAUTOHIDEBAR, hwnd=(nil), edge=3): stub
fixme:appbar:handle_appbarmessage SHAppBarMessage(ABM_GETAUTOHIDEBAR, hwnd=(nil), edge=1): stub
fixme:appbar:handle_appbarmessage SHAppBarMessage(ABM_GETAUTOHIDEBAR, hwnd=(nil), edge=0): stub
fixme:appbar:handle_appbarmessage SHAppBarMessage(ABM_GETAUTOHIDEBAR, hwnd=(nil), edge=2): stub
fixme:appbar:handle_appbarmessage SHAppBarMessage(ABM_GETSTATE): stub
fixme:appbar:handle_appbarmessage SHAppBarMessage(ABM_GETAUTOHIDEBAR, hwnd=(nil), edge=3): stub
fixme:appbar:handle_appbarmessage SHAppBarMessage(ABM_GETAUTOHIDEBAR, hwnd=(nil), edge=1): stub
fixme:appbar:handle_appbarmessage SHAppBarMessage(ABM_GETAUTOHIDEBAR, hwnd=(nil), edge=0): stub
fixme:appbar:handle_appbarmessage SHAppBarMessage(ABM_GETAUTOHIDEBAR, hwnd=(nil), edge=2): stub
fixme:threadpool:RtlQueueWorkItem Flags 0x4 not supported
fixme:advapi:RegisterTraceGuidsW (0x3925320, 0x3f7b738, {3dada31d-19ef-4dc1-b345-037927193422}, 1, 0x3f53b24, (null), (null), 0x3f7b750,)
fixme:threadpool:RtlQueueWorkItem Flags 0x4 not supported
fixme:threadpool:RtlQueueWorkItem Flags 0x4 not supported
fixme:threadpool:RtlQueueWorkItem Flags 0x4 not supported
fixme:threadpool:RtlQueueWorkItem Flags 0x4 not supported
fixme:threadpool:RtlQueueWorkItem Flags 0x4 not supported
fixme:threadpool:RtlQueueWorkItem Flags 0x4 not supported
fixme:threadpool:RtlQueueWorkItem Flags 0x4 not supported
fixme:threadpool:RtlQueueWorkItem Flags 0x4 not supported
fixme:threadpool:RtlQueueWorkItem Flags 0x4 not supported
fixme:threadpool:RtlQueueWorkItem Flags 0x4 not supported
fixme:threadpool:RtlQueueWorkItem Flags 0x4 not supported
fixme:threadpool:RtlQueueWorkItem Flags 0x4 not supported
fixme:threadpool:RtlQueueWorkItem Flags 0x4 not supported
fixme:threadpool:RtlQueueWorkItem Flags 0x4 not supported
fixme:threadpool:RtlQueueWorkItem Flags 0x4 not supported
fixme:threadpool:RtlQueueWorkItem Flags 0x4 not supported
fixme:threadpool:RtlQueueWorkItem Flags 0x4 not supported
fixme:threadpool:RtlQueueWorkItem Flags 0x4 not supported
fixme:threadpool:RtlQueueWorkItem Flags 0x4 not supported


Any Ideas?

---

