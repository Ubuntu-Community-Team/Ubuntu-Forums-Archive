---
title: "Dreamweaver CS3 crashes when using WYSIWYG"
date: 2009-07-19
forum: Wine
---

### Post by DeadMetal on 2009-07-19
Hi,

A year ago I completely switched to Ubuntu. I only kept using Windows for Dreamweaver CS3. Later I started using Virtualbox for that and now I switched to Wine.

Via Wine everything works fine, but almost every I switch to the WYSIWYG-view Dreamweaver will crash. Is anyone familiar with this or willing to help me to find a solution?

I you want me to run some commands so you can see debugging information, that's fine.

---

### Post by DeadMetal on 2009-07-19
It just happened again while working in the WYSIWYG mode.

The terminal output is as follows:

```

wine: Unhandled page fault on read access to 0xbb9eb008 at address 0x594915a (thread 002c), starting debugger...
Unhandled exception: page fault on read access to 0xbb9eb008 in 32-bit code (0x0594915a).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:0594915a ESP:0032ecd0 EBP:00001001 EFLAGS:00210286(  R- --  I S - -P- )
 EAX:00000001 EBX:04d06608 ECX:00000000 EDX:bb9eb000
 ESI:05bb9000 EDI:bb9eb000
Stack dump:
0x0032ecd0:  04d06298 05bb9000 0032ede0 04d06608
0x0032ece0:  00000000 05aec000 04d06608 00000002
0x0032ecf0:  00000000 00000001 00000000 00000001
0x0032ed00:  05949408 05bb9000 00000001 00000002
0x0032ed10:  05946472 00000008 00000003 00000004
0x0032ed20:  00000004 00000001 05946521 00000004
Backtrace:
=>0 0x0594915a in authplay (+0x1d915a) (0x00001001)
  1 0x00000000 (0x00000000)
0x0594915a: movl	0x8(%edx),%ecx
Modules:
Module	Address			Debug info	Name (183 modules)
PE	  330000-  37a000	Deferred        bib
PE	  380000-  451000	Deferred        libeay32
PE	  460000-  487000	Deferred        ssleay32
PE	  490000-  49c000	Deferred        ahclient
PE	  720000-  757000	Deferred        adobe_caps
PE	  760000-  7c1000	Deferred        adobe_epic
PE	  800000- 17be000	Deferred        dreamweaver
PE	 17c0000- 23ca000	Deferred        adobepsl
PE	 3590000- 35e9000	Deferred        adobe_eula
PE	 3700000- 375a000	Deferred        adobe_personalization
PE	 3870000- 3ae6000	Deferred        adobelm_libfnp
PE	 42f0000- 436a000	Deferred        jsbridge
PE	 5770000- 5adf000	Export          authplay
PE	10000000-10756000	Deferred        fireworks library
PE	12000000-121ca000	Deferred        xerces-c_2_6
PE	30000000-30023000	Deferred        libcurl
PE	30100000-30124000	Deferred        coretypes
PE	30200000-3022c000	Deferred        dwfile
PE	30700000-30731000	Deferred        mm
PE	30800000-30842000	Deferred        mmnotes
PE	30900000-30912000	Deferred        netio
PE	30b00000-30b31000	Deferred        netioftp
PE	30e00000-31037000	Deferred        resources
PE	31400000-31430000	Deferred        swffile
PE	31500000-3153a000	Deferred        tsl
PE	32100000-3216c000	Deferred        workspace
PE	4a800000-4a893000	Deferred        icuuc30
PE	4ad00000-4b52d000	Deferred        icudt30
PE	5d360000-5d36e000	Deferred        mfc80enu
PE	70d00000-70ea0000	Deferred        gdiplus
PE	78130000-781cb000	Deferred        msvcr80
PE	782e0000-783ed000	Deferred        mfc80u
ELF	792a2000-79307000	Deferred        winedos<elf>
  \-PE	792b0000-79307000	\               winedos
ELF	7b800000-7b962000	Deferred        kernel32<elf>
  \-PE	7b820000-7b962000	\               kernel32
ELF	7b97a000-7b98f000	Deferred        schannel<elf>
  \-PE	7b980000-7b98f000	\               schannel
ELF	7ba77000-7bb00000	Deferred        crypt32<elf>
  \-PE	7ba80000-7bb00000	\               crypt32
ELF	7bc00000-7bcb1000	Deferred        ntdll<elf>
  \-PE	7bc10000-7bcb1000	\               ntdll
ELF	7bcb6000-7bce1000	Deferred        secur32<elf>
  \-PE	7bcc0000-7bce1000	\               secur32
ELF	7bce1000-7bcf0000	Deferred        libgcc_s.so.1
ELF	7bf00000-7bf04000	Deferred        <wine-loader>
ELF	7bf08000-7bf0f000	Deferred        libnss_dns.so.2
ELF	7bf0f000-7bf12000	Deferred        libnss_mdns4_minimal.so.2
ELF	7bf16000-7bf50000	Deferred        rsaenh<elf>
  \-PE	7bf20000-7bf50000	\               rsaenh
ELF	7bf50000-7bfc0000	Deferred        setupapi<elf>
  \-PE	7bf60000-7bfc0000	\               setupapi
ELF	7bfc0000-7bfd7000	Deferred        snmpapi<elf>
  \-PE	7bfd0000-7bfd7000	\               snmpapi
ELF	7bfd7000-7c000000	Deferred        oledlg<elf>
  \-PE	7bfe0000-7c000000	\               oledlg
ELF	7c011000-7c0a3000	Deferred        libkrb5.so.3
ELF	7c0a3000-7c140000	Deferred        libgnutls.so.26
PE	7c340000-7c396000	Deferred        msvcr71
ELF	7c3a0000-7c3b7000	Deferred        oleacc<elf>
  \-PE	7c3b0000-7c3b7000	\               oleacc
ELF	7c3b7000-7c420000	Deferred        libgcrypt.so.11
PE	7c420000-7c4a7000	Deferred        msvcp80
ELF	7c4a8000-7c4cc000	Deferred        mlang<elf>
  \-PE	7c4b0000-7c4cc000	\               mlang
ELF	7c4cc000-7c4d0000	Deferred        libgpg-error.so.0
ELF	7c4d0000-7c4f4000	Deferred        libk5crypto.so.3
ELF	7c4f4000-7c51f000	Deferred        libgssapi_krb5.so.2
ELF	7c51f000-7c556000	Deferred        libcups.so.2
ELF	7c597000-7c5a9000	Deferred        libtasn1.so.3
ELF	7c5a9000-7c5c2000	Deferred        spoolss<elf>
  \-PE	7c5b0000-7c5c2000	\               spoolss
ELF	7c5c2000-7c5e0000	Deferred        localspl<elf>
  \-PE	7c5d0000-7c5e0000	\               localspl
ELF	7cc8f000-7cc93000	Deferred        libkeyutils.so.1
ELF	7cc93000-7cc9c000	Deferred        libkrb5support.so.0
ELF	7cc9c000-7cca0000	Deferred        libcom_err.so.2
ELF	7ccf5000-7cd0a000	Deferred        midimap<elf>
  \-PE	7cd00000-7cd0a000	\               midimap
ELF	7cd0a000-7cd30000	Deferred        msacm32<elf>
  \-PE	7cd10000-7cd30000	\               msacm32
ELF	7cd30000-7cd48000	Deferred        msacm32<elf>
  \-PE	7cd40000-7cd48000	\               msacm32
ELF	7cd48000-7cd4e000	Deferred        libattr.so.1
ELF	7cd4e000-7cd55000	Deferred        libgdbm.so.3
ELF	7cd55000-7cdb4000	Deferred        libpulse.so.0
ELF	7cdc4000-7cdcd000	Deferred        librt.so.1
ELF	7cdcd000-7ce95000	Deferred        libasound.so.2
ELF	7ce99000-7ce9e000	Deferred        libcap.so.2
ELF	7ce9e000-7cea5000	Deferred        libasound_module_pcm_pulse.so
ELF	7cea5000-7cedc000	Deferred        winealsa<elf>
  \-PE	7ceb0000-7cedc000	\               winealsa
ELF	7cf2a000-7cf5d000	Deferred        uxtheme<elf>
  \-PE	7cf30000-7cf5d000	\               uxtheme
ELF	7cf5d000-7cf66000	Deferred        libxcursor.so.1
ELF	7cf66000-7cf6b000	Deferred        libxfixes.so.3
ELF	7cf6b000-7cf6f000	Deferred        libxcomposite.so.1
ELF	7cf6f000-7cf79000	Deferred        libxrender.so.1
ELF	7cf79000-7cf7f000	Deferred        libxxf86vm.so.1
ELF	7cf8f000-7d02c000	Deferred        winex11<elf>
  \-PE	7cfa0000-7d02c000	\               winex11
ELF	7d07b000-7d0a2000	Deferred        libexpat.so.1
ELF	7d0a2000-7d0cf000	Deferred        libfontconfig.so.1
ELF	7d0cf000-7d146000	Deferred        libfreetype.so.6
ELF	7d146000-7d16d000	Deferred        netapi32<elf>
  \-PE	7d150000-7d16d000	\               netapi32
ELF	7d16d000-7d193000	Deferred        odbc32<elf>
  \-PE	7d170000-7d193000	\               odbc32
ELF	7d193000-7d245000	Deferred        comdlg32<elf>
  \-PE	7d1a0000-7d245000	\               comdlg32
ELF	7d245000-7d25b000	Deferred        libresolv.so.2
ELF	7d25c000-7d264000	Deferred        libxrandr.so.2
ELF	7d26b000-7d28b000	Deferred        iphlpapi<elf>
  \-PE	7d270000-7d28b000	\               iphlpapi
ELF	7d28b000-7d2b9000	Deferred        ws2_32<elf>
  \-PE	7d290000-7d2b9000	\               ws2_32
ELF	7d2b9000-7d2d4000	Deferred        wsock32<elf>
  \-PE	7d2c0000-7d2d4000	\               wsock32
ELF	7d2d4000-7d3bc000	Deferred        oleaut32<elf>
  \-PE	7d2f0000-7d3bc000	\               oleaut32
ELF	7d3bc000-7d3f2000	Deferred        winspool<elf>
  \-PE	7d3c0000-7d3f2000	\               winspool
ELF	7d3f2000-7d3f7000	Deferred        libxdmcp.so.6
ELF	7d3f7000-7e30f000	Deferred        libglcore.so.1
ELF	7e30f000-7e329000	Deferred        libxcb.so.1
ELF	7e329000-7e32d000	Deferred        libxau.so.6
ELF	7e32d000-7e3e7000	Deferred        libgl.so.1
ELF	7e3e7000-7e4d6000	Deferred        libx11.so.6
ELF	7e4d6000-7e4e6000	Deferred        libxext.so.6
ELF	7e4e6000-7e4fe000	Deferred        libice.so.6
ELF	7e4fe000-7e507000	Deferred        libsm.so.6
ELF	7e507000-7e59f000	Deferred        opengl32<elf>
  \-PE	7e520000-7e59f000	\               opengl32
ELF	7e59f000-7e5b3000	Deferred        msimg32<elf>
  \-PE	7e5a0000-7e5b3000	\               msimg32
ELF	7e5b3000-7e622000	Deferred        msvcrt<elf>
  \-PE	7e5c0000-7e622000	\               msvcrt
ELF	7e622000-7e6be000	Deferred        winmm<elf>
  \-PE	7e630000-7e6be000	\               winmm
ELF	7e6be000-7e786000	Deferred        comctl32<elf>
  \-PE	7e6d0000-7e786000	\               comctl32
ELF	7e786000-7e914000	Deferred        shell32<elf>
  \-PE	7e7a0000-7e914000	\               shell32
ELF	7e914000-7e972000	Deferred        shlwapi<elf>
  \-PE	7e920000-7e972000	\               shlwapi
ELF	7e972000-7e995000	Deferred        mpr<elf>
  \-PE	7e980000-7e995000	\               mpr
ELF	7e995000-7e9ab000	Deferred        libz.so.1
ELF	7e9ab000-7e9ae000	Deferred        libxinerama.so.1
ELF	7e9bb000-7ea0e000	Deferred        wininet<elf>
  \-PE	7e9c0000-7ea0e000	\               wininet
ELF	7ea0e000-7ea2f000	Deferred        imm32<elf>
  \-PE	7ea10000-7ea2f000	\               imm32
ELF	7ea2f000-7ea43000	Deferred        lz32<elf>
  \-PE	7ea30000-7ea43000	\               lz32
ELF	7ea43000-7ea5e000	Deferred        version<elf>
  \-PE	7ea50000-7ea5e000	\               version
ELF	7ea5e000-7eacb000	Deferred        rpcrt4<elf>
  \-PE	7ea70000-7eacb000	\               rpcrt4
ELF	7eacb000-7ebc7000	Deferred        ole32<elf>
  \-PE	7eae0000-7ebc7000	\               ole32
ELF	7ebc7000-7ebdd000	Deferred        psapi<elf>
  \-PE	7ebd0000-7ebdd000	\               psapi
ELF	7ebdd000-7ec2c000	Deferred        dbghelp<elf>
  \-PE	7ebf0000-7ec2c000	\               dbghelp
ELF	7ec2c000-7ec82000	Deferred        advapi32<elf>
  \-PE	7ec40000-7ec82000	\               advapi32
ELF	7ec82000-7ed24000	Deferred        gdi32<elf>
  \-PE	7ec90000-7ed24000	\               gdi32
ELF	7ed24000-7ee70000	Deferred        user32<elf>
  \-PE	7ed40000-7ee70000	\               user32
ELF	7ef9a000-7efa6000	Deferred        libnss_files.so.2
ELF	7efa6000-7efb1000	Deferred        libnss_nis.so.2
ELF	7efb1000-7efca000	Deferred        libnsl.so.1
ELF	7efca000-7eff0000	Deferred        libm.so.6
ELF	7eff2000-7eff7000	Deferred        libuuid.so.1
ELF	7eff7000-7f000000	Deferred        libnss_compat.so.2
ELF	b7cb0000-b7cb2000	Deferred        libnvidia-tls.so.1
ELF	b7cb4000-b7cb8000	Deferred        libdl.so.2
ELF	b7cb8000-b7e1b000	Deferred        libc.so.6
ELF	b7e1c000-b7e35000	Deferred        libpthread.so.0
ELF	b7e45000-b7f81000	Deferred        libwine.so.1
ELF	b7f83000-b7fa1000	Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
0000000e 
	00000014    0
	00000010    0
	0000000f    0
00000011 
	00000017    0
	00000016    0
	00000013    0
	00000012    0
0000002b (D) C:\Program Files\Adobe\Adobe Dreamweaver CS3\Dreamweaver.exe
	00000047    0
	0000003a   15
	00000039    0
	00000038    0
	00000030    0
	0000002f    0
	0000002c    0 <==
0000002d 
	0000002e    0
Backtrace:
=>0 0x0594915a in authplay (+0x1d915a) (0x00001001)
  1 0x00000000 (0x00000000)
err:commctrl:COMCTL32_SubclassProc Our sub classing stack got erased for 0x602a0!! Nothing we can do

```

---

### Post by DeadMetal on 2009-07-23
Anyone?

---

