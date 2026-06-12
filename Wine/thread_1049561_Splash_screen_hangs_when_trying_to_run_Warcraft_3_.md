---
title: "Splash screen hangs when trying to run Warcraft 3: TFT with wine..."
date: 2009-01-24
forum: Wine
---

### Post by Xil3 on 2009-01-24
**After issuing the following command:**

wine "C:\Program Files\Warcraft III\Frozen Throne.exe" -opengl

**I get the following errors, and the splash screen just hangs there.**

err:ole:CoCreateInstance apartment not initialised
wine: Unhandled page fault on write access to 0x771e9f8c at address 0x7d201b66 (thread 0025), starting debugger...
Unhandled exception: page fault on write access to 0x771e9f8c in 32-bit code (0x7d201b66).
Register dump:
 CS:0023 SS:002b DS:002b ES:002b FS:0063 GS:006b
 EIP:7d201b66 ESP:0033f170 EBP:00000008 EFLAGS:00010246(   - 00      -RIZP1)
 EAX:00000018 EBX:f7cd06b0 ECX:7d2554e0 EDX:771e9f8c
 ESI:f7cd06b0 EDI:000049b4
Stack dump:
0x0033f170:  00000000 7d2096c4 00000003 00000000
0x0033f180:  00000001 01fbab2c 000049b4 00000001
0x0033f190:  ffebaba8 7d209c16 f7cd06b0 000049b4
0x0033f1a0:  00000001 00000000 7b7f378c 7c31d560
0x0033f1b0:  0033f1d0 7abdf2e6 f7fbbff4 7ee8c264
0x0033f1c0:  f7e1349b f7fbbff4 7c31c1f0 00000000
Backtrace:
=>0 0x7d201b66 in libgl.so.1 (+0x65b66) (0x00000008)
  1 0x00000000 (0x00000000)
0x7d201b66: movl	$0x7d233000,0x0(%edx)
Modules:
Module	Address			Debug info	Name (120 modules)
PE	  400000-  46f000	Deferred        war3
PE	15000000-15067000	Deferred        storm
PE	21100000-2115f000	Deferred        mss32
PE	60000000-6005d000	Deferred        ijl15
ELF	7a995000-7b800000	Deferred        libglcore.so.1
ELF	7b800000-7b940000	Deferred        kernel32<elf>
  \-PE	7b820000-7b940000	\               kernel32
ELF	7bc00000-7bcad000	Deferred        ntdll<elf>
  \-PE	7bc10000-7bcad000	\               ntdll
ELF	7bf00000-7bf04000	Deferred        <wine-loader>
ELF	7d19c000-7d256000	Export          libgl.so.1
ELF	7d256000-7d2eb000	Deferred        opengl32<elf>
ELF	7d2eb000-7d30c000	Deferred        devenum<elf>
  \-PE	7d2f0000-7d30c000	\               devenum
ELF	7db37000-7db4c000	Deferred        avicap32<elf>
  \-PE	7db40000-7db4c000	\               avicap32
ELF	7db4c000-7db99000	Deferred        dsound<elf>
  \-PE	7db50000-7db99000	\               dsound
ELF	7dc0a000-7dcf6000	Deferred        oleaut32<elf>
  \-PE	7dc20000-7dcf6000	\               oleaut32
ELF	7dcf6000-7dd1f000	Deferred        msacm32<elf>
  \-PE	7dd00000-7dd1f000	\               msacm32
ELF	7dd1f000-7dd38000	Deferred        msacm32<elf>
  \-PE	7dd20000-7dd38000	\               msacm32
ELF	7dd38000-7dd50000	Deferred        libice.so.6
ELF	7dd50000-7dda0000	Deferred        libpulse.so.0
ELF	7dda2000-7ddb7000	Deferred        midimap<elf>
  \-PE	7ddb0000-7ddb7000	\               midimap
ELF	7ddb7000-7ddc0000	Deferred        librt.so.1
ELF	7ddc0000-7de88000	Deferred        libasound.so.2
ELF	7de88000-7debf000	Deferred        winealsa<elf>
  \-PE	7de90000-7debf000	\               winealsa
ELF	7debf000-7dec3000	Deferred        libgpg-error.so.0
ELF	7dec3000-7df2c000	Deferred        libgcrypt.so.11
ELF	7df2c000-7df3e000	Deferred        libtasn1.so.3
ELF	7df3e000-7df42000	Deferred        libkeyutils.so.1
ELF	7df42000-7df4b000	Deferred        libkrb5support.so.0
ELF	7df4b000-7df7d000	Deferred        libcrypt.so.1
ELF	7df7d000-7e01a000	Deferred        libgnutls.so.26
ELF	7e01a000-7e03e000	Deferred        libk5crypto.so.3
ELF	7e03e000-7e0d0000	Deferred        libkrb5.so.3
ELF	7e0d0000-7e0fa000	Deferred        libgssapi_krb5.so.2
ELF	7e0fa000-7e130000	Deferred        libcups.so.2
ELF	7e133000-7e137000	Deferred        libcap.so.1
ELF	7e137000-7e140000	Deferred        libsm.so.6
ELF	7e140000-7e147000	Deferred        libasound_module_pcm_pulse.so
ELF	7e174000-7e1db000	Deferred        rpcrt4<elf>
  \-PE	7e180000-7e1db000	\               rpcrt4
ELF	7e1db000-7e2ed000	Deferred        ole32<elf>
  \-PE	7e200000-7e2ed000	\               ole32
ELF	7e2ed000-7e2f1000	Deferred        libcom_err.so.2
ELF	7e304000-7e337000	Deferred        uxtheme<elf>
  \-PE	7e310000-7e337000	\               uxtheme
ELF	7e337000-7e340000	Deferred        libxcursor.so.1
ELF	7e340000-7e345000	Deferred        libxfixes.so.3
ELF	7e345000-7e349000	Deferred        libxcomposite.so.1
ELF	7e349000-7e350000	Deferred        libxrandr.so.2
ELF	7e350000-7e35a000	Deferred        libxrender.so.1
ELF	7e35a000-7e360000	Deferred        libxxf86vm.so.1
ELF	7e360000-7e379000	Deferred        libxcb.so.1
ELF	7e379000-7e468000	Deferred        libx11.so.6
ELF	7e468000-7e477000	Deferred        libxext.so.6
ELF	7e48e000-7e52a000	Deferred        winex11<elf>
  \-PE	7e4a0000-7e52a000	\               winex11
ELF	7e571000-7e598000	Deferred        libexpat.so.1
ELF	7e598000-7e5c5000	Deferred        libfontconfig.so.1
ELF	7e5c5000-7e5db000	Deferred        libz.so.1
ELF	7e5db000-7e651000	Deferred        libfreetype.so.6
ELF	7e651000-7e674000	Deferred        mpr<elf>
  \-PE	7e660000-7e674000	\               mpr
ELF	7e674000-7e6c5000	Deferred        wininet<elf>
  \-PE	7e680000-7e6c5000	\               wininet
ELF	7e6c5000-7e6e6000	Deferred        imm32<elf>
  \-PE	7e6d0000-7e6e6000	\               imm32
ELF	7e6e6000-7e6fa000	Deferred        libresolv.so.2
ELF	7e6fb000-7e6fe000	Deferred        libxinerama.so.1
ELF	7e6fe000-7e703000	Deferred        libxdmcp.so.6
ELF	7e711000-7e731000	Deferred        iphlpapi<elf>
  \-PE	7e720000-7e731000	\               iphlpapi
ELF	7e731000-7e75e000	Deferred        ws2_32<elf>
  \-PE	7e740000-7e75e000	\               ws2_32
ELF	7e75e000-7e779000	Deferred        wsock32<elf>
  \-PE	7e760000-7e779000	\               wsock32
ELF	7e779000-7e794000	Deferred        version<elf>
  \-PE	7e780000-7e794000	\               version
ELF	7e794000-7e801000	Deferred        msvcrt<elf>
  \-PE	7e7a0000-7e801000	\               msvcrt
ELF	7e801000-7e895000	Deferred        winmm<elf>
  \-PE	7e810000-7e895000	\               winmm
ELF	7e895000-7e8cc000	Deferred        winspool<elf>
  \-PE	7e8a0000-7e8cc000	\               winspool
ELF	7e8cc000-7e993000	Deferred        comctl32<elf>
  \-PE	7e8d0000-7e993000	\               comctl32
ELF	7e993000-7e9f0000	Deferred        shlwapi<elf>
  \-PE	7e9a0000-7e9f0000	\               shlwapi
ELF	7e9f0000-7eb6b000	Deferred        shell32<elf>
  \-PE	7ea00000-7eb6b000	\               shell32
ELF	7eb6b000-7ec19000	Deferred        comdlg32<elf>
  \-PE	7eb70000-7ec19000	\               comdlg32
ELF	7ec19000-7ec6e000	Deferred        advapi32<elf>
  \-PE	7ec30000-7ec6e000	\               advapi32
ELF	7ec6e000-7ed0f000	Deferred        gdi32<elf>
  \-PE	7ec80000-7ed0f000	\               gdi32
ELF	7ed0f000-7ee5e000	Deferred        user32<elf>
  \-PE	7ed30000-7ee5e000	\               user32
ELF	7ee5e000-7ee6a000	Deferred        libnss_files.so.2
ELF	7ee6a000-7ee83000	Deferred        libnsl.so.1
ELF	7ee83000-7ee8c000	Deferred        libnss_compat.so.2
ELF	7ee8c000-7ee8e000	Deferred        libnvidia-tls.so.1
ELF	7ee8e000-7eea3000	Deferred        lz32<elf>
  \-PE	7ee90000-7eea3000	\               lz32
ELF	7efc3000-7efe9000	Deferred        libm.so.6
ELF	7efeb000-7efee000	Deferred        libxcb-xlib.so.0
ELF	7efee000-7eff1000	Deferred        libxau.so.6
ELF	7eff2000-7effd000	Deferred        libnss_nis.so.2
ELF	f7cd1000-f7cd5000	Deferred        libdl.so.2
ELF	f7cd5000-f7e33000	Deferred        libc.so.6
ELF	f7e34000-f7e4d000	Deferred        libpthread.so.0
ELF	f7e64000-f7f9b000	Deferred        libwine.so.1
ELF	f7f9d000-f7fbd000	Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
0000000c 
	0000000e    0
	0000000d    0
0000001f 
	00000023    0
	00000020    0
00000021 
	00000022    0
00000024 (D) C:\Program Files\Warcraft III\war3.exe
	00000025    0 <==
Backtrace:
=>0 0x7d201b66 in libgl.so.1 (+0x65b66) (0x00000008)
  1 0x00000000 (0x00000000)

---

### Post by Xil3 on 2009-01-24
I forgot to add a few things - I'm currently running Ubuntu 8.10 and using the latest version of Wine.

And yes I do have the proper drivers installed for my video card, and it's working fine.

---

### Post by maximMK on 2009-01-24
if u cant fix it use Windows:D:D:D

---

### Post by Xil3 on 2009-01-24
> **maximMK said:**
> if u cant fix it use Windows:D:D:D

How helpful :)

---

### Post by hotweiss on 2009-01-24
run warcraft 3 with the -opengl switch

See if you get any errors if you paste this in Terminal:

> wine .wine/drive_c/Program\ Files/Warcraft\ III/Frozen\ Throne.exe -opengl

...but I think this is a video card driver problem. As I have had this problem myself before. The Nvidia 180.22 AMD64 drivers break libgl.so.1 and you get the same error. The solution was to install the 177.82 drivers and then the 180.22 drivers over top of them.

---

### Post by binbash on 2009-01-24
did you rename the movie folder?

---

### Post by Xil3 on 2009-01-24
> **hotweiss said:**
> run warcraft 3 with the -opengl switch

See if you get any errors if you paste this in Terminal:



...but I think this is a video card driver problem. As I have had this problem myself before. The Nvidia 180.22 AMD64 drivers break libgl.so.1 and you get the same error. The solution was to install the 177.82 drivers and then the 180.22 drivers over top of them.

**Tried what you said below:**

jon@jon-desktop:~$ wine .wine/drive_c/Program\ Files/Warcraft\ III/Frozen\ Throne.exe -opengl

**And got the following errors: (looks like the same errors that I've been getting from before)**

err:ole:CoCreateInstance apartment not initialised
wine: Unhandled page fault on write access to 0x7bfeb6fb at address 0x7d207b66 (thread 0030), starting debugger...
Unhandled exception: page fault on write access to 0x7bfeb6fb in 32-bit code (0x7d207b66).
Register dump:
 CS:0023 SS:002b DS:002b ES:002b FS:0063 GS:006b
 EIP:7d207b66 ESP:0033f178 EBP:00000008 EFLAGS:00010246(   - 00      -RIZP1)
 EAX:00000018 EBX:f7c936b0 ECX:7d25b4e0 EDX:7bfeb6fb
 ESI:f7c936b0 EDI:000009b3
Stack dump:
0x0033f178:  00000000 7d20f6c4 00000003 00000000
0x0033f188:  00000001 01fbab2c 000009b3 00000001
0x0033f198:  ffc80198 7d20fc16 f7c936b0 000009b3
0x0033f1a8:  00000001 00000000 7b7f378c 7cc508d8
0x0033f1b8:  0033f1d8 7abdf2e6 f7f7eff4 7e48c264
0x0033f1c8:  f7dd649b f7f7eff4 7cc4fe98 00000000
Backtrace:
=>0 0x7d207b66 in libgl.so.1 (+0x65b66) (0x00000008)
  1 0x00000000 (0x00000000)
0x7d207b66: movl	$0x7d239000,0x0(%edx)
Modules:
Module	Address			Debug info	Name (121 modules)
PE	  400000-  47d000	Deferred        war3
PE	15000000-15061000	Deferred        storm
PE	21100000-2115f000	Deferred        mss32
PE	60000000-6005d000	Deferred        ijl15
PE	78130000-781cb000	Deferred        msvcr80
ELF	7a995000-7b800000	Deferred        libglcore.so.1
ELF	7b800000-7b940000	Deferred        kernel32<elf>
  \-PE	7b820000-7b940000	\               kernel32
ELF	7bc00000-7bcad000	Deferred        ntdll<elf>
  \-PE	7bc10000-7bcad000	\               ntdll
ELF	7bf00000-7bf04000	Deferred        <wine-loader>
ELF	7d1a2000-7d25c000	Export          libgl.so.1
ELF	7d25c000-7d2f1000	Deferred        opengl32<elf>
ELF	7d2f1000-7d312000	Deferred        devenum<elf>
  \-PE	7d300000-7d312000	\               devenum
ELF	7d33c000-7d389000	Deferred        dsound<elf>
  \-PE	7d340000-7d389000	\               dsound
ELF	7d3fa000-7d4e6000	Deferred        oleaut32<elf>
  \-PE	7d410000-7d4e6000	\               oleaut32
ELF	7d4e6000-7d54f000	Deferred        libgcrypt.so.11
ELF	7d54f000-7d561000	Deferred        libtasn1.so.3
ELF	7d561000-7d593000	Deferred        libcrypt.so.1
ELF	7d593000-7d630000	Deferred        libgnutls.so.26
ELF	7d630000-7d654000	Deferred        libk5crypto.so.3
ELF	7d654000-7d6e6000	Deferred        libkrb5.so.3
ELF	7d6e6000-7d710000	Deferred        libgssapi_krb5.so.2
ELF	7d710000-7d746000	Deferred        libcups.so.2
ELF	7d748000-7d75d000	Deferred        avicap32<elf>
  \-PE	7d750000-7d75d000	\               avicap32
ELF	7df82000-7df86000	Deferred        libgpg-error.so.0
ELF	7df86000-7df8a000	Deferred        libkeyutils.so.1
ELF	7df8a000-7df93000	Deferred        libkrb5support.so.0
ELF	7df9c000-7e003000	Deferred        rpcrt4<elf>
  \-PE	7dfb0000-7e003000	\               rpcrt4
ELF	7e003000-7e115000	Deferred        ole32<elf>
  \-PE	7e020000-7e115000	\               ole32
ELF	7e115000-7e119000	Deferred        libcom_err.so.2
ELF	7e141000-7e16a000	Deferred        msacm32<elf>
  \-PE	7e150000-7e16a000	\               msacm32
ELF	7e16a000-7e183000	Deferred        msacm32<elf>
  \-PE	7e170000-7e183000	\               msacm32
ELF	7e183000-7e19b000	Deferred        libice.so.6
ELF	7e19b000-7e1eb000	Deferred        libpulse.so.0
ELF	7e1ed000-7e202000	Deferred        midimap<elf>
  \-PE	7e1f0000-7e202000	\               midimap
ELF	7e202000-7e20b000	Deferred        librt.so.1
ELF	7e20b000-7e2d3000	Deferred        libasound.so.2
ELF	7e2d3000-7e30a000	Deferred        winealsa<elf>
  \-PE	7e2e0000-7e30a000	\               winealsa
ELF	7e30a000-7e33d000	Deferred        uxtheme<elf>
  \-PE	7e310000-7e33d000	\               uxtheme
ELF	7e33d000-7e346000	Deferred        libxcursor.so.1
ELF	7e346000-7e34b000	Deferred        libxfixes.so.3
ELF	7e34b000-7e34f000	Deferred        libxcomposite.so.1
ELF	7e34f000-7e356000	Deferred        libxrandr.so.2
ELF	7e356000-7e360000	Deferred        libxrender.so.1
ELF	7e360000-7e366000	Deferred        libxxf86vm.so.1
ELF	7e366000-7e369000	Deferred        libxinerama.so.1
ELF	7e369000-7e36e000	Deferred        libxdmcp.so.6
ELF	7e36e000-7e387000	Deferred        libxcb.so.1
ELF	7e387000-7e38a000	Deferred        libxcb-xlib.so.0
ELF	7e38a000-7e38d000	Deferred        libxau.so.6
ELF	7e38d000-7e47c000	Deferred        libx11.so.6
ELF	7e47c000-7e48b000	Deferred        libxext.so.6
ELF	7e48c000-7e48e000	Deferred        libnvidia-tls.so.1
ELF	7e48e000-7e492000	Deferred        libcap.so.1
ELF	7e492000-7e49b000	Deferred        libsm.so.6
ELF	7e49b000-7e4a2000	Deferred        libasound_module_pcm_pulse.so
ELF	7e4a2000-7e53e000	Deferred        winex11<elf>
  \-PE	7e4b0000-7e53e000	\               winex11
ELF	7e57d000-7e5a4000	Deferred        libexpat.so.1
ELF	7e5a4000-7e5d1000	Deferred        libfontconfig.so.1
ELF	7e5d1000-7e5e7000	Deferred        libz.so.1
ELF	7e5e7000-7e65d000	Deferred        libfreetype.so.6
ELF	7e65d000-7e67e000	Deferred        imm32<elf>
  \-PE	7e660000-7e67e000	\               imm32
ELF	7e67e000-7e692000	Deferred        libresolv.so.2
ELF	7e6a9000-7e6c9000	Deferred        iphlpapi<elf>
  \-PE	7e6b0000-7e6c9000	\               iphlpapi
ELF	7e6c9000-7e6f6000	Deferred        ws2_32<elf>
  \-PE	7e6d0000-7e6f6000	\               ws2_32
ELF	7e6f6000-7e711000	Deferred        wsock32<elf>
  \-PE	7e700000-7e711000	\               wsock32
ELF	7e711000-7e734000	Deferred        mpr<elf>
  \-PE	7e720000-7e734000	\               mpr
ELF	7e734000-7e785000	Deferred        wininet<elf>
  \-PE	7e740000-7e785000	\               wininet
ELF	7e785000-7e7a0000	Deferred        version<elf>
  \-PE	7e790000-7e7a0000	\               version
ELF	7e7a0000-7e80d000	Deferred        msvcrt<elf>
  \-PE	7e7b0000-7e80d000	\               msvcrt
ELF	7e80d000-7e844000	Deferred        winspool<elf>
  \-PE	7e810000-7e844000	\               winspool
ELF	7e844000-7e8a1000	Deferred        shlwapi<elf>
  \-PE	7e850000-7e8a1000	\               shlwapi
ELF	7e8a1000-7ea1c000	Deferred        shell32<elf>
  \-PE	7e8b0000-7ea1c000	\               shell32
ELF	7ea1c000-7eaca000	Deferred        comdlg32<elf>
  \-PE	7ea20000-7eaca000	\               comdlg32
ELF	7eaca000-7eb5e000	Deferred        winmm<elf>
  \-PE	7eae0000-7eb5e000	\               winmm
ELF	7eb5e000-7ebb3000	Deferred        advapi32<elf>
  \-PE	7eb70000-7ebb3000	\               advapi32
ELF	7ebb3000-7ec54000	Deferred        gdi32<elf>
  \-PE	7ebc0000-7ec54000	\               gdi32
ELF	7ec54000-7eda3000	Deferred        user32<elf>
  \-PE	7ec70000-7eda3000	\               user32
ELF	7eda3000-7ee6a000	Deferred        comctl32<elf>
  \-PE	7edb0000-7ee6a000	\               comctl32
ELF	7ee6a000-7ee83000	Deferred        libnsl.so.1
ELF	7ee83000-7ee8c000	Deferred        libnss_compat.so.2
ELF	7ee8d000-7eea2000	Deferred        lz32<elf>
  \-PE	7ee90000-7eea2000	\               lz32
ELF	7efc3000-7efe9000	Deferred        libm.so.6
ELF	7efe9000-7eff5000	Deferred        libnss_files.so.2
ELF	7eff5000-7f000000	Deferred        libnss_nis.so.2
ELF	f7c94000-f7c98000	Deferred        libdl.so.2
ELF	f7c98000-f7df6000	Deferred        libc.so.6
ELF	f7df7000-f7e10000	Deferred        libpthread.so.0
ELF	f7e27000-f7f5e000	Deferred        libwine.so.1
ELF	f7f60000-f7f80000	Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
0000000c 
	0000000e    0
	0000000d    0
00000011 
	00000012    0
00000013 
	00000014    0
0000002c 
	0000002e    0
	0000002d    0
0000002f (D) Z:\home\jon\.wine\drive_c\program files\warcraft iii\war3.exe
	00000030    0 <==
Backtrace:
=>0 0x7d207b66 in libgl.so.1 (+0x65b66) (0x00000008)
  1 0x00000000 (0x00000000)

---

### Post by Xil3 on 2009-01-24
> **binbash said:**
> did you rename the movie folder?

Yes, the movie folder was renamed.

---

### Post by Xil3 on 2009-01-24
Yea, it looks like I have the 180.22 nvidia drivers installed - so, you think I should uninstall those and install the 177.82 version and the 180.22 right after that?

---

### Post by hotweiss on 2009-01-24
> **Xil3 said:**
> Yea, it looks like I have the 180.22 nvidia drivers installed - so, you think I should uninstall those and install the 177.82 version and the 180.22 right after that?

Yes, that should fix your problems. I think your error is identical to mine.

---

### Post by Xil3 on 2009-01-25
> **hotweiss said:**
> Yes, that should fix your problems. I think your error is identical to mine.

Yeah, that seems to have done it, but it was a big pain in the end - I removed the drivers and installed the 177 one from the ubuntu distribution, which it didn't detect, so I had to go back in and uninstall everything again and install the nvidia downloaded drivers from the root prompt in safety mode.

Thanks for your help though!

---

### Post by hotweiss on 2009-01-25
> **Xil3 said:**
> Yeah, that seems to have done it, but it was a big pain in the end - I removed the drivers and installed the 177 one from the ubuntu distribution, which it didn't detect, so I had to go back in and uninstall everything again and install the nvidia downloaded drivers from the root prompt in safety mode.

Thanks for your help though!

I had the same problems as you. I don't why Envy doesn't work after a regular Nvidia driver install?

---

