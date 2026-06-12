---
title: "WINE and COUNTER STRIKE : SOURCE"
date: 2009-03-27
forum: Wine
---

### Post by hazenvnn on 2009-03-27
I've just install CS:S on my Ubuntu 8.10 pc. But It can't run, this is the output from terminal, can someone help ?
 > fixme:win:EnumDisplayDevicesW ((null),0,0x32e1ac,0x00000000), stub!
err:d3d:getColorBits Unsupported format: WINED3DFMT_A16B16G16R16F
wine: Unhandled page fault on write access to 0x2a079c70 at address 0x3a4a0d (thread 0009), starting debugger...
Unhandled exception: page fault on write access to 0x2a079c70 in 32-bit code (0x003a4a0d).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:003a4a0d ESP:0032d8c0 EBP:0032dd10 EFLAGS:00010202(   - 00      - -RI1)
 EAX:2a079c70 EBX:2a079c70 ECX:20038700 EDX:00000000
 ESI:0032d8d0 EDI:0cfa16d0
Stack dump:
0x0032d8c0:  0032d8d8 003dad68 0032da60 00000000
0x0032d8d0:  00000000 00000000 00000000 00000000
0x0032d8e0:  00000000 00000000 00000000 00000000
0x0032d8f0:  00000000 00000000 00000000 00000000
0x0032d900:  00000000 00000000 00000000 00000000
0x0032d910:  00000000 00000000 00000000 705c3a63
Backtrace:
=>1 0x003a4a0d in filesystem_steam (+0x14a0d) (0x0032dd10)
0x003a4a0d: movl	%edx,0x0(%eax)
Modules:
Module	Address			Debug info	Name (122 modules)
PE	  330000-  366000	Deferred        tier0
PE	  370000-  38e000	Deferred        vstdlib
PE	  390000-  3e4000	Export          filesystem_steam
PE	  400000-  41c000	Deferred        hl2
PE	 d0b0000- d1ae000	Deferred        datamodel
PE	 d2c0000- d2fd000	Deferred        dmserializers
PE	 d300000- d325000	Deferred        datacache
PE	 d330000- d344000	Deferred        inputsystem
PE	 d460000- d514000	Deferred        materialsystem
PE	 d520000- d536000	Deferred        valve_avi
PE	 d540000- d610000	Deferred        vguimatsurface
PE	 d610000- d685000	Deferred        vgui2
PE	 d690000- dc7e000	Deferred        engine
PE	 dc80000- dc94000	Deferred        steam_api
PE	10000000-10030000	Deferred        launcher
PE	20000000-20043000	Deferred        steam
PE	26000000-26138000	Deferred        vphysics
PE	2a000000-2a0a8000	Deferred        shaderapidx9
PE	2c000000-2c3e3000	Deferred        studiorender
PE	628c0000-628d9000	Deferred        parsifal
ELF	7b800000-7b93d000	Deferred        kernel32<elf>
  \-PE	7b820000-7b93d000	\               kernel32
ELF	7bc00000-7bca7000	Deferred        ntdll<elf>
  \-PE	7bc10000-7bca7000	\               ntdll
ELF	7bf00000-7bf04000	Deferred        <wine-loader>
ELF	7c5b2000-7d329000	Deferred        libglcore.so.1
ELF	7d329000-7d3cc000	Deferred        libgl.so.1
ELF	7d3cc000-7d4e1000	Deferred        wined3d<elf>
  \-PE	7d3e0000-7d4e1000	\               wined3d
ELF	7de65000-7de67000	Deferred        libnvidia-tls.so.1
ELF	7de7c000-7de91000	Deferred        winejoystick<elf>
  \-PE	7de80000-7de91000	\               winejoystick
ELF	7de91000-7dec2000	Deferred        d3d9<elf>
  \-PE	7dea0000-7dec2000	\               d3d9
ELF	7dec2000-7dee5000	Deferred        mpr<elf>
  \-PE	7ded0000-7dee5000	\               mpr
ELF	7dee5000-7df35000	Deferred        wininet<elf>
  \-PE	7def0000-7df35000	\               wininet
ELF	7df35000-7dfdb000	Deferred        oleaut32<elf>
  \-PE	7df50000-7dfdb000	\               oleaut32
ELF	7dfdb000-7dff0000	Deferred        lz32<elf>
  \-PE	7dfe0000-7dff0000	\               lz32
ELF	7dff0000-7e00b000	Deferred        version<elf>
  \-PE	7e000000-7e00b000	\               version
ELF	7e00b000-7e034000	Deferred        msvfw32<elf>
  \-PE	7e010000-7e034000	\               msvfw32
ELF	7e034000-7e070000	Deferred        avifil32<elf>
  \-PE	7e040000-7e070000	\               avifil32
ELF	7e070000-7e098000	Deferred        msacm32<elf>
  \-PE	7e080000-7e098000	\               msacm32
ELF	7e098000-7e0b1000	Deferred        msacm32<elf>
  \-PE	7e0a0000-7e0b1000	\               msacm32
ELF	7e0b1000-7e101000	Deferred        libpulse.so.0
ELF	7e101000-7e10a000	Deferred        librt.so.1
ELF	7e10a000-7e1d2000	Deferred        libasound.so.2
ELF	7e1d2000-7e1e7000	Deferred        midimap<elf>
  \-PE	7e1e0000-7e1e7000	\               midimap
ELF	7e1e7000-7e21e000	Deferred        winealsa<elf>
  \-PE	7e1f0000-7e21e000	\               winealsa
ELF	7e21e000-7e2b2000	Deferred        winmm<elf>
  \-PE	7e230000-7e2b2000	\               winmm
ELF	7e49c000-7e4cf000	Deferred        uxtheme<elf>
  \-PE	7e4a0000-7e4cf000	\               uxtheme
ELF	7e4cf000-7e594000	Deferred        comctl32<elf>
  \-PE	7e4e0000-7e594000	\               comctl32
ELF	7e594000-7e5ef000	Deferred        shlwapi<elf>
  \-PE	7e5a0000-7e5ef000	\               shlwapi
ELF	7e5ef000-7e703000	Deferred        shell32<elf>
  \-PE	7e600000-7e703000	\               shell32
ELF	7e703000-7e766000	Deferred        rpcrt4<elf>
  \-PE	7e710000-7e766000	\               rpcrt4
ELF	7e766000-7e80c000	Deferred        ole32<elf>
  \-PE	7e770000-7e80c000	\               ole32
ELF	7e80c000-7e820000	Deferred        libresolv.so.2
ELF	7e820000-7e83f000	Deferred        iphlpapi<elf>
  \-PE	7e830000-7e83f000	\               iphlpapi
ELF	7e83f000-7e86c000	Deferred        ws2_32<elf>
  \-PE	7e850000-7e86c000	\               ws2_32
ELF	7e86c000-7e887000	Deferred        wsock32<elf>
  \-PE	7e870000-7e887000	\               wsock32
ELF	7e887000-7e890000	Deferred        libxcursor.so.1
ELF	7e890000-7e895000	Deferred        libxfixes.so.3
ELF	7e895000-7e899000	Deferred        libxcomposite.so.1
ELF	7e899000-7e8a0000	Deferred        libxrandr.so.2
ELF	7e8a0000-7e8aa000	Deferred        libxrender.so.1
ELF	7e8aa000-7e8ad000	Deferred        libxinerama.so.1
ELF	7e8ad000-7e8ce000	Deferred        imm32<elf>
  \-PE	7e8b0000-7e8ce000	\               imm32
ELF	7e8ce000-7e8d3000	Deferred        libxdmcp.so.6
ELF	7e8d3000-7e8ec000	Deferred        libxcb.so.1
ELF	7e8ec000-7e8ef000	Deferred        libxcb-xlib.so.0
ELF	7e8ef000-7e8f2000	Deferred        libxau.so.6
ELF	7e8f2000-7e9e1000	Deferred        libx11.so.6
ELF	7e9e1000-7e9f0000	Deferred        libxext.so.6
ELF	7e9f0000-7ea08000	Deferred        libice.so.6
ELF	7ea08000-7ea11000	Deferred        libsm.so.6
ELF	7ea11000-7ea18000	Deferred        libasound_module_pcm_pulse.so
ELF	7ea22000-7ea26000	Deferred        libcap.so.1
ELF	7ea26000-7eac1000	Deferred        winex11<elf>
  \-PE	7ea30000-7eac1000	\               winex11
ELF	7eb39000-7eb60000	Deferred        libexpat.so.1
ELF	7eb60000-7eb8d000	Deferred        libfontconfig.so.1
ELF	7eb8d000-7eba3000	Deferred        libz.so.1
ELF	7eba3000-7ec19000	Deferred        libfreetype.so.6
ELF	7ec1b000-7ec21000	Deferred        libxxf86vm.so.1
ELF	7ec2e000-7ec81000	Deferred        advapi32<elf>
  \-PE	7ec40000-7ec81000	\               advapi32
ELF	7ec81000-7ed20000	Deferred        gdi32<elf>
  \-PE	7ec90000-7ed20000	\               gdi32
ELF	7ed20000-7ee6c000	Deferred        user32<elf>
  \-PE	7ed40000-7ee6c000	\               user32
ELF	7ef8c000-7ef98000	Deferred        libnss_files.so.2
ELF	7ef98000-7efa3000	Deferred        libnss_nis.so.2
ELF	7efa3000-7efbc000	Deferred        libnsl.so.1
ELF	7efbc000-7efc5000	Deferred        libnss_compat.so.2
ELF	7efc5000-7efeb000	Deferred        libm.so.6
ELF	b7e03000-b7e07000	Deferred        libdl.so.2
ELF	b7e07000-b7f65000	Deferred        libc.so.6
ELF	b7f65000-b7f7e000	Deferred        libpthread.so.0
ELF	b7f94000-b80cb000	Deferred        libwine.so.1
ELF	b80cb000-b80d8000	Deferred        xvnkb.so.0.2.9a
ELF	b80da000-b80f7000	Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
00000008 (D) C:\Program Files\Counter-Strike Source\hl2.exe
	00000016    2
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
00000017 
	00000018    0
Backtrace:
=>1 0x003a4a0d in filesystem_steam (+0x14a0d) (0x0032dd10)



---

### Post by bapoumba on 2009-03-27
Moved to Wine.

---

### Post by hazenvnn on 2009-03-28
Can someone help ?

---

### Post by hikaricore on 2009-03-28
Not much info to go on there please read though the sticky at the top of this forum for what you need to look at first and what info you can provide to help us help you.

[URL="http://ubuntuforums.org/showthread.php?t=885111"]http://ubuntuforums.org/showthread.php?t=885111
[IMG]http://img.photobucket.com/albums/v414/hikari_corgan/omfg-1.jpg[/IMG][/URL]

---

