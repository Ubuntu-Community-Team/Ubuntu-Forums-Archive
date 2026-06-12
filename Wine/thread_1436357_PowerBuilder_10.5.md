---
title: "PowerBuilder 10.5"
date: 2010-03-22
forum: Wine
---

### Post by morgue on 2010-03-22
Ok I was able to install it, I created the [ODBC]("http://wiki.winehq.org/NativeOdbc") and SQL Anywhere works and some other stuff, but when I try to run C:\Program Files\Sybase\PowerBuilder 10.5\PB105.exe I get the following:

```

~/.wine/drive_c/Program Files/Sybase/PowerBuilder 10.5$ wine PB105.exe 
wine: Unhandled page fault on read access to 0x01f38738 at address 0x10bd997a (thread 0009), starting debugger...
Unhandled exception: page fault on read access to 0x01f38738 in 32-bit code (0x10bd997a).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:10bd997a ESP:0032d2d8 EBP:0032d340 EFLAGS:00010202(   - 00      - -RI1)
 EAX:00000001 EBX:01f38738 ECX:c40b9600 EDX:01f38738
 ESI:00000000 EDI:0032d33f
Stack dump:
0x0032d2d8:  00f9dffc 00f9dfbc 01f38738 00200001
0x0032d2e8:  0000002e 00000001 33463130 38333738
0x0032d2f8:  2020203a 20202020 20202020 20202020
0x0032d308:  20202020 20202020 20202020 20202020
0x0032d318:  20202020 20202020 20202020 20202020
0x0032d328:  20202020 20202020 20202020 20202020
Backtrace:
=>1 0x10bd997a in pbshr105 (+0xd997a) (0x0032d340)
  2 0x10bda29f in pbshr105 (+0xda29f) (0x00000008)
  3 0x00000000 (0x00000000)
0x10bd997a: movzbl	0xffffffff(%edx,%eax,1),%eax
Modules:
Module	Address			Debug info	Name (117 modules)
PE	  450000-  811000	Deferred        pbvm105
PE	  820000-  89f000	Deferred        libjcc
PE	  8a0000-  8d4000	Deferred        libjutils
PE	  8e0000-  9ab000	Deferred        pbdts105
PE	  9b0000-  9dd000	Deferred        pbapl105
PE	  9e0000-  a19000	Deferred        pbeas105
PE	10000000-10010000	Deferred        pb105
PE	103d0000-10478000	Deferred        pbcmp105
PE	10480000-1050e000	Deferred        pbdev105
PE	10510000-10534000	Deferred        pbdpp105
PE	10600000-109bf000	Deferred        pbsys105
PE	10b00000-10c4c000	Export          pbshr105
PE	10d30000-10d40000	Deferred        pborc105
PE	10e10000-10ea3000	Deferred        pbsql105
PE	11500000-1183c000	Deferred        pbdwe105
PE	11880000-118a0000	Deferred        pbwed105
PE	11e00000-11f3d000	Deferred        pblib105
PE	12000000-121e0000	Deferred        pbdwp105
PE	12600000-1267a000	Deferred        pbscr105
PE	12700000-128bb000	Deferred        pbudo105
ELF	60000000-6001d000	Deferred        ld-linux.so.2
ELF	6001d000-60153000	Deferred        libwine.so.1
ELF	60153000-6016c000	Deferred        libpthread.so.0
ELF	6016c000-602b1000	Deferred        libc.so.6
ELF	602b1000-602b5000	Deferred        libdl.so.2
ELF	602b5000-602db000	Deferred        libm.so.6
ELF	602db000-602e3000	Deferred        libnss_compat.so.2
ELF	602e3000-602fa000	Deferred        libnsl.so.1
ELF	602fa000-60306000	Deferred        libnss_files.so.2
ELF	60306000-60451000	Deferred        user32<elf>
  \-PE	60320000-60451000	\               user32
ELF	60451000-604ff000	Deferred        comdlg32<elf>
  \-PE	60460000-604ff000	\               comdlg32
ELF	604ff000-60613000	Deferred        shell32<elf>
  \-PE	60510000-60613000	\               shell32
ELF	60613000-6066e000	Deferred        shlwapi<elf>
  \-PE	60620000-6066e000	\               shlwapi
ELF	6066e000-606a5000	Deferred        winspool<elf>
  \-PE	60680000-606a5000	\               winspool
ELF	606a5000-6074b000	Deferred        ole32<elf>
  \-PE	606b0000-6074b000	\               ole32
ELF	6074b000-607ae000	Deferred        rpcrt4<elf>
  \-PE	60760000-607ae000	\               rpcrt4
ELF	607ae000-607cd000	Deferred        iphlpapi<elf>
  \-PE	607b0000-607cd000	\               iphlpapi
ELF	607cd000-607e1000	Deferred        libresolv.so.2
ELF	607e1000-60887000	Deferred        oleaut32<elf>
  \-PE	607f0000-60887000	\               oleaut32
ELF	60887000-60906000	Deferred        libfreetype.so.6
ELF	60906000-6091c000	Deferred        libz.so.1
ELF	6091c000-60949000	Deferred        libfontconfig.so.1
ELF	60949000-60970000	Deferred        libexpat.so.1
ELF	60970000-60a0a000	Deferred        winex11<elf>
  \-PE	60980000-60a0a000	\               winex11
ELF	60a0a000-60a13000	Deferred        libsm.so.6
ELF	60a13000-60a2e000	Deferred        libice.so.6
ELF	60a2e000-60b5d000	Deferred        libx11.so.6
ELF	60b5d000-60b62000	Deferred        libuuid.so.1
ELF	60b62000-60b66000	Deferred        libxau.so.6
ELF	60b66000-60b84000	Deferred        libxcb.so.1
ELF	60b84000-60ba5000	Deferred        imm32<elf>
  \-PE	60b90000-60ba5000	\               imm32
ELF	60ba5000-60ba8000	Deferred        libxinerama.so.1
ELF	60ba8000-60bb1000	Deferred        libxrandr.so.2
ELF	60bb1000-60bb5000	Deferred        libxcomposite.so.1
ELF	60bb5000-60bbb000	Deferred        libxfixes.so.3
ELF	60bbb000-60bc6000	Deferred        libxcursor.so.1
ELF	60bc6000-60be1000	Deferred        wsock32<elf>
  \-PE	60bd0000-60be1000	\               wsock32
ELF	60be1000-60c0e000	Deferred        ws2_32<elf>
  \-PE	60bf0000-60c0e000	\               ws2_32
ELF	60c0e000-60c29000	Deferred        version<elf>
  \-PE	60c10000-60c29000	\               version
ELF	60c29000-60c3e000	Deferred        lz32<elf>
  \-PE	60c30000-60c3e000	\               lz32
ELF	60c3e000-60c64000	Deferred        oledlg<elf>
  \-PE	60c40000-60c64000	\               oledlg
ELF	60c64000-60c97000	Deferred        uxtheme<elf>
  \-PE	60c70000-60c97000	\               uxtheme
ELF	60c97000-60cc1000	Deferred        libgssapi_krb5.so.2
ELF	60cc1000-60d69000	Deferred        libgnutls.so.26
ELF	60d69000-60d75000	Deferred        libavahi-common.so.3
ELF	60d75000-60d86000	Deferred        libavahi-client.so.3
ELF	60d86000-60e2c000	Deferred        libkrb5.so.3
ELF	60e2c000-60e55000	Deferred        libk5crypto.so.3
ELF	60e55000-60e59000	Deferred        libcom_err.so.2
ELF	60e59000-60e61000	Deferred        libkrb5support.so.0
ELF	60e61000-60e65000	Deferred        libkeyutils.so.1
ELF	60e65000-60e77000	Deferred        libtasn1.so.3
ELF	60e77000-60ef3000	Deferred        libgcrypt.so.11
ELF	61d74000-61dba000	Deferred        libcups.so.2
ELF	6658f000-66594000	Deferred        libgpg-error.so.0
ELF	669dd000-669f1000	Deferred        olepro32<elf>
  \-PE	669e0000-669f1000	\               olepro32
ELF	678d0000-6796f000	Deferred        gdi32<elf>
  \-PE	678e0000-6796f000	\               gdi32
ELF	692f1000-692f6000	Deferred        libxdmcp.so.6
ELF	6a48c000-6a495000	Deferred        librt.so.1
ELF	6b233000-6b243000	Deferred        libxext.so.6
PE	70d00000-70e91000	Deferred        gdiplus
ELF	71a05000-71a0b000	Deferred        libxxf86vm.so.1
ELF	73d19000-73ddc000	Deferred        comctl32<elf>
  \-PE	73d20000-73ddc000	\               comctl32
ELF	74cad000-74cb8000	Deferred        libnss_nis.so.2
ELF	76004000-7603d000	Deferred        libdbus-1.so.3
ELF	76188000-76192000	Deferred        libxrender.so.1
PE	78000000-78044000	Deferred        msvcrt
ELF	78827000-78879000	Deferred        advapi32<elf>
  \-PE	78830000-78879000	\               advapi32
ELF	7b800000-7b93c000	Deferred        kernel32<elf>
  \-PE	7b820000-7b93c000	\               kernel32
ELF	7bc00000-7bca7000	Deferred        ntdll<elf>
  \-PE	7bc10000-7bca7000	\               ntdll
ELF	7bf00000-7bf04000	Deferred        <wine-loader>
PE	7c120000-7c139000	Deferred        atl71
PE	7c340000-7c396000	Deferred        msvcr71
PE	7c3a0000-7c41b000	Deferred        msvcp71
Threads:
process  tid      prio (all id:s are in hex)
00000008 (D) C:\Program Files\Sybase\PowerBuilder 10.5\PB105.exe
	00000009    0 <==
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
00000017 
	00000018    0
Backtrace:
=>1 0x10bd997a in pbshr105 (+0xd997a) (0x0032d340)
  2 0x10bda29f in pbshr105 (+0xda29f) (0x00000008)
  3 0x00000000 (0x00000000)

```

I'm even able to have an Adaptive Server database running, but no clue about this, and it would be nice to have, I'm experimenting here, it's not a must, but if it's one of the last things I need from Windows here at work...

---

### Post by morgue on 2010-03-23
bump

---

### Post by morgue on 2010-03-26
well... I couldn't figure this one out, I guess Virtual Box is the way to go :)

---

