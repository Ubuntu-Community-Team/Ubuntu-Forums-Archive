---
title: "Graphics Problems with Age Of Mythology"
date: 2008-12-07
forum: Wine
---

### Post by dirbaio on 2008-12-07
Hi,

I want to play Age Of Mythology in linux with wine. I have installed the game without problems. It runs, but the textures display incorrectly, as you can see in the screenshot i attach.
I have tried lots of things, changing wine's config, copying some dll files to the wine system32 folder ( mfc42  bootvid  hal  kdcom), adding overrides for them... it doesn't work.

I'd appreciate a lot any help!
Thanks in advance.

-----------
My settings:

Wine version: I have tried both 1.0.1 and 1.1.10
Age of Mythology version: 1.10
Ubuntu version: 8.10 (Intrepid)

Wine settings:
```

DLL OVERRIDES (native, builtin)
  mfc42
  bootvid
  hal
  kdcom
WINDOWS VERSION: I have tried win98, winXP and Vista
VIRTUAL DESKTOP: yes, 800x600

```

Terminal output
```
err:ole:CoGetClassObject class {ebb08c45-6c4a-4fdc-ae53-4eb8c4c7db8e} not registered
err:ole:CoGetClassObject no class object {ebb08c45-6c4a-4fdc-ae53-4eb8c4c7db8e} could be created for context 0x1
fixme:imm:ImmReleaseContext (0x10028, 0x13a368): stub
fixme:imm:NotifyIME NI_CLOSECANDIDATE
fixme:imm:ImmGetOpenStatus (0x13a368): semi-stub
fixme:win:EnumDisplayDevicesW ((null),0,0x32ee44,0x00000000), stub!
fixme:d3d:WineD3D_ChoosePixelFormat Add OpenGL context recreation support to SetDepthStencilSurface
fixme:d3d_shader:vshader_set_limits Unrecognized vertex shader version 0
fixme:d3d_shader:vshader_set_limits Unrecognized vertex shader version 0
fixme:d3d_shader:vshader_set_limits Unrecognized vertex shader version 0
fixme:d3d_shader:vshader_set_limits Unrecognized vertex shader version 0
fixme:d3d_shader:vshader_set_limits Unrecognized vertex shader version 0
fixme:d3d_shader:vshader_set_limits Unrecognized vertex shader version 0
fixme:d3d_shader:vshader_set_limits Unrecognized vertex shader version 0
fixme:d3d_shader:vshader_set_limits Unrecognized vertex shader version 0
err:ole:CoGetClassObject class {ebb08c45-6c4a-4fdc-ae53-4eb8c4c7db8e} not registered
err:ole:CoGetClassObject no class object {ebb08c45-6c4a-4fdc-ae53-4eb8c4c7db8e} could be created for context 0x1
fixme:d3d:WineD3D_ChoosePixelFormat Add OpenGL context recreation support to SetDepthStencilSurface
err:wgl:internal_SetPixelFormat Invalid operation on root_window
err:d3d:CreateContext SetPixelFormat failed on HDC=0x374 for iPixelFormat=8
fixme:d3d:IWineD3DDeviceImpl_EvictManagedResources (0x1403d0) : stub
fixme:imm:ImmDisableIME (-1): stub
fixme:advapi:RegisterEventSourceW ((null),L"Age of Mythology"): stub
fixme:advapi:ReportEventA (0xcafe4242,0x0001,0x0000,0x000003e8,(nil),0x0005,0x0000004b,0x7e2817fc,0x7e2813b4): stub
fixme:advapi:ReportEventW (0xcafe4242,0x0001,0x0000,0x000003e8,(nil),0x0005,0x0000004b,0x12e770,0x7e2813b4): stub
err:eventlog:ReportEventW L"aom.exe"
err:eventlog:ReportEventW L"3.2004.4.2300"
err:eventlog:ReportEventW L""
err:eventlog:ReportEventW L"0.0.0.0"
err:eventlog:ReportEventW L"00000000"
fixme:advapi:DeregisterEventSource (0xcafe4242) stub


```

---

### Post by kb1pkj on 2009-01-04
Ditto. I have been trying everything recommended. Virtual desktop 1024x600, 800x600,640x480. Turned off IntroCinematics etc. Here is my Wine startup command line and the output :

```
env WINEPREFIX="/home/kb1pkj/.wine" wine "C:\Program Files\games\AgeofMythology\aom.exe" xres=640 yres=480 +noSound bpp=16 +window +lowend +terrainHalfDensity +lowpoly -waterbump skipMipMapLevels=1 graphicDetail=2 +noIntroCinematics
err:ole:CoGetClassObject class {ebb08c45-6c4a-4fdc-ae53-4eb8c4c7db8e} not registered
err:ole:CoGetClassObject no class object {ebb08c45-6c4a-4fdc-ae53-4eb8c4c7db8e} could be created for context 0x1
fixme:imm:ImmReleaseContext (0x10024, 0x137d48): stub
fixme:imm:NotifyIME NI_CLOSECANDIDATE
fixme:imm:ImmGetOpenStatus (0x137d48): semi-stub
fixme:win:EnumDisplayDevicesW ((null),0,0x32ed08,0x00000000), stub!
fixme:d3d:WineD3D_ChoosePixelFormat Add OpenGL context recreation support to SetDepthStencilSurface
err:d3d:WineD3D_ChoosePixelFormat Can't find a suitable iPixelFormat
fixme:d3d:WineD3D_ChoosePixelFormat Add OpenGL context recreation support to SetDepthStencilSurface
fixme:d3d_shader:vshader_set_limits Unrecognized vertex shader version 0
fixme:d3d_shader:vshader_set_limits Unrecognized vertex shader version 0
fixme:d3d_shader:vshader_set_limits Unrecognized vertex shader version 0
fixme:d3d_shader:vshader_set_limits Unrecognized vertex shader version 0
fixme:d3d_shader:vshader_set_limits Unrecognized vertex shader version 0
fixme:d3d_shader:vshader_set_limits Unrecognized vertex shader version 0
fixme:d3d_shader:vshader_set_limits Unrecognized vertex shader version 0
fixme:d3d_shader:vshader_set_limits Unrecognized vertex shader version 0
err:ole:CoGetClassObject class {ebb08c45-6c4a-4fdc-ae53-4eb8c4c7db8e} not registered
err:ole:CoGetClassObject no class object {ebb08c45-6c4a-4fdc-ae53-4eb8c4c7db8e} could be created for context 0x1
fixme:d3d:WineD3D_ChoosePixelFormat Add OpenGL context recreation support to SetDepthStencilSurface
err:d3d:WineD3D_ChoosePixelFormat Can't find a suitable iPixelFormat
fixme:d3d:WineD3D_ChoosePixelFormat Add OpenGL context recreation support to SetDepthStencilSurface
err:wgl:internal_SetPixelFormat Invalid operation on root_window
err:d3d:CreateContext SetPixelFormat failed on HDC=0x374 for iPixelFormat=8
fixme:d3d:IWineD3DDeviceImpl_EvictManagedResources (0x1387d0) : stub
fixme:ole:CoInitializeSecurity ((nil),-1,(nil),(nil),1,3,(nil),0,(nil)) - stub!
err:ole:CoGetClassObject class {4590f811-1d3a-11d0-891f-00aa004b2e24} not registered
err:ole:CoGetClassObject no class object {4590f811-1d3a-11d0-891f-00aa004b2e24} could be created for context 0x1
fixme:reg:GetNativeSystemInfo (0x33ec94) using GetSystemInfo()
fixme:dsound:IKsPrivatePropertySetImpl_Get unsupported property: {f2957840-260c-11d1-a4d8-00c04fc28aca}
fixme:win:EnumDisplayDevicesW ((null),0,0x33ed00,0x00000000), stub!
fixme:win:EnumDisplayDevicesW (L"\\\\.\\DISPLAY1",0,0x33e9b8,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),1,0x33ed00,0x00000000), stub!
fixme:dsound:IKsPrivatePropertySetImpl_Get unsupported property: {1aeaa606-35f0-11d1-b161-00c04fc28aca}
fixme:win:EnumDisplayDevicesW ((null),0,0x33f1d4,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33eebc,0x00000000), stub!
fixme:wintrust:CryptCATAdminAcquireContext 0x6883b8 (null) 0
fixme:thread:SetThreadIdealProcessor (0xfffffffe): stub
fixme:adpcm:ADPCM_StreamOpen We don't support encoding yet
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80040111
err:ole:CoGetClassObject no class object {da4e3da0-d07d-11d0-bd50-00a0c911ce86} could be created for context 0x1
err:ole:CoGetClassObject class {0a4252a0-7e70-11d0-a5d6-28db04c10000} not registered
err:ole:CoGetClassObject no class object {0a4252a0-7e70-11d0-a5d6-28db04c10000} could be created for context 0x1
err:ole:CoGetClassObject class {2721ae20-7e70-11d0-a5d6-28db04c10000} not registered
err:ole:CoGetClassObject no class object {2721ae20-7e70-11d0-a5d6-28db04c10000} could be created for context 0x1
err:ole:CoGetClassObject class {2eb07ea0-7e70-11d0-a5d6-28db04c10000} not registered
err:ole:CoGetClassObject no class object {2eb07ea0-7e70-11d0-a5d6-28db04c10000} could be created for context 0x1
err:ole:CoGetClassObject class {65e8773d-8f56-11d0-a3b9-00a0c9223196} not registered
err:ole:CoGetClassObject no class object {65e8773d-8f56-11d0-a3b9-00a0c9223196} could be created for context 0x1
err:ole:CoGetClassObject class {65e8773e-8f56-11d0-a3b9-00a0c9223196} not registered
err:ole:CoGetClassObject no class object {65e8773e-8f56-11d0-a3b9-00a0c9223196} could be created for context 0x1
err:ole:CoGetClassObject class {ad809c00-7b88-11d0-a5d6-28db04c10000} not registered
err:ole:CoGetClassObject no class object {ad809c00-7b88-11d0-a5d6-28db04c10000} could be created for context 0x1
err:ole:CoGetClassObject class {cc7bfb41-f175-11d1-a392-00e0291f3959} not registered
err:ole:CoGetClassObject no class object {cc7bfb41-f175-11d1-a392-00e0291f3959} could be created for context 0x1
err:ole:CoGetClassObject class {cc7bfb46-f175-11d1-a392-00e0291f3959} not registered
err:ole:CoGetClassObject no class object {cc7bfb46-f175-11d1-a392-00e0291f3959} could be created for context 0x1
err:ole:CoGetClassObject class {cf1dda2c-9743-11d0-a3ee-00a0c9223196} not registered
err:ole:CoGetClassObject no class object {cf1dda2c-9743-11d0-a3ee-00a0c9223196} could be created for context 0x1
err:ole:CoGetClassObject class {cf1dda2d-9743-11d0-a3ee-00a0c9223196} not registered
err:ole:CoGetClassObject no class object {cf1dda2d-9743-11d0-a3ee-00a0c9223196} could be created for context 0x1
err:ole:CoGetClassObject class {fbf6f530-07b9-11d2-a71e-0000f8004788} not registered
err:ole:CoGetClassObject no class object {fbf6f530-07b9-11d2-a71e-0000f8004788} could be created for context 0x1
fixme:wintrust:CryptCATAdminReleaseContext 0xdeadbeef 0
fixme:imm:ImmDisableIME (-1): stub
fixme:advapi:RegisterEventSourceW ((null),L"Age of Mythology"): stub
fixme:advapi:ReportEventA (0xcafe4242,0x0001,0x0000,0x000003e8,(nil),0x0005,0x0000004b,0x7e2647fc,0x7e2643b4): stub
fixme:advapi:ReportEventW (0xcafe4242,0x0001,0x0000,0x000003e8,(nil),0x0005,0x0000004b,0x135bf8,0x7e2643b4): stub
err:eventlog:ReportEventW L"aom.exe"
err:eventlog:ReportEventW L"3.2002.10.700"
err:eventlog:ReportEventW L""
err:eventlog:ReportEventW L"0.0.0.0"
err:eventlog:ReportEventW L"00000000"
fixme:advapi:DeregisterEventSource (0xcafe4242) stub
fixme:wininet:InternetGetConnectedState always returning LAN connection.
wine: Unhandled page fault on read access to 0x00001154 at address 0x7d44f66c (thread 0009), starting debugger...
Unhandled exception: page fault on read access to 0x00001154 in 32-bit code (0x7d44f66c).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:7d44f66c ESP:0032fc04 EBP:0032fc2c EFLAGS:00210246(   - 00      -RIZP1)
 EAX:00000000 EBX:7d52fff4 ECX:00138588 EDX:00000000
 ESI:00000001 EDI:00000000
Stack dump:
0x0032fc04:  00148618 00000000 00148880 7bc4202e
0x0032fc14:  00000000 00110000 7d44f64b 7d52fff4
0x0032fc24:  00000001 00000001 0032fc7c 7d4d86eb
0x0032fc34:  001387d0 00000000 001485d8 7bc432d9
0x0032fc44:  7e0f8ff4 00000002 0032fc7c 7e0ed434
0x0032fc54:  7d530b88 7d522c80 7d50ea44 7bc33f61
Backtrace:
=>1 0x7d44f66c DestroyContext+0x2c() in wined3d (0x0032fc2c)
  2 0x7d4d86eb in wined3d (+0xa86eb) (0x0032fc7c)
  3 0x7e0ed676 in d3d8 (+0x1d676) (0x0032fcac)
  4 0x7e0e9c08 D3D8CB_DestroySwapChain+0x78() in d3d8 (0x0032fcec)
  5 0x7d4641ef in wined3d (+0x341ef) (0x0032fd2c)
  6 0x7e0e8125 in d3d8 (+0x18125) (0x0032fd5c)
  7 0x00812e16 in aom (+0x412e16) (0x004b9630)
  8 0x1c35ff00 (0x4ba43c68)
  9 0x00000000 (0x00000000)
0x7d44f66c DestroyContext+0x2c in wined3d: cmpl	0x1154(%edi),%eax
Modules:
Module	Address			Debug info	Name (115 modules)
PE	  330000-  3bd000	Deferred        granny
PE	  400000-  ac5000	Export          aom
PE	 1540000- 15da000	Deferred        language
PE	10000000-10014000	Deferred        rockalldll
PE	21100000-2115e000	Deferred        mss32
PE	69b10000-69c3e000	Deferred        msxml4
PE	780c0000-78121000	Deferred        msvcp60
ELF	7b800000-7b93d000	Deferred        kernel32<elf>
  \-PE	7b820000-7b93d000	\               kernel32
ELF	7bc00000-7bca7000	Deferred        ntdll<elf>
  \-PE	7bc10000-7bca7000	\               ntdll
ELF	7bf00000-7bf04000	Deferred        <wine-loader>
ELF	7d1d1000-7d41f000	Deferred        i915_dri.so
ELF	7d41f000-7d534000	Export          wined3d<elf>
  \-PE	7d430000-7d534000	\               wined3d
ELF	7d534000-7d57f000	Deferred        riched20<elf>
  \-PE	7d540000-7d57f000	\               riched20
ELF	7d57f000-7d593000	Deferred        riched32<elf>
  \-PE	7d580000-7d593000	\               riched32
ELF	7d593000-7d597000	Deferred        libgpg-error.so.0
ELF	7d597000-7d600000	Deferred        libgcrypt.so.11
ELF	7d600000-7d612000	Deferred        libtasn1.so.3
ELF	7d612000-7d644000	Deferred        libcrypt.so.1
ELF	7d644000-7d6e1000	Deferred        libgnutls.so.26
ELF	7d6e1000-7d705000	Deferred        libk5crypto.so.3
ELF	7d705000-7d797000	Deferred        libkrb5.so.3
ELF	7d797000-7d7cd000	Deferred        libcups.so.2
ELF	7dfd0000-7dfd9000	Deferred        libkrb5support.so.0
ELF	7dfd9000-7e003000	Deferred        libgssapi_krb5.so.2
ELF	7e04f000-7e058000	Deferred        libdrm.so.2
ELF	7e058000-7e05b000	Deferred        libxdamage.so.1
ELF	7e05b000-7e0bc000	Deferred        libgl.so.1
ELF	7e0ce000-7e0fa000	Export          d3d8<elf>
  \-PE	7e0d0000-7e0fa000	\               d3d8
ELF	7e146000-7e179000	Deferred        uxtheme<elf>
  \-PE	7e150000-7e179000	\               uxtheme
ELF	7e179000-7e18e000	Deferred        midimap<elf>
  \-PE	7e180000-7e18e000	\               midimap
ELF	7e18e000-7e1b6000	Deferred        msacm32<elf>
  \-PE	7e190000-7e1b6000	\               msacm32
ELF	7e1b6000-7e1cf000	Deferred        msacm32<elf>
  \-PE	7e1c0000-7e1cf000	\               msacm32
ELF	7e1cf000-7e1d3000	Deferred        libcap.so.1
ELF	7e1d3000-7e223000	Deferred        libpulse.so.0
ELF	7e223000-7e2eb000	Deferred        libasound.so.2
ELF	7e2ec000-7e2f0000	Deferred        libkeyutils.so.1
ELF	7e2f9000-7e2fd000	Deferred        libcom_err.so.2
ELF	7e2fd000-7e334000	Deferred        winealsa<elf>
  \-PE	7e310000-7e334000	\               winealsa
ELF	7e334000-7e33d000	Deferred        libxcursor.so.1
ELF	7e33d000-7e342000	Deferred        libxfixes.so.3
ELF	7e342000-7e346000	Deferred        libxcomposite.so.1
ELF	7e346000-7e34d000	Deferred        libxrandr.so.2
ELF	7e34d000-7e357000	Deferred        libxrender.so.1
ELF	7e357000-7e35a000	Deferred        libxinerama.so.1
ELF	7e35a000-7e35f000	Deferred        libxdmcp.so.6
ELF	7e35f000-7e378000	Deferred        libxcb.so.1
ELF	7e378000-7e37b000	Deferred        libxcb-xlib.so.0
ELF	7e37b000-7e37e000	Deferred        libxau.so.6
ELF	7e37e000-7e46d000	Deferred        libx11.so.6
ELF	7e46d000-7e47c000	Deferred        libxext.so.6
ELF	7e47c000-7e482000	Deferred        libxxf86vm.so.1
ELF	7e482000-7e49a000	Deferred        libice.so.6
ELF	7e49a000-7e4a3000	Deferred        libsm.so.6
ELF	7e4a3000-7e4aa000	Deferred        libasound_module_pcm_pulse.so
ELF	7e4aa000-7e4b3000	Deferred        librt.so.1
ELF	7e4b5000-7e550000	Deferred        winex11<elf>
  \-PE	7e4c0000-7e550000	\               winex11
ELF	7e5ab000-7e5d2000	Deferred        libexpat.so.1
ELF	7e5d2000-7e5ff000	Deferred        libfontconfig.so.1
ELF	7e5ff000-7e615000	Deferred        libz.so.1
ELF	7e615000-7e68b000	Deferred        libfreetype.so.6
ELF	7e68b000-7e6a0000	Deferred        lz32<elf>
  \-PE	7e690000-7e6a0000	\               lz32
ELF	7e6a0000-7e6bb000	Deferred        version<elf>
  \-PE	7e6b0000-7e6bb000	\               version
ELF	7e6bb000-7e780000	Deferred        comctl32<elf>
  \-PE	7e6c0000-7e780000	\               comctl32
ELF	7e780000-7e7db000	Deferred        shlwapi<elf>
  \-PE	7e790000-7e7db000	\               shlwapi
ELF	7e7db000-7e8ef000	Deferred        shell32<elf>
  \-PE	7e7f0000-7e8ef000	\               shell32
ELF	7e8ef000-7e910000	Deferred        imm32<elf>
  \-PE	7e900000-7e910000	\               imm32
ELF	7e910000-7e9b6000	Deferred        oleaut32<elf>
  \-PE	7e920000-7e9b6000	\               oleaut32
ELF	7e9b6000-7ea22000	Deferred        msvcrt<elf>
  \-PE	7e9d0000-7ea22000	\               msvcrt
ELF	7ea22000-7ea4f000	Deferred        ws2_32<elf>
  \-PE	7ea30000-7ea4f000	\               ws2_32
ELF	7ea4f000-7eae3000	Deferred        winmm<elf>
  \-PE	7ea60000-7eae3000	\               winmm
ELF	7eae3000-7eaf7000	Deferred        libresolv.so.2
ELF	7eb09000-7eb28000	Deferred        iphlpapi<elf>
  \-PE	7eb10000-7eb28000	\               iphlpapi
ELF	7eb28000-7eb8b000	Deferred        rpcrt4<elf>
  \-PE	7eb30000-7eb8b000	\               rpcrt4
ELF	7eb8b000-7ec31000	Deferred        ole32<elf>
  \-PE	7eba0000-7ec31000	\               ole32
ELF	7ec31000-7ec84000	Deferred        advapi32<elf>
  \-PE	7ec40000-7ec84000	\               advapi32
ELF	7ec84000-7ed23000	Deferred        gdi32<elf>
  \-PE	7ec90000-7ed23000	\               gdi32
ELF	7ed23000-7ee6f000	Deferred        user32<elf>
  \-PE	7ed40000-7ee6f000	\               user32
ELF	7ef8f000-7ef9b000	Deferred        libnss_files.so.2
ELF	7ef9b000-7efa6000	Deferred        libnss_nis.so.2
ELF	7efa6000-7efbf000	Deferred        libnsl.so.1
ELF	7efbf000-7efc8000	Deferred        libnss_compat.so.2
ELF	7efc8000-7efee000	Deferred        libm.so.6
ELF	b7db2000-b7db6000	Deferred        libdl.so.2
ELF	b7db6000-b7f14000	Deferred        libc.so.6
ELF	b7f15000-b7f2e000	Deferred        libpthread.so.0
ELF	b7f40000-b8077000	Deferred        libwine.so.1
ELF	b8079000-b8096000	Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
00000008 (D) C:\Program Files\games\AgeofMythology\aom.exe
	00000009    0 <==
0000000c 
	0000001a    0
	00000012    0
	0000000e    0
	0000000d    0
0000000f 
	00000016    0
	00000014    0
	00000011    0
	00000010    0
00000017 
	0000001b    0
	00000019    0
	00000018    0
0000001c 
	0000001d    0
Backtrace:
=>1 0x7d44f66c DestroyContext+0x2c() in wined3d (0x0032fc2c)
  2 0x7d4d86eb in wined3d (+0xa86eb) (0x0032fc7c)
  3 0x7e0ed676 in d3d8 (+0x1d676) (0x0032fcac)
  4 0x7e0e9c08 D3D8CB_DestroySwapChain+0x78() in d3d8 (0x0032fcec)
  5 0x7d4641ef in wined3d (+0x341ef) (0x0032fd2c)
  6 0x7e0e8125 in d3d8 (+0x18125) (0x0032fd5c)
  7 0x00812e16 in aom (+0x412e16) (0x004b9630)
  8 0x1c35ff00 (0x4ba43c68)
  9 0x00000000 (0x00000000)
err:seh:setup_exception_record nested exception on signal stack in thread 0009 eip 7bc679c0 esp 7ffdbc7c stack 0x232000-0x330000


```

Wine Version 1.0.1
Ubuntu 8.10 Ibex
Asus eee PC 1000 (2 gigs RAM, intel 945GM chipset video)
Age of Mythology w/Titans Expansion fully patched


Any help appreciated. Same issue as original poster. Looks great starting up then as soon as opening menu appears the texture maps go kerflooey.

Game looks like it would be phenomenal on the Asus eee and in fact it has been installed successfully on other versions of Linux on other Asus models. 

Thanks,
Mike

---

