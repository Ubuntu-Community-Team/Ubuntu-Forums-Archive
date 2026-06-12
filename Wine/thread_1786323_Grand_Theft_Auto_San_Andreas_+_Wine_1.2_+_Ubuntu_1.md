---
title: "Grand Theft Auto: San Andreas + Wine 1.2 + Ubuntu 11.04"
date: 2011-06-19
forum: Wine
---

### Post by piccoli on 2011-06-19
Hello. I have recently decided to change from Windows to Ubuntu, given that I will be able to run most of what Windows has to offer (via Wine) on Ubuntu. Even though I am still getting used to doing things via command line in Ubuntu, I think that it will be better than Windows in many ways...

I like gaming, and one of the problems I am currently having is that I cannot seem to get Grand Theft Auto: San Andreas to work properly with Wine and Ubuntu. I am still learning Ubuntu and where to find things, so please go easy on me! I have the retail copy of the game, but a no-CD patch for the "gta_sa.exe" file (it's easier, plus I read somewhere that it's better to run a cracked game with Wine). Every time I go to run Wine (even with the smallest programs) it gives me this message; "The program *winemenubuilder.exe* has encountered an error and needs to close." When I attempt to load *gta_sa.exe*, the game opens but the game window will remain black and I can't do anything. With all other programs, the error appears and the program freezes.

Could someone enlighten me?

---

### Post by That Nerd 2049 on 2011-06-19
Try opening it though the console and see if it gives some more informative error output.
Without the quotes.
"cd /path to app directory/"
enter
"wine gta_sa.exe"

I also looked up winemenubuilder.exe on Wine FAQ and found that you can disable it but if you do it will not change filetype associations, add menu items, or create desktop links.

[http://wiki.winehq.org/FAQ](http://wiki.winehq.org/FAQ)

Just Search for winemenubuilder.exe

I hope this helps.

---

### Post by piccoli on 2011-06-19
> **That Nerd 2049 said:**
> Try opening it though the console and see if it gives some more informative error output.
Without the quotes.
"cd /path to app directory/"
enter
"wine gta_sa.exe"

I also looked up winemenubuilder.exe on Wine FAQ and found that you can disable it but if you do it will not change filetype associations, add menu items, or create desktop links.

[http://wiki.winehq.org/FAQ](http://wiki.winehq.org/FAQ)

Just Search for winemenubuilder.exe

I hope this helps.

Okay, I can give that a try. One problem, the directory path has directory names with spaces in them, giving me this; "No such file or directory." Is there any way around it?

---

### Post by That Nerd 2049 on 2011-06-19
Try these:

cd "path to app directory"

cd 'path to app directory'

Source: [bash-script-to-cd-to-directory-with-spaces-in-pathname]("http://stackoverflow.com/questions/589149/bash-script-to-cd-to-directory-with-spaces-in-pathname")

See if they work.

---

### Post by piccoli on 2011-06-19
> **That Nerd 2049 said:**
> Try these:

cd "path to app directory"

cd 'path to app directory'

Source: [bash-script-to-cd-to-directory-with-spaces-in-pathname]("http://stackoverflow.com/questions/589149/bash-script-to-cd-to-directory-with-spaces-in-pathname")

See if they work.

Okay, got it working by using a *\* before each space. As for the original problem, this is what the terminal window produced:

```
wine: cannot find L"C:\\windows\\system32\\plugplay.exe"
wine: Unhandled page fault on read access to 0x0041b008 at address 0x681ca9f0 (thread 000d), starting debugger...
fixme:d3d_caps:select_card_intel_mesa Card selection not handled for Mesa Intel driver
fixme:d3d_caps:init_driver_info Unhandled vendor 8086.
fixme:win:EnumDisplayDevicesW ((null),0,0x177f494,0x00000000), stub!
fixme:d3d_caps:select_card_intel_mesa Card selection not handled for Mesa Intel driver
fixme:d3d_caps:init_driver_info Unhandled vendor 8086.
fixme:win:EnumDisplayDevicesW ((null),0,0x177f484,0x00000000), stub!
fixme:dsalsa:IDsDriverBufferImpl_SetVolumePan (0x12b980,0x136f38): stub
fixme:d3d_caps:select_card_intel_mesa Card selection not handled for Mesa Intel driver
fixme:d3d_caps:init_driver_info Unhandled vendor 8086.
fixme:win:EnumDisplayDevicesW ((null),0,0x177f10c,0x00000000), stub!
fixme:d3d_caps:select_card_intel_mesa Card selection not handled for Mesa Intel driver
fixme:d3d_caps:init_driver_info Unhandled vendor 8086.
fixme:win:EnumDisplayDevicesW ((null),0,0x177f5a4,0x00000000), stub!
fixme:system:SystemParametersInfoW Unimplemented action: 59 (SPI_SETSTICKYKEYS)
fixme:d3d:state_clipping Clipping disabled, but ARB_depth_clamp isn't supported.
fixme:d3d:state_clipping Clipping disabled, but ARB_depth_clamp isn't supported.
fixme:d3d:state_clipping Clipping disabled, but ARB_depth_clamp isn't supported.
err:avicap:query_video_device Video 4 Linux support not enabled
err:avicap:query_video_device Video 4 Linux support not enabled
err:avicap:query_video_device Video 4 Linux support not enabled
err:avicap:query_video_device Video 4 Linux support not enabled
err:avicap:query_video_device Video 4 Linux support not enabled
err:avicap:query_video_device Video 4 Linux support not enabled
err:avicap:query_video_device Video 4 Linux support not enabled
err:avicap:query_video_device Video 4 Linux support not enabled
err:avicap:query_video_device Video 4 Linux support not enabled
err:avicap:query_video_device Video 4 Linux support not enabled
err:ole:COMPOBJ_DllList_Add couldn't load in-process dll L"C:\\windows\\system32\\winegstreamer.dll"
err:ole:CoGetClassObject no class object {f9d8d64e-a144-47dc-8ee0-f53498372c29} could be created for context 0x1
fixme:quartz:MPEGSplitter_query_accept MPEG-1 system streams not yet supported.
err:ole:COMPOBJ_DllList_Add couldn't load in-process dll L"C:\\windows\\system32\\winegstreamer.dll"
err:ole:CoGetClassObject no class object {f9d8d64e-a144-47dc-8ee0-f53498372c29} could be created for context 0x1
fixme:quartz:MPEGSplitter_query_accept MPEG-1 system streams not yet supported.
wine: Unhandled page fault on read access to 0x00000024 at address 0x4dd5a3 (thread 0009), starting debugger...
Unhandled exception: page fault on read access to 0x0041b008 in 32-bit code (0x681ca9f0).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:681ca9f0 ESP:0033fbb8 EBP:0033fc20 EFLAGS:00210283(  R- --  I S - - -C)
 EAX:0041affc EBX:681d7ff4 ECX:0000fe01 EDX:00000797
 ESI:00000000 EDI:0000c188
Stack dump:
0x0033fbb8:  004145c8 00418c90 681c7f50 0033fbfc
0x0033fbc8:  00000000 0012e018 00000028 00110014
0x0033fbd8:  00000028 004145c8 0012e018 0000c188
0x0033fbe8:  0000fe01 000009e4 0000ffff 003d0001
0x0033fbf8:  00110000 0033fc04 ffffffff 00418c90
0x0033fc08:  0012d810 681d2a64 681ca90d 681d7ff4
Backtrace:
=>0 0x681ca9f0 in winemenubuilder (+0xa9f0) (0x0033fc20)
  1 0x681cc76e in winemenubuilder (+0xc76d) (0x0033fcb0)
  2 0x681d0960 wWinMain+0x23cf() in winemenubuilder (0x0033fde0)
  3 0x681d1351 wmain+0xb0() in winemenubuilder (0x0033fe60)
  4 0x681d1292 in winemenubuilder (+0x11291) (0x0033fe90)
  5 0x7b85437c call_process_entry+0xb() in kernel32 (0x0033fea8)
  6 0x7b85501f ExitProcess+0xc9e() in kernel32 (0x0033fee8)
  7 0x7bc70be0 call_thread_func+0xb() in ntdll (0x0033fef8)
  8 0x7bc73770 call_thread_entry_point+0x6f() in ntdll (0x0033ffc8)
  9 0x7bc498ba call_dll_entry_point+0x659() in ntdll (0x0033ffe8)
0x681ca9f0: movzwl    0xc(%eax),%esi
Modules:
Module    Address            Debug info    Name (63 modules)
ELF    20000000-20019000    Deferred        version<elf>
  \-PE    20010000-20019000    \               version
ELF    27cba000-27cce000    Deferred        lz32<elf>
  \-PE    27cc0000-27cce000    \               lz32
ELF    3d06c000-3d091000    Deferred        libpng12.so.0
ELF    68000000-6801e000    Deferred        ld-linux.so.2
ELF    6801e000-6815e000    Export          libwine.so.1
ELF    6815e000-68177000    Deferred        libpthread.so.0
ELF    68177000-6817b000    Deferred        libdl.so.2
ELF    6817b000-681a1000    Deferred        libm.so.6
ELF    681a1000-681a9000    Deferred        libnss_compat.so.2
ELF    681a9000-681b5000    Deferred        libnss_files.so.2
ELF    681b5000-681d9000    Export          winemenubuilder<elf>
  \-PE    681c0000-681d9000    \               winemenubuilder
ELF    681d9000-683b2000    Deferred        shell32<elf>
  \-PE    681f0000-683b2000    \               shell32
ELF    683b2000-68413000    Deferred        shlwapi<elf>
  \-PE    683c0000-68413000    \               shlwapi
ELF    68413000-68545000    Deferred        user32<elf>
  \-PE    68420000-68545000    \               user32
ELF    68545000-685d0000    Deferred        gdi32<elf>
  \-PE    68550000-685d0000    \               gdi32
ELF    685d0000-686cf000    Deferred        ole32<elf>
  \-PE    685f0000-686cf000    \               ole32
ELF    686cf000-68742000    Deferred        rpcrt4<elf>
  \-PE    686e0000-68742000    \               rpcrt4
ELF    68742000-687c8000    Deferred        libfreetype.so.6
ELF    687c8000-687dd000    Deferred        libz.so.1
ELF    687dd000-6880c000    Deferred        libfontconfig.so.1
ELF    6880c000-68836000    Deferred        libexpat.so.1
ELF    68836000-688d7000    Deferred        winex11<elf>
  \-PE    68840000-688d7000    \               winex11
ELF    688d7000-688df000    Deferred        libsm.so.6
ELF    688df000-688ee000    Deferred        libxext.so.6
ELF    688ee000-68a09000    Deferred        libx11.so.6
ELF    68a09000-68a0e000    Deferred        libuuid.so.1
ELF    68a0e000-68a27000    Deferred        libxcb.so.1
ELF    68a27000-68a2b000    Deferred        libxau.so.6
ELF    68a2b000-68a31000    Deferred        libxdmcp.so.6
ELF    68a31000-68a52000    Deferred        imm32<elf>
  \-PE    68a40000-68a52000    \               imm32
ELF    68a52000-68a56000    Deferred        libxinerama.so.1
ELF    68a56000-68a60000    Deferred        libxrender.so.1
ELF    68a60000-68a68000    Deferred        libxrandr.so.2
ELF    68a68000-68a6c000    Deferred        libxcomposite.so.1
ELF    68a6c000-68a76000    Deferred        libxcursor.so.1
ELF    68a76000-68a7c000    Deferred        libxfixes.so.3
ELF    68a7c000-68ab0000    Deferred        uxtheme<elf>
  \-PE    68a80000-68ab0000    \               uxtheme
ELF    69392000-693a9000    Deferred        libnsl.so.1
ELF    6d153000-6d2b4000    Deferred        libc.so.6
ELF    71720000-7180d000    Deferred        comctl32<elf>
  \-PE    71730000-7180d000    \               comctl32
ELF    732d8000-732e3000    Deferred        libnss_nis.so.2
ELF    756e3000-756e9000    Deferred        libxxf86vm.so.1
ELF    7726f000-77287000    Deferred        libice.so.6
ELF    7b587000-7b5e1000    Deferred        advapi32<elf>
  \-PE    7b590000-7b5e1000    \               advapi32
ELF    7b800000-7b97c000    Export          kernel32<elf>
  \-PE    7b810000-7b97c000    \               kernel32
ELF    7bc00000-7bcba000    Export          ntdll<elf>
  \-PE    7bc10000-7bcba000    \               ntdll
ELF    7bf00000-7bf04000    Deferred        <wine-loader>
Threads:
process  tid      prio (all id:s are in hex)
00000008 gta_sa.exe
    00000023    0
    0000001d    0
    00000009    0
0000000c (D) C:\windows\system32\winemenubuilder.exe
    0000000d    0 <==
0000000e services.exe
    00000014    0
    00000010    0
    0000000f    0
00000011 winedevice.exe
    00000018    0
    00000017    0
    00000013    0
    00000012    0
0000001e explorer.exe
    0000001f    0
00000025 winedbg.exe
    00000026    0
Backtrace:
=>0 0x681ca9f0 in winemenubuilder (+0xa9f0) (0x0033fc20)
  1 0x681cc76e in winemenubuilder (+0xc76d) (0x0033fcb0)
  2 0x681d0960 wWinMain+0x23cf() in winemenubuilder (0x0033fde0)
  3 0x681d1351 wmain+0xb0() in winemenubuilder (0x0033fe60)
  4 0x681d1292 in winemenubuilder (+0x11291) (0x0033fe90)
  5 0x7b85437c call_process_entry+0xb() in kernel32 (0x0033fea8)
  6 0x7b85501f ExitProcess+0xc9e() in kernel32 (0x0033fee8)
  7 0x7bc70be0 call_thread_func+0xb() in ntdll (0x0033fef8)
  8 0x7bc73770 call_thread_entry_point+0x6f() in ntdll (0x0033ffc8)
  9 0x7bc498ba call_dll_entry_point+0x659() in ntdll (0x0033ffe8)
Killed
piccoli@p-Ubuntu:~/.wine/drive_c/Program Files/Rockstar Games/GTA San Andreas$ couldn't load main module (2)
Process of pid=0008 has terminated
No process loaded, cannot execute 'echo Modules:'
Cannot get info on module while no process is loaded
No process loaded, cannot execute 'echo Threads:'
process  tid      prio (all id:s are in hex)
0000000e services.exe
    00000014    0
    00000010    0
    0000000f    0
00000011 winedevice.exe
    00000018    0
    00000017    0
    00000013    0
    00000012    0
0000001e explorer.exe
    0000001f    0
You must be attached to a process to run this command.
No process loaded, cannot execute 'detach'

```

It seems this time, the error was given about "gta_sa.exe" experiencing a serious problem and needing to close. Obviously, loading it via the terminal window works better. I see a lot of errors above about an Intel graphics card, mine is on-board. I'll go ahead and assume missing drivers?

---

### Post by That Nerd 2049 on 2011-06-19
There is a program under system administration in the menu called additional drivers, open it and see if it finds any 3rd party drivers for you.

---

### Post by piccoli on 2011-06-19
> **That Nerd 2049 said:**
> There is a program under system administration in the menu called additional drivers, open it and see if it finds any 3rd party drivers for you.

I went ahead and checked that program, it was empty. I restarted my computer and tried the program again, although, it was still empty...

---

### Post by That Nerd 2049 on 2011-06-19
I noticed close to the top of the error report it said "Unhandled vendor 8086" so I looked it up and read some one saying that changing "VertexShaderMode" to none may help.

open regedit and go to "[Software\\Wine\\Direct3D] 1267716040"

set "VertexShaderMode"="none".

source: [http://www.eveonline.com/ingameboard.asp?a=topic&threadID=1262420](http://www.eveonline.com/ingameboard.asp?a=topic&threadID=1262420)

Sorry but that's my only idea at the moment.

It may be that there is no suitable 3D drivers for your card.:sad:

Have you tried to run any other 3D programs on Ubuntu?

---

### Post by desktorp on 2011-06-19
I am pretty sure this game is not going to run with Intel onboard graphics.

---

### Post by XeKaaz on 2011-09-24
Good Evening.

This is a bumb so I don't have to create yet another thread about a simular problem.

I'm sitting on a pc 3,4ghz amd processor, a 512 ati radeon x850 gfx card.
And Ubuntu 11.04, latest version of wine and playonlinux.

Now, I have a copy of GTA San Andreas, not very retail. More transferred via servers.

Anyhow, it's a .rar file which I've extracted since pol couldn't find a program how to deal with .rar via wine. So I try to do the same as with the retail.


Install using POL on the gta_sa.exe file. Thing goes black, decreases my screen to 800x600 or less. I've read the tips so far but the problem stands.

Can anyone give a sort of manual how to install this properly?

Yes... I'm a complete noob, but eventually I'll learn.

Many Thanks!

---

