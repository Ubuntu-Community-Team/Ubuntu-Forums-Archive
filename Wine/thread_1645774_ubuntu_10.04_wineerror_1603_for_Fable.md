---
title: "ubuntu 10.04 wine/error 1603 for Fable"
date: 2010-12-15
forum: Wine
---

### Post by smupid on 2010-12-15
OK well i have been going on about 3 days now 
trying every little possible configuration to get Fable to even install!

Anyways at first I had problems even getting the game to install 
with install shield through Wine, Playonlinux,Crossover, and whatever els 
I've tried. finally i got the dLL problem all figured out!
now it installs but close to the end it gives an 
"Error 1603"

anyways any clue as to how i might fix this problem
i had high hope and they were shot down after this problem.
note: i am not new to Linux but am new to the version i am using
not to mention i just got back from reverting to windows because they really suck!

sorry off topic any help is greatly appreciated
ty: Smupid

extra info:
Ubuntu vr.10.04 "sixpack"
Wine vr.1.3.8

"info from terminal"
```

military@military-desktop:~$ wine /home/military/.wine/dosdevices/c:/windows/Fable/setup.exe
fixme:storage:create_storagefile Storage share mode not implemented.
fixme:advapi:LookupAccountNameW (null) L"military" (nil) 0x32b1c0 (nil) 0x32b1c4 0x32b1b8 - stub
fixme:advapi:LookupAccountNameW (null) L"military" 0x172048 0x32b1c0 0x172200 0x32b1c4 0x32b1b8 - stub
fixme:msi:ITERATE_DuplicateFiles We should track these duplicate files as well
err:rpc:I_RpcGetBuffer no binding
fixme:storage:create_storagefile Storage share mode not implemented.
fixme:advapi:LookupAccountNameW (null) L"military" (nil) 0x33c648 (nil) 0x33c64c 0x33c640 - stub
fixme:advapi:LookupAccountNameW (null) L"military" 0x1b0e08 0x33c648 0x1b6658 0x33c64c 0x33c640 - stub
err:msi:remove_tracked_tempfiles failed to delete L"C:\\users\\military\\Temp\\msi6bb2.tmp"
fixme:advapi:LookupAccountNameW (null) L"military" (nil) 0x307b1cc (nil) 0x307b1d0 0x307b1c4 - stub
fixme:advapi:LookupAccountNameW (null) L"military" 0x12bcb70 0x307b1cc 0x12bc840 0x307b1d0 0x307b1c4 - stub
fixme:ntdll:NtFsControlFile FSCTL_PIPE_IMPERSONATE: impersonating self
fixme:ntdll:NtFsControlFile FSCTL_PIPE_IMPERSONATE: impersonating self
fixme:ntdll:NtFsControlFile FSCTL_PIPE_IMPERSONATE: impersonating self
fixme:ntdll:NtFsControlFile FSCTL_PIPE_IMPERSONATE: impersonating self
err:msi:extract_cabinet FDICopy failed
err:msi:ACTION_InstallFiles Failed to extract cabinet: L"Disk4C~1.cab"
err:msi:ITERATE_Actions Execution halted, action L"InstallFiles" returned 1603
err:ole:ClientRpcChannelBuffer_SendReceive called from wrong apartment, should have been 0x2e00000025
err:ole:xCall RpcChannelBuffer SendReceive failed, 8001010e
err:rpc:I_RpcReceive we got fault packet with status 0x80010108
err:rpc:I_RpcReceive we got fault packet with status 0x1c010003
err:ole:ifproxy_release_public_refs IRemUnknown_RemRelease failed with error 0x800706b5

```

---

### Post by dino99 on 2010-12-15
[http://appdb.winehq.org/objectManager.php?sClass=version&iId=3827](http://appdb.winehq.org/objectManager.php?sClass=version&iId=3827)

read the comments scrolling page down

---

### Post by smupid on 2010-12-15
ok i looked up the link
so anyways i see someone has played it
or gotten it to work "not the greatest but good enough"
so then how do i go about on that site "winehq" to fix my problem?

---

### Post by smupid on 2010-12-18
ok well i figured out how to navigate the winehq site and stuff but still have not figured out how to get the game working any insight helps thanks

---

