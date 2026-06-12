---
title: "Crysis Fails to start"
date: 2009-05-22
forum: Wine
---

### Post by Gothamite on 2009-05-22
I did everything in the how to I found at winehq.org, but Crysis still will not start. Here is the terminal output: 

[QUOTEskipper@skipper-desktop:~$ cd /media/cdrom0
skipper@skipper-desktop:/media/cdrom0$  wine AutoRunCD.exe -h
wine: Unhandled page fault on write access to 0x00650180 at address 0x7ee7d922 (thread 0029), starting debugger...
Unhandled exception: page fault on write access to 0x00650180 in 32-bit code (0x7ee7d922).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:7ee7d922 ESP:0064e6b0 EBP:0064e748 EFLAGS:00010246(  R- --  I  Z- -P- )
 EAX:006500e0 EBX:7ee7f10c ECX:00000000 EDX:00001000
 ESI:006608cc EDI:0065d000
Stack dump:
0x0064e6b0:  0065d000 00001000 00000080 00000000
0x0064e6c0:  00114088 00000000 00000001 0064e738
0x0064e6d0:  0064e734 00113f88 006500e0 00001000
0x0064e6e0:  00640000 00650000 006608cc 7bc34cf1
0x0064e6f0:  00000000 0064e730 00110014 7bc3469f
0x0064e700:  00110014 7bc91448 0064e748 7bc43eff
Backtrace:
=>0 0x7ee7d922 in winedevice (+0xd922) (0x0064e748)
  1 0x7ee7df7b in winedevice (+0xdf7b) (0x0064e9e8)
  2 0x7ee54207 in advapi32 (+0x34207) (0x0064ea38)
  3 0x7bc7102e call_thread_entry_point+0xe() in ntdll (0x0064ea48)
  4 0x7bc71382 in ntdll (+0x61382) (0x0064eae8)
  5 0x7bc72425 in ntdll (+0x62425) (0x0064f3d8)
  6 0xb7d984fb start_thread+0xcb() in libpthread.so.0 (0x0064f4c8)
0x7ee7d922: movl    $0x0,0xa0(%eax)
Modules:
Module    Address            Debug info    Name (28 modules)
PE      650000-  661000    Deferred        sfdrv01.sys
ELF    7b800000-7b944000    Deferred        kernel32<elf>
  \-PE    7b820000-7b944000    \               kernel32
ELF    7bc00000-7bcad000    Export          ntdll<elf>
  \-PE    7bc10000-7bcad000    \               ntdll
ELF    7bf00000-7bf03000    Deferred        <wine-loader>
ELF    7ecf4000-7ed5f000    Deferred        msvcrt<elf>
  \-PE    7ed00000-7ed5f000    \               msvcrt
ELF    7ed5f000-7ed75000    Deferred        hal<elf>
  \-PE    7ed60000-7ed75000    \               hal
ELF    7ed75000-7eddf000    Deferred        rpcrt4<elf>
  \-PE    7ed80000-7eddf000    \               rpcrt4
ELF    7eddf000-7ee18000    Deferred        ntoskrnl<elf>
  \-PE    7edf0000-7ee18000    \               ntoskrnl
ELF    7ee18000-7ee6c000    Export          advapi32<elf>
  \-PE    7ee20000-7ee6c000    \               advapi32
ELF    7ee6c000-7ee80000    Export          winedevice<elf>
  \-PE    7ee70000-7ee80000    \               winedevice
ELF    7ee80000-7ee98000    Deferred        libnsl.so.1
ELF    7ee98000-7eea1000    Deferred        libnss_compat.so.2
ELF    7efce000-7eff3000    Deferred        libm.so.6
ELF    7eff5000-7f000000    Deferred        libnss_files.so.2
ELF    b7c30000-b7c3a000    Deferred        libnss_nis.so.2
ELF    b7c3f000-b7c43000    Deferred        libdl.so.2
ELF    b7c43000-b7d92000    Deferred        libc.so.6
ELF    b7d93000-b7dab000    Export          libpthread.so.0
ELF    b7db8000-b7ef3000    Deferred        libwine.so.1
ELF    b7ef5000-b7f11000    Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
00000008 
    00000009    0
0000000a 
    0000000b    0
0000000c 
    00000028    0
    00000023    0
    0000001c    0
    00000017    0
    00000013    0
    00000012    0
    0000000e    0
    0000000d    0
0000000f 
    0000001d    0
    0000001b    0
    00000016    0
    00000014    0
    00000011    0
    00000010    0
00000018 
    0000001f    0
    0000001e    0
    0000001a    0
    00000019    0
00000020 
    00000024    0
    00000022    0
    00000021    0
00000025 (D) C:\windows\system32\winedevice.exe
    00000029    0 <==
    00000027    0
    00000026    0
0000002c 
    0000002d    0
Backtrace:
=>0 0x7ee7d922 in winedevice (+0xd922) (0x0064e748)
  1 0x7ee7df7b in winedevice (+0xdf7b) (0x0064e9e8)
  2 0x7ee54207 in advapi32 (+0x34207) (0x0064ea38)
  3 0x7bc7102e call_thread_entry_point+0xe() in ntdll (0x0064ea48)
  4 0x7bc71382 in ntdll (+0x61382) (0x0064eae8)
  5 0x7bc72425 in ntdll (+0x62425) (0x0064f3d8)
  6 0xb7d984fb start_thread+0xcb() in libpthread.so.0 (0x0064f4c8)
wine: Unhandled page fault on write access to 0x00650178 at address 0x7ee7d922 (thread 0032), starting debugger...
Unhandled exception: page fault on write access to 0x00650178 in 32-bit code (0x7ee7d922).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:7ee7d922 ESP:0064e6b0 EBP:0064e748 EFLAGS:00010246(  R- --  I  Z- -P- )
 EAX:006500d8 EBX:7ee7f10c ECX:00000000 EDX:00001000
 ESI:006570bc EDI:00655000
Stack dump:
0x0064e6b0:  00655000 00001000 00000080 00000000
0x0064e6c0:  00114088 00000000 00000001 0064e738
0x0064e6d0:  0064e734 00113f88 006500d8 00001000
0x0064e6e0:  00640000 00650000 006570bc 7bc34cf1
0x0064e6f0:  00000000 0064e730 00110014 7bc3469f
0x0064e700:  00110014 7bc91448 0064e748 7bc43eff
Backtrace:
=>0 0x7ee7d922 in winedevice (+0xd922) (0x0064e748)
  1 0x7ee7df7b in winedevice (+0xdf7b) (0x0064e9e8)
  2 0x7ee54207 in advapi32 (+0x34207) (0x0064ea38)
  3 0x7bc7102e call_thread_entry_point+0xe() in ntdll (0x0064ea48)
  4 0x7bc71382 in ntdll (+0x61382) (0x0064eae8)
  5 0x7bc72425 in ntdll (+0x62425) (0x0064f3d8)
  6 0xb7db84fb start_thread+0xcb() in libpthread.so.0 (0x0064f4c8)
0x7ee7d922: movl    $0x0,0xa0(%eax)
Modules:
Module    Address            Debug info    Name (24 modules)
PE      650000-  658000    Deferred        sfhlp02.sys
ELF    7b800000-7b944000    Deferred        kernel32<elf>
  \-PE    7b820000-7b944000    \               kernel32
ELF    7bc00000-7bcad000    Export          ntdll<elf>
  \-PE    7bc10000-7bcad000    \               ntdll
ELF    7bf00000-7bf03000    Deferred        <wine-loader>
ELF    7ed75000-7eddf000    Deferred        rpcrt4<elf>
  \-PE    7ed80000-7eddf000    \               rpcrt4
ELF    7eddf000-7ee18000    Deferred        ntoskrnl<elf>
  \-PE    7edf0000-7ee18000    \               ntoskrnl
ELF    7ee18000-7ee6c000    Export          advapi32<elf>
  \-PE    7ee20000-7ee6c000    \               advapi32
ELF    7ee6c000-7ee80000    Export          winedevice<elf>
  \-PE    7ee70000-7ee80000    \               winedevice
ELF    7ee80000-7ee98000    Deferred        libnsl.so.1
ELF    7ee98000-7eea1000    Deferred        libnss_compat.so.2
ELF    7efce000-7eff3000    Deferred        libm.so.6
ELF    7eff5000-7f000000    Deferred        libnss_files.so.2
ELF    b7c50000-b7c5a000    Deferred        libnss_nis.so.2
ELF    b7c5f000-b7c63000    Deferred        libdl.so.2
ELF    b7c63000-b7db2000    Deferred        libc.so.6
ELF    b7db3000-b7dcb000    Export          libpthread.so.0
ELF    b7dd8000-b7f13000    Deferred        libwine.so.1
ELF    b7f15000-b7f31000    Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
00000008 
    00000009    0
0000000a 
    0000000b    0
0000000c 
    00000031    0
    00000023    0
    0000001c    0
    00000017    0
    00000013    0
    00000012    0
    0000000e    0
    0000000d    0
0000000f 
    0000001d    0
    0000001b    0
    00000016    0
    00000014    0
    00000011    0
    00000010    0
00000018 
    0000001f    0
    0000001e    0
    0000001a    0
    00000019    0
00000020 
    00000024    0
    00000022    0
    00000021    0
0000002c 
    0000002d    0
0000002e (D) C:\windows\system32\winedevice.exe
    00000032    0 <==
    00000030    0
    0000002f    0
Backtrace:
=>0 0x7ee7d922 in winedevice (+0xd922) (0x0064e748)
  1 0x7ee7df7b in winedevice (+0xdf7b) (0x0064e9e8)
  2 0x7ee54207 in advapi32 (+0x34207) (0x0064ea38)
  3 0x7bc7102e call_thread_entry_point+0xe() in ntdll (0x0064ea48)
  4 0x7bc71382 in ntdll (+0x61382) (0x0064eae8)
  5 0x7bc72425 in ntdll (+0x62425) (0x0064f3d8)
  6 0xb7db84fb start_thread+0xcb() in libpthread.so.0 (0x0064f4c8)
wine: Call from 0x7b843b46 to unimplemented function ntoskrnl.exe.IoAllocateErrorLogEntry, aborting
wine: Unimplemented function ntoskrnl.exe.IoAllocateErrorLogEntry called at address 0x7b843b46 (thread 0039), starting debugger...
Unhandled exception: unimplemented function ntoskrnl.exe.IoAllocateErrorLogEntry called in 32-bit code (0x7b843b46).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:7b843b46 ESP:0064e664 EBP:0064e6c8 EFLAGS:00200202(   - --  I   - - - )
 EAX:7b82eb11 EBX:7b8b37f8 ECX:00000000 EDX:0064e6ec
 ESI:0064e6ec EDI:00000000
Stack dump:
0x0064e664:  0064e6ec 00000008 7bc48382 7bc91448
0x0064e674:  80000100 00000001 00000000 7b843b46
0x0064e684:  00000002 7edf4ce0 7edf677c 00000000
0x0064e694:  ffffffff 00000000 00000000 00000000
0x0064e6a4:  00000000 00000000 00000000 00000000
0x0064e6b4:  00000000 00000000 00000000 00000000
Backtrace:
=>0 0x7b843b46 in kernel32 (+0x23b46) (0x0064e6c8)
  1 0x7edf4c86 in ntoskrnl (+0x14c86) (0x0064e6f8)
0x7b843b46: movl    0xfffffffc(%ebp),%ebx
Modules:
Module    Address            Debug info    Name (28 modules)
PE      650000-  655040    Deferred        sfsync02.sys
ELF    7b800000-7b944000    Export          kernel32<elf>
  \-PE    7b820000-7b944000    \               kernel32
ELF    7bc00000-7bcad000    Deferred        ntdll<elf>
  \-PE    7bc10000-7bcad000    \               ntdll
ELF    7bf00000-7bf03000    Deferred        <wine-loader>
ELF    7ece9000-7ed54000    Deferred        msvcrt<elf>
  \-PE    7ed00000-7ed54000    \               msvcrt
ELF    7ed54000-7ed6a000    Deferred        hal<elf>
  \-PE    7ed60000-7ed6a000    \               hal
ELF    7ed6a000-7edd4000    Deferred        rpcrt4<elf>
  \-PE    7ed80000-7edd4000    \               rpcrt4
ELF    7edd4000-7ee0d000    Export          ntoskrnl<elf>
  \-PE    7ede0000-7ee0d000    \               ntoskrnl
ELF    7ee0d000-7ee61000    Deferred        advapi32<elf>
  \-PE    7ee20000-7ee61000    \               advapi32
ELF    7ee61000-7ee75000    Deferred        winedevice<elf>
  \-PE    7ee70000-7ee75000    \               winedevice
ELF    7ee75000-7ee80000    Deferred        libnss_files.so.2
ELF    7ee80000-7ee98000    Deferred        libnsl.so.1
ELF    7ee98000-7eea1000    Deferred        libnss_compat.so.2
ELF    7efce000-7eff3000    Deferred        libm.so.6
ELF    7eff6000-7f000000    Deferred        libnss_nis.so.2
ELF    b7c9e000-b7ca2000    Deferred        libdl.so.2
ELF    b7ca2000-b7df1000    Deferred        libc.so.6
ELF    b7df2000-b7e0a000    Deferred        libpthread.so.0
ELF    b7e17000-b7f52000    Deferred        libwine.so.1
ELF    b7f54000-b7f70000    Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
00000008 
    00000009    0
0000000a 
    0000000b    0
0000000c 
    00000038    0
    00000023    0
    0000001c    0
    00000017    0
    00000013    0
    00000012    0
    0000000e    0
    0000000d    0
0000000f 
    0000001d    0
    0000001b    0
    00000016    0
    00000014    0
    00000011    0
    00000010    0
00000018 
    0000001f    0
    0000001e    0
    0000001a    0
    00000019    0
00000020 
    00000024    0
    00000022    0
    00000021    0
0000002c 
    0000002d    0
00000035 (D) C:\windows\system32\winedevice.exe
    00000039    0 <==
    00000037    0
    00000036    0
Backtrace:
=>0 0x7b843b46 in kernel32 (+0x23b46) (0x0064e6c8)
  1 0x7edf4c86 in ntoskrnl (+0x14c86) (0x0064e6f8)
wine: Call from 0x7b843b46 to unimplemented function ntoskrnl.exe.IoAllocateErrorLogEntry, aborting
err:ntlm:SECUR32_initNTLMSP ntlm_auth was not found or is outdated. Make sure that ntlm_auth >= 3.0.25 is in your path.
err:ntlm:SECUR32_initNTLMSP Usually, you can find it in the winbind package of your distribution.
fixme:advapi:RegisterTraceGuidsW 0x100778a 0x100a060 0x1001818 1 0x33fe78 (null) (null) 0x100a068
fixme:advapi:RegisterTraceGuidsW 0x100778a 0x100a080 0x1001808 1 0x33fe78 (null) (null) 0x100a088
fixme:advapi:RegisterTraceGuidsW 0x100778a 0x100a0a0 0x10017f8 1 0x33fe78 (null) (null) 0x100a0a8
fixme:advapi:RegisterTraceGuidsW 0x100778a 0x100a0c0 0x10017e8 1 0x33fe78 (null) (null) 0x100a0c8
fixme:advapi:RegisterTraceGuidsW 0x100778a 0x100a0e0 0x10017d8 1 0x33fe78 (null) (null) 0x100a0e8
fixme:advapi:RegisterTraceGuidsW 0x100778a 0x100a100 0x10017c8 1 0x33fe78 (null) (null) 0x100a108
fixme:win:RegisterDeviceNotificationW (hwnd=0x129d10, filter=0x65e90c,flags=0x00000001),
    returns a fake device notification handle!
fixme:mixer:ALSA_MixerInit No master control found on HDA ATI HDMI, disabling mixer
fixme:dsalsa:IDsDriverBufferImpl_SetVolumePan (0x1386d0,0x1385d0): stub
skipper@skipper-desktop:/media/cdrom0$ fixme:ntdll:NtQueryInformationProcess (0xffffffff,info_class=34,0x52a520,0x00000004,0x52a51c) Unknown information class
fixme:ntdll:NtQuerySystemInformation info_class SYSTEM_HANDLE_INFORMATION
fixme:ntdll:NtQueryObject Unsupported information class 3
fixme:debugstr:CheckRemoteDebuggerPresent (0xffffffff)->(0x52940c): Stub!
err:rpc:I_RpcGetBuffer no binding
fixme:d3d:IWineD3DImpl_FillGLCaps OpenGL implementation supports 16 vertex samplers and 16 total samplers
fixme:d3d:IWineD3DImpl_FillGLCaps Expected vertex samplers + MAX_TEXTURES(=8) > combined_samplers
fixme:win:EnumDisplayDevicesW ((null),0,0x529174,0x00000000), stub!
fixme:d3d:IWineD3DImpl_FillGLCaps OpenGL implementation supports 16 vertex samplers and 16 total samplers
fixme:d3d:IWineD3DImpl_FillGLCaps Expected vertex samplers + MAX_TEXTURES(=8) > combined_samplers
fixme:win:EnumDisplayDevicesW ((null),0,0x528cf4,0x00000000), stub!
fixme:psapi:EnumPageFilesA (0x374081e0, 0x509d18) stub
fixme:psapi:EnumPageFilesA (0x374081e0, 0x4d4634) stub
fixme:d3d:IWineD3DImpl_FillGLCaps OpenGL implementation supports 16 vertex samplers and 16 total samplers
fixme:d3d:IWineD3DImpl_FillGLCaps Expected vertex samplers + MAX_TEXTURES(=8) > combined_samplers
fixme:win:EnumDisplayDevicesW ((null),0,0x475820,0x00000000), stub!
fixme:d3d:IWineD3DImpl_FillGLCaps OpenGL implementation supports 16 vertex samplers and 16 total samplers
fixme:d3d:IWineD3DImpl_FillGLCaps Expected vertex samplers + MAX_TEXTURES(=8) > combined_samplers
fixme:win:EnumDisplayDevicesW ((null),0,0x4753a0,0x00000000), stub!
fixme:d3d:IWineD3DImpl_FillGLCaps OpenGL implementation supports 16 vertex samplers and 16 total samplers
fixme:d3d:IWineD3DImpl_FillGLCaps Expected vertex samplers + MAX_TEXTURES(=8) > combined_samplers
fixme:win:EnumDisplayDevicesW ((null),0,0x475824,0x00000000), stub!
fixme:d3d:IWineD3DImpl_FillGLCaps OpenGL implementation supports 16 vertex samplers and 16 total samplers
fixme:d3d:IWineD3DImpl_FillGLCaps Expected vertex samplers + MAX_TEXTURES(=8) > combined_samplers
fixme:win:EnumDisplayDevicesW ((null),0,0x4753a4,0x00000000), stub!
fixme:ntdll:server_ioctl_file Unsupported ioctl 2d0c04 (device=2d access=0 func=301 method=0)
fixme:ntdll:server_ioctl_file Unsupported ioctl 2d1400 (device=2d access=0 func=500 method=0)
fixme:ntdll:server_ioctl_file Unsupported ioctl 2d0c04 (device=2d access=0 func=301 method=0)
fixme:ntdll:server_ioctl_file Unsupported ioctl 2d1400 (device=2d access=0 func=500 method=0)
fixme:ntdll:NtQueryInformationProcess (process=0xffffffff) Unimplemented information class: ProcessDeviceMap
fixme:ntdll:NtQueryInformationProcess (process=0xffffffff) Unimplemented information class: ProcessDeviceMap
fixme:ntdll:NtQueryInformationProcess (process=0xffffffff) Unimplemented information class: ProcessDeviceMap
fixme:ntdll:NtQueryInformationProcess (process=0xffffffff) Unimplemented information class: ProcessDeviceMap
fixme:ntdll:NtQueryInformationProcess (process=0xffffffff) Unimplemented information class: ProcessDeviceMap
fixme:ntdll:NtQueryInformationProcess (process=0xffffffff) Unimplemented information class: ProcessDeviceMap
fixme:ntdll:NtQueryInformationProcess (process=0xffffffff) Unimplemented information class: ProcessDeviceMap
fixme:ntdll:NtQueryInformationProcess (process=0xffffffff) Unimplemented information class: ProcessDeviceMap
fixme:ntdll:NtQueryInformationProcess (process=0xffffffff) Unimplemented information class: ProcessDeviceMap
fixme:ntdll:NtQueryInformationProcess (process=0xffffffff) Unimplemented information class: ProcessDeviceMap
fixme:ntdll:NtQueryInformationProcess (process=0xffffffff) Unimplemented information class: ProcessDeviceMap
fixme:ntdll:NtQueryInformationProcess (process=0xffffffff) Unimplemented information class: ProcessDeviceMap
fixme:ntdll:NtQueryInformationProcess (process=0xffffffff) Unimplemented information class: ProcessDeviceMap
fixme:ntdll:NtQueryInformationProcess (process=0xffffffff) Unimplemented information class: ProcessDeviceMap
fixme:ntdll:NtQueryInformationProcess (process=0xffffffff) Unimplemented information class: ProcessDeviceMap
fixme:ntdll:NtQueryInformationProcess (process=0xffffffff) Unimplemented information class: ProcessDeviceMap
fixme:ntdll:NtQueryInformationProcess (process=0xffffffff) Unimplemented information class: ProcessDeviceMap
fixme:ntdll:NtQueryInformationProcess (process=0xffffffff) Unimplemented information class: ProcessDeviceMap
fixme:ntdll:NtQueryInformationProcess (process=0xffffffff) Unimplemented information class: ProcessDeviceMap
fixme:ntdll:NtQueryInformationProcess (process=0xffffffff) Unimplemented information class: ProcessDeviceMap
fixme:ntdll:NtQueryInformationProcess (process=0xffffffff) Unimplemented information class: ProcessDeviceMap
fixme:ntdll:NtQueryInformationProcess (process=0xffffffff) Unimplemented information class: ProcessDeviceMap
fixme:ntdll:NtQueryInformationProcess (process=0xffffffff) Unimplemented information class: ProcessDeviceMap
fixme:file:Wow64DisableWow64FsRedirection 0x375f774b
fixme:file:Wow64RevertWow64FsRedirection 0x375f774b
fixme:ntdll:NtQuerySystemInformation (0x00000007,0x501f84,0x00000018,(nil)) stub
fixme:ntdll:server_ioctl_file Unsupported ioctl 4d0008 (device=4d access=0 func=2 method=0)
fixme:cursor:SetSystemCursor (0x10de,00007f00),stub!
fixme:cursor:CURSORICON_CreateIconFromANI Loading all frames for .ani cursors not implemented.
fixme:cursor:SetSystemCursor (0x11d6,00007f00),stub!
fixme:cursor:CURSORICON_CreateIconFromANI Loading all frames for .ani cursors not implemented.
fixme:cursor:SetSystemCursor (0x11de,00007f8a),stub!
fixme:cursor:CURSORICON_CreateIconFromANI Loading all frames for .ani cursors not implemented.
fixme:cursor:SetSystemCursor (0x11e6,00007f03),stub!
fixme:cursor:CURSORICON_CreateIconFromANI Loading all frames for .ani cursors not implemented.
fixme:cursor:SetSystemCursor (0x11ee,00007f01),stub!
fixme:cursor:CURSORICON_CreateIconFromANI Loading all frames for .ani cursors not implemented.
fixme:cursor:SetSystemCursor (0x11f6,00007f88),stub!
fixme:cursor:CURSORICON_CreateIconFromANI Loading all frames for .ani cursors not implemented.
fixme:cursor:SetSystemCursor (0x11fe,00007f86),stub!
fixme:cursor:CURSORICON_CreateIconFromANI Loading all frames for .ani cursors not implemented.
fixme:cursor:SetSystemCursor (0x1206,00007f83),stub!
fixme:cursor:CURSORICON_CreateIconFromANI Loading all frames for .ani cursors not implemented.
fixme:cursor:SetSystemCursor (0x120e,00007f82),stub!
fixme:cursor:CURSORICON_CreateIconFromANI Loading all frames for .ani cursors not implemented.
fixme:cursor:SetSystemCursor (0x1216,00007f84),stub!
fixme:cursor:CURSORICON_CreateIconFromANI Loading all frames for .ani cursors not implemented.
fixme:cursor:SetSystemCursor (0x121e,00007f04),stub!
fixme:cursor:CURSORICON_CreateIconFromANI Loading all frames for .ani cursors not implemented.
fixme:cursor:SetSystemCursor (0x1226,00007f02),stub!
fixme:cursor:SetSystemCursor (0x10de,00007f00),stub!
fixme:cursor:SetSystemCursor (0x112e,00007f8a),stub!
fixme:cursor:SetSystemCursor (0x1136,00007f00),stub!
fixme:cursor:SetSystemCursor (0x1146,00007f03),stub!
fixme:cursor:SetSystemCursor (0x114e,00007f01),stub!
fixme:cursor:SetSystemCursor (0x115e,00007f88),stub!
fixme:cursor:SetSystemCursor (0x116e,00007f86),stub!
fixme:cursor:SetSystemCursor (0x117e,00007f83),stub!
fixme:cursor:SetSystemCursor (0x118e,00007f85),stub!
fixme:cursor:SetSystemCursor (0x119e,00007f82),stub!
fixme:cursor:SetSystemCursor (0x11ae,00007f84),stub!
fixme:cursor:SetSystemCursor (0x11be,00007f04),stub!
fixme:cursor:SetSystemCursor (0x11ce,00007f02),stub!
fixme:ntdll:NtQueryInformationProcess (process=0xffffffff) Unimplemented information class: ProcessDeviceMap
fixme:ntdll:NtQuerySystemInformation info_class SYSTEM_HANDLE_INFORMATION
fixme:ntdll:NtQueryObject Unsupported information class 3
fixme:debugstr:CheckRemoteDebuggerPresent (0xffffffff)->(0x53f940): Stub!
err:rpc:I_RpcGetBuffer no binding
fixme:powrprof:DllMain (0x7bff0000, 1, (nil)) not fully implemented
ALSA lib pcm_dmix.c:874:(snd_pcm_dmix_open) unable to open slave
fixme:mixer:ALSA_MixerInit No master control found on HDA ATI HDMI, disabling mixer

][/quote]

By the way I recently updated from Wine 1.1.19 to 1.1.21 and whenever I start a program under wine it will run, but after  I updated wine it always gives me this error three times before a program starts:
 "The program winedevice.exe has encounterd a serious problem and needs to close. We are sorry for the inconvenience" These three errors make a lot of terminal output just so you know.

Any help would be great Thanks.

---

### Post by cogadh on 2009-05-22
Use the forum [CODE] tags, not the [QUOTE] tags, it will make that error output much easier to read.

---

### Post by asdfoo on 2009-05-22
The flood of messages is because you have a device driver instatlled in your Wine prefix which loads when Wine loads, eg you installed WMP which installs something todo with cd burning, or maybe you installed some other app.  

Use a new prefix and it won't happen.

---

