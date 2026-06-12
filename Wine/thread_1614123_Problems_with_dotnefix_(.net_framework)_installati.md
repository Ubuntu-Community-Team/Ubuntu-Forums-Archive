---
title: "Problems with dotnefix (.net framework) installation"
date: 2010-11-05
forum: Wine
---

### Post by karogi on 2010-11-05
Hi guys, how i can install .NET framework using wine? 

it always crasing on installations start.

look what says terminal:

```
fixme:advapi:DecryptFileA "C:\\users\\karolis\\Temp\\IXP000.TMP\\" 00000000
fixme:advapi:LsaOpenPolicy ((null),0x33f33c,0x00000001,0x33f364) stub
fixme:advapi:LsaClose (0xcafe) stub
fixme:advapi:LookupAccountNameW (null) L"karolis" (nil) 0x7cddc8 (nil) 0x7cddcc 0x7cddc0 - stub
fixme:advapi:LookupAccountNameW (null) L"karolis" 0x1afeb0 0x7cddc8 0x1b04e8 0x7cddcc 0x7cddc0 - stub
fixme:advapi:LookupAccountNameW (null) L"karolis" (nil) 0x7cdd98 (nil) 0x7cdd9c 0x7cdd90 - stub
fixme:advapi:LookupAccountNameW (null) L"karolis" 0xaa7508 0x7cdd98 0xabb110 0x7cdd9c 0x7cdd90 - stub
fixme:msi:ACTION_CustomAction Rollback only action... rollbacks not supported yet
fixme:msi:ACTION_CustomAction Rollback only action... rollbacks not supported yet
fixme:msi:ACTION_CustomAction Rollback only action... rollbacks not supported yet
fixme:msi:ACTION_CustomAction Rollback only action... rollbacks not supported yet
fixme:msi:ACTION_CustomAction Rollback only action... rollbacks not supported yet
fixme:msi:ACTION_CustomAction Rollback only action... rollbacks not supported yet
fixme:msi:ACTION_CustomAction Rollback only action... rollbacks not supported yet
fixme:msi:ACTION_CustomAction Rollback only action... rollbacks not supported yet
fixme:msi:ACTION_CustomAction Rollback only action... rollbacks not supported yet
fixme:msi:ACTION_CustomAction Rollback only action... rollbacks not supported yet
fixme:msi:ACTION_CustomAction Rollback only action... rollbacks not supported yet
fixme:msi:ACTION_CustomAction Rollback only action... rollbacks not supported yet
fixme:msi:ACTION_CustomAction Rollback only action... rollbacks not supported yet
fixme:msi:ACTION_CustomAction Rollback only action... rollbacks not supported yet
fixme:msi:ACTION_CustomAction Rollback only action... rollbacks not supported yet
fixme:msi:ACTION_CustomAction Rollback only action... rollbacks not supported yet
fixme:msi:ACTION_CustomAction Rollback only action... rollbacks not supported yet
fixme:msi:ACTION_CustomAction Rollback only action... rollbacks not supported yet
fixme:msi:ACTION_CustomAction Rollback only action... rollbacks not supported yet
fixme:msi:ACTION_CustomAction Rollback only action... rollbacks not supported yet
fixme:msi:ACTION_CustomAction Rollback only action... rollbacks not supported yet
fixme:msi:ACTION_CustomAction Rollback only action... rollbacks not supported yet
fixme:msi:ACTION_CustomAction Rollback only action... rollbacks not supported yet
fixme:msi:ACTION_CustomAction Rollback only action... rollbacks not supported yet
fixme:msi:ACTION_CustomAction Rollback only action... rollbacks not supported yet
fixme:msi:ACTION_CustomAction Rollback only action... rollbacks not supported yet
fixme:msi:ACTION_CustomAction Rollback only action... rollbacks not supported yet
fixme:msi:ACTION_CustomAction Rollback only action... rollbacks not supported yet
fixme:msi:ACTION_CustomAction Rollback only action... rollbacks not supported yet
fixme:msi:ACTION_CustomAction Rollback only action... rollbacks not supported yet
fixme:msi:ACTION_CustomAction Rollback only action... rollbacks not supported yet
fixme:msi:ACTION_CustomAction Rollback only action... rollbacks not supported yet
fixme:msi:ACTION_CustomAction Rollback only action... rollbacks not supported yet
fixme:msi:ACTION_CustomAction Rollback only action... rollbacks not supported yet
fixme:msi:ACTION_CustomAction Rollback only action... rollbacks not supported yet
fixme:msi:ACTION_CustomAction Rollback only action... rollbacks not supported yet
fixme:msi:ACTION_CustomAction Rollback only action... rollbacks not supported yet
fixme:msi:ACTION_CustomAction Rollback only action... rollbacks not supported yet
fixme:msi:ACTION_CustomAction Rollback only action... rollbacks not supported yet
fixme:msi:ACTION_CustomAction Rollback only action... rollbacks not supported yet
fixme:msi:ACTION_CustomAction Rollback only action... rollbacks not supported yet
fixme:msi:ACTION_CustomAction Rollback only action... rollbacks not supported yet
fixme:msi:ACTION_CustomAction Rollback only action... rollbacks not supported yet
fixme:msi:ACTION_CustomAction Rollback only action... rollbacks not supported yet
fixme:msi:ACTION_CustomAction Rollback only action... rollbacks not supported yet
fixme:msi:ACTION_CustomAction Rollback only action... rollbacks not supported yet
fixme:msi:ACTION_CustomAction Rollback only action... rollbacks not supported yet
fixme:msi:ACTION_CustomAction Rollback only action... rollbacks not supported yet
fixme:msi:ACTION_CustomAction Rollback only action... rollbacks not supported yet
fixme:msi:ACTION_CustomAction Rollback only action... rollbacks not supported yet
fixme:msi:ACTION_CustomAction Rollback only action... rollbacks not supported yet
fixme:msi:msi_unimplemented_action_stub MsiUnpublishAssemblies -> 2 ignored L"MsiAssembly" table values
wine: Unhandled page fault on read access to 0x00000000 at address 0x47175068 (thread 001f), starting debugger...
Unhandled exception: page fault on read access to 0x00000000 in 32-bit code (0x47175068).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:47175068 ESP:007cdc68 EBP:007ce510 EFLAGS:00210246(  R- --  I  Z- -P- )
 EAX:00000000 EBX:471cdff4 ECX:00110064 EDX:00000000
 ESI:00d2af20 EDI:00d2af44
Stack dump:
0x007cdc68:  00188ff8 471bd820 00000000 00000000
0x007cdc78:  00000000 00000000 71c7cff4 00000000
0x007cdc88:  007cddfc 007cdeac 7bc9bff4 00000000
0x007cdc98:  00000000 007cdcdc 7bc76c43 00000001
0x007cdca8:  007cdd0c 00000004 00000000 00000000
0x007cdcb8:  00000008 471bd820 00000001 00000000
Backtrace:
=>0 0x47175068 ready_media+0x2e8() in msi (0x007ce510)
  1 0x47166bd3 ACTION_InstallFiles+0x182() in msi (0x007ce590)
  2 0x4713245e in msi (+0x1245d) (0x007ce5f0)
  3 0x471341f4 ACTION_PerformAction+0x43() in msi (0x007ce640)
  4 0x47134353 in msi (+0x14352) (0x007ce6a0)
  5 0x47140a0c in msi (+0x20a0b) (0x007ce6e0)
  6 0x4713245e in msi (+0x1245d) (0x007ce740)
  7 0x471341f4 ACTION_PerformAction+0x43() in msi (0x007ce790)
  8 0x4713517f in msi (+0x1517e) (0x007ce7d0)
  9 0x471837c0 MSI_IterateRecords+0x6f() in msi (0x007ce830)
  10 0x471316b6 in msi (+0x116b5) (0x007ce880)
  11 0x47141fa6 MSI_InstallPackage+0x3d5() in msi (0x007ce8e0)
  12 0x47178363 MsiInstallProductW+0x82() in msi (0x007ce930)
  13 0x0041826f in install (+0x1826e) (0x007ce9a8)
0x47175068 ready_media+0x2e8 in msi: movzwl	0x0(%edx,%eax,1),%ecx
Modules:
Module	Address			Debug info	Name (107 modules)
PE	  400000-  4ad000	Export          install
ELF	20000000-2002a000	Deferred        netapi32<elf>
  \-PE	20010000-2002a000	\               netapi32
ELF	2002a000-20087000	Deferred        urlmon<elf>
  \-PE	20030000-20087000	\               urlmon
ELF	20087000-200ab000	Deferred        mpr<elf>
  \-PE	20090000-200ab000	\               mpr
ELF	200ab000-200cd000	Deferred        cabinet<elf>
  \-PE	200b0000-200cd000	\               cabinet
ELF	200cd000-200ec000	Deferred        libgcc_s.so.1
ELF	200ec000-2016e000	Deferred        msvcrt<elf>
  \-PE	20100000-2016e000	\               msvcrt
ELF	3a6c6000-3a6f2000	Deferred        secur32<elf>
  \-PE	3a6d0000-3a6f2000	\               secur32
ELF	47114000-471e4000	Export          msi<elf>
  \-PE	47120000-471e4000	\               msi
ELF	4bb6c000-4bb99000	Deferred        ws2_32<elf>
  \-PE	4bb70000-4bb99000	\               ws2_32
ELF	4f414000-4f435000	Deferred        iphlpapi<elf>
  \-PE	4f420000-4f435000	\               iphlpapi
PE	50590000-505a6000	Deferred        install.res.1033
ELF	68000000-6801d000	Deferred        ld-linux.so.2
ELF	6801d000-6815d000	Deferred        libwine.so.1
ELF	6815d000-68176000	Deferred        libpthread.so.0
ELF	68176000-682d0000	Deferred        libc.so.6
ELF	682d0000-682d4000	Deferred        libdl.so.2
ELF	682d4000-682fa000	Deferred        libm.so.6
ELF	682fa000-68302000	Deferred        libnss_compat.so.2
ELF	68302000-68319000	Deferred        libnsl.so.1
ELF	68319000-68323000	Deferred        libnss_nis.so.2
ELF	68323000-6832f000	Deferred        libnss_files.so.2
ELF	6832f000-683ba000	Deferred        gdi32<elf>
  \-PE	68340000-683ba000	\               gdi32
ELF	683ba000-68415000	Deferred        advapi32<elf>
  \-PE	683d0000-68415000	\               advapi32
ELF	68415000-685ed000	Deferred        shell32<elf>
  \-PE	68430000-685ed000	\               shell32
ELF	685ed000-6864f000	Deferred        shlwapi<elf>
  \-PE	68600000-6864f000	\               shlwapi
ELF	6864f000-686c4000	Deferred        rpcrt4<elf>
  \-PE	68660000-686c4000	\               rpcrt4
ELF	686c4000-687ad000	Deferred        oleaut32<elf>
  \-PE	686e0000-687ad000	\               oleaut32
ELF	687ad000-687e5000	Deferred        winspool<elf>
  \-PE	687b0000-687e5000	\               winspool
ELF	687e5000-687fe000	Deferred        version<elf>
  \-PE	687f0000-687fe000	\               version
ELF	687fe000-68812000	Deferred        lz32<elf>
  \-PE	68800000-68812000	\               lz32
ELF	68812000-68888000	Deferred        libfreetype.so.6
ELF	68888000-6889d000	Deferred        libz.so.1
ELF	6889d000-688cd000	Deferred        libfontconfig.so.1
ELF	688cd000-688f4000	Deferred        libexpat.so.1
ELF	688f4000-68997000	Deferred        winex11<elf>
  \-PE	68900000-68997000	\               winex11
ELF	68997000-689a0000	Deferred        libsm.so.6
ELF	689a0000-689b9000	Deferred        libice.so.6
ELF	689b9000-689c9000	Deferred        libxext.so.6
ELF	689c9000-68ae6000	Deferred        libx11.so.6
ELF	68ae6000-68aeb000	Deferred        libuuid.so.1
ELF	68aeb000-68b05000	Deferred        libxcb.so.1
ELF	68b05000-68b09000	Deferred        libxau.so.6
ELF	68b09000-68b0f000	Deferred        libxdmcp.so.6
ELF	68b0f000-68b13000	Deferred        libxinerama.so.1
ELF	68b13000-68b19000	Deferred        libxxf86vm.so.1
ELF	68b19000-68b23000	Deferred        libxrender.so.1
ELF	68b23000-68b29000	Deferred        libxfixes.so.3
ELF	68b29000-68b5d000	Deferred        uxtheme<elf>
  \-PE	68b30000-68b5d000	\               uxtheme
ELF	68b5d000-68ba4000	Deferred        libcups.so.2
ELF	68ba4000-68bd3000	Deferred        libgssapi_krb5.so.2
ELF	68bd3000-68bdf000	Deferred        libavahi-common.so.3
ELF	68bdf000-68c03000	Deferred        libk5crypto.so.3
ELF	68c03000-68c07000	Deferred        libcom_err.so.2
ELF	68c07000-68c0b000	Deferred        libkeyutils.so.1
ELF	68c0b000-68c1f000	Deferred        libresolv.so.2
ELF	68c1f000-68c30000	Deferred        libtasn1.so.3
ELF	68c30000-68c39000	Deferred        librt.so.1
ELF	68c39000-68c3e000	Deferred        libgpg-error.so.0
ELF	68c63000-68c6d000	Deferred        libxcursor.so.1
ELF	68c6d000-68d08000	Deferred        libgnutls.so.26
ELF	68d08000-68db9000	Deferred        libkrb5.so.3
ELF	68db9000-68e2c000	Deferred        libgcrypt.so.11
ELF	68e2c000-68e65000	Deferred        libdbus-1.so.3
ELF	69891000-69991000	Deferred        ole32<elf>
  \-PE	698b0000-69991000	\               ole32
ELF	6ccef000-6cdda000	Deferred        comctl32<elf>
  \-PE	6cd00000-6cdda000	\               comctl32
ELF	6f0ae000-6f10a000	Deferred        wininet<elf>
  \-PE	6f0c0000-6f10a000	\               wininet
ELF	7116b000-71173000	Deferred        libkrb5support.so.0
ELF	71bae000-71ce0000	Deferred        user32<elf>
  \-PE	71bc0000-71ce0000	\               user32
ELF	73635000-7363d000	Deferred        libxrandr.so.2
ELF	73c85000-73c89000	Deferred        libxcomposite.so.1
ELF	775ba000-775cb000	Deferred        libavahi-client.so.3
ELF	78a4c000-78aa6000	Deferred        riched20<elf>
  \-PE	78a60000-78aa6000	\               riched20
ELF	7937c000-7939e000	Deferred        imm32<elf>
  \-PE	79380000-7939e000	\               imm32
ELF	7afc9000-7b027000	Deferred        setupapi<elf>
  \-PE	7afd0000-7b027000	\               setupapi
ELF	7b800000-7b972000	Deferred        kernel32<elf>
  \-PE	7b810000-7b972000	\               kernel32
ELF	7bc00000-7bcb8000	Deferred        ntdll<elf>
  \-PE	7bc10000-7bcb8000	\               ntdll
ELF	7bf00000-7bf04000	Deferred        <wine-loader>
Threads:
process  tid      prio (all id:s are in hex)
00000008 dotnetfx.exe
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
0000001d (D) C:\users\karolis\Temp\IXP000.TMP\install.exe
	00000020    0
	0000001f    0 <==
	0000001e    0
Backtrace:
=>0 0x47175068 ready_media+0x2e8() in msi (0x007ce510)
  1 0x47166bd3 ACTION_InstallFiles+0x182() in msi (0x007ce590)
  2 0x4713245e in msi (+0x1245d) (0x007ce5f0)
  3 0x471341f4 ACTION_PerformAction+0x43() in msi (0x007ce640)
  4 0x47134353 in msi (+0x14352) (0x007ce6a0)
  5 0x47140a0c in msi (+0x20a0b) (0x007ce6e0)
  6 0x4713245e in msi (+0x1245d) (0x007ce740)
  7 0x471341f4 ACTION_PerformAction+0x43() in msi (0x007ce790)
  8 0x4713517f in msi (+0x1517e) (0x007ce7d0)
  9 0x471837c0 MSI_IterateRecords+0x6f() in msi (0x007ce830)
  10 0x471316b6 in msi (+0x116b5) (0x007ce880)
  11 0x47141fa6 MSI_InstallPackage+0x3d5() in msi (0x007ce8e0)
  12 0x47178363 MsiInstallProductW+0x82() in msi (0x007ce930)
  13 0x0041826f in install (+0x1826e) (0x007ce9a8)

```
P.S. i want to run lineage 2 (rpg-club server, gracia final). As i remember on ubuntu9.10 i wasn't have any problems to launch lineage 2, but with 10.04 - i can't.

Any ideas?

---

### Post by cogadh on 2010-11-05
You need to use [winetricks]("http://wiki.winehq.org/winetricks") to install .NET, however, .NET 3.5 doesn't work in Wine, so if that version is the one required, it won't help.

---

### Post by karogi on 2010-11-05
i used winetricks to install .net framework... and error which i posted is from that time.

---

### Post by cogadh on 2010-11-05
Which version are you trying to install?

---

### Post by karogi on 2010-11-05
2.0

---

### Post by lkjoel on 2010-11-05
Have you tried the latest PlayOnLinux?
[http://www.playonlinux.com]("http://www.playonlinux.com")

---

### Post by karogi on 2010-11-05
I don't know how play with this....

---

### Post by lkjoel on 2010-11-05
> **karogi said:**
> I don't know how play with this....
Don't get deceived by the title.
It is a GUI to WINE, and it helps WINE installations.

---

### Post by karogi on 2010-11-05
there is no selection of lineage 2 in playonlinux.

whatever... finally i made it! i can play lineage 2 with wine with not bad performance.

Are any ways to improve games performance using wine?

---

