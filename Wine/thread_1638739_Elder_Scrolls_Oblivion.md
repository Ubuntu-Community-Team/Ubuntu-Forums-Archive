---
title: "Elder Scrolls: Oblivion"
date: 2010-12-06
forum: Wine
---

### Post by Zelse on 2010-12-06
Hello all!

I've heard how great the community for ubuntu is and hopefully you can help me. I finally dove right into linux and am loving it.

However, I am having some trouble getting wine to install Oblivion.

I consider my ability/knowledge of computers to be medium-high, and I'm fairly unfamiliar with linux, but am learning fast.

Specs: Q6600@3.2Ghz
           4GB DDR2 800mhz RAM
           XFX (NVidia) 9600GT (512mb)
           Ubuntu 10.10 64-bit
            Wine 1.2.1
            Oblivion GOTY Edition DVD

I've checked around and followed most of the instructions I could find. I added a new wine drive to "Media/Oblivion GOTY 1".

At first when attempting to run setup.exe, it froze my computer and I had to reboot.

then I did some more research and installed d3dx9 (or whatever) using winetricks.

Now I  seem to get a 50/50 chance of having it freeze, or I get an error message saying "Setup.exe has encountered a problem and has to close etc."

When running in the terminal, this is what it spits out:

aric@ubuntu:/media/Oblivion GOTY 1$ wine setup.exe
fixme:ntdll:NtQuerySystemInformation info_class SYSTEM_HANDLE_INFORMATION
fixme:ntdll:NtQueryObject Unsupported information class 3
err:rpc:I_RpcGetBuffer no binding
fixme:win:EnumDisplayDevicesW ((null),0,0xed8fb0,0x00000000), stub!
wine: Unhandled page fault on read access to 0xffffffff at address 0xffffffff (thread 0009), starting debugger...
Unhandled exception: page fault on read access to 0xffffffff in 32-bit code (0xffffffff).
Register dump:
 CS:0023 SS:002b DS:002b ES:002b FS:0063 GS:006b
 EIP:ffffffff ESP:00ed8874 EBP:00000001 EFLAGS:00010286(  R- --  I S - -P- )
 EAX:ffffffff EBX:00000000 ECX:7ce88148 EDX:00000001
 ESI:7cfd3b90 EDI:00000008
Stack dump:
0x00ed8874:  7d7716c7 00000000 7ce88148 7cfd3b90
0x00ed8884:  00000001 f75743c0 f7572ff4 f75743c0
0x00ed8894:  7ce88148 00000000 00000001 00000001
0x00ed88a4:  00000000 7cfd3b90 00000055 7cf066fc
0x00ed88b4:  7d771bb6 00000000 7ce88148 7cfd3b90
0x00ed88c4:  00000001 0001a848 00000001 00000001
Backtrace:
0xffffffff: -- no code accessible --
Modules:
Module    Address            Debug info    Name (77 modules)
PE      400000-  cf0000    Deferred        setup
ELF    7b800000-7b971000    Deferred        kernel32<elf>
  \-PE    7b810000-7b971000    \               kernel32
ELF    7bc00000-7bcb7000    Deferred        ntdll<elf>
  \-PE    7bc10000-7bcb7000    \               ntdll
ELF    7bf00000-7bf04000    Deferred        <wine-loader>
ELF    7d189000-7dec9000    Deferred        libglcore.so.1
ELF    7dec9000-7df6d000    Deferred        libgl.so.1
ELF    7df86000-7e0be000    Deferred        wined3d<elf>
  \-PE    7df90000-7e0be000    \               wined3d
ELF    7e0be000-7e0f2000    Deferred        d3d9<elf>
  \-PE    7e0c0000-7e0f2000    \               d3d9
ELF    7e18a000-7e1be000    Deferred        uxtheme<elf>
  \-PE    7e190000-7e1be000    \               uxtheme
ELF    7e1be000-7e1c8000    Deferred        libxcursor.so.1
ELF    7e1c8000-7e1ce000    Deferred        libxfixes.so.3
ELF    7e1ce000-7e1d2000    Deferred        libxcomposite.so.1
ELF    7e1d2000-7e1da000    Deferred        libxrandr.so.2
ELF    7e1da000-7e1e4000    Deferred        libxrender.so.1
ELF    7e1e4000-7e1ea000    Deferred        libxxf86vm.so.1
ELF    7e1ea000-7e1ee000    Deferred        libxinerama.so.1
ELF    7e1ee000-7e20f000    Deferred        imm32<elf>
  \-PE    7e1f0000-7e20f000    \               imm32
ELF    7e20f000-7e215000    Deferred        libxdmcp.so.6
ELF    7e215000-7e219000    Deferred        libxau.so.6
ELF    7e219000-7e233000    Deferred        libxcb.so.1
ELF    7e233000-7e238000    Deferred        libuuid.so.1
ELF    7e238000-7e355000    Deferred        libx11.so.6
ELF    7e355000-7e365000    Deferred        libxext.so.6
ELF    7e365000-7e37e000    Deferred        libice.so.6
ELF    7e37e000-7e387000    Deferred        libsm.so.6
ELF    7e39c000-7e39e000    Deferred        libnvidia-tls.so.1
ELF    7e3a0000-7e441000    Deferred        winex11<elf>
  \-PE    7e3b0000-7e441000    \               winex11
ELF    7e470000-7e497000    Deferred        libexpat.so.1
ELF    7e497000-7e4c7000    Deferred        libfontconfig.so.1
ELF    7e4c7000-7e4dc000    Deferred        libz.so.1
ELF    7e4dc000-7e553000    Deferred        libfreetype.so.6
ELF    7e553000-7e567000    Deferred        libresolv.so.2
ELF    7e580000-7e5a0000    Deferred        iphlpapi<elf>
  \-PE    7e590000-7e5a0000    \               iphlpapi
ELF    7e5a0000-7e5cd000    Deferred        ws2_32<elf>
  \-PE    7e5b0000-7e5cd000    \               ws2_32
ELF    7e5cd000-7e5e8000    Deferred        wsock32<elf>
  \-PE    7e5d0000-7e5e8000    \               wsock32
ELF    7e5e8000-7e6cf000    Deferred        oleaut32<elf>
  \-PE    7e600000-7e6cf000    \               oleaut32
ELF    7e6cf000-7e742000    Deferred        rpcrt4<elf>
  \-PE    7e6e0000-7e742000    \               rpcrt4
ELF    7e742000-7e840000    Deferred        ole32<elf>
  \-PE    7e760000-7e840000    \               ole32
ELF    7e840000-7e92a000    Deferred        comctl32<elf>
  \-PE    7e850000-7e92a000    \               comctl32
ELF    7e92a000-7e98b000    Deferred        shlwapi<elf>
  \-PE    7e940000-7e98b000    \               shlwapi
ELF    7e98b000-7eb68000    Deferred        shell32<elf>
  \-PE    7e9a0000-7eb68000    \               shell32
ELF    7eb68000-7ebc2000    Deferred        advapi32<elf>
  \-PE    7eb70000-7ebc2000    \               advapi32
ELF    7ebc2000-7ec4d000    Deferred        gdi32<elf>
  \-PE    7ebd0000-7ec4d000    \               gdi32
ELF    7ec4d000-7ed7d000    Deferred        user32<elf>
  \-PE    7ec60000-7ed7d000    \               user32
ELF    7ed7d000-7ed91000    Deferred        lz32<elf>
  \-PE    7ed80000-7ed91000    \               lz32
ELF    7ed91000-7edaa000    Deferred        version<elf>
  \-PE    7eda0000-7edaa000    \               version
ELF    7efaa000-7efb6000    Deferred        libnss_files.so.2
ELF    7efb6000-7efc1000    Deferred        libnss_nis.so.2
ELF    7efc1000-7efe7000    Deferred        libm.so.6
ELF    7efe9000-7f000000    Deferred        libnsl.so.1
ELF    f7410000-f7418000    Deferred        libnss_compat.so.2
ELF    f7419000-f741d000    Deferred        libdl.so.2
ELF    f741d000-f7577000    Deferred        libc.so.6
ELF    f7578000-f7591000    Deferred        libpthread.so.0
ELF    f75aa000-f76ea000    Deferred        libwine.so.1
ELF    f76ec000-f770a000    Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
00000008 (D) D:\setup.exe
    00000009    0 <==
0000000e services.exe
    00000014    0
    00000010    0
    0000000f    0
00000011 winedevice.exe
    00000018    0
    00000017    0
    00000013    0
    00000012    0
00000023 explorer.exe
    00000024    0
00000028 winecfg.exe
    00000029    0
Backtrace:


Any insight would be much appreciated as I would love to get this working. Cookies for a fix :D

---

### Post by benmoran on 2010-12-06
Try PlayOnLinux. It's a frontend for wine, that includes a lot of specific profiles for games. Oblivion is one of them.

---

### Post by handy on 2010-12-06
Also, the [**_UESPWiki_**]("http://www.uesp.net/wiki/Oblivion:Oblivion") has [**_this how-to_**]("http://www.uesp.net/wiki/Oblivion:Linux") written by Mongoose. It was originally written for this forum so you'll find it here if you search for Oblivion. 

The one on the Wiki is easier to use than the one here due to it being wiki indexed.

---

### Post by Zelse on 2010-12-06
@ Benmoren Thanks for that, I'll try it.

@ Handy, The UESP wiki instructions are the main set that I followed, But I appreciate the response this late.

---

### Post by Zelse on 2010-12-06
Alright, It seems securom is my problem. I don't think POL is compatible with it, so I'm going to try and download a backup copy (seeing as I already paid for it), which will hopefully not have this issue. I will keep this thread updated as to my progress.

---

### Post by Sugi on 2010-12-06
Hello Zelse,
I have recently tried Oblivion on Linux again through Wine.  I was able to get it running and playable with very little tweaks.  

Just a couple of tips, try the newest wine version. This is always helpful, because they patch of past erros and bugs [duh XD].  Try coping the game from your windows partition, if you are having issues with installation this is just one less headache you need to worry about.  Then try some quick regedit[s], these are always helpful and most of the time they are the answers to your problem.

Lastly, check the appdb for a howto or tutorial. Just keep in mind, they can be extremely outdated.
[http://appdb.winehq.org/objectManager.php?sClass=version&iId=7506]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=7506")

Now, the results of my testing with Oblivion. I was kind disappointed comparing it to Windows. I was not able to handle full settings and I got some crashes.  I wasn't able to fix the crashes and the performances lost was kind annoying.  Except for those minor set backs, it's completely playable and others has gotten a lot better results.

Good luck with your project and hopefully this was helpful,
Sugi

---

### Post by Zelse on 2010-12-06
Thank you all for the aid thus far.

So through POL I am able to get Oblivion and all the DLC installed. When I click run it opens the Launcher fine. However, when I click play, It either freezes, or gives me a "Invalid parameter" type message. 

I'm determined to get this, and will keep looking, but any insight would be very much appreciated.

---

### Post by Zelse on 2010-12-06
I was able to get into the main menu finally. Started mucking about with settings (mostly changing my resolution to 1680x1050. Restarted to apply changes and system crashed.

Maybe have wine emulate a virtual desktop at this resolution?

---

### Post by Sugi on 2010-12-06
Zelse, Please use the edit button to update your post instead of posting mutliple times.

---

### Post by Zelse on 2010-12-06
Sorry :/

Anyway, I can now get into the game and it is somewhat playable (I use POL to simulate a windows reboot until it opens), but whenever I am attacked by something, my screen flashes black and my menus are weird. It also doesn't want to load the interior cell immediately after the first one.

---

### Post by iiiears on 2010-12-06
Check your disk again for a fingerprint/scratch.

TES works pretty well on WINE but once it is installed changing the settings to something more intensive than their initial defaults can crash TES and make adjustment menus impossible to reach without re-installing.

I haven't tried installing from a windows zipped file. (Add-ons take some time to install and adjust don't they?.. lol)

Best wishes.

---

### Post by Zelse on 2010-12-07
Thanks. Is there a way to open it in windowed mode? By default it opens in fullscreen. If I can do this then the default resolution wouldn't look so unplayable.

---

### Post by Sugi on 2010-12-10
Winecfg > emulate desktop
or
wine explorer /desktop=TES,800x600 Game.exe

If not, just edit the config file for Oblivion and you should be fine.

Sugi

---

