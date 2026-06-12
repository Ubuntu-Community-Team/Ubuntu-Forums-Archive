---
title: "TVUPlayer in wine stopped working"
date: 2009-09-04
forum: Wine
---

### Post by spursncowboys on 2009-09-04
I installed wine, then wine-doors. I followed this HOW TO [http://linux4humanbeing.blogspot.com/2009/04/how-to-install-tvuplayer-on-linux.html](http://linux4humanbeing.blogspot.com/2009/04/how-to-install-tvuplayer-on-linux.html) for installing TVU Player. Everything worked perfect and then I tried to set up the Upside-Down-Ternet from this HOW TO [https://help.ubuntu.com/community/Upside-Down-TernetHowTo](https://help.ubuntu.com/community/Upside-Down-TernetHowTo) and since then TVU has not worked for me. It crashes. I uninstalled tvu and then followed the directions to reinstall. Then two things I installed from the Upside-Down-Ternet is squid, squid3, and apache2. I removed and purged squid and squid3.

---

### Post by spursncowboys on 2009-09-05
This is what I get from the terminal
```
fixme:ntoskrnl:KeInitializeSpinLock stub: 0x661740
fixme:ntoskrnl:KeInitializeSpinLock stub: 0x66173c
fixme:ntoskrnl:KeInitializeSpinLock stub: 0x661744
fixme:ntoskrnl:KeInitializeSpinLock stub: 0x661748
fixme:ntoskrnl:KeInitializeSpinLock stub: 0x66174c
fixme:ntoskrnl:KeInitializeMutex stub: 0x74b49c, 1
fixme:ntoskrnl:KeInitializeEvent stub: 0x66172c 1 0
fixme:ntoskrnl:IoInitializeTimer stub: 0x65f020, 0x65c3d0, 0x65f020
fixme:ntoskrnl:IoStartTimer stub: 0x65f020
fixme:ntoskrnl:KeWaitForSingleObject stub: 0x66172c, 0, 0, 0, (nil)
fixme:ntoskrnl:PsTerminateSystemThread stub: 0
fixme:ntoskrnl:ExInitializeResourceLite stub: 0x114832
fixme:ntoskrnl:KeInitializeSpinLock stub: 0x11488a
fixme:ntoskrnl:KeInitializeSpinLock stub: 0x114896
fixme:ntoskrnl:KeInitializeEvent stub: 0x11489e 1 1
fixme:ntoskrnl:KeInitializeSpinLock stub: 0x1148ae
fixme:ntoskrnl:KeInitializeSpinLock stub: 0x11487e
fixme:ntoskrnl:ExInitializeZone stub: 0x11486e, 192, 0x116200, 24584
Can't open file c:\windows\profiles\family\Application Data\TVU Networks\AutoUpgrade\upgrade.x
fixme:win:EnumDisplayDevicesW ((null),0,0x326c24,0x00000000), stub!
fixme:urlmon:URLMoniker_BindToObject use running object table
fixme:system:SetProcessDPIAware stub!
fixme:dwmapi:DwmIsCompositionEnabled 0x32588c
fixme:iphlpapi:NotifyAddrChange (Handle 0x3fae908, overlapped 0x3fae910): stub
fixme:iphlpapi:GetAdaptersAddresses no support for IPv6 addresses
0[185a18]: IMM32: InitKeyboardLayout, aKeyboardLayout=04090409, sCodePage=1252, sIMEProperty=00090000
fixme:shdocvw:ClOleCommandTarget_QueryStatus (0x17fb88)->((null) 1 0x325e54 (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x17fb88)->((null) 25 2 0x325e68 (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x17fb88)->((null) 26 2 0x325e68 (nil))
fixme:mshtml:on_change_dlcontrol unsupported dlcontrol 00000070
fixme:shdocvw:ClientSite_GetContainer (0x17fb88)->(0x325ea4)
fixme:shdocvw:ClOleCommandTarget_Exec (0x17fb88)->({000214d1-0000-0000-c000-000000000046} 37 0 0x325f30 (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x17fb88)->({000214d1-0000-0000-c000-000000000046} 84 0 (nil) 0x325f58)
fixme:urlmon:URLMoniker_BindToObject use running object table
fixme:shdocvw:ClOleCommandTarget_QueryStatus (0x1826f0)->((null) 1 0x324ae0 (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x1826f0)->((null) 25 2 0x324af4 (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x1826f0)->((null) 26 2 0x324af4 (nil))
fixme:mshtml:on_change_dlcontrol unsupported dlcontrol 00000070
fixme:shdocvw:ClientSite_GetContainer (0x1826f0)->(0x324b30)
fixme:shdocvw:ClOleCommandTarget_Exec (0x1826f0)->({000214d1-0000-0000-c000-000000000046} 37 0 0x324bbc (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x1826f0)->({000214d1-0000-0000-c000-000000000046} 84 0 (nil) 0x324be4)
fixme:mshtml:HTMLDocument_clear (0x183058)
fixme:urlmon:URLMoniker_BindToObject use running object table
fixme:shdocvw:ClOleCommandTarget_QueryStatus (0x4244910)->((null) 1 0x324ae0 (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x4244910)->((null) 25 2 0x324af4 (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x4244910)->((null) 26 2 0x324af4 (nil))
fixme:mshtml:on_change_dlcontrol unsupported dlcontrol 00000070
fixme:shdocvw:ClientSite_GetContainer (0x4244910)->(0x324b30)
fixme:shdocvw:ClOleCommandTarget_Exec (0x4244910)->({000214d1-0000-0000-c000-000000000046} 37 0 0x324bbc (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x4244910)->({000214d1-0000-0000-c000-000000000046} 84 0 (nil) 0x324be4)
fixme:mshtml:HTMLDocument_clear (0x4229210)
err:ole:CoGetClassObject class {6c736db1-bd94-11d0-8a23-00aa00b58e10} not registered
err:ole:CoGetClassObject no class object {6c736db1-bd94-11d0-8a23-00aa00b58e10} could be created for context 0x1
err:ole:CoGetClassObject class {6c736db1-bd94-11d0-8a23-00aa00b58e10} not registered
err:ole:CoGetClassObject no class object {6c736db1-bd94-11d0-8a23-00aa00b58e10} could be created for context 0x1
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
------------------------start-----------------------
Become a master
Return
------------------------end-----------------------

start server at port 1955
fixme:urlmon:URLMoniker_BindToObject use running object table
fixme:wininet:InternetAttemptConnect Stub
ret1=1 ret2=1
udp ipExternal:3f968f4b  Internal:6501a8c0  portLocal:8080    portExternal1:8080    External2:8080  linkType:120
udp LinkType(guess):120
err:ole:CoGetClassObject class {ae1e00aa-3fd5-403c-8a27-2bbdc30cd0e1} not registered
err:ole:CoGetClassObject class {ae1e00aa-3fd5-403c-8a27-2bbdc30cd0e1} not registered
err:ole:create_server class {ae1e00aa-3fd5-403c-8a27-2bbdc30cd0e1} not registered
fixme:ole:CoGetClassObject CLSCTX_REMOTE_SERVER not supported
err:ole:CoGetClassObject no class object {ae1e00aa-3fd5-403c-8a27-2bbdc30cd0e1} could be created for context 0x17
err:ole:CoGetClassObject class {ae1e00aa-3fd5-403c-8a27-2bbdc30cd0e1} not registered
err:ole:CoGetClassObject class {ae1e00aa-3fd5-403c-8a27-2bbdc30cd0e1} not registered
err:ole:create_server class {ae1e00aa-3fd5-403c-8a27-2bbdc30cd0e1} not registered
fixme:ole:CoGetClassObject CLSCTX_REMOTE_SERVER not supported
err:ole:CoGetClassObject no class object {ae1e00aa-3fd5-403c-8a27-2bbdc30cd0e1} could be created for context 0x17
fixme:mshtml:HTMLDocument_clear (0x183058)
fixme:dciman:DCICreatePrimary 0x39c 0x1bf13b8
m Files\TVUPlayer\TVUPlayer.exe: ../../src/xcb_io.c:378: _XAllocID: Assertion `ret != inval_id' failed.

```

---

### Post by coolbrook on 2009-09-05
I never got TVUPlayer to work and gave up a long time ago, so I'll bookmark this thread.

---

