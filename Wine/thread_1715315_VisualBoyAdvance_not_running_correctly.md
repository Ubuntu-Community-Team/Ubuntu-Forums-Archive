---
title: "VisualBoyAdvance not running correctly"
date: 2011-03-26
forum: Wine
---

### Post by carega on 2011-03-26
Hi, I'm  kinda really new with ubuntu and would like to run my gba games using visualboyadvance. I ran the windows version using wine and had this problem at first:

```
carega@amaterasu:~/Documentos/juegos/gba$ wine VisualBoyAdvance.exe
err:module:import_dll Library MFC42.DLL (which is needed by L"Z:\\home\\carega\\Documentos\\juegos\\gba\\VisualBoyAdvance.exe") not found
err:module:LdrInitializeThunk Main exe initialization for L"Z:\\home\\carega\\Documentos\\juegos\\gba\\VisualBoyAdvance.exe" failed, status c0000135

```So I looked up mfc42.dll, downloaded it and the emulator ran succesfully. I tried to open a file though and this happened:

```
carega@amaterasu:~/Documentos/juegos/gba$ wine VisualBoyAdvance.exe
err:winediag:X11DRV_WineGL_InitOpenglInfo Direct rendering is disabled, most likely your OpenGL drivers haven't been installed correctly
fixme:win:EnumDisplayDevicesW ((null),0,0x32ea58,0x00000000), stub!
fixme:menu:GetMenuBarInfo (0x2009c,0xfffffffd,0x00000000,0x32f9a4)
fixme:menu:GetMenuBarInfo (0x2009c,0xfffffffd,0x00000000,0x32f9bc)
fixme:menu:GetMenuBarInfo (0x2009c,0xfffffffd,0x00000000,0x32f9bc)
wine: Call from 0x7bc49f00 to unimplemented function MFC42.DLL.6876, aborting
wine: Unimplemented function MFC42.DLL.6876 called at address 0x7bc49f00 (thread 0009), starting debugger...
Unhandled exception: unimplemented function MFC42.DLL.6876 called in 32-bit code (0x7bc49f00).
err:dbghelp:pe_load_dbg_file Couldn't find .DBG file "MFC42.dbg" ("")
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:7bc49f00 ESP:0032f8d4 EBP:0032f938 EFLAGS:00000202(   - --  I   - - - )
 EAX:00001adc EBX:7bc9aff4 ECX:0032f970 EDX:0017a918
 ESI:0032f8e0 EDI:00175918
Stack dump:
0x0032f8d4:  7b8649a0 0032f8f8 7b8649d3 80000100
0x0032f8e4:  00000001 00000000 7bc49f00 00000002
0x0032f8f4:  00516fa8 00001adc 5f40889a 00400000
0x0032f904:  00000045 00000006 00175918 00000445
0x0032f914:  0032fa1c 00000001 5f40e6f1 0017a918
0x0032f924:  5f401756 0017a918 0032f970 00000001
Backtrace:
=>0 0x7bc49f00 in ntdll (+0x39f00) (0x0032f938)
  1 0x0033003c (0x0032fa1c)
  2 0x5f4039db in mfc42 (+0x39da) (0x0032fa4c)
  3 0x5f411e08 in mfc42 (+0x11e07) (0x0032fa9c)
  4 0x5f4023ed in mfc42 (+0x23ec) (0x0032fb1c)
  5 0x5f40230b in mfc42 (+0x230a) (0x0032fb3c)
  6 0x5f402294 in mfc42 (+0x2293) (0x0032fb9c)
  7 0x5f40221f in mfc42 (+0x221e) (0x0032fbb8)
  8 0x5f4021d6 in mfc42 (+0x21d5) (0x0032fbe4)
  9 0x6838711a WINPROC_wrapper+0x19() in user32 (0x0032fc14)
  10 0x68388c2c in user32 (+0x98c2b) (0x0032fc64)
  11 0x68389f7f in user32 (+0x99f7e) (0x0032fcb4)
  12 0x6834dd6e DispatchMessageA+0x9d() in user32 (0x0032fda4)
  13 0x5f40133b in mfc42 (+0x133a) (0x005d08a4)
  14 0x00000111 (0x0002009c)
0x7bc49f00: subl    $4,%esp
Modules:
Module    Address            Debug info    Name (103 modules)
PE      400000-  737000    Deferred        visualboyadvance
ELF    20000000-20138000    Deferred        wined3d<elf>
  \-PE    20010000-20138000    \               wined3d
ELF    20138000-20171000    Deferred        dinput<elf>
  \-PE    20140000-20171000    \               dinput
PE    5f400000-5f4ed000    Export          mfc42
ELF    68000000-6801e000    Deferred        ld-linux.so.2
ELF    6801e000-6815e000    Deferred        libwine.so.1
ELF    6815e000-68178000    Deferred        libpthread.so.0
ELF    68178000-6817c000    Deferred        libdl.so.2
ELF    6817c000-681a2000    Deferred        libm.so.6
ELF    681a2000-681ad000    Deferred        libnss_nis.so.2
ELF    681ad000-681b9000    Deferred        libnss_files.so.2
ELF    681b9000-681d9000    Deferred        iphlpapi<elf>
  \-PE    681c0000-681d9000    \               iphlpapi
ELF    681d9000-681ed000    Deferred        libresolv.so.2
ELF    681ed000-68247000    Deferred        advapi32<elf>
  \-PE    68200000-68247000    \               advapi32
ELF    68247000-682db000    Deferred        winmm<elf>
  \-PE    68250000-682db000    \               winmm
ELF    682db000-6840b000    Export          user32<elf>
  \-PE    682f0000-6840b000    \               user32
ELF    6840b000-68496000    Deferred        gdi32<elf>
  \-PE    68420000-68496000    \               gdi32
ELF    68496000-684d3000    Deferred        avifil32<elf>
  \-PE    684a0000-684d3000    \               avifil32
ELF    684d3000-684fa000    Deferred        msacm32<elf>
  \-PE    684e0000-684fa000    \               msacm32
ELF    684fa000-68521000    Deferred        msvfw32<elf>
  \-PE    68500000-68521000    \               msvfw32
ELF    68521000-6860c000    Deferred        comctl32<elf>
  \-PE    68530000-6860c000    \               comctl32
ELF    6860c000-6870a000    Deferred        ole32<elf>
  \-PE    68620000-6870a000    \               ole32
ELF    6870a000-6877d000    Deferred        rpcrt4<elf>
  \-PE    68720000-6877d000    \               rpcrt4
ELF    6877d000-68821000    Deferred        opengl32<elf>
  \-PE    68790000-68821000    \               opengl32
ELF    68821000-6882a000    Deferred        libsm.so.6
ELF    6882a000-68843000    Deferred        libice.so.6
ELF    68843000-68853000    Deferred        libxext.so.6
ELF    68853000-68970000    Deferred        libx11.so.6
ELF    68970000-68a34000    Deferred        libgl.so.1
ELF    68a34000-68a4e000    Deferred        libxcb.so.1
ELF    68a4e000-68a56000    Deferred        libatiuki.so.1
ELF    68a56000-68a72000    Deferred        libgcc_s.so.1
ELF    68a72000-68a78000    Deferred        libxdmcp.so.6
ELF    68a78000-68af8000    Deferred        msvcrt<elf>
  \-PE    68a90000-68af8000    \               msvcrt
ELF    68af8000-68bb6000    Deferred        comdlg32<elf>
  \-PE    68b00000-68bb6000    \               comdlg32
ELF    68bb6000-68d8f000    Deferred        shell32<elf>
  \-PE    68bc0000-68d8f000    \               shell32
ELF    68d8f000-68df0000    Deferred        shlwapi<elf>
  \-PE    68da0000-68df0000    \               shlwapi
ELF    68df0000-68e27000    Deferred        winspool<elf>
  \-PE    68e00000-68e27000    \               winspool
ELF    68e27000-68e9e000    Deferred        libfreetype.so.6
ELF    68e9e000-68f40000    Deferred        winex11<elf>
  \-PE    68eb0000-68f40000    \               winex11
ELF    68f40000-68f61000    Deferred        imm32<elf>
  \-PE    68f50000-68f61000    \               imm32
ELF    68f61000-68f65000    Deferred        libxinerama.so.1
ELF    68f65000-68f6b000    Deferred        libxxf86vm.so.1
ELF    68f6b000-68f75000    Deferred        libxrender.so.1
ELF    68f75000-68f7d000    Deferred        libxrandr.so.2
ELF    68f7d000-68f81000    Deferred        libxcomposite.so.1
ELF    68f81000-68f87000    Deferred        libxfixes.so.3
ELF    68f87000-68fbb000    Deferred        uxtheme<elf>
  \-PE    68f90000-68fbb000    \               uxtheme
ELF    68fbb000-69005000    Deferred        libcups.so.2
ELF    69005000-69034000    Deferred        libgssapi_krb5.so.2
ELF    69034000-690a8000    Deferred        libgcrypt.so.11
ELF    690a8000-690b4000    Deferred        libavahi-common.so.3
ELF    690b4000-690c4000    Deferred        libavahi-client.so.3
ELF    690c4000-69173000    Deferred        libkrb5.so.3
ELF    69173000-69197000    Deferred        libk5crypto.so.3
ELF    69197000-6919b000    Deferred        libcom_err.so.2
ELF    6919b000-691a3000    Deferred        libkrb5support.so.0
ELF    691a3000-691a7000    Deferred        libkeyutils.so.1
ELF    691a7000-691b8000    Deferred        libtasn1.so.3
ELF    691b8000-691f4000    Deferred        libdbus-1.so.3
ELF    691f4000-691fd000    Deferred        librt.so.1
ELF    6935b000-69360000    Deferred        libgpg-error.so.0
ELF    6acdf000-6ace4000    Deferred        libuuid.so.1
ELF    6fa70000-6fa97000    Deferred        libexpat.so.1
ELF    6fbe2000-6fc7d000    Deferred        libgnutls.so.26
ELF    70989000-7098d000    Deferred        libxau.so.6
ELF    71139000-7114e000    Deferred        libz.so.1
ELF    72888000-728b5000    Deferred        ws2_32<elf>
  \-PE    72890000-728b5000    \               ws2_32
ELF    7474d000-74768000    Deferred        wsock32<elf>
  \-PE    74750000-74768000    \               wsock32
ELF    7517f000-751af000    Deferred        libfontconfig.so.1
ELF    779aa000-779c1000    Deferred        libnsl.so.1
ELF    77e86000-77fe3000    Deferred        libc.so.6
ELF    79efa000-79f02000    Deferred        libnss_compat.so.2
ELF    7a2d2000-7a2dc000    Deferred        libxcursor.so.1
ELF    7b800000-7b97b000    Deferred        kernel32<elf>
  \-PE    7b810000-7b97b000    \               kernel32
ELF    7bc00000-7bcb7000    Export          ntdll<elf>
  \-PE    7bc10000-7bcb7000    \               ntdll
ELF    7bf00000-7bf04000    Deferred        <wine-loader>
Threads:
process  tid      prio (all id:s are in hex)
00000008 (D) Z:\home\carega\Documentos\juegos\gba\VisualBoyAdvance.exe
    0000001c    0
    00000009    2 <==
0000000e services.exe
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
=>0 0x7bc49f00 in ntdll (+0x39f00) (0x0032f938)
  1 0x0033003c (0x0032fa1c)
  2 0x5f4039db in mfc42 (+0x39da) (0x0032fa4c)
  3 0x5f411e08 in mfc42 (+0x11e07) (0x0032fa9c)
  4 0x5f4023ed in mfc42 (+0x23ec) (0x0032fb1c)
  5 0x5f40230b in mfc42 (+0x230a) (0x0032fb3c)
  6 0x5f402294 in mfc42 (+0x2293) (0x0032fb9c)
  7 0x5f40221f in mfc42 (+0x221e) (0x0032fbb8)
  8 0x5f4021d6 in mfc42 (+0x21d5) (0x0032fbe4)
  9 0x6838711a WINPROC_wrapper+0x19() in user32 (0x0032fc14)
  10 0x68388c2c in user32 (+0x98c2b) (0x0032fc64)
  11 0x68389f7f in user32 (+0x99f7e) (0x0032fcb4)
  12 0x6834dd6e DispatchMessageA+0x9d() in user32 (0x0032fda4)
  13 0x5f40133b in mfc42 (+0x133a) (0x005d08a4)
  14 0x00000111 (0x0002009c)
wine: Call from 0x7bc49f00 to unimplemented function MFC42.DLL.6876, aborting
wine: Call from 0x7bc49f00 to unimplemented function MFC42.DLL.6876, aborting
Terminado (killed)

```Can anyone tell me what is going on or how can I fix this? Thank you!

---

### Post by cogadh on 2011-03-26
That mfc42.dll file is part of Visual C++ Runtime, so just copying that alone might not be enough. You should use winetricks to install the full runtime package instead: [http://wiki.winehq.org/winetricks](http://wiki.winehq.org/winetricks)

However, there appears to be a bigger problem in that error trail:
```
err:winediag:X11DRV_WineGL_InitOpenglInfo Direct rendering is disabled, most likely your OpenGL drivers haven't been installed correctly
```
Without direct rendering, even a GBA emulator might never work. What do you have for a video card/chipset?

---

### Post by carega on 2011-03-26
I have no idea what my video card/chipset is. Where can I look?

So I should install visualboyadvance  through winetricks? is that what you're telling me? I'm not really clear about this, please bear with me: I'm really new at linux.

---

### Post by cogadh on 2011-03-26
Run this in a terminal to find out what your video card/chipset is:
```
lspci | grep VGA
```
It should spit out something like this:
```
01:00.0 VGA compatible controller: nVidia Corporation GT218 [GeForce G210M] (rev a2)
```
Obviously the actual details of yours will be different, unless you happen to have that same exact graphics card.

No, not install visualboyadvance, you should install Visual C++ Runtime with winetricks, instead of simply copying the mfc42.dll file.

EDIT - I just noticed that there is a Linux native version of VisualBoyAdvance, you might have better luck trying that instead of going through Wine.

---

### Post by carega on 2011-03-26
About the graphics card:

```
carega@amaterasu:~$ lspci | grep VGA
01:05.0 VGA compatible controller: ATI Technologies Inc RS780M/RS780MN [Radeon HD 3200 Graphics]

```

I tried playing the linux version of visualboy but it was way too slow and the sound was choppy. I read that it runs faster on wine, that's why I'm giving it a shot.

---

### Post by cogadh on 2011-03-26
Okay, then you need to install the drivers for your video card. Go to System > Administration > Additional Drivers, it should detect your card and it will offer you the correct drivers to install.

---

### Post by carega on 2011-03-27
Sorry I took so long to reply, I was without internet until recently.

Regarding the graphics card, i did what you told me and it seems I already have a graphic controller for the card. It's named "Graphic controller FGLRX for ATI/AMD"

I downloaded winetricks but i don't know how to install Visual C++ Runtime nor what to do with the program. I feel like I'm being a pain for asking for so much instructions but I'm really new at this thing. Thank you for helping me!

---

### Post by cogadh on 2011-03-30
There is a link to the winetricks instructions in my very first post.

ATI graphics can be a pain in Linux and the open source driver is not really the greatest. You might try going for the ATI proprietary driver instead:
[http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.42&lang=English](http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.42&lang=English)

---

### Post by carega on 2011-03-30
I read the link and all, so I assume the library I should install is this:

```
vcrun6        MS Visual C++ 6 sp4 libraries (mfc42, msvcp60, msvcrt)
```

right?

I'm gonna go install the ATI propietary driver now, so I'll let you know if anything happens. Thanks for your help!

---

### Post by carega on 2011-03-31
I'm really sorry for being such a pain, but I have no idea how to install the ATI propietary driver. I downloaded it and double-clicked it (as any ex-windows user would do) and couldn't install anything. Can you tell me how to do it? Thanks in advance.

---

### Post by cogadh on 2011-03-31
First, mark the driver install package as executable (right-click on it, Properties > Permissions, check the "Allow executing..." box) then open a terminal, change directories to where you downloaded the driver, then run it with sudo permissions:
```
sudo ./ati-driver-installer-11-3-x86.x86_64.run
```

For winetricks, that is the correct library, just open a terminal and run this:
```
winetricks vcrun6
```

---

### Post by carega on 2011-03-31
Ok, I did both installations and everything is kinda running slower. Should I use the option Tear Free Desktop on the ATI Control Center? 

Also, now that I have the new ATI controller the wine-visualboyadvance won't open at all. Before, it opened but everytime I wanted to use the option "open" on the menu to load a new game, the program crashed. Did the graphics card controller install incorrectly or what?

EDIT: I selectged to use the Tear Free Desktop and now I can't even open the Control Center? What's going on? Can I uninstall this? How?

---

### Post by cogadh on 2011-03-31
Not sure why it is misbehaving, just run this to get rid of it:
```
sudo sh /usr/share/ati/fglrx-uninstall.sh
```

More information on it, as well as more complex but arguably safer method of installation can be found here:
[http://wiki.cchtml.com/index.php/Ubuntu_Maverick_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Maverick_Installation_Guide)

---

### Post by carega on 2011-03-31
I can't uninstall:

```
sh: Can't open /usr/shar/ati/fglrx-uninstall.sh 
```I tried looking for the file fglrx-uninstall.sh to change the route but was unable to find it.

EDIT: never mind! typo on "shar". I think I'm gonna give up on playing visualboyadvance through wine and start getting help playing the linux version, since it runs just fine except it goes slow. Thanks anyway!

---

### Post by carega on 2011-03-31
Ok, I'm now in panic. I can't open the user interface at my computer. I rebooted it after uninstalling the driver and now I can't see anything! everything is just like a really big terminal. What do I do now?

I tried sudo gnome-panel but it displayed this:

```
 (gnome-panel:1434): Gtk-WARNING **: cannot open display: 
```

I'm on a friend's computer right now. What can I do to have my screen as it was before?

---

### Post by cogadh on 2011-03-31
That shouldn't have happened. Type "startx" at the terminal and post back with results.

---

### Post by carega on 2011-04-01
Tried "startx" and was unable to do anything. Then I did the following, based on a thread i read:

sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.backup

I then was able to log in, using startx. What did I exactly do there? And also, is the ATI controller still installed? I'd like to know.

---

