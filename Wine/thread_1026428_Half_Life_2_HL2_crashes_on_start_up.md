---
title: "Half Life 2 HL2 crashes on start up"
date: 2008-12-31
forum: Wine
---

### Post by edmonds on 2008-12-31
hi
i have been trying  to get hl2 going  on ubuntu for a few weeks now, but it crashes on start up (it says Loading).

this is what i get:

/.wine/drive_c/Program Files/Valve/Steam$ WINEDEBUG=fixme-all wine steam.exe -applaunch 220 -novid -dxlevel 81 -width 1024 -height 768 -fullscreen -heapsize 1024000 -refresh 60
err:ntdll:RtlpWaitForCriticalSection section 0x7bc906e4 "loader.c: loader_section" wait timed out in thread 0020, blocked by 0009, retrying (60 sec)
CellID: Fetching server list from CSDS. . .
err:dscapture:widDsCreate DirectSoundCapture flag not set
This sound card's driver does not support direct access
The (slower) DirectSound HEL mode will be used instead.
CellID: CSDS returned 215 servers.
CellID: Connecting to 114.80.71.114:27031. . .
CellID: Connect to 114.80.71.114:27031 took 371 MS
CellID: Nothing beat our old best time of 38 MS
err:ole:CoGetClassObject class {4590f811-1d3a-11d0-891f-00aa004b2e24} not registered
err:ole:CoGetClassObject no class object {4590f811-1d3a-11d0-891f-00aa004b2e24} could be created for context 0x1
err:ole:CoGetClassObject class {9a5ea990-3034-4d6f-9128-01f3c61022bc} not registered
err:ole:CoGetClassObject no class object {9a5ea990-3034-4d6f-9128-01f3c61022bc} could be created for context 0x1
err:d3d:getColorBits Unsupported format: WINED3DFMT_A16B16G16R16F
err:ole:CoGetClassObject class {9a5ea990-3034-4d6f-9128-01f3c61022bc} not registered
err:ole:CoGetClassObject no class object {9a5ea990-3034-4d6f-9128-01f3c61022bc} could be created for context 0x1
err:d3d:getColorBits Unsupported format: WINED3DFMT_A16B16G16R16F
err:d3d:getColorBits Unsupported format: WINED3DFMT_A16B16G16R16F
err:d3d:getColorBits Unsupported format: WINED3DFMT_A16B16G16R16F
err:d3d:getColorBits Unsupported format: WINED3DFMT_R32F
err:d3d:getColorBits Unsupported format: WINED3DFMT_A32B32G32R32F
wine: Unhandled page fault on write access to 0x00000022 at address 0xd488a37 (thread 000b), starting debugger...
Unhandled exception: page fault on write access to 0x00000022 in 32-bit code (0x0d488a37).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:0d488a37 ESP:0033e574 EBP:00000004 EFLAGS:00010206(   - 00      - RIP1)
 EAX:00000000 EBX:07350070 ECX:0d49a9d0 EDX:0d4967b8
 ESI:00000700 EDI:0d49a9d0
Stack dump:
0x0033e574:  00000090 0d49a9d0 00000004 006a010c
0x0033e584:  0d489d32 07350070 00000730 17a20074
0x0033e594:  0d49a9d0 006a010c 0d48a084 17a20074
0x0033e5a4:  00000730 17a20074 0d49a9f0 0d49a9d0
0x0033e5b4:  0d4886ca 17a20074 ffffffff 0033e60c
0x0033e5c4:  00000008 0033ff08 00000000 100070bb
Backtrace:
0x0d488a37: addw	$0xffff,0x22(%eax)
Modules:
Module	Address			Debug info	Name (151 modules)
PE	  340000-  374000	Deferred        tier0
PE	  380000-  3a0000	Deferred        vstdlib
PE	  3a0000-  3d6000	Deferred        filesystem_steam
PE	  3e0000-  3f5000	Deferred        valve_avi
PE	  400000-  41c000	Deferred        hl2
PE	 d1b0000- d288000	Deferred        datamodel
PE	 d3a0000- d3c9000	Deferred        dmserializers
PE	 d3d0000- d475000	Deferred        materialsystem
PE	 d480000- d4a1000	Export          datacache
PE	 d5c0000- d684000	Deferred        vguimatsurface
PE	 d690000- d6f7000	Deferred        vgui2
PE	 d700000- d72f000	Deferred        soundemittersystem
PE	 d730000- d740000	Deferred        steam_api
PE	 da70000- da98000	Deferred        stdshader_dbg
PE	 daa0000- dad3000	Deferred        stdshader_dx6
PE	 dae0000- db07000	Deferred        stdshader_dx7
PE	 db10000- db4f000	Deferred        stdshader_dx8
PE	 db50000- db5e000	Deferred        unicode
PE	 e980000- ec38000	Deferred        steamclient
PE	 ec40000- ecbb000	Deferred        vstdlib_s
PE	 ecc0000- ecfe000	Deferred        tier0_s
PE	 ee20000- ef4d000	Deferred        p2pvoice
PE	 f060000- f21d000	Deferred        gameui
PE	10000000-1002e000	Deferred        launcher
PE	10390000-103a0000	Deferred        vaudio_miles
PE	103a0000-10404000	Deferred        mss32
PE	11b70000-11c84000	Deferred        serverbrowser
PE	20000000-2064b000	Deferred        engine
PE	21100000-211ad000	Deferred        mss32_s
PE	22000000-2263d000	Deferred        server
PE	24000000-24388000	Deferred        client
PE	26000000-26126000	Deferred        vphysics
PE	26400000-26439000	Deferred        mssvoice.asi
PE	26f00000-26f2e000	Deferred        mssmp3.asi
PE	2a000000-2a09f000	Deferred        shaderapidx9
PE	2c000000-2c2d8000	Deferred        studiorender
PE	30000000-302bc000	Deferred        steam
PE	60000000-60021000	Deferred        cserhelper
PE	628c0000-628d9000	Deferred        parsifal
ELF	7a692000-7a6dc000	Deferred        dbghelp<elf>
  \-PE	7a6a0000-7a6dc000	\               dbghelp
ELF	7b800000-7b92d000	Deferred        kernel32<elf>
  \-PE	7b820000-7b92d000	\               kernel32
ELF	7b9a1000-7b9eb000	Deferred        dsound<elf>
  \-PE	7b9b0000-7b9eb000	\               dsound
ELF	7b9eb000-7b9ff000	Deferred        winejoystick<elf>
  \-PE	7b9f0000-7b9ff000	\               winejoystick
ELF	7bc00000-7bca4000	Deferred        ntdll<elf>
  \-PE	7bc10000-7bca4000	\               ntdll
ELF	7bf00000-7bf03000	Deferred        <wine-loader>
ELF	7c5da000-7c642000	Deferred        crypt32<elf>
  \-PE	7c5e0000-7c642000	\               crypt32
ELF	7cde4000-7cdea000	Deferred        libnss_dns.so.2
ELF	7cdea000-7ce10000	Deferred        netapi32<elf>
  \-PE	7cdf0000-7ce10000	\               netapi32
ELF	7ce10000-7ce37000	Deferred        secur32<elf>
  \-PE	7ce20000-7ce37000	\               secur32
ELF	7cf01000-7cf16000	Deferred        psapi<elf>
  \-PE	7cf10000-7cf16000	\               psapi
ELF	7cf1a000-7cf31000	Deferred        mcicda<elf>
  \-PE	7cf20000-7cf31000	\               mcicda
ELF	7cf8a000-7dd01000	Deferred        libglcore.so.1
ELF	7dd01000-7dda4000	Deferred        libgl.so.1
ELF	7dfc6000-7e0c9000	Deferred        wined3d<elf>
  \-PE	7dfe0000-7e0c9000	\               wined3d
ELF	7e0c9000-7e0f9000	Deferred        d3d9<elf>
  \-PE	7e0d0000-7e0f9000	\               d3d9
ELF	7e0f9000-7e11a000	Deferred        mpr<elf>
  \-PE	7e100000-7e11a000	\               mpr
ELF	7e11a000-7e168000	Deferred        wininet<elf>
  \-PE	7e120000-7e168000	\               wininet
ELF	7e168000-7e20a000	Deferred        oleaut32<elf>
  \-PE	7e180000-7e20a000	\               oleaut32
ELF	7e20a000-7e21e000	Deferred        midimap<elf>
  \-PE	7e210000-7e21e000	\               midimap
ELF	7e21e000-7e235000	Deferred        msacm32<elf>
  \-PE	7e220000-7e235000	\               msacm32
ELF	7e235000-7e270000	Deferred        wineoss<elf>
  \-PE	7e240000-7e270000	\               wineoss
ELF	7e270000-7e298000	Deferred        msvfw32<elf>
  \-PE	7e280000-7e298000	\               msvfw32
ELF	7e298000-7e32a000	Deferred        winmm<elf>
  \-PE	7e2a0000-7e32a000	\               winmm
ELF	7e32a000-7e350000	Deferred        msacm32<elf>
  \-PE	7e330000-7e350000	\               msacm32
ELF	7e350000-7e38b000	Deferred        avifil32<elf>
  \-PE	7e360000-7e38b000	\               avifil32
ELF	7e4c0000-7e521000	Deferred        rpcrt4<elf>
  \-PE	7e4d0000-7e521000	\               rpcrt4
ELF	7e521000-7e5c5000	Deferred        ole32<elf>
  \-PE	7e530000-7e5c5000	\               ole32
ELF	7e5ed000-7e620000	Deferred        uxtheme<elf>
  \-PE	7e5f0000-7e620000	\               uxtheme
ELF	7e620000-7e6df000	Deferred        comctl32<elf>
  \-PE	7e630000-7e6df000	\               comctl32
ELF	7e6df000-7e7f2000	Deferred        shell32<elf>
  \-PE	7e6f0000-7e7f2000	\               shell32
ELF	7e7f2000-7e84b000	Deferred        shlwapi<elf>
  \-PE	7e800000-7e84b000	\               shlwapi
ELF	7e84b000-7e85f000	Deferred        lz32<elf>
  \-PE	7e850000-7e85f000	\               lz32
ELF	7e85f000-7e878000	Deferred        version<elf>
  \-PE	7e860000-7e878000	\               version
ELF	7e878000-7e88b000	Deferred        libresolv.so.2
ELF	7e88b000-7e88e000	Deferred        libnss_mdns4_minimal.so.2
ELF	7e89c000-7e8ba000	Deferred        iphlpapi<elf>
  \-PE	7e8a0000-7e8ba000	\               iphlpapi
ELF	7e8ba000-7e8e6000	Deferred        ws2_32<elf>
  \-PE	7e8c0000-7e8e6000	\               ws2_32
ELF	7e8e6000-7e900000	Deferred        wsock32<elf>
  \-PE	7e8f0000-7e900000	\               wsock32
ELF	7e900000-7e909000	Deferred        libxcursor.so.1
ELF	7e909000-7e90e000	Deferred        libxfixes.so.3
ELF	7e90e000-7e911000	Deferred        libxcomposite.so.1
ELF	7e911000-7e917000	Deferred        libxrandr.so.2
ELF	7e917000-7e91f000	Deferred        libxrender.so.1
ELF	7e91f000-7e922000	Deferred        libxinerama.so.1
ELF	7e922000-7e942000	Deferred        imm32<elf>
  \-PE	7e930000-7e942000	\               imm32
ELF	7e942000-7e947000	Deferred        libxdmcp.so.6
ELF	7e947000-7e95f000	Deferred        libxcb.so.1
ELF	7e95f000-7e961000	Deferred        libxcb-xlib.so.0
ELF	7e961000-7e964000	Deferred        libxau.so.6
ELF	7e964000-7ea4b000	Deferred        libx11.so.6
ELF	7ea4b000-7ea59000	Deferred        libxext.so.6
ELF	7ea59000-7ea5e000	Deferred        libxxf86vm.so.1
ELF	7ea5e000-7ea76000	Deferred        libice.so.6
ELF	7ea76000-7ea7e000	Deferred        libsm.so.6
ELF	7ea8b000-7ea8d000	Deferred        libnvidia-tls.so.1
ELF	7ea8f000-7eb26000	Deferred        winex11<elf>
  \-PE	7eaa0000-7eb26000	\               winex11
ELF	7eb5b000-7eb7c000	Deferred        libexpat.so.1
ELF	7eb7c000-7eba6000	Deferred        libfontconfig.so.1
ELF	7ebb7000-7ebcc000	Deferred        libz.so.1
ELF	7ebcc000-7ec39000	Deferred        libfreetype.so.6
ELF	7ec39000-7ec8b000	Deferred        advapi32<elf>
  \-PE	7ec50000-7ec8b000	\               advapi32
ELF	7ec8b000-7ed26000	Deferred        gdi32<elf>
  \-PE	7eca0000-7ed26000	\               gdi32
ELF	7ed26000-7ee6d000	Deferred        user32<elf>
  \-PE	7ed40000-7ee6d000	\               user32
ELF	7ee6d000-7ee78000	Deferred        libnss_files.so.2
ELF	7ee78000-7ee90000	Deferred        libnsl.so.1
ELF	7ee90000-7ee99000	Deferred        libnss_compat.so.2
ELF	7efca000-7efef000	Deferred        libm.so.6
ELF	7eff6000-7f000000	Deferred        libnss_nis.so.2
ELF	b7c31000-b7c35000	Deferred        libdl.so.2
ELF	b7c35000-b7d84000	Deferred        libc.so.6
ELF	b7d85000-b7d9d000	Deferred        libpthread.so.0
ELF	b7dae000-b7ee4000	Deferred        libwine.so.1
ELF	b7ee6000-b7f02000	Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
00000008 
	00000037    1
	00000025    1
	00000045    0
	00000044    0
	00000043    1
	00000042    0
	00000041    1
	00000040    0
	0000003f    1
	0000003e    0
	0000003d    1
	0000003c    0
	0000003b    1
	0000003a    0
	00000039    1
	00000035    0
	00000034    1
	00000033    0
	00000032    0
	00000030    0
	0000002f    1
	0000002a    0
	00000028   15
	00000027    0
	00000026    0
	00000024    0
	00000022    0
	00000021    1
	00000020    0
	0000001f    0
	0000001e    0
	0000001d    0
	0000001c    0
	0000001b    0
	0000001a    0
	00000019    0
	00000009    0
0000000c 
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
00000047 (D) C:\Program Files\Valve\Steam\SteamApps\tomf580\half-life 2\hl2.exe
	00000038    0
	0000002e    0
	0000002d    0
	0000002c    0
	00000031    0
	0000002b    0
	00000029    0
	00000023    2
	0000000b    0 <==
Backtrace:


can anybody help?
thanks

---

### Post by soluphobe on 2008-12-31
I got this same sort of error (the unhandled page fault) a lot on a totally unrelated game.  The problem ended up being that some of the dlls were present, but needed to be overridden.  Do you have any overrides present for hl2.exe?

vstdlib shows up early on in your trace, the problem might be there.  A quick glance at the appdb shows someone else having trouble with that call.  Try and see if you have the right version of vstdlib, and if it needs to be overridden.

(Disclaimer:  wandering fool who may or may not know what he's talking about.)

Assuming that doesn't help, what kind of graphics card (and drivers) do you have?  Can you run any other steam stuff (if you have it)?

---

### Post by edmonds on 2009-01-02
hi soluphobe
thanks very much for replying
i thought i replied to this last night - seems not.
i have d3dx9_34.dll set to native,builtin - though i  am not sure if that is the right setting.
i have now installed vstdlib.dll in system32 folder. though dont know what override to set.
i have an nvidia 9600gt with 177.82 driver installed.
i dont have any other games installed, though steam itself seems ok.
it now crashes with:
CellID: Connect to 87.248.196.196:27031 took 135 MS
CellID: Connecting to 208.111.140.5:27031. . .
CellID: Connect to 208.111.140.5:27031 took 293 MS
CellID: Connecting to 114.80.71.105:27031. . .
CellID: Connect to 114.80.71.105:27031 took 451 MS
CellID: Connecting to 79.141.161.3:27031. . .
CellID: Connect to 79.141.161.3:27031 took 121 MS
CellID: Connecting to 213.8.254.150:27031. . .
CellID: Connect to 213.8.254.150:27031 took 189 MS
CellID: Connecting to 68.142.100.78:27031. . .
CellID: Connect to 68.142.100.78:27031 took 219 MS
CellID: Connecting to 113.29.129.11:27031. . .
CellID: Connect to 113.29.129.11:27031 took 583 MS
CellID: Connecting to 203.66.135.26:27031. . .
CellID: Connect to 203.66.135.26:27031 took 442 MS
CellID: Connecting to 119.167.242.104:27031. . .
CellID: Connect to 119.167.242.104:27031 took 839 MS
CellID: Connecting to 119.167.242.97:27031. . .
CellID: Connect to 119.167.242.97:27031 took 837 MS
CellID: Connecting to 69.28.158.129:27031. . .
CellID: Connect to 69.28.158.129:27031 took 225 MS
CellID: Connecting to 203.77.185.4:27031. . .
err:ole:CoGetClassObject class {4590f811-1d3a-11d0-891f-00aa004b2e24} not registered
err:ole:CoGetClassObject no class object {4590f811-1d3a-11d0-891f-00aa004b2e24} could be created for context 0x1
CellID: Connect to 203.77.185.4:27031 took 432 MS
CellID: Connecting to 222.233.53.27:27031. . .
CellID: Connect to 222.233.53.27:27031 took 518 MS
CellID: Connecting to 116.193.88.75:27031. . .
CellID: timeout connecting to 116.193.88.75:27031
CellID: Connecting to 87.248.209.210:27031. . .
CellID: Connect to 87.248.209.210:27031 took 100 MS
CellID: Connecting to 87.248.196.118:27031. . .
CellID: Connect to 87.248.196.118:27031 took 108 MS
CellID: Connecting to 87.248.208.115:27031. . .
CellID: Connect to 87.248.208.115:27031 took 119 MS
CellID: Connecting to 68.142.81.4:27031. . .
CellID: Connect to 68.142.81.4:27031 took 204 MS
err:ole:CoGetClassObject class {9a5ea990-3034-4d6f-9128-01f3c61022bc} not registered
err:ole:CoGetClassObject no class object {9a5ea990-3034-4d6f-9128-01f3c61022bc} could be created for context 0x1
CellID: Connecting to 117.121.248.123:27031. . .
err:d3d:getColorBits Unsupported format: WINED3DFMT_A16B16G16R16F
CellID: Connect to 117.121.248.123:27031 took 471 MS
CellID: Connecting to 68.142.81.2:27031. . .
CellID: Connect to 68.142.81.2:27031 took 192 MS
CellID: Connecting to 68.142.116.3:27031. . .
CellID: Connect to 68.142.116.3:27031 took 289 MS
CellID: Connecting to 114.80.71.97:27031. . .
CellID: Connect to 114.80.71.97:27031 took 430 MS
CellID: Connecting to 65.122.178.70:27031. . .
CellID: Connect to 65.122.178.70:27031 took 294 MS
CellID: Connecting to 63.236.98.116:27031. . .
CellID: Connect to 63.236.98.116:27031 took 182 MS
CellID: Connecting to 65.113.241.34:27031. . .
CellID: Connect to 65.113.241.34:27031 took 255 MS
CellID: Connecting to 87.248.196.197:27031. . .
CellID: Connect to 87.248.196.197:27031 took 102 MS
CellID: Connecting to 113.29.129.79:27031. . .
CellID: Connect to 113.29.129.79:27031 took 359 MS
CellID: Connecting to 79.141.167.5:27031. . .
CellID: Connect to 79.141.167.5:27031 took 99 MS
CellID: Connecting to 121.254.164.102:27031. . .
CellID: Connect to 121.254.164.102:27031 took 431 MS
CellID: Connecting to 87.248.208.117:27031. . .
CellID: Connect to 87.248.208.117:27031 took 114 MS
err:ole:CoGetClassObject class {9a5ea990-3034-4d6f-9128-01f3c61022bc} not registered
err:ole:CoGetClassObject no class object {9a5ea990-3034-4d6f-9128-01f3c61022bc} could be created for context 0x1
CellID: Connecting to 119.167.242.109:27031. . .
CellID: Connect to 119.167.242.109:27031 took 847 MS
CellID: Connecting to 202.173.128.178:27031. . .
CellID: Connect to 202.173.128.178:27031 took 427 MS
CellID: Connecting to 69.28.181.180:27031. . .
CellID: Connect to 69.28.181.180:27031 took 255 MS
CellID: Connecting to 116.193.84.100:27031. . .
CellID: Connect to 116.193.84.100:27031 took 455 MS
CellID: Connecting to 58.120.225.151:27031. . .
CellID: Connect to 58.120.225.151:27031 took 492 MS
CellID: Connecting to 69.28.151.29:27031. . .
CellID: Connect to 69.28.151.29:27031 took 269 MS
CellID: Connecting to 208.111.140.4:27031. . .
CellID: Connect to 208.111.140.4:27031 took 277 MS
CellID: Connecting to 69.28.140.244:27031. . .
CellID: Connect to 69.28.140.244:27031 took 291 MS
CellID: Connecting to 208.74.64.70:27031. . .
wine: Call from 0x100018ed to unimplemented function vstdlib.dll.Q_StrRight, aborting
wine: Unimplemented function vstdlib.dll.Q_StrRight called at address 0x100018ed (thread 002d), starting debugger...
CellID: Connect to 208.74.64.70:27031 took 298 MS
CellID: Connecting to 202.80.110.131:27031. . .
Unhandled exception: unimplemented function vstdlib.dll.Q_StrRight called in 32-bit code (0x7bc451ec).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:7bc451ec ESP:0033e224 EBP:0033e288 EFLAGS:00000206(   - 00      - -IP1)
 EAX:10025078 EBX:7bc88444 ECX:0033e402 EDX:0033e35c
 ESI:0033e230 EDI:00384aa0
Stack dump:
0x0033e224:  0033e234 7b8b3884 0033e3c8 80000100
0x0033e234:  00000001 00000000 100018ed 00000002
0x0033e244:  1002512a 10025078 001278c8 00000042
0x0033e254:  0033e274 7b850d2f 00110000 00000000
0x0033e264:  001278c8 00000042 7b8b3884 001278c8
0x0033e274:  0033e2a4 7b866eb1 00110000 00000104
Backtrace:
=>1 0x7bc451ec in ntdll (+0x351ec) (0x0033e288)
  2 0x100018ed in launcher (+0x18ed) (0x0033ff08)
  3 0x7b8773a7 in kernel32 (+0x573a7) (0x0033ffe8)
0x7bc451ec: subl	$4,%esp
Modules:
Module	Address			Debug info	Name (55 modules)
PE	  340000-  374000	Deferred        tier0
PE	  380000-  396000	Deferred        vstdlib
PE	  400000-  41c000	Deferred        hl2
PE	10000000-1002e000	Export          launcher
ELF	7b800000-7b92d000	Export          kernel32<elf>
  \-PE	7b820000-7b92d000	\               kernel32
ELF	7bc00000-7bca4000	Export          ntdll<elf>
  \-PE	7bc10000-7bca4000	\               ntdll
ELF	7bf00000-7bf03000	Deferred        <wine-loader>
ELF	7e885000-7e898000	Deferred        libresolv.so.2
ELF	7e8a9000-7e8c7000	Deferred        iphlpapi<elf>
  \-PE	7e8b0000-7e8c7000	\               iphlpapi
ELF	7e8c7000-7e8f3000	Deferred        ws2_32<elf>
  \-PE	7e8d0000-7e8f3000	\               ws2_32
ELF	7e8f3000-7e90d000	Deferred        wsock32<elf>
  \-PE	7e900000-7e90d000	\               wsock32
ELF	7e90d000-7e916000	Deferred        libxcursor.so.1
ELF	7e916000-7e91b000	Deferred        libxfixes.so.3
ELF	7e91b000-7e91e000	Deferred        libxcomposite.so.1
ELF	7e91e000-7e924000	Deferred        libxrandr.so.2
ELF	7e924000-7e92c000	Deferred        libxrender.so.1
ELF	7e92c000-7e92f000	Deferred        libxinerama.so.1
ELF	7e92f000-7e94f000	Deferred        imm32<elf>
  \-PE	7e940000-7e94f000	\               imm32
ELF	7e94f000-7e954000	Deferred        libxdmcp.so.6
ELF	7e954000-7e96c000	Deferred        libxcb.so.1
ELF	7e96c000-7e96f000	Deferred        libxau.so.6
ELF	7e96f000-7ea56000	Deferred        libx11.so.6
ELF	7ea56000-7ea64000	Deferred        libxext.so.6
ELF	7ea64000-7ea69000	Deferred        libxxf86vm.so.1
ELF	7ea69000-7ea81000	Deferred        libice.so.6
ELF	7ea81000-7ea89000	Deferred        libsm.so.6
ELF	7ea9a000-7eb31000	Deferred        winex11<elf>
  \-PE	7eab0000-7eb31000	\               winex11
ELF	7eb66000-7eb87000	Deferred        libexpat.so.1
ELF	7eb87000-7ebb1000	Deferred        libfontconfig.so.1
ELF	7ebb1000-7ebb3000	Deferred        libxcb-xlib.so.0
ELF	7ebc2000-7ebd7000	Deferred        libz.so.1
ELF	7ebd7000-7ec44000	Deferred        libfreetype.so.6
ELF	7ec44000-7ec96000	Deferred        advapi32<elf>
  \-PE	7ec50000-7ec96000	\               advapi32
ELF	7ec96000-7ed31000	Deferred        gdi32<elf>
  \-PE	7ecb0000-7ed31000	\               gdi32
ELF	7ed31000-7ee78000	Deferred        user32<elf>
  \-PE	7ed50000-7ee78000	\               user32
ELF	7ee78000-7ee90000	Deferred        libnsl.so.1
ELF	7ee90000-7ee99000	Deferred        libnss_compat.so.2
ELF	7efca000-7efef000	Deferred        libm.so.6
ELF	7eff5000-7f000000	Deferred        libnss_files.so.2
ELF	b7d03000-b7d0d000	Deferred        libnss_nis.so.2
ELF	b7d0e000-b7d12000	Deferred        libdl.so.2
ELF	b7d12000-b7e61000	Deferred        libc.so.6
ELF	b7e62000-b7e7a000	Deferred        libpthread.so.0
ELF	b7e8b000-b7fc1000	Deferred        libwine.so.1
ELF	b7fc3000-b7fdf000	Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
00000008 
	00000009    0
0000000c 
	00000027    0
	00000026    0
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
00000019 
	00000014    0
	00000013    0
	0000000b    1
	00000047    0
	00000046    1
	00000045    0
	00000044    1
	00000043    0
	00000042    1
	00000041    0
	00000040    1
	0000003f    0
	0000003e    1
	00000039    0
	00000038    1
	00000037    0
	00000036    0
	00000034    0
	00000033    1
	0000002e    0
	0000002c   15
	0000002b    0
	0000002a    0
	00000028    0
	00000024    0
	00000023    1
	00000022    0
	00000021    0
	00000020    0
	0000001f    0
	0000001e    0
	0000001d    0
	0000001c    0
	0000001b    0
	0000001a    0
00000029 (D) C:\Program Files\Valve\Steam\SteamApps\tomf580\half-life 2\hl2.exe
	0000002d    0 <==
Backtrace:
=>1 0x7bc451ec in ntdll (+0x351ec) (0x0033e288)
  2 0x100018ed in launcher (+0x18ed) (0x0033ff08)
  3 0x7b8773a7 in kernel32 (+0x573a7) (0x0033ffe8)
wine: Call from 0x100018ed to unimplemented function vstdlib.dll.Q_StrRight, aborting
CellID: Connect to 202.80.110.131:27031 took 466 MS
CellID: Connecting to 209.11.243.244:27031. . .
CellID: Connect to 209.11.243.244:27031 took 279 MS
CellID: Connecting to 68.142.72.253:27031. . .
CellID: Connect to 68.142.72.253:27031 took 264 MS
CellID: Connecting to 58.120.225.166:27031. . .
CellID: Connect to 58.120.225.166:27031 took 483 MS
CellID: Connecting to 195.56.146.154:27031. . .
CellID: Connect to 195.56.146.154:27031 took 151 MS
CellID: Connecting to 79.141.163.2:27031. . .
CellID: Connect to 79.141.163.2:27031 took 104 MS
CellID: Connecting to 87.248.196.115:27031. . .
CellID: Connect to 87.248.196.115:27031 took 111 MS
CellID: Connecting to 203.66.135.28:27031. . .
CellID: Connect to 203.66.135.28:27031 took 402 MS
CellID: Connecting to 193.34.49.3:27031. . .
CellID: Connect to 193.34.49.3:27031 took 134 MS
CellID: Connecting to 87.248.209.212:27031. . .
CellID: Connect to 87.248.209.212:27031 took 113 MS
CellID: Connecting to 210.208.88.54:27031. . .
CellID: Connect to 210.208.88.54:27031 took 478 MS
CellID: Connecting to 87.248.208.118:27031. . .
CellID: Connect to 87.248.208.118:27031 took 135 MS
CellID: Connecting to 114.80.71.103:27031. . .
CellID: Connect to 114.80.71.103:27031 took 464 MS
CellID: Connecting to 119.167.242.96:27031. . .
CellID: Connect to 119.167.242.96:27031 took 758 MS
CellID: Connecting to 69.28.153.90:27031. . .
CellID: Connect to 69.28.153.90:27031 took 204 MS
CellID: Connecting to 68.142.119.11:27031. . .
CellID: Connect to 68.142.119.11:27031 took 226 MS
CellID: Connecting to 62.118.240.142:27031. . .
CellID: Connect to 62.118.240.142:27031 took 191 MS
CellID: Connecting to 119.167.242.113:27031. . .
CellID: Connect to 119.167.242.113:27031 took 753 MS
CellID: Connecting to 150.101.120.97:27031. . .
CellID: Connect to 150.101.120.97:27031 took 431 MS
CellID: Connecting to 87.248.196.200:27031. . .
CellID: Connect to 87.248.196.200:27031 took 99 MS
CellID: Connecting to 119.167.242.99:27031. . .
CellID: Connect to 119.167.242.99:27031 took 683 MS
CellID: Connecting to 66.77.143.140:27031. . .
CellID: Connect to 66.77.143.140:27031 took 175 MS
CellID: Connecting to 69.28.151.182:27031. . .
CellID: Connect to 69.28.151.182:27031 took 231 MS
CellID: Connecting to 114.80.71.98:27031. . .
CellID: Connect to 114.80.71.98:27031 took 410 MS
CellID: Connecting to 194.124.229.14:27031. . .
CellID: Connect to 194.124.229.14:27031 took 84 MS
CellID: Connecting to 196.38.180.3:27031. . .
CellID: Connect to 196.38.180.3:27031 took 334 MS
CellID: Connecting to 119.167.242.108:27031. . .
CellID: Connect to 119.167.242.108:27031 took 728 MS
CellID: Connecting to 117.121.248.124:27031. . .
CellID: Connect to 117.121.248.124:27031 took 462 MS
CellID: Connecting to 79.141.162.3:27031. . .
CellID: Connect to 79.141.162.3:27031 took 95 MS
CellID: Connecting to 116.193.88.76:27031. . .
CellID: timeout connecting to 116.193.88.76:27031
CellID: Connecting to 87.248.196.117:27031. . .
CellID: Connect to 87.248.196.117:27031 took 63 MS
CellID: New Best!
CellID: Connecting to 87.248.209.211:27031. . .
CellID: Connect to 87.248.209.211:27031 took 82 MS
CellID: Connecting to 114.80.71.107:27031. . .
CellID: Connect to 114.80.71.107:27031 took 422 MS
CellID: Connecting to 193.34.49.5:27031. . .
CellID: Connect to 193.34.49.5:27031 took 128 MS
CellID: Connecting to 87.248.196.114:27031. . .
CellID: Connect to 87.248.196.114:27031 took 112 MS
CellID: Connecting to 202.80.110.132:27031. . .
CellID: Connect to 202.80.110.132:27031 took 401 MS
CellID: Connecting to 119.167.242.112:27031. . .
CellID: Connect to 119.167.242.112:27031 took 738 MS
CellID: Connecting to 208.111.140.3:27031. . .
CellID: Connect to 208.111.140.3:27031 took 232 MS
CellID: Connecting to 203.77.185.5:27031. . .
CellID: Connect to 203.77.185.5:27031 took 350 MS
CellID: Connecting to 69.28.151.28:27031. . .
CellID: Connect to 69.28.151.28:27031 took 254 MS
CellID: Connecting to 68.142.100.77:27031. . .
CellID: Connect to 68.142.100.77:27031 took 188 MS
CellID: Connecting to 193.34.50.5:27031. . .
CellID: Connect to 193.34.50.5:27031 took 83 MS
CellID: Connecting to 68.142.81.5:27031. . .
CellID: Connect to 68.142.81.5:27031 took 152 MS
CellID: Connecting to 211.44.250.15:27031. . .
CellID: Connect to 211.44.250.15:27031 took 435 MS
CellID: Connecting to 69.28.151.170:27031. . .
CellID: Connect to 69.28.151.170:27031 took 221 MS
CellID: Connecting to 194.124.229.12:27031. . .
CellID: Connect to 194.124.229.12:27031 took 59 MS
CellID: New Best!
CellID: Connecting to 79.141.163.3:27031. . .
CellID: Connect to 79.141.163.3:27031 took 67 MS
CellID: Connecting to 194.124.229.16:27031. . .
CellID: Connect to 194.124.229.16:27031 took 58 MS
CellID: New Best!
CellID: Connecting to 114.80.71.109:27031. . .
CellID: Connect to 114.80.71.109:27031 took 370 MS
CellID: Connecting to 193.34.51.2:27031. . .
CellID: Connect to 193.34.51.2:27031 took 86 MS
CellID: Connecting to 68.142.116.4:27031. . .
CellID: Connect to 68.142.116.4:27031 took 212 MS
CellID: Connecting to 79.141.165.2:27031. . .
CellID: Connect to 79.141.165.2:27031 took 82 MS
CellID: Connecting to 113.29.129.10:27031. . .
CellID: Connect to 113.29.129.10:27031 took 338 MS
CellID: Connecting to 119.167.242.101:27031. . .
CellID: Connect to 119.167.242.101:27031 took 696 MS
CellID: Connecting to 114.80.71.112:27031. . .
CellID: Connect to 114.80.71.112:27031 took 395 MS
CellID: Connecting to 193.34.49.6:27031. . .
CellID: Connect to 193.34.49.6:27031 took 95 MS
CellID: Connecting to 114.80.71.104:27031. . .
CellID: Connect to 114.80.71.104:27031 took 383 MS
CellID: Connecting to 79.141.162.2:27031. . .
CellID: Connect to 79.141.162.2:27031 took 70 MS
CellID: Connecting to 69.28.153.107:27031. . .
CellID: Connect to 69.28.153.107:27031 took 116 MS
CellID: Connecting to 208.111.156.52:27031. . .
CellID: Connect to 208.111.156.52:27031 took 163 MS
CellID: Connecting to 117.121.248.125:27031. . .
CellID: Connect to 117.121.248.125:27031 took 429 MS
CellID: Connecting to 69.28.135.85:27031. . .
CellID: Connect to 69.28.135.85:27031 took 201 MS
CellID: Connecting to 202.190.75.100:27031. . .
CellID: Connect to 202.190.75.100:27031 took 399 MS
CellID: Connecting to 193.34.50.3:27031. . .
CellID: Connect to 193.34.50.3:27031 took 52 MS
CellID: New Best!
CellID: Connecting to 79.141.161.2:27031. . .
CellID: Connect to 79.141.161.2:27031 took 41 MS
CellID: New Best!
CellID: Connecting to 208.111.133.82:27031. . .
CellID: Connect to 208.111.133.82:27031 took 132 MS
CellID: Connecting to 150.101.135.1:27031. . .
CellID: Connect to 150.101.135.1:27031 took 404 MS
CellID: Connecting to 58.120.225.190:27031. . .
CellID: Connect to 58.120.225.190:27031 took 434 MS
CellID: Connecting to 69.28.140.243:27031. . .
CellID: Connect to 69.28.140.243:27031 took 198 MS
CellID: Connecting to 114.80.71.96:27031. . .
CellID: Connect to 114.80.71.96:27031 took 366 MS
CellID: Connecting to 208.111.156.53:27031. . .
CellID: Connect to 208.111.156.53:27031 took 155 MS
CellID: Connecting to 69.28.153.106:27031. . .
CellID: Connect to 69.28.153.106:27031 took 119 MS
CellID: Connecting to 69.28.158.130:27031. . .
CellID: Connect to 69.28.158.130:27031 took 125 MS
CellID: Connecting to 72.165.61.151:27031. . .
CellID: Connect to 72.165.61.151:27031 took 240 MS
CellID: Connecting to 79.141.164.2:27031. . .
CellID: Connect to 79.141.164.2:27031 took 92 MS
CellID: Connecting to 79.141.160.3:27031. . .
CellID: Connect to 79.141.160.3:27031 took 120 MS
CellID: Connecting to 119.167.242.98:27031. . .
CellID: Connect to 119.167.242.98:27031 took 734 MS
CellID: Connecting to 69.28.140.242:27031. . .
CellID: Connect to 69.28.140.242:27031 took 197 MS
CellID: Connecting to 119.167.242.105:27031. . .
CellID: Connect to 119.167.242.105:27031 took 768 MS
CellID: Connecting to 69.28.151.27:27031. . .
CellID: Connect to 69.28.151.27:27031 took 212 MS
CellID: Connecting to 58.120.225.167:27031. . .
CellID: Connect to 58.120.225.167:27031 took 414 MS
CellID: Connecting to 203.34.186.24:27031. . .
CellID: Connect to 203.34.186.24:27031 took 369 MS
CellID: Connecting to 195.13.60.2:27031. . .
CellID: Connect to 195.13.60.2:27031 took 83 MS
CellID: Connecting to 68.142.100.75:27031. . .
CellID: Connect to 68.142.100.75:27031 took 165 MS
CellID: Connecting to 62.118.240.141:27031. . .
CellID: Connect to 62.118.240.141:27031 took 106 MS
CellID: Connecting to 87.248.208.116:27031. . .
CellID: Connect to 87.248.208.116:27031 took 50 MS
CellID: Connecting to 68.142.72.251:27031. . .
CellID: Connect to 68.142.72.251:27031 took 152 MS
CellID: Connecting to 202.80.110.133:27031. . .
CellID: Connect to 202.80.110.133:27031 took 358 MS
CellID: Connecting to 203.66.135.25:27031. . .
CellID: Connect to 203.66.135.25:27031 took 366 MS
CellID: Connecting to 210.208.88.59:27031. . .
CellID: Connect to 210.208.88.59:27031 took 361 MS
CellID: Connecting to 117.121.248.122:27031. . .
CellID: Connect to 117.121.248.122:27031 took 456 MS
CellID: Connecting to 116.193.88.77:27031. . .
CellID: timeout connecting to 116.193.88.77:27031
CellID: Connecting to 62.118.240.140:27031. . .
CellID: Connect to 62.118.240.140:27031 took 182 MS
CellID: Connecting to 208.111.133.83:27031. . .
CellID: Connect to 208.111.133.83:27031 took 172 MS
CellID: Connecting to 193.34.49.2:27031. . .
CellID: Connect to 193.34.49.2:27031 took 110 MS
CellID: Connecting to 79.141.167.4:27031. . .
CellID: Connect to 79.141.167.4:27031 took 121 MS
CellID: Connecting to 87.248.196.199:27031. . .
CellID: Connect to 87.248.196.199:27031 took 93 MS
CellID: Connecting to 68.142.116.2:27031. . .
CellID: Connect to 68.142.116.2:27031 took 254 MS
CellID: Connecting to 208.111.182.250:27031. . .
CellID: Connect to 208.111.182.250:27031 took 157 MS
CellID: Connecting to 203.66.135.29:27031. . .
CellID: Connect to 203.66.135.29:27031 took 409 MS
CellID: Connecting to 69.28.181.179:27031. . .
CellID: Connect to 69.28.181.179:27031 took 293 MS
CellID: Connecting to 195.13.60.3:27031. . .
CellID: Connect to 195.13.60.3:27031 took 150 MS
CellID: Connecting to 87.248.208.114:27031. . .
CellID: Connect to 87.248.208.114:27031 took 150 MS
CellID: Connecting to 69.28.135.83:27031. . .
CellID: Connect to 69.28.135.83:27031 took 278 MS
CellID: Connecting to 213.202.254.131:27031. . .
CellID: timeout connecting to 213.202.254.131:27031
CellID: Connecting to 69.28.153.109:27031. . .
CellID: Connect to 69.28.153.109:27031 took 166 MS
CellID: Connecting to 203.77.185.10:27031. . .
CellID: Connect to 203.77.185.10:27031 took 385 MS
CellID: Connecting to 114.80.71.99:27031. . .
CellID: Connect to 114.80.71.99:27031 took 418 MS
CellID: Connecting to 69.28.145.82:27031. . .
CellID: Connect to 69.28.145.82:27031 took 246 MS
CellID: Connecting to 69.28.158.131:27031. . .
CellID: Connect to 69.28.158.131:27031 took 176 MS
CellID: Connecting to 79.141.160.2:27031. . .
CellID: Connect to 79.141.160.2:27031 took 139 MS
CellID: Connecting to 119.167.242.107:27031. . .
CellID: Connect to 119.167.242.107:27031 took 764 MS
CellID: Connecting to 68.142.72.252:27031. . .
CellID: Connect to 68.142.72.252:27031 took 188 MS
CellID: Connecting to 69.28.151.26:27031. . .
CellID: Connect to 69.28.151.26:27031 took 263 MS
CellID: Connecting to 116.193.84.102:27031. . .
CellID: Connect to 116.193.84.102:27031 took 451 MS
CellID: Connecting to 193.34.50.6:27031. . .
CellID: Connect to 193.34.50.6:27031 took 105 MS
CellID: Connecting to 87.248.196.198:27031. . .
CellID: Connect to 87.248.196.198:27031 took 124 MS
CellID: Connecting to 202.80.110.130:27031. . .
CellID: Connect to 202.80.110.130:27031 took 401 MS
CellID: Connecting to 203.77.185.6:27031. . .
CellID: Connect to 203.77.185.6:27031 took 389 MS
CellID: Connecting to 87.248.209.213:27031. . .
CellID: Connect to 87.248.209.213:27031 took 135 MS
CellID: Connecting to 119.167.242.106:27031. . .
CellID: Connect to 119.167.242.106:27031 took 813 MS
CellID: Connecting to 203.77.185.2:27031. . .
CellID: Connect to 203.77.185.2:27031 took 360 MS
CellID: Connecting to 69.28.181.178:27031. . .
CellID: Connect to 69.28.181.178:27031 took 239 MS
CellID: Connecting to 194.124.229.15:27031. . .
CellID: Connect to 194.124.229.15:27031 took 94 MS
CellID: Connecting to 114.80.71.108:27031. . .
CellID: Connect to 114.80.71.108:27031 took 418 MS
CellID: Connecting to 202.72.191.174:27031. . .
CellID: Connect to 202.72.191.174:27031 took 503 MS
CellID: Connecting to 87.248.196.195:27031. . .
CellID: Connect to 87.248.196.195:27031 took 128 MS
CellID: Connecting to 208.111.140.6:27031. . .
CellID: Connect to 208.111.140.6:27031 took 267 MS
CellID: Connecting to 210.208.88.55:27031. . .
CellID: Connect to 210.208.88.55:27031 took 413 MS
CellID: Connecting to 87.248.196.116:27031. . .
CellID: Connect to 87.248.196.116:27031 took 99 MS
CellID: Connecting to 69.28.135.84:27031. . .
CellID: Connect to 69.28.135.84:27031 took 234 MS
CellID: !! Got Cell ID 4 from server 79.141.161.2:27031

---

### Post by edmonds on 2009-01-03
ok
its that time of day again.
added vstdlib.dll to libraries and made it 'native, builtin'
started steam/hl2
and got this:
wine: Call from 0x100018ed to unimplemented function vstdlib.dll.Q_StrRight, aborting
wine: Unimplemented function vstdlib.dll.Q_StrRight called at address 0x100018ed (thread 000b), starting debugger...
Unhandled exception: unimplemented function vstdlib.dll.Q_StrRight called in 32-bit code (0x7bc451ec).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:7bc451ec ESP:0033e224 EBP:0033e288 EFLAGS:00200206(   - 00      - -IP1)
 EAX:10025078 EBX:7bc88444 ECX:0033e402 EDX:0033e35c
 ESI:0033e230 EDI:00384aa0

and lots more but maybe this is the important stuff.
tom

---

