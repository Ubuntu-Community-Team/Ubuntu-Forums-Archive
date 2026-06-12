---
title: "worms world party no anda... pantalla negra."
date: 2009-05-01
forum: Software
---

### Post by granjero on 2009-05-01
estoy tratando de hacer andar el worms world party. se instala bien. pero al ejecutarlo me da este error.

si alguien sabe como solucionarlo le agradecería mucho porque es de las últimas cosas que me ata a micro$chot. 

```


jm@pcjm:~$ wine /media/cdrom0/AUTORUN.EXE 
wine: Call from 0x7b844b20 to unimplemented function ntoskrnl.exe.IoAllocateErrorLogEntry, aborting
wine: Unimplemented function ntoskrnl.exe.IoAllocateErrorLogEntry called at address 0x7b844b20 (thread 001b), starting debugger...
Unhandled exception: unimplemented function ntoskrnl.exe.IoAllocateErrorLogEntry called in 32-bit code (0x7b844b96).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:7b844b96 ESP:7ec2684c EBP:7ec268b0 EFLAGS:00200212(   - 00      - -IA1)
 EAX:7b82eb09 EBX:7b8b3884 ECX:00000000 EDX:00000000
 ESI:00000000 EDI:00000000
Stack dump:
0x7ec2684c:  7ec268d8 00000008 7ec268b4 7bc4384e
0x7ec2685c:  80000100 00000001 00000000 7b844b20
0x7ec2686c:  00000002 7edeab00 7edec5df 7ec268b8
0x7ec2687c:  00110014 7bc336cf 00110014 7bc88444
0x7ec2688c:  7ec268cc 7bc42887 00110048 7ee688ec
0x7ec2689c:  7ec26920 00000000 00110014 7edf4914
Backtrace:
=>1 0x7b844b96 in kernel32 (+0x24b96) (0x7ec268b0)
  2 0x7edeaa95 in ntoskrnl (+0x1aa95) (0x7ec268e0)
  3 0x7ede26f4 in ntoskrnl (+0x126f4) (0x7ec2690c)
  4 0x00451e53 in sfdrv01.sys (+0x1e53) (0x7ec269e8)
  5 0x7ee3e359 in advapi32 (+0x2e359) (0x7ec26a38)
  6 0x7bc6aeae call_thread_entry_point+0xe() in ntdll (0x7ec26a48)
  7 0x7bc6b542 in ntdll (+0x5b542) (0x7ec26ae8)
  8 0x7bc6b772 in ntdll (+0x5b772) (0x7ec273d8)
  9 0xb7e0e4fb start_thread+0xcb() in libpthread.so.0 (0x7ec274c8)
0x7b844b96: movl	0xfffffffc(%ebp),%ebx
Modules:
Module	Address			Debug info	Name (31 modules)
PE	  450000-  461000	Export          sfdrv01.sys
ELF	7b800000-7b92d000	Export          kernel32<elf>
  \-PE	7b820000-7b92d000	\               kernel32
ELF	7bc00000-7bca4000	Export          ntdll<elf>
  \-PE	7bc10000-7bca4000	\               ntdll
ELF	7bf00000-7bf03000	Deferred        <wine-loader>
ELF	7ea77000-7ea8c000	Deferred        hal<elf>
  \-PE	7ea80000-7ea8c000	\               hal
ELF	7eaad000-7eb17000	Deferred        msvcrt<elf>
  \-PE	7eac0000-7eb17000	\               msvcrt
ELF	7ec28000-7ec3b000	Deferred        libresolv.so.2
ELF	7ec3b000-7ec59000	Deferred        iphlpapi<elf>
  \-PE	7ec40000-7ec59000	\               iphlpapi
ELF	7ec59000-7ecba000	Deferred        rpcrt4<elf>
  \-PE	7ec70000-7ecba000	\               rpcrt4
ELF	7edcb000-7ee03000	Export          ntoskrnl<elf>
  \-PE	7edd0000-7ee03000	\               ntoskrnl
ELF	7ee03000-7ee55000	Export          advapi32<elf>
  \-PE	7ee10000-7ee55000	\               advapi32
ELF	7ee55000-7ee69000	Deferred        winedevice<elf>
  \-PE	7ee60000-7ee69000	\               winedevice
ELF	7ee69000-7ee74000	Deferred        libnss_files.so.2
ELF	7ee74000-7ee8c000	Deferred        libnsl.so.1
ELF	7ee8c000-7ee95000	Deferred        libnss_compat.so.2
ELF	7efc8000-7efed000	Deferred        libm.so.6
ELF	7eff6000-7f000000	Deferred        libnss_nis.so.2
ELF	b7cb5000-b7cb9000	Deferred        libdl.so.2
ELF	b7cb9000-b7e08000	Deferred        libc.so.6
ELF	b7e09000-b7e21000	Export          libpthread.so.0
ELF	b7e34000-b7f6a000	Deferred        libwine.so.1
ELF	b7f6c000-b7f88000	Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
00000008 
	00000009    0
0000000a 
	0000000b    0
0000000c 
	0000001a    0
	00000019    0
	00000013    0
	00000012    0
	0000000e    0
	0000000d    0
0000000f 
	00000015    0
	00000014    0
	00000011    0
	00000010    0
00000016 (D) C:\windows\system32\winedevice.exe
	0000001b    0 <==
	00000018    0
	00000017    0
Backtrace:
=>1 0x7b844b96 in kernel32 (+0x24b96) (0x7ec268b0)
  2 0x7edeaa95 in ntoskrnl (+0x1aa95) (0x7ec268e0)
  3 0x7ede26f4 in ntoskrnl (+0x126f4) (0x7ec2690c)
  4 0x00451e53 in sfdrv01.sys (+0x1e53) (0x7ec269e8)
  5 0x7ee3e359 in advapi32 (+0x2e359) (0x7ec26a38)
  6 0x7bc6aeae call_thread_entry_point+0xe() in ntdll (0x7ec26a48)
  7 0x7bc6b542 in ntdll (+0x5b542) (0x7ec26ae8)
  8 0x7bc6b772 in ntdll (+0x5b772) (0x7ec273d8)
  9 0xb7e0e4fb start_thread+0xcb() in libpthread.so.0 (0x7ec274c8)
wine: Call from 0x7b844b20 to unimplemented function ntoskrnl.exe.IoAllocateIrp, aborting
wine: Call from 0x7b844b20 to unimplemented function ntoskrnl.exe.IoCreateSynchronizationEvent, aborting
wine: Unimplemented function ntoskrnl.exe.IoCreateSynchronizationEvent called at address 0x7b844b20 (thread 0022), starting debugger...
Unhandled exception: unimplemented function ntoskrnl.exe.IoCreateSynchronizationEvent called in 32-bit code (0x7b844b96).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:7b844b96 ESP:7ec1c840 EBP:7ec1c8a4 EFLAGS:00200212(   - 00      - -IA1)
 EAX:7b82eb09 EBX:7b8b3884 ECX:00000000 EDX:00000000
 ESI:00000000 EDI:7bc5d320
Stack dump:
0x7ec1c840:  7ec1c8cc 00000008 00000000 00000000
0x7ec1c850:  80000100 00000001 00000000 7b844b20
0x7ec1c860:  00000002 7ede0b00 7ede28a1 0045506c
0x7ec1c870:  00000028 00455048 00000020 00000000
0x7ec1c880:  00000000 00000000 00000000 00000000
0x7ec1c890:  00000000 7edea914 7ec1c914 7ec1c91c
Backtrace:
=>1 0x7b844b96 in kernel32 (+0x24b96) (0x7ec1c8a4)
  2 0x7ede0a95 in ntoskrnl (+0x10a95) (0x7ec1c8d4)
  3 0x7edd8b50 in ntoskrnl (+0x8b50) (0x7ec1c930)
  4 0x004552dc in sfhlp02.sys (+0x52dc) (0x7ec1c9e8)
  5 0x7ee34359 in advapi32 (+0x24359) (0x7ec1ca38)
  6 0x7bc6aeae call_thread_entry_point+0xe() in ntdll (0x7ec1ca48)
  7 0x7bc6b542 in ntdll (+0x5b542) (0x7ec1cae8)
  8 0x7bc6b772 in ntdll (+0x5b772) (0x7ec1d3d8)
  9 0xb7e0d4fb start_thread+0xcb() in libpthread.so.0 (0x7ec1d4c8)
0x7b844b96: movl	0xfffffffc(%ebp),%ebx
Modules:
Module	Address			Debug info	Name (29 modules)
PE	  450000-  458000	Export          sfhlp02.sys
ELF	7b800000-7b92d000	Export          kernel32<elf>
  \-PE	7b820000-7b92d000	\               kernel32
ELF	7bc00000-7bca4000	Export          ntdll<elf>
  \-PE	7bc10000-7bca4000	\               ntdll
ELF	7bf00000-7bf03000	Deferred        <wine-loader>
ELF	7eaa3000-7eb0d000	Deferred        msvcrt<elf>
  \-PE	7eab0000-7eb0d000	\               msvcrt
ELF	7ec1e000-7ec31000	Deferred        libresolv.so.2
ELF	7ec31000-7ec4f000	Deferred        iphlpapi<elf>
  \-PE	7ec40000-7ec4f000	\               iphlpapi
ELF	7ec4f000-7ecb0000	Deferred        rpcrt4<elf>
  \-PE	7ec60000-7ecb0000	\               rpcrt4
ELF	7edc1000-7edf9000	Export          ntoskrnl<elf>
  \-PE	7edd0000-7edf9000	\               ntoskrnl
ELF	7edf9000-7ee4b000	Export          advapi32<elf>
  \-PE	7ee10000-7ee4b000	\               advapi32
ELF	7ee4b000-7ee5f000	Deferred        winedevice<elf>
  \-PE	7ee50000-7ee5f000	\               winedevice
ELF	7ee5f000-7ee6a000	Deferred        libnss_files.so.2
ELF	7ee6a000-7ee74000	Deferred        libnss_nis.so.2
ELF	7ee74000-7ee8c000	Deferred        libnsl.so.1
ELF	7ee8c000-7ee95000	Deferred        libnss_compat.so.2
ELF	7efc8000-7efed000	Deferred        libm.so.6
ELF	b7cb4000-b7cb8000	Deferred        libdl.so.2
ELF	b7cb8000-b7e07000	Deferred        libc.so.6
ELF	b7e08000-b7e20000	Export          libpthread.so.0
ELF	b7e33000-b7f69000	Deferred        libwine.so.1
ELF	b7f6b000-b7f87000	Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
00000008 
	00000009    0
0000000a 
	0000000b    0
0000000c 
	00000021    0
	0000001a    0
	00000013    0
	00000012    0
	0000000e    0
	0000000d    0
0000000f 
	00000015    0
	00000014    0
	00000011    0
	00000010    0
0000001e (D) C:\windows\system32\winedevice.exe
	00000022    0 <==
	00000020    0
	0000001f    0
Backtrace:
=>1 0x7b844b96 in kernel32 (+0x24b96) (0x7ec1c8a4)
  2 0x7ede0a95 in ntoskrnl (+0x10a95) (0x7ec1c8d4)
  3 0x7edd8b50 in ntoskrnl (+0x8b50) (0x7ec1c930)
  4 0x004552dc in sfhlp02.sys (+0x52dc) (0x7ec1c9e8)
  5 0x7ee34359 in advapi32 (+0x24359) (0x7ec1ca38)
  6 0x7bc6aeae call_thread_entry_point+0xe() in ntdll (0x7ec1ca48)
  7 0x7bc6b542 in ntdll (+0x5b542) (0x7ec1cae8)
  8 0x7bc6b772 in ntdll (+0x5b772) (0x7ec1d3d8)
  9 0xb7e0d4fb start_thread+0xcb() in libpthread.so.0 (0x7ec1d4c8)
wine: Call from 0x7b844b20 to unimplemented function ntoskrnl.exe.IoCreateUnprotectedSymbolicLink, aborting
wine: Call from 0x7b844b20 to unimplemented function ntoskrnl.exe.IoCsqInitialize, aborting
wine: Call from 0x7b844b20 to unimplemented function ntoskrnl.exe.IoAllocateErrorLogEntry, aborting
wine: Unimplemented function ntoskrnl.exe.IoAllocateErrorLogEntry called at address 0x7b844b20 (thread 0029), starting debugger...
Unhandled exception: unimplemented function ntoskrnl.exe.IoAllocateErrorLogEntry called in 32-bit code (0x7b844b96).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:7b844b96 ESP:7ec1c824 EBP:7ec1c888 EFLAGS:00200212(   - 00      - -IA1)
 EAX:7b82eb09 EBX:7b8b3884 ECX:00000000 EDX:00000000
 ESI:00000000 EDI:00000000
Stack dump:
0x7ec1c824:  7ec1c8b0 00000008 7bc5bee6 7bc88444
0x7ec1c834:  80000100 00000001 00000000 7b844b20
0x7ec1c844:  00000002 7ede0b00 7ede25df b7cdfd91
0x7ec1c854:  7ec1cb10 7bc46d00 7bc63a0b 7bc88444
0x7ec1c864:  0000005c 7ec1c8c0 7ec1c8fc 7bc4e223
0x7ec1c874:  7ec1c880 00000000 ffffffff 00000000
Backtrace:
=>1 0x7b844b96 in kernel32 (+0x24b96) (0x7ec1c888)
  2 0x7ede0a95 in ntoskrnl (+0x10a95) (0x7ec1c8b8)
  3 0x7edd86f4 in ntoskrnl (+0x86f4) (0x7ec1c8e4)
  4 0x00451753 in sfsync02.sys (+0x1753) (0x7ec1c938)
  5 0x7ee5d0d0 in winedevice (+0xd0d0) (0x7ec1c9e8)
  6 0x7ee34359 in advapi32 (+0x24359) (0x7ec1ca38)
  7 0x7bc6aeae call_thread_entry_point+0xe() in ntdll (0x7ec1ca48)
  8 0x7bc6b542 in ntdll (+0x5b542) (0x7ec1cae8)
  9 0x7bc6b772 in ntdll (+0x5b772) (0x7ec1d3d8)
  10 0xb7e0a4fb start_thread+0xcb() in libpthread.so.0 (0x7ec1d4c8)
0x7b844b96: movl	0xfffffffc(%ebp),%ebx
Modules:
Module	Address			Debug info	Name (31 modules)
PE	  450000-  459000	Export          sfsync02.sys
ELF	7b800000-7b92d000	Export          kernel32<elf>
  \-PE	7b820000-7b92d000	\               kernel32
ELF	7bc00000-7bca4000	Export          ntdll<elf>
  \-PE	7bc10000-7bca4000	\               ntdll
ELF	7bf00000-7bf03000	Deferred        <wine-loader>
ELF	7ea6d000-7ea82000	Deferred        hal<elf>
  \-PE	7ea70000-7ea82000	\               hal
ELF	7eaa3000-7eb0d000	Deferred        msvcrt<elf>
  \-PE	7eab0000-7eb0d000	\               msvcrt
ELF	7ec1e000-7ec31000	Deferred        libresolv.so.2
ELF	7ec31000-7ec4f000	Deferred        iphlpapi<elf>
  \-PE	7ec40000-7ec4f000	\               iphlpapi
ELF	7ec4f000-7ecb0000	Deferred        rpcrt4<elf>
  \-PE	7ec60000-7ecb0000	\               rpcrt4
ELF	7edc1000-7edf9000	Export          ntoskrnl<elf>
  \-PE	7edd0000-7edf9000	\               ntoskrnl
ELF	7edf9000-7ee4b000	Export          advapi32<elf>
  \-PE	7ee10000-7ee4b000	\               advapi32
ELF	7ee4b000-7ee5f000	Export          winedevice<elf>
  \-PE	7ee50000-7ee5f000	\               winedevice
ELF	7ee5f000-7ee6a000	Deferred        libnss_files.so.2
ELF	7ee6a000-7ee74000	Deferred        libnss_nis.so.2
ELF	7ee74000-7ee8c000	Deferred        libnsl.so.1
ELF	7ee8c000-7ee95000	Deferred        libnss_compat.so.2
ELF	7efc8000-7efed000	Deferred        libm.so.6
ELF	b7cb1000-b7cb5000	Deferred        libdl.so.2
ELF	b7cb5000-b7e04000	Deferred        libc.so.6
ELF	b7e05000-b7e1d000	Export          libpthread.so.0
ELF	b7e30000-b7f66000	Deferred        libwine.so.1
ELF	b7f68000-b7f84000	Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
00000008 
	00000009    0
0000000a 
	0000000b    0
0000000c 
	00000028    0
	0000001a    0
	00000013    0
	00000012    0
	0000000e    0
	0000000d    0
0000000f 
	00000015    0
	00000014    0
	00000011    0
	00000010    0
00000025 (D) C:\windows\system32\winedevice.exe
	00000029    0 <==
	00000027    0
	00000026    0
Backtrace:
=>1 0x7b844b96 in kernel32 (+0x24b96) (0x7ec1c888)
  2 0x7ede0a95 in ntoskrnl (+0x10a95) (0x7ec1c8b8)
  3 0x7edd86f4 in ntoskrnl (+0x86f4) (0x7ec1c8e4)
  4 0x00451753 in sfsync02.sys (+0x1753) (0x7ec1c938)
  5 0x7ee5d0d0 in winedevice (+0xd0d0) (0x7ec1c9e8)
  6 0x7ee34359 in advapi32 (+0x24359) (0x7ec1ca38)
  7 0x7bc6aeae call_thread_entry_point+0xe() in ntdll (0x7ec1ca48)
  8 0x7bc6b542 in ntdll (+0x5b542) (0x7ec1cae8)
  9 0x7bc6b772 in ntdll (+0x5b772) (0x7ec1d3d8)
  10 0xb7e0a4fb start_thread+0xcb() in libpthread.so.0 (0x7ec1d4c8)
wine: Call from 0x7b844b20 to unimplemented function ntoskrnl.exe.IoAllocateIrp, aborting
wine: Call from 0x7b844b20 to unimplemented function ntoskrnl.exe.IoAssignResources, aborting
jm@pcjm:~$ fixme:ntdll:find_reg_tz_info Can't find matching timezone information in the registry for bias 180, std (d/m/y): 15/03/2009, dlt (d/m/y): 18/10/2009
fixme:d3d:IWineD3DImpl_FillGLCaps OpenGL implementation supports 32 vertex samplers and 32 total samplers
fixme:d3d:IWineD3DImpl_FillGLCaps Expected vertex samplers + MAX_TEXTURES(=8) > combined_samplers
fixme:win:EnumDisplayDevicesW ((null),0,0x2c7dac,0x00000000), stub!
fixme:x11drv:X11DRV_desktop_SetCurrentMode Cannot change screen BPP from 32 to 8
fixme:d3d:IWineD3DDeviceImpl_CreateAdditionalSwapChain The app requests more than one back buffer, this can't be supported properly. Please configure the application to use double buffering(=1 back buffer) if possible
fixme:d3d:WineD3D_ChoosePixelFormat Add OpenGL context recreation support to SetDepthStencilSurface
fixme:d3d_surface:surface_get_gl_buffer Higher back buffer, returning GL_BACK
fixme:d3d_surface:surface_get_gl_buffer Higher back buffer, returning GL_BACK
fixme:d3d_surface:surface_get_gl_buffer Higher back buffer, returning GL_BACK
err:quartz:FilterGraph2_AddSourceFilter Load (80070003)
fixme:d3d_surface:surface_get_gl_buffer Higher back buffer, returning GL_BACK
fixme:d3d_surface:surface_get_gl_buffer Higher back buffer, returning GL_BACK
fixme:d3d_surface:surface_get_gl_buffer Higher back buffer, returning GL_BACK
fixme:d3d_surface:surface_get_gl_buffer Higher back buffer, returning GL_BACK
fixme:d3d_surface:surface_get_gl_buffer Higher back buffer, returning GL_BACK
fixme:d3d_surface:surface_get_gl_buffer Higher back buffer, returning GL_BACK
fixme:d3d_surface:surface_get_gl_buffer Higher back buffer, returning GL_BACK
fixme:d3d_surface:surface_get_gl_buffer Higher back buffer, returning GL_BACK
fixme:d3d_surface:surface_get_gl_buffer Higher back buffer, returning GL_BACK
fixme:d3d_surface:surface_get_gl_buffer Higher back buffer, returning GL_BACK
fixme:d3d_surface:surface_get_gl_buffer Higher back buffer, returning GL_BACK
fixme:d3d_surface:surface_get_gl_buffer Higher back buffer, returning GL_BACK
fixme:d3d_surface:surface_get_gl_buffer Higher back buffer, returning GL_BACK
fixme:d3d_surface:surface_get_gl_buffer Higher back buffer, returning GL_BACK
fixme:d3d_surface:surface_get_gl_buffer Higher back buffer, returning GL_BACK
fixme:d3d_surface:surface_get_gl_buffer Higher back buffer, returning GL_BACK
fixme:d3d_surface:surface_get_gl_buffer Higher back buffer, returning GL_BACK
fixme:d3d_surface:surface_get_gl_buffer Higher back buffer, returning GL_BACK
fixme:d3d_surface:surface_get_gl_buffer Higher back buffer, returning GL_BACK
fixme:d3d_surface:surface_get_gl_buffer Higher back buffer, returning GL_BACK
fixme:d3d_surface:surface_get_gl_buffer Higher back buffer, returning GL_BACK
fixme:d3d_surface:surface_get_gl_buffer Higher back buffer, returning GL_BACK
fixme:d3d_surface:surface_get_gl_buffer Higher back buffer, returning GL_BACK
fixme:d3d_surface:surface_get_gl_buffer Higher back buffer, returning GL_BACK
fixme:d3d_surface:surface_get_gl_buffer Higher back buffer, returning GL_BACK
fixme:d3d_surface:surface_get_gl_buffer Higher back buffer, returning GL_BACK
fixme:d3d_surface:surface_get_gl_buffer Higher back buffer, returning GL_BACK
fixme:d3d_surface:surface_get_gl_buffer Higher back buffer, returning GL_BACK
fixme:d3d_surface:surface_get_gl_buffer Higher back buffer, returning GL_BACK
fixme:d3d_surface:surface_get_gl_buffer Higher back buffer, returning GL_BACK
fixme:d3d_surface:surface_get_gl_buffer Higher back buffer, returning GL_BACK
fixme:d3d_surface:surface_get_gl_buffer Higher back buffer, returning GL_BACK
fixme:d3d_surface:surface_get_gl_buffer Higher back buffer, returning GL_BACK
fixme:d3d_surface:surface_get_gl_buffer Higher back buffer, returning GL_BACK
fixme:d3d_surface:surface_get_gl_buffer Higher back buffer, returning GL_BACK
fixme:d3d_surface:surface_get_gl_buffer Higher back buffer, returning GL_BACK
fixme:d3d_surface:surface_get_gl_buffer Higher back buffer, returning GL_BACK
fixme:d3d_surface:surface_get_gl_buffer Higher back buffer, returning GL_BACK
fixme:d3d_surface:surface_get_gl_buffer Higher back buffer, returning GL_BACK
fixme:d3d_surface:surface_get_gl_buffer Higher back buffer, returning GL_BACK
fixme:d3d_surface:surface_get_gl_buffer Higher back buffer, returning GL_BACK
fixme:d3d_surface:surface_get_gl_buffer Higher back buffer, returning GL_BACK
fixme:d3d_surface:surface_get_gl_buffer Higher back buffer, returning GL_BACK
fixme:d3d_surface:surface_get_gl_buffer Higher back buffer, returning GL_BACK
fixme:d3d_surface:surface_get_gl_buffer Higher back buffer, returning GL_BACK
fixme:d3d_surface:surface_get_gl_buffer Higher back buffer, returning GL_B
```

lo ejecuto así porque si le doy click al icono que me creo al instalar me pide el cd y no hay forma que ande desde winecfg al poner en la solapa unidades las locaciones donde esta el cd.

probe poniendolo en la compactera, monstandolo en un directorio con -loop y varias otras formas que encontre por inet para que wine levante un cd....

gracias de antemano.

---

