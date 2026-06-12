---
title: "How-to: Run Ragnarok Online in WINE"
date: 2006-08-20
forum: Tutorials
---

### Post by MKR. on 2006-08-20
Some tips have been adapted from:

[http://appdb.winehq.org/appview.php?iVersionId=928](http://appdb.winehq.org/appview.php?iVersionId=928)

This guide assumes that you have the RO client and an installation of a fairly recent WINE

Step 1: Open a terminal (alt+f2 and type gnome-terminal if in gnome, start->run->konsole if in KDE)

Step 2: run winecfg

Step 3: Select the graphics tab, and enable "Emulate a virtual desktop", and set it to a resulution that is supported by the RO client (see the next step)

Step 4: Locate the RO folder, and launch Setup.exe in wine. Set it to run in fullscreen, and choose a resolution. Make sure the lightmap box is unticked as this can cause problems

Step 5: open another terminal, or reuse the one you used for step 3 to navigate to the folder you installed RO in

Step 6: Determine which server you use; sakray would be Sakexe.exe, the main servers would be Ragexe.exe. Private servers are tricky as they tend to use data folders, which for some reason cause problems.

Step 7: type wine, a space, the name of the executable, another space, and 1rag1 (those are ones, not Ls)

The client should load properly

2010: Wow, this game is still around. Well it doesn't look like the client is much different, and WINE has come a long way. You probably won't have problems running it.

I guess you can still post in this thread if you have problems, and if someone who plays the game in Ubuntu is around, they'll help out.

2011 edit: No need to apologize for necroing. If RO can live for ten plus years, then this thread can keep popping up. :)

---

### Post by mewray on 2006-08-30
I'm trying to run Ragnarok Online, but I keep getting this error:

wine: Call from 0x402052 to unimplemented function MFC42.DLL.6478, aborting
wine: Unimplemented function MFC42.DLL.6478 called at address 0x402052 (thread 0009), starting debugger...
WineDbg starting on pid 0x8
Unhandled exception: unimplemented function MFC42.DLL.6478 called in 32-bit code (0x602bd447).
Register dump:
 CS:0023 SS:002b DS:002b ES:002b FS:006b GS:0063
 EIP:602bd447 ESP:0033e504 EBP:0033e568 EFLAGS:00000212(   - 00      - -IA1)
 EAX:0000194e EBX:602fa280 ECX:00192910 EDX:00110024
 ESI:0033e510 EDI:00000001
Stack dump:
0x0033e504:  00010028 00000000 00000000 80000100
0x0033e514:  00000001 00000000 00402052 00000002
0x0033e524:  0041c8aa 0000194e 00000002 605a3078
0x0033e534:  605eb040 605d065c 00110000 60b56a1c
0x0033e544:  ffffffff 00000001 0033e56c 60b3d393
0x0033e554:  00110000 00000000 000004c8 606588c2
fixme:ntdll:RtlNtStatusToDosErrorNoTeb no mapping for c0000119
Backtrace:
=>1 0x602bd447 call_dll_entry_point+0x67 in ntdll (0x602bd447)
  2 0x00402052 in sakray (+0x2052) (0x00402052)
  3 0x00000000 (0x00000000)
0x602bd447 call_dll_entry_point+0x67 in ntdll: subl     $4,%esp
Modules:
Module  Address                 Debug info      Name (66 modules)
PE      400000-424000   Export          sakray
PE      5f400000-5f4ed000       Deferred        mfc42
ELF     60000000-60017000       Deferred        ld-linux.so.2
ELF     60019000-60129000       Deferred        libwine.so.1
ELF     6012b000-60133000       Deferred        libxrender.so.1
ELF     60133000-6013c000       Deferred        libxcursor.so.1
ELF     6013c000-60140000       Deferred        libxfixes.so.3
ELF     60141000-60153000       Deferred        libpthread.so.0
ELF     60154000-60283000       Deferred        libc.so.6
ELF     60283000-60286000       Deferred        libdl.so.2
ELF     60287000-60305000       Export          ntdll<elf>
  \-PE  602a0000-60305000       \               ntdll
ELF     60305000-60327000       Deferred        libm.so.6
ELF     60327000-60330000       Deferred        libnss_compat.so.2
ELF     60330000-60345000       Deferred        libnsl.so.1
ELF     60345000-6034e000       Deferred        libnss_nis.so.2
ELF     6034e000-60358000       Deferred        libnss_files.so.2
ELF     60358000-6045a000       Deferred        kernel32<elf>
  \-PE  60370000-6045a000       \               kernel32
ELF     6048d000-604d4000       Deferred        wininet<elf>
  \-PE  604a0000-604d4000       \               wininet
ELF     604d4000-604f3000       Deferred        mpr<elf>
  \-PE  604e0000-604f3000       \               mpr
ELF     604f3000-60625000       Deferred        user32<elf>
  \-PE  60510000-60625000       \               user32
ELF     60625000-606d7000       Deferred        gdi32<elf>
  \-PE  60640000-606d7000       \               gdi32
ELF     607b2000-607bd000       Deferred        libgcc_s.so.1
ELF     607bd000-60801000       Deferred        advapi32<elf>
  \-PE  607d0000-60801000       \               advapi32
ELF     60801000-60857000       Deferred        shlwapi<elf>
  \-PE  60810000-60857000       \               shlwapi
ELF     60857000-608e7000       Deferred        ole32<elf>
  \-PE  60870000-608e7000       \               ole32
ELF     608e7000-60936000       Deferred        rpcrt4<elf>
  \-PE  608f0000-60936000       \               rpcrt4
ELF     60936000-60955000       Deferred        iphlpapi<elf>
  \-PE  60940000-60955000       \               iphlpapi
ELF     60955000-60968000       Deferred        libresolv.so.2
ELF     60968000-60a4e000       Deferred        shell32<elf>
  \-PE  60980000-60a4e000       \               shell32
ELF     60a4e000-60b10000       Deferred        comctl32<elf>
  \-PE  60a60000-60b10000       \               comctl32
ELF     60b10000-60b72000       Deferred        msvcrt<elf>
  \-PE  60b20000-60b72000       \               msvcrt
ELF     60b72000-60bdb000       Deferred        libfreetype.so.6
ELF     60bdb000-60bef000       Deferred        libz.so.1
ELF     60bef000-60c1d000       Deferred        libfontconfig.so.1
ELF     60c1d000-60c3c000       Deferred        libexpat.so.1
ELF     60c3c000-60cbe000       Deferred        winex11<elf>
  \-PE  60c50000-60cbe000       \               winex11
ELF     60cbe000-60cc6000       Deferred        libsm.so.6
ELF     60cc6000-60cde000       Deferred        libice.so.6
ELF     60cde000-60ce3000       Deferred        libxxf86vm.so.1
ELF     60ce3000-60cf0000       Deferred        libxext.so.6
ELF     60cf0000-60dd6000       Deferred        libx11.so.6
ELF     60dd6000-60dd9000       Deferred        libxau.so.6
ELF     60dd9000-60e5e000       Deferred        libgl.so.1
ELF     60e5e000-61620000       Deferred        libglcore.so.1
ELF     61620000-61622000       Deferred        libnvidia-tls.so.1
ELF     61622000-6163e000       Deferred        imm32<elf>
  \-PE  61630000-6163e000       \               imm32
ELF     61640000-61672000       Deferred        uxtheme<elf>
  \-PE  61650000-61672000       \               uxtheme
PE      780c0000-78121000       Deferred        msvcp60
ELF     7bf00000-7bf03000       Deferred        <wine-loader>
Threads:
process  tid      prio (all id:s are in hex)
0000000a
        0000000b    0
00000008 (D) C:\Program Files\Gravity\RO\sakray.exe
        00000009    0 <==


I've configured wine to use native mfc42.dll and got the dll off the web, and put it in windows/system (and windows/system32 AND the RO folder, based on various fixes I've read)... yet this continues to occur.  Any ideas?

---

### Post by Linked on 2006-09-02
I used mfc42.dll from my XP Pro installation, client loads fine but its very laggy.

Very nice How-to anyways.:wink:

---

### Post by Exakun on 2006-12-12
I tried your method... it sort of worked. After 5 minutes, the client popped up. The interface was in Korean, and there appeared to be splits in the image. The emulated desktop showed two empty windows and it flickered between that and the "fullscreen" Ragnarok. i was able to log into my server successfully, but it took exceptionally long to load the map I was in, and was unplayable due to the flickering. I use a personally hexed client for a private server that uses a data folder, but that doesn't seem to be the only issue from the errors I got. The fact that the client was in Korean leads me to believe that it could not read the Data folder, where translated sprites are located, but the other issues appear to be problems with video and sound emulation. Note that <-(x#) means that this error repeated # times.

Errors:
```
fixme:d3d:IWineD3DDeviceImpl_GetAvailableTextureMem (0x1670028) : stub, simulating 64MB for now, returning 64MB left
fixme:ddraw:IDirectDrawImpl_SetCooperativeLevel (0x1e6aa8)->(0x20024,00000c13)
fixme:ddraw:IDirectDrawImpl_SetCooperativeLevel (0x1e6aa8) Unhandled flag DDSCL_MULTITHREADED, Uh Oh...
fixme:x11drv:X11DRV_desktop_SetCurrentMode Cannot change screen BPP from 32 to 16
fixme:d3d:state_blend Unrecognized dst blend value 0
fixme:d3d:IWineD3DDeviceImpl_SetRenderState WINED3DRS_POINTSIZE_MIN not supported on this opengl
err:d3d:IWineD3DDeviceImpl_SetRenderState Multisample antialiasing not supported by gl
fixme:d3d:IWineD3DDeviceImpl_SetRenderState WINED3DRS_POINTSIZE_MAX not supported on this opengl
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:imm:ImmReleaseContext (0x20024, 0x16c670): stub
fixme:imm:ImmReleaseContext (0x20024, 0x16c670): stub
fixme:d3d_surface:IWineGDISurfaceImpl_Blt Can't handle DDBLT_WAIT flag right now.
err:dsound:DSOUND_MixOne underrun on sound buffer 0x1e54c0 <- (x7)
fixme:imm:ImmReleaseContext (0x20024, 0x16c670): stub
err:dsound:DSOUND_MixOne underrun on sound buffer 0x1e54c0 <-(x4)
fixme:imm:ImmReleaseContext (0x20024, 0x16c670): stub <-(x6)
err:dsound:DSOUND_MixOne underrun on sound buffer 0x1e54c0 <-(x24)
<I killed wine with CTRL+C at this point>

```

From this it would seem that it cannot emulate sound, and that it is trying to drop the window from 32 to 16 bits.

I am running Edgy (beryl was running, I'll try without it) on an unmodified Toshiba Satellite M105-S3031. If anyone knows how to solve these problems, please let me know. I'm dying to be able to play my favorite game on linux :D

---

### Post by Stargazer989 on 2008-06-09
(bad idea) for me, i tried to run this like you said but everything froze and i had to hold the power button to force a reboot

---

### Post by Boebuntu on 2008-07-05
Sorry for the grave dig, but I got an error.

> boe@boe-desktop:~$ wine limitro lragl
preloader: Warning: failed to reserve range 00000000-60000000
preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report

What does this mean?

---

### Post by MKR. on 2008-07-14
I wrote this guide two years ago. The client has probably changed considerably since then, and I haven't played in about a year. Someone else will have to figure it out. :P

---

### Post by MatthijsL on 2008-08-08
Any Idea why it runs slow with ATI cards?

---

### Post by SevenOrange on 2009-08-26
I was wondering the same thing. Why is the client so laggy when running with ATI cards? Drivers?

---

### Post by budi_indira on 2009-11-09
Hi, thanks for your 'how-to'. I can play Ragnarok Online Indonesia (IdRO) now..

But, my slow inet connection make me.. huffhh... :'(

Ps:
I'm using Ubuntu 9.10 Karmic Koala with Wine 1.0.1

---

### Post by MKR. on 2010-10-21
Wow, this game is still around. It looks like Gravity just dropped a pretty big update on iRO with a new client.

Since this thread is still the #1 result on Google for *ragnarok online ubuntu*, I guess it'd be a good idea for someone who still plays this game to let me know if this guide still works. 

And if not, to write an updated guide for getting it to work so I can toss it up in the OP. :)

---

### Post by deathm00n on 2011-03-19
hey, sorry to ressurrect this topic, but I would really like to play ragnarok in my ubuntu

tried to follow your instructions to install the official international ragnarok(IRO) but I'm lost at step 7, the terminal can't find the Ragnarok.exe, it searches for it on c:/windows/system32 but  the game auto installs itself in c/program file/gravity/ragnarok online renewal and you cant choose another directory, how can I find the place in the terminal?

---

### Post by MKR. on 2011-03-19
> **deathm00n said:**
> hey, sorry to ressurrect this topic, but I would really like to play ragnarok in my ubuntu

tried to follow your instructions to install the official international ragnarok(IRO) but I'm lost at step 7, the terminal can't find the Ragnarok.exe, it searches for it on c:/windows/system32 but  the game auto installs itself in c/program file/gravity/ragnarok online renewal and you cant choose another directory, how can I find the place in the terminal?

My Linux-terminal-fu is weak lately, but I'm sure someone will be along soon to tell you where WINE keeps Program Files.

---

### Post by deathm00n on 2011-03-19
thank you anyway, I will wait someone else

---

### Post by Wintermute27 on 2011-04-09
I found mine in: /home/[user_name]/.wine/drive_c/Program Files/Gravity/Ragnarok Online Renewal/

I followed these steps, and while it runs, the mouse lag is something awful. Do you need any other applications to get it to run smooth(er), or do I just need to tweak some settings? I'm using Wine 1.3.17

---

### Post by MKR. on 2011-04-09
> **Wintermute27 said:**
> I found mine in: /home/[user_name]/.wine/drive_c/Program Files/Gravity/Ragnarok Online Renewal/

I followed these steps, and while it runs, the mouse lag is something awful. Do you need any other applications to get it to run smooth(er), or do I just need to tweak some settings? I'm using Wine 1.3.17

It seems to depend very heavily on your GPU.

---

### Post by mpthrapp on 2011-06-14
I followed the steps you gave, but running Setup.exe just starts up the virtual desktop, waits a moment, and then closes. Any advice?

---

### Post by 5PUTN|K on 2011-06-25
i get this error what causes this 

> deniz@deniz-laptop:~$ wine "/home/deniz/.wine/dosdevices/c:/Program Files/Gravity/Ragnarok Online/Ragnarok.exe" 1rag1
fixme:ntoskrnl:KeInitializeTimerEx stub: 0x110fb0 0
err:module:import_dll Library MFC42.DLL (which is needed by L"C:\\Program Files\\Gravity\\Ragnarok Online\\Ragnarok.exe") not found
err:menubuilder:write_freedesktop_mime_type_entry error writing file /home/deniz/.local/share/mime/packages/x-wine-extension-/bzw.xml
err:menubuilder:write_freedesktop_association_entry error writing association file "/home/deniz/.local/share/applications/wine-extension-/bzw.desktop"
err:module:find_forwarded_export module not found for forward 'msvcp90.?erase@?$basic_string@DU?$char_traits@D@std@@V?$allocator@D@2@@std@@QAEAAV12@II@Z' used by L"C:\\windows\\system32\\msvcp60.dll"
err:module:find_forwarded_export module not found for forward 'msvcp90.?find@?$basic_string@DU?$char_traits@D@std@@V?$allocator@D@2@@std@@QBEIPBDII@Z' used by L"C:\\windows\\system32\\msvcp60.dll"
err:module:find_forwarded_export module not found for forward 'msvcp90.??1?$basic_string@DU?$char_traits@D@std@@V?$allocator@D@2@@std@@QAE@XZ' used by L"C:\\windows\\system32\\msvcp60.dll"
err:module:find_forwarded_export module not found for forward 'msvcp90.??0?$basic_string@DU?$char_traits@D@std@@V?$allocator@D@2@@std@@QAE@ABV01@@Z' used by L"C:\\windows\\system32\\msvcp60.dll"
err:module:find_forwarded_export module not found for forward 'msvcp90.?assign@?$basic_string@DU?$char_traits@D@std@@V?$allocator@D@2@@std@@QAEAAV12@ABV12@II@Z' used by L"C:\\windows\\system32\\msvcp60.dll"
err:module:find_forwarded_export module not found for forward 'msvcp90.?npos@?$basic_string@DU?$char_traits@D@std@@V?$allocator@D@2@@std@@2IB' used by L"C:\\windows\\system32\\msvcp60.dll"
err:module:find_forwarded_export module not found for forward 'msvcp90.?assign@?$basic_string@DU?$char_traits@D@std@@V?$allocator@D@2@@std@@QAEAAV12@PBDI@Z' used by L"C:\\windows\\system32\\msvcp60.dll"
err:module:LdrInitializeThunk Main exe initialization for L"C:\\Program Files\\Gravity\\Ragnarok Online\\Ragnarok.exe" failed, status c0000135
deniz@deniz-laptop:~$ 

---

### Post by 5PUTN|K on 2011-06-25
i fixed that just by adding the missing dll files into the game folder but im now getting this error

> deniz@deniz-laptop:~$ wine "/home/deniz/.wine/dosdevices/c:/Program Files/Gravity/Ragnarok Online/Ragnarok.exe"
fixme:ntoskrnl:KeInitializeTimerEx stub: 0x110fb0 0
err:menubuilder:write_freedesktop_mime_type_entry error writing file /home/deniz/.local/share/mime/packages/x-wine-extension-/bzw.xml
err:menubuilder:write_freedesktop_association_entry error writing association file "/home/deniz/.local/share/applications/wine-extension-/bzw.desktop"
wine: Call from 0x7bc499f0 to unimplemented function MFC42.DLL.6478, aborting
wine: Unimplemented function MFC42.DLL.6478 called at address 0x7bc499f0 (thread 0009), starting debugger...
Unhandled exception: unimplemented function MFC42.DLL.6478 called in 32-bit code (0x7bc499f0).
Register dump:
 CS:0023 SS:002b DS:002b ES:002b FS:0063 GS:006b
 EIP:7bc499f0 ESP:0032e408 EBP:0032e46c EFLAGS:00000202(   - --  I   - - - )
 EAX:0000194e EBX:7bc9dff4 ECX:00135ea8 EDX:00000000
 ESI:0032e414 EDI:00000001
Stack dump:
0x0032e408:  7bc3438f 00000000 00000000 80000100
0x0032e418:  00000001 00000000 7bc499f0 00000002
0x0032e428:  0041d922 0000194e 00000001 00000000
0x0032e438:  00110014 00000000 00000000 7bc474cd
0x0032e448:  7ecb5ff4 ffffffff 00000001 0032e474
0x0032e458:  7ec78137 00110000 00000000 7ed3d300
Backtrace:
=>0 0x7bc499f0 stub_entry_point+0x50(dll="MFC42.DLL", name=*** invalid address 0x194e ***, ret_addr=0x402052) [/build/buildd/wine1.3-1.3.21/dlls/ntdll/loader.c:197] in ntdll (0x0032e46c)
0x7bc499f0 stub_entry_point+0x50 [/build/buildd/wine1.3-1.3.21/dlls/ntdll/loader.c:197] in ntdll: subl    $4,%esp
Unable to access file '/build/buildd/wine1.3-1.3.21/dlls/ntdll/loader.c'
Modules:
Module    Address            Debug info    Name (69 modules)
PE      400000-  427000    Deferred        ragnarok
PE    5f400000-5f4ed000    Deferred        mfc42
PE    70bd0000-70c34000    Deferred        shlwapi
PE    780c0000-78121000    Deferred        msvcp60
ELF    7b800000-7b99e000    Deferred        kernel32<elf>
  \-PE    7b810000-7b99e000    \               kernel32
ELF    7bc00000-7bcba000    Dwarf           ntdll<elf>
  \-PE    7bc10000-7bcba000    \               ntdll
ELF    7bf00000-7bf04000    Deferred        <wine-loader>
ELF    7e3b2000-7e424000    Deferred        rpcrt4<elf>
  \-PE    7e3c0000-7e424000    \               rpcrt4
ELF    7e424000-7e526000    Deferred        ole32<elf>
  \-PE    7e440000-7e526000    \               ole32
ELF    7e53c000-7e56f000    Deferred        uxtheme<elf>
  \-PE    7e540000-7e56f000    \               uxtheme
ELF    7e56f000-7e579000    Deferred        libxcursor.so.1
ELF    7e579000-7e587000    Deferred        libxi.so.6
ELF    7e587000-7e58d000    Deferred        libxfixes.so.3
ELF    7e58d000-7e591000    Deferred        libxcomposite.so.1
ELF    7e591000-7e599000    Deferred        libxrandr.so.2
ELF    7e599000-7e5a3000    Deferred        libxrender.so.1
ELF    7e5a3000-7e5a9000    Deferred        libxxf86vm.so.1
ELF    7e5a9000-7e5ad000    Deferred        libxinerama.so.1
ELF    7e5ad000-7e5ce000    Deferred        imm32<elf>
  \-PE    7e5b0000-7e5ce000    \               imm32
ELF    7e5ce000-7e5d4000    Deferred        libxdmcp.so.6
ELF    7e5d4000-7e5d8000    Deferred        libxau.so.6
ELF    7e5d8000-7e5f2000    Deferred        libxcb.so.1
ELF    7e5f2000-7e5f7000    Deferred        libuuid.so.1
ELF    7e5f7000-7e714000    Deferred        libx11.so.6
ELF    7e714000-7e724000    Deferred        libxext.so.6
ELF    7e724000-7e73d000    Deferred        libice.so.6
ELF    7e73d000-7e746000    Deferred        libsm.so.6
ELF    7e769000-7e810000    Deferred        winex11<elf>
  \-PE    7e770000-7e810000    \               winex11
ELF    7e823000-7e84a000    Deferred        libexpat.so.1
ELF    7e84a000-7e87a000    Deferred        libfontconfig.so.1
ELF    7e87a000-7e8f1000    Deferred        libfreetype.so.6
ELF    7e8f1000-7e92a000    Deferred        libncurses.so.5
ELF    7e94d000-7ea41000    Deferred        comctl32<elf>
  \-PE    7e950000-7ea41000    \               comctl32
ELF    7ea41000-7ec3c000    Deferred        shell32<elf>
  \-PE    7ea50000-7ec3c000    \               shell32
ELF    7ec3c000-7ecbf000    Deferred        msvcrt<elf>
  \-PE    7ec50000-7ecbf000    \               msvcrt
ELF    7ecbf000-7ed1b000    Deferred        advapi32<elf>
  \-PE    7ecd0000-7ed1b000    \               advapi32
ELF    7ed1b000-7edb1000    Deferred        gdi32<elf>
  \-PE    7ed30000-7edb1000    \               gdi32
ELF    7edb1000-7eee7000    Deferred        user32<elf>
  \-PE    7edc0000-7eee7000    \               user32
ELF    7eee7000-7ef0b000    Deferred        mpr<elf>
  \-PE    7eef0000-7ef0b000    \               mpr
ELF    7ef0b000-7ef20000    Deferred        libz.so.1
ELF    7ef20000-7ef89000    Deferred        wininet<elf>
  \-PE    7ef30000-7ef89000    \               wininet
ELF    7ef89000-7ef95000    Deferred        libnss_files.so.2
ELF    7ef95000-7efa0000    Deferred        libnss_nis.so.2
ELF    7efa0000-7efb7000    Deferred        libnsl.so.1
ELF    7efb7000-7efdd000    Deferred        libm.so.6
ELF    7efe7000-7f000000    Deferred        version<elf>
  \-PE    7eff0000-7f000000    \               version
ELF    f748b000-f748f000    Deferred        libdl.so.2
ELF    f748f000-f75ea000    Deferred        libc.so.6
ELF    f75eb000-f7604000    Deferred        libpthread.so.0
ELF    f7608000-f7610000    Deferred        libnss_compat.so.2
ELF    f7627000-f7768000    Dwarf           libwine.so.1
ELF    f776a000-f7788000    Deferred        ld-linux.so.2
ELF    f7788000-f7789000    Deferred        [vdso].so
Threads:
process  tid      prio (all id:s are in hex)
00000008 (D) C:\Program Files\Gravity\Ragnarok Online\Ragnarok.exe
    00000009    0 <==
0000000e services.exe
    00000026    0
    00000020    0
    0000001b    0
    00000016    0
    00000015    0
    00000014    0
    00000010    0
    0000000f    0
00000011 winedevice.exe
    00000017    0
    00000013    0
    00000012    0
00000018 winedevice.exe
    0000001c    0
    0000001a    0
    00000019    0
0000001d winedevice.exe
    00000022    0
    00000021    0
    0000001f    0
    0000001e    0
00000023 plugplay.exe
    00000027    0
    00000025    0
    00000024    0
00000028 explorer.exe
    00000029    0
Backtrace:
=>0 0x7bc499f0 stub_entry_point+0x50(dll="MFC42.DLL", name=*** invalid address 0x194e ***, ret_addr=0x402052) [/build/buildd/wine1.3-1.3.21/dlls/ntdll/loader.c:197] in ntdll (0x0032e46c)
wine: Call from 0x7bc499f0 to unimplemented function MFC42.DLL.6478, aborting
deniz@deniz-laptop:~$ 


---

### Post by 5PUTN|K on 2011-06-25
now i get no error messages but the game does not start but i get this in terminal

> deniz@deniz-laptop:~$ wine "/home/deniz/.wine/dosdevices/c:/Program Files/Gravity/Ragnarok Online/Ragnarok.exe"
fixme:ntoskrnl:KeInitializeTimerEx stub: 0x110fb0 0
err:module:import_dll Loading library MFC42.DLL (which is needed by L"C:\\Program Files\\Gravity\\Ragnarok Online\\Ragnarok.exe") failed (error c000007b).
err:module:import_dll Loading library MSVCP60.dll (which is needed by L"C:\\Program Files\\Gravity\\Ragnarok Online\\Ragnarok.exe") failed (error c000007b).
err:module:LdrInitializeThunk Main exe initialization for L"C:\\Program Files\\Gravity\\Ragnarok Online\\Ragnarok.exe" failed, status c0000135
deniz@deniz-laptop:~$ err:menubuilder:write_freedesktop_mime_type_entry error writing file /home/deniz/.local/share/mime/packages/x-wine-extension-/bzw.xml
err:menubuilder:write_freedesktop_association_entry error writing association file "/home/deniz/.local/share/applications/wine-extension-/bzw.desktop"

---

### Post by Arkelsa on 2011-07-01
Sorry for Necro, really need help


Have you been able to figure out your problems yet sputnik? After much difficulty I finally managed to figure out my Wine installation and install Ragnarok, when I try to load it all that I get is a Blue screen and it appears to be trying to load my Ragnarok Online, then freezes, when I load it in terminal the same thing happens, even if I use 1rag1, hes the issues that seem to occur


fixme:dsalsa:IDsDriverBufferImpl_SetVolumePan (0x131c40,0x132088): stub
fixme:dsalsa:IDsDriverBufferImpl_SetVolumePan (0x131c40,0x132088): stub
fixme:d3d_caps:select_card_intel_mesa Card selection not handled for Mesa Intel driver
fixme:d3d_caps:init_driver_info Unhandled vendor 8086.
fixme:win:EnumDisplayDevicesW ((null),0,0x32f220,0x00000000), stub!
fixme:d3d:swapchain_init Add OpenGL context recreation support to context_validate_onscreen_formats
fixme:dinput:SysMouseAImpl_Acquire Clipping cursor to (0,0)-(806,612)
fixme:ddraw:IDirectDrawImpl_RestoreAllSurfaces (0x1eb2d8): Stub
fixme:ddraw:IDirectDrawImpl_WaitForVerticalBlank (0x1eb2d8)->(1,(nil)): Stub


If anyone could help i'd really appreciate it :) thank you all


~Arky

---

### Post by 5PUTN|K on 2011-07-19
I finaly got it all working nice and smooth but my problem was caused by some dll file i just installed the missing dlls using winetricks and it worked maybe winetricks can solve your problem too but im not sure what you need to install for the error you get

---

### Post by felinoel on 2011-08-09
> **5PUTN|K said:**
> I finaly got it all working nice and smooth but my problem was caused by some dll file i just installed the missing dlls using winetricks and it worked maybe winetricks can solve your problem too but im not sure what you need to install for the error you getWait so you actually got it to work? Post how please?

---

### Post by rongden on 2011-08-10
ok I'll test . thank you

---

### Post by asdfuogh on 2011-08-21
I was able to run this (after installing from dll's)... but I wasn't able to connect. You guys think it's because it's running on an emulator so the server thinks it is some kind of hack?

---

### Post by skathed on 2011-08-28
has anyone had a issue with wine saying theres a run time error with ragnorak after installing it?

---

### Post by asdfuogh on 2011-08-28
You know what's interesting? The cursor is laggy as hell and won't move when I get it to run. But then, if you keep tapping alt as you move the mouse, wine recognizes it as moving and then it actually moves. Why is that? What is alt's purpose in wine?

---

### Post by everard on 2012-01-19
You can try the fix for laggy cursor (or probably laggy game) here:
[http://everardonggon.com/?p=32]("http://everardonggon.com/?p=32")
Hope this helps :-)

---

