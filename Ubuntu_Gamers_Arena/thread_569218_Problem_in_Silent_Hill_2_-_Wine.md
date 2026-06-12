---
title: "Problem in Silent Hill 2 - Wine"
date: 2007-10-06
forum: Ubuntu Gamers Arena
---

### Post by samurailink3 on 2007-10-06
Just installed last night, worked fine under wine, set my options correctly, game ran smooth. Try to play again today, and the game keeps crashing. Here are the terminal results from wine:

```
samurailink3@FragProLaptop:~$ wine /home/samurailink3/.wine/drive_c/Program\ Files/Konami/Silent\ Hill\ 2/sh2pc.exe 
boot: 554.89M
fixme:win:EnumDisplayDevicesW ((null),0,0x33f9d4,0x00000000), stub!
fixme:d3d:IWineD3DDeviceImpl_EvictManagedResources (0x152b38) : stub
fixme:d3d:IWineD3DDeviceImpl_EvictManagedResources (0x152b38) : stub
Refresh: 60Hz
wine: Unhandled page fault on read access to 0x00000000 at address 0x7eba16ff (thread 0017), starting debugger...
Unhandled exception: page fault on read access to 0x00000000 in 32-bit code (0x7eba16ff).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:7eba16ff ESP:0033f650 EBP:0033f798 EFLAGS:00010246(   - 00      -RIZP1)
 EAX:00000000 EBX:7ebbf7f4 ECX:00000000 EDX:00000000
 ESI:0033f81c EDI:0033f69a
Stack dump:
0x0033f650:  00000090 0033f69a 0033f818 00000000
0x0033f660:  00000000 00000000 00000000 00000000
0x0033f670:  00000090 505c3a43 72676f72 46206d61
0x0033f680:  73656c69 6e6f4b5c 5c696d61 656c6953
0x0033f690:  4820746e 206c6c69 68735c32 2e637032
0x0033f6a0:  5c657865 65726944 6e497463 00747570
Backtrace:
=>1 0x7eba16ff get_app_key+0x17f() in dinput (0x0033f798)
  2 0x7ebabb52 in dinput (+0x1bb52) (0x0033fa48)
  3 0x7eba666b in dinput (+0x1666b) (0x0033fa98)
  4 0x7eba6821 in dinput (+0x16821) (0x0033fab8)
  5 0x0045819a in sh2pc (+0x5819a) (0x0033fd7c)
  6 0x00458a0d in sh2pc (+0x58a0d) (0x0033ff08)
  7 0x7b874dae in kernel32 (+0x54dae) (0x0033ffe8)
  8 0xb7eae9c7 wine_switch_to_stack+0x17() in libwine.so.1 (0x00000000)
0x7eba16ff get_app_key+0x17f in dinput: cmpl    $0,0x0(%edx)
Modules:
Module  Address                 Debug info      Name (78 modules)
PE        400000- 254b000       Export          sh2pc
PE      30000000-3006d000       Deferred        binkw32
PE      5d000000-5d054000       Deferred        msvcr70
ELF     7b800000-7b929000       Export          kernel32<elf>
  \-PE  7b820000-7b929000       \               kernel32
ELF     7bc00000-7bca0000       Deferred        ntdll<elf>
  \-PE  7bc10000-7bca0000       \               ntdll
ELF     7bf00000-7bf03000       Deferred        <wine-loader>
PE      7c080000-7c0f7000       Deferred        msvcp70
ELF     7d2eb000-7d300000       Deferred        midimap<elf>
  \-PE  7d2f0000-7d300000       \               midimap
ELF     7d300000-7d33a000       Deferred        wineoss<elf>
  \-PE  7d310000-7d33a000       \               wineoss
ELF     7d47d000-7dd03000       Deferred        libglcore.so.1
ELF     7dd03000-7dd8e000       Deferred        winex11<elf>
  \-PE  7dd10000-7dd8e000       \               winex11
ELF     7de92000-7deb8000       Deferred        msacm32<elf>
  \-PE  7dea0000-7deb8000       \               msacm32
ELF     7dfc3000-7dfdb000       Deferred        msacm32<elf>
  \-PE  7dfd0000-7dfdb000       \               msacm32
ELF     7dfdb000-7dfe0000       Deferred        libxfixes.so.3
ELF     7dfe0000-7dfe9000       Deferred        libxcursor.so.1
ELF     7dfe9000-7e006000       Deferred        imm32<elf>
  \-PE  7dff0000-7e006000       \               imm32
ELF     7e006000-7e00e000       Deferred        libxrender.so.1
ELF     7e42e000-7e4ba000       Deferred        libgl.so.1
ELF     7e4ba000-7e4bf000       Deferred        libxdmcp.so.6
ELF     7e4bf000-7e4c2000       Deferred        libxau.so.6
ELF     7e4c2000-7e5b3000       Deferred        libx11.so.6
ELF     7e5b3000-7e5c1000       Deferred        libxext.so.6
ELF     7e5c1000-7e5c6000       Deferred        libxxf86vm.so.1
ELF     7e5c6000-7e5de000       Deferred        libice.so.6
ELF     7e5de000-7e5e7000       Deferred        libsm.so.6
ELF     7e5eb000-7e5f1000       Deferred        libxrandr.so.2
ELF     7e802000-7e822000       Deferred        libexpat.so.1
ELF     7e822000-7e84d000       Deferred        libfontconfig.so.1
ELF     7e84d000-7e861000       Deferred        libz.so.1
ELF     7e861000-7e8cc000       Deferred        libfreetype.so.6
ELF     7e8cc000-7e8e0000       Deferred        lz32<elf>
  \-PE  7e8d0000-7e8e0000       \               lz32
ELF     7e8e0000-7e8fa000       Deferred        version<elf>
  \-PE  7e8f0000-7e8fa000       \               version
ELF     7e8fa000-7e944000       Deferred        dsound<elf>
  \-PE  7e900000-7e944000       \               dsound
ELF     7e944000-7ea24000       Deferred        wined3d<elf>
  \-PE  7e960000-7ea24000       \               wined3d
ELF     7ea24000-7ea4f000       Deferred        d3d8<elf>
  \-PE  7ea30000-7ea4f000       \               d3d8
ELF     7ea4f000-7ea62000       Deferred        libresolv.so.2
ELF     7ea73000-7ea91000       Deferred        iphlpapi<elf>
  \-PE  7ea80000-7ea91000       \               iphlpapi
ELF     7ea91000-7eaea000       Deferred        rpcrt4<elf>
  \-PE  7eaa0000-7eaea000       \               rpcrt4
ELF     7eaea000-7eb8b000       Deferred        ole32<elf>
  \-PE  7eb00000-7eb8b000       \               ole32
ELF     7eb8b000-7ebc1000       Export          dinput<elf>
  \-PE  7eb90000-7ebc1000       \               dinput
ELF     7ebc1000-7ebda000       Deferred        dinput8<elf>
  \-PE  7ebd0000-7ebda000       \               dinput8
ELF     7ebda000-7ec23000       Deferred        advapi32<elf>
  \-PE  7ebf0000-7ec23000       \               advapi32
ELF     7ec23000-7ecbe000       Deferred        gdi32<elf>
  \-PE  7ec40000-7ecbe000       \               gdi32
ELF     7ecbe000-7edfc000       Deferred        user32<elf>
  \-PE  7ece0000-7edfc000       \               user32
ELF     7edfc000-7ee8a000       Deferred        winmm<elf>
  \-PE  7ee10000-7ee8a000       \               winmm
ELF     7ef9c000-7efa7000       Deferred        libnss_files.so.2
ELF     7efa7000-7efb1000       Deferred        libnss_nis.so.2
ELF     7efb1000-7efc8000       Deferred        libnsl.so.1
ELF     7efc8000-7efef000       Deferred        libm.so.6
ELF     7eff7000-7f000000       Deferred        libnss_compat.so.2
ELF     b7d30000-b7d32000       Deferred        libnvidia-tls.so.1
ELF     b7d39000-b7d3d000       Deferred        libdl.so.2
ELF     b7d3d000-b7e7e000       Deferred        libc.so.6
ELF     b7e7f000-b7e96000       Deferred        libpthread.so.0
ELF     b7ea7000-b7fbb000       Export          libwine.so.1
ELF     b7fbd000-b7fd8000       Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
00000016 (D) C:\Program Files\Konami\Silent Hill 2\sh2pc.exe
        00000019    0
        00000018    0
        00000017    0 <==
0000000f 
        00000011    0
        00000010    0
0000000a 
        0000000c    0
        0000000b    0

```

I reinstalled the game this morning, played about 3 hours of it, worked perfectly. But then exited, and now its not working anymore. Any suggestions would be appreciated. Thanks :)  !!

---

### Post by cogadh on 2007-10-07
When you launched the game after installing it, how did you launch it; i.e. was there a "Launch game" option at the end of the install, or did you manually launch it from the terminal?

Also, when you launch the game, you should cd to the game's directory before launching:
```
cd /home/samurailink3/.wine/drive_c/Program\ Files/Konami/Silent\ Hill\ 2/
wine sh2pc.exe
```
Windows applications (especially games) often need to be run in their install directories, otherwise the executable might have trouble finding the necessary data files and resources.

---

### Post by samurailink3 on 2007-10-07
Yea, I did cd into the directory beforehand, and it was a direct launch through the terminal.

---

### Post by cogadh on 2007-10-07
What you posted before did not indicate that you had cd'd to the game's install directory, are you certain you actually did that? 

You posted that you ran the game like this:
```
wine /home/samurailink3/.wine/drive_c/Program\ Files/Konami/Silent\ Hill\ 2/sh2pc.exe
```
Not like this:
```
cd /home/samurailink3/.wine/drive_c/Program\ Files/Konami/Silent\ Hill\ 2/
wine sh2pc.exe
```
Also, how do you currently have Wine configured (OS version, sound settings, graphics settings, etc.)? Have you applied any special registry edits?

Lastly, it appears that the game has inconsistent performance with Wine. In the past it has received bronze and garbage ratings on AppDB, while the two most recent results report it as gold (both submitted by the same person however):
[http://appdb.winehq.org/objectManager.php?sClass=version&iId=4525](http://appdb.winehq.org/objectManager.php?sClass=version&iId=4525)

---

### Post by samurailink3 on 2007-10-08
Hmm.. Just tried it again, and I honestly remember cd'ing into the silent hill directory at one point or another and having it crash. But I just tried it again, and it worked :) . I've got my wine settings set to Win2000, Graphics are "Allow the window manager... = Yes, Vertex Shader = Hardware, Allow Pixel Shader = Yes" Sound = OSS. It appears that the game is working just fine for now, but I'll make another post if I run into problems. Thanks for the help :) I had no idea that cd'ing could make such a huge difference!

---

