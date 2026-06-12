---
title: "Configure wine cannot work at all"
date: 2009-12-08
forum: Wine
---

### Post by jetwolf on 2009-12-08
I just installed wine, but cannot open configure wine at all.(click it, but doesn't work)  Even I use winecfg under terminal mode, it appears information as follows

ALSA lib pcm_dmix.c:874:(snd_pcm_dmix_open) unable to open slave
fixme:shell:MLSetMLHInstance (0x71590000,0x7ea80000) stub
fixme:mlang:GetGlobalFontLinkObject 
wine: Unhandled page fault on read access to 0x00000004 at address 0x4 (thread 0009), starting debugger...
Unhandled exception: page fault on read access to 0x00000004 in 32-bit code (0x00000004).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:00000004 ESP:0032ec54 EBP:0032ec9c EFLAGS:00210246(  R- --  I  Z- -P- )
 EAX:00000000 EBX:00000002 ECX:715f4028 EDX:715f402c
 ESI:0032eddc EDI:0032ec98
Stack dump:
0x0032ec54:  0032ec98 715ad67d 0032ec98 0032eddc
0x0032ec64:  00000004 00000002 7ea17e64 7e4038bc
0x0032ec74:  7c02f348 b7da8a0c 0032ecac 7e3f3c91
0x0032ec84:  00000001 00000000 0032eca4 00000000
0x0032ec94:  7c02f348 00000000 0032edc0 715934a2
0x0032eca4:  00000250 0032eddc 00000004 0032ef04
Backtrace:
=>0 0x00000004 (0x0032ec9c)
err:dbghelp:pe_load_dbg_file Couldn't find .DBG file "COMCTL32.dbg" ("")
  1 0x715934a2 in comctl32 (+0x34a2) (0x0032edc0)
  2 0x715b44af in comctl32 (+0x244af) (0x0032eedc)
  3 0x71592514 in comctl32 (+0x2514) (0x0032ef2c)
  4 0x71592a71 in comctl32 (+0x2a71) (0x0032ef58)
  5 0x715920b7 in comctl32 (+0x20b7) (0x0032ef94)
  6 0x7eaf07ea WINPROC_wrapper+0x1a() in user32 (0x0032efc4)
  7 0x7eaf0eae WINPROC_wrapper+0x6de() in user32 (0x0032f004)
  8 0x7eaf61db in user32 (+0xb61db) (0x0032f044)
  9 0x7eab7ef1 in user32 (+0x77ef1) (0x0032f0a4)
  10 0x7eabc2cd in user32 (+0x7c2cd) (0x0032f104)
  11 0x7eabc73a SendMessageW+0x4a() in user32 (0x0032f144)
  12 0x715b3b4f in comctl32 (+0x23b4f) (0x0032f4d4)
  13 0x715b25dc in comctl32 (+0x225dc) (0x0032f538)
  14 0x7eaf07ea WINPROC_wrapper+0x1a() in user32 (0x0032f568)
  15 0x7eaf2538 in user32 (+0xb2538) (0x0032f5a8)
  16 0x7eaf5f43 in user32 (+0xb5f43) (0x0032f5e8)
  17 0x7ea818d1 DefDlgProcW+0x81() in user32 (0x0032f618)
  18 0x7eaf07ea WINPROC_wrapper+0x1a() in user32 (0x0032f648)
  19 0x7eaf0eae WINPROC_wrapper+0x6de() in user32 (0x0032f688)
  20 0x7eaf61db in user32 (+0xb61db) (0x0032f6c8)
  21 0x7eab7ef1 in user32 (+0x77ef1) (0x0032f728)
  22 0x7eabc2cd in user32 (+0x7c2cd) (0x0032f788)
  23 0x7eabc73a SendMessageW+0x4a() in user32 (0x0032f7c8)
  24 0x7ea8720e in user32 (+0x4720e) (0x0032fb58)
  25 0x7ea88546 CreateDialogIndirectParamAorW+0x36() in user32 (0x0032fb78)
  26 0x7ea88591 CreateDialogIndirectParamW+0x41() in user32 (0x0032fba8)
  27 0x715b3878 in comctl32 (+0x23878) (0x0032fbcc)
  28 0x715b3666 in comctl32 (+0x23666) (0x0032fc34)
  29 0x715b34c9 in comctl32 (+0x234c9) (0x0032fc4c)
  30 0x715b33b3 in comctl32 (+0x233b3) (0x0032fe08)
  31 0x7ee270e5 main+0xa5() in winecfg (0x0032fe88)
  32 0x7ee27007 in winecfg (+0x17007) (0x0032feb8)
  33 0x7b8753c5 in kernel32 (+0x553c5) (0x0032fee8)
  34 0x7bc6b204 call_thread_func+0xc() in ntdll (0x0032fef8)
  35 0x7bc6d311 in ntdll (+0x5d311) (0x0032ffc8)
  36 0x7bc484ca in ntdll (+0x384ca) (0x0032ffe8)
0x00000004: -- no code accessible --
Modules:
Module	Address			Debug info	Name (93 modules)
PE	71590000-71617000	Export          comctl32
ELF	7b800000-7b96e000	Export          kernel32<elf>
  \-PE	7b820000-7b96e000	\               kernel32
ELF	7bc00000-7bcb0000	Export          ntdll<elf>
  \-PE	7bc10000-7bcb0000	\               ntdll
ELF	7bf00000-7bf03000	Deferred        <wine-loader>
ELF	7cb80000-7cba3000	Deferred        mlang<elf>
  \-PE	7cb90000-7cba3000	\               mlang
ELF	7cba3000-7cbb7000	Deferred        midimap<elf>
  \-PE	7cbb0000-7cbb7000	\               midimap
ELF	7cbb7000-7cbdc000	Deferred        msacm32<elf>
  \-PE	7cbc0000-7cbdc000	\               msacm32
ELF	7cbdc000-7cbf3000	Deferred        msacm32<elf>
  \-PE	7cbe0000-7cbf3000	\               msacm32
ELF	7cbf3000-7ccb6000	Deferred        libasound.so.2
ELF	7ccb6000-7ccec000	Deferred        winealsa<elf>
  \-PE	7ccc0000-7ccec000	\               winealsa
ELF	7ccec000-7ccf0000	Deferred        libgpg-error.so.0
ELF	7ccf0000-7cd3d000	Deferred        libgcrypt.so.11
ELF	7cd3d000-7cd4d000	Deferred        libtasn1.so.3
ELF	7cd4d000-7cd60000	Deferred        libresolv.so.2
ELF	7cd60000-7cd63000	Deferred        libkeyutils.so.1
ELF	7cd63000-7cd95000	Deferred        libcrypt.so.1
ELF	7cd95000-7ce0b000	Deferred        libgnutls.so.13
ELF	7ce0b000-7ce2e000	Deferred        libk5crypto.so.3
ELF	7ce2e000-7cebb000	Deferred        libkrb5.so.3
ELF	7cebb000-7cee4000	Deferred        libgssapi_krb5.so.2
ELF	7cee4000-7cf17000	Deferred        libcups.so.2
ELF	7cf27000-7cf3f000	Deferred        spoolss<elf>
  \-PE	7cf30000-7cf3f000	\               spoolss
ELF	7cf3f000-7cf5e000	Deferred        localspl<elf>
  \-PE	7cf40000-7cf5e000	\               localspl
ELF	7e3a0000-7e3a9000	Deferred        libxcursor.so.1
ELF	7e3a9000-7e3ae000	Deferred        libxfixes.so.3
ELF	7e3ae000-7e3b1000	Deferred        libxcomposite.so.1
ELF	7e3b1000-7e3b7000	Deferred        libxrandr.so.2
ELF	7e3b7000-7e3bf000	Deferred        libxrender.so.1
ELF	7e3bf000-7e3c4000	Deferred        libxxf86vm.so.1
ELF	7e3c4000-7e3c7000	Deferred        libxinerama.so.1
ELF	7e3c7000-7e3e7000	Deferred        imm32<elf>
  \-PE	7e3d0000-7e3e7000	\               imm32
ELF	7e3e7000-7e3ec000	Deferred        libxdmcp.so.6
ELF	7e3ec000-7e404000	Deferred        libxcb.so.1
ELF	7e404000-7e406000	Deferred        libxcb-xlib.so.0
ELF	7e406000-7e409000	Deferred        libxau.so.6
ELF	7e409000-7e4f0000	Deferred        libx11.so.6
ELF	7e4f0000-7e4fe000	Deferred        libxext.so.6
ELF	7e4fe000-7e516000	Deferred        libice.so.6
ELF	7e516000-7e51e000	Deferred        libsm.so.6
ELF	7e51f000-7e527000	Deferred        libkrb5support.so.0
ELF	7e527000-7e52a000	Deferred        libcom_err.so.2
ELF	7e52e000-7e5c9000	Deferred        winex11<elf>
  \-PE	7e540000-7e5c9000	\               winex11
ELF	7e5e3000-7e604000	Deferred        libexpat.so.1
ELF	7e604000-7e62e000	Deferred        libfontconfig.so.1
ELF	7e63e000-7e653000	Deferred        libz.so.1
ELF	7e653000-7e6c0000	Deferred        libfreetype.so.6
ELF	7e6d0000-7e6e4000	Deferred        system.drv16.so
PE	7e6e0000-7e6e4000	Deferred        system.drv16
ELF	7e6e4000-7e717000	Deferred        uxtheme<elf>
  \-PE	7e6f0000-7e717000	\               uxtheme
ELF	7e717000-7e79c000	Deferred        winmm<elf>
  \-PE	7e720000-7e79c000	\               winmm
ELF	7e79c000-7e808000	Deferred        rpcrt4<elf>
  \-PE	7e7b0000-7e808000	\               rpcrt4
ELF	7e808000-7e900000	Deferred        ole32<elf>
  \-PE	7e820000-7e900000	\               ole32
ELF	7e900000-7e933000	Deferred        winspool<elf>
  \-PE	7e910000-7e933000	\               winspool
ELF	7e933000-7e98a000	Deferred        advapi32<elf>
  \-PE	7e940000-7e98a000	\               advapi32
ELF	7e98a000-7ea29000	Deferred        gdi32<elf>
  \-PE	7e9a0000-7ea29000	\               gdi32
ELF	7ea29000-7eb6e000	Export          user32<elf>
  \-PE	7ea40000-7eb6e000	\               user32
ELF	7eb6e000-7ebc9000	Deferred        shlwapi<elf>
  \-PE	7eb80000-7ebc9000	\               shlwapi
ELF	7ebc9000-7ed58000	Deferred        shell32<elf>
  \-PE	7ebe0000-7ed58000	\               shell32
ELF	7ed58000-7ee02000	Deferred        comdlg32<elf>
  \-PE	7ed60000-7ee02000	\               comdlg32
ELF	7ee02000-7ee88000	Export          winecfg<elf>
  \-PE	7ee10000-7ee88000	\               winecfg
ELF	7efa8000-7efb3000	Deferred        libnss_files.so.2
ELF	7efb3000-7efcb000	Deferred        libnsl.so.1
ELF	7efcb000-7eff0000	Deferred        libm.so.6
ELF	7eff6000-7f000000	Deferred        libnss_nis.so.2
ELF	b7c42000-b7c4b000	Deferred        libnss_compat.so.2
ELF	b7c4c000-b7c50000	Deferred        libdl.so.2
ELF	b7c50000-b7d9f000	Deferred        libc.so.6
ELF	b7da0000-b7db8000	Deferred        libpthread.so.0
ELF	b7dc8000-b7f03000	Deferred        libwine.so.1
ELF	b7f05000-b7f21000	Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
00000008 (D) C:\windows\system32\winecfg.exe
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
=>0 0x00000004 (0x0032ec9c)
  1 0x715934a2 in comctl32 (+0x34a2) (0x0032edc0)
  2 0x715b44af in comctl32 (+0x244af) (0x0032eedc)
  3 0x71592514 in comctl32 (+0x2514) (0x0032ef2c)
  4 0x71592a71 in comctl32 (+0x2a71) (0x0032ef58)
  5 0x715920b7 in comctl32 (+0x20b7) (0x0032ef94)
  6 0x7eaf07ea WINPROC_wrapper+0x1a() in user32 (0x0032efc4)
  7 0x7eaf0eae WINPROC_wrapper+0x6de() in user32 (0x0032f004)
  8 0x7eaf61db in user32 (+0xb61db) (0x0032f044)
  9 0x7eab7ef1 in user32 (+0x77ef1) (0x0032f0a4)
  10 0x7eabc2cd in user32 (+0x7c2cd) (0x0032f104)
  11 0x7eabc73a SendMessageW+0x4a() in user32 (0x0032f144)
  12 0x715b3b4f in comctl32 (+0x23b4f) (0x0032f4d4)
  13 0x715b25dc in comctl32 (+0x225dc) (0x0032f538)
  14 0x7eaf07ea WINPROC_wrapper+0x1a() in user32 (0x0032f568)
  15 0x7eaf2538 in user32 (+0xb2538) (0x0032f5a8)
  16 0x7eaf5f43 in user32 (+0xb5f43) (0x0032f5e8)
  17 0x7ea818d1 DefDlgProcW+0x81() in user32 (0x0032f618)
  18 0x7eaf07ea WINPROC_wrapper+0x1a() in user32 (0x0032f648)
  19 0x7eaf0eae WINPROC_wrapper+0x6de() in user32 (0x0032f688)
  20 0x7eaf61db in user32 (+0xb61db) (0x0032f6c8)
  21 0x7eab7ef1 in user32 (+0x77ef1) (0x0032f728)
  22 0x7eabc2cd in user32 (+0x7c2cd) (0x0032f788)
  23 0x7eabc73a SendMessageW+0x4a() in user32 (0x0032f7c8)
  24 0x7ea8720e in user32 (+0x4720e) (0x0032fb58)
  25 0x7ea88546 CreateDialogIndirectParamAorW+0x36() in user32 (0x0032fb78)
  26 0x7ea88591 CreateDialogIndirectParamW+0x41() in user32 (0x0032fba8)
  27 0x715b3878 in comctl32 (+0x23878) (0x0032fbcc)
  28 0x715b3666 in comctl32 (+0x23666) (0x0032fc34)
  29 0x715b34c9 in comctl32 (+0x234c9) (0x0032fc4c)
  30 0x715b33b3 in comctl32 (+0x233b3) (0x0032fe08)
  31 0x7ee270e5 main+0xa5() in winecfg (0x0032fe88)
  32 0x7ee27007 in winecfg (+0x17007) (0x0032feb8)
  33 0x7b8753c5 in kernel32 (+0x553c5) (0x0032fee8)
  34 0x7bc6b204 call_thread_func+0xc() in ntdll (0x0032fef8)
  35 0x7bc6d311 in ntdll (+0x5d311) (0x0032ffc8)
  36 0x7bc484ca in ntdll (+0x384ca) (0x0032ffe8)


can anyone give me some idea about how to solve this problem ?

by the way, the version I used is 1.1.33

---

