---
title: "Republic: The Revoultion (Installation problems)"
date: 2008-12-16
forum: Wine
---

### Post by mr.bear on 2008-12-16
Hey,

I'm new to both Ubuntu and Wine, and I'm experiencing some problems with the installation of the game ['Republic: The Revolution']("http://appdb.winehq.org/objectManager.php?sClass=version&iId=4080"). The problem is that when the installation process is about to begin, I'll get a message asking me to insert disc 1 (which of course is already in the drive). I have no idea what to do, which is why I'm asking you guys.

Screenshot
[img]http://www.spaceforest.net/images/error.png[/img]

Terminal
```
david@*****:~$ wine /media/cdrom/setup.exe
fixme:advapi:LookupAccountNameW (null) L"david" (nil) 0x32bdf0 (nil) 0x32bdf4 0x32bde8 - stub
fixme:advapi:LookupAccountNameW (null) L"david" 0x179270 0x32bdf0 0x179640 0x32bdf4 0x32bde8 - stub
err:msi:ITERATE_DuplicateFiles Original file unknown L"F1319_IDriver.exe"
fixme:msi:msi_unimplemented_action_stub RemoveFolders -> 1 ignored L"CreateFolder" table values
fixme:advapi:LookupAccountNameW (null) L"david" (nil) 0x33f81c (nil) 0x33f820 0x33f814 - stub
fixme:advapi:LookupAccountNameW (null) L"david" 0x133410 0x33f81c 0x132a70 0x33f820 0x33f814 - stub
fixme:rpc:RpcMgmtWaitServerListen not waiting for server calls to finish
fixme:msi:ACTION_HandleStandardAction unhandled standard action L"SetODBCFolders"
fixme:rpc:RpcImpersonateClient (0x19b208): stub
err:ole:ClientRpcChannelBuffer_SendReceive called from wrong apartment, should have been 0x2200000023
err:ole:xCall RpcChannelBuffer SendReceive failed, 8001010e
fixme:rpc:RpcRevertToSelfEx (0x19b208): stub
fixme:msi:msi_unimplemented_action_stub RemoveShortcuts -> 11 ignored L"Shortcut" table values
fixme:msi:msi_unimplemented_action_stub RemoveFolders -> 4 ignored L"CreateFolder" table values
err:msi:msi_view_get_row Error fetching data for 1
```

---

