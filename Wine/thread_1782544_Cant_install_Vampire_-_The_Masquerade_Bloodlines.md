---
title: "Cant install Vampire - The Masquerade Bloodlines"
date: 2011-06-14
forum: Wine
---

### Post by heldernunes on 2011-06-14
I can't install this game...

in terminal have this error:


> helder@helder-PC:~/cd 1$ wine setup.exe 
fixme:advapi:LookupAccountNameW (null) L"helder" (nil) 0x32b708 (nil) 0x32b70c 0x32b700 - stub
fixme:advapi:LookupAccountNameW (null) L"helder" 0x170cb0 0x32b708 0x170350 0x32b70c 0x32b700 - stub
fixme:ntdll:find_reg_tz_info Can't find matching timezone information in the registry for bias 180, std (d/m/y): 0/00/0000, dlt (d/m/y): 0/00/0000
fixme:msi:ITERATE_DuplicateFiles We should track these duplicate files as well
fixme:advapi:LookupAccountNameW (null) L"helder" (nil) 0x33c674 (nil) 0x33c678 0x33c66c - stub
fixme:advapi:LookupAccountNameW (null) L"helder" 0x1ad8c0 0x33c674 0x1ad550 0x33c678 0x33c66c - stub
fixme:advapi:LookupAccountNameW (null) L"helder" (nil) 0x33c674 (nil) 0x33c678 0x33c66c - stub
fixme:advapi:LookupAccountNameW (null) L"helder" 0x1b83e0 0x33c674 0x1b8550 0x33c678 0x33c66c - stub
fixme:ntdll:find_reg_tz_info Can't find matching timezone information in the registry for bias 180, std (d/m/y): 0/00/0000, dlt (d/m/y): 0/00/0000
fixme:storage:create_storagefile Storage share mode not implemented.
err:ole:marshal_object object doesn't expose interface {60e73571-8258-478b-bd66-a7c07319cc89}, failing with error 0x80004002
err:ole:ClientIdentity_QueryMultipleInterfaces IRemUnknown_RemQueryInterface failed with error 0x80004002
err:ole:marshal_object object doesn't expose interface {60e73571-8258-478b-bd66-a7c07319cc89}, failing with error 0x80004002
err:ole:ClientIdentity_QueryMultipleInterfaces IRemUnknown_RemQueryInterface failed with error 0x80004002
fixme:advapi:LookupAccountNameW (null) L"helder" (nil) 0x9d2d954 (nil) 0x9d2d958 0x9d2d94c - stub
fixme:advapi:LookupAccountNameW (null) L"helder" 0x1487078 0x9d2d954 0x1486d08 0x9d2d958 0x9d2d94c - stub
fixme:rpc:RpcMgmtWaitServerListen not waiting for server calls to finish
fixme:ntdll:NtFsControlFile FSCTL_PIPE_IMPERSONATE: impersonating self
fixme:ntdll:NtFsControlFile FSCTL_PIPE_IMPERSONATE: impersonating self
fixme:ntdll:NtFsControlFile FSCTL_PIPE_IMPERSONATE: impersonating self
fixme:ntdll:NtFsControlFile FSCTL_PIPE_IMPERSONATE: impersonating self
fixme:ntdll:NtFsControlFile FSCTL_PIPE_IMPERSONATE: impersonating self
fixme:msi:MsiSourceListGetInfoW Unhandled context 4
err:msi:ready_media Cabinet not found: L"Z:\\home\\helder\\cd 1\\Bin.cab"
err:msi:ACTION_InstallFiles Failed to ready media for L"_A830AAADA89B45FDB85FCB546AE12FAE"
err:msi:ITERATE_Actions Execution halted, action L"InstallFinalize" returned 1603
err:ole:ClientRpcChannelBuffer_SendReceive called from wrong apartment, should have been 0x1c00000039
err:ole:xCall RpcChannelBuffer SendReceive failed, 8001010e
in wine have this error:
> Error: -1603 Fatal error during installation.
Consult Windows Installer Help (Msi.chm) or MSDN for more information. Thank you for help...

---

### Post by desktorp on 2011-06-15
If you are unable to get help here, please try posting this output, with your system information and all that good stuff, to [the Wine user forum]("http://forum.winehq.org/index.php").  Some of the more skilled troubleshooters do not use Ubuntu.  If I had to take a shot in the dark, I'd say you're possibly missing some (Microsoft?) components.

I'm only guessing this because of the line that says: "fixme:storage:create_storagefile Storage share **mode not implemented**."  This could be one of those things where you have to identify and obtain a missing .dll and run it as native, etc..

Good luck and sorry I'm not much help at this step of your problem.

---

