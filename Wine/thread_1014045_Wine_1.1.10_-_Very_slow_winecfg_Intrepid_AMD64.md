---
title: "Wine 1.1.10 - Very slow winecfg Intrepid AMD64"
date: 2008-12-17
forum: Wine
---

### Post by goughs on 2008-12-17
Apologies if this has been posted about previously, I am having extreme problems with wine being slow to respond to any commands.  For instance, running winecfg from the terminal, I have wait several seconds before I get an output (a very strange output, I may add) in the Terminal window, and before the Config tool actually pops up on screen.

The same is true when running any of the scripts contained within winetricks, I press enter, and the terminal sits for a silly amount of time, before it responds.  The system in general usage is perfectly fine.  I have tried removing wine from synaptic, and deleting the .wine folder from home, and re-installing to no avail, can anyone shed any light?

I attach the terminal output from the first run of winecfg (any run thereafter produces no output, but is still horribly slow to load).

```

gough@gough-pc:~$ winecfg
wine: created the configuration directory '/home/gough/.wine'
fixme:system:SetProcessDPIAware stub!
fixme:iphlpapi:NotifyAddrChange (Handle 0x7cdda9f8, overlapped 0x7cdda9dc): stub
fixme:shell:DllCanUnloadNow stub
wine: Unhandled page fault on write access to 0x3a931508 at address 0x7cc77cb6 (thread 000b), starting debugger...
Unhandled exception: page fault on write access to 0x3a931508 in 32-bit code (0x7cc77cb6).
Register dump:
 CS:0023 SS:002b DS:002b ES:002b FS:0063 GS:006b
 EIP:7cc77cb6 ESP:0033ce78 EBP:00000008 EFLAGS:00010246(   - 00      -RIZP1)
 EAX:00000018 EBX:f7c9b6b0 ECX:7ccca4e0 EDX:3a931508
 ESI:f7c9b6b0 EDI:00001a02
Stack dump:
0x0033ce78:  00000000 7cc7f154 00000004 00000000
0x0033ce88:  00000001 01fbd62c 00001a02 00000001
0x0033ce98:  fff83cd8 7cc7f6a6 f7c9b6b0 00001a02
0x0033cea8:  00000001 00000000 0c389000 7cc0aff4
0x0033ceb8:  0033cec8 7cbe52bd 7cc0aff4 7d867048
0x0033cec8:  f7dde49b f7f82ff4 7d866dd8 00000000
Backtrace:
=>1 0x7cc77cb6 in libgl.so.1 (+0x65cb6) (0x00000008)
  2 0x00000000 (0x00000000)
0x7cc77cb6: movl	$0x7cca8000,0x0(%edx)
Modules:
Module	Address			Debug info	Name (195 modules)
PE	  450000-  457000	Deferred        plc4
PE	  460000-  466000	Deferred        plds4
PE	  8f0000-  959000	Deferred        xpcom_core
PE	  960000-  987000	Deferred        nspr4
PE	  990000-  99a000	Deferred        nsprefm
PE	  9a0000-  9b4000	Deferred        xpcom_compat
PE	  9c0000-  9c7000	Deferred        xmlextras
PE	  9d0000-  a05000	Deferred        xpc3250
PE	  a10000-  a81000	Deferred        js3250
PE	  a90000-  a98000	Deferred        pippki
PE	  aa0000-  ace000	Deferred        i18n
PE	  ad0000-  adf000	Deferred        jsd3250
PE	  ae0000-  aed000	Deferred        jar50
PE	  af0000-  b01000	Deferred        mozz
PE	  b10000-  b1f000	Deferred        caps
PE	  b20000-  b33000	Deferred        wallet
PE	  b40000-  b4a000	Deferred        necko2
PE	  b50000-  b5c000	Deferred        oji
PE	  b60000-  b73000	Deferred        jsj3250
PE	  b80000-  b87000	Deferred        imgicon
PE	  b90000-  bc9000	Deferred        gkparser
PE	  bd0000-  bf4000	Deferred        gkplugin
PE	  c00000-  c1b000	Deferred        rdf
PE	  c20000-  c26000	Deferred        wlltvwrs
PE	  c30000-  c36000	Deferred        mozfind
PE	  c40000-  c49000	Deferred        cookie
PE	  c50000-  c5e000	Deferred        spellchk
PE	  c60000-  ca6000	Deferred        websrvcs
PE	  cb0000-  cd5000	Deferred        gkwidget
PE	  ce0000-  cf6000	Deferred        gkgfx
PE	  d00000-  d1a000	Deferred        mork
PE	  d20000-  d2e000	Deferred        webbrwsr
PE	  d30000-  d37000	Deferred        xpcom_compat_c
PE	  d40000-  d47000	Deferred        ucvmath
PE	  d50000-  d77000	Deferred        xpinstal
PE	  d80000-  d9a000	Deferred        universalchardet
PE	  da0000-  dd8000	Deferred        pipnss
PE	  de0000-  dfa000	Deferred        smime3
PE	  e00000-  e5b000	Deferred        nss3
PE	  e60000-  e9f000	Deferred        softokn3
PE	  ea0000-  ec0000	Deferred        ssl3
PE	  ec0000-  ec8000	Deferred        autoconfig
PE	  ed0000-  edc000	Deferred        xppref32
PE	  ee0000-  f9e000	Deferred        uconv
PE	  fa0000- 1239000	Deferred        gklayout
PE	 1240000- 124b000	Deferred        intlcmpt
PE	 1250000- 1260000	Deferred        chrome
PE	 1260000- 126e000	Deferred        composer
PE	 1270000- 127c000	Deferred        typeaheadfind
PE	 1280000- 12e4000	Deferred        editor
PE	 12f0000- 12fa000	Deferred        myspell
PE	 1300000- 131f000	Deferred        embedcomponents
PE	 1320000- 1359000	Deferred        strgcmps
PE	 1360000- 1370000	Deferred        appshell
PE	 1370000- 13a8000	Deferred        appcomps
PE	 13b0000- 13b7000	Deferred        sroaming
PE	 13c0000- 13c7000	Deferred        auth
PE	 13d0000- 13f4000	Deferred        gkgfxwin
PE	 1400000- 1427000	Deferred        imglib2
PE	 1430000- 14ad000	Deferred        necko
PE	 14b0000- 14e1000	Deferred        transformiix
PE	 14f0000- 14f7000	Deferred        txmgr
PE	 1500000- 150f000	Deferred        profile
PE	 1510000- 1518000	Deferred        pipboot
PE	 1520000- 154c000	Deferred        docshell
PE	 1550000- 1568000	Deferred        srchsvc
PE	 1570000- 1576000	Deferred        mozctlx
PE	 1e00000- 1e31000	Deferred        freebl3
PE	 1e40000- 1e7e000	Deferred        nssckbi
PE	 1e80000- 1e86000	Deferred        xpistub
PE	10000000-10006000	Deferred        xpcom
ELF	7a998000-7b800000	Deferred        libglcore.so.1
ELF	7b800000-7b940000	Deferred        kernel32<elf>
  \-PE	7b820000-7b940000	\               kernel32
ELF	7bc00000-7bcac000	Deferred        ntdll<elf>
  \-PE	7bc10000-7bcac000	\               ntdll
ELF	7bf00000-7bf04000	Deferred        <wine-loader>
ELF	7cc12000-7cccb000	Export          libgl.so.1
ELF	7cfed000-7d056000	Deferred        libgcrypt.so.11
ELF	7d056000-7d088000	Deferred        libcrypt.so.1
ELF	7d088000-7d125000	Deferred        libgnutls.so.26
ELF	7d125000-7d149000	Deferred        libk5crypto.so.3
ELF	7d149000-7d1db000	Deferred        libkrb5.so.3
ELF	7d1db000-7d205000	Deferred        libgssapi_krb5.so.2
ELF	7d205000-7d23b000	Deferred        libcups.so.2
ELF	7d23b000-7d2e9000	Deferred        comdlg32<elf>
  \-PE	7d240000-7d2e9000	\               comdlg32
ELF	7d3fa000-7d466000	Deferred        msvcrt<elf>
  \-PE	7d410000-7d466000	\               msvcrt
ELF	7d466000-7d591000	Deferred        shell32<elf>
  \-PE	7d480000-7d591000	\               shell32
ELF	7d591000-7d5b0000	Deferred        advpack<elf>
  \-PE	7d5a0000-7d5b0000	\               advpack
ELF	7d5b5000-7d5c7000	Deferred        libtasn1.so.3
ELF	7d5c7000-7d5fe000	Deferred        winspool<elf>
  \-PE	7d5d0000-7d5fe000	\               winspool
ELF	7d5fe000-7d62b000	Deferred        ws2_32<elf>
  \-PE	7d610000-7d62b000	\               ws2_32
ELF	7d62b000-7d646000	Deferred        wsock32<elf>
  \-PE	7d630000-7d646000	\               wsock32
ELF	7d707000-7d778000	Deferred        libglu.so.1
ELF	7d778000-7d78f000	Deferred        glu32<elf>
ELF	7d78f000-7d7ec000	Deferred        shlwapi<elf>
  \-PE	7d7a0000-7d7ec000	\               shlwapi
ELF	7d8ac000-7d8bb000	Deferred        libgcc_s.so.1
ELF	7e0d9000-7e10c000	Deferred        uxtheme<elf>
  \-PE	7e0e0000-7e10c000	\               uxtheme
ELF	7e10c000-7e1d3000	Deferred        comctl32<elf>
  \-PE	7e120000-7e1d3000	\               comctl32
ELF	7e1d3000-7e1fd000	Deferred        msvfw32<elf>
  \-PE	7e1e0000-7e1fd000	\               msvfw32
ELF	7e1fd000-7e249000	Deferred        dsound<elf>
  \-PE	7e200000-7e249000	\               dsound
ELF	7e249000-7e2bb000	Deferred        quartz<elf>
  \-PE	7e250000-7e2bb000	\               quartz
ELF	7e2bb000-7e2d0000	Deferred        midimap<elf>
  \-PE	7e2c0000-7e2d0000	\               midimap
ELF	7e2d0000-7e320000	Deferred        libpulse.so.0
ELF	7e320000-7e3e8000	Deferred        libasound.so.2
ELF	7e3e8000-7e4f9000	Deferred        ole32<elf>
  \-PE	7e400000-7e4f9000	\               ole32
ELF	7e52c000-7e530000	Deferred        libgpg-error.so.0
ELF	7e530000-7e549000	Deferred        msacm32<elf>
  \-PE	7e540000-7e549000	\               msacm32
ELF	7e549000-7e54d000	Deferred        libcap.so.1
ELF	7e54d000-7e565000	Deferred        libice.so.6
ELF	7e565000-7e56e000	Deferred        libsm.so.6
ELF	7e56f000-7e578000	Deferred        libkrb5support.so.0
ELF	7e581000-7e5b8000	Deferred        winealsa<elf>
  \-PE	7e590000-7e5b8000	\               winealsa
ELF	7e5b9000-7e5bd000	Deferred        libkeyutils.so.1
ELF	7e5bd000-7e6a9000	Deferred        oleaut32<elf>
  \-PE	7e5d0000-7e6a9000	\               oleaut32
ELF	7e6a9000-7e73d000	Deferred        winmm<elf>
  \-PE	7e6b0000-7e73d000	\               winmm
ELF	7e73d000-7e766000	Deferred        msacm32<elf>
  \-PE	7e740000-7e766000	\               msacm32
ELF	7e767000-7e769000	Deferred        libnvidia-tls.so.1
ELF	7e769000-7e76d000	Deferred        libcom_err.so.2
ELF	7e76d000-7e782000	Deferred        avicap32<elf>
  \-PE	7e770000-7e782000	\               avicap32
ELF	7e782000-7e7a3000	Deferred        devenum<elf>
  \-PE	7e790000-7e7a3000	\               devenum
ELF	7e7a3000-7e7ac000	Deferred        libxcursor.so.1
ELF	7e7ac000-7e7b1000	Deferred        libxfixes.so.3
ELF	7e7b1000-7e7b5000	Deferred        libxcomposite.so.1
ELF	7e7b5000-7e7bc000	Deferred        libxrandr.so.2
ELF	7e7bc000-7e7c6000	Deferred        libxrender.so.1
ELF	7e7c6000-7e7cc000	Deferred        libxxf86vm.so.1
ELF	7e7cc000-7e7ed000	Deferred        imm32<elf>
  \-PE	7e7d0000-7e7ed000	\               imm32
ELF	7e7ed000-7e806000	Deferred        libxcb.so.1
ELF	7e806000-7e8f5000	Deferred        libx11.so.6
ELF	7e8f5000-7e904000	Deferred        libxext.so.6
ELF	7e904000-7e9a0000	Deferred        winex11<elf>
  \-PE	7e910000-7e9a0000	\               winex11
ELF	7e9e9000-7ea10000	Deferred        libexpat.so.1
ELF	7ea10000-7ea3d000	Deferred        libfontconfig.so.1
ELF	7ea50000-7ea66000	Deferred        libz.so.1
ELF	7ea66000-7eadc000	Deferred        libfreetype.so.6
ELF	7eadc000-7eaf0000	Deferred        libresolv.so.2
ELF	7eaf0000-7eb10000	Deferred        iphlpapi<elf>
  \-PE	7eb00000-7eb10000	\               iphlpapi
ELF	7eb10000-7eb77000	Deferred        rpcrt4<elf>
  \-PE	7eb20000-7eb77000	\               rpcrt4
ELF	7eb77000-7eb8c000	Deferred        lz32<elf>
  \-PE	7eb80000-7eb8c000	\               lz32
ELF	7eb8c000-7eba7000	Deferred        version<elf>
  \-PE	7eb90000-7eba7000	\               version
ELF	7eba7000-7ec47000	Deferred        gdi32<elf>
  \-PE	7ebc0000-7ec47000	\               gdi32
ELF	7ec47000-7ed95000	Deferred        user32<elf>
  \-PE	7ec60000-7ed95000	\               user32
ELF	7ed95000-7edff000	Deferred        setupapi<elf>
  \-PE	7eda0000-7edff000	\               setupapi
ELF	7edff000-7ee54000	Deferred        advapi32<elf>
  \-PE	7ee10000-7ee54000	\               advapi32
ELF	7ee54000-7ee72000	Deferred        wineboot<elf>
  \-PE	7ee60000-7ee72000	\               wineboot
ELF	7ee72000-7ee8b000	Deferred        libnsl.so.1
ELF	7ee8b000-7ee94000	Deferred        libnss_compat.so.2
ELF	7ee96000-7ee9d000	Deferred        libasound_module_pcm_pulse.so
ELF	7ee9d000-7eea6000	Deferred        librt.so.1
ELF	7efc7000-7efed000	Deferred        libm.so.6
ELF	7efef000-7eff4000	Deferred        libxdmcp.so.6
ELF	7eff4000-7f000000	Deferred        libnss_files.so.2
ELF	f7c90000-f7c9b000	Deferred        libnss_nis.so.2
ELF	f7c9c000-f7ca0000	Deferred        libdl.so.2
ELF	f7ca0000-f7dfe000	Deferred        libc.so.6
ELF	f7dff000-f7e18000	Deferred        libpthread.so.0
ELF	f7e18000-f7e1b000	Deferred        libxinerama.so.1
ELF	f7e1b000-f7e1e000	Deferred        libxcb-xlib.so.0
ELF	f7e1e000-f7e21000	Deferred        libxau.so.6
ELF	f7e2b000-f7f62000	Deferred        libwine.so.1
ELF	f7f64000-f7f84000	Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
00000008 
	00000009    0
0000000a (D) C:\windows\system32\wineboot.exe
	00000015    0
	00000014    0
	00000013    0
	0000000b    0 <==
0000000c 
	00000019    0
	0000000e    0
	0000000d    0
0000000f 
	00000010    0
Backtrace:
=>1 0x7cc77cb6 in libgl.so.1 (+0x65cb6) (0x00000008)
  2 0x00000000 (0x00000000)


```

---

### Post by hotweiss on 2009-01-12
Same problem here! I also got the libgl.so.1 error when I was installing my Nvidia driver...

PS-I'm using wine 1.1.12

---

### Post by hotweiss on 2009-01-12
I've created a bug report, vote for it:

[http://bugs.winehq.org/show_bug.cgi?id=16910](http://bugs.winehq.org/show_bug.cgi?id=16910)

---

