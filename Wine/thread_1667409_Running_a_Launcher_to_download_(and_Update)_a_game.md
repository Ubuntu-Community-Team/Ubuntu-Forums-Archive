---
title: "Running a Launcher to download (and Update) a game."
date: 2011-01-14
forum: Wine
---

### Post by Fireblasto on 2011-01-14
Hi! 

I've been trying to run a game called Legions:Overdrive through wine. Never heard of it? Probably not. However, it is downloadable from here if you want to try:

[http://www.legionsoverdrive.com/download/](http://www.legionsoverdrive.com/download/)

This is not me specifically trying to get the game working on ubuntu, it is for the whole community. So therefore any info I give on drivers/videocards will be irrelevant, as I am trying to get a unified version of the game working from whatever system. However, if specific driver/videocard info is needed for the fix, I shall provide it for my system.

The difference from most other games which run an installer, this game runs through a patcher system, which auto-updates the game every time you run the launcher.

My experience with WINE is about 5 minutes running through the options, and marking the .exe as an executable, so typically, I have no idea how to get it running.

However I am pretty certain that one the patcher starts running, the game will download, and then run from the patcher.

---

### Post by cogadh on 2011-01-14
You can't really try to come up with a "unified version" using only one set of hardware. The best you could probably come up with is a "here's what worked for me", which might be enough to help others get started. 

Hardware can make a huge difference in how Wine does what it does, especially the video card/driver. Given that, any hardware info you might provide is certainly not irrelevant in the slightest.

The patcher system is a slight concern. Many games that use a system like that also rely on anti-cheat software like HackShield and GameGuard, which by their nature will never work in Wine, thus preventing the game from working in Wine. Before you get too involved in this project, you might want to find out if this game is using anything of the sort.

As for getting it to run, once the .exe is marked as executable, its just like with Windows: double-click the file and it launches. If it doesn't, then you should try running it from the terminal to get some error output from wine:
```
cd /<directory of .exe>
wine <executable name>.exe
```

That should be enough to get you rolling with this, be sure to be very detailed with any testing results you post, it can make all the difference in figuring out problems/solutions.

---

### Post by Fireblasto on 2011-01-16
Yeah, the game has only recently come out and is completely indie at the moment, so it has zero anti-cheating software bundled with it (and to make sure I even asked the lead programmer, so there ;) )  

I've marked it as an executable file, and double clicked on it, but typically, it doesn't do anything apart from displaying the loading glass. I'll look in the options again, and try the terminal command.

EDIT:

This is the line it returns to me:

```

wine: Install the Windows version of Mono to run .NET executables

```

---

### Post by cogadh on 2011-01-16
Okay, that's an easy one. Use [winetricks]("http://wiki.winehq.org/winetricks") to install either the real .NET or the open source alternative Mono in Wine (NOTE: If you go with the real .NET, you can only install up to .NET 3.0, versions 3.5 and 4.0 do not work with Wine yet). That should make that error go away... no guarantee that it will now work, but it will be one step closer to running.

---

### Post by Fireblasto on 2011-01-16
Downloading Mono right now.

EDIT: It wants NET only, but it wants 2.0, which I can get.

[IMG]http://i.imgur.com/nH3Mk.png[/IMG]

---

### Post by Fireblasto on 2011-01-16
Ok, downloaded the Net 2.0 thing, and this is the output that I get from the terminal:

```


fireblasto@Electro:~$ wine Launcher.exe
fixme:sync:CreateMemoryResourceNotification (0) stub
err:ole:CoGetContextToken apartment not initialised
fixme:shell:URL_ParseUrl failed to parse L"System"
fixme:shell:URL_ParseUrl failed to parse L"System.Windows.Forms"
fixme:shell:URL_ParseUrl failed to parse L"System.Drawing"
fixme:crypt:CRYPT_RegControl CERT_STORE_CTRL_AUTO_RESYNC: stub
fixme:crypt:CRYPT_RegControl CERT_STORE_CTRL_AUTO_RESYNC: stub
fixme:shell:URL_ParseUrl failed to parse L"System.Xml"
fixme:shell:URL_ParseUrl failed to parse L"System.Drawing.resources"
fixme:shell:URL_ParseUrl failed to parse L"System.Drawing.resources"
fixme:shell:URL_ParseUrl failed to parse L"LAuth.resources"
fixme:shell:URL_ParseUrl failed to parse L"LAuth.resources"
fixme:gdiplus:GdipGetFamilyName No support for handling of multiple languages!
fixme:shell:URL_ParseUrl failed to parse L"LAuth.resources"
fixme:shell:URL_ParseUrl failed to parse L"LAuth.resources"
fixme:gdiplus:GdipCreateHalftonePalette stub
fixme:gdiplus:GdipDrawImagePointsRect Color transforms not implemented
fixme:shell:URL_ParseUrl failed to parse L"System.Web"
fixme:shell:URL_ParseUrl failed to parse L"System.Configuration"
fixme:ras:RasEnumConnectionsW (0x4446b98,0x42bdcd0,0x42bdccc),stub!
fixme:ras:RasEnumConnectionsW RAS support is not implemented! Configure program to use LAN connection/winsock instead!
fixme:winsock:WSAIoctl -> SIO_ADDRESS_LIST_CHANGE request: stub
fixme:ras:RasConnectionNotificationW (0xffffffff,0x1d4,0x00000003),stub!
fixme:shell:URL_ParseUrl failed to parse L"System.resources"
fixme:shell:URL_ParseUrl failed to parse L"System.resources"
fixme:winhttp:WinHttpDetectAutoProxyConfigUrl 0x00000001, 0x42bdc60
fixme:winhttp:WinHttpDetectAutoProxyConfigUrl 0x00000002, 0x42bdc60
fixme:winsock:WSAIoctl -> SIO_ADDRESS_LIST_CHANGE request: stub
fixme:secur32:schan_InitializeSecurityContextW Using hardcoded "NORMAL" priority
fixme:shell:URL_ParseUrl failed to parse L"mscorlib.resources"
fixme:shell:URL_ParseUrl failed to parse L"mscorlib.resources"
fixme:exec:SHELL_execute flags ignored: 0x00000100
Created new window in existing browser session.
fireblasto@Electro:~$ wine Launcher.exe
fixme:sync:CreateMemoryResourceNotification (0) stub
fixme:shell:URL_ParseUrl failed to parse L"System"
fixme:shell:URL_ParseUrl failed to parse L"System.Windows.Forms"
fixme:shell:URL_ParseUrl failed to parse L"System.Drawing"
fixme:crypt:CRYPT_RegControl CERT_STORE_CTRL_AUTO_RESYNC: stub
fixme:crypt:CRYPT_RegControl CERT_STORE_CTRL_AUTO_RESYNC: stub
fixme:shell:URL_ParseUrl failed to parse L"System.Xml"
<?xml version="1.0" encoding="ibm850"?>
<Settings>
  <Login>
    <RememberMe name="Fireblasto">Disabled</RememberMe>
  </Login>
  <Patcher>
    <ClientMods>Disabled</ClientMods>
    <AutoLaunch>Disabled</AutoLaunch>
    <LastChan>
    </LastChan>
  </Patcher>
</Settings>fixme:shell:URL_ParseUrl failed to parse L"mscorlib.resources"
fixme:shell:URL_ParseUrl failed to parse L"mscorlib.resources"
fixme:shell:URL_ParseUrl failed to parse L"System.Drawing.resources"
fixme:shell:URL_ParseUrl failed to parse L"System.Drawing.resources"
fixme:shell:URL_ParseUrl failed to parse L"LAuth.resources"
fixme:shell:URL_ParseUrl failed to parse L"LAuth.resources"
fixme:gdiplus:GdipGetFamilyName No support for handling of multiple languages!
fixme:shell:URL_ParseUrl failed to parse L"LAuth.resources"
fixme:shell:URL_ParseUrl failed to parse L"LAuth.resources"
fixme:gdiplus:GdipCreateHalftonePalette stub
fixme:gdiplus:GdipDrawImagePointsRect Color transforms not implemented
fixme:shell:URL_ParseUrl failed to parse L"System.Web"
fixme:shell:URL_ParseUrl failed to parse L"System.Configuration"
fixme:ras:RasEnumConnectionsW (0x4409ad0,0x42ddcd0,0x42ddccc),stub!
fixme:ras:RasEnumConnectionsW RAS support is not implemented! Configure program to use LAN connection/winsock instead!
fixme:winsock:WSAIoctl -> SIO_ADDRESS_LIST_CHANGE request: stub
fixme:ras:RasConnectionNotificationW (0xffffffff,0x1dc,0x00000003),stub!
fixme:shell:URL_ParseUrl failed to parse L"System.resources"
fixme:shell:URL_ParseUrl failed to parse L"System.resources"
fixme:winhttp:WinHttpDetectAutoProxyConfigUrl 0x00000001, 0x42ddc60
fixme:winhttp:WinHttpDetectAutoProxyConfigUrl 0x00000002, 0x42ddc60
fixme:winsock:WSAIoctl -> SIO_ADDRESS_LIST_CHANGE request: stub
fixme:secur32:schan_InitializeSecurityContextW Using hardcoded "NORMAL" priority

```

You probably don't see anything in here, but posted it just in case. The Launcher is working, sort of. The problem is it has to talk the network to log me in. I believe the auth server uses a SSL, after talking to someone in IRC, and that person also believes that networking in wine is weak.

However, because the patcher is only one thing and then downloads the game for you, I've decided to copy the files of the game from my windows partition to my ubuntu one.

But that did not go well:

```


fireblasto@Electro:~$ wine legions.exe
fixme:dsalsa:IDsDriverBufferImpl_SetVolumePan (0x12eae0,0x12ea28): stub
fixme:dsalsa:IDsDriverBufferImpl_SetVolumePan (0x12eae0,0x12ea28): stub
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
Cannot connect to server socket err = No such file or directory
Cannot connect to server socket
jack server is not running or cannot be started
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
Cannot connect to server socket err = No such file or directory
Cannot connect to server socket
jack server is not running or cannot be started
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
Cannot connect to server socket err = No such file or directory
Cannot connect to server socket
jack server is not running or cannot be started
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
Cannot connect to server socket err = No such file or directory
Cannot connect to server socket
jack server is not running or cannot be started
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
Cannot connect to server socket err = No such file or directory
Cannot connect to server socket
jack server is not running or cannot be started
fixme:keyboard:X11DRV_LoadKeyboardLayout L"00000409", 0000: stub!
fixme:keyboard:X11DRV_UnloadKeyboardLayout (nil): stub!
fixme:imm:ImmReleaseContext ((nil), 0x176568): stub
fixme:d3d_caps:select_card_intel_mesa Card selection not handled for Mesa Intel driver
fixme:d3d_caps:init_driver_info Unhandled vendor 8086.
fixme:win:EnumDisplayDevicesW ((null),0,0x32a020,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x3299c8,0x00000000), stub!
fixme:d3d_caps:select_card_intel_mesa Card selection not handled for Mesa Intel driver
fixme:d3d_caps:init_driver_info Unhandled vendor 8086.
fixme:win:EnumDisplayDevicesW ((null),0,0x32924c,0x00000000), stub!
fixme:d3d_caps:select_card_intel_mesa Card selection not handled for Mesa Intel driver
fixme:d3d_caps:init_driver_info Unhandled vendor 8086.
fixme:win:EnumDisplayDevicesW ((null),0,0x3292fc,0x00000000), stub!
fixme:devenum:DEVENUM_ICreateDevEnum_CreateClassEnumerator Category {cc7bfb41-f175-11d1-a392-00e0291f3959} not found
fixme:devenum:DEVENUM_ICreateDevEnum_CreateClassEnumerator Category {cc7bfb46-f175-11d1-a392-00e0291f3959} not found
fixme:d3d_caps:select_card_intel_mesa Card selection not handled for Mesa Intel driver
fixme:d3d_caps:init_driver_info Unhandled vendor 8086.
fixme:win:EnumDisplayDevicesW ((null),0,0x32a5fc,0x00000000), stub!
fixme:d3dx:D3DXCreateTexture (0x17ccc0, 500, 128, 1, 0, 15, 1, 0x19ae1b4): semi-stub
fixme:d3dx:D3DXCreateTexture (0x17ccc0, 88, 24, 1, 0, 15, 1, 0x19ae374): semi-stub
fixme:d3dx:D3DXCreateTexture (0x17ccc0, 128, 19, 1, 0, 15, 1, 0x19ae764): semi-stub
fixme:d3dx:D3DXCreateTexture (0x17ccc0, 128, 19, 1, 0, 15, 1, 0x19ae7f4): semi-stub
fixme:d3dx:D3DXCreateTexture (0x17ccc0, 128, 19, 1, 0, 15, 1, 0x19ae884): semi-stub
fixme:d3dx:D3DXCreateTexture (0x17ccc0, 128, 19, 1, 0, 15, 1, 0x19ae914): semi-stub
fixme:d3dx:D3DXCreateTexture (0x17ccc0, 128, 19, 1, 0, 15, 1, 0x19ae9a4): semi-stub
fixme:d3dx:D3DXCreateTexture (0x17ccc0, 128, 19, 1, 0, 15, 1, 0x19aea34): semi-stub
fixme:d3dx:D3DXCreateTexture (0x17ccc0, 128, 19, 1, 0, 15, 1, 0x19aeac4): semi-stub
fixme:d3dx:D3DXCreateTexture (0x17ccc0, 128, 19, 1, 0, 15, 1, 0x19aeb54): semi-stub
fixme:d3dx:D3DXCreateTexture (0x17ccc0, 128, 19, 1, 0, 15, 1, 0x19aebe4): semi-stub
fixme:d3dx:D3DXCreateTexture (0x17ccc0, 174, 20, 1, 0, 15, 1, 0x19aeddc): semi-stub
fixme:d3dx:D3DXCreateTexture (0x17ccc0, 172, 18, 1, 0, 15, 1, 0x19aefac): semi-stub
fixme:d3dx:D3DXCreateTexture (0x17ccc0, 172, 18, 1, 0, 15, 1, 0x19afb3c): semi-stub
fixme:d3dx:D3DXCreateTexture (0x17ccc0, 174, 20, 1, 0, 15, 1, 0x19afca4): semi-stub
fixme:d3dx:D3DXCreateTexture (0x17ccc0, 172, 18, 1, 0, 15, 1, 0x19afe0c): semi-stub
fixme:d3dx:D3DXCreateTexture (0x17ccc0, 172, 18, 1, 0, 15, 1, 0x19afe9c): semi-stub
fixme:d3dx:D3DXCreateTexture (0x17ccc0, 334, 46, 1, 0, 15, 1, 0x19b1aa4): semi-stub
fixme:d3dx:D3DXCreateTexture (0x17ccc0, 109, 30, 1, 0, 15, 1, 0x1a698f4): semi-stub
fixme:d3dx:D3DXCreateTexture (0x17ccc0, 89, 28, 1, 0, 15, 1, 0x1a6ac54): semi-stub
fixme:d3dx:D3DXCreateTexture (0x17ccc0, 980, 551, 1, 0, 16, 1, 0x1a722c4): semi-stub
fixme:d3dx:D3DXCreateTexture (0x17ccc0, 5023, 2899, 1, 0, 15, 1, 0x1a0c424): semi-stub
err:d3d_surface:surface_init Private setup failed, returning 0x8876086a
err:d3d9:device_parent_CreateSurface (0x17ccc4) CreateSurface failed, returning 0x8876086a
fixme:d3d_texture:texture_init Failed to create surface 0x20b1b00, hr 0x8876086a
wine: Unhandled page fault on read access to 0x00000000 at address 0x55db14 (thread 0009), starting debugger...
Unhandled exception: page fault on read access to 0x00000000 in 32-bit code (0x0055db14).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:0055db14 ESP:00329b88 EBP:00000000 EFLAGS:00010246(  R- --  I  Z- -P- )
 EAX:00000080 EBX:00000b53 ECX:00000000 EDX:00000000
 ESI:01a0c3a8 EDI:0000139f
Stack dump:
0x00329b88:  00935264 01a0c3a8 0000139f 018c09c0
0x00329b98:  01000000 00000000 00000001 018c09c0
0x00329ba8:  018eff28 00329bcc 0054a316 46ca9385
0x00329bb8:  00935264 01a0c3a8 018c09c0 01a0c3a8
0x00329bc8:  00329c04 0055dc5a 01a0c3a8 00000b53
0x00329bd8:  0000139f 00000000 0000000a 00000015
Backtrace:
0x0055db14: movl	0x0(%ebp),%eax
Modules:
Module	Address			Debug info	Name (161 modules)
PE	  400000-  a35000	Export          legions
PE	10000000-101ac000	Deferred        fmodex
ELF	20000000-20048000	Deferred        dsound<elf>
  \-PE	20010000-20048000	\               dsound
ELF	20048000-2007f000	Deferred        winealsa<elf>
  \-PE	20050000-2007f000	\               winealsa
ELF	2007f000-20085000	Deferred        libxtst.so.6
ELF	20085000-2008e000	Deferred        libwrap.so.0
ELF	2008e000-200da000	Deferred        libflac.so.8
ELF	200da000-20102000	Deferred        libvorbis.so.0
ELF	20102000-20128000	Deferred        msacm32<elf>
  \-PE	20110000-20128000	\               msacm32
ELF	20128000-2013e000	Deferred        midimap<elf>
  \-PE	20130000-2013e000	\               midimap
ELF	2013e000-2018b000	Deferred        libopenal.so.1
ELF	2018b000-201a6000	Deferred        dinput8<elf>
  \-PE	20190000-201a6000	\               dinput8
ELF	201a6000-201da000	Deferred        d3d9<elf>
  \-PE	201b0000-201da000	\               d3d9
ELF	2289f000-228b9000	Deferred        openal32<elf>
  \-PE	228b0000-228b9000	\               openal32
ELF	2b3ae000-2b416000	Deferred        libsndfile.so.1
ELF	2d74f000-2d752000	Deferred        libx11-xcb.so.1
ELF	324ff000-3252e000	Deferred        mmdevapi<elf>
  \-PE	32510000-3252e000	\               mmdevapi
ELF	33c3f000-33c89000	Deferred        libpulsecommon-0.9.21.so
ELF	3760e000-37628000	Deferred        d3dx9_42<elf>
  \-PE	37610000-37628000	\               d3dx9_42
ELF	38047000-3805b000	Deferred        lz32<elf>
  \-PE	38050000-3805b000	\               lz32
ELF	3c8b0000-3c8cd000	Deferred        dxdiagn<elf>
  \-PE	3c8c0000-3c8cd000	\               dxdiagn
ELF	42806000-4281a000	Deferred        xinput1_3<elf>
  \-PE	42810000-4281a000	\               xinput1_3
ELF	49418000-4943a000	Deferred        devenum<elf>
  \-PE	49420000-4943a000	\               devenum
ELF	4a810000-4a81e000	Deferred        libxi.so.6
ELF	4aed3000-4af86000	Deferred        quartz<elf>
  \-PE	4aee0000-4af86000	\               quartz
ELF	52c18000-52c98000	Deferred        msvcrt<elf>
  \-PE	52c30000-52c98000	\               msvcrt
ELF	52fa6000-52fe8000	Deferred        libpulse.so.0
ELF	55930000-55aa8000	Deferred        libvorbisenc.so.2
ELF	596bf000-59785000	Deferred        libasound.so.2
ELF	5d88c000-5d8c5000	Deferred        dinput<elf>
  \-PE	5d890000-5d8c5000	\               dinput
ELF	6222d000-62254000	Deferred        msvfw32<elf>
  \-PE	62230000-62254000	\               msvfw32
ELF	6258d000-625e5000	Deferred        ddraw<elf>
  \-PE	62590000-625e5000	\               ddraw
ELF	661de000-661f3000	Deferred        avicap32<elf>
  \-PE	661e0000-661f3000	\               avicap32
ELF	68000000-6801e000	Deferred        ld-linux.so.2
ELF	6801e000-6815e000	Deferred        libwine.so.1
ELF	6815e000-682bb000	Deferred        libc.so.6
ELF	682bb000-682bf000	Deferred        libdl.so.2
ELF	682bf000-682e5000	Deferred        libm.so.6
ELF	682e5000-682ed000	Deferred        libnss_compat.so.2
ELF	682ed000-682f8000	Deferred        libnss_nis.so.2
ELF	682f8000-68304000	Deferred        libnss_files.so.2
ELF	68304000-683be000	Deferred        comdlg32<elf>
  \-PE	68310000-683be000	\               comdlg32
ELF	683be000-6859b000	Deferred        shell32<elf>
  \-PE	683d0000-6859b000	\               shell32
ELF	6859b000-685fc000	Deferred        shlwapi<elf>
  \-PE	685b0000-685fc000	\               shlwapi
ELF	685fc000-6872c000	Deferred        user32<elf>
  \-PE	68610000-6872c000	\               user32
ELF	6872c000-68786000	Deferred        advapi32<elf>
  \-PE	68740000-68786000	\               advapi32
ELF	68786000-68871000	Deferred        comctl32<elf>
  \-PE	68790000-68871000	\               comctl32
ELF	68871000-68902000	Deferred        winmm<elf>
  \-PE	68880000-68902000	\               winmm
ELF	68902000-6891d000	Deferred        wsock32<elf>
  \-PE	68910000-6891d000	\               wsock32
ELF	6891d000-6893d000	Deferred        iphlpapi<elf>
  \-PE	68920000-6893d000	\               iphlpapi
ELF	6893d000-6895e000	Deferred        imm32<elf>
  \-PE	68940000-6895e000	\               imm32
ELF	6895e000-6898d000	Deferred        d3d8<elf>
  \-PE	68960000-6898d000	\               d3d8
ELF	6898d000-68ac5000	Deferred        wined3d<elf>
  \-PE	689a0000-68ac5000	\               wined3d
ELF	68ac5000-68b69000	Deferred        opengl32<elf>
  \-PE	68ae0000-68b69000	\               opengl32
ELF	68b69000-68b72000	Deferred        libsm.so.6
ELF	68b72000-68b8b000	Deferred        libice.so.6
ELF	68b8b000-68b9b000	Deferred        libxext.so.6
ELF	68b9b000-68cb8000	Deferred        libx11.so.6
ELF	68cb8000-68d0b000	Deferred        libgl.so.1
ELF	68d0b000-68d10000	Deferred        libuuid.so.1
ELF	68d10000-68d2a000	Deferred        libxcb.so.1
ELF	68d2a000-68d2e000	Deferred        libxdamage.so.1
ELF	68d2e000-68d34000	Deferred        libxfixes.so.3
ELF	68d34000-68d3a000	Deferred        libxxf86vm.so.1
ELF	68d3a000-68d44000	Deferred        libdrm.so.2
ELF	68e2f000-68e4b000	Deferred        libgcc_s.so.1
ELF	68e4b000-68e4f000	Deferred        libxau.so.6
ELF	68e4f000-68e55000	Deferred        libxdmcp.so.6
ELF	68e55000-68e5e000	Deferred        librt.so.1
ELF	68e5e000-68f5c000	Deferred        ole32<elf>
  \-PE	68e80000-68f5c000	\               ole32
ELF	68f5c000-68fcf000	Deferred        rpcrt4<elf>
  \-PE	68f70000-68fcf000	\               rpcrt4
ELF	68fcf000-690b6000	Deferred        oleaut32<elf>
  \-PE	68fe0000-690b6000	\               oleaut32
ELF	690b6000-690ba000	Deferred        libxinerama.so.1
ELF	690ba000-690c4000	Deferred        libxrender.so.1
ELF	690c7000-69152000	Deferred        gdi32<elf>
  \-PE	690d0000-69152000	\               gdi32
ELF	69152000-69167000	Deferred        libz.so.1
ELF	69167000-6918e000	Deferred        libexpat.so.1
ELF	6918e000-6922f000	Deferred        winex11<elf>
  \-PE	691a0000-6922f000	\               winex11
ELF	6922f000-69237000	Deferred        libxrandr.so.2
ELF	69237000-6923b000	Deferred        libxcomposite.so.1
ELF	6923b000-6926f000	Deferred        uxtheme<elf>
  \-PE	69240000-6926f000	\               uxtheme
ELF	6926f000-6929e000	Deferred        libgssapi_krb5.so.2
ELF	6929e000-69312000	Deferred        libgcrypt.so.11
ELF	69312000-6931e000	Deferred        libavahi-common.so.3
ELF	6931e000-693cd000	Deferred        libkrb5.so.3
ELF	693cd000-693f1000	Deferred        libk5crypto.so.3
ELF	693f1000-693f5000	Deferred        libcom_err.so.2
ELF	693f5000-693fd000	Deferred        libkrb5support.so.0
ELF	693fd000-69401000	Deferred        libkeyutils.so.1
ELF	69401000-69412000	Deferred        libtasn1.so.3
ELF	69412000-69417000	Deferred        libgpg-error.so.0
ELF	69417000-69422000	Deferred        libdrm_intel.so.1
ELF	698fd000-6990d000	Deferred        libavahi-client.so.3
ELF	69971000-69976000	Deferred        libxcb-atom.so.1
ELF	69ab5000-69acf000	Deferred        libpthread.so.0
ELF	69ad6000-69b03000	Deferred        ws2_32<elf>
  \-PE	69ae0000-69b03000	\               ws2_32
ELF	69daa000-69e45000	Deferred        libgnutls.so.26
ELF	6da59000-6da90000	Deferred        winspool<elf>
  \-PE	6da60000-6da90000	\               winspool
ELF	6e426000-6e43f000	Deferred        msacm32<elf>
  \-PE	6e430000-6e43f000	\               msacm32
ELF	6f494000-6f4ad000	Deferred        version<elf>
  \-PE	6f4a0000-6f4ad000	\               version
ELF	715d4000-715db000	Deferred        libogg.so.0
ELF	7258a000-72594000	Deferred        libxcursor.so.1
ELF	74747000-74a4f000	Deferred        i915_dri.so
ELF	75402000-7543e000	Deferred        libdbus-1.so.3
ELF	7557d000-755df000	Deferred        d3dx9_36<elf>
  \-PE	75590000-755df000	\               d3dx9_36
ELF	77ec6000-77edd000	Deferred        libnsl.so.1
ELF	79656000-796a0000	Deferred        libcups.so.2
ELF	7aaf3000-7aafd000	Deferred        libtalloc.so.2
ELF	7b52e000-7b542000	Deferred        xinput9_1_0<elf>
  \-PE	7b530000-7b542000	\               xinput9_1_0
ELF	7b800000-7b971000	Deferred        kernel32<elf>
  \-PE	7b810000-7b971000	\               kernel32
ELF	7bc00000-7bcb7000	Deferred        ntdll<elf>
  \-PE	7bc10000-7bcb7000	\               ntdll
ELF	7bf00000-7bf04000	Deferred        <wine-loader>
ELF	7c736000-7c7ad000	Deferred        libfreetype.so.6
ELF	7cab5000-7cac9000	Deferred        libresolv.so.2
ELF	7d648000-7d678000	Deferred        libfontconfig.so.1
Threads:
process  tid      prio (all id:s are in hex)
00000008 (D) C:\windows\system32\legions.exe
	0000001e    0
	0000001d    0
	00000009    0 <==
0000000e services.exe
	00000016    0
	00000015    0
	00000014    0
	00000010    0
	0000000f    0
00000011 winedevice.exe
	00000018    0
	00000017    0
	00000013    0
	00000012    0
00000019 explorer.exe
	0000001a    0
Backtrace:
Killed

```

The problem with this is that the game has a specific file structure, and if it doesn't have this file structure, it freaks out. I can't keep the file structure as it would be on windows because to run an .exe, wine demands that it be in that system32 folder, and doesn't run anything even if you put it in a sub-folder of the system32 folder. Is there anyway to get around this?

---

### Post by cogadh on 2011-01-16
Nope, Wine only demands that if it can't find the correct application path. That is usually resolved by opening a terminal, changing directories to the location of the executable, then running it. Assuming the game is normally installed in Program Files, simply copy the game files to /home/<your username>/.wine/drive_c/Program Files/, then change directories to that location and run the executable.

---

### Post by Fireblasto on 2011-01-16
Indeed, I tried around with a few applications path, and I've found one that works, but I still get the same error messages posted above.

I think we need to focus on getting it contacting the auth server to get it going (so that would be the first section of code there )

---

### Post by Fireblasto on 2011-01-18
Ok, seeing as I'm getting no responce, I'm going make a thread about this over at the wineHQ forums. I'll post the link when done.

---

### Post by Robbz on 2013-03-04
I have completed this.....

[http://forums.legionsoverdrive.com/threads/l-o-for-linux-and-mac.5008/](http://forums.legionsoverdrive.com/threads/l-o-for-linux-and-mac.5008/)

---

### Post by wildmanne39 on 2013-03-05
Thanks for sharing! old thread closed, please do not post in od threads.
Thanks

---

