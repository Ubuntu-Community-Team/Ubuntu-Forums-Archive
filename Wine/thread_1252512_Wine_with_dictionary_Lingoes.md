---
title: "Wine with dictionary Lingoes"
date: 2009-08-28
forum: Wine
---

### Post by luckymancvp on 2009-08-28
Please tell me how to run dictionary Lingoes with wine .
I see somewhere , lingoes can run .
[http://cdndalat.edu.vn/Di%E1%BB%85n%C4%91%C3%A0n/tabid/56/forumid/5/postid/748/scope/posts/Default.aspx]("http://cdndalat.edu.vn/Di%E1%BB%85n%C4%91%C3%A0n/tabid/56/forumid/5/postid/748/scope/posts/Default.aspx")
This is error when I run it. 

```

err:ntdll:NtQueryInformationToken Unhandled Token Information class 18!
fixme:mountmgr:harddisk_ioctl unsupported ioctl 74080
fixme:mountmgr:harddisk_ioctl unsupported ioctl 2d1400
fixme:mountmgr:harddisk_ioctl unsupported ioctl 74080
fixme:font:WineEngAddFontResourceEx Ignoring flags 10
fixme:shdocvw:PersistStreamInit_InitNew (0x14a960)
fixme:shdocvw:WebBrowser_put_RegisterAsDropTarget (0x14a960)->(0)
fixme:shdocvw:navigate_url Unsupported args (Flags 0x32cb3c:3; TargetFrameName 0x32cb2c:8)
fixme:urlmon:URLMonikerImpl_BindToObject use running object table
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:iphlpapi:NotifyAddrChange (Handle 0x7d01a9b4, overlapped 0x7d01a998): stub
fixme:system:SetProcessDPIAware stub!
fixme:msimtf:CActiveIMM_Create ((nil) {08c0e040-62d1-11d1-9326-0060b067b86e} 0x19fef34)
fixme:ole:CoCreateInstance no instance created for interface {08c0e040-62d1-11d1-9326-0060b067b86e} of class {4955dd33-b159-11d0-8fcf-00aa006bcc59}, hres is 0x80004002
fixme:shdocvw:ClOleCommandTarget_QueryStatus (0x14a9fc)->((null) 1 0x32bed4 (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x14a9fc)->((null) 25 2 0x32bee8 (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x14a9fc)->((null) 26 2 0x32bee8 (nil))
fixme:shdocvw:ClientSite_GetContainer (0x14a9fc)->(0x32bf24)
fixme:shdocvw:ClOleCommandTarget_Exec (0x14a9fc)->({000214d1-0000-0000-c000-000000000046} 37 0 0x32bff8 (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x14a9fc)->({000214d1-0000-0000-c000-000000000046} 84 0 (nil) 0x32c088)
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
wine: Unhandled page fault on write access to 0x00000000 at address 0x10064 (thread 0009), starting debugger...
Unhandled exception: page fault on write access to 0x00000000 in 32-bit code (0x00010064).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:00010064 ESP:0032cb24 EBP:008b9968 EFLAGS:00210246(   - 00      -RIZP1)
 EAX:00000000 EBX:005acaa8 ECX:00000009 EDX:0014c324
 ESI:00000001 EDI:00000000
Stack dump:
0x0032cb24:  000000f1 00000000 00000000 00000000
0x0032cb34:  00000000 0032cb68 0045d551 005acaa8
0x0032cb44:  00000000 00d990a8 0045d5a8 005acaa8
0x0032cb54:  00d99108 00d990a8 00430dac 005acaa8
0x0032cb64:  005aaa84 ffffffff 00d990a8 00430c36
0x0032cb74:  00000001 0001005c 00000000 0032dce4
Backtrace:
=>1 0x00010064 (0x008b9968)
  2 0x008100e8 (0x005759dc)
  3 0x004dff50 in lingoes (+0xdff50) (0x004df6e0)
0x00010064: addb	%al,0x0(%eax)
Modules:
Module	Address			Debug info	Name (166 modules)
PE	  400000-  6f4000	Export          lingoes
PE	  f60000-  f66000	Deferred        xpcom
PE	  f70000-  fd9000	Deferred        xpcom_core
PE	  fe0000- 1007000	Deferred        nspr4
PE	 1010000- 1017000	Deferred        plc4
PE	 1020000- 1026000	Deferred        plds4
PE	 1030000- 103f000	Deferred        jsd3250
PE	 1040000- 10b1000	Deferred        js3250
PE	 10c0000- 10f5000	Deferred        xpc3250
PE	 1100000- 115b000	Deferred        nss3
PE	 1160000- 119f000	Deferred        softokn3
PE	 11a0000- 11c0000	Deferred        ssl3
PE	 11c0000- 11d1000	Deferred        mozz
PE	 11e0000- 11fa000	Deferred        smime3
PE	 1200000- 1216000	Deferred        gkgfx
PE	 1220000- 1226000	Deferred        mozctlx
PE	 1230000- 1244000	Deferred        xpcom_compat
PE	 1250000- 1256000	Deferred        xpistub
PE	 1260000- 129e000	Deferred        nssckbi
PE	 12a0000- 12b3000	Deferred        jsj3250
PE	 12c0000- 12f1000	Deferred        freebl3
PE	 1300000- 137d000	Deferred        necko
PE	 1380000- 138c000	Deferred        xppref32
PE	 1390000- 13be000	Deferred        i18n
PE	 13c0000- 13df000	Deferred        embedcomponents
PE	 13e0000- 13ef000	Deferred        caps
PE	 13f0000- 13fc000	Deferred        typeaheadfind
PE	 1400000- 1699000	Deferred        gklayout
PE	 16a0000- 16c7000	Deferred        imglib2
PE	 16d0000- 16eb000	Deferred        rdf
PE	 16f0000- 1728000	Deferred        appcomps
PE	 1730000- 1740000	Deferred        appshell
PE	 1740000- 174f000	Deferred        profile
PE	 1750000- 1757000	Deferred        xpcom_compat_c
PE	 1760000- 1767000	Deferred        sroaming
PE	 1770000- 1780000	Deferred        chrome
PE	 1780000- 17b9000	Deferred        gkparser
PE	 17c0000- 187e000	Deferred        uconv
PE	 1880000- 18ac000	Deferred        docshell
PE	 18b0000- 18ba000	Deferred        nsprefm
PE	 19d0000- 19de000	Deferred        webbrwsr
PE	 19e0000- 1a05000	Deferred        gkwidget
PE	 1a10000- 1a34000	Deferred        gkgfxwin
PE	 1a40000- 1a48000	Deferred        pipboot
PE	 1a50000- 1a5c000	Deferred        oji
PE	 1a60000- 1a6d000	Deferred        jar50
PE	 1a70000- 1a8a000	Deferred        mork
PE	10000000-10046000	Deferred        lgui64u
PE	5f800000-5f8f2000	Deferred        mfc42u
PE	75ff0000-76051000	Deferred        msvcp60
PE	78000000-78044000	Deferred        msvcrt
ELF	7b800000-7b93d000	Deferred        kernel32<elf>
  \-PE	7b820000-7b93d000	\               kernel32
ELF	7bc00000-7bca7000	Deferred        ntdll<elf>
  \-PE	7bc10000-7bca7000	\               ntdll
ELF	7bf00000-7bf04000	Deferred        <wine-loader>
ELF	7cb5e000-7cbc1000	Deferred        winedos<elf>
  \-PE	7cb70000-7cbc1000	\               winedos
ELF	7cde3000-7cdfa000	Deferred        msimtf<elf>
  \-PE	7cdf0000-7cdfa000	\               msimtf
ELF	7d23e000-7d253000	Deferred        lz32<elf>
  \-PE	7d240000-7d253000	\               lz32
ELF	7d253000-7d26e000	Deferred        version<elf>
  \-PE	7d260000-7d26e000	\               version
ELF	7d26e000-7d289000	Deferred        wsock32<elf>
  \-PE	7d270000-7d289000	\               wsock32
ELF	7d289000-7d32a000	Deferred        mshtml<elf>
  \-PE	7d290000-7d32a000	\               mshtml
ELF	7d32a000-7d37a000	Deferred        wininet<elf>
  \-PE	7d330000-7d37a000	\               wininet
ELF	7d37a000-7d3b9000	Deferred        urlmon<elf>
  \-PE	7d380000-7d3b9000	\               urlmon
ELF	7d3b9000-7d3f5000	Deferred        shdocvw<elf>
  \-PE	7d3c0000-7d3f5000	\               shdocvw
ELF	7d5cb000-7d5ee000	Deferred        mpr<elf>
  \-PE	7d5d0000-7d5ee000	\               mpr
ELF	7d623000-7d638000	Deferred        midimap<elf>
  \-PE	7d630000-7d638000	\               midimap
ELF	7d638000-7d660000	Deferred        msacm32<elf>
  \-PE	7d640000-7d660000	\               msacm32
ELF	7d660000-7d679000	Deferred        msacm32<elf>
  \-PE	7d670000-7d679000	\               msacm32
ELF	7de7a000-7de80000	Deferred        libattr.so.1
ELF	7de80000-7de87000	Deferred        libgdbm.so.3
ELF	7de87000-7dee6000	Deferred        libpulse.so.0
ELF	7def7000-7df00000	Deferred        librt.so.1
ELF	7df00000-7dfc8000	Deferred        libasound.so.2
ELF	7dfc8000-7dfff000	Deferred        winealsa<elf>
  \-PE	7dfd0000-7dfff000	\               winealsa
ELF	7dfff000-7e003000	Deferred        libgpg-error.so.0
ELF	7e003000-7e06c000	Deferred        libgcrypt.so.11
ELF	7e06c000-7e090000	Deferred        libk5crypto.so.3
ELF	7e090000-7e122000	Deferred        libkrb5.so.3
ELF	7e122000-7e1bf000	Deferred        libgnutls.so.26
ELF	7e1bf000-7e1ea000	Deferred        libgssapi_krb5.so.2
ELF	7e227000-7e239000	Deferred        libtasn1.so.3
ELF	7e239000-7e23d000	Deferred        libkeyutils.so.1
ELF	7e23d000-7e246000	Deferred        libkrb5support.so.0
ELF	7e246000-7e27d000	Deferred        libcups.so.2
ELF	7e282000-7e287000	Deferred        libcap.so.2
ELF	7e287000-7e28e000	Deferred        libasound_module_pcm_pulse.so
ELF	7e2b2000-7e2e5000	Deferred        uxtheme<elf>
  \-PE	7e2c0000-7e2e5000	\               uxtheme
ELF	7e30d000-7e316000	Deferred        libxcursor.so.1
ELF	7e316000-7e31b000	Deferred        libxfixes.so.3
ELF	7e31b000-7e31f000	Deferred        libxcomposite.so.1
ELF	7e31f000-7e327000	Deferred        libxrandr.so.2
ELF	7e327000-7e331000	Deferred        libxrender.so.1
ELF	7e331000-7e334000	Deferred        libxinerama.so.1
ELF	7e334000-7e355000	Deferred        imm32<elf>
  \-PE	7e340000-7e355000	\               imm32
ELF	7e355000-7e35a000	Deferred        libxdmcp.so.6
ELF	7e35a000-7e374000	Deferred        libxcb.so.1
ELF	7e374000-7e378000	Deferred        libxau.so.6
ELF	7e378000-7e37d000	Deferred        libuuid.so.1
ELF	7e37d000-7e46c000	Deferred        libx11.so.6
ELF	7e46c000-7e47c000	Deferred        libxext.so.6
ELF	7e47c000-7e482000	Deferred        libxxf86vm.so.1
ELF	7e482000-7e49a000	Deferred        libice.so.6
ELF	7e49a000-7e4a3000	Deferred        libsm.so.6
ELF	7e4ae000-7e4b2000	Deferred        libcom_err.so.2
ELF	7e4b4000-7e54f000	Deferred        winex11<elf>
  \-PE	7e4c0000-7e54f000	\               winex11
ELF	7e580000-7e5a7000	Deferred        libexpat.so.1
ELF	7e5a7000-7e5d4000	Deferred        libfontconfig.so.1
ELF	7e5d4000-7e5ea000	Deferred        libz.so.1
ELF	7e5ea000-7e661000	Deferred        libfreetype.so.6
ELF	7e661000-7e68e000	Deferred        ws2_32<elf>
  \-PE	7e670000-7e68e000	\               ws2_32
ELF	7e68e000-7e722000	Deferred        winmm<elf>
  \-PE	7e6a0000-7e722000	\               winmm
ELF	7e722000-7e7c8000	Deferred        oleaut32<elf>
  \-PE	7e730000-7e7c8000	\               oleaut32
ELF	7e7c8000-7e7de000	Deferred        libresolv.so.2
ELF	7e7ef000-7e80e000	Deferred        iphlpapi<elf>
  \-PE	7e800000-7e80e000	\               iphlpapi
ELF	7e80e000-7e871000	Deferred        rpcrt4<elf>
  \-PE	7e820000-7e871000	\               rpcrt4
ELF	7e871000-7e917000	Deferred        ole32<elf>
  \-PE	7e880000-7e917000	\               ole32
ELF	7e917000-7e94e000	Deferred        winspool<elf>
  \-PE	7e920000-7e94e000	\               winspool
ELF	7e94e000-7e9a9000	Deferred        shlwapi<elf>
  \-PE	7e960000-7e9a9000	\               shlwapi
ELF	7e9a9000-7eabd000	Deferred        shell32<elf>
  \-PE	7e9c0000-7eabd000	\               shell32
ELF	7eabd000-7eb6b000	Deferred        comdlg32<elf>
  \-PE	7eac0000-7eb6b000	\               comdlg32
ELF	7eb6b000-7ec30000	Deferred        comctl32<elf>
  \-PE	7eb70000-7ec30000	\               comctl32
ELF	7ec30000-7ed7c000	Deferred        user32<elf>
  \-PE	7ec50000-7ed7c000	\               user32
ELF	7ed7c000-7edcf000	Deferred        advapi32<elf>
  \-PE	7ed90000-7edcf000	\               advapi32
ELF	7edcf000-7ee6f000	Deferred        gdi32<elf>
  \-PE	7ede0000-7ee6f000	\               gdi32
ELF	7ef99000-7efa5000	Deferred        libnss_files.so.2
ELF	7efa5000-7efb0000	Deferred        libnss_nis.so.2
ELF	7efb0000-7efc9000	Deferred        libnsl.so.1
ELF	7efc9000-7efef000	Deferred        libm.so.6
ELF	b7da4000-b7dad000	Deferred        libnss_compat.so.2
ELF	b7dae000-b7db2000	Deferred        libdl.so.2
ELF	b7db2000-b7f15000	Deferred        libc.so.6
ELF	b7f16000-b7f2f000	Deferred        libpthread.so.0
ELF	b7f40000-b8077000	Deferred        libwine.so.1
ELF	b8079000-b8097000	Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
00000008 (D) Z:\media\GT\Study\Dictionary\Lingoes\lingoes_portable_2.6.2\Lingoes.exe
	0000001e    0
	0000001d    0
	0000001c    0
	0000001b    0
	0000001a    0
	00000019    0
	00000018    0
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
=>1 0x00010064 (0x008b9968)
  2 0x008100e8 (0x005759dc)
  3 0x004dff50 in lingoes (+0xdff50) (0x004df6e0)


```

---

### Post by luckymancvp on 2009-08-29
Please help me, I really need to tranlate book

---

### Post by luckymancvp on 2009-08-29
Please help me

---

### Post by ackanao on 2009-08-29
Hi, luckymancvp

I've just tested it and it seems to work but it depends on IE6 and vcrun6 libraries - this will wreak havoc on your default wineprefix so it's a good idea to create new wineprefix just for Lingoes. 

Here's the instructions for installing Lingoes:

1. Create Lingoes wineprefix:
```
WINEPREFIX=~/Desktop/Lingoes wineboot
```
*this will create Lingoes wineprefix on your Desktop - choose another path if you want*

2. Download winetricks:
```
wget http://www.kegel.com/wine/winetricks
```

3. Use winetricks to install vcrun6 and ie6:
```
WINEPREFIX=~/Desktop/Lingoes sh winetricks vcrun6 ie6
```

4. Install Lingoes:
```
env WINEPREFIX=~/Desktop/Lingoes wine /path/to/Lingoes/Installer/lingoes_2.6.2.exe
```

5. Run Lingoes:
```
env WINEPREFIX=~/Desktop/Lingoes wine "C:\Program Files\Lingoes\Translator2\Lingoes.exe"
```

There's an Lingoes entry on WineHQ AppDB and it's rated as "Gold", here's the link:
[http://appdb.winehq.org/objectManager.php?sClass=version&iId=17469]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=17469")

I've tested it with Wine 1.1.28 and it seems to work fairly well.

---

### Post by luckymancvp on 2009-08-30
Thanks you so much.

I don't install IE 6 .

---

### Post by ackanao on 2009-08-31
I'm glad I was able to help but I didn't understand your last post - did you manage to make Lingoes work or not?

You don't have to worry about anything as long as you use different wineprefix to install Lingoes and IE. Just follow my instructions and everything will be OK. 

Just a side note: There are far more better Dictionary/Translator tools available for Linux than Lingoes - just search this forum or ask for help and I'm sure you'll find them (I can't help you that much because I rarely use them).

---

### Post by serbring on 2010-01-11
i have correctly installed lingoes, but it doesn't work properly, because from a pdf reader, it doesn't capture word on screen when i active the mode. as   pdf reader i use windows version of foxit reader lanched with wine.

---

