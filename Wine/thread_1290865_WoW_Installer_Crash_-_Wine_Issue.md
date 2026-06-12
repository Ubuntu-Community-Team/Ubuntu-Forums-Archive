---
title: "WoW Installer Crash - Wine Issue?"
date: 2009-10-14
forum: Wine
---

### Post by r4itei on 2009-10-14
so i run the WoWinstaller.exe file

it gives me 3 options: classic, burning crusade, wrath of lich king

i pick the first 2nd or third option and it closes on me.

On Ubuntu 8.04 Hardy LTS
Wine is updated to version 1.1.31
Tried to use Windows ver.98, XP and Vista.
No library overrides/registry edits.
Wine only used for uTorrent.


Terminal:
```
r4itei@r4itei-laptop:~$ wine "/home/r4itei/Downloads/InstallWoW.exe"
system.reg is not a valid registry file
userdef.reg is not a valid registry file
user.reg is not a valid registry file
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (3000): STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT 3000
err:ole:CoGetClassObject class {8856f961-340a-11d0-a96b-00c04fd705a2} not registered
err:ole:CoGetClassObject class {8856f961-340a-11d0-a96b-00c04fd705a2} not registered
err:ole:CoGetClassObject no class object {8856f961-340a-11d0-a96b-00c04fd705a2} could be created for context 0x3
wine: Unhandled page fault on read access to 0x00000010 at address 0x422654 (thread 0009), starting debugger...
Unhandled exception: page fault on read access to 0x00000010 in 32-bit code (0x00422654).
Register dump:
 CS:0023 SS:002b DS:002b ES:002b FS:0063 GS:006b
 EIP:00422654 ESP:0032f85c EBP:004d0bb8 EFLAGS:00010286(  R- --  I S - -P- )
 EAX:00000000 EBX:00000005 ECX:00000000 EDX:00000000
 ESI:0032f988 EDI:ffffffff
Stack dump:
0x0032f85c:  00407e42 00000000 bd742fe7 00688b18
0x0032f86c:  0032f988 0032fe08 00484b30 00000004
0x0032f87c:  00406fbe bd742f0b 004d0bb8 004d0bb8
0x0032f88c:  0032feb8 ffffffff 00688018 00688b18
0x0032f89c:  004b80b4 00000001 00000000 00000000
0x0032f8ac:  00000000 00000001 00000000 00000000
Backtrace:
=>0 0x00422654 in installwow (+0x22654) (0x004d0bb8)
  1 0x00000001 (0x004a4eb4)
  2 0x004065b0 in installwow (+0x65b0) (0x0045cfac)
0x00422654: cmpl    $0,0x10(%ecx)
Modules:
Module    Address            Debug info    Name (95 modules)
PE      400000-  522000    Export          installwow
ELF    7b800000-7b96e000    Deferred        kernel32<elf>
  \-PE    7b820000-7b96e000    \               kernel32
ELF    7bc00000-7bcae000    Deferred        ntdll<elf>
  \-PE    7bc10000-7bcae000    \               ntdll
ELF    7bf00000-7bf03000    Deferred        <wine-loader>
ELF    7df3b000-7df95000    Deferred        riched20<elf>
  \-PE    7df50000-7df95000    \               riched20
ELF    7df95000-7dfad000    Deferred        spoolss<elf>
  \-PE    7dfa0000-7dfad000    \               spoolss
ELF    7dfad000-7dfcb000    Deferred        localspl<elf>
  \-PE    7dfb0000-7dfcb000    \               localspl
ELF    7dfcb000-7dfcf000    Deferred        libgpg-error.so.0
ELF    7dfcf000-7e01c000    Deferred        libgcrypt.so.11
ELF    7e01c000-7e02c000    Deferred        libtasn1.so.3
ELF    7e02c000-7e03f000    Deferred        libresolv.so.2
ELF    7e03f000-7e042000    Deferred        libkeyutils.so.1
ELF    7e042000-7e074000    Deferred        libcrypt.so.1
ELF    7e074000-7e0ea000    Deferred        libgnutls.so.13
ELF    7e0ea000-7e10d000    Deferred        libk5crypto.so.3
ELF    7e10d000-7e19a000    Deferred        libkrb5.so.3
ELF    7e19a000-7e1c3000    Deferred        libgssapi_krb5.so.2
ELF    7e1c3000-7e1f6000    Deferred        libcups.so.2
ELF    7e1f9000-7e204000    Deferred        libgcc_s.so.1
ELF    7e204000-7e20a000    Deferred        libnss_dns.so.2
ELF    7e20a000-7e20d000    Deferred        libnss_mdns4_minimal.so.2
ELF    7e25b000-7e28e000    Deferred        uxtheme<elf>
  \-PE    7e260000-7e28e000    \               uxtheme
ELF    7e28e000-7e297000    Deferred        libxcursor.so.1
ELF    7e297000-7e29c000    Deferred        libxfixes.so.3
ELF    7e29c000-7e29f000    Deferred        libxcomposite.so.1
ELF    7e29f000-7e2a5000    Deferred        libxrandr.so.2
ELF    7e2a5000-7e2ad000    Deferred        libxrender.so.1
ELF    7e2ad000-7e2b2000    Deferred        libxxf86vm.so.1
ELF    7e2b2000-7e2b5000    Deferred        libxinerama.so.1
ELF    7e2b5000-7e2d5000    Deferred        imm32<elf>
  \-PE    7e2c0000-7e2d5000    \               imm32
ELF    7e2d5000-7e2da000    Deferred        libxdmcp.so.6
ELF    7e2da000-7e2f2000    Deferred        libxcb.so.1
ELF    7e2f2000-7e2f4000    Deferred        libxcb-xlib.so.0
ELF    7e2f4000-7e3db000    Deferred        libx11.so.6
ELF    7e3db000-7e3e9000    Deferred        libxext.so.6
ELF    7e3e9000-7e3f1000    Deferred        libkrb5support.so.0
ELF    7e3fb000-7e3fe000    Deferred        libcom_err.so.2
ELF    7e400000-7e49b000    Deferred        winex11<elf>
  \-PE    7e410000-7e49b000    \               winex11
ELF    7e4a8000-7e4c9000    Deferred        libexpat.so.1
ELF    7e4c9000-7e4f3000    Deferred        libfontconfig.so.1
ELF    7e4f3000-7e560000    Deferred        libfreetype.so.6
ELF    7e577000-7e58b000    Deferred        system.drv16.so
PE    7e580000-7e58b000    Deferred        system.drv16
ELF    7e58b000-7e5a3000    Deferred        version<elf>
  \-PE    7e590000-7e5a3000    \               version
ELF    7e5a3000-7e5c5000    Deferred        mpr<elf>
  \-PE    7e5b0000-7e5c5000    \               mpr
ELF    7e5c5000-7e5da000    Deferred        libz.so.1
ELF    7e5db000-7e5de000    Deferred        libxau.so.6
ELF    7e5de000-7e5f1000    Deferred        lz32<elf>
  \-PE    7e5e0000-7e5f1000    \               lz32
ELF    7e5f1000-7e647000    Deferred        wininet<elf>
  \-PE    7e600000-7e647000    \               wininet
ELF    7e647000-7e726000    Deferred        oleaut32<elf>
  \-PE    7e660000-7e726000    \               oleaut32
ELF    7e726000-7e791000    Deferred        rpcrt4<elf>
  \-PE    7e730000-7e791000    \               rpcrt4
ELF    7e791000-7e889000    Deferred        ole32<elf>
  \-PE    7e7b0000-7e889000    \               ole32
ELF    7e889000-7e8b2000    Deferred        oledlg<elf>
  \-PE    7e890000-7e8b2000    \               oledlg
ELF    7e8b2000-7e8e5000    Deferred        winspool<elf>
  \-PE    7e8c0000-7e8e5000    \               winspool
ELF    7e8e5000-7e9ac000    Deferred        comctl32<elf>
  \-PE    7e8f0000-7e9ac000    \               comctl32
ELF    7e9ac000-7ea07000    Deferred        shlwapi<elf>
  \-PE    7e9c0000-7ea07000    \               shlwapi
ELF    7ea07000-7eb95000    Deferred        shell32<elf>
  \-PE    7ea20000-7eb95000    \               shell32
ELF    7eb95000-7ec46000    Deferred        comdlg32<elf>
  \-PE    7eba0000-7ec46000    \               comdlg32
ELF    7ec46000-7ec9c000    Deferred        advapi32<elf>
  \-PE    7ec50000-7ec9c000    \               advapi32
ELF    7ec9c000-7ed3b000    Deferred        gdi32<elf>
  \-PE    7ecb0000-7ed3b000    \               gdi32
ELF    7ed3b000-7ee81000    Deferred        user32<elf>
  \-PE    7ed50000-7ee81000    \               user32
ELF    7efa1000-7efac000    Deferred        libnss_files.so.2
ELF    7efac000-7efc4000    Deferred        libnsl.so.1
ELF    7efc4000-7efe9000    Deferred        libm.so.6
ELF    7efed000-7eff7000    Deferred        libnss_nis.so.2
ELF    7eff7000-7f000000    Deferred        libnss_compat.so.2
ELF    f7c37000-f7c3b000    Deferred        libdl.so.2
ELF    f7c3b000-f7d8a000    Deferred        libc.so.6
ELF    f7d8b000-f7da3000    Deferred        libpthread.so.0
ELF    f7dba000-f7ef5000    Deferred        libwine.so.1
ELF    f7ef7000-f7f16000    Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
00000008 (D) Z:\home\r4itei\Downloads\InstallWoW.exe
    00000011    0
    00000009    0 <==
0000000c 
    0000000e    0
    0000000d    0
0000000f 
    00000010    0
Backtrace:
=>0 0x00422654 in installwow (+0x22654) (0x004d0bb8)
  1 0x00000001 (0x004a4eb4)
  2 0x004065b0 in installwow (+0x65b0) (0x0045cfac)

```

If any other info is necessary, will reply back as soon as possible

---

### Post by 8Kuula on 2009-10-14
Somewhat long shot...

> ```
system.reg is not a valid registry file
userdef.reg is not a valid registry file
user.reg is not a valid registry file
```

Maybe some reason wine can't access those files? or files are corrupted?
So when installer tries to access registery it crashes, well anyway here is what i suggest to try:

1.) Open terminal.

2.) These create new default .wine directory to your home directory, named as .wine-wow, when you run winecfg check that your drive settings are correct.
WINEPREFIX setting will be lost if you close your terminal.

Commands:
$ export WINEPREFIX=$HOME/.wine-wow
$ winecfg

3.) Lets run installer then.
$ cd /home/r4itei/Downloads
$ wine ./InstallWoW.exe

4.) If won't work, remember to mock me on my stupidity.
You can just delete that .wine-wow directory from your home directory if it won't work.
$ rm -r ~/.wine-wow

5.) Close terminal. kkthxbb.

If this did work, remember to add/edit "env WINEPREFIX=/home/r4itei/.wine-wow wine ..." to your launcher icon so wine uses that .wine-wow directory.

---

