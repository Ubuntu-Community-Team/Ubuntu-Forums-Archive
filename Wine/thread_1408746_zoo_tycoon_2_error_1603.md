---
title: "zoo tycoon 2 error 1603"
date: 2010-02-16
forum: Wine
---

### Post by Affrikka on 2010-02-16
Hey,

Apparently 2 years ago i install ZT2, because I found an old post of mine (hee hee) but now, two years later, my baby sister wants to have ZT2 on her computer. She's running 8.04 Edubuntu, with the latest wine upgrade. The install gets to about 99% and gives error 1603, which I found is something to do with the system having full control.

Can anyone help?


Thanks,



Affrikka


PS: because i know SOME one will ask for it, here's the terminal output for the installation:

```
fixme:advapi:LookupAccountNameW (null) L"kathryn" (nil) 0x32ae8c (nil) 0x32ae90 0x32ae84 - stub
fixme:advapi:LookupAccountNameW (null) L"kathryn" 0x15aa18 0x32ae8c 0x15ace0 0x32ae90 0x32ae84 - stub
err:msi:ITERATE_DuplicateFiles Failed to copy file L"C:\\Program Files\\Common Files\\InstallShield\\Driver\\11\\Intel 32\\IDriver.exe" -> L"C:\\Program Files\\Common Files\\InstallShield\\Driver\\11\\Intel 32\\", last error 80
fixme:msi:ITERATE_DuplicateFiles We should track these duplicate files as well
fixme:msi:msi_unimplemented_action_stub RemoveFolders -> 2 ignored L"CreateFolder" table values
err:rpc:I_RpcGetBuffer no binding
fixme:advapi:LookupAccountNameW (null) L"kathryn" (nil) 0x33cb44 (nil) 0x33cb48 0x33cb3c - stub
fixme:advapi:LookupAccountNameW (null) L"kathryn" 0x197830 0x33cb44 0x197000 0x33cb48 0x33cb3c - stub
fixme:storage:StgCreateDocfile Storage share mode not implemented.
fixme:reg:GetNativeSystemInfo (0x331478) using GetSystemInfo()
fixme:ntdll:RtlNtStatusToDosErrorNoTeb no mapping for c0000109
fixme:ole:CoInitializeSecurity (0x530310,-1,(nil),(nil),4,3,(nil),0,(nil)) - stub!
fixme:advapi:RegisterEventSourceA ((null),"IDriverT"): stub
fixme:advapi:RegisterEventSourceW (L"",L"IDriverT"): stub
fixme:advapi:ReportEventA (0xcafe4242,0x0004,0x0000,0x00000000,(nil),0x0001,0x00000000,0x94e9e8,(nil)): stub
fixme:advapi:ReportEventW (0xcafe4242,0x0004,0x0000,0x00000000,(nil),0x0001,0x00000000,0x14a6e8,(nil)): stub
fixme:advapi:DeregisterEventSource (0xcafe4242) stub
fixme:ntdll:RtlNtStatusToDosErrorNoTeb no mapping for c0000109
fixme:advapi:DecryptFileA "C:\\windows\\VCTEMP\\" 00000000
fixme:advapi:DecryptFileA "C:\\windows\\temp\\IXP000.TMP\\" 00000000
fixme:advapi:LookupAccountNameW (null) L"kathryn" (nil) 0x33f5bc (nil) 0x33f5c0 0x33f5b4 - stub
fixme:advapi:LookupAccountNameW (null) L"kathryn" 0x1558c8 0x33f5bc 0x155870 0x33f5c0 0x33f5b4 - stub
fixme:msi:ACTION_HandleStandardAction unhandled standard action L"SetODBCFolders"
fixme:msi:msi_unimplemented_action_stub MsiUnpublishAssemblies -> 10 ignored L"MsiAssembly" table values
err:msi:remove_tracked_tempfiles failed to delete L"C:\\windows\\temp\\msi5e7a.tmp"
fixme:advapi:LookupAccountNameW (null) L"kathryn" (nil) 0x203b1d0 (nil) 0x203b1d4 0x203b1c8 - stub
fixme:advapi:LookupAccountNameW (null) L"kathryn" 0x1374ac0 0x203b1d0 0x1375338 0x203b1d4 0x203b1c8 - stub
fixme:rpc:RpcMgmtWaitServerListen not waiting for server calls to finish
fixme:msi:ACTION_HandleStandardAction unhandled standard action L"SetODBCFolders"
fixme:rpc:RpcImpersonateClient (0x13ae740): stub
fixme:rpc:RpcRevertToSelfEx (0x13ae740): stub
fixme:rpc:RpcImpersonateClient (0x13ae228): stub
fixme:rpc:RpcRevertToSelfEx (0x13ae228): stub
fixme:rpc:RpcImpersonateClient (0x13ba350): stub
fixme:rpc:RpcRevertToSelfEx (0x13ba350): stub
fixme:rpc:RpcImpersonateClient (0x13b9798): stub
fixme:rpc:RpcRevertToSelfEx (0x13b9798): stub
fixme:msi:msi_unimplemented_action_stub RemoveFolders -> 4 ignored L"CreateFolder" table values
fixme:rpc:RpcImpersonateClient (0x13c72a0): stub
fixme:rpc:RpcRevertToSelfEx (0x13c72a0): stub
err:msi:ACTION_InstallFiles Failed to copy L"D:\\program files\\Microsoft Games\\Zoo Tycoon 2\\x151_000.z2f" to L"C:\\Program Files\\Microsoft Games\\Zoo Tycoon 2\\x151_000.z2f" (2)
err:msi:ITERATE_Actions Execution halted, action L"InstallFinalize" returned 1603
err:rpc:I_RpcReceive we got fault packet with status 0x1c010003
fixme:advapi:RegisterEventSourceA ((null),"IDriverT"): stub
fixme:advapi:RegisterEventSourceW (L"",L"IDriverT"): stub
fixme:advapi:ReportEventA (0xcafe4242,0x0004,0x0000,0x00000000,(nil),0x0001,0x00000000,0x94ea38,(nil)): stub
fixme:advapi:ReportEventW (0xcafe4242,0x0004,0x0000,0x00000000,(nil),0x0001,0x00000000,0x152f48,(nil)): stub
fixme:advapi:DeregisterEventSource (0xcafe4242) stub
err:ole:ifproxy_release_public_refs IRemUnknown_RemRelease failed with error 0x800706b5
err:ole:ifproxy_release_public_refs IRemUnknown_RemRelease failed with error 0x800706be

```

---

### Post by gsmanners on 2010-02-16
If you have the repository version, you will need the latest beta of Wine.

See: [http://www.winehq.org/download/deb](http://www.winehq.org/download/deb)
And: [http://appdb.winehq.org/objectManager.php?sClass=application&iId=4220](http://appdb.winehq.org/objectManager.php?sClass=application&iId=4220)

---

### Post by Affrikka on 2010-02-17
i have the latest-- 1.1.38 i think is what it is

---

