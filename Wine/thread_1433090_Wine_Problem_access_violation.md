---
title: "Wine Problem access violation"
date: 2010-03-18
forum: Wine
---

### Post by Silent_Voice on 2010-03-18
Hello, I am trying to install this program through wine but it comes up with a problem  
"access violation at adress 00000000 in module..."

The terminal output is:
err:module:import_dll Library MFC42.DLL (which is needed by L"C:\\windows\\temp\\tmp0DBA.tmp") not found
fixme:reg:GetNativeSystemInfo (0x33fe78) using GetSystemInfo()
fixme:advapi:CheckTokenMembership ((nil) 0x1357f0 0x33fd74) stub!

I've searched in the internet  but I haven't found an actual solution.
I am running on Ubuntu 9.10 and GNOME 2.28.1.
I am not sure if there is any other information needed.. Thank you!

---

### Post by eronisko on 2010-03-18
Maybe the program's name and version would help :)

Have you tried copying it to the "C:" drive and running it from there?

Applications -> Wine -> Browse C:\ Drive

---

### Post by Silent_Voice on 2010-03-18
Oh..right.. :S the program is FL studio 7
I copied to C: but the same error appears..
Thank you for posting

---

### Post by asdfoo on 2010-03-18
You need to install mfc42.dll to do this, open a terminal:

wget kegel.com/wine/winetricks && sh winetricks mfc42

---

### Post by Silent_Voice on 2010-03-19
Yep it worked! Thank you very much!

---

### Post by Silent_Voice on 2010-03-19
Actually I jinxed it :/

Although it was installed normally (except one error but continued the installation)
when i try to open it there is a problem "Runtime error 216 at 01184792". 
I am not sure if it is a wine error or something else. 
Also how do I run it from terminal so I can see the output?

---

### Post by Silent_Voice on 2010-03-20
Anyone ideas?

---

### Post by eronisko on 2010-03-20
Have you been here yet?

[http://appdb.winehq.org/objectManager.php?sClass=version&iId=7036](http://appdb.winehq.org/objectManager.php?sClass=version&iId=7036)

---

### Post by Silent_Voice on 2010-03-20
Yep I 've been but no luck..

---

### Post by Silent_Voice on 2010-03-24
I navigated in the folder where Fl is and run it with "wine FL.exe"
The ooutput was:

wine: Unhandled page fault on read access to 0x0095abf0 at address 0x0000:0x01184792 (thread 0009), starting debugger...
First chance exception: page fault on read access to 0x0095abf0 in 32-bit code (0x01184792).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:01184792 ESP:0032f330 EBP:0032fa30 EFLAGS:00210206(   - 00      - RIP1)
 EAX:0095abf0 EBX:01185302 ECX:00000000 EDX:0032f301
 ESI:00000001 EDI:0032fa14
Stack dump:
0x0032f330:  0118505d 0118530c 00000000 011ade45
0x0032f340:  0095abf0 0032f7b4 0032f370 0032f388
0x0032f350:  0032fa14 00000001 601faff4 601d56b5
0x0032f360:  0032f7b4 0032fa14 0032f4e8 0032f41c
0x0032f370:  0032f80c 601aa8b0 0032fa14 601a39b1
0x0032f380:  6062be00 fffff000 0032f3a8 601d5687
Backtrace:
=>1 0x01184792 in flengine (+0x4792) (0x0032fa30)
  2 0x011853dc in flengine (+0x53dc) (0x0032fa80)
  3 0x601b4635 (0x0032faa0)
  4 0x601b72a3 (0x0032fbe0)
  5 0x601b7be0 (0x0032fc40)
  6 0x601ba891 (0x0032fc80)
  7 0x7b869110 in kernel32 (+0x49110) (0x0032fcd0)
  8 0x7b8691e4 LoadLibraryExW+0x44() in kernel32 (0x0032fd10)
  9 0x7b869313 LoadLibraryExA+0x43() in kernel32 (0x0032fd30)
  10 0x7b86934d LoadLibraryA+0x2d() in kernel32 (0x0032fd50)
  11 0x0040ba0e in fl (+0xba0e) (0x0032fd84)
  12 0x0040fcba in fl (+0xfcba) (0x0032fda8)
  13 0x0040fd37 in fl (+0xfd37) (0x0032feec)
  14 0x004112d7 in fl (+0x112d7) (0x0032ff08)
  15 0x7b877f48 in kernel32 (+0x57f48) (0x0032ffe8)
  16 0x60024b77 wine_switch_to_stack+0x17() in libwine.so.1 (0x00000000)
0x01184792: movl    0x0(%eax),%ecx
Modules:
Module    Address            Debug info    Name (114 modules)
PE      400000-  466000    Export          fl
PE     1180000- 16e4000    Export          flengine
PE    10000000-10039000    Deferred        rewire
ELF    60000000-6001d000    Deferred        ld-linux.so.2
ELF    6001d000-60153000    Export          libwine.so.1
ELF    60153000-6016c000    Deferred        libpthread.so.0
ELF    6016c000-60170000    Deferred        libdl.so.2
PE    60180000-60184000    Deferred        ntdll
ELF    60217000-6023d000    Deferred        libm.so.6
ELF    6023d000-60245000    Deferred        libnss_compat.so.2
ELF    60245000-6025c000    Deferred        libnsl.so.1
ELF    6025c000-60267000    Deferred        libnss_nis.so.2
ELF    60267000-60273000    Deferred        libnss_files.so.2
ELF    60273000-60319000    Deferred        ole32<elf>
  \-PE    60280000-60319000    \               ole32
ELF    60319000-6036b000    Deferred        advapi32<elf>
  \-PE    60330000-6036b000    \               advapi32
ELF    6036b000-604b6000    Deferred        user32<elf>
  \-PE    60390000-604b6000    \               user32
ELF    604b6000-604d5000    Deferred        iphlpapi<elf>
  \-PE    604c0000-604d5000    \               iphlpapi
ELF    604d5000-60554000    Deferred        libfreetype.so.6
ELF    60554000-6056a000    Deferred        libz.so.1
ELF    6056a000-60597000    Deferred        libfontconfig.so.1
ELF    60597000-60631000    Deferred        winex11<elf>
  \-PE    605b0000-60631000    \               winex11
ELF    60631000-6063a000    Deferred        libsm.so.6
ELF    6063a000-60655000    Deferred        libice.so.6
ELF    60655000-6065b000    Deferred        libxxf86vm.so.1
ELF    6065b000-60660000    Deferred        libuuid.so.1
ELF    60660000-60664000    Deferred        libxau.so.6
ELF    60664000-60682000    Deferred        libxcb.so.1
ELF    60682000-60687000    Deferred        libxdmcp.so.6
ELF    60687000-6068a000    Deferred        libxinerama.so.1
ELF    6068a000-60694000    Deferred        libxrender.so.1
ELF    60694000-6069d000    Deferred        libxrandr.so.2
ELF    6069d000-606a1000    Deferred        libxcomposite.so.1
ELF    606a1000-606a7000    Deferred        libxfixes.so.3
ELF    606a7000-606c2000    Deferred        version<elf>
  \-PE    606b0000-606c2000    \               version
ELF    606c2000-606d7000    Deferred        lz32<elf>
  \-PE    606d0000-606d7000    \               lz32
ELF    606d7000-606eb000    Deferred        msimg32<elf>
  \-PE    606e0000-606eb000    \               msimg32
ELF    606eb000-6070e000    Deferred        mpr<elf>
  \-PE    606f0000-6070e000    \               mpr
ELF    6070e000-60745000    Deferred        winspool<elf>
  \-PE    60720000-60745000    \               winspool
ELF    60745000-607a0000    Deferred        shlwapi<elf>
  \-PE    60750000-607a0000    \               shlwapi
ELF    607a0000-607c3000    Deferred        hhctrl<elf>
  \-PE    607b0000-607c3000    \               hhctrl
ELF    607c3000-607c7000    Deferred        libcom_err.so.2
ELF    607c7000-607cb000    Deferred        libkeyutils.so.1
ELF    607cd000-60804000    Deferred        winealsa<elf>
  \-PE    607e0000-60804000    \               winealsa
ELF    60804000-608cb000    Deferred        libasound.so.2
ELF    608cb000-608d4000    Deferred        librt.so.1
ELF    608d4000-60914000    Deferred        libpulse.so.0
ELF    60914000-6095e000    Deferred        libpulsecommon-0.9.19.so
ELF    6095e000-60964000    Deferred        libxtst.so.6
ELF    60964000-6096d000    Deferred        libwrap.so.0
ELF    6096d000-609d9000    Deferred        libsndfile.so.1
ELF    609d9000-60a29000    Deferred        libflac.so.8
ELF    60a29000-60b25000    Deferred        libvorbisenc.so.2
ELF    60b25000-60b4e000    Deferred        libvorbis.so.0
ELF    60b4e000-60b55000    Deferred        libogg.so.0
ELF    60b55000-60b5c000    Deferred        libasound_module_pcm_pulse.so
ELF    60b5c000-60b74000    Deferred        msacm32<elf>
  \-PE    60b60000-60b74000    \               msacm32
ELF    60b74000-60b9c000    Deferred        msacm32<elf>
  \-PE    60b80000-60b9c000    \               msacm32
ELF    60b9c000-60c5f000    Deferred        comctl32<elf>
  \-PE    60ba0000-60c5f000    \               comctl32
ELF    60c5f000-60d73000    Deferred        shell32<elf>
  \-PE    60c70000-60d73000    \               shell32
ELF    60d73000-60e21000    Deferred        comdlg32<elf>
  \-PE    60d80000-60e21000    \               comdlg32
ELF    60e21000-60e54000    Deferred        uxtheme<elf>
  \-PE    60e30000-60e54000    \               uxtheme
ELF    60e54000-60e7e000    Deferred        libgssapi_krb5.so.2
ELF    60e7e000-60f26000    Deferred        libgnutls.so.26
ELF    60f26000-60f32000    Deferred        libavahi-common.so.3
ELF    60f32000-60f43000    Deferred        libavahi-client.so.3
ELF    60f43000-60fe9000    Deferred        libkrb5.so.3
ELF    60fe9000-61012000    Deferred        libk5crypto.so.3
ELF    61012000-6101a000    Deferred        libkrb5support.so.0
ELF    6101a000-6102c000    Deferred        libtasn1.so.3
ELF    6102c000-61031000    Deferred        libgpg-error.so.0
ELF    632f7000-63426000    Deferred        libx11.so.6
ELF    63523000-6359f000    Deferred        libgcrypt.so.11
ELF    666e7000-666fb000    Deferred        libresolv.so.2
ELF    6a83b000-6a84b000    Deferred        libxext.so.6
ELF    6ad3c000-6ade2000    Deferred        oleaut32<elf>
  \-PE    6ad50000-6ade2000    \               oleaut32
ELF    6d986000-6d99c000    Deferred        midimap<elf>
  \-PE    6d990000-6d99c000    \               midimap
ELF    6f335000-6f356000    Deferred        imm32<elf>
  \-PE    6f340000-6f356000    \               imm32
ELF    701ed000-701f8000    Deferred        libxcursor.so.1
ELF    70887000-7091b000    Deferred        winmm<elf>
  \-PE    70890000-7091b000    \               winmm
ELF    711ca000-711f1000    Deferred        libexpat.so.1
ELF    732e5000-73384000    Deferred        gdi32<elf>
  \-PE    73300000-73384000    \               gdi32
ELF    76e6f000-76ea8000    Deferred        libdbus-1.so.3
ELF    78503000-78566000    Deferred        rpcrt4<elf>
  \-PE    78510000-78566000    \               rpcrt4
ELF    79d41000-79d87000    Deferred        libcups.so.2
ELF    7b800000-7b93c000    Export          kernel32<elf>
  \-PE    7b820000-7b93c000    \               kernel32
ELF    7bac7000-7bc0c000    Deferred        libc.so.6
ELF    7bc00000-7bca7000    Deferred        ntdll<elf>
ELF    7bf00000-7bf04000    Deferred        <wine-loader>
Threads:
process  tid      prio (all id:s are in hex)
00000008 (D) C:\Program Files\Image-Line\FL Studio 7\FL.exe
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
=>1 0x01184792 in flengine (+0x4792) (0x0032fa30)
  2 0x011853dc in flengine (+0x53dc) (0x0032fa80)
  3 0x601b4635 (0x0032faa0)
  4 0x601b72a3 (0x0032fbe0)
  5 0x601b7be0 (0x0032fc40)
  6 0x601ba891 (0x0032fc80)
  7 0x7b869110 in kernel32 (+0x49110) (0x0032fcd0)
  8 0x7b8691e4 LoadLibraryExW+0x44() in kernel32 (0x0032fd10)
  9 0x7b869313 LoadLibraryExA+0x43() in kernel32 (0x0032fd30)
  10 0x7b86934d LoadLibraryA+0x2d() in kernel32 (0x0032fd50)
  11 0x0040ba0e in fl (+0xba0e) (0x0032fd84)
  12 0x0040fcba in fl (+0xfcba) (0x0032fda8)
  13 0x0040fd37 in fl (+0xfd37) (0x0032feec)
  14 0x004112d7 in fl (+0x112d7) (0x0032ff08)
  15 0x7b877f48 in kernel32 (+0x57f48) (0x0032ffe8)
  16 0x60024b77 wine_switch_to_stack+0x17() in libwine.so.1 (0x00000000)

Any ideas?

---

### Post by asdfoo on 2010-03-24
could be copy protection related, iirc FL studio is packed with a particular copy protection that does not work with wine

later versions of fl studio use an updated copy protection which does work with wine

check out the appdb for more information or ask there

---

