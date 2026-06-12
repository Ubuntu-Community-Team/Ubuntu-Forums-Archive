---
title: "Cannot install office 2003 service pack 3"
date: 2009-10-27
forum: Wine
---

### Post by bailout on 2009-10-27
I am running ubuntu 9.04 and wine 1.1.32. I have installed office 2003 pro typical install and it runs. I have tried installing sp3 but it fails. The installer runs, shows the user agreement, extracts the patch and comes up with a message saying 'the update cannot be applied'. 

I have searched the forums and found a couple of similar posts but no resolution. There are a couple of bug reports on the issue which indicate it has been fixed. One suggested that the 2003 cd needed to be in but I have tried that. 

One line from the log is 
err:msi:ready_media Cabinet not found: L"C:\\windows\\Installer\\L2561403.CAB" 

The cab file referenced is on the install cd which was in the drive. 

From searching the forum I did see a recommendation to use a native dll, riched20, when running office 2003. I don't thiink this was intended to help the sp instal but I tried both ways and no difference. 

Has anyone got a fix for this? I am new to wine so I may have missed something basic. 

thanks 
```

fixme:reg:RegSetKeySecurity :(0x74,4,0x149d18): stub 
fixme:reg:RegSetKeySecurity :(0x7c,4,0x14af98): stub 
fixme:ntoskrnl:KeInitializeMutex stub: 0x131750, 1 
fixme:ntoskrnl:KeInitializeMutex stub: 0x130f18, 1 
fixme:ntoskrnl:KeInitializeMutex stub: 0x131040, 1 
fixme:ntoskrnl:KeInitializeSpinLock stub: 0x667e94 
wine: Call from 0x7b843983 to unimplemented function ntoskrnl.exe.IoGetCurrentProcess, aborting 
wine: Unimplemented function ntoskrnl.exe.IoGetCurrentProcess called at address 0x7b843983 (thread 0024), starting debugger... 
Unhandled exception: unimplemented function ntoskrnl.exe.IoGetCurrentProcess called in 32-bit code (0x7b843983). 
Register dump: 
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b 
 EIP:7b843983 ESP:0064e6c8 EBP:0064e72c EFLAGS:00200246(   - --  I  Z- -P- ) 
 EAX:7b82e84d EBX:7b8b4ff4 ECX:00000000 EDX:0064e750 
 ESI:0064e750 EDI:7ee9a4a0 
Stack dump: 
0x0064e6c8:  0064e750 00000008 0000003c 80000100 
0x0064e6d8:  00000001 00000000 7b843983 00000002 
0x0064e6e8:  7ede6620 7ede84fe 00667f24 00000078 
0x0064e6f8:  0064e728 7ede52ca 00110000 00000000 
0x0064e708:  00000078 00000008 0064e740 7ede52ca 
0x0064e718:  7bc96ff4 00667f34 7b84391a 7ee99ff4 
Backtrace: 
=>0 0x7b843983 in kernel32 (+0x23983) (0x0064e72c) 
  1 0x7ede65a8 in ntoskrnl (+0x165a8) (0x0064e75c) 
  2 0x7eddd580 in ntoskrnl (+0xd580) (0x0064e9f8) 
  3 0x7ee98326 in winedevice (+0x8326) (0x0064ea48) 
  4 0x7ee3e4ec in advapi32 (+0x2e4ec) (0x0064ea98) 
  5 0x7bc6cf04 call_thread_func+0xc() in ntdll (0x0064eaa8) 
  6 0x7bc6d120 call_thread_entry_point+0x70() in ntdll (0x0064eb78) 
  7 0x7bc7536b in ntdll (+0x6536b) (0x0064f3b8) 
  8 0xb7de24ff start_thread+0xbf() in libpthread.so.0 (0x0064f4b8) 
  9 0xb7d5d49e __clone+0x5e() in libc.so.6 (0x00000000) 
0x7b843983: subl   $4,%esp 
Modules: 
Module   Address         Debug info   Name (30 modules) 
PE     650000-  66a260   Deferred        snapman.sys 
ELF   7b800000-7b972000   Export          kernel32<elf> 
  \-PE   7b820000-7b972000   \               kernel32 
ELF   7bc00000-7bcb3000   Export          ntdll<elf> 
  \-PE   7bc10000-7bcb3000   \               ntdll 
ELF   7bf00000-7bf04000   Deferred        <wine-loader> 
ELF   7ecbc000-7ecd3000   Deferred        hal<elf> 
  \-PE   7ecc0000-7ecd3000   \               hal 
ELF   7ecd3000-7ed42000   Deferred        msvcrt<elf> 
  \-PE   7ece0000-7ed42000   \               msvcrt 
ELF   7ed42000-7edb0000   Deferred        rpcrt4<elf> 
  \-PE   7ed50000-7edb0000   \               rpcrt4 
ELF   7edb0000-7edc5000   Deferred        system.drv16.so 
PE   7edc0000-7edc5000   Deferred        system.drv16 
ELF   7edc5000-7ee00000   Export          ntoskrnl<elf> 
  \-PE   7edd0000-7ee00000   \               ntoskrnl 
ELF   7ee00000-7ee58000   Export          advapi32<elf> 
  \-PE   7ee10000-7ee58000   \               advapi32 
ELF   7ee58000-7ee64000   Deferred        libnss_files.so.2 
ELF   7ee64000-7ee7d000   Deferred        libnsl.so.1 
ELF   7ee7d000-7ee86000   Deferred        libnss_compat.so.2 
ELF   7ee86000-7ee9b000   Export          winedevice<elf> 
  \-PE   7ee90000-7ee9b000   \               winedevice 
ELF   7efc5000-7efeb000   Deferred        libm.so.6 
ELF   7eff5000-7f000000   Deferred        libnss_nis.so.2 
ELF   b7c75000-b7c79000   Deferred        libdl.so.2 
ELF   b7c79000-b7ddc000   Export          libc.so.6 
ELF   b7ddc000-b7df5000   Export          libpthread.so.0 
ELF   b7e0a000-b7f46000   Deferred        libwine.so.1 
ELF   b7f48000-b7f66000   Deferred        ld-linux.so.2 
Threads: 
process  tid      prio (all id:s are in hex) 
00000008 
   00000009    0 
0000000a 
   0000000b    0 
0000000e 
   00000023    0 
   0000001f    0 
   0000001c    0 
   00000015    0 
   00000014    0 
   00000010    0 
   0000000f    0 
00000011 
   00000018    0 
   00000017    0 
   00000016    0 
   00000013    0 
   00000012    0 
00000019 
   0000001e    0 
   0000001d    0 
   0000001b    0 
   0000001a    0 
00000020 (D) C:\windows\system32\winedevice.exe 
   00000024    0 <== 
   00000022    0 
   00000021    0 
Backtrace: 
=>0 0x7b843983 in kernel32 (+0x23983) (0x0064e72c) 
  1 0x7ede65a8 in ntoskrnl (+0x165a8) (0x0064e75c) 
  2 0x7eddd580 in ntoskrnl (+0xd580) (0x0064e9f8) 
  3 0x7ee98326 in winedevice (+0x8326) (0x0064ea48) 
  4 0x7ee3e4ec in advapi32 (+0x2e4ec) (0x0064ea98) 
  5 0x7bc6cf04 call_thread_func+0xc() in ntdll (0x0064eaa8) 
  6 0x7bc6d120 call_thread_entry_point+0x70() in ntdll (0x0064eb78) 
  7 0x7bc7536b in ntdll (+0x6536b) (0x0064f3b8) 
  8 0xb7de24ff start_thread+0xbf() in libpthread.so.0 (0x0064f4b8) 
  9 0xb7d5d49e __clone+0x5e() in libc.so.6 (0x00000000) 
wine: Call from 0x7b843983 to unimplemented function ntoskrnl.exe.IoGetCurrentProcess, aborting 
wine: Call from 0x7b843983 to unimplemented function ntoskrnl.exe.IoGetCurrentProcess, aborting 
fixme:advapi:CheckTokenMembership ((nil) 0x144fc8 0x32fd28) stub! 
fixme:advapi:DecryptFileA "C:\\windows\\temp\\IXP000.TMP\\" 00000000 
fixme:advapi:LookupAccountNameW (null) L"me" (nil) 0x33c378 (nil) 0x33c37c 0x33c370 - stub 
fixme:advapi:LookupAccountNameW (null) L"me" 0x15e5e0 0x33c378 0x15bf30 0x33c37c 0x33c370 - stub 
fixme:msi:MsiSourceListGetInfoW Unhandled context 4 
fixme:msi:MsiSourceListGetInfoW Unhandled context 4 
fixme:advapi:CheckTokenMembership ((nil) 0xf9fef0 0x158e3ac) stub! 
fixme:shell:DllCanUnloadNow stub 
fixme:msi:ACTION_HandleStandardAction unhandled standard action L"SetODBCFolders" 
fixme:msi:msi_unimplemented_action_stub RemoveExistingProducts -> 76 ignored L"Upgrade" table values 
fixme:mscoree:LoadLibraryShim (0x7e01c88c L"fusion.dll", (nil), (nil), 0x33c7d0): semi-stub 
fixme:msi:resolve_keypath UNIMPLEMENTED keypath as ODBC Source 
fixme:msi:msi_unimplemented_action_stub UnpublishComponents -> 807 ignored L"PublishComponent" table values 
err:rpc:I_RpcGetBuffer no binding 
fixme:msi:msi_unimplemented_action_stub DeleteServices -> 2 ignored L"ServiceControl" table values 
fixme:msi:msi_unimplemented_action_stub UnregisterTypeLibraries -> 69 ignored L"TypeLib" table values 
fixme:msi:msi_unimplemented_action_stub UnregisterFonts -> 191 ignored L"Font" table values 
fixme:msi:msi_unimplemented_action_stub RemoveRegistryValues -> 324 ignored L"RemoveRegistry" table values 
fixme:msi:msi_unimplemented_action_stub UnregisterClassInfo -> 2 ignored L"AppId" table values 
fixme:msi:msi_unimplemented_action_stub UnregisterExtensionInfo -> 78 ignored L"Extension" table values 
fixme:msi:msi_unimplemented_action_stub UnregisterProgIdInfo -> 386 ignored L"ProgId" table values 
fixme:msi:msi_unimplemented_action_stub UnregisterMIMEInfo -> 12 ignored L"MIME" table values 
fixme:msi:msi_unimplemented_action_stub RemoveIniValues -> 2 ignored L"RemoveIniFile" table values 
fixme:msi:msi_unimplemented_action_stub RemoveShortcuts -> 18 ignored L"Shortcut" table values 
fixme:msi:msi_unimplemented_action_stub RemoveDuplicateFiles -> 2 ignored L"DuplicateFile" table values 
fixme:msi:msi_unimplemented_action_stub RemoveFolders -> 62 ignored L"CreateFolder" table values 
fixme:msi:MsiSourceListGetInfoW Unhandled context 4 
err:msi:ready_media Cabinet not found: L"C:\\windows\\Installer\\L2561403.CAB" 
err:msi:ACTION_InstallFiles Failed to ready media 
err:msi:ITERATE_Actions Execution halted, action L"InstallExecute" returned 1603

```

---

### Post by dca on 2009-11-06
I can't install SPs for any Office vers in Wine...

---

