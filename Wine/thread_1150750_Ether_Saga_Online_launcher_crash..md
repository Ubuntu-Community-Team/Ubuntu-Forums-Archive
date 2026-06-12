---
title: "Ether Saga Online launcher crash."
date: 2009-05-06
forum: Wine
---

### Post by mentality2 on 2009-05-06
Problem: I've installed and all. All files have been verified. Now when I try to actually run it, the launcher loads for about 1 second, then instantly crashes and WINE exits. Any ideas why? I'm using latest wine as of 7th May 2009. (ver 1.9 something? I'm sure it had a 9 in it somewhere)

Note: I've tried it on Windows XP and it works fine, but I'd REALLY like this to work on Linux too :) (considering wiping windows temporarily).

Thanks in advance.

Here's the terminal output:

```
./Ether Saga Online.desktop: line 1: [Desktop: command not found
./Ether Saga Online.desktop: line 2: Saga: command not found
get fences failed: -1
param: 6, val: 0
fixme:win:EnumDisplayDevicesW ((null),0,0x32f9c0,0x00000000), stub!
fixme:shdocvw:PersistStreamInit_InitNew (0x150f20)
fixme:iphlpapi:NotifyAddrChange (Handle 0x7af4c9e8, overlapped 0x7af4c9cc): stub
fixme:system:SetProcessDPIAware stub!
fixme:msimtf:CActiveIMM_Create ((nil) {08c0e040-62d1-11d1-9326-0060b067b86e} 0x22cef34)
fixme:ole:CoCreateInstance no instance created for interface {08c0e040-62d1-11d1-9326-0060b067b86e} of class {4955dd33-b159-11d0-8fcf-00aa006bcc59}, hres is 0x80004002
fixme:shdocvw:ClOleCommandTarget_QueryStatus (0x150fbc)->((null) 1 0x7c603384 (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x150fbc)->((null) 25 2 0x7c603398 (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x150fbc)->((null) 26 2 0x7c603398 (nil))
fixme:shdocvw:ClientSite_GetContainer (0x150fbc)->(0x7c6033d4)
fixme:shdocvw:ClOleCommandTarget_Exec (0x150fbc)->({000214d1-0000-0000-c000-000000000046} 37 0 0x7c6034a8 (nil))
fixme:shdocvw:HttpNegotiate_BeginningTransaction (0x151848)->(L"" L"" 0 0x7c6034e0)
fixme:shdocvw:ClOleCommandTarget_Exec (0x150fbc)->((null) 29 2 0x7c6046c4 (nil))
fixme:shdocvw:DocHostUIHandler_GetDropTarget (0x150fbc)
fixme:shdocvw:ClientSite_GetContainer (0x150fbc)->(0x7c604674)
fixme:shdocvw:InPlaceFrame_SetStatusText (0x150fbc)->(0xb7f41d31)
fixme:shdocvw:ClOleCommandTarget_Exec (0x150fbc)->((null) 25 2 0x7c6045a8 (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x150fbc)->((null) 26 2 0x7c6045a8 (nil))
X Error of failed request:  BadAlloc (insufficient resources for operation)
  Major opcode of failed request:  53 (X_CreatePixmap)
  Serial number of failed request:  5625
  Current serial number in output stream:  5629
./Ether Saga Online.desktop: line 6: Saga: command not found
./Ether Saga Online.desktop: line 7: Files/Perfect: No such file or directory
```

---

### Post by cogadh on 2009-05-06
Have you already tried the fixes listed here:
[http://appdb.winehq.org/objectManager.php?sClass=version&iId=16161](http://appdb.winehq.org/objectManager.php?sClass=version&iId=16161)

---

### Post by mentality2 on 2009-05-07
I'm running v 1.1.19 so as far as I know, I don't need patching, but yes I tried it anyway. The launcher loads (flashes open), then immediately crashes..

---

### Post by cogadh on 2009-05-07
Patching Wine wasn't the only suggestion there. The more important one is running it in a Wine virtual desktop. Did you try that?

---

### Post by mentality2 on 2009-05-07
Is that making it run in a blue square looking thing? If it is, then yes. If it isn't, then I have absolutely no idea what you're talking about...

---

### Post by rcarroll05 on 2009-12-20
I have the same issue when running ether saga.  Have done all the suggestions.  Most current version of wine installed, downloaded directx, installed video drivers, set to run in xp mode in a screened window.

Here are the error messages:

fixme:advapi:SetEntriesInAclA 1 0x33f79c (nil) 0x33f7d4fixme:advapi:SetSecurityInfo stub
fixme:advapi:SetEntriesInAclA 1 0x33f788 (nil) 0x33f7d0
fixme:advapi:SetSecurityInfo stub
fixme:advapi:SetEntriesInAclA 1 0x33f7a8 (nil) 0x33f7f0
fixme:advapi:SetSecurityInfo stub
fixme:win:EnumDisplayDevicesW ((null),0,0x32f994,0x00000000), stub!
fixme:iphlpapi:NotifyAddrChange (Handle 0x7ebfa9b8, overlapped 0x7ebfa99c): stub
fixme:shdocvw:PersistStreamInit_InitNew (0x14efb8)
fixme:iphlpapi:NotifyAddrChange (Handle 0x7d5939b8, overlapped 0x7d59399c): stub
fixme:system:SetProcessDPIAware stub!
fixme:msimtf:CActiveIMM_Create ((nil) {08c0e040-62d1-11d1-9326-0060b067b86e} 0x22cef34)
fixme:ole:CoCreateInstance no instance created for interface {08c0e040-62d1-11d1-9326-0060b067b86e} of class {4955dd33-b159-11d0-8fcf-00aa006bcc59}, hres is 0x80004002
fixme:shdocvw:ClOleCommandTarget_QueryStatus (0x14f054)->((null) 1 0x7e4de2fc (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x14f054)->((null) 25 2 0x7e4de310 (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x14f054)->((null) 26 2 0x7e4de310 (nil))
fixme:shdocvw:ClientSite_GetContainer (0x14f054)->(0x7e4de354)
fixme:shdocvw:ClOleCommandTarget_Exec (0x14f054)->({000214d1-0000-0000-c000-000000000046} 37 0 0x7e4de410 (nil))
fixme:shdocvw:HttpNegotiate_BeginningTransaction (0x14f4a0)->(L"" L"" 0 0x7e4de448)
fixme:shdocvw:ClOleCommandTarget_Exec (0x14f054)->((null) 29 2 0x7e4df63c (nil))
fixme:shdocvw:DocHostUIHandler_GetDropTarget (0x14f054)
fixme:shdocvw:ClientSite_GetContainer (0x14f054)->(0x7e4df5b4)
fixme:shdocvw:InPlaceFrame_SetStatusText (0x14f054)->(0x6003eb71)
fixme:shdocvw:ClOleCommandTarget_Exec (0x14f054)->((null) 25 2 0x7e4df4c0 (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x14f054)->((null) 26 2 0x7e4df4c0 (nil))
X Error of failed request:  BadAlloc (insufficient resources for operation)
  Major opcode of failed request:  53 (X_CreatePixmap)
  Serial number of failed request:  5620
  Current serial number in output stream:  5631

---

