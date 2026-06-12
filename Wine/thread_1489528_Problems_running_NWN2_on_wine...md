---
title: "Problems running NWN2 on wine.."
date: 2010-05-21
forum: Wine
---

### Post by Nordstroemen on 2010-05-21
Trying to run th good old game of Neverwinter Nights 2, but I am getting into some trouble along the way.. I get to the intro screen, but once i press play, it gives me a program error: "nvn2main.exe has encountered a serious problem and needs to close."

Anyone who can help me around this problem?

Thank you for your time


```
 rnp@rnp-laptop:~$ wine "C:\Program Files\Atari\Neverwinter Nights 2\NWN2Launcher.exe"
fixme:mixer:ALSA_MixerInit No master control found on HDA ATI HDMI, disabling mixer
rnp@rnp-laptop:~$ fixme:ntdll:NtQuerySystemInformation info_class SYSTEM_HANDLE_INFORMATION
fixme:ntdll:NtQueryObject Unsupported information class 3
err:rpc:I_RpcGetBuffer no binding
fixme:win:EnumDisplayDevicesW ((null),0,0x1373a90,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x1373610,0x00000000), stub!
fixme:psapi:EnumPageFilesA (0xbf8c50, 0x1355330) stub
fixme:psapi:EnumPageFilesA (0xbf8c50, 0x1323858) stub
fixme:ntdll:NtQuerySystemInformation info_class SYSTEM_HANDLE_INFORMATION
fixme:ntdll:NtQuerySystemInformation (0x00000007,0x134fdac,0x00000018,(nil)) stub
fixme:ntdll:server_ioctl_file Unsupported ioctl 2d0c04 (device=2d access=0 func=301 method=0)
wine: Unhandled page fault on read access to 0x00000000 at address 0xd80303 (thread 0029), starting debugger...
Unhandled exception: page fault on read access to 0x00000000 in 32-bit code (0x00d80303).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:00d80303 ESP:0134ec20 EBP:0134f590 EFLAGS:00010296(  R- --  I S -A-P- )
 EAX:00000000 EBX:00000000 ECX:c0000001 EDX:ffffffff
 ESI:00f54284 EDI:00f54284
Stack dump:
0x0134ec20:  00000078 00000073 00f566b4 00d7b277
0x0134ec30:  0134f55c 00f566ac 0134f5b0 0134f9bc
0x0134ec40:  0000006f 00000000 013528ab 00000000
0x0134ec50:  00000000 00000000 00000000 00000000
0x0134ec60:  00000000 00000000 00000000 00000000
0x0134ec70:  00000000 00000000 00000000 00000000
Backtrace:
=>0 0x00d80303 in nwn2main (+0x980303) (0x0134f590)
  1 0x00d83498 in nwn2main (+0x983497) (0x0134fdb8)
  2 0x00d555b1 in nwn2main (+0x9555b0) (0x013528bc)
  3 0x00d5f4d5 in nwn2main (+0x95f4d4) (0x01359254)
  4 0x0c2c70fa (0x01062760)
  5 0x00000000 (0x00c3124c)
  6 0xf18b5601 (0x042444f6)
0x00d80303: cmpb    $0x0,0x0(%ebx)
Modules:
Module    Address            Debug info    Name (94 modules)
PE      400000- 1190000    Export          nwn2main
PE     1390000- 15f0000    Deferred        d3dx9_30
PE    10000000-1000e000    Deferred        nwn2_memorymgr
ELF    20000000-2002f000    Deferred        libatiadlxx.so
PE    21100000-21164000    Deferred        mss32
ELF    21164000-22c18000    Deferred        fglrx_dri.so
PE    30000000-3006d000    Deferred        binkw32
ELF    30fe9000-30fff000    Deferred        psapi<elf>
  \-PE    30ff0000-30fff000    \               psapi
ELF    35472000-3547b000    Deferred        librt.so.1
ELF    4bbc4000-4bbe3000    Deferred        libgcc_s.so.1
PE    50000000-50090000    Deferred        granny2
ELF    6323f000-63247000    Deferred        libatiuki.so.1
ELF    68000000-6801d000    Deferred        ld-linux.so.2
ELF    6801d000-68158000    Deferred        libwine.so.1
ELF    68158000-68171000    Deferred        libpthread.so.0
ELF    68171000-682cb000    Deferred        libc.so.6
ELF    682cb000-682f1000    Deferred        libm.so.6
ELF    682f1000-682f9000    Deferred        libnss_compat.so.2
ELF    682f9000-68303000    Deferred        libnss_nis.so.2
ELF    68303000-6830f000    Deferred        libnss_files.so.2
ELF    6830f000-68396000    Deferred        winmm<elf>
  \-PE    68320000-68396000    \               winmm
ELF    68396000-683ef000    Deferred        advapi32<elf>
  \-PE    683a0000-683ef000    \               advapi32
ELF    683ef000-68460000    Deferred        rpcrt4<elf>
  \-PE    68400000-68460000    \               rpcrt4
ELF    68460000-6855c000    Deferred        ole32<elf>
  \-PE    68480000-6855c000    \               ole32
ELF    6855c000-685bb000    Deferred        shlwapi<elf>
  \-PE    68570000-685bb000    \               shlwapi
ELF    685bb000-685e7000    Deferred        ws2_32<elf>
  \-PE    685c0000-685e7000    \               ws2_32
ELF    685e7000-68620000    Deferred        dinput<elf>
  \-PE    685f0000-68620000    \               dinput
ELF    68620000-68654000    Deferred        d3d9<elf>
  \-PE    68630000-68654000    \               d3d9
ELF    68654000-68675000    Deferred        imm32<elf>
  \-PE    68660000-68675000    \               imm32
ELF    68675000-68809000    Deferred        shell32<elf>
  \-PE    68690000-68809000    \               shell32
ELF    68809000-688d7000    Deferred        comctl32<elf>
  \-PE    68810000-688d7000    \               comctl32
ELF    688d7000-689bd000    Deferred        oleaut32<elf>
  \-PE    688f0000-689bd000    \               oleaut32
ELF    689bd000-689dd000    Deferred        iphlpapi<elf>
  \-PE    689c0000-689dd000    \               iphlpapi
ELF    689dd000-689f2000    Deferred        libz.so.1
ELF    689f2000-68a22000    Deferred        libfontconfig.so.1
ELF    68a22000-68a49000    Deferred        libexpat.so.1
ELF    68a49000-68ae8000    Deferred        winex11<elf>
  \-PE    68a60000-68ae8000    \               winex11
ELF    68ae8000-68af1000    Deferred        libsm.so.6
ELF    68af1000-68b0a000    Deferred        libice.so.6
ELF    68b0a000-68c27000    Deferred        libx11.so.6
ELF    68c27000-68c2c000    Deferred        libuuid.so.1
ELF    68c2c000-68c32000    Deferred        libxdmcp.so.6
ELF    68c32000-68c38000    Deferred        libxxf86vm.so.1
ELF    68c38000-68c42000    Deferred        libxrender.so.1
ELF    68c42000-68c4a000    Deferred        libxrandr.so.2
ELF    68c4a000-68c4e000    Deferred        libxcomposite.so.1
ELF    68c4e000-68c54000    Deferred        libxfixes.so.3
ELF    68c54000-68c5e000    Deferred        libxcursor.so.1
ELF    68c5e000-68c91000    Deferred        uxtheme<elf>
  \-PE    68c60000-68c91000    \               uxtheme
ELF    6e30e000-6e444000    Deferred        wined3d<elf>
  \-PE    6e320000-6e444000    \               wined3d
ELF    7012b000-7013b000    Deferred        libxext.so.6
ELF    70787000-707a0000    Deferred        version<elf>
  \-PE    70790000-707a0000    \               version
ELF    72b7c000-72c32000    Deferred        libgl.so.1
ELF    72cc6000-72dd5000    Deferred        user32<elf>
  \-PE    72ce0000-72dd5000    \               user32
ELF    72f2c000-72f40000    Deferred        lz32<elf>
  \-PE    72f30000-72f40000    \               lz32
ELF    7415d000-74171000    Deferred        libresolv.so.2
ELF    750ea000-750ee000    Deferred        libdl.so.2
ELF    756fa000-756fe000    Deferred        libxinerama.so.1
PE    78000000-78044000    Deferred        msvcrt
PE    78130000-781cb000    Deferred        msvcr80
ELF    7923b000-792b1000    Deferred        libfreetype.so.6
ELF    79d3c000-79d53000    Deferred        libnsl.so.1
ELF    7a581000-7a59b000    Deferred        libxcb.so.1
ELF    7a62f000-7a64a000    Deferred        wsock32<elf>
  \-PE    7a630000-7a64a000    \               wsock32
ELF    7b65f000-7b663000    Deferred        libxau.so.6
ELF    7b704000-7b78e000    Deferred        gdi32<elf>
  \-PE    7b710000-7b78e000    \               gdi32
ELF    7b800000-7b93a000    Deferred        kernel32<elf>
  \-PE    7b810000-7b93a000    \               kernel32
ELF    7bc00000-7bcb6000    Deferred        ntdll<elf>
  \-PE    7bc10000-7bcb6000    \               ntdll
ELF    7bf00000-7bf04000    Deferred        <wine-loader>
PE    7c420000-7c4a7000    Deferred        msvcp80
Threads:
process  tid      prio (all id:s are in hex)
0000000e services.exe
    0000001c    0
    00000017    0
    00000015    0
    00000014    0
    00000010    0
    0000000f    0
00000011 winedevice.exe
    00000018    0
    00000016    0
    00000013    0
    00000012    0
00000019 winedevice.exe
    0000001d    0
    0000001b    0
    0000001a    0
0000001e explorer.exe
    0000001f    0
00000024 nwloader.exe
    00000025    0
00000026 nwn2.exe
    00000027    0
00000028 (D) C:\Program Files\Atari\Neverwinter Nights 2\nwn2main.exe
    00000029    0 <==
Backtrace:
=>0 0x00d80303 in nwn2main (+0x980303) (0x0134f590)
  1 0x00d83498 in nwn2main (+0x983497) (0x0134fdb8)
  2 0x00d555b1 in nwn2main (+0x9555b0) (0x013528bc)
  3 0x00d5f4d5 in nwn2main (+0x95f4d4) (0x01359254)
  4 0x0c2c70fa (0x01062760)
  5 0x00000000 (0x00c3124c)
  6 0xf18b5601 (0x042444f6)

```

---

### Post by cogadh on 2010-05-21
Today must be the day for NWN2. 

Did you follow the limited how-to listed here:
[http://appdb.winehq.org/objectManager.php?sClass=application&iId=4118](http://appdb.winehq.org/objectManager.php?sClass=application&iId=4118)

---

### Post by Nordstroemen on 2010-05-22
> **cogadh said:**
> Today must be the day for NWN2. 

Did you follow the limited how-to listed here:
[http://appdb.winehq.org/objectManager.php?sClass=application&iId=4118](http://appdb.winehq.org/objectManager.php?sClass=application&iId=4118)

Yes followed the list, and just double checked it just as a precaution.. Only point where Im in doubt is at the: 

> Use of dll overrides "devenum.dll" and "dxdiagn.dll" may be necessary  for the game to run.When i use winecfg, in libraries, i have set devenum.dll and dxdiagn.dll to 'native and 'build in' is that the correct procedure?

Else its the same problem as before..

thx for your help..

---

### Post by cogadh on 2010-05-22
That is correct, but if you set the DLL to "native" you also need to have a copy of the actual Windows DLL in your system32 directory in Wine for it to work.

---

### Post by Nordstroemen on 2010-05-24
> **cogadh said:**
> That is correct, but if you set the DLL to "native" you also need to have a copy of the actual Windows DLL in your system32 directory in Wine for it to work.

How do I do that? 

Or is there another way to configure devenum.dll and dxdiagn.dll, that im missing?

---

### Post by cogadh on 2010-05-24
If you have an existing Windows installation somewhere, just copy those DLLs from it and place them in /home/<username>/.wine/drive_c/windows/system32 to go along with the override. If you don't have an existing install of Windows, you may be able to download the DLLs somewhere; Google is your friend.

---

### Post by Nordstroemen on 2010-05-24
> **cogadh said:**
> That is correct, but if you set the DLL to "native" you also need to have a copy of the actual Windows DLL in your system32 directory in Wine for it to work.

Ok i have tried to download and unzip the .dll files you suggested but to no use (so far at least).. I am not sure if it is the right .dll files though, but perhaps you can give me a hint? When searching out there there seems to be an endless amount of .dll files to choose from, so which do I choose?

Have tried these to no avail: 
[http://www.dll-files.com/dllindex/dll-files.shtml?hal](http://www.dll-files.com/dllindex/dll-files.shtml?hal)

I have unzipped them, or rather it looks like its only one, but it doesnt work..can that be correct?

[U][[IMG]http://img256.imageshack.us/img256/6394/screenshotsystem32fileb.th.png[/IMG]]("http://img256.imageshack.us/i/screenshotsystem32fileb.png/")

  [/U] sorry for all this hassle im a newb, but thx for your patience

---

### Post by cogadh on 2010-05-24
That's the wrong DLL, you need to find devenum.dll and dxdiagn.dll. You actually can get both of those by installing DirectX in Wine, but I honestly don't recommend doing that, it has been known to break Wine. 

This is kind of a roundabout way to do it, but you could re-name your current .wine directory, create a new one by running winecfg, install DirectX in the new one, then copy the correct DLL files out of that into the old one. Once you are done with the copying, delete the new .wine directory and re-name your old one back to .wine.

---

### Post by Nordstroemen on 2010-05-24
Frightfully sry..but it is still not working :P

Have downloaded the .dll files you pointed to, but problem remains the same

[[IMG]http://img155.imageshack.us/img155/9689/devenumanddxiagndll.th.png[/IMG]]("http://img155.imageshack.us/i/devenumanddxiagndll.png/")

Quite sure i did i right, but then again, im no expert..any suggestions?

---

### Post by cogadh on 2010-05-24
Hmmm... have you applied all the updates for NWN2? You could be seeing an error broght on by the copy protection check that the game has by default and at least one of the more recent patches removed that:
[http://nwvault.ign.com/View.php?view=NWN2Articles.Detail&id=230](http://nwvault.ign.com/View.php?view=NWN2Articles.Detail&id=230)

---

### Post by Nordstroemen on 2010-05-24
Perhaps its just not meant to be.. getting an error messag allrdy when extracting the first patch; nwn2_pc_english_from100788_to102809.zip :D

[[IMG]http://img46.imageshack.us/img46/7152/downloadingpatch.th.png[/IMG]]("http://img46.imageshack.us/i/downloadingpatch.png/")

Advice needed..should I just continue patching or..?

Unzipping the patches in /home/name/.wine/drive_c/program files/Atari/Neverwinter Nights 2/patch

not working after first patch

---

### Post by Hibashira on 2011-12-05
Hey, first post! I'd hate to use it to beat a dead horse, but I kind of need a hand. I DLed NWN2 through steam since it was dirt cheap. I was able to get it up and running by over riding Devernum and dxdiag, as well as msvcr80. I also had installed vcrun2005, directx9 and dotnet 2.0. Everything ran great until I changed settings so I could play some Civ 5. Afterwards, nothing could be done to play NWN2 again. Keeps reminding me that my video RAM is insufficient and is under 128 mb. I've tried fixing it in the wine config and in winetricks, neither yield any worth. I've literally overidden all the previously overidden files and even all the d3dx files that other have suggested. When nothing seemed to work I tried to use PlayOnLinux, but it doesn't seem to recognize my vid driver's 3d acceleration. So I reinstalled my vid driver, wine POL, Winetricks, ect. redid everything, and even a complete reinstall of everything but steam doesn't seem to work. I'm kind of scratching my head here... 

I've been using Linux less than a year, I'd hate to sound like a noob, really I learn quick... any suggestions?

I'm using Oneiric, wine 1.3, and NWN2 Platinum edition final release.

Thank you very much ](*,)

---

