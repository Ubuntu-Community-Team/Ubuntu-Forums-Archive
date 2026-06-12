---
title: "Bad Compnay 2"
date: 2010-06-21
forum: Wine
---

### Post by jchase45 on 2010-06-21
Ok I tried to launch BF2 Bad COmapny 2 from terminal and got this error log 


[PHP]


jared@jared-desktop:~/.wine/drive_c/Program Files/Electronic Arts/Battlefield Bad Company 2$ wine BFBC2Game.exe 
fixme:ntdll:NtQuerySystemInformation info_class SYSTEM_HANDLE_INFORMATION 
fixme:ntdll:NtQueryObject Unsupported information class 3 
err:rpc:I_RpcGetBuffer no binding 
fixme:ntdll:NtQueryInformationProcess (process=0xffffffff) Unimplemented information class: ProcessDebugFlags 
fixme:win:EnumDisplayDevicesW ((null),0,0x2fca978,0x00000000), stub! 
fixme:win:EnumDisplayDevicesW ((null),0,0x2fca4f8,0x00000000), stub! 
fixme:psapi:EnumPageFilesA (0x2136910, 0x2fa9734) stub 
fixme:psapi:EnumPageFilesA (0x2136910, 0x2f74050) stub 
fixme:win:EnumDisplayDevicesW ((null),0,0x2f0dfd8,0x00000000), stub! 
fixme:win:EnumDisplayDevicesW ((null),0,0x2f0db58,0x00000000), stub! 
fixme:win:EnumDisplayDevicesW ((null),0,0x2f0da10,0x00000000), stub! 
fixme:win:EnumDisplayDevicesW ((null),0,0x2f0d590,0x00000000), stub! 
fixme:win:EnumDisplayDevicesW ((null),0,0x2f0da10,0x00000000), stub! 
fixme:win:EnumDisplayDevicesW ((null),0,0x2f0d590,0x00000000), stub! 
fixme:win:EnumDisplayDevicesW ((null),0,0x2f0d89c,0x00000000), stub! 
fixme:win:EnumDisplayDevicesW ((null),0,0x2f0d41c,0x00000000), stub! 
wine: Unhandled page fault on read access to 0xa7b2e550 at address 0xa7b2e550 (thread 0015), starting debugger... 
Unhandled exception: page fault on read access to 0xa7b2e550 in 32-bit code (0xa7b2e550). 
Register dump: 
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b 
 EIP:a7b2e550 ESP:02fae544 EBP:02fae590 EFLAGS:00010287(  R- --  I S - -P-C) 
 EAX:05f5cbd2 EBX:a7b2e550 ECX:0000001f EDX:0314b307 
 ESI:00137694 EDI:7e5a4ff4 
Stack dump: 
0x02fae544:  7e595fbc 0019cd18 02fae5d4 ffffffff 
0x02fae554:  7e59429e 00137694 02fae698 02fae707 
0x02fae564:  b76caff4 02fae5b4 02fae694 b75dfc22 
0x02fae574:  00000000 02fae59c b76caff4 02fae5b4 
0x02fae584:  7e5a4ff4 00137640 02fae5d0 02faf5f0 
0x02fae594:  7e5965a1 00137694 02fae5d4 00001000 
Backtrace: 
=>0 0xa7b2e550 (0x02fae590) 
  1 0x7e5965a1 in winhttp (+0x65a0) (0x02faf5f0) 
  2 0x7e596aa1 WinHttpQueryDataAvailable+0x60() in winhttp (0x02faf640) 
0xa7b2e550: -- no code accessible -- 
Modules: 
Module   Address         Debug info   Name (140 modules) 
PE     230000-  2a0000   Deferred        d3dx10_42 
PE     2a0000-  2db000   Deferred        d3dx11_42 
PE     2e0000-  2f6000   Deferred        xinput1_3 
PE     400000- 2ad7000   Deferred        bfbc2game 
PE    2fe0000- 31c7000   Deferred        d3dcompiler_42 
PE    3500000- 355d000   Export          paul 
PE    3670000- 36b3000   Deferred        winui 
PE   10000000-101e5000   Deferred        d3dx9_42 
PE   18000000-1803b000   Deferred        binkw32 
PE   78130000-781cb000   Deferred        msvcr80 
ELF   7b800000-7b946000   Deferred        kernel32<elf> 
  \-PE   7b810000-7b946000   \               kernel32 
ELF   7bc00000-7bcb8000   Deferred        ntdll<elf> 
  \-PE   7bc10000-7bcb8000   \               ntdll 
ELF   7bf00000-7bf04000   Deferred        <wine-loader> 
PE   7c420000-7c4a7000   Deferred        msvcp80 
ELF   7d94b000-7d950000   Deferred        libgpg-error.so.0 
ELF   7d950000-7d959000   Deferred        librt.so.1 
ELF   7d959000-7d992000   Deferred        libdbus-1.so.3 
ELF   7d992000-7da05000   Deferred        libgcrypt.so.11 
ELF   7da05000-7da16000   Deferred        libtasn1.so.3 
ELF   7da16000-7da1a000   Deferred        libkeyutils.so.1 
ELF   7da1a000-7da3e000   Deferred        libk5crypto.so.3 
ELF   7da3e000-7daef000   Deferred        libkrb5.so.3 
ELF   7daef000-7db00000   Deferred        libavahi-client.so.3 
ELF   7db00000-7db0c000   Deferred        libavahi-common.so.3 
ELF   7db0c000-7dba7000   Deferred        libgnutls.so.26 
ELF   7dba7000-7dbd6000   Deferred        libgssapi_krb5.so.2 
ELF   7dbd6000-7dc1c000   Deferred        libcups.so.2 
ELF   7dc89000-7dcbd000   Deferred        uxtheme<elf> 
  \-PE   7dc90000-7dcbd000   \               uxtheme 
ELF   7dcbd000-7dcc7000   Deferred        libxcursor.so.1 
ELF   7dcc7000-7dccd000   Deferred        libxfixes.so.3 
ELF   7dccd000-7dcd1000   Deferred        libxcomposite.so.1 
ELF   7dcd1000-7dcd9000   Deferred        libxrandr.so.2 
ELF   7dcd9000-7dce3000   Deferred        libxrender.so.1 
ELF   7dce3000-7dce9000   Deferred        libxxf86vm.so.1 
ELF   7dce9000-7dced000   Deferred        libxinerama.so.1 
ELF   7dced000-7dd0f000   Deferred        imm32<elf> 
  \-PE   7dcf0000-7dd0f000   \               imm32 
ELF   7dd0f000-7dd15000   Deferred        libxdmcp.so.6 
ELF   7dd15000-7dd19000   Deferred        libxau.so.6 
ELF   7dd19000-7dd33000   Deferred        libxcb.so.1 
ELF   7dd33000-7dd38000   Deferred        libuuid.so.1 
ELF   7dd38000-7de55000   Deferred        libx11.so.6 
ELF   7de55000-7de65000   Deferred        libxext.so.6 
ELF   7de65000-7de7e000   Deferred        libice.so.6 
ELF   7de7e000-7de87000   Deferred        libsm.so.6 
ELF   7de88000-7de90000   Deferred        libkrb5support.so.0 
ELF   7de93000-7de97000   Deferred        libcom_err.so.2 
ELF   7de99000-7df3b000   Deferred        winex11<elf> 
  \-PE   7deb0000-7df3b000   \               winex11 
ELF   7df73000-7df9a000   Deferred        libexpat.so.1 
ELF   7df9a000-7dfca000   Deferred        libfontconfig.so.1 
ELF   7dfdc000-7dff1000   Deferred        libz.so.1 
ELF   7dff1000-7e067000   Deferred        libfreetype.so.6 
ELF   7e067000-7e082000   Deferred        wsock32<elf> 
  \-PE   7e070000-7e082000   \               wsock32 
ELF   7e082000-7e137000   Deferred        comdlg32<elf> 
  \-PE   7e090000-7e137000   \               comdlg32 
ELF   7e137000-7e26f000   Deferred        wined3d<elf> 
  \-PE   7e140000-7e26f000   \               wined3d 
ELF   7e26f000-7e2a3000   Deferred        d3d9<elf> 
  \-PE   7e280000-7e2a3000   \               d3d9 
ELF   7e2a3000-7e2eb000   Deferred        dsound<elf> 
  \-PE   7e2b0000-7e2eb000   \               dsound 
ELF   7e2eb000-7e315000   Deferred        netapi32<elf> 
  \-PE   7e2f0000-7e315000   \               netapi32 
ELF   7e315000-7e329000   Deferred        msimg32<elf> 
  \-PE   7e320000-7e329000   \               msimg32 
ELF   7e329000-7e411000   Deferred        oleaut32<elf> 
  \-PE   7e340000-7e411000   \               oleaut32 
ELF   7e411000-7e477000   Deferred        gdiplus<elf> 
  \-PE   7e420000-7e477000   \               gdiplus 
ELF   7e477000-7e48b000   Deferred        lz32<elf> 
  \-PE   7e480000-7e48b000   \               lz32 
ELF   7e48b000-7e4a4000   Deferred        version<elf> 
  \-PE   7e490000-7e4a4000   \               version 
ELF   7e4a4000-7e4db000   Deferred        winspool<elf> 
  \-PE   7e4b0000-7e4db000   \               winspool 
ELF   7e4db000-7e538000   Deferred        setupapi<elf> 
  \-PE   7e4f0000-7e538000   \               setupapi 
ELF   7e538000-7e54c000   Deferred        libresolv.so.2 
ELF   7e55e000-7e57f000   Deferred        iphlpapi<elf> 
  \-PE   7e560000-7e57f000   \               iphlpapi 
ELF   7e57f000-7e5a6000   Export          winhttp<elf> 
  \-PE   7e590000-7e5a6000   \               winhttp 
ELF   7e5a6000-7e62e000   Deferred        winmm<elf> 
  \-PE   7e5b0000-7e62e000   \               winmm 
ELF   7e62e000-7e686000   Deferred        dbghelp<elf> 
  \-PE   7e640000-7e686000   \               dbghelp 
ELF   7e686000-7e6b3000   Deferred        ws2_32<elf> 
  \-PE   7e690000-7e6b3000   \               ws2_32 
ELF   7e6b3000-7e7b3000   Deferred        ole32<elf> 
  \-PE   7e6d0000-7e7b3000   \               ole32 
ELF   7e7b3000-7e7ec000   Deferred        dinput<elf> 
  \-PE   7e7c0000-7e7ec000   \               dinput 
ELF   7e7ec000-7e807000   Deferred        dinput8<elf> 
  \-PE   7e7f0000-7e807000   \               dinput8 
ELF   7e807000-7e889000   Deferred        msvcrt<elf> 
  \-PE   7e820000-7e889000   \               msvcrt 
ELF   7e889000-7e974000   Deferred        comctl32<elf> 
  \-PE   7e890000-7e974000   \               comctl32 
ELF   7e974000-7e9ff000   Deferred        gdi32<elf> 
  \-PE   7e980000-7e9ff000   \               gdi32 
ELF   7e9ff000-7eb2f000   Deferred        user32<elf> 
  \-PE   7ea10000-7eb2f000   \               user32 
ELF   7eb2f000-7eb91000   Deferred        shlwapi<elf> 
  \-PE   7eb40000-7eb91000   \               shlwapi 
ELF   7eb91000-7ed63000   Deferred        shell32<elf> 
  \-PE   7eba0000-7ed63000   \               shell32 
ELF   7ed63000-7edd8000   Deferred        rpcrt4<elf> 
  \-PE   7ed70000-7edd8000   \               rpcrt4 
ELF   7edd8000-7ee32000   Deferred        advapi32<elf> 
  \-PE   7ede0000-7ee32000   \               advapi32 
ELF   7ee32000-7ee48000   Deferred        psapi<elf> 
  \-PE   7ee40000-7ee48000   \               psapi 
ELF   7efa5000-7efb1000   Deferred        libnss_files.so.2 
ELF   7efb1000-7efc8000   Deferred        libnsl.so.1 
ELF   7efc8000-7efee000   Deferred        libm.so.6 
ELF   7efee000-7eff8000   Deferred        libnss_nis.so.2 
ELF   7eff8000-7f000000   Deferred        libnss_compat.so.2 
ELF   b57d5000-b5812000   Deferred        rsaenh<elf> 
  \-PE   b57e0000-b5812000   \               rsaenh 
ELF   b5812000-b58a8000   Deferred        crypt32<elf> 
  \-PE   b5820000-b58a8000   \               crypt32 
ELF   b58a8000-b59fa000   Deferred        libcrypto.so.0.9.8 
ELF   b59fa000-b5a40000   Deferred        libssl.so.0.9.8 
ELF   b5e31000-b5e37000   Deferred        libnss_dns.so.2 
ELF   b5e37000-b5e3b000   Deferred        libnss_mdns4_minimal.so.2 
ELF   b5e4d000-b5e66000   Deferred        oleacc<elf> 
  \-PE   b5e50000-b5e66000   \               oleacc 
ELF   b5e87000-b5e89000   Deferred        libnvidia-tls.so.1 
ELF   b5e89000-b7499000   Deferred        libglcore.so.1 
ELF   b7499000-b755e000   Deferred        libgl.so.1 
ELF   b7571000-b7575000   Deferred        libdl.so.2 
ELF   b7575000-b76cf000   Deferred        libc.so.6 
ELF   b76d0000-b76e9000   Deferred        libpthread.so.0 
ELF   b76fb000-b783b000   Deferred        libwine.so.1 
ELF   b783d000-b785a000   Deferred        ld-linux.so.2 
Threads: 
process  tid      prio (all id:s are in hex) 
00000008 Steam.exe 
   0000003f    0 
   0000003e    0 
   0000003d    0 
   0000003a    0 
   00000038    1 
   00000037    0 
   00000036    0 
   00000035    0 
   00000033    0 
   00000031   15 
   0000002f    0 
   0000002e    0 
   0000002d    0 
   0000002c    0 
   0000002b    0 
   0000002a    0 
   00000029    0 
   00000028    0 
   00000027    0 
   00000026    0 
   00000025    0 
   00000009    0 
0000000e services.exe 
   00000021    0 
   0000001c    0 
   00000014    0 
   00000010    0 
   0000000f    0 
00000011 winedevice.exe 
   00000018    0 
   00000017    0 
   00000013    0 
   00000012    0 
00000019 PnkBstrA.exe 
   0000001d    0 
   0000001b    0 
   0000001a    0 
0000001e PnkBstrB.exe 
   00000022    0 
   00000020    0 
   0000001f    0 
00000023 explorer.exe 
   00000024    0 
00000040 (D) C:\Program Files\Electronic Arts\Battlefield Bad Company 2\BFBC2Game.exe 
   00000015    0 <== 
Backtrace: 
=>0 0xa7b2e550 (0x02fae590) 
  1 0x7e5965a1 in winhttp (+0x65a0) (0x02faf5f0) 
  2 0x7e596aa1 WinHttpQueryDataAvailable+0x60() in winhttp (0x02faf640) 
jared@jared-desktop:~/.wine/drive_c/Program Files/Electronic Arts/Battlefield Bad Company 2$











[/PHP]

Any help would be greatly appreciated

---

### Post by jchase45 on 2010-06-21
no one knows how to get b f2 running?

---

### Post by AllRadioisDead on 2010-06-21
[http://appdb.winehq.org/objectManager.php?sClass=version&iId=19520&iTestingId=50906](http://appdb.winehq.org/objectManager.php?sClass=version&iId=19520&iTestingId=50906)

---

### Post by jchase45 on 2010-06-21
Thats what she said :lolflag:

---

### Post by asdfoo on 2010-06-24
are you still getting this crash with 1.2-rc4 or latest git?  It would be worth filing a bug for it on the winehq bugzilla if so.

---

