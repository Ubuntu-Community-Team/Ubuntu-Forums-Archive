---
title: "FIFA10 on Ubuntu 9.10 using wine 1.0.1"
date: 2009-11-05
forum: Wine
---

### Post by kg_87 on 2009-11-05
I tried to run FIFA 10 on Ubuntu 9.10 karmic Koala using wine 1.0.1
When I run the game using terminal I get this message:-

> $ wine fifa10
fixme:win:EnumDisplayDevicesW ((null),0,0x198f8f0,0x00000000), stub!
fixme:d3d:WineD3D_ChoosePixelFormat Add OpenGL context recreation support to SetDepthStencilSurface
wine: Call from 0x7b8453f0 to unimplemented function d3dx9_36.dll.D3DXCreateTextureFromFileInMemoryEx, aborting
wine: Unimplemented function d3dx9_36.dll.D3DXCreateTextureFromFileInMemoryEx called at address 0x7b8453f0 (thread 0009), starting debugger...
Unhandled exception: unimplemented function d3dx9_36.dll.D3DXCreateTextureFromFileInMemoryEx called in 32-bit code (0x7b845442).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:7b845442 ESP:0198fca0 EBP:0198fd04 EFLAGS:00200246(   - 00      - IZP1)
 EAX:7b82ecc9 EBX:7b8b6ff4 ECX:00000000 EDX:80000100
 ESI:80000100 EDI:01aa0be8
Stack dump:
0x0198fca0:  0198fd24 00000008 0000003c 80000100
0x0198fcb0:  00000001 00000000 7b8453f0 00000002
0x0198fcc0:  77588b80 7758948d 603ebff4 01daa718
0x0198fcd0:  00139908 0198fd24 6032012b 01daa718
0x0198fce0:  003c5c38 000003b4 600221a8 01c9a6b0
0x0198fcf0:  00000000 00110000 7b8453fa 00000000
Backtrace:
=>1 0x7b845442 in kernel32 (+0x25442) (0x0198fd04)
  2 0x77588ae5 in d3dx9_36 (+0x8ae5) (0x0198fd34)
  3 0x77586140 in d3dx9_36 (+0x6140) (0x01aa0c08)
  4 0x6163696c (0x00000000)
0x7b845442: subl	$4,%esp
Modules:
Module	Address			Debug info	Name (122 modules)
PE	  3b0000-  3f5000	Deferred        1911
PE	  400000- 1486000	Deferred        fifa10
PE	10000000-1004f000	Deferred        dirtysock
ELF	60000000-6001d000	Deferred        ld-linux.so.2
ELF	6001d000-60153000	Deferred        libwine.so.1
ELF	60153000-60297000	Deferred        libc.so.6
ELF	60297000-6029b000	Deferred        libdl.so.2
ELF	6029b000-602c1000	Deferred        libm.so.6
ELF	602c1000-602c9000	Deferred        libnss_compat.so.2
ELF	602c9000-602d4000	Deferred        libnss_nis.so.2
ELF	602d4000-602e0000	Deferred        libnss_files.so.2
ELF	602e0000-603f0000	Deferred        wined3d<elf>
  \-PE	602f0000-603f0000	\               wined3d
ELF	603f0000-6053b000	Deferred        user32<elf>
  \-PE	60410000-6053b000	\               user32
ELF	6053b000-6058d000	Deferred        advapi32<elf>
  \-PE	60550000-6058d000	\               advapi32
ELF	6058d000-605e5000	Deferred        ddraw<elf>
  \-PE	605a0000-605e5000	\               ddraw
ELF	605e5000-60604000	Deferred        iphlpapi<elf>
  \-PE	605f0000-60604000	\               iphlpapi
ELF	60604000-60618000	Deferred        libresolv.so.2
ELF	60618000-60631000	Deferred        dinput8<elf>
  \-PE	60620000-60631000	\               dinput8
ELF	60631000-60636000	Deferred        libuuid.so.1
ELF	60636000-60638000	Deferred        libnvidia-tls.so.1
ELF	60638000-606de000	Deferred        ole32<elf>
  \-PE	60650000-606de000	\               ole32
ELF	606de000-60741000	Deferred        rpcrt4<elf>
  \-PE	606f0000-60741000	\               rpcrt4
ELF	60741000-60779000	Deferred        dinput<elf>
  \-PE	60750000-60779000	\               dinput
ELF	60779000-607c4000	Deferred        dsound<elf>
  \-PE	60780000-607c4000	\               dsound
ELF	607c4000-60858000	Deferred        winmm<elf>
  \-PE	607d0000-60858000	\               winmm
ELF	60858000-60873000	Deferred        wsock32<elf>
  \-PE	60860000-60873000	\               wsock32
ELF	60873000-608a0000	Deferred        ws2_32<elf>
  \-PE	60880000-608a0000	\               ws2_32
ELF	608a0000-608c7000	Deferred        netapi32<elf>
  \-PE	608b0000-608c7000	\               netapi32
ELF	608c7000-608e6000	Deferred        msvcr71<elf>
  \-PE	608d0000-608e6000	\               msvcr71
ELF	608e6000-60950000	Deferred        msvcrt<elf>
  \-PE	60900000-60950000	\               msvcrt
ELF	60950000-60971000	Deferred        imm32<elf>
  \-PE	60960000-60971000	\               imm32
ELF	60971000-60a17000	Deferred        oleaut32<elf>
  \-PE	60980000-60a17000	\               oleaut32
ELF	60a17000-60b2b000	Deferred        shell32<elf>
  \-PE	60a30000-60b2b000	\               shell32
ELF	60b2b000-60b86000	Deferred        shlwapi<elf>
  \-PE	60b40000-60b86000	\               shlwapi
ELF	60b86000-60c49000	Deferred        comctl32<elf>
  \-PE	60b90000-60c49000	\               comctl32
ELF	60c49000-60cc8000	Deferred        libfreetype.so.6
ELF	60cc8000-60cde000	Deferred        libz.so.1
ELF	60cde000-60d0b000	Deferred        libfontconfig.so.1
ELF	60d0b000-60d32000	Deferred        libexpat.so.1
ELF	60d32000-60d3b000	Deferred        libsm.so.6
ELF	60d3b000-60d56000	Deferred        libice.so.6
ELF	60d56000-60d66000	Deferred        libxext.so.6
ELF	60d66000-60e95000	Deferred        libx11.so.6
ELF	60e95000-60e99000	Deferred        libxau.so.6
ELF	60e99000-60eb7000	Deferred        libxcb.so.1
ELF	60eb7000-60ebc000	Deferred        libxdmcp.so.6
ELF	60ebc000-60ebf000	Deferred        libxinerama.so.1
ELF	60ebf000-60ec9000	Deferred        libxrender.so.1
ELF	60ec9000-60ed2000	Deferred        libxrandr.so.2
ELF	60ed2000-60ed6000	Deferred        libxcomposite.so.1
ELF	60ed6000-60edc000	Deferred        libxfixes.so.3
ELF	60edc000-60ee7000	Deferred        libxcursor.so.1
ELF	60ee7000-60fae000	Deferred        libasound.so.2
ELF	60fae000-60fb7000	Deferred        librt.so.1
ELF	60fba000-60ffa000	Deferred        libpulse.so.0
ELF	60ffa000-61044000	Deferred        libpulsecommon-0.9.19.so
ELF	61044000-6104a000	Deferred        libxtst.so.6
ELF	6104a000-61053000	Deferred        libwrap.so.0
ELF	61053000-610bf000	Deferred        libsndfile.so.1
ELF	610bf000-610f8000	Deferred        libdbus-1.so.3
ELF	610f8000-611f2000	Deferred        libvorbisenc.so.2
ELF	611f2000-6121d000	Deferred        libvorbis.so.0
ELF	6121d000-61224000	Deferred        libogg.so.0
ELF	61224000-6122b000	Deferred        libasound_module_pcm_pulse.so
ELF	6122b000-61243000	Deferred        msacm32<elf>
  \-PE	61230000-61243000	\               msacm32
ELF	61243000-61259000	Deferred        midimap<elf>
  \-PE	61250000-61259000	\               midimap
ELF	61259000-6128c000	Deferred        uxtheme<elf>
  \-PE	61260000-6128c000	\               uxtheme
ELF	6128c000-612a6000	Deferred        d3dx9_31<elf>
  \-PE	61290000-612a6000	\               d3dx9_31
ELF	612a6000-612c6000	Deferred        d3dx8<elf>
  \-PE	612b0000-612c6000	\               d3dx8
ELF	612c6000-6136e000	Deferred        libgl.so.1
ELF	616fd000-62666000	Deferred        libglcore.so.1
ELF	670bd000-670d4000	Deferred        libnsl.so.1
ELF	67a7a000-67aca000	Deferred        libflac.so.8
ELF	6c0b5000-6c14f000	Deferred        winex11<elf>
  \-PE	6c0c0000-6c14f000	\               winex11
ELF	6d239000-6d261000	Deferred        msacm32<elf>
  \-PE	6d240000-6d261000	\               msacm32
ELF	6d370000-6d38e000	Deferred        tapi32<elf>
  \-PE	6d380000-6d38e000	\               tapi32
ELF	6e2f1000-6e328000	Deferred        winealsa<elf>
  \-PE	6e300000-6e328000	\               winealsa
ELF	6eff4000-6f00d000	Deferred        libpthread.so.0
ELF	717e1000-717f5000	Deferred        sensapi<elf>
  \-PE	717f0000-717f5000	\               sensapi
ELF	73d9e000-73da4000	Deferred        libxxf86vm.so.1
ELF	74f77000-74fa8000	Deferred        d3d9<elf>
  \-PE	74f80000-74fa8000	\               d3d9
ELF	77573000-77591000	Export          d3dx9_36<elf>
  \-PE	77580000-77591000	\               d3dx9_36
ELF	780fb000-7819a000	Deferred        gdi32<elf>
  \-PE	78110000-7819a000	\               gdi32
ELF	7b800000-7b93c000	Export          kernel32<elf>
  \-PE	7b820000-7b93c000	\               kernel32
ELF	7bc00000-7bca7000	Deferred        ntdll<elf>
  \-PE	7bc10000-7bca7000	\               ntdll
ELF	7bf00000-7bf04000	Deferred        <wine-loader>
Threads:
process  tid      prio (all id:s are in hex)
00000008 (D) C:\windows\system32\fifa10.exe
	00000009    0 <==
0000000c 
	00000013    0
	00000012    0
	0000000e    0
	0000000d    0
0000000f 
	00000015    0
	00000014    0
	00000011    0
	00000010    0
00000016 
	00000017    0
Backtrace:
=>1 0x7b845442 in kernel32 (+0x25442) (0x0198fd04)
  2 0x77588ae5 in d3dx9_36 (+0x8ae5) (0x0198fd34)
  3 0x77586140 in d3dx9_36 (+0x6140) (0x01aa0c08)
  4 0x6163696c (0x00000000)
wine: Call from 0x7b8453f0 to unimplemented function d3dx9_36.dll.D3DXCreateTextureFromFileW, aborting

did I do anything wrong? I mean while installing game :?:

wine settings - default
OS Version - Windows XP
Library Overrides - None(blank)
Audio-Alsa Driver (Tested,working fine)
Graphics Settings - Direct 3D,vertex shader support - Hardware
NVIDIA Driver Version - 185

other wine Applications - None

---

