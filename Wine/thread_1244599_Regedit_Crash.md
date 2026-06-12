---
title: "Regedit Crash"
date: 2009-08-19
forum: Wine
---

### Post by dannymichel on 2009-08-19
```
danny@danny-desktop:~$ regedit
Trying to load PE image for unsupported architecture (AMD-64)
err:module:import_dll Loading library shlwapi.dll (which is needed by L"C:\\windows\\system32\\shell32.dll") failed (error c000007b).
Trying to load PE image for unsupported architecture (AMD-64)
err:module:import_dll Loading library shell32.dll (which is needed by L"C:\\windows\\system32\\comdlg32.dll") failed (error c000007b).
Trying to load PE image for unsupported architecture (AMD-64)
err:module:import_dll Loading library shlwapi.dll (which is needed by L"C:\\windows\\system32\\comdlg32.dll") failed (error c000007b).
Trying to load PE image for unsupported architecture (AMD-64)
err:module:DelayLoadFailureHook failed to delay load comdlg32.dll.GetOpenFileNameW
wine: Call from 0x7b844430 to unimplemented function comdlg32.dll.GetOpenFileNameW, aborting
wine: Unimplemented function comdlg32.dll.GetOpenFileNameW called at address 0x7b844430 (thread 0009), starting debugger...
Unhandled exception: unimplemented function comdlg32.dll.GetOpenFileNameW called in 32-bit code (0x7b8444a3).
Register dump:
 CS:0023 SS:002b DS:002b ES:002b FS:0063 GS:006b
 EIP:7b8444a3 ESP:0032e124 EBP:0032e188 EFLAGS:00000246(   - 00      - IZP1)
 EAX:7b82ebfd EBX:7b8b6ff4 ECX:00000000 EDX:0032e1b4
 ESI:0032e1b4 EDI:7ee42c7c
Stack dump:
0x0032e124:  0032e1b4 00000008 0000003c 80000100
0x0032e134:  00000001 00000000 7b844430 00000002
0x0032e144:  7ee42c7c 7ee42ced f7f85ff4 7b93b7f0
0x0032e154:  7ee42c7c 0032e188 f7e64249 00000001
0x0032e164:  7b93b7f0 7b8af0ff 7b8af079 0032e1a0
0x0032e174:  000d000c 001a0018 7b84443a 7b8b6ff4
Backtrace:
=>0 0x7b8444a3 in kernel32 (+0x244a3) (0x0032e188)
  1 0x7b8669cb DelayLoadFailureHook+0x5b() in kernel32 (0x0032e1c8)
  2 0x7ee3f371 in regedit (+0x1f371) (0x0032e1e8)
  3 0x7ee30d98 in regedit (+0x10d98) (0x0032fb78)
  4 0x7ee3682a FrameWndProc+0x32a() in regedit (0x0032fc98)
  5 0x7ecdf08a WINPROC_wrapper+0x1a() in user32 (0x0032fcc8)
  6 0x7ecdf4da WINPROC_wrapper+0x46a() in user32 (0x0032fd08)
  7 0x7ece57a7 in user32 (+0xb57a7) (0x0032fd48)
  8 0x7eca34c6 DispatchMessageA+0x96() in user32 (0x0032fd88)
  9 0x7ee398ca WinMain+0x47a() in regedit (0x0032fe58)
  10 0x7ee3f4cd main+0xad() in regedit (0x0032fed8)
  11 0x7ee3f408 in regedit (+0x1f408) (0x0032ff08)
  12 0x7b878200 in kernel32 (+0x58200) (0x0032ffe8)
  13 0xf7e66dd7 wine_switch_to_stack+0x17() in libwine.so.1 (0x00000000)
0x7b8444a3: subl	$4,%esp
Modules:
Module	Address			Debug info	Name (51 modules)
ELF	7b800000-7b93e000	Export          kernel32<elf>
  \-PE	7b820000-7b93e000	\               kernel32
ELF	7bc00000-7bcb1000	Deferred        ntdll<elf>
  \-PE	7bc10000-7bcb1000	\               ntdll
ELF	7bf00000-7bf04000	Deferred        <wine-loader>
ELF	7e5d1000-7e607000	Deferred        winspool<elf>
  \-PE	7e5e0000-7e607000	\               winspool
ELF	7e702000-7e735000	Deferred        uxtheme<elf>
  \-PE	7e710000-7e735000	\               uxtheme
ELF	7e735000-7e7fd000	Deferred        comctl32<elf>
  \-PE	7e740000-7e7fd000	\               comctl32
ELF	7e810000-7e819000	Deferred        libxcursor.so.1
ELF	7e819000-7e81e000	Deferred        libxfixes.so.3
ELF	7e81e000-7e822000	Deferred        libxcomposite.so.1
ELF	7e822000-7e82a000	Deferred        libxrandr.so.2
ELF	7e82a000-7e834000	Deferred        libxrender.so.1
ELF	7e834000-7e83a000	Deferred        libxxf86vm.so.1
ELF	7e83a000-7e83d000	Deferred        libxinerama.so.1
ELF	7e83d000-7e85e000	Deferred        imm32<elf>
  \-PE	7e840000-7e85e000	\               imm32
ELF	7e85e000-7e863000	Deferred        libxdmcp.so.6
ELF	7e863000-7e87d000	Deferred        libxcb.so.1
ELF	7e87d000-7e881000	Deferred        libxau.so.6
ELF	7e881000-7e970000	Deferred        libx11.so.6
ELF	7e970000-7e980000	Deferred        libxext.so.6
ELF	7e997000-7ea33000	Deferred        winex11<elf>
  \-PE	7e9b0000-7ea33000	\               winex11
ELF	7ea77000-7ea9e000	Deferred        libexpat.so.1
ELF	7ea9e000-7eacb000	Deferred        libfontconfig.so.1
ELF	7eacb000-7eae1000	Deferred        libz.so.1
ELF	7eae1000-7eb58000	Deferred        libfreetype.so.6
ELF	7eb6f000-7ec10000	Deferred        gdi32<elf>
  \-PE	7eb80000-7ec10000	\               gdi32
ELF	7ec10000-7ed5c000	Export          user32<elf>
  \-PE	7ec30000-7ed5c000	\               user32
ELF	7ed5c000-7edc9000	Deferred        msvcrt<elf>
  \-PE	7ed70000-7edc9000	\               msvcrt
ELF	7edc9000-7ee1e000	Deferred        advapi32<elf>
  \-PE	7ede0000-7ee1e000	\               advapi32
ELF	7ee1e000-7ee74000	Export          regedit<elf>
  \-PE	7ee20000-7ee74000	\               regedit
ELF	7ef9e000-7efaa000	Deferred        libnss_files.so.2
ELF	7efaa000-7efc3000	Deferred        libnsl.so.1
ELF	7efc3000-7efe9000	Deferred        libm.so.6
ELF	7efec000-7eff7000	Deferred        libnss_nis.so.2
ELF	7eff7000-7f000000	Deferred        libnss_compat.so.2
ELF	f7cc7000-f7ccb000	Deferred        libdl.so.2
ELF	f7ccb000-f7e2e000	Deferred        libc.so.6
ELF	f7e2f000-f7e48000	Deferred        libpthread.so.0
ELF	f7e5f000-f7f9a000	Export          libwine.so.1
ELF	f7f9c000-f7fbd000	Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
00000008 (D) C:\windows\system32\regedit.exe
	00000009    0 <==
0000000c 
	00000014    0
	00000013    0
	00000012    0
	0000000e    0
	0000000d    0
0000000f 
	00000016    0
	00000015    0
	00000011    0
	00000010    0
00000017 
	00000018    0
Backtrace:
=>0 0x7b8444a3 in kernel32 (+0x244a3) (0x0032e188)
  1 0x7b8669cb DelayLoadFailureHook+0x5b() in kernel32 (0x0032e1c8)
  2 0x7ee3f371 in regedit (+0x1f371) (0x0032e1e8)
  3 0x7ee30d98 in regedit (+0x10d98) (0x0032fb78)
  4 0x7ee3682a FrameWndProc+0x32a() in regedit (0x0032fc98)
  5 0x7ecdf08a WINPROC_wrapper+0x1a() in user32 (0x0032fcc8)
  6 0x7ecdf4da WINPROC_wrapper+0x46a() in user32 (0x0032fd08)
  7 0x7ece57a7 in user32 (+0xb57a7) (0x0032fd48)
  8 0x7eca34c6 DispatchMessageA+0x96() in user32 (0x0032fd88)
  9 0x7ee398ca WinMain+0x47a() in regedit (0x0032fe58)
  10 0x7ee3f4cd main+0xad() in regedit (0x0032fed8)
  11 0x7ee3f408 in regedit (+0x1f408) (0x0032ff08)
  12 0x7b878200 in kernel32 (+0x58200) (0x0032ffe8)
  13 0xf7e66dd7 wine_switch_to_stack+0x17() in libwine.so.1 (0x00000000)
danny@danny-desktop:~$ 


```
i was trying to import a key
any ideas?

---

### Post by NightMKoder on 2009-08-20
Have you been copying things from a windows install? Seems like you overrode something wine needed. rm -rf ~/.wine and start again.

---

