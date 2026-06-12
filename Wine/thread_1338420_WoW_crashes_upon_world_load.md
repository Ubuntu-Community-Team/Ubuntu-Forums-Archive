---
title: "WoW crashes upon world load"
date: 2009-11-26
forum: Wine
---

### Post by bethebunny on 2009-11-26
My WoW client crashes 3-5 seconds after loading any world environment, even without moving.

I've tried every troubleshooting suggestion on WoWWiki, the Ubuntu community documentation for WoW, and AppDB.
(
[http://www.wowwiki.com/World_of_Warcraft_functionality_on_Wine](http://www.wowwiki.com/World_of_Warcraft_functionality_on_Wine)
[https://help.ubuntu.com/community/WorldofWarcraft/Troubleshooting](https://help.ubuntu.com/community/WorldofWarcraft/Troubleshooting)
[http://www.wowwiki.com/Wine_miscellaneous_info](http://www.wowwiki.com/Wine_miscellaneous_info)
[http://www.wowwiki.com/Wine_troubleshooting](http://www.wowwiki.com/Wine_troubleshooting)
[http://appdb.winehq.org/objectManager.php?sClass=version&iId=14154](http://appdb.winehq.org/objectManager.php?sClass=version&iId=14154)
[http://www.phoronix.com/forums/showthread.php?t=12778](http://www.phoronix.com/forums/showthread.php?t=12778)
)

System info:
Lenovo Thinkpad T60
2.0 GHz Intel Dual Core
3GBi Ram
Ubuntu 9.10 Karmic (Upgrade from 9.04 base install)

```

~$ uname -a
Linux hazel 2.6.31-14-generic #48-Ubuntu SMP Fri Oct 16 14:05:01 UTC 2009 x86_64 GNU/Linux
~$ wine --version
wine-1.1.33
~$ lspci | grep VGA
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility X1400
~$ sudo lshw -C video
  *-display UNCLAIMED     
       description: VGA compatible controller
       product: Radeon Mobility X1400
       vendor: ATI Technologies Inc
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: pm pciexpress msi bus_master cap_list
       configuration: latency=0
       resources: memory:d8000000-dfffffff(prefetchable) ioport:2000(size=256) memory:ee100000-ee10ffff memory:ee120000-ee13ffff(prefetchable)

```

winecfg:

Tried several OS compatabilities (98, 2000, XP, 7)
Tried various audio settings (ALSA had been throwing errors, so switched to OSS), including both hardware accelerated and emulated audio.
Tried each with and without a virtual desktop.
All other settings are defaults.


Wine error report:

```

~/.wine/drive_c/Program Files/World of Warcraft$ wine Wow.exe
fixme:advapi:SetSecurityInfo stub
archive Data\enUS\patch-enUS.MPQ opened
archive Data\patch.MPQ opened
archive Data\enUS\patch-enUS-2.MPQ opened
archive Data\patch-2.MPQ opened
archive Data\expansion.MPQ opened
archive Data\lichking.MPQ opened
archive Data\common.MPQ opened
archive Data\common-2.MPQ opened
archive Data\enUS\locale-enUS.MPQ opened
archive Data\enUS\speech-enUS.MPQ opened
archive Data\enUS\expansion-locale-enUS.MPQ opened
archive Data\enUS\lichking-locale-enUS.MPQ opened
archive Data\enUS\expansion-speech-enUS.MPQ opened
archive Data\enUS\lichking-speech-enUS.MPQ opened
fixme:win:EnumDisplayDevicesW ((null),0,0x39ed30,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x39ea44,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x39f374,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x39f50c,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x39f508,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x39f4fc,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x39f0c4,0x00000000), stub!
err:heap:HEAP_GetPtr Invalid heap 0x7df498c4!
err:heap:HEAP_GetPtr Invalid heap 0x7df498c4!
fixme:win:EnumDisplayDevicesW ((null),0,0x39de70,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x39de98,0x00000000), stub!
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (5000): STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT 5000
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (5000): STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT 5000
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (5000): STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT 5000
fixme:reg:GetNativeSystemInfo (0x37404364) using GetSystemInfo()
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONTEXT_VALUE; STUB
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONTEXT_VALUE; STUB
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONTEXT_VALUE; STUB
fixme:win:EnumDisplayDevicesW ((null),0,0x39da38,0x00000000), stub!
wine: Unhandled page fault on read access to 0x00000000 at address (nil) (thread 0009), starting debugger...
Unhandled exception: page fault on read access to 0x00000000 in 32-bit code (0x00000000).
Register dump:
 CS:0023 SS:002b DS:002b ES:002b FS:0063 GS:006b
 EIP:00000000 ESP:0039fc10 EBP:0039fc70 EFLAGS:00010246(  R- --  I  Z- -P- )
 EAX:000083f1 EBX:00002000 ECX:00000de1 EDX:09f93e38
 ESI:00000000 EDI:0d1f6d78
Stack dump:
0x0039fc10:  0061f493 00000de1 00000000 000083f1
0x0039fc20:  00000080 00000080 00000000 00002000
0x0039fc30:  09f93e38 00000080 0d1f6d78 00000080
0x0039fc40:  00000000 00000000 00000080 00000080
0x0039fc50:  00606913 00000008 00000000 00000100
0x0039fc60:  09f95e38 00002000 09f93e38 000083f1
Backtrace:
=>0 0x00000000 (0x0039fc70)
  1 0x0061f6a8 in wow (+0x21f6a8) (0x0039fcc8)
  2 0x0061f752 in wow (+0x21f752) (0x0039fcd8)
  3 0x006058ac in wow (+0x2058ac) (0x0039fce4)
  4 0x00603004 in wow (+0x203004) (0x0039fd08)
  5 0x0048a51f in wow (+0x8a51f) (0x0039fd44)
  6 0x00427069 in wow (+0x27069) (0x0039fd74)
  7 0x0042421c in wow (+0x2421c) (0x0039fda0)
  8 0x004256ea in wow (+0x256ea) (0x0039fdf4)
  9 0x00425731 in wow (+0x25731) (0x0039fe0c)
  10 0x00406d9d in wow (+0x6d9d) (0x0039fea8)
  11 0x7b877c04 in kernel32 (+0x57c04) (0x0039fee8)
  12 0x7bc6cee4 call_thread_func+0xc() in ntdll (0x0039fef8)
  13 0x7bc6d0f0 call_thread_entry_point+0x70() in ntdll (0x0039ffc8)
  14 0x7bc48ffa in ntdll (+0x38ffa) (0x0039ffe8)
  15 0xf769dedd wine_call_on_stack+0x1d() in libwine.so.1 (0x00000000)
0x00000000: addb	%al,0x0(%eax)
Modules:
Module	Address			Debug info	Name (124 modules)
PE	  400000- 17aa000	Export          wow
PE	10000000-10069000	Deferred        divxdecoder
PE	3c910000-3c984000	Deferred        battle.net
PE	78130000-781cb000	Deferred        msvcr80
ELF	7b800000-7b972000	Export          kernel32<elf>
  \-PE	7b820000-7b972000	\               kernel32
ELF	7bc00000-7bcb2000	Export          ntdll<elf>
  \-PE	7bc10000-7bcb2000	\               ntdll
ELF	7bf00000-7bf04000	Deferred        <wine-loader>
ELF	7db31000-7db9f000	Deferred        msvcrt<elf>
  \-PE	7db40000-7db9f000	\               msvcrt
ELF	7db9f000-7dba6000	Deferred        libnss_dns.so.2
ELF	7dbc3000-7dbe1000	Deferred        libgcc_s.so.1
ELF	7dbe1000-7dc2e000	Deferred        dsound<elf>
  \-PE	7dbf0000-7dc2e000	\               dsound
ELF	7dc2e000-7dc33000	Deferred        libgpg-error.so.0
ELF	7dc33000-7dc6c000	Deferred        libdbus-1.so.3
ELF	7dc6c000-7dce8000	Deferred        libgcrypt.so.11
ELF	7dce8000-7dcfa000	Deferred        libtasn1.so.3
ELF	7dcfa000-7dd0e000	Deferred        libresolv.so.2
ELF	7dd0e000-7dd12000	Deferred        libkeyutils.so.1
ELF	7dd12000-7dd1b000	Deferred        libkrb5support.so.0
ELF	7dd1b000-7dd46000	Deferred        libk5crypto.so.3
ELF	7dd46000-7ddf8000	Deferred        libkrb5.so.3
ELF	7ddf8000-7de09000	Deferred        libavahi-client.so.3
ELF	7de09000-7de15000	Deferred        libavahi-common.so.3
ELF	7de15000-7debd000	Deferred        libgnutls.so.26
ELF	7debd000-7deea000	Deferred        libgssapi_krb5.so.2
ELF	7deea000-7df2f000	Deferred        libcups.so.2
ELF	7df48000-7df4c000	Deferred        libnss_mdns4_minimal.so.2
ELF	7df4c000-7df65000	Deferred        spoolss<elf>
  \-PE	7df50000-7df65000	\               spoolss
ELF	7df65000-7df85000	Deferred        localspl<elf>
  \-PE	7df70000-7df85000	\               localspl
ELF	7df85000-7df9b000	Deferred        midimap<elf>
  \-PE	7df90000-7df9b000	\               midimap
ELF	7df9b000-7dfb3000	Deferred        msacm32<elf>
  \-PE	7dfa0000-7dfb3000	\               msacm32
ELF	7dfb3000-7dff1000	Deferred        wineoss<elf>
  \-PE	7dfc0000-7dff1000	\               wineoss
ELF	7e032000-7e065000	Deferred        uxtheme<elf>
  \-PE	7e040000-7e065000	\               uxtheme
ELF	7e065000-7e070000	Deferred        libxcursor.so.1
ELF	7e070000-7e074000	Deferred        libxcomposite.so.1
ELF	7e074000-7e07d000	Deferred        libxrandr.so.2
ELF	7e07d000-7e087000	Deferred        libxrender.so.1
ELF	7e087000-7e08a000	Deferred        libxinerama.so.1
ELF	7e08b000-7e08f000	Deferred        libcom_err.so.2
ELF	7e0a7000-7e146000	Deferred        winex11<elf>
  \-PE	7e0c0000-7e146000	\               winex11
ELF	7e1b8000-7e1df000	Deferred        libexpat.so.1
ELF	7e1df000-7e20c000	Deferred        libfontconfig.so.1
ELF	7e20c000-7e28b000	Deferred        libfreetype.so.6
ELF	7e2a8000-7e2bd000	Deferred        system.drv16.so
PE	7e2b0000-7e2bd000	Deferred        system.drv16
ELF	7e2bd000-7e2d2000	Deferred        hid<elf>
  \-PE	7e2c0000-7e2d2000	\               hid
ELF	7e2d2000-7e306000	Deferred        winspool<elf>
  \-PE	7e2e0000-7e306000	\               winspool
ELF	7e306000-7e35d000	Deferred        setupapi<elf>
  \-PE	7e310000-7e35d000	\               setupapi
ELF	7e35d000-7e383000	Deferred        msacm32<elf>
  \-PE	7e360000-7e383000	\               msacm32
ELF	7e383000-7e40a000	Deferred        winmm<elf>
  \-PE	7e390000-7e40a000	\               winmm
ELF	7e40a000-7e477000	Deferred        rpcrt4<elf>
  \-PE	7e420000-7e477000	\               rpcrt4
ELF	7e477000-7e572000	Deferred        ole32<elf>
  \-PE	7e490000-7e572000	\               ole32
ELF	7e572000-7e5ab000	Deferred        dinput<elf>
  \-PE	7e580000-7e5ab000	\               dinput
ELF	7e5ab000-7e5d5000	Deferred        ws2_32<elf>
  \-PE	7e5b0000-7e5d5000	\               ws2_32
ELF	7e5d5000-7e6a3000	Deferred        comctl32<elf>
  \-PE	7e5e0000-7e6a3000	\               comctl32
ELF	7e6a3000-7e833000	Deferred        shell32<elf>
  \-PE	7e6b0000-7e833000	\               shell32
ELF	7e833000-7e890000	Deferred        shlwapi<elf>
  \-PE	7e840000-7e890000	\               shlwapi
ELF	7e890000-7e8b3000	Deferred        mpr<elf>
  \-PE	7e8a0000-7e8b3000	\               mpr
ELF	7e8b3000-7e8c9000	Deferred        libz.so.1
ELF	7e8cc000-7e8e6000	Deferred        dinput8<elf>
  \-PE	7e8d0000-7e8e6000	\               dinput8
ELF	7e8e6000-7e93d000	Deferred        wininet<elf>
  \-PE	7e8f0000-7e93d000	\               wininet
ELF	7e93d000-7e95e000	Deferred        imm32<elf>
  \-PE	7e940000-7e95e000	\               imm32
ELF	7e95e000-7e972000	Deferred        lz32<elf>
  \-PE	7e960000-7e972000	\               lz32
ELF	7e972000-7e9cb000	Deferred        advapi32<elf>
  \-PE	7e980000-7e9cb000	\               advapi32
ELF	7e9cb000-7ea6b000	Deferred        gdi32<elf>
  \-PE	7e9e0000-7ea6b000	\               gdi32
ELF	7ea6b000-7ebb3000	Deferred        user32<elf>
  \-PE	7ea80000-7ebb3000	\               user32
ELF	7ebb3000-7ebbc000	Deferred        librt.so.1
ELF	7ebbc000-7ebc1000	Deferred        libxdmcp.so.6
ELF	7ebc1000-7ebcb000	Deferred        libdrm.so.2
ELF	7ebcb000-7ebd1000	Deferred        libxfixes.so.3
ELF	7ebd1000-7ebd7000	Deferred        libxxf86vm.so.1
ELF	7ebd7000-7ebf5000	Deferred        libxcb.so.1
ELF	7ebf5000-7ebf9000	Deferred        libxau.so.6
ELF	7ebf9000-7ec5d000	Deferred        libgl.so.1
ELF	7ec5d000-7ed8c000	Deferred        libx11.so.6
ELF	7ed8c000-7ed9c000	Deferred        libxext.so.6
ELF	7ed9c000-7edb7000	Deferred        libice.so.6
ELF	7edb7000-7edc0000	Deferred        libsm.so.6
ELF	7edc0000-7ee5b000	Deferred        opengl32<elf>
  \-PE	7ede0000-7ee5b000	\               opengl32
ELF	7ef87000-7ef93000	Deferred        libnss_files.so.2
ELF	7ef93000-7ef9e000	Deferred        libnss_nis.so.2
ELF	7ef9e000-7efb5000	Deferred        libnsl.so.1
ELF	7efb5000-7efbd000	Deferred        libnss_compat.so.2
ELF	7efbd000-7efe3000	Deferred        libm.so.6
ELF	7efe6000-7f000000	Deferred        version<elf>
  \-PE	7eff0000-7f000000	\               version
ELF	f7511000-f7516000	Deferred        libuuid.so.1
ELF	f7517000-f751b000	Deferred        libdl.so.2
ELF	f751b000-f765f000	Deferred        libc.so.6
ELF	f7660000-f7679000	Deferred        libpthread.so.0
ELF	f7679000-f767c000	Deferred        libxdamage.so.1
ELF	f7696000-f77d1000	Export          libwine.so.1
ELF	f77d3000-f77f1000	Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
00000008 (D) C:\Program Files\World of Warcraft\Wow.exe
	0000002b    0
	0000002a    0
	00000029    0
	00000028    0
	00000027    0
	00000026    0
	00000025    0
	00000024    2
	00000023   15
	00000022   15
	00000021    2
	00000020   15
	0000001e   15
	0000001c    0
	0000001b    0
	0000001a    0
	00000009    0 <==
0000000e 
	00000015    0
	00000014    0
	00000010    0
	0000000f    0
00000011 
	00000017    0
	00000016    0
	00000013    0
	00000012    0
00000018 
	00000019    0
Backtrace:
=>0 0x00000000 (0x0039fc70)
  1 0x0061f6a8 in wow (+0x21f6a8) (0x0039fcc8)
  2 0x0061f752 in wow (+0x21f752) (0x0039fcd8)
  3 0x006058ac in wow (+0x2058ac) (0x0039fce4)
  4 0x00603004 in wow (+0x203004) (0x0039fd08)
  5 0x0048a51f in wow (+0x8a51f) (0x0039fd44)
  6 0x00427069 in wow (+0x27069) (0x0039fd74)
  7 0x0042421c in wow (+0x2421c) (0x0039fda0)
  8 0x004256ea in wow (+0x256ea) (0x0039fdf4)
  9 0x00425731 in wow (+0x25731) (0x0039fe0c)
  10 0x00406d9d in wow (+0x6d9d) (0x0039fea8)
  11 0x7b877c04 in kernel32 (+0x57c04) (0x0039fee8)
  12 0x7bc6cee4 call_thread_func+0xc() in ntdll (0x0039fef8)
  13 0x7bc6d0f0 call_thread_entry_point+0x70() in ntdll (0x0039ffc8)
  14 0x7bc48ffa in ntdll (+0x38ffa) (0x0039ffe8)
  15 0xf769dedd wine_call_on_stack+0x1d() in libwine.so.1 (0x00000000)

```


Any suggestions at all are appreciated, as I currently have no idea what's going on.

---

### Post by Ylon on 2009-11-26
A "quick" try is to mv your **~/.wine** folder (**~/.wine.back**) and reinstall WoW..is like you had formatted windows :popcorn:

For better solution wait for the real experts.

---

### Post by jamessnell on 2010-06-13
I'm having this same problem on my Ubuntu 10.04 x86 laptop with an Intel X3100 GPU. :\

---

### Post by GeoPirate on 2010-06-14
I'm having the same exact problem with a core i3 based desktop.  I'm no expert but I've definetly worked through a lot of problems on ubuntu, but I'e been unable to find a solution or a workaround.  I think it's some problem with the intel driver, but I don't know exactly what.  I've tried several games in wine on this system and they all seem to have problems loading some textures correctly.

---

