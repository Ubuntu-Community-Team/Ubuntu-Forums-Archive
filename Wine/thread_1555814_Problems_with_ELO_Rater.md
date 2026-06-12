---
title: "Problems with ELO Rater"
date: 2010-08-18
forum: Wine
---

### Post by afowles on 2010-08-18
Hi all.  I'm having a problem running ELO Rater, a program for easily calculating chess ratings in a small club environment (unlike the tournament programs that are available, which require pairings and the like).  I *really* want to use this program.  [http://www.garnergaggle.org/papa/chess/ELORater/](http://www.garnergaggle.org/papa/chess/ELORater/)

But I'm having a problem.  I download the program and run it through Wine, which works fine.  I can even generate a ratings file through the program.  When I try to load a previously generated ratings file, however, the program crashes and instructs me to check Wine's App HQ.  I did.  It ain't got what I need.

I ran it from the terminal and this is what I got:

```
student@teachertower:~/Desktop$ wine ELORater.exe cms.elo
wine: Unhandled page fault on write access to 0x00000000 at address 0x32fd11 (thread 0009), starting debugger...
Unhandled exception: page fault on write access to 0x00000000 in 32-bit code (0x0032fd11).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:0032fd11 ESP:0032fc41 EBP:683a8440 EFLAGS:00010286(  R- --  I S - -P- )
 EAX:00000000 EBX:00000000 ECX:68407764 EDX:00000000
 ESI:0012ea60 EDI:0012ea60
Stack dump:
0x0032fc41:  600012ea 300012ea 250012ea 6000416e
0x0032fc51:  300012ea 6000416d 6f0012ea 6000416e
0x0032fc61:  000012ea 0c000000 c20032fd 04004117
0x0032fc71:  0c000000 d80032fd 000032fc 00000000
0x0032fc81:  01000000 60000000 000012ea a1000000
0x0032fc91:  040040f0 68000000 dc83d8d9 100032fc
Backtrace:
=>0 0x0032fd11 (0x683a8440)
0x0032fd11: addb    %al,0x0(%eax)
Modules:
Module    Address            Debug info    Name (81 modules)
PE      400000-  477000    Deferred        elorater
ELF    68000000-6801d000    Deferred        ld-linux.so.2
ELF    6801d000-68158000    Deferred        libwine.so.1
ELF    68158000-68171000    Deferred        libpthread.so.0
ELF    68171000-682cb000    Deferred        libc.so.6
ELF    682cb000-682cf000    Deferred        libdl.so.2
ELF    682cf000-682f5000    Deferred        libm.so.6
ELF    682f5000-6830c000    Deferred        libnsl.so.1
ELF    6830c000-68316000    Deferred        libnss_nis.so.2
ELF    68316000-68322000    Deferred        libnss_files.so.2
ELF    68322000-68431000    Deferred        user32<elf>
  \-PE    68330000-68431000    \               user32
ELF    68431000-684bb000    Deferred        gdi32<elf>
  \-PE    68440000-684bb000    \               gdi32
ELF    684bb000-68514000    Deferred        advapi32<elf>
  \-PE    684d0000-68514000    \               advapi32
ELF    68514000-68585000    Deferred        rpcrt4<elf>
  \-PE    68520000-68585000    \               rpcrt4
ELF    68585000-68630000    Deferred        comdlg32<elf>
  \-PE    68590000-68630000    \               comdlg32
ELF    68630000-687c4000    Deferred        shell32<elf>
  \-PE    68640000-687c4000    \               shell32
ELF    687c4000-68823000    Deferred        shlwapi<elf>
  \-PE    687d0000-68823000    \               shlwapi
ELF    68823000-688f1000    Deferred        comctl32<elf>
  \-PE    68830000-688f1000    \               comctl32
ELF    688f1000-6891a000    Deferred        oledlg<elf>
  \-PE    68900000-6891a000    \               oledlg
ELF    6891a000-68a16000    Deferred        ole32<elf>
  \-PE    68930000-68a16000    \               ole32
ELF    68a16000-68afc000    Deferred        oleaut32<elf>
  \-PE    68a30000-68afc000    \               oleaut32
ELF    68afc000-68b2c000    Deferred        libfontconfig.so.1
ELF    68b2c000-68b53000    Deferred        libexpat.so.1
ELF    68b53000-68b5c000    Deferred        libsm.so.6
ELF    68b5c000-68b75000    Deferred        libice.so.6
ELF    68b75000-68b85000    Deferred        libxext.so.6
ELF    68b85000-68ca2000    Deferred        libx11.so.6
ELF    68ca2000-68ca7000    Deferred        libuuid.so.1
ELF    68ca7000-68cc1000    Deferred        libxcb.so.1
ELF    68cc1000-68cc5000    Deferred        libxau.so.6
ELF    68cc5000-68ccb000    Deferred        libxdmcp.so.6
ELF    68ccb000-68cec000    Deferred        imm32<elf>
  \-PE    68cd0000-68cec000    \               imm32
ELF    68cec000-68cf0000    Deferred        libxinerama.so.1
ELF    68cf0000-68cf6000    Deferred        libxxf86vm.so.1
ELF    68cf6000-68d00000    Deferred        libxrender.so.1
ELF    68d00000-68d08000    Deferred        libxrandr.so.2
ELF    68d08000-68d0c000    Deferred        libxcomposite.so.1
ELF    68d0c000-68d12000    Deferred        libxfixes.so.3
ELF    68d12000-68d1c000    Deferred        libxcursor.so.1
ELF    68d1c000-68d4f000    Deferred        uxtheme<elf>
  \-PE    68d20000-68d4f000    \               uxtheme
ELF    68d4f000-68d96000    Deferred        libcups.so.2
ELF    68d96000-68dc5000    Deferred        libgssapi_krb5.so.2
ELF    68dc5000-68e60000    Deferred        libgnutls.so.26
ELF    68e60000-68e71000    Deferred        libavahi-client.so.3
ELF    68e71000-68e95000    Deferred        libk5crypto.so.3
ELF    68e95000-68e99000    Deferred        libcom_err.so.2
ELF    68e99000-68e9d000    Deferred        libkeyutils.so.1
ELF    68e9d000-68eb1000    Deferred        libresolv.so.2
ELF    68eb1000-68ec2000    Deferred        libtasn1.so.3
ELF    68ec2000-68f35000    Deferred        libgcrypt.so.11
ELF    68f35000-68f6e000    Deferred        libdbus-1.so.3
ELF    68f6e000-68f77000    Deferred        librt.so.1
ELF    68f77000-68f7c000    Deferred        libgpg-error.so.0
ELF    69bb6000-69bc2000    Deferred        libavahi-common.so.3
ELF    6b888000-6b89d000    Deferred        libz.so.1
ELF    6d105000-6d1a4000    Deferred        winex11<elf>
  \-PE    6d110000-6d1a4000    \               winex11
ELF    6e9ef000-6eaa0000    Deferred        libkrb5.so.3
ELF    6fe00000-6fe76000    Deferred        libfreetype.so.6
ELF    73e9a000-73ea2000    Deferred        libnss_compat.so.2
ELF    759df000-759e7000    Deferred        libkrb5support.so.0
ELF    79f39000-79f6f000    Deferred        winspool<elf>
  \-PE    79f40000-79f6f000    \               winspool
ELF    7b800000-7b93a000    Deferred        kernel32<elf>
  \-PE    7b810000-7b93a000    \               kernel32
ELF    7bc00000-7bcb6000    Deferred        ntdll<elf>
  \-PE    7bc10000-7bcb6000    \               ntdll
ELF    7bf00000-7bf04000    Deferred        <wine-loader>
Threads:
process  tid      prio (all id:s are in hex)
00000008 (D) Z:\home\student\Desktop\ELORater.exe
    00000009    0 <==
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
=>0 0x0032fd11 (0x683a8440)

```I tried reinstalling Wine.  I tried changing permissions on both files so they're +rwx.  

The most perplexing thing is that I can make it work on an IDENTICALLY CONFIGURED machine.  Any ideas you have would be greatly appreciated.  I'm running 10.04.

---

### Post by afowles on 2010-08-20
Well, it's not a fix, but a work-around. The program doesn't crash if I use a four-letter filename for the ratings file.

---

