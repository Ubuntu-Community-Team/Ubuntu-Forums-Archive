---
title: "Recent Wine update (1.1.23) broke all my installed applications"
date: 2009-06-13
forum: Wine
---

### Post by AFarris01 on 2009-06-13
just as the title suggests... the recent update to WINE 1.1.23 broke the installs to every single windows program i have installed.  among the not-so-happy campers:

Starcraft + Brood War
Hitman 2- Silent Assassin
Doom 2 for win95
Diablo 1 & 2
Fallout 1, 2, and Tactics
Warcraft 2
Bejweled 2 Deluxe
Robowar 5
Steam et al
Pocket Tanks Deluxe
Age of Empires 2

All the apps that actually report errors report 
```
Exception: Access Violation (code 0xc0000005) 
```
through their own error reporting systems... Below I've also included a crash report from Bejeweled 2 Deluxe... when the other programs crash, they either look pretty much the same, or they don't actually crash (but the access violation is still given)

```

fixme:ntoskrnl:KeInitializeTimerEx stub: 0x113ff8 0
err:alsa:ALSA_CheckSetVolume Could not find 'PCM Playback Volume' element
err:alsa:ALSA_CheckSetVolume Could not find 'PCM Playback Volume' element
fixme:mixer:ALSA_MixerInit No master control found on CA0106, disabling mixer
fixme:mixer:ALSA_MixerInit No master control found on HDA ATI HDMI, disabling mixer
fixme:mixer:ALSA_MixerInit No master control found on USB Device 0x46d:0x9a1, disabling mixer
wine: Unhandled page fault on read access to 0x0000003c at address 0x451d8a (thread 0009), starting debugger...
Unhandled exception: page fault on read access to 0x0000003c in 32-bit code (0x00451d8a).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:00451d8a ESP:0032d0c0 EBP:0032d0ec EFLAGS:00210202(  R- --  I   - - - )
 EAX:0000002f EBX:00000000 ECX:00110054 EDX:00110058
 ESI:00000000 EDI:00000010
Stack dump:
0x0032d0c0:  7b874ed0 00000000 0000000f 00000000
0x0032d0d0:  00000000 00000001 00110000 00001000
0x0032d0e0:  00000001 00020000 7b874ed0 0032de40
0x0032d0f0:  004651d2 00000010 0032dc2c 00000104
0x0032d100:  0032de2c 0032de28 00000010 0032e7f4
0x0032d110:  00000000 61726150 203a736d 30303030
Backtrace:
=>0 0x00451d8a in winbej2 (+0x51d8a) (0x0032d0ec)
  1 0x004651d2 in winbej2 (+0x651d2) (0x0032de40)
  2 0x00477e76 in winbej2 (+0x77e76) (0x0032e740)
  3 0x0047840e in winbej2 (+0x7840e) (0x0032e74c)
  4 0x7b844d77 UnhandledExceptionFilter+0x57() in kernel32 (0x0032e7ac)
  5 0x0053b04c in winbej2 (+0x13b04c) (0x0032e7c8)
  6 0x0052efdd in winbej2 (+0x12efdd) (0x0032ff08)
  7 0x7b877ec0 in kernel32 (+0x57ec0) (0x0032ffe8)
  8 0xb7e81da7 wine_switch_to_stack+0x17() in libwine.so.1 (0x00000000)
0x00451d8a: movl	0x3c(%esi),%eax
Modules:
Module	Address			Debug info	Name (105 modules)
PE	  400000-  5db000	Export          winbej2
ELF	7a2ac000-7b800000	Deferred        fglrx_dri.so
ELF	7b800000-7b954000	Export          kernel32<elf>
  \-PE	7b820000-7b954000	\               kernel32
ELF	7bc00000-7bcb0000	Deferred        ntdll<elf>
  \-PE	7bc10000-7bcb0000	\               ntdll
ELF	7bf00000-7bf04000	Deferred        <wine-loader>
ELF	7c416000-7c485000	Deferred        msvcrt<elf>
  \-PE	7c430000-7c485000	\               msvcrt
ELF	7c485000-7c4d4000	Deferred        dbghelp<elf>
  \-PE	7c490000-7c4d4000	\               dbghelp
ELF	7c4d4000-7c4ec000	Deferred        imagehlp<elf>
  \-PE	7c4e0000-7c4ec000	\               imagehlp
ELF	7caec000-7cb10000	Deferred        libatiadlxx.so
ELF	7cb19000-7cb2f000	Deferred        psapi<elf>
  \-PE	7cb20000-7cb2f000	\               psapi
ELF	7d32f000-7d3bd000	Deferred        libgl.so.1
ELF	7d3bd000-7d4e8000	Deferred        wined3d<elf>
  \-PE	7d3d0000-7d4e8000	\               wined3d
ELF	7ddb5000-7ddc4000	Deferred        libgcc_s.so.1
ELF	7dde3000-7de30000	Deferred        dsound<elf>
  \-PE	7ddf0000-7de30000	\               dsound
ELF	7de30000-7de88000	Deferred        ddraw<elf>
  \-PE	7de40000-7de88000	\               ddraw
ELF	7de88000-7de9c000	Deferred        lz32<elf>
  \-PE	7de90000-7de9c000	\               lz32
ELF	7de9c000-7deb7000	Deferred        version<elf>
  \-PE	7dea0000-7deb7000	\               version
ELF	7df99000-7dfcc000	Deferred        uxtheme<elf>
  \-PE	7dfa0000-7dfcc000	\               uxtheme
ELF	7dfcc000-7dfe1000	Deferred        midimap<elf>
  \-PE	7dfd0000-7dfe1000	\               midimap
ELF	7dfe1000-7e007000	Deferred        msacm32<elf>
  \-PE	7dff0000-7e007000	\               msacm32
ELF	7e007000-7e00d000	Deferred        libattr.so.1
ELF	7e00d000-7e06c000	Deferred        libpulse.so.0
ELF	7e06c000-7e134000	Deferred        libasound.so.2
ELF	7e13b000-7e153000	Deferred        msacm32<elf>
  \-PE	7e140000-7e153000	\               msacm32
ELF	7e153000-7e18a000	Deferred        winealsa<elf>
  \-PE	7e160000-7e18a000	\               winealsa
ELF	7e18a000-7e193000	Deferred        libxcursor.so.1
ELF	7e193000-7e198000	Deferred        libxfixes.so.3
ELF	7e198000-7e19c000	Deferred        libxcomposite.so.1
ELF	7e19c000-7e1a4000	Deferred        libxrandr.so.2
ELF	7e1a4000-7e1ae000	Deferred        libxrender.so.1
ELF	7e1ae000-7e1b4000	Deferred        libxxf86vm.so.1
ELF	7e1b4000-7e1b7000	Deferred        libxinerama.so.1
ELF	7e1b7000-7e1d8000	Deferred        imm32<elf>
  \-PE	7e1c0000-7e1d8000	\               imm32
ELF	7e1d8000-7e1dd000	Deferred        libxdmcp.so.6
ELF	7e1dd000-7e1f7000	Deferred        libxcb.so.1
ELF	7e1f7000-7e1fc000	Deferred        libuuid.so.1
ELF	7e1fc000-7e2eb000	Deferred        libx11.so.6
ELF	7e2eb000-7e2fb000	Deferred        libxext.so.6
ELF	7e2fb000-7e313000	Deferred        libice.so.6
ELF	7e313000-7e31c000	Deferred        libsm.so.6
ELF	7e31d000-7e324000	Deferred        libgdbm.so.3
ELF	7e324000-7e329000	Deferred        libcap.so.2
ELF	7e329000-7e330000	Deferred        libasound_module_pcm_pulse.so
ELF	7e330000-7e339000	Deferred        librt.so.1
ELF	7e33b000-7e3d7000	Deferred        winex11<elf>
  \-PE	7e350000-7e3d7000	\               winex11
ELF	7e526000-7e54d000	Deferred        libexpat.so.1
ELF	7e54d000-7e57a000	Deferred        libfontconfig.so.1
ELF	7e57a000-7e590000	Deferred        libz.so.1
ELF	7e590000-7e607000	Deferred        libfreetype.so.6
ELF	7e607000-7e6ee000	Deferred        oleaut32<elf>
  \-PE	7e620000-7e6ee000	\               oleaut32
ELF	7e6ee000-7e75b000	Deferred        rpcrt4<elf>
  \-PE	7e700000-7e75b000	\               rpcrt4
ELF	7e75b000-7e855000	Deferred        ole32<elf>
  \-PE	7e770000-7e855000	\               ole32
ELF	7e855000-7e91d000	Deferred        comctl32<elf>
  \-PE	7e860000-7e91d000	\               comctl32
ELF	7e91d000-7e97b000	Deferred        shlwapi<elf>
  \-PE	7e930000-7e97b000	\               shlwapi
ELF	7e97b000-7eb05000	Deferred        shell32<elf>
  \-PE	7e990000-7eb05000	\               shell32
ELF	7eb05000-7eb1b000	Deferred        libresolv.so.2
ELF	7eb1b000-7eb1f000	Deferred        libxau.so.6
ELF	7eb3a000-7eb5a000	Deferred        iphlpapi<elf>
  \-PE	7eb40000-7eb5a000	\               iphlpapi
ELF	7eb5a000-7eb88000	Deferred        ws2_32<elf>
  \-PE	7eb60000-7eb88000	\               ws2_32
ELF	7eb88000-7ec1f000	Deferred        winmm<elf>
  \-PE	7eb90000-7ec1f000	\               winmm
ELF	7ec1f000-7ec75000	Deferred        advapi32<elf>
  \-PE	7ec30000-7ec75000	\               advapi32
ELF	7ec75000-7ed16000	Deferred        gdi32<elf>
  \-PE	7ec90000-7ed16000	\               gdi32
ELF	7ed16000-7ee61000	Deferred        user32<elf>
  \-PE	7ed30000-7ee61000	\               user32
ELF	7ef8b000-7ef97000	Deferred        libnss_files.so.2
ELF	7ef97000-7efa2000	Deferred        libnss_nis.so.2
ELF	7efa2000-7efbb000	Deferred        libnsl.so.1
ELF	7efbb000-7efe1000	Deferred        libm.so.6
ELF	7efe3000-7effe000	Deferred        wsock32<elf>
  \-PE	7eff0000-7effe000	\               wsock32
ELF	b7cda000-b7cde000	Deferred        libdl.so.2
ELF	b7cde000-b7e41000	Deferred        libc.so.6
ELF	b7e42000-b7e5b000	Deferred        libpthread.so.0
ELF	b7e71000-b7e7a000	Deferred        libnss_compat.so.2
ELF	b7e7a000-b7fb5000	Export          libwine.so.1
ELF	b7fb7000-b7fd5000	Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
00000008 (D) C:\Program Files\Bejeweled 2 Deluxe\WinBej2.exe
	00000026   -2
	00000009    0 <==
0000000c 
	00000024    0
	00000020    0
	0000001d    0
	00000018    0
	00000013    0
	00000012    0
	0000000e    0
	0000000d    0
0000000f 
	00000014    0
	00000011    0
	00000010    0
00000015 
	00000019    0
	00000017    0
	00000016    0
0000001a 
	0000001f    0
	0000001e    0
	0000001c    0
	0000001b    0
00000021 
	00000025    0
	00000023    0
	00000022    0
00000027 
	00000028    0
Backtrace:
=>0 0x00451d8a in winbej2 (+0x51d8a) (0x0032d0ec)
  1 0x004651d2 in winbej2 (+0x651d2) (0x0032de40)
  2 0x00477e76 in winbej2 (+0x77e76) (0x0032e740)
  3 0x0047840e in winbej2 (+0x7840e) (0x0032e74c)
  4 0x7b844d77 UnhandledExceptionFilter+0x57() in kernel32 (0x0032e7ac)
  5 0x0053b04c in winbej2 (+0x13b04c) (0x0032e7c8)
  6 0x0052efdd in winbej2 (+0x12efdd) (0x0032ff08)
  7 0x7b877ec0 in kernel32 (+0x57ec0) (0x0032ffe8)
  8 0xb7e81da7 wine_switch_to_stack+0x17() in libwine.so.1 (0x00000000)


```

Anybody else having similar problems, or am I alone again?

---

### Post by cogadh on 2009-06-13
Actually, I have more games working now than I had before the update. I'm not saying you are alone, but my experience with the update has been nothing like yours (so far).

---

### Post by AFarris01 on 2009-06-13
Lucky...

Internet searches appear to show that nobody else has experienced what I am either...so far...

I'm getting ready to move my old wine install and try re-installing some of my games and see if they still fail

just out of curiosity... what did you get working? I was looking forward to the update so I could try installing fallout 3 again

---

### Post by NightMKoder on 2009-06-13
Wine 1.1.23 switched offscreenrenderingmode to default to fbo instead of backbuffer. Change it to backbuffer and see if it helps. It most likely will if you're on an ATI card.

---

### Post by AFarris01 on 2009-06-13
Thanks!

I actually just found that while reading this post: [http://ubuntuforums.org/showthread.php?p=7442213](http://ubuntuforums.org/showthread.php?p=7442213)

went and changed the offscreenrenderingmode to backbuffer, and it appears that things are workign again, though I only tested Diablo 2... (did notice it seemed a bit speedier when loading, so thats cool)

---

