---
title: "Wine show &quot;program error&quot; when I start Origin 8"
date: 2010-08-24
forum: Wine
---

### Post by niziris on 2010-08-24
Hello ubuntu newbe here 

Successfully installed Origin 8 but as soon as I start Origin, it goes gray and window with "Program error" is shown
then I started wine/origin with terminal to see what is the problem and this is what I get...

> niziris@SrebrniVuk:~$ wine '/home/niziris/.wine/dosdevices/c:/Program Files/OriginLab/Origin8/Origin8.exe' 
fixme:setupapi:SetupDiCreateDeviceInfoListExW remote support is not implemented
fixme:setupapi:SetupDiGetClassDevsExW L"": unimplemented for remote machines
fixme:setupapi:SetupDiCreateDeviceInfoListExW remote support is not implemented
fixme:setupapi:SetupDiGetClassDevsExW L"": unimplemented for remote machines
fixme:shdocvw:PersistStreamInit_InitNew (0x8d588
err:ole:ITypeInfo_fnInvoke did not find member id -514, flags 0x2!
err:ole:ITypeInfo_fnInvoke did not find member id -504, flags 0x2!
err:ole:ITypeInfo_fnInvoke did not find member id -514, flags 0x2!
err:ole:ITypeInfo_fnInvoke did not find member id -504, flags 0x2!
err:ole:ITypeInfo_fnInvoke did not find member id -514, flags 0x2!
err:ole:ITypeInfo_fnInvoke did not find member id -504, flags 0x2!
fixme:storage:StgCreateDocfile Storage share mode not implemented.
wine: Unhandled page fault on read access to 0x00000000 at address 0x3d2d8087 (thread 0009), starting debugger...
Unhandled exception: page fault on read access to 0x00000000 in 32-bit code (0x3d2d8087).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:3d2d8087 ESP:0066f474 EBP:0066f4bc EFLAGS:00010202(  R- --  I   - - - )
 EAX:00000000 EBX:3d2ffff4 ECX:3d2ff1e0 EDX:00000000
 ESI:00000000 EDI:0353b070
Stack dump:
0x0066f474:  03695c90 0066f4e4 0012fa80 17e1fc42
0x0066f484:  0066f5f0 0066f744 15914814 00000004
0x0066f494:  03695c90 00000004 5f4d0088 0066f4d0
0x0066f4a4:  5f401b49 5f4d0088 00000040 3d2ffff4
0x0066f4b4:  00000000 0353b070 0066f4dc 3d2e08b7
0x0066f4c4:  00000000 15918087 0066f4ec 03695c90
Backtrace:
=>0 0x3d2d8087 xmldoc_release+0x17() in msxml3 (0x0066f4bc)
  1 0x3d2e08b7 destroy_xmlnode+0x26() in msxml3 (0x0066f4dc)
  2 0x3d2db424 in msxml3 (+0x1b423) (0x0066f51c)
  3 0x17e19bd9 in omocavc (+0x19bd (0x17e20c30)
0x3d2d8087 xmldoc_release+0x17 in msxml3: movl    0x0(%eax),%edi
Modules:
Module    Address            Debug info    Name (141 modules)
PE      3b0000-  3e1000    Deferred        dl35wd32
PE      3f0000-  3fb000    Deferred        ol35wd32
PE      400000-  462000    Deferred        origin8
PE     1140000- 11e2000    Deferred        okxf
PE     2000000- 2100000    Deferred        od70
PE     6000000- 6c9d000    Deferred        ok80
PE     8000000- 804c000    Deferred        outl60
PE     8600000- 8622000    Deferred        osts60
PE     9200000- 9246000    Deferred        ouim60
PE     9d00000- 9d1d000    Deferred        opack
PE     a300000- a4f8000    Deferred        mocabasetypes70
PE     aa00000- ab49000    Deferred        ocompiler80
PE     af00000- af0d000    Deferred        ocmath2
PE     b000000- b00a000    Deferred        ocutils
PE     c000000- c04d000    Deferred        oc3dx70
PE     e000000- e089000    Deferred        orespr70
PE    10000000-100a1000    Deferred        offt
PE    12000000-1225b000    Deferred        ou80
PE    13000000-13020000    Deferred        octree
PE    14000000-14016000    Deferred        oltmsg
PE    14100000-1417e000    Deferred        otreeeditor
PE    14600000-14627000    Deferred        onlsf8
PE    15000000-15190000    Deferred        ogrid
PE    15800000-1592f000    Deferred        okutil80
PE    15f00000-15f2f000    Deferred        otext
PE    16000000-161bc000    Deferred        ocmath
PE    16600000-1661b000    Deferred        octree_utils
PE    16900000-169a4000    Deferred        ocntrls
PE    16b00000-175f5000    Deferred        onag8
PE    17c00000-17c0d000    Deferred        olep
PE    17e00000-17e54000    Export          omocavc
ELF    20000000-20042000    Deferred        shdocvw<elf>
  \-PE    20010000-20042000    \               shdocvw
ELF    20042000-2016c000    Deferred        libxml2.so.2
ELF    2016c000-201c7000    Deferred        urlmon<elf>
  \-PE    20180000-201c7000    \               urlmon
ELF    319fe000-31a36000    Deferred        libxslt.so.1
ELF    3d2b8000-3d30c000    Export          msxml3<elf>
  \-PE    3d2c0000-3d30c000    \               msxml3
PE    44000000-44029000    Deferred        osc60as
PE    4c000000-4c0d6000    Deferred        osr70
ELF    56f90000-56fe9000    Deferred        wininet<elf>
  \-PE    56fa0000-56fe9000    \               wininet
ELF    5cc1a000-5cc3d000    Deferred        mpr<elf>
  \-PE    5cc20000-5cc3d000    \               mpr
PE    5f400000-5f4f2000    Deferred        mfc42
ELF    68000000-6801d000    Deferred        ld-linux.so.2
ELF    6801d000-68036000    Deferred        libpthread.so.0
ELF    68036000-6805c000    Deferred        libm.so.6
ELF    6805c000-68064000    Deferred        libnss_compat.so.2
ELF    68064000-6807b000    Deferred        libnsl.so.1
ELF    6807b000-68087000    Deferred        libnss_files.so.2
ELF    68087000-68196000    Deferred        user32<elf>
  \-PE    680a0000-68196000    \               user32
ELF    68196000-68220000    Deferred        gdi32<elf>
  \-PE    681a0000-68220000    \               gdi32
ELF    68220000-68291000    Deferred        rpcrt4<elf>
  \-PE    68230000-68291000    \               rpcrt4
ELF    68291000-6833c000    Deferred        comdlg32<elf>
  \-PE    682a0000-6833c000    \               comdlg32
ELF    6833c000-684d0000    Deferred        shell32<elf>
  \-PE    68350000-684d0000    \               shell32
ELF    684d0000-6852f000    Deferred        shlwapi<elf>
  \-PE    684e0000-6852f000    \               shlwapi
ELF    6852f000-685fd000    Deferred        comctl32<elf>
  \-PE    68540000-685fd000    \               comctl32
ELF    685fd000-68633000    Deferred        winspool<elf>
  \-PE    68600000-68633000    \               winspool
ELF    68633000-6872f000    Deferred        ole32<elf>
  \-PE    68650000-6872f000    \               ole32
ELF    6872f000-6879f000    Deferred        msvcrt<elf>
  \-PE    68740000-6879f000    \               msvcrt
ELF    6879f000-687b8000    Deferred        version<elf>
  \-PE    687a0000-687b8000    \               version
ELF    687b8000-687cc000    Deferred        lz32<elf>
  \-PE    687c0000-687cc000    \               lz32
ELF    687cc000-687e0000    Deferred        olepro32<elf>
  \-PE    687d0000-687e0000    \               olepro32
ELF    687e0000-68856000    Deferred        libfreetype.so.6
ELF    68856000-68886000    Deferred        libfontconfig.so.1
ELF    68886000-68925000    Deferred        winex11<elf>
  \-PE    68890000-68925000    \               winex11
ELF    68925000-6892e000    Deferred        libsm.so.6
ELF    6892e000-68947000    Deferred        libice.so.6
ELF    68947000-68957000    Deferred        libxext.so.6
ELF    68957000-6895c000    Deferred        libuuid.so.1
ELF    6895c000-68976000    Deferred        libxcb.so.1
ELF    68976000-6897a000    Deferred        libxau.so.6
ELF    6897a000-68980000    Deferred        libxdmcp.so.6
ELF    68980000-689a1000    Deferred        imm32<elf>
  \-PE    68990000-689a1000    \               imm32
ELF    689a1000-689a5000    Deferred        libxinerama.so.1
ELF    689a5000-689ab000    Deferred        libxxf86vm.so.1
ELF    689ab000-689b5000    Deferred        libxrender.so.1
ELF    689b5000-689bd000    Deferred        libxrandr.so.2
ELF    689bd000-689c1000    Deferred        libxcomposite.so.1
ELF    689c1000-689c7000    Deferred        libxfixes.so.3
ELF    689c7000-689d1000    Deferred        libxcursor.so.1
ELF    689d1000-689f8000    Deferred        netapi32<elf>
  \-PE    689e0000-689f8000    \               netapi32
ELF    689f8000-68a18000    Deferred        iphlpapi<elf>
  \-PE    68a00000-68a18000    \               iphlpapi
ELF    68a18000-68a2c000    Deferred        libresolv.so.2
ELF    68a2c000-68a5f000    Deferred        uxtheme<elf>
  \-PE    68a30000-68a5f000    \               uxtheme
ELF    68a5f000-68aa6000    Deferred        libcups.so.2
ELF    68aa6000-68ad5000    Deferred        libgssapi_krb5.so.2
ELF    68ad5000-68b70000    Deferred        libgnutls.so.26
ELF    68b70000-68b7c000    Deferred        libavahi-common.so.3
ELF    68b7c000-68c2d000    Deferred        libkrb5.so.3
ELF    68c2d000-68c31000    Deferred        libcom_err.so.2
ELF    68c31000-68c39000    Deferred        libkrb5support.so.0
ELF    68c39000-68c3d000    Deferred        libkeyutils.so.1
ELF    68c3d000-68c4e000    Deferred        libtasn1.so.3
ELF    68c4e000-68cc1000    Deferred        libgcrypt.so.11
ELF    68cc1000-68cfa000    Deferred        libdbus-1.so.3
ELF    68cfa000-68d03000    Deferred        librt.so.1
ELF    6ad0c000-6ae66000    Deferred        libc.so.6
ELF    6e709000-6e826000    Deferred        libx11.so.6
ELF    6ef5d000-6f043000    Deferred        oleaut32<elf>
  \-PE    6ef70000-6f043000    \               oleaut32
ELF    6f67c000-6f681000    Deferred        libgpg-error.so.0
ELF    717fa000-71823000    Deferred        oledlg<elf>
  \-PE    71800000-71823000    \               oledlg
ELF    72ccc000-72cf8000    Deferred        ws2_32<elf>
  \-PE    72cd0000-72cf8000    \               ws2_32
ELF    745c2000-745e9000    Deferred        libexpat.so.1
ELF    7586f000-759aa000    Deferred        libwine.so.1
ELF    761a7000-761bc000    Deferred        libz.so.1
ELF    76b0d000-76b31000    Deferred        libk5crypto.so.3
PE    780c0000-78121000    Deferred        msvcp60
ELF    79c41000-79c45000    Deferred        libdl.so.2
ELF    79fc2000-79fd3000    Deferred        libavahi-client.so.3
ELF    7a1a9000-7a202000    Deferred        advapi32<elf>
  \-PE    7a1c0000-7a202000    \               advapi32
ELF    7b800000-7b93a000    Deferred        kernel32<elf>
  \-PE    7b810000-7b93a000    \               kernel32
ELF    7bc00000-7bcb6000    Deferred        ntdll<elf>
  \-PE    7bc10000-7bcb6000    \               ntdll
ELF    7bf00000-7bf04000    Deferred        <wine-loader>
ELF    7c029000-7c033000    Deferred        libnss_nis.so.2
Threads:
process  tid      prio (all id:s are in hex)
00000008 (D) C:\Program Files\OriginLab\Origin8\Origin8.exe
    0000001d    0
    0000001c    0
    0000001b    0
    0000001a    0
    00000009    0 <==
0000000e services.exe
    00000015    0
    00000014    0
    00000010    0
    0000000f    0
00000011 winedevice.exe
    00000017    0
    00000016    0
    00000013    0
    00000012    0
00000018 explorer.exe
    00000019    0
Backtrace:
=>0 0x3d2d8087 xmldoc_release+0x17() in msxml3 (0x0066f4bc)
  1 0x3d2e08b7 destroy_xmlnode+0x26() in msxml3 (0x0066f4dc)
  2 0x3d2db424 in msxml3 (+0x1b423) (0x0066f51c)
  3 0x17e19bd9 in omocavc (+0x19bd (0x17e20c30)
Killed
and I have no idea what this means 

also I found [wine comment about Origin 8]("http://appdb.winehq.org/objectManager.php?sClass=application&iId=1598"), they didnt mention any problem, except that Wine need two .dll to run Origin 7.5-> maybe this is the problem, but ..but..but....which is the needed dll? where to find them? etc

wine version is:1.2
ubuntu 10.04 

some help pls!!! I try to open origin project in to QtiPlot but QtiPlot crash instantly so this Wine -Origin version is only one left (ok there is probably more software which can do what origin i qtiplot do, but I need to be compatible with my colleagues which use origin  )

---

### Post by niziris on 2010-08-24
Well I indirectly solved my problem by installing Origin 7 in Wine and so far so good...dont know should I marked this thread as solved?

---

