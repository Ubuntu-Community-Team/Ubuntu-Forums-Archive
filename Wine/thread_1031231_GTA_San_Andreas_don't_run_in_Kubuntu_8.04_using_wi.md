---
title: "GTA San Andreas don't run in Kubuntu 8.04 using wine"
date: 2009-01-05
forum: Wine
---

### Post by jonathan bispo on 2009-01-05
Hi everyone...
Before other things, excuse me my bad english, cause I'am brazilian and I'm learning english yet.
Well, I've tried to install GTA in my kubuntu 8.04, but I didn't get success.

When I run 
$ wine setup.exe

in the mount folder of GTA I receive this error:

fixme:ntdll:find_reg_tz_info Can't find matching timezone information in the registry for bias 180, std (d/m/y): 15/02/2009, dlt (d/m/y): 18/10/2009
err:ole:TLB_ReadTypeLib Loading of typelib L"C:\\Arquivos de programas\\Arquivos comuns\\InstallShield\\Professional\\RunTime\\IsProBE.tlb" failed with error 2

but I achieve to finish the installation.

when I try to run the game, in the GTA's installation folder it returns:

$ cd ~/.wine/drive_c/Arquivos\ de\ programas/rockstar Games/GTA San Andreas/
$ wine gta_sa.exe

err:wgl:get_render_type_from_fbconfig Unknown render_type: 0
err:wgl:get_render_type_from_fbconfig Unknown render_type: 0
err:d3d:WineD3D_CreateFakeGLContext Can't find a suitable iPixelFormat
err:d3d:InitAdapters Failed to get a gl context for default adapter
wine: Unhandled page fault on read access to 0x00000000 at address 0x7e22a6d6 (thread 001f), starting debugger...
Unhandled exception: page fault on read access to 0x00000000 in 32-bit code (0x7e22a6d6).
Register dump:
CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
EIP:7e22a6d6 ESP:0177fb70 EBP:0177fce4 EFLAGS:00010206( - 00 - RIP1)
EAX:00000000 EBX:7c02fe30 ECX:b7e77168 EDX:7c04a548
ESI:7c049a70 EDI:00000000
Stack dump:
0x0177fb70: 0000353c 7c049a70 7e213e5f b7d266b0
0x0177fb80: 0000353c 00000001 7e6aa40c b7e8aa24
0x0177fb90: b7ff7ff4 b7ff7ff4 b7feafcf b7ff8260
0x0177fba0: 00000000 b7e0f25b 7bc8e4c4 00000000
0x0177fbb0: b7ff8668 b7ff8948 7c003168 7c005128
0x0177fbc0: 7c00b670 7c00b9f8 7c00bdb0 7c00c1a8
Backtrace:
= >0 0x7e22a6d6 in libgl.so.1 (+0x736d6) (0x0177fce4)
1 0xb7d59084 exit+0xd4() in libc.so.6 (0x0177fd04)
2 0x7bc532d0 NtSetInformationProcess() in ntdll (0x0177fd94)
3 0x7b8742ef process_ExitProcess+0x2f() in kernel32 (0x0177fdb4)
4 0x7b873eb2 ExitProcess+0x12() in kernel32 (0x0177fdc8)
err:dbghelp_msc:codeview_process_info Unknown CODEVIEW signature 8c2e96f8 in module L"gta_sa"
5 0x00823b6d in gta_sa (+0x423b6d) (0x0177fddc)
6 0x00823cfb in gta_sa (+0x423cfb) (0x0177ff08)
7 0x7b877a67 in kernel32 (+0x57a67) (0x0177ffe8)
0x7e22a6d6: movl 0x0(%eax),%esi
Modules:
Module Address Debug info Name (78 modules)
PE 230000- 239000 Deferred ogg
PE 240000- 348000 Deferred vorbis
PE 350000- 380000 Deferred eax
PE 400000- 1577000 Export gta_sa
PE 10000000-10011000 Deferred vorbisfile
ELF 7b800000-7b93c000 Export kernel32<elf>
\-PE 7b820000-7b93c000 \ kernel32
ELF 7bc00000-7bcaa000 Export ntdll<elf>
\-PE 7bc10000-7bcaa000 \ ntdll
ELF 7bf00000-7bf03000 Deferred <wine-loader>
ELF 7d3f6000-7d440000 Deferred dsound<elf>
\-PE 7d400000-7d440000 \ dsound
ELF 7d440000-7e1b7000 Deferred libglcore.so.1
ELF 7e1b7000-7e25a000 Export libgl.so.1
ELF 7e294000-7e3a4000 Deferred wined3d<elf>
\-PE 7e2b0000-7e3a4000 \ wined3d
ELF 7e3a4000-7e3fd000 Deferred ddraw<elf>
\-PE 7e3b0000-7e3fd000 \ ddraw
ELF 7e60e000-7e622000 Deferred midimap<elf>
\-PE 7e610000-7e622000 \ midimap
ELF 7e622000-7e649000 Deferred msacm32<elf>
\-PE 7e630000-7e649000 \ msacm32
ELF 7e649000-7e660000 Deferred msacm32
\-PE 7e650000-7e660000 \ msacm32
ELF 7e660000-7e69b000 Deferred wineoss
\-PE 7e670000-7e69b000 \ wineoss
ELF 7e69b000-7e6a4000 Deferred libxcursor.so.1
ELF 7e6a4000-7e6a9000 Deferred libxfixes.so.3
ELF 7e6a9000-7e6ac000 Deferred libxcomposite.so.1
ELF 7e6ac000-7e6b2000 Deferred libxrandr.so.2
ELF 7e6b2000-7e6ba000 Deferred libxrender.so.1
ELF 7e6ba000-7e6bf000 Deferred libxxf86vm.so.1
ELF 7e6bf000-7e6c2000 Deferred libxinerama.so.1
ELF 7e6c2000-7e6e2000 Deferred imm32<elf>
\-PE 7e6d0000-7e6e2000 \ imm32
ELF 7e6e2000-7e6e7000 Deferred libxdmcp.so.6
ELF 7e6e7000-7e6ff000 Deferred libxcb.so.1
ELF 7e6ff000-7e701000 Deferred libxcb-xlib.so.0
ELF 7e701000-7e704000 Deferred libxau.so.6
ELF 7e704000-7e7eb000 Deferred libx11.so.6
ELF 7e7eb000-7e7f9000 Deferred libxext.so.6
ELF 7e7f9000-7e811000 Deferred libice.so.6
ELF 7e811000-7e819000 Deferred libsm.so.6
ELF 7e81a000-7e825000 Deferred libgcc_s.so.1
ELF 7e827000-7e829000 Deferred libnvidia-tls.so.1
ELF 7e82b000-7e8c3000 Deferred winex11<elf>
\-PE 7e840000-7e8c3000 \ winex11
ELF 7e8cd000-7e8ee000 Deferred libexpat.so.1
ELF 7e8ee000-7e918000 Deferred libfontconfig.so.1
ELF 7e92a000-7e93f000 Deferred libz.so.1
ELF 7e93f000-7e9ac000 Deferred libfreetype.so.6
ELF 7e9ac000-7e9bf000 Deferred libresolv.so.2
ELF 7e9d1000-7e9f0000 Deferred iphlpapi<elf>
\-PE 7e9e0000-7e9f0000 \ iphlpapi
ELF 7e9f0000-7ea55000 Deferred rpcrt4<elf>
\-PE 7ea00000-7ea55000 \ rpcrt4
ELF 7ea55000-7eb61000 Deferred ole32<elf>
\-PE 7ea70000-7eb61000 \ ole32
ELF 7eb61000-7eb8e000 Deferred ws2_32<elf>
\-PE 7eb70000-7eb8e000 \ ws2_32
ELF 7ebad000-7ec02000 Deferred advapi32<elf>
\-PE 7ebc0000-7ec02000 \ advapi32
ELF 7ec02000-7eca0000 Deferred gdi32<elf>
\-PE 7ec10000-7eca0000 \ gdi32
ELF 7eca0000-7edea000 Deferred user32<elf>
\-PE 7ecc0000-7edea000 \ user32
ELF 7edea000-7ee7c000 Deferred winmm<elf>
\-PE 7ee00000-7ee7c000 \ winmm
ELF 7ef9c000-7efa7000 Deferred libnss_files.so.2
ELF 7efa7000-7efb1000 Deferred libnss_nis.so.2
ELF 7efb1000-7efc9000 Deferred libnsl.so.1
ELF 7efc9000-7efee000 Deferred libm.so.6
ELF 7eff7000-7f000000 Deferred libnss_compat.so.2
ELF b7d27000-b7d2b000 Deferred libdl.so.2
ELF b7d2b000-b7e7a000 Export libc.so.6
ELF b7e7b000-b7e93000 Deferred libpthread.so.0
ELF b7ea5000-b7fdb000 Deferred libwine.so.1
ELF b7fdd000-b7ff9000 Deferred ld-linux.so.2
Threads:
process tid prio (all id:s are in hex)
0000000c
00000012 0
0000000e 0
0000000d 0
0000000f
00000016 0
00000015 0
00000011 0
00000010 0
00000017
00000018 0
0000003f
00000040 0
00000047 (D) C:\Arquivos de programas\Rockstar Games\GTA San Andreas\gta_sa.exe
0000001f 0 <= =
Backtrace:
= > 0 0x7e22a6d6 in libgl.so.1 (+0x736d6) (0x0177fce4)
1 0xb7d59084 exit+0xd4() in libc.so.6 (0x0177fd04)
2 0x7bc532d0 NtSetInformationProcess() in ntdll (0x0177fd94)
3 0x7b8742ef process_ExitProcess+0x2f() in kernel32 (0x0177fdb4)
4 0x7b873eb2 ExitProcess+0x12() in kernel32 (0x0177fdc8)
5 0x00823b6d in gta_sa (+0x423b6d) (0x0177fddc)
6 0x00823cfb in gta_sa (+0x423cfb) (0x0177ff08)
7 0x7b877a67 in kernel32 (+0x57a67) (0x0177ffe8)
[email]jonathan@kpccore2:~/.wine[/email]/drive_c/Arquivos de programas/ Rockstar Games/ GTA San Andreas$ wine gta_sa.exe
err:alsa:ALSA_CheckSetVolume Could not find 'PCM Playback Volume' element
fixme:mixer:ALSA_MixerInit No master control found on Brooktree Bt878, disabling mixer
fixme:mixer:ALSA_MixerInit No master control found on USB camera, disabling mixer
err:wgl:get_render_type_from_fbconfig Unknown render_type: 0
err:wgl:get_render_type_from_fbconfig Unknown render_type: 0
err:d3d:WineD3D_CreateFakeGLContext Can't find a suitable iPixelFormat
err:d3d:InitAdapters Failed to get a gl context for default adapter
err:d3d:WineDirect3DCreate Direct3D9 is not available without opengl
wine: Unhandled page fault on read access to 0x00000000 at address 

I'm using wine 1.1.12.

I need help.

If somebody knows how I can solve it, please post it.

Thanks a milion.

---

### Post by binbash on 2009-01-05
[http://appdb.winehq.org/objectManager.php?sClass=version&iId=7677](http://appdb.winehq.org/objectManager.php?sClass=version&iId=7677)

---

