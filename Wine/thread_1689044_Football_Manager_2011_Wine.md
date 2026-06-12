---
title: "Football Manager 2011 Wine"
date: 2011-02-16
forum: Wine
---

### Post by Dmjthomas on 2011-02-16
Hi there, I used the guide in the following link to install football manager onto my netbook, following a small tweak to make my netbook display 1024x768 I managed to get the game up and running with no issues what so ever:

[http://appdb.winehq.org/objectManager.php?sClass=version&iId=21960](http://appdb.winehq.org/objectManager.php?sClass=version&iId=21960)

However, I have had to reinstall ubuntu onto my netbook (I decided that I didn't need my windows partition and did a clean install). As far as I'm aware I used the same Ubuntu install that was on my usb pen drive. I installed Play on linux and as a result wine was installed as part of this.

Again I followed the exact same procedure to install Football manager. However when I go to play it, it does not work at all with an error box popping up.

I have also installed Office 2007 onto my netbook. These are the only two Windows programs I was going to use. I did briefly have Itunes as I thought I needed to reset my IPod, however I uninstalled it as I managed to get it working with Banshee.

I have tried to run through the terminal and have attached the output from this.

Can someone help me? I think it may be a sequencing issue as before I installed Office after I installed Football manager. Could this be causing me my grief?

Ubuntu 10.04, Dell mini 10v
wine version 1.2.2

Terminal output:

[email]david@david-netbook:~/.wine[/email]/drive_c/Program Files/Sports Interactive/Football Manager 2011$ wine fm.exe
err:module:import_dll Library Wlanapi.dll (which is needed by L"C:\\Program Files\\Sports Interactive\\Football Manager 2011\\IntelLaptopGamingVista.dll") not found
err:ole:CoGetClassObject class {9a5ea990-3034-4d6f-9128-01f3c61022bc} not registered
err:ole:CoGetClassObject no class object {9a5ea990-3034-4d6f-9128-01f3c61022bc} could be created for context 0x1
fixme:wtsapi:WTSRegisterSessionNotification Stub 0x1006c 0x00000000
fixme:d3d_caps:select_card_intel_mesa Card selection not handled for Mesa Intel driver
fixme:d3d_caps:init_driver_info Unhandled vendor 8086.
fixme:win:EnumDisplayDevicesW ((null),0,0x315e1f4,0x00000000), stub!
fixme:wtsapi:WTSRegisterSessionNotification Stub 0x20072 0x00000000
fixme:d3d:context_check_fbo_status FBO status GL_FRAMEBUFFER_UNSUPPORTED (0x8cdd)
fixme:d3d:context_check_fbo_status 	Color attachment 0: (0x163008) WINED3DFMT_B8G8R8X8_UNORM 1024x753
fixme:d3d:context_check_fbo_status 	Depth attachment: (0x163170) WINED3DFMT_D24_UNORM_S8_UINT 1024x753
err:d3d:IWineD3DDeviceImpl_ClearSurface >>>>>>>>>>>>>>>>> GL_INVALID_FRAMEBUFFER_OPERATION (0x506) from glClear @ device.c / 4525
err:d3d:IWineD3DDeviceImpl_Reset Cannot change the back buffer count yet
wine: Unhandled page fault on read access to 0x00000018 at address 0x137ce22 (thread 001c), starting debugger...
Unhandled exception: page fault on read access to 0x00000018 in 32-bit code (0x0137ce22).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:0137ce22 ESP:0315e858 EBP:00000000 EFLAGS:00210212(  R- --  I   -A- - )
 EAX:00000000 EBX:02d00d90 ECX:7ecab244 EDX:00000000
 ESI:0315e960 EDI:02d00d90
Stack dump:
0x0315e858:  02d00d90 0315ea10 02d00b28 00000000
0x0315e868:  00000000 00000400 00000300 00000000
0x0315e878:  00000000 00000400 00000300 00000000
0x0315e888:  00000000 00000400 00000300 0137d835
0x0315e898:  0315e8b4 02d00d90 024aa454 02d00b28
0x0315e8a8:  00000000 02d007c0 0137e0e0 0315e960
Backtrace:
0x0137ce22: movl	0x18(%eax),%edi
Modules:
Module	Address			Debug info	Name (124 modules)
PE	  330000-  3ba000	Deferred        saaudit2005mt
PE	  400000- 2648000	Export          fm
PE	10000000-1041a000	Deferred        d3dx9_41
PE	3b400000-3b41f000	Deferred        steam_api
ELF	41000000-41140000	Deferred        libwine.so.1
ELF	41001000-41006000	Deferred        libgpg-error.so.0
ELF	41123000-41196000	Deferred        libgcrypt.so.11
ELF	41198000-411a9000	Deferred        libtasn1.so.3
ELF	411ab000-41246000	Deferred        libgnutls.so.26
ELF	41339000-4133d000	Deferred        libcom_err.so.2
ELF	41396000-413c5000	Deferred        libgssapi_krb5.so.2
ELF	413d0000-413d8000	Deferred        libkrb5support.so.0
ELF	413f9000-414aa000	Deferred        libkrb5.so.3
ELF	414ac000-414b0000	Deferred        libkeyutils.so.1
ELF	414dd000-41501000	Deferred        libk5crypto.so.3
ELF	4e127000-4e144000	Deferred        ld-linux.so.2
ELF	4e146000-4e151000	Deferred        libdrm.so.2
ELF	4e153000-4e159000	Deferred        libxxf86vm.so.1
ELF	4e15e000-4e168000	Deferred        libdrm_intel.so.1
ELF	4e1b2000-4e217000	Deferred        libgl.so.1
ELF	4e1b2000-4e217000	Deferred        libgl.so.1
ELF	4e224000-4e235000	Deferred        libavahi-client.so.3
ELF	4e237000-4e27e000	Deferred        libcups.so.2
ELF	4e237000-4e27e000	Deferred        libcups.so.2
ELF	4f08e000-4f1e8000	Deferred        libc.so.6
ELF	4f1ea000-4f1ee000	Deferred        libdl.so.2
ELF	4f1f0000-4f209000	Deferred        libpthread.so.0
ELF	4f20b000-4f214000	Deferred        librt.so.1
ELF	4f216000-4f23c000	Deferred        libm.so.6
ELF	4f23e000-4f253000	Deferred        libz.so.1
ELF	4f371000-4f375000	Deferred        libxau.so.6
ELF	4f377000-4f391000	Deferred        libxcb.so.1
ELF	4f393000-4f399000	Deferred        libxdmcp.so.6
ELF	4f39b000-4f4b8000	Deferred        libx11.so.6
ELF	4f4c2000-4f4fb000	Deferred        libdbus-1.so.3
ELF	4f4fd000-4f511000	Deferred        libresolv.so.2
ELF	4f55b000-4f56b000	Deferred        libxext.so.6
ELF	4f60d000-4f634000	Deferred        libexpat.so.1
ELF	4f656000-4f6cc000	Deferred        libfreetype.so.6
ELF	4f6de000-4f6e3000	Deferred        libuuid.so.1
ELF	4f70c000-4f73c000	Deferred        libfontconfig.so.1
ELF	4f73e000-4f742000	Deferred        libxdamage.so.1
ELF	4f744000-4f74e000	Deferred        libxrender.so.1
ELF	4f750000-4f756000	Deferred        libxfixes.so.3
ELF	4f7fd000-4f807000	Deferred        libxcursor.so.1
ELF	4f809000-4f80d000	Deferred        libxcomposite.so.1
ELF	4f80f000-4f817000	Deferred        libxrandr.so.2
ELF	4f89f000-4f8a3000	Deferred        libxinerama.so.1
ELF	4fe59000-4fe62000	Deferred        libsm.so.6
ELF	4fe64000-4fe7d000	Deferred        libice.so.6
PE	70bd0000-70c34000	Deferred        shlwapi
ELF	7b800000-7b97d000	Deferred        kernel32<elf>
  \-PE	7b810000-7b97d000	\               kernel32
ELF	7bc00000-7bcb9000	Deferred        ntdll<elf>
  \-PE	7bc10000-7bcb9000	\               ntdll
ELF	7bf00000-7bf04000	Deferred        <wine-loader>
ELF	7d989000-7d9bd000	Deferred        uxtheme<elf>
  \-PE	7d990000-7d9bd000	\               uxtheme
ELF	7de83000-7df26000	Deferred        winex11<elf>
  \-PE	7de90000-7df26000	\               winex11
ELF	7e040000-7e0fe000	Deferred        comdlg32<elf>
  \-PE	7e050000-7e0fe000	\               comdlg32
ELF	7e0fe000-7e1e7000	Deferred        oleaut32<elf>
  \-PE	7e120000-7e1e7000	\               oleaut32
ELF	7e1e7000-7e286000	Deferred        crypt32<elf>
  \-PE	7e1f0000-7e286000	\               crypt32
ELF	7e286000-7e371000	Deferred        comctl32<elf>
  \-PE	7e290000-7e371000	\               comctl32
ELF	7e371000-7e54b000	Deferred        shell32<elf>
  \-PE	7e380000-7e54b000	\               shell32
ELF	7e54b000-7e570000	Deferred        mpr<elf>
  \-PE	7e550000-7e570000	\               mpr
ELF	7e585000-7e5e1000	Deferred        wininet<elf>
  \-PE	7e590000-7e5e1000	\               wininet
ELF	7e5e1000-7e5f5000	Deferred        lz32<elf>
  \-PE	7e5f0000-7e5f5000	\               lz32
ELF	7e5f5000-7e60e000	Deferred        version<elf>
  \-PE	7e600000-7e60e000	\               version
ELF	7e60e000-7e646000	Deferred        winspool<elf>
  \-PE	7e620000-7e646000	\               winspool
ELF	7e646000-7e6a5000	Deferred        setupapi<elf>
  \-PE	7e650000-7e6a5000	\               setupapi
ELF	7e6ca000-7e6eb000	Deferred        iphlpapi<elf>
  \-PE	7e6d0000-7e6eb000	\               iphlpapi
ELF	7e6eb000-7e760000	Deferred        rpcrt4<elf>
  \-PE	7e700000-7e760000	\               rpcrt4
ELF	7e760000-7e860000	Deferred        ole32<elf>
  \-PE	7e780000-7e860000	\               ole32
ELF	7e860000-7e8f5000	Deferred        winmm<elf>
  \-PE	7e870000-7e8f5000	\               winmm
ELF	7e8f5000-7e93d000	Deferred        dsound<elf>
  \-PE	7e900000-7e93d000	\               dsound
ELF	7e93d000-7e953000	Deferred        psapi<elf>
  \-PE	7e940000-7e953000	\               psapi
ELF	7e953000-7e9ab000	Deferred        dbghelp<elf>
  \-PE	7e960000-7e9ab000	\               dbghelp
ELF	7e9ab000-7e9c1000	Deferred        wtsapi32<elf>
  \-PE	7e9b0000-7e9c1000	\               wtsapi32
ELF	7e9c1000-7e9ee000	Deferred        ws2_32<elf>
  \-PE	7e9d0000-7e9ee000	\               ws2_32
ELF	7e9ee000-7ea10000	Deferred        imm32<elf>
  \-PE	7e9f0000-7ea10000	\               imm32
ELF	7ea10000-7ea25000	Deferred        faultrep<elf>
  \-PE	7ea20000-7ea25000	\               faultrep
ELF	7ea25000-7ea42000	Deferred        pdh<elf>
  \-PE	7ea30000-7ea42000	\               pdh
ELF	7ea42000-7eb74000	Deferred        user32<elf>
  \-PE	7ea50000-7eb74000	\               user32
ELF	7eb74000-7ecac000	Deferred        wined3d<elf>
  \-PE	7eb80000-7ecac000	\               wined3d
ELF	7ecac000-7ece0000	Deferred        d3d9<elf>
  \-PE	7ecb0000-7ece0000	\               d3d9
ELF	7ece0000-7ed3b000	Deferred        advapi32<elf>
  \-PE	7ecf0000-7ed3b000	\               advapi32
ELF	7ed3b000-7edc7000	Deferred        gdi32<elf>
  \-PE	7ed50000-7edc7000	\               gdi32
ELF	7edc7000-7ee49000	Deferred        msvcrt<elf>
  \-PE	7ede0000-7ee49000	\               msvcrt
ELF	7efa6000-7efb2000	Deferred        libnss_files.so.2
ELF	7eff6000-7f000000	Deferred        libnss_nis.so.2
ELF	b71eb000-b7488000	Deferred        i915_dri.so
ELF	b7519000-b752f000	Deferred        powrprof<elf>
  \-PE	b7520000-b752f000	\               powrprof
ELF	b7535000-b753d000	Deferred        libnss_compat.so.2
Threads:
process  tid      prio (all id:s are in hex)
00000008 (D) C:\Program Files\Sports Interactive\Football Manager 2011\fm.exe
	0000001c    0 <==
	0000001b    0
	00000009    0
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

---

### Post by Dmjthomas on 2011-02-18
I tried running office programmes and they weren't loading either. I think Winetricks has caused some errors.

I think I'm going to have to uninstall all of wine and go through the process again.

---

### Post by de_island on 2011-04-12
The one thing I'm missing since recently moving over to Linux is Football Manager.

I've been looking through forums and other sites, and I can't seem to find anything of any major use.

Hopefully Playonlinux will get a working version before too long.

---

### Post by neelan.nair on 2011-04-21
I've been missing it for a long time :(
What about Mac versions of FM2011? Will they be compatible considering they're Unix based?

---

### Post by Maestrofix on 2011-09-15
i manage to install it on mint 11.. but cant start it. so my q. is how i unstall it again_`*?? i just tried linux for the first time. so hope some can help me unstall it.

---

