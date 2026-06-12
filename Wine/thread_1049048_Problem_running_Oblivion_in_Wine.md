---
title: "Problem running Oblivion in Wine"
date: 2009-01-24
forum: Wine
---

### Post by bigtex79 on 2009-01-24
I have read alot of forums and done some tweaking to get Oblivion to work on Ubuntu 8.10 using Wine 1.0.1.  Here is what I have done so far....

1) I have copied all of the d3dx9_24.dll through d3dx9_36.dll from my Windows install to Wine's System32 folder.  I have also gone into the configuration of Wine to the Libraries tab and made an exemption for each one making sure it is set to "native".

2) I have also gone into regedit and added the DIRECT3D folder in HKEY_CURRENT_USER\SOFTWARE\WINE and added the following string values (as you may have guessed the DIRECT3D folder was not in the Wine folder to begin with):

DirectDrawRenderer = opengl
OffscreenRenderingMode = pbuffer
PixelShaderMode = enabled
UseGLSL = enabled
VertexShaderMode = hardware
VideoMemorySize = 512 (by the way I have a BFG Nvidia 8800 GTS OC 512MB)

After doing that I still get the following when I try to run Obilivion.exe from the terminal:

[email]bigtex79@bigtex79-desktop:~/.wine[/email]/drive_c/Program Files/Bethesda Softworks/Oblivion$ wine Oblivion.exe
Trying to load PE image for unsupported architecture (AMD-64)
err:module:import_dll Loading library d3dx9_27.dll (which is needed by L"C:\\Program Files\\Bethesda Softworks\\Oblivion\\Oblivion.exe") failed (error c000007b).
err:module:LdrInitializeThunk Main exe initialization for L"C:\\Program Files\\Bethesda Softworks\\Oblivion\\Oblivion.exe" failed, status c0000135

So can someone point out to me where I am going wrong or what I'm missing?  Oh and by the way I did all this AFTER installing Oblivion.  By the way here are my system specs:

AMD X2 64 6000+
4GB RAM
BFG Nvidia 8800 GTS OC 512MB
M2N32 mobo

Thanks for any help.

---

### Post by bigtex79 on 2009-01-25
Ok, I did some digging around and I have done alot since I last posted.  Like actually installing Directx 9.0c via Wine, however, now I have a new problem.  Well, it's the same problem (Oblivion won't run) but I get a different output when running it in the terminal.  Here is what I get when I try to run Oblivion via the terminal:

[email]bigtex79@bigtex79-desktop:~/.wine[/email]/drive_c/Program Files/Bethesda Softworks/Oblivion$ wine Oblivion.exe
fixme:d3d:IWineD3DImpl_FillGLCaps OpenGL implementation supports 32 vertex samplers and 32 total samplers
fixme:d3d:IWineD3DImpl_FillGLCaps Expected vertex samplers + MAX_TEXTURES(=8) > combined_samplers
fixme:win:EnumDisplayDevicesW ((null),0,0x32ef08,0x00000000), stub!
err:d3d:getColorBits Unsupported format: WINED3DFMT_R16F
err:d3d:getColorBits Unsupported format: WINED3DFMT_A16B16G16R16F
err:d3d:getColorBits Unsupported format: WINED3DFMT_R32F
err:d3d:getColorBits Unsupported format: WINED3DFMT_A32B32G32R32F
err:d3d:getColorBits Unsupported format: WINED3DFMT_R16F
err:d3d:getColorBits Unsupported format: WINED3DFMT_A16B16G16R16F
err:d3d:getColorBits Unsupported format: WINED3DFMT_R32F
err:d3d:getColorBits Unsupported format: WINED3DFMT_A32B32G32R32F
err:d3d:getColorBits Unsupported format: WINED3DFMT_R16F
err:d3d:getColorBits Unsupported format: WINED3DFMT_A16B16G16R16F
err:d3d:getColorBits Unsupported format: WINED3DFMT_R32F
err:d3d:getColorBits Unsupported format: WINED3DFMT_A32B32G32R32F
err:d3d:getColorBits Unsupported format: WINED3DFMT_R16F
err:d3d:getColorBits Unsupported format: WINED3DFMT_A16B16G16R16F
err:d3d:getColorBits Unsupported format: WINED3DFMT_R32F
err:d3d:getColorBits Unsupported format: WINED3DFMT_A32B32G32R32F
wine: Unhandled page fault on read access to 0x00000000 at address 0x498749 (thread 0009), starting debugger...
Unhandled exception: page fault on read access to 0x00000000 in 32-bit code (0x00498749).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:00498749 ESP:0032f448 EBP:014c68f8 EFLAGS:00210202(   - 00      - -RI1)
 EAX:00000000 EBX:014c6488 ECX:00003001 EDX:12001401
 ESI:00000200 EDI:014c6688
Stack dump:
0x0032f448:  00000001 00000016 00080000 00000003
0x0032f458:  00000071 d790c0f7 0032f9b5 00010028
0x0032f468:  00000000 00400000 00000000 014c6b7c
0x0032f478:  00000000 00000000 00000000 00000000
0x0032f488:  00000000 00000000 00000000 00000001
0x0032f498:  0032f4c8 7eb05b40 00000042 00000003
Backtrace:
=>0 0x00498749 in oblivion (+0x98749) (0x014c68f8)
  1 0x00000000 (0x00000001)
  2 0x00000000 (0x00000000)
0x00498749: movl	0x0(%eax),%ecx
Modules:
Module	Address			Debug info	Name (100 modules)
PE	  400000-  baf000	Export          oblivion
PE	  bb0000-  dff000	Deferred        d3dx9_27
PE	18000000-18068000	Deferred        binkw32
ELF	7b800000-7b940000	Deferred        kernel32<elf>
  \-PE	7b820000-7b940000	\               kernel32
ELF	7bc00000-7bcad000	Deferred        ntdll<elf>
  \-PE	7bc10000-7bcad000	\               ntdll
ELF	7bf00000-7bf04000	Deferred        <wine-loader>
ELF	7c1da000-7cf51000	Deferred        libglcore.so.1
ELF	7cf51000-7d074000	Deferred        wined3d<elf>
  \-PE	7cf60000-7d074000	\               wined3d
ELF	7dd34000-7ddd7000	Deferred        libgl.so.1
ELF	7dde8000-7de19000	Deferred        d3d9<elf>
  \-PE	7ddf0000-7de19000	\               d3d9
ELF	7e087000-7e09c000	Deferred        midimap<elf>
  \-PE	7e090000-7e09c000	\               midimap
ELF	7e09c000-7e0c5000	Deferred        msacm32<elf>
  \-PE	7e0a0000-7e0c5000	\               msacm32
ELF	7e0c5000-7e0de000	Deferred        msacm32<elf>
  \-PE	7e0d0000-7e0de000	\               msacm32
ELF	7e0de000-7e12e000	Deferred        libpulse.so.0
ELF	7e13f000-7e207000	Deferred        libasound.so.2
ELF	7e20f000-7e211000	Deferred        libnvidia-tls.so.1
ELF	7e211000-7e218000	Deferred        libasound_module_pcm_pulse.so
ELF	7e218000-7e24f000	Deferred        winealsa<elf>
  \-PE	7e220000-7e24f000	\               winealsa
ELF	7e24f000-7e282000	Deferred        uxtheme<elf>
  \-PE	7e260000-7e282000	\               uxtheme
ELF	7e282000-7e28b000	Deferred        libxcursor.so.1
ELF	7e28b000-7e290000	Deferred        libxfixes.so.3
ELF	7e290000-7e294000	Deferred        libxcomposite.so.1
ELF	7e294000-7e29b000	Deferred        libxrandr.so.2
ELF	7e29b000-7e2a5000	Deferred        libxrender.so.1
ELF	7e2a5000-7e2ab000	Deferred        libxxf86vm.so.1
ELF	7e2ab000-7e2ae000	Deferred        libxinerama.so.1
ELF	7e2ae000-7e2cf000	Deferred        imm32<elf>
  \-PE	7e2b0000-7e2cf000	\               imm32
ELF	7e2cf000-7e2d4000	Deferred        libxdmcp.so.6
ELF	7e2d4000-7e2ed000	Deferred        libxcb.so.1
ELF	7e2ed000-7e3dc000	Deferred        libx11.so.6
ELF	7e3dc000-7e3eb000	Deferred        libxext.so.6
ELF	7e3eb000-7e403000	Deferred        libice.so.6
ELF	7e403000-7e40c000	Deferred        libsm.so.6
ELF	7e40e000-7e412000	Deferred        libcap.so.1
ELF	7e412000-7e41b000	Deferred        librt.so.1
ELF	7e41d000-7e4b9000	Deferred        winex11<elf>
  \-PE	7e430000-7e4b9000	\               winex11
ELF	7e4e9000-7e510000	Deferred        libexpat.so.1
ELF	7e510000-7e53d000	Deferred        libfontconfig.so.1
ELF	7e53d000-7e553000	Deferred        libz.so.1
ELF	7e553000-7e5c9000	Deferred        libfreetype.so.6
ELF	7e5c9000-7e5f6000	Deferred        ws2_32<elf>
  \-PE	7e5d0000-7e5f6000	\               ws2_32
ELF	7e5f6000-7e611000	Deferred        wsock32<elf>
  \-PE	7e600000-7e611000	\               wsock32
ELF	7e611000-7e67f000	Deferred        msvcrt<elf>
  \-PE	7e620000-7e67f000	\               msvcrt
ELF	7e67f000-7e694000	Deferred        lz32<elf>
  \-PE	7e680000-7e694000	\               lz32
ELF	7e694000-7e6af000	Deferred        version<elf>
  \-PE	7e6a0000-7e6af000	\               version
ELF	7e6af000-7e70c000	Deferred        shlwapi<elf>
  \-PE	7e6c0000-7e70c000	\               shlwapi
ELF	7e70c000-7e887000	Deferred        shell32<elf>
  \-PE	7e720000-7e887000	\               shell32
ELF	7e887000-7e8d4000	Deferred        dsound<elf>
  \-PE	7e890000-7e8d4000	\               dsound
ELF	7e8d4000-7e968000	Deferred        winmm<elf>
  \-PE	7e8e0000-7e968000	\               winmm
ELF	7e968000-7e97c000	Deferred        libresolv.so.2
ELF	7e97c000-7e97f000	Deferred        libxcb-xlib.so.0
ELF	7e97f000-7e982000	Deferred        libxau.so.6
ELF	7e98d000-7e9ad000	Deferred        iphlpapi<elf>
  \-PE	7e990000-7e9ad000	\               iphlpapi
ELF	7e9ad000-7ea14000	Deferred        rpcrt4<elf>
  \-PE	7e9c0000-7ea14000	\               rpcrt4
ELF	7ea14000-7eb26000	Deferred        ole32<elf>
  \-PE	7ea30000-7eb26000	\               ole32
ELF	7eb26000-7eb5e000	Deferred        dinput<elf>
  \-PE	7eb30000-7eb5e000	\               dinput
ELF	7eb5e000-7eb78000	Deferred        dinput8<elf>
  \-PE	7eb60000-7eb78000	\               dinput8
ELF	7eb78000-7ebcd000	Deferred        advapi32<elf>
  \-PE	7eb80000-7ebcd000	\               advapi32
ELF	7ebcd000-7ec6e000	Deferred        gdi32<elf>
  \-PE	7ebe0000-7ec6e000	\               gdi32
ELF	7ec6e000-7edbd000	Deferred        user32<elf>
  \-PE	7ec90000-7edbd000	\               user32
ELF	7edbd000-7ee84000	Deferred        comctl32<elf>
  \-PE	7edd0000-7ee84000	\               comctl32
ELF	7efa4000-7efb0000	Deferred        libnss_files.so.2
ELF	7efb0000-7efc9000	Deferred        libnsl.so.1
ELF	7efc9000-7efef000	Deferred        libm.so.6
ELF	7eff5000-7f000000	Deferred        libnss_nis.so.2
ELF	b7d62000-b7d6b000	Deferred        libnss_compat.so.2
ELF	b7d6c000-b7d70000	Deferred        libdl.so.2
ELF	b7d70000-b7ece000	Deferred        libc.so.6
ELF	b7ecf000-b7ee8000	Deferred        libpthread.so.0
ELF	b7ef9000-b8030000	Deferred        libwine.so.1
ELF	b8032000-b804f000	Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
00000008 (D) C:\Program Files\Bethesda Softworks\Oblivion\Oblivion.exe
	0000001b   15
	0000001a   15
	00000019    0
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
=>0 0x00498749 in oblivion (+0x98749) (0x014c68f8)
  1 0x00000000 (0x00000001)
  2 0x00000000 (0x00000000)
fixme:winmm:MMDRV_Exit Closing while ll-driver open


CAN SOMEONE PLEASE HELP!!! :(:(:(

Thank you

---

### Post by hikaricore on 2009-01-25
Did you happen to read the guide to installing Oblivion under WINE yet?

[http://ubuntuforums.org/showthread.php?t=349764](http://ubuntuforums.org/showthread.php?t=349764)

---

### Post by bigtex79 on 2009-01-25
Yep, I checked that already.  But now I have yet another issue....sigh

I downloaded and installed the 180.26 driver for my Nvidia now the system is completed F***ED!

I think I'm just gonna wipe it and start from scratch.

---

### Post by bigtex79 on 2009-01-25
What I did with my video driver was when I tried updating it to 180.26 thinking that the reason the game was not running was due to it not having GLSL support.  So I downloaded the latest Linux driver from Nvidia which was 180.26.  But when I tried running it in the terminal it said that xserver was still running.

After turning xserver off I started the install, during the install it said I was missing something and it needed to compile a program or something.  After that it installed properly but after I rebooted....BOOM....I would get a message saying that my video card was not detected or something but it would allow me to go into Gnome but xserver was not running.

I tried removing the packages for 177 but still no go so I'm just going to reinstall Ubuntu 8.10 and try to redo Oblivion again.

---

### Post by bigtex79 on 2009-01-26
GOT IT TO WORK!!!

I had to reinstall my system and then I did exactly what was instructed on this site [http://ubuntuforums.org/showthread.php?t=349764]("http://ubuntuforums.org/showthread.php?t=349764") and everything works!

I guess I must have done something to mess up my Wine install or something.  Not sure what but it works and that's all I care about.

If I can get Call of Duty 4, Crysis, Call of Duty: World at War, Half-Life 2 (and it's episodes), and CS:S to work......GOOD BYE VISTA!!!

---

