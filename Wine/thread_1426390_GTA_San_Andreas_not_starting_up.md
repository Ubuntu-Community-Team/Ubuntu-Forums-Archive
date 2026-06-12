---
title: "GTA San Andreas not starting up"
date: 2010-03-10
forum: Wine
---

### Post by sportspool7 on 2010-03-10
**GTA San Andreas not starting up** 
When I run the game from the terminal and post Wine's terminal output here, it explain to me like this:
 
Code:
fixme:system:SystemParametersInfoW Unimplemented action: 8193 (SPI_SETFOREGROUNDLOCKTIMEOUT)
wine: Unhandled page fault on read access to 0x00000000 at address 0x746929 (thread 0034), starting debugger...
Unhandled exception: page fault on read access to 0x00000000 in 32-bit code (0x00746929).
err:dbghelp_msc:codeview_process_info Unknown CODEVIEW signature 088d8601 in module L"gta_sa"
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:00746929 ESP:0177fd58 EBP:0177ff08 EFLAGS:00210246(   - 00      -RIZP1)
 EAX:00000000 EBX:00000000 ECX:00000000 EDX:0000057f
 ESI:00000000 EDI:7b868100
Stack dump:
0x0177fd58:  00748732 7b8b6ff4 010e0000 00400000
0x0177fd68:  00828cb3 00856c80 7bc3313f 7b8b6ff4
0x0177fd78:  00000002 0177fdd4 0177fdb0 7b8680af
0x0177fd88:  00000002 00000000 0177fdd4 00c9ad08
0x0177fd98:  0177fdd4 00823b3e 00000008 7b8b6ff4
0x0177fda8:  00000000 7b868100 0177fde0 7b86812c
Backtrace:
=>1 0x00746929 in gta_sa (+0x346929) (0x0177ff0:cool:
  2 0x7b877f48 in kernel32 (+0x57f4:cool: (0x0177ffe:cool:
  3 0x60024b77 wine_switch_to_stack+0x17() in libwine.so.1 (0x00000000)
0x00746929: movl    0x0(%eax),%ecx
Modules:
Module    Address            Debug info    Name (81 modules)
PE      230000-  239000    Deferred        ogg
PE      240000-  348000    Deferred        vorbis
PE      350000-  380000    Deferred        eax
PE      400000- 1577000    Export          gta_sa
PE    10000000-10011000    Deferred        vorbisfile
ELF    60000000-6001d000    Deferred        ld-linux.so.2
ELF    6001d000-60153000    Export          libwine.so.1
ELF    60153000-6016c000    Deferred        libpthread.so.0
ELF    6016c000-60170000    Deferred        libdl.so.2
ELF    60170000-60196000    Deferred        libm.so.6
ELF    60196000-601ad000    Deferred        libnsl.so.1
ELF    601ad000-601b8000    Deferred        libnss_nis.so.2
ELF    601b8000-601c4000    Deferred        libnss_files.so.2
ELF    601c4000-6030f000    Deferred        user32<elf>
  \-PE    601e0000-6030f000    \               user32
ELF    6030f000-60361000    Deferred        advapi32<elf>
  \-PE    60320000-60361000    \               advapi32
ELF    60361000-60375000    Deferred        libresolv.so.2
ELF    60375000-603d8000    Deferred        rpcrt4<elf>
  \-PE    60380000-603d8000    \               rpcrt4
ELF    603d8000-60405000    Deferred        libfontconfig.so.1
ELF    60405000-6040a000    Deferred        libuuid.so.1
ELF    6040b000-604aa000    Deferred        gdi32<elf>
  \-PE    60420000-604aa000    \               gdi32
ELF    604aa000-60550000    Deferred        ole32<elf>
  \-PE    604c0000-60550000    \               ole32
ELF    60550000-605ea000    Deferred        winex11<elf>
  \-PE    60560000-605ea000    \               winex11
ELF    605ea000-605f3000    Deferred        libsm.so.6
ELF    605f3000-60603000    Deferred        libxext.so.6
ELF    60603000-60732000    Deferred        libx11.so.6
ELF    60732000-60750000    Deferred        libxcb.so.1
ELF    60750000-60755000    Deferred        libxdmcp.so.6
ELF    60755000-60776000    Deferred        imm32<elf>
  \-PE    60760000-60776000    \               imm32
ELF    60776000-60779000    Deferred        libxinerama.so.1
ELF    60779000-60783000    Deferred        libxrender.so.1
ELF    60783000-6078c000    Deferred        libxrandr.so.2
ELF    6078c000-60790000    Deferred        libxcomposite.so.1
ELF    60790000-60796000    Deferred        libxfixes.so.3
ELF    60796000-607cd000    Deferred        winealsa<elf>
  \-PE    607a0000-607cd000    \               winealsa
ELF    607cd000-60894000    Deferred        libasound.so.2
ELF    60894000-6089d000    Deferred        librt.so.1
ELF    608a0000-608e0000    Deferred        libpulse.so.0
ELF    608e0000-608e6000    Deferred        libxtst.so.6
ELF    608e6000-608ef000    Deferred        libwrap.so.0
ELF    608ef000-6095b000    Deferred        libsndfile.so.1
ELF    6095b000-60994000    Deferred        libdbus-1.so.3
ELF    60994000-609e4000    Deferred        libflac.so.8
ELF    609e4000-60ae0000    Deferred        libvorbisenc.so.2
ELF    60ae0000-60b09000    Deferred        libvorbis.so.0
ELF    60b09000-60b10000    Deferred        libogg.so.0
ELF    60b10000-60b28000    Deferred        msacm32<elf>
  \-PE    60b20000-60b28000    \               msacm32
ELF    60b28000-60b3e000    Deferred        midimap<elf>
  \-PE    60b30000-60b3e000    \               midimap
ELF    65f56000-65f6c000    Deferred        libz.so.1
ELF    664e8000-6650f000    Deferred        libexpat.so.1
ELF    6a900000-6a928000    Deferred        msacm32<elf>
  \-PE    6a910000-6a928000    \               msacm32
ELF    6ba25000-6ba6f000    Deferred        libpulsecommon-0.9.19.so
ELF    6c08f000-6c10e000    Deferred        libfreetype.so.6
ELF    6d91f000-6d925000    Deferred        libxxf86vm.so.1
ELF    6de57000-6de72000    Deferred        libice.so.6
ELF    6f311000-6f456000    Deferred        libc.so.6
ELF    6f510000-6f53d000    Deferred        ws2_32<elf>
  \-PE    6f520000-6f53d000    \               ws2_32
ELF    6fe35000-6fe3c000    Deferred        libasound_module_pcm_pulse.so
ELF    726fb000-7271a000    Deferred        iphlpapi<elf>
  \-PE    72700000-7271a000    \               iphlpapi
ELF    77e4c000-77e57000    Deferred        libxcursor.so.1
ELF    7931f000-793b3000    Deferred        winmm<elf>
  \-PE    79330000-793b3000    \               winmm
ELF    7b555000-7b559000    Deferred        libxau.so.6
ELF    7b800000-7b93c000    Export          kernel32<elf>
  \-PE    7b820000-7b93c000    \               kernel32
ELF    7bc00000-7bca7000    Deferred        ntdll<elf>
  \-PE    7bc10000-7bca7000    \               ntdll
ELF    7bf00000-7bf04000    Deferred        <wine-loader>
ELF    7c01d000-7c025000    Deferred        libnss_compat.so.2
Threads:
process  tid      prio (all id:s are in hex)
00000008 
    00000009    0
0000000c 
    00000012    0
    0000000e    0
    0000000d    0
0000000f 
    00000015    0
    00000014    0
    00000011    0
    00000010    0
00000018 
    00000019    0
00000032 (D) C:\Game\GTA-SanAndreas\gta_sa.exe
    00000034    0 <==
Backtrace:
=>1 0x00746929 in gta_sa (+0x346929) (0x0177ff0:cool:
  2 0x7b877f48 in kernel32 (+0x57f4:cool: (0x0177ffe:cool:
  3 0x60024b77 wine_switch_to_stack+0x17() in libwine.so.1 (0x00000000)
err:seh:raise_exception Unhandled exception code c0000005 flags 0 addr 0x746929

somebody can fix this problems?
I using Ubuntu 9.10

---

### Post by asdfoo on 2010-03-10
you don't say which version of Wine you are using so I am going to suggest 1.1.40.

---

### Post by sportspool7 on 2010-03-11
My version Wine is 1.0.1 and how to get version Wine 1.1.40?

---

### Post by sportspool7 on 2010-03-11
I have been able to Wine 1.1.40 and when I run the game GTA SA, out of a problem like this: 
 The program gta_sa.exe has encountered a serious problem and needs to close. We are sorry for the inconvenience.

Someboy can help me?????????

---

### Post by asdfoo on 2010-03-12
first of all, stop opening multiple threads for the same problem.

This may be an issue with copy protection - testing with a nocd patch would be one way to verify this.

---

### Post by sportspool7 on 2010-03-12
Ok thanks your information and I have tried with no cd patch but still no working. It is still showing :

'Program error message'

I using ubuntu 9.10 and wine 1.1.40

---

### Post by asdfoo on 2010-03-12
> **sportspool7 said:**
> Ok thanks your information and I have tried with no cd patch but still no working. It is still showing :

'Program error message'

I using ubuntu 9.10 and wine 1.1.40

when the error message appears, click ok and then can you paste the information from the terminal?

---

### Post by sportspool7 on 2010-03-12
> **asdfoo said:**
> when the error message appears, click ok and then can you paste the information from the terminal?

What do you means? I can't understand. It is showing :

[IMG]http:///home/mhf07/Desktop/Screenshot.jpeg[/IMG]

---

### Post by bhaveshnande on 2010-10-29
I got the same problem.. It says serious error and shows that box. 
Some please help us.

---

### Post by bobwyajnr on 2010-10-29
> **bhaveshnande said:**
> I got the same problem.. It says serious error and shows that box. 
Some please help us.

I've got GTA San Andreas working with WINE 1.3.5. But that is the Steam version. If you are using the Steam version (or probably also with a retail version and no-CD crack) then I found that the game was stopping with that error popup because the codecs for playing the intro movies weren't supported/registered.

I know there are some developer patches floating about this. However I got the intro movies to work by going to town with Winetricks (using .dll overrides for quartz, devenum.dll,
etc.)

Appears to run OK. Not sure if the latest release (1.3.6) fixes the need for codec .dll overrides yet (there is some mention of GStreamer additions)...

A link to my test submission for WINE 1.3.5:
[WineHQ AppDB : GTA San Andreas (Steam)]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=15325")

Bob

---

