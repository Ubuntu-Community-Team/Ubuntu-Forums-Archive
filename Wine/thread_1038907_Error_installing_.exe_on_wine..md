---
title: "Error installing .exe on wine."
date: 2009-01-14
forum: Wine
---

### Post by tabithaboof on 2009-01-14
I am trying to install adobe air on wine. I do know there is a linux version of this available but I need to use the windows version for a wine only gaming app called ggpo ([http://ggpo.net/blog/](http://ggpo.net/blog/))

I have a couple of other wine apps up and running nicely but, when I install double click on the adobe installer .exe my HD light flashing indicating something is happening but no install window appears. I tried running it in terminal and I get the following code which im afraid i dont understand. Sorry its a long post. Any help much appreciated.

```
david@trina ~/Desktop $ wine AdobeAIRInstaller.exe
fixme:console:AttachConsole stub ffffffff
fixme:console:AttachConsole stub ffffffff
err:alsa:ALSA_CheckSetVolume Could not find 'PCM Playback Volume' element
err:alsa:ALSA_CheckSetVolume Could not find 'PCM Playback Volume' element
fixme:mixer:ALSA_MixerInit No master control found on EDIROL UA-25, disabling mixer
fixme:secur32:schan_FreeCredentialsHandle (0x1771e8): stub
wine: Unhandled page fault on read access to 0x00000000 at address 0x5392a6b (thread 0026), starting debugger...
Unhandled exception: page fault on read access to 0x00000000 in 32-bit code (0x05392a6b).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:05392a6b ESP:0033f0e0 EBP:00000000 EFLAGS:00010246(   - 00      -RIZP1)
 EAX:00000000 EBX:06090bc0 ECX:0033f0b0 EDX:060bb048
 ESI:00000000 EDI:060e6b80
Stack dump:
0x0033f0e0:  00000005 053773aa 00000000 00000000
0x0033f0f0:  06090bc0 00000005 05436aa0 00000000
0x0033f100:  00000044 00000000 06090bc0 00000001
0x0033f110:  ffffffff 05447d8a 00000000 00000005
0x0033f120:  060e6b14 00000000 00000000 00000000
0x0033f130:  06090bc0 06090a74 00c3368f 01010000
Backtrace:
=>1 0x05392a6b in webkit (+0x1b2a6b) (0x00000000)
0x05392a6b: movl	0x0(%esi),%eax
Modules:
Module	Address			Debug info	Name (127 modules)
PE	  400000-  40c000	Deferred        adobe air installer
PE	 51e0000- 607e000	Export          webkit
PE	10000000-1084e000	Deferred        adobe air
ELF	7b800000-7b93d000	Deferred        kernel32<elf>
  \-PE	7b820000-7b93d000	\               kernel32
ELF	7bc00000-7bca7000	Deferred        ntdll<elf>
  \-PE	7bc10000-7bca7000	\               ntdll
ELF	7bf00000-7bf04000	Deferred        <wine-loader>
ELF	7d378000-7d39f000	Deferred        netapi32<elf>
  \-PE	7d380000-7d39f000	\               netapi32
ELF	7d39f000-7d3c7000	Deferred        secur32<elf>
  \-PE	7d3b0000-7d3c7000	\               secur32
ELF	7d3c7000-7d430000	Deferred        libgcrypt.so.11
ELF	7d430000-7d4cd000	Deferred        libgnutls.so.26
ELF	7dcce000-7dce7000	Deferred        usp10<elf>
  \-PE	7dcd0000-7dce7000	\               usp10
ELF	7dce7000-7dcf6000	Deferred        libgcc_s.so.1
ELF	7dcf6000-7dd17000	Deferred        mlang<elf>
  \-PE	7dd00000-7dd17000	\               mlang
ELF	7dd17000-7dd1b000	Deferred        libgpg-error.so.0
ELF	7dd1b000-7dd2d000	Deferred        libtasn1.so.3
ELF	7dd2d000-7dd31000	Deferred        libkeyutils.so.1
ELF	7dd31000-7dd63000	Deferred        libcrypt.so.1
ELF	7dd63000-7dd87000	Deferred        libk5crypto.so.3
ELF	7dd87000-7de19000	Deferred        libkrb5.so.3
ELF	7de19000-7de43000	Deferred        libgssapi_krb5.so.2
ELF	7de43000-7de79000	Deferred        libcups.so.2
ELF	7de79000-7de8e000	Deferred        midimap<elf>
  \-PE	7de80000-7de8e000	\               midimap
ELF	7de8e000-7deb6000	Deferred        msacm32<elf>
  \-PE	7de90000-7deb6000	\               msacm32
ELF	7deb6000-7decf000	Deferred        msacm32<elf>
  \-PE	7dec0000-7decf000	\               msacm32
ELF	7decf000-7df1f000	Deferred        libpulse.so.0
ELF	7df32000-7df3b000	Deferred        librt.so.1
ELF	7df3b000-7e003000	Deferred        libasound.so.2
ELF	7e003000-7e03a000	Deferred        winealsa<elf>
  \-PE	7e010000-7e03a000	\               winealsa
ELF	7e03a000-7e06e000	Deferred        liblcms.so.1
ELF	7e071000-7e07a000	Deferred        libkrb5support.so.0
ELF	7e07a000-7e081000	Deferred        libasound_module_pcm_pulse.so
ELF	7e081000-7e09f000	Deferred        mscms<elf>
  \-PE	7e090000-7e09f000	\               mscms
ELF	7e09f000-7e0d6000	Deferred        winspool<elf>
  \-PE	7e0b0000-7e0d6000	\               winspool
ELF	7e0d6000-7e184000	Deferred        comdlg32<elf>
  \-PE	7e0e0000-7e184000	\               comdlg32
ELF	7e184000-7e198000	Deferred        msimg32<elf>
  \-PE	7e190000-7e198000	\               msimg32
ELF	7e198000-7e1c5000	Deferred        ws2_32<elf>
  \-PE	7e1a0000-7e1c5000	\               ws2_32
ELF	7e1c5000-7e22e000	Deferred        crypt32<elf>
  \-PE	7e1d0000-7e22e000	\               crypt32
ELF	7e22e000-7e2c2000	Deferred        winmm<elf>
  \-PE	7e240000-7e2c2000	\               winmm
ELF	7e30e000-7e341000	Deferred        uxtheme<elf>
  \-PE	7e310000-7e341000	\               uxtheme
ELF	7e341000-7e34a000	Deferred        libxcursor.so.1
ELF	7e34a000-7e34f000	Deferred        libxfixes.so.3
ELF	7e34f000-7e353000	Deferred        libxcomposite.so.1
ELF	7e353000-7e35a000	Deferred        libxrandr.so.2
ELF	7e35a000-7e364000	Deferred        libxrender.so.1
ELF	7e364000-7e367000	Deferred        libxinerama.so.1
ELF	7e367000-7e388000	Deferred        imm32<elf>
  \-PE	7e370000-7e388000	\               imm32
ELF	7e388000-7e38d000	Deferred        libxdmcp.so.6
ELF	7e38d000-7e3a6000	Deferred        libxcb.so.1
ELF	7e3a6000-7e495000	Deferred        libx11.so.6
ELF	7e495000-7e4a4000	Deferred        libxext.so.6
ELF	7e4a4000-7e4aa000	Deferred        libxxf86vm.so.1
ELF	7e4aa000-7e4c2000	Deferred        libice.so.6
ELF	7e4c4000-7e4c8000	Deferred        libcom_err.so.2
ELF	7e4d1000-7e4d5000	Deferred        libcap.so.1
ELF	7e4d5000-7e570000	Deferred        winex11<elf>
  \-PE	7e4e0000-7e570000	\               winex11
ELF	7e570000-7e597000	Deferred        libexpat.so.1
ELF	7e597000-7e5c4000	Deferred        libfontconfig.so.1
ELF	7e5d7000-7e5ed000	Deferred        libz.so.1
ELF	7e5ed000-7e663000	Deferred        libfreetype.so.6
ELF	7e663000-7e678000	Deferred        lz32<elf>
  \-PE	7e670000-7e678000	\               lz32
ELF	7e678000-7e693000	Deferred        version<elf>
  \-PE	7e680000-7e693000	\               version
ELF	7e693000-7e739000	Deferred        oleaut32<elf>
  \-PE	7e6a0000-7e739000	\               oleaut32
ELF	7e739000-7e75b000	Deferred        cabinet<elf>
  \-PE	7e740000-7e75b000	\               cabinet
ELF	7e75b000-7e820000	Deferred        comctl32<elf>
  \-PE	7e760000-7e820000	\               comctl32
ELF	7e820000-7e934000	Deferred        shell32<elf>
  \-PE	7e830000-7e934000	\               shell32
ELF	7e934000-7e957000	Deferred        mpr<elf>
  \-PE	7e940000-7e957000	\               mpr
ELF	7e957000-7e9a7000	Deferred        wininet<elf>
  \-PE	7e960000-7e9a7000	\               wininet
ELF	7e9a7000-7ea02000	Deferred        shlwapi<elf>
  \-PE	7e9b0000-7ea02000	\               shlwapi
ELF	7ea02000-7ea16000	Deferred        libresolv.so.2
ELF	7ea16000-7ea35000	Deferred        iphlpapi<elf>
  \-PE	7ea20000-7ea35000	\               iphlpapi
ELF	7ea35000-7ea98000	Deferred        rpcrt4<elf>
  \-PE	7ea40000-7ea98000	\               rpcrt4
ELF	7ea98000-7eb3e000	Deferred        ole32<elf>
  \-PE	7eab0000-7eb3e000	\               ole32
ELF	7eb3e000-7eb7d000	Deferred        urlmon<elf>
  \-PE	7eb50000-7eb7d000	\               urlmon
ELF	7eb7d000-7ec28000	Deferred        msi<elf>
  \-PE	7eb90000-7ec28000	\               msi
ELF	7ec28000-7ec7b000	Deferred        advapi32<elf>
  \-PE	7ec30000-7ec7b000	\               advapi32
ELF	7ec7b000-7ed1a000	Deferred        gdi32<elf>
  \-PE	7ec90000-7ed1a000	\               gdi32
ELF	7ed1a000-7ee66000	Deferred        user32<elf>
  \-PE	7ed30000-7ee66000	\               user32
ELF	7ee66000-7ee72000	Deferred        libnss_files.so.2
ELF	7ee72000-7ee8b000	Deferred        libnsl.so.1
ELF	7ee8b000-7ee94000	Deferred        libnss_compat.so.2
ELF	7ee95000-7ee98000	Deferred        libxcb-xlib.so.0
ELF	7ee98000-7eea1000	Deferred        libsm.so.6
ELF	7efc7000-7efed000	Deferred        libm.so.6
ELF	7efef000-7eff2000	Deferred        libxau.so.6
ELF	7eff5000-7f000000	Deferred        libnss_nis.so.2
ELF	b7c5b000-b7c5f000	Deferred        libdl.so.2
ELF	b7c5f000-b7dbd000	Deferred        libc.so.6
ELF	b7dbe000-b7dd7000	Deferred        libpthread.so.0
ELF	b7dea000-b7f21000	Deferred        libwine.so.1
ELF	b7f23000-b7f40000	Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
0000000c 
	00000012    0
	0000000e    0
	0000000d    0
0000000f 
	00000015    0
	00000014    0
	00000011    0
	00000010    0
00000016 
	00000018    0
	00000017    0
00000019 
	00000020   15
	0000001e    0
	0000001d    0
00000023 
	00000025    0
	00000024    0
00000029 
	0000002e   15
	0000002c    0
	0000002b    0
00000027 
	0000002a    0
	00000030    0
0000002f 
	00000035   15
	00000034    0
	00000037    0
00000041 
	0000002d    0
	0000001f    0
00000047 (D) C:\windows\temp\AIR9b43.tmp\Adobe AIR Installer.exe
	0000003a   15
	00000039    0
	00000044    0
	00000026    0 <==
Backtrace:
=>1 0x05392a6b in webkit (+0x1b2a6b) (0x00000000)



```

---

### Post by Ahadiel on 2009-01-14
Check [http://appdb.winehq.org/]("http://appdb.winehq.org/").

---

### Post by tabithaboof on 2009-01-14
Thanks, thats a useful page for sure but I have checked it and it doesn't really tell me much other than it SHOULD work. So I know im on the right track.

---

### Post by mc4man on 2009-01-14
In winecfg, did you configure the audio? There's a tab for it, maybe pick alsa to start...?

---

### Post by ratmandall on 2009-01-14
[http://appdb.winehq.org/objectManager.php?sClass=version&iId=9238](http://appdb.winehq.org/objectManager.php?sClass=version&iId=9238)
That's a review of it which rates it "garbage", which also get's some errors like yours.
```

fixme:console:AttachConsole stub ffffffff
fixme:console:AttachConsole stub ffffffff

wine: Unhandled page fault on read access to 0x00000004 at address 0x10140d66 (thread 002e), starting debugger... 

Unhandled exception: page fault on read access to 0x00000004 in 32-bit code (0x10140d66).

Register dump: 
```

---

### Post by binbash on 2009-01-14
there is a linux version of adobe air :

[http://www.adobe.com/products/air/](http://www.adobe.com/products/air/)

---

### Post by tabithaboof on 2009-01-17
Ok, the audio settings advice was helpful, it got me a little further I think. However I sill haven't managed to get it working. Output from terminal follows.

> **binbash said:**
> there is a linux version of adobe air :

[http://www.adobe.com/products/air/](http://www.adobe.com/products/air/)

Thanks alot for the heads up but I think I mentioned in my first post, I am trying to install a windows only air app so I really do need the wine version of air or its not going to work.

```
david@trina ~/Desktop $ wine AdobeAIRInstaller.exe
fixme:console:AttachConsole stub ffffffff
fixme:console:AttachConsole stub ffffffff
fixme:secur32:schan_FreeCredentialsHandle (0x170c18): stub
wine: Unhandled page fault on read access to 0x00000000 at address 0x5392a6b (thread 0019), starting debugger...
Unhandled exception: page fault on read access to 0x00000000 in 32-bit code (0x05392a6b).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:05392a6b ESP:0033f0e0 EBP:00000000 EFLAGS:00010246(   - 00      -RIZP1)
 EAX:00000000 EBX:06090ba8 ECX:0033f0b0 EDX:060bb008
 ESI:00000000 EDI:060e6b40
Stack dump:
0x0033f0e0:  00000005 053773aa 00000000 00000000
0x0033f0f0:  06090ba8 00000005 05436aa0 00000000
0x0033f100:  00000044 00000000 06090ba8 00000001
0x0033f110:  ffffffff 05447d8a 00000000 00000005
0x0033f120:  060e6ad4 00000000 00000000 00000000
0x0033f130:  06090ba8 06090a5c 00c3368f 01010000
Backtrace:
=>1 0x05392a6b in webkit (+0x1b2a6b) (0x00000000)
0x05392a6b: movl	0x0(%esi),%eax
Modules:
Module	Address			Debug info	Name (122 modules)
PE	  400000-  40c000	Deferred        adobe air installer
PE	 51e0000- 607e000	Export          webkit
PE	10000000-1084e000	Deferred        adobe air
ELF	7b800000-7b93d000	Deferred        kernel32<elf>
  \-PE	7b820000-7b93d000	\               kernel32
ELF	7bc00000-7bca7000	Deferred        ntdll<elf>
  \-PE	7bc10000-7bca7000	\               ntdll
ELF	7bf00000-7bf04000	Deferred        <wine-loader>
ELF	7d7e2000-7d7fb000	Deferred        usp10<elf>
  \-PE	7d7f0000-7d7fb000	\               usp10
ELF	7dcbb000-7dce2000	Deferred        netapi32<elf>
  \-PE	7dcc0000-7dce2000	\               netapi32
ELF	7dce2000-7dd0a000	Deferred        secur32<elf>
  \-PE	7dcf0000-7dd0a000	\               secur32
ELF	7dd0a000-7dd19000	Deferred        libgcc_s.so.1
ELF	7dd19000-7dd3a000	Deferred        mlang<elf>
  \-PE	7dd20000-7dd3a000	\               mlang
ELF	7dd3a000-7dd3e000	Deferred        libgpg-error.so.0
ELF	7dd3e000-7dda7000	Deferred        libgcrypt.so.11
ELF	7dda7000-7ddb9000	Deferred        libtasn1.so.3
ELF	7ddb9000-7ddc2000	Deferred        libkrb5support.so.0
ELF	7ddc2000-7ddf4000	Deferred        libcrypt.so.1
ELF	7ddf4000-7de91000	Deferred        libgnutls.so.26
ELF	7de91000-7deb5000	Deferred        libk5crypto.so.3
ELF	7deb5000-7df47000	Deferred        libkrb5.so.3
ELF	7df47000-7df71000	Deferred        libgssapi_krb5.so.2
ELF	7df71000-7dfa7000	Deferred        libcups.so.2
ELF	7dfa7000-7dfbc000	Deferred        midimap<elf>
  \-PE	7dfb0000-7dfbc000	\               midimap
ELF	7dfbc000-7dfe4000	Deferred        msacm32<elf>
  \-PE	7dfc0000-7dfe4000	\               msacm32
ELF	7dfe4000-7dffd000	Deferred        msacm32<elf>
  \-PE	7dff0000-7dffd000	\               msacm32
ELF	7dffd000-7e03a000	Deferred        wineoss<elf>
  \-PE	7e000000-7e03a000	\               wineoss
ELF	7e03a000-7e06e000	Deferred        liblcms.so.1
ELF	7e081000-7e09f000	Deferred        mscms<elf>
  \-PE	7e090000-7e09f000	\               mscms
ELF	7e09f000-7e0d6000	Deferred        winspool<elf>
  \-PE	7e0b0000-7e0d6000	\               winspool
ELF	7e0d6000-7e184000	Deferred        comdlg32<elf>
  \-PE	7e0e0000-7e184000	\               comdlg32
ELF	7e184000-7e198000	Deferred        msimg32<elf>
  \-PE	7e190000-7e198000	\               msimg32
ELF	7e198000-7e1c5000	Deferred        ws2_32<elf>
  \-PE	7e1a0000-7e1c5000	\               ws2_32
ELF	7e1c5000-7e22e000	Deferred        crypt32<elf>
  \-PE	7e1d0000-7e22e000	\               crypt32
ELF	7e22e000-7e2c2000	Deferred        winmm<elf>
  \-PE	7e240000-7e2c2000	\               winmm
ELF	7e30e000-7e341000	Deferred        uxtheme<elf>
  \-PE	7e310000-7e341000	\               uxtheme
ELF	7e341000-7e34a000	Deferred        libxcursor.so.1
ELF	7e34a000-7e34f000	Deferred        libxfixes.so.3
ELF	7e34f000-7e353000	Deferred        libxcomposite.so.1
ELF	7e353000-7e35a000	Deferred        libxrandr.so.2
ELF	7e35a000-7e364000	Deferred        libxrender.so.1
ELF	7e364000-7e367000	Deferred        libxinerama.so.1
ELF	7e367000-7e388000	Deferred        imm32<elf>
  \-PE	7e370000-7e388000	\               imm32
ELF	7e388000-7e38d000	Deferred        libxdmcp.so.6
ELF	7e38d000-7e3a6000	Deferred        libxcb.so.1
ELF	7e3a6000-7e495000	Deferred        libx11.so.6
ELF	7e495000-7e4a4000	Deferred        libxext.so.6
ELF	7e4a4000-7e4aa000	Deferred        libxxf86vm.so.1
ELF	7e4aa000-7e4c2000	Deferred        libice.so.6
ELF	7e4c4000-7e4c8000	Deferred        libkeyutils.so.1
ELF	7e4d1000-7e4d5000	Deferred        libcom_err.so.2
ELF	7e4d5000-7e570000	Deferred        winex11<elf>
  \-PE	7e4e0000-7e570000	\               winex11
ELF	7e570000-7e597000	Deferred        libexpat.so.1
ELF	7e597000-7e5c4000	Deferred        libfontconfig.so.1
ELF	7e5d7000-7e5ed000	Deferred        libz.so.1
ELF	7e5ed000-7e663000	Deferred        libfreetype.so.6
ELF	7e663000-7e678000	Deferred        lz32<elf>
  \-PE	7e670000-7e678000	\               lz32
ELF	7e678000-7e693000	Deferred        version<elf>
  \-PE	7e680000-7e693000	\               version
ELF	7e693000-7e739000	Deferred        oleaut32<elf>
  \-PE	7e6a0000-7e739000	\               oleaut32
ELF	7e739000-7e75b000	Deferred        cabinet<elf>
  \-PE	7e740000-7e75b000	\               cabinet
ELF	7e75b000-7e820000	Deferred        comctl32<elf>
  \-PE	7e760000-7e820000	\               comctl32
ELF	7e820000-7e934000	Deferred        shell32<elf>
  \-PE	7e830000-7e934000	\               shell32
ELF	7e934000-7e957000	Deferred        mpr<elf>
  \-PE	7e940000-7e957000	\               mpr
ELF	7e957000-7e9a7000	Deferred        wininet<elf>
  \-PE	7e960000-7e9a7000	\               wininet
ELF	7e9a7000-7ea02000	Deferred        shlwapi<elf>
  \-PE	7e9b0000-7ea02000	\               shlwapi
ELF	7ea02000-7ea16000	Deferred        libresolv.so.2
ELF	7ea16000-7ea35000	Deferred        iphlpapi<elf>
  \-PE	7ea20000-7ea35000	\               iphlpapi
ELF	7ea35000-7ea98000	Deferred        rpcrt4<elf>
  \-PE	7ea40000-7ea98000	\               rpcrt4
ELF	7ea98000-7eb3e000	Deferred        ole32<elf>
  \-PE	7eab0000-7eb3e000	\               ole32
ELF	7eb3e000-7eb7d000	Deferred        urlmon<elf>
  \-PE	7eb50000-7eb7d000	\               urlmon
ELF	7eb7d000-7ec28000	Deferred        msi<elf>
  \-PE	7eb90000-7ec28000	\               msi
ELF	7ec28000-7ec7b000	Deferred        advapi32<elf>
  \-PE	7ec30000-7ec7b000	\               advapi32
ELF	7ec7b000-7ed1a000	Deferred        gdi32<elf>
  \-PE	7ec90000-7ed1a000	\               gdi32
ELF	7ed1a000-7ee66000	Deferred        user32<elf>
  \-PE	7ed30000-7ee66000	\               user32
ELF	7ee66000-7ee72000	Deferred        libnss_files.so.2
ELF	7ee72000-7ee8b000	Deferred        libnsl.so.1
ELF	7ee8b000-7ee94000	Deferred        libnss_compat.so.2
ELF	7ee95000-7ee98000	Deferred        libxcb-xlib.so.0
ELF	7ee98000-7eea1000	Deferred        libsm.so.6
ELF	7efc7000-7efed000	Deferred        libm.so.6
ELF	7eff5000-7f000000	Deferred        libnss_nis.so.2
ELF	b7d40000-b7d43000	Deferred        libxau.so.6
ELF	b7d4a000-b7d4e000	Deferred        libdl.so.2
ELF	b7d4e000-b7eac000	Deferred        libc.so.6
ELF	b7ead000-b7ec6000	Deferred        libpthread.so.0
ELF	b7ed9000-b8010000	Deferred        libwine.so.1
ELF	b8012000-b802f000	Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
00000008 
	00000017    0
	00000009    0
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
00000018 (D) C:\windows\temp\AIRa7d.tmp\Adobe AIR Installer.exe
	0000001f   15
	0000001d    0
	0000001c    0
	00000019    0 <==
0000001a 
	0000001b    0
Backtrace:
=>1 0x05392a6b in webkit (+0x1b2a6b) (0x00000000)

```

---

### Post by binbash on 2009-01-17
I got your point but it is marked as garbage.So you cant do anything about that.However mame also does play that roms and there is [http://www.google.com/url?q=http://www.kaillera.com/](http://www.google.com/url?q=http://www.kaillera.com/) to play them online.I did not test this at linux, i am sure there is a way to play them online at linux.

---

### Post by tabithaboof on 2009-01-17
> **binbash said:**
> I got your point but it is marked as garbage.So you cant do anything about that.However mame also does play that roms and there is [http://www.google.com/url?q=http://www.kaillera.com/](http://www.google.com/url?q=http://www.kaillera.com/) to play them online.I did not test this at linux, i am sure there is a way to play them online at linux.

Thanks, for the link to Kaillera, its again good info but the online play (which is the only reason I am trying this) with Kaillera isnt really up to par. 

I do have a question though, based on what I have read, numerous people have managed to install the windows version of air to do this. I dont understand what being marked as garbage means specifically. Adobe air on windows has a platinum rating on winehq. Thanks for the continuing advice though,

---

