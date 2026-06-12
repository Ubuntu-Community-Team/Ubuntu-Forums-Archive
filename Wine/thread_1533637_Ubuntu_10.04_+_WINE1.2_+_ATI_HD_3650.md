---
title: "Ubuntu 10.04 + WINE1.2 + ATI HD 3650"
date: 2010-07-18
forum: Wine
---

### Post by Yuukan on 2010-07-18
Hi

Hi there 

Im a windows network admin making the move to Linux....... heh 

Anyway I have installed Ubuntu on my Dell Studio 17 Laptop. 
Quick run over 
3 Gig Ram 
ATI Radeon HD 3650  256mb 

I have installed Wine and Playonlinux 

also further I have followed these two guides 
[http://howto.landure.fr/gnu-linux/install-directx-9-0c-on-linux-using-wine](http://howto.landure.fr/gnu-linux/install-directx-9-0c-on-linux-using-wine) 
[http://www.wine-reviews.net/wine-reviews/microsoft/directx-90c-march-2008-redistributable-on-linux-with-wine.html](http://www.wine-reviews.net/wine-reviews/microsoft/directx-90c-march-2008-redistributable-on-linux-with-wine.html) 

However I am still experiencing very poor performance ingame,  graphical tearing/glitching and upon launching WoW i receive a  dxdllreg.exe error. 

I would appreciate if there is anyone else that could talk me  through quickly or point me towards a helpful post.                   

I am now experiencing 8-12 FPS in World of Warcraft and similarly low FPS in Red Alert 3

When attempting the WINE DEBUG mode through the Terminal I receive this:

Wine Debug Reporting

Trying to disable the reporting for Wine to help improve performance according to what I have read this can also be attributed to poor (8-12) FPS.

Below is the error I receive when attempting to run it through terminal.

yuukan@yuukan-laptop:~$ WINEDEBUG="fixme-all" wine /home/yuukan/.wine/dosdevices/c:/users/yuukan/Desktop/wow/wow.exe
err:module:attach_process_dlls "opengl32.dll" failed to initialize, aborting
err:module:LdrInitializeThunk Main exe initialization for L"C:\\users\\yuukan\\Desktop\\wow\\wow.exe" failed, status c0000005
yuukan@yuukan-laptop:~$ wine: Unhandled page fault on read access to 0x0000000f at address 0x68300137 (thread 001a), starting debugger...
Unhandled exception: page fault on read access to 0x0000000f in 32-bit code (0x68300137).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:68300137 ESP:0033f4d8 EBP:0033f840 EFLAGS:00010246(  R- --  I  Z- -P- )
 EAX:00000000 EBX:6834bff4 ECX:0b41fc3c EDX:00000000
 ESI:00000000 EDI:01001858
Stack dump:
0x0033f4d8:  00000108 00410033 0033f544 7bc4613e
0x0033f4e8:  002d0036 00320032 00320032 00000080
0x0033f4f8:  00110000 7bc99ff4 7bc46e71 09818000
0x0033f508:  00000002 01042f60 00320032 7bc99ff4
0x0033f518:  01018000 01018028 0033f570 7bc472d7
0x0033f528:  ffffffff 0033f554 0033f550 00008000
Backtrace:
=>0 0x68300137 NdrDllRegisterProxy+0x27() in rpcrt4 (0x0033f840)
  1 0x358215aa in msvidctl (+0x215a9) (0x0033f878)
  2 0x010055ca in dxdllreg (+0x55c9) (0x0033fbe8)
  3 0x01005a17 in dxdllreg (+0x5a16) (0x0033fe18)
  4 0x010069a1 in dxdllreg (+0x69a0) (0x0033fea8)
  5 0x7b858534 in kernel32 (+0x48533) (0x0033fee8)
  6 0x7bc6f584 call_thread_func+0xb() in ntdll (0x0033fef8)
  7 0x7bc6f750 call_thread_entry_point+0x6f() in ntdll (0x0033ffc8)
  8 0x7bc4b0aa in ntdll (+0x3b0a9) (0x0033ffe8)
0x68300137 NdrDllRegisterProxy+0x27 in rpcrt4: movzbl    0xf(%esi),%eax
Modules:
Module    Address            Debug info    Name (88 modules)
PE      470000-  493000    Deferred        devenum
PE     1000000- 1018000    Export          dxdllreg
ELF    20000000-20087000    Deferred        winmm<elf>
  \-PE    20010000-20087000    \               winmm
ELF    20087000-200cf000    Deferred        dsound<elf>
  \-PE    20090000-200cf000    \               dsound
ELF    200cf000-20102000    Deferred        uxtheme<elf>
  \-PE    200e0000-20102000    \               uxtheme
ELF    33ddd000-33ec3000    Deferred        oleaut32<elf>
  \-PE    33df0000-33ec3000    \               oleaut32
PE    35500000-35708000    Deferred        quartz
PE    35800000-35931000    Export          msvidctl
ELF    46d65000-46e33000    Deferred        comctl32<elf>
  \-PE    46d70000-46e33000    \               comctl32
ELF    48fdc000-4904c000    Deferred        msvcrt<elf>
  \-PE    48ff0000-4904c000    \               msvcrt
ELF    68000000-6801d000    Deferred        ld-linux.so.2
ELF    6801d000-68158000    Export          libwine.so.1
ELF    68158000-68171000    Deferred        libpthread.so.0
ELF    68171000-682cb000    Deferred        libc.so.6
ELF    682cb000-682cf000    Deferred        libdl.so.2
ELF    682cf000-682d7000    Deferred        libnss_compat.so.2
ELF    682d7000-682e1000    Deferred        libnss_nis.so.2
ELF    682e1000-68352000    Export          rpcrt4<elf>
  \-PE    682f0000-68352000    \               rpcrt4
ELF    68352000-683ab000    Deferred        setupapi<elf>
  \-PE    68360000-683ab000    \               setupapi
ELF    683ab000-684ba000    Deferred        user32<elf>
  \-PE    683c0000-684ba000    \               user32
ELF    684ba000-68544000    Deferred        gdi32<elf>
  \-PE    684d0000-68544000    \               gdi32
ELF    68544000-6855d000    Deferred        version<elf>
  \-PE    68550000-6855d000    \               version
ELF    6855d000-68571000    Deferred        lz32<elf>
  \-PE    68560000-68571000    \               lz32
ELF    68571000-6866d000    Deferred        ole32<elf>
  \-PE    68590000-6866d000    \               ole32
ELF    6866d000-686e3000    Deferred        libfreetype.so.6
ELF    686e3000-686f8000    Deferred        libz.so.1
ELF    686f8000-68728000    Deferred        libfontconfig.so.1
ELF    68728000-6874f000    Deferred        libexpat.so.1
ELF    6874f000-687ee000    Deferred        winex11<elf>
  \-PE    68760000-687ee000    \               winex11
ELF    687ee000-687f7000    Deferred        libsm.so.6
ELF    687f7000-68810000    Deferred        libice.so.6
ELF    68810000-68820000    Deferred        libxext.so.6
ELF    68820000-6893d000    Deferred        libx11.so.6
ELF    6893d000-68942000    Deferred        libuuid.so.1
ELF    68942000-6895c000    Deferred        libxcb.so.1
ELF    6895c000-68960000    Deferred        libxau.so.6
ELF    68960000-68966000    Deferred        libxdmcp.so.6
ELF    68966000-68987000    Deferred        imm32<elf>
  \-PE    68970000-68987000    \               imm32
ELF    68987000-6898b000    Deferred        libxinerama.so.1
ELF    6898b000-68991000    Deferred        libxxf86vm.so.1
ELF    68991000-68995000    Deferred        libxcomposite.so.1
ELF    68995000-6899b000    Deferred        libxfixes.so.3
ELF    6899b000-689e1000    Deferred        libcups.so.2
ELF    689e1000-68a10000    Deferred        libgssapi_krb5.so.2
ELF    68a10000-68aab000    Deferred        libgnutls.so.26
ELF    68aab000-68ab7000    Deferred        libavahi-common.so.3
ELF    68ab7000-68ac8000    Deferred        libavahi-client.so.3
ELF    68ac8000-68aec000    Deferred        libk5crypto.so.3
ELF    68aec000-68af0000    Deferred        libcom_err.so.2
ELF    68af0000-68af8000    Deferred        libkrb5support.so.0
ELF    68af8000-68afc000    Deferred        libkeyutils.so.1
ELF    68afc000-68b10000    Deferred        libresolv.so.2
ELF    68b10000-68b21000    Deferred        libtasn1.so.3
ELF    68b21000-68b5a000    Deferred        libdbus-1.so.3
ELF    68b5a000-68b63000    Deferred        librt.so.1
ELF    68b63000-68b68000    Deferred        libgpg-error.so.0
ELF    6ada2000-6adc8000    Deferred        libm.so.6
ELF    6d137000-6d141000    Deferred        libxrender.so.1
ELF    7063e000-706b1000    Deferred        libgcrypt.so.11
ELF    71cf1000-71d08000    Deferred        libnsl.so.1
ELF    7275f000-72810000    Deferred        libkrb5.so.3
ELF    73e37000-73e41000    Deferred        libxcursor.so.1
ELF    74339000-7436f000    Deferred        winspool<elf>
  \-PE    74340000-7436f000    \               winspool
ELF    7564f000-7565b000    Deferred        libnss_files.so.2
ELF    7b3a5000-7b3ad000    Deferred        libxrandr.so.2
ELF    7b800000-7b93a000    Export          kernel32<elf>
  \-PE    7b810000-7b93a000    \               kernel32
ELF    7bc00000-7bcb6000    Export          ntdll<elf>
  \-PE    7bc10000-7bcb6000    \               ntdll
ELF    7bf00000-7bf04000    Deferred        <wine-loader>
ELF    7ca0d000-7ca66000    Deferred        advapi32<elf>
  \-PE    7ca20000-7ca66000    \               advapi32
Threads:
process  tid      prio (all id:s are in hex)
0000000e services.exe
    0000001e    0
    0000001d    0
    0000001c    0
    00000015    0
    00000014    0
    00000010    0
    0000000f    0
00000011 dxdllreg.exe
    00000016    0
    00000013    0
    00000012    0
00000017 winedevice.exe
    00000020    0
    0000001f    0
    0000001b    0
    00000018    0
00000019 (D) C:\windows\system32\dxdllreg.exe
    0000001a    0 <==
00000021 explorer.exe
    00000022    0
Backtrace:
=>0 0x68300137 NdrDllRegisterProxy+0x27() in rpcrt4 (0x0033f840)
  1 0x358215aa in msvidctl (+0x215a9) (0x0033f878)
  2 0x010055ca in dxdllreg (+0x55c9) (0x0033fbe8)
  3 0x01005a17 in dxdllreg (+0x5a16) (0x0033fe18)
  4 0x010069a1 in dxdllreg (+0x69a0) (0x0033fea8)
  5 0x7b858534 in kernel32 (+0x48533) (0x0033fee8)
  6 0x7bc6f584 call_thread_func+0xb() in ntdll (0x0033fef8)
  7 0x7bc6f750 call_thread_entry_point+0x6f() in ntdll (0x0033ffc8)
  8 0x7bc4b0aa in ntdll (+0x3b0a9) (0x0033ffe8)

---

### Post by apuglisi on 2010-07-18
I'm experiencing a similar problem using GuildWars and with an ATI HD4200 in my notebook Acer Aspire 5542.

In windows 7 I get like 45-50 fps but in wine i can't seem to get above 10 to 15 fps at most.

I hope we can work this thing out soon.
Good luck!

---

### Post by asdfoo on 2010-07-18
have you tried the most recent version of fglrx?

---

