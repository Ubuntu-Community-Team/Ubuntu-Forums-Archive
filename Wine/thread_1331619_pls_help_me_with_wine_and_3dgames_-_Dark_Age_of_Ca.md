---
title: "pls help me with wine and 3dgames - Dark Age of Camelot don't work :("
date: 2009-11-19
forum: Wine
---

### Post by realac0 on 2009-11-19
heya all, first of all sry for my english (i'am italian).
i am a ubuntu user from 4/5 mounths, all ok, now running Karmic 64bit
Proc E8400
ATI radeon 5850 (just changed, maybe my old nvidia 9800gx2 was better for ubuntu)
i have just installed catalyst 9.11
and running wine 1.1.32

i have installed directx9c and if i test with dxdiag on wine directory all work 100% perfectly

problem is that, anyway, i can't run 3d games, even if on WineApps the game is listed like "working"

GTR2 and many others, don't work

now i am trying from 2 days with Dark Age of Camelot, listed as "working" and listed on playonlinux too.

all installation goes ok, connection work, server list work, but when i try to start with a character i have errors.

i try to post what terminal give me while running the game, hoping someone here can help me understand why all can run some games on ubuntu than me :(

this is what happen on terminal when the game crash:

```
wine: Unhandled page fault on read access to 0x00000014 at address 0x7a777b7c (thread 0019), starting debugger...
Unhandled exception: page fault on read access to 0x00000014 in 32-bit code (0x7a777b7c).
Register dump:
 CS:0023 SS:002b DS:002b ES:002b FS:0063 GS:006b
 EIP:7a777b7c ESP:0033ec7c EBP:00000000 EFLAGS:00210246(  R- --  I  Z- -P- )
 EAX:00000001 EBX:00000000 ECX:00000000 EDX:00000000
 ESI:0000000b EDI:7c719e00
Stack dump:
0x0033ec7c:  7a8f7859 00000000 7c81d798 7c507460
0x0033ec8c:  00000000 00000000 00000000 0000000b
0x0033ec9c:  7a8f7605 7c719e00 7a7651f8 00000029
0x0033ecac:  7b7a9894 0000000b 7b7af824 7c719ea0
0x0033ecbc:  00000000 7c9746d8 7d463b38 7c7843d8
0x0033eccc:  00000000 00000000 7a7672a4 7c719e00
Backtrace:
=>0 0x7a777b7c in fglrx_dri.so (+0x817b7c) (0x00000000)
0x7a777b7c: movl    0x14(%edx),%eax
Modules:
Module    Address            Debug info    Name (120 modules)
PE      3a0000-  3bb000    Deferred        mssds3d.m3d
PE      400000- 23b1000    Deferred        game
PE    10000000-100a4000    Deferred        libxml2
PE    21100000-21164000    Deferred        mss32
PE    22100000-22122000    Deferred        mssa3d.m3d
PE    22300000-2232c000    Deferred        msseax.m3d
PE    22400000-22419000    Deferred        msssoft.m3d
PE    22600000-2261f000    Deferred        mssdx7.m3d
PE    22700000-22768000    Deferred        mssrsx.m3d
PE    24100000-24120000    Deferred        mssdsp.flt
PE    26400000-26439000    Deferred        mssvoice.asi
PE    26f00000-26f2c000    Deferred        mssmp3.asi
ELF    79f60000-7b800000    Export          fglrx_dri.so
ELF    7b800000-7b972000    Deferred        kernel32<elf>
  \-PE    7b820000-7b972000    \               kernel32
ELF    7bc00000-7bcb3000    Deferred        ntdll<elf>
  \-PE    7bc10000-7bcb3000    \               ntdll
ELF    7bf00000-7bf04000    Deferred        <wine-loader>
ELF    7c12f000-7c17c000    Deferred        dsound<elf>
  \-PE    7c140000-7c17c000    \               dsound
ELF    7c97e000-7c9aa000    Deferred        libatiadlxx.so
ELF    7d1ca000-7d25c000    Deferred        libgl.so.1
ELF    7d25c000-7d38c000    Deferred        wined3d<elf>
  \-PE    7d270000-7d38c000    \               wined3d
ELF    7d4c6000-7d4e4000    Deferred        libgcc_s.so.1
ELF    7d503000-7d536000    Deferred        d3d9<elf>
  \-PE    7d510000-7d536000    \               d3d9
ELF    7d536000-7d54c000    Deferred        psapi<elf>
  \-PE    7d540000-7d54c000    \               psapi
ELF    7d54c000-7d561000    Deferred        midimap<elf>
  \-PE    7d550000-7d561000    \               midimap
ELF    7d561000-7d587000    Deferred        msacm32<elf>
  \-PE    7d570000-7d587000    \               msacm32
ELF    7d587000-7d59f000    Deferred        msacm32<elf>
  \-PE    7d590000-7d59f000    \               msacm32
ELF    7dda0000-7dda7000    Deferred        libogg.so.0
ELF    7dda7000-7ddd2000    Deferred        libvorbis.so.0
ELF    7ddd2000-7decc000    Deferred        libvorbisenc.so.2
ELF    7decc000-7df1c000    Deferred        libflac.so.8
ELF    7df1c000-7df55000    Deferred        libdbus-1.so.3
ELF    7df55000-7dfc1000    Deferred        libsndfile.so.1
ELF    7dfc1000-7dfca000    Deferred        libwrap.so.0
ELF    7dfca000-7dfd0000    Deferred        libxtst.so.6
ELF    7dfd0000-7e01a000    Deferred        libpulsecommon-0.9.19.so
ELF    7e01a000-7e05a000    Deferred        libpulse.so.0
ELF    7e05a000-7e063000    Deferred        librt.so.1
ELF    7e063000-7e12b000    Deferred        libasound.so.2
ELF    7e14a000-7e182000    Deferred        winealsa<elf>
  \-PE    7e150000-7e182000    \               winealsa
ELF    7e1c3000-7e1f7000    Deferred        uxtheme<elf>
  \-PE    7e1d0000-7e1f7000    \               uxtheme
ELF    7e1f7000-7e202000    Deferred        libxcursor.so.1
ELF    7e202000-7e208000    Deferred        libxfixes.so.3
ELF    7e208000-7e20c000    Deferred        libxcomposite.so.1
ELF    7e20c000-7e215000    Deferred        libxrandr.so.2
ELF    7e215000-7e21f000    Deferred        libxrender.so.1
ELF    7e21f000-7e225000    Deferred        libxxf86vm.so.1
ELF    7e225000-7e22a000    Deferred        libxdmcp.so.6
ELF    7e22a000-7e248000    Deferred        libxcb.so.1
ELF    7e248000-7e24c000    Deferred        libxau.so.6
ELF    7e24c000-7e251000    Deferred        libuuid.so.1
ELF    7e251000-7e380000    Deferred        libx11.so.6
ELF    7e380000-7e390000    Deferred        libxext.so.6
ELF    7e390000-7e3ab000    Deferred        libice.so.6
ELF    7e3ab000-7e3b4000    Deferred        libsm.so.6
ELF    7e3b4000-7e3bb000    Deferred        libasound_module_pcm_pulse.so
ELF    7e3d3000-7e472000    Deferred        winex11<elf>
  \-PE    7e3e0000-7e472000    \               winex11
ELF    7e49a000-7e4c1000    Deferred        libexpat.so.1
ELF    7e4c1000-7e4ee000    Deferred        libfontconfig.so.1
ELF    7e4ee000-7e504000    Deferred        libz.so.1
ELF    7e504000-7e583000    Deferred        libfreetype.so.6
ELF    7e583000-7e586000    Deferred        libxinerama.so.1
ELF    7e5a2000-7e5b7000    Deferred        system.drv16.so
PE    7e5b0000-7e5b7000    Deferred        system.drv16
ELF    7e5b7000-7e681000    Deferred        comctl32<elf>
  \-PE    7e5c0000-7e681000    \               comctl32
ELF    7e681000-7e811000    Deferred        shell32<elf>
  \-PE    7e690000-7e811000    \               shell32
ELF    7e811000-7e86f000    Deferred        shlwapi<elf>
  \-PE    7e820000-7e86f000    \               shlwapi
ELF    7e86f000-7e890000    Deferred        imm32<elf>
  \-PE    7e880000-7e890000    \               imm32
ELF    7e890000-7e8e7000    Deferred        ddraw<elf>
  \-PE    7e8a0000-7e8e7000    \               ddraw
ELF    7e8e7000-7e96e000    Deferred        winmm<elf>
  \-PE    7e8f0000-7e96e000    \               winmm
ELF    7e96e000-7e9dc000    Deferred        rpcrt4<elf>
  \-PE    7e980000-7e9dc000    \               rpcrt4
ELF    7e9dc000-7ea7c000    Deferred        gdi32<elf>
  \-PE    7e9f0000-7ea7c000    \               gdi32
ELF    7ea7c000-7ebc8000    Deferred        user32<elf>
  \-PE    7eaa0000-7ebc8000    \               user32
ELF    7ebc8000-7ecc4000    Deferred        ole32<elf>
  \-PE    7ebe0000-7ecc4000    \               ole32
ELF    7ecc4000-7ecfd000    Deferred        dinput<elf>
  \-PE    7ecd0000-7ecfd000    \               dinput
ELF    7ecfd000-7ed6c000    Deferred        msvcrt<elf>
  \-PE    7ed10000-7ed6c000    \               msvcrt
ELF    7ed6c000-7edc4000    Deferred        advapi32<elf>
  \-PE    7ed80000-7edc4000    \               advapi32
ELF    7edc4000-7edd8000    Deferred        libresolv.so.2
ELF    7ede3000-7edf7000    Deferred        shfolder<elf>
  \-PE    7edf0000-7edf7000    \               shfolder
ELF    7edf7000-7ee17000    Deferred        iphlpapi<elf>
  \-PE    7ee00000-7ee17000    \               iphlpapi
ELF    7ee17000-7ee41000    Deferred        ws2_32<elf>
  \-PE    7ee20000-7ee41000    \               ws2_32
ELF    7ee41000-7ee5c000    Deferred        wsock32<elf>
  \-PE    7ee50000-7ee5c000    \               wsock32
ELF    7ee5c000-7ee68000    Deferred        libnss_files.so.2
ELF    7ee68000-7ee70000    Deferred        libnss_compat.so.2
ELF    7efbb000-7efe1000    Deferred        libm.so.6
ELF    7efe9000-7f000000    Deferred        libnsl.so.1
ELF    f7460000-f746b000    Deferred        libnss_nis.so.2
ELF    f746c000-f7470000    Deferred        libdl.so.2
ELF    f7470000-f75b4000    Deferred        libc.so.6
ELF    f75b5000-f75ce000    Deferred        libpthread.so.0
ELF    f75ed000-f7729000    Deferred        libwine.so.1
ELF    f772b000-f7749000    Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
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
00000018 (D) C:\Dark Age of Camelot - Catacombs\game.dll
    0000001f    0
    0000001e   15
    0000001d   15
    0000001c    0
    00000019    0 <==
0000001a 
    0000001b    0
Backtrace:
=>0 0x7a777b7c in fglrx_dri.so (+0x817b7c) (0x00000000)

```and at this point i have the usual screen that appear every time i try to run a 3d game

_[http://www.webalice.it/aconet/wine_error.jpg](http://www.webalice.it/aconet/wine_error.jpg)_

last thing:

- i know i must close compiz before run 3d with wine (i use compiz-switch)
- i close all screenlets too
- i don't close cairo-dock because seem to not affect the problem (but anyway i can close it too)
- i know that on WineHQapps is specified to disable vertex support on wine before run DAOC

...

this is all

some one can help me?

bye and thanks!!
Federico

p.s.
EDIT:
u like my last version of ubuntu desktop? ;)

[U][http://www.webalice.it/aconet/desktop.jpg]("http://www.webalice.it/aconet/wine_error.jpg")

UBUNTU POWERRRRRRRRRRRRRR!!!!!!!!!!!!!!
[/U]

---

### Post by Xog on 2009-11-19
[quote=YokoZar]Do not try and install DirectX - Wine already has its own implementation of DirectX, and attempting to install the Windows version will simply break things. 
[/quote]

[http://ubuntuforums.org/showthread.php?t=885111](http://ubuntuforums.org/showthread.php?t=885111)

I haven't dealt with anyone installing direct x, but I'm pretty sure you completely broke a portion of wine by doing it. you're going to have to completely reinstall it. Go to your C:\ in wine and copy any games/applications you have to another part of your drive. Then uninstall wine, remove the ~.wine dir and reinstall it. That's what I would do, but I suggest you wait on more opinions.

---

### Post by realac0 on 2009-11-19
> **Xog said:**
> [http://ubuntuforums.org/showthread.php?t=885111](http://ubuntuforums.org/showthread.php?t=885111)

I haven't dealt with anyone installing direct x, but I'm pretty sure you completely broke a portion of wine by doing it. you're going to have to completely reinstall it. Go to your C:\ in wine and copy any games/applications you have to another part of your drive. Then uninstall wine, remove the ~.wine dir and reinstall it. That's what I would do, but I suggest you wait on more opinions.

omg, never know about this ;(
i am pretty noob about ubuntu.

i'll try!!

but i can just copy and paste my .wine dir for the reinstallation on wine?

no need to reinstall all the apps?

---

### Post by Xog on 2009-11-19
> **realac0 said:**
> omg, never know about this ;(
i am pretty noob about ubuntu.

i'll try!!

but i can just copy and paste my .wine dir for the reinstallation on wine?

no need to reinstall all the apps?


You're going to have to reinstall any applications you have running for wine.

Go to applications -> Ubuntu Software Center
search "wine"
open it, select "Remove"

To remove all programs installed under Wine, remove the ~/.wine directory: 

```
rm -rf $HOME/.wine
```

Also the uninstaller does not remove menu and desktop entries. To remove all Wine-created menu entries run the following commands:
*NOTE: After each line, press ENTER to execute the command.

```
rm -f $HOME/.config/menus/applications-merged/wine*
rm -rf $HOME/.local/share/applications/wine
rm -f $HOME/.local/share/desktop-directories/wine*
rm -f $HOME/.local/share/icons/????_*.xpm
```

Next is to make sure you are going to have the latest version of wine. What you're going to do, is go back into Ubuntu Software Manager, search "wine," open it, and click Install.

This is a complete clean install. After it's done installing, enter this in termainal:
```
winecfg
```

Click Audio, let it detect your audio, click Drives so it can detect your drives, and click Apply / OK.

Next is to make sure you have the completely newest version of wine installed.

Click on System -> Administration -> Software Sources
Click on "Third Party Software" or "Other Software" tab.
Click "Add"
paste: ppa:ubuntu-wine/ppa
Click "Add Source"
Click close to finish, and then reload the package information when prompted.

---

### Post by realac0 on 2009-11-19
[http://www.webalice.it/aconet/error.jpg](http://www.webalice.it/aconet/error.jpg)

this when i try to update 1.1.32 wine versione .deb i have on desktop (after the installation)

ops,. sorry is on italian :=)

it say something like:

impossible to use all the packages for installation or upgrade 
the applications listed below have some dependences not resolved
be sure to have all ok on repository ecc ecc

so at the moment i have, after all your help, 1.1.32 working 64bit

---

### Post by Xog on 2009-11-19
> **realac0 said:**
> [http://www.webalice.it/aconet/error.jpg](http://www.webalice.it/aconet/error.jpg)

this when i try to update 1.1.32 wine versione .deb i have on desktop (after the installation)

ops,. sorry is on italian :=)

it say something like:

impossible to use all the packages for installation or upgrade 
the applications listed below have some dependences not resolved
be sure to have all ok on repository ecc ecc

so at the moment i have, after all your help, 1.1.32 working 64bit

Lei deve usare: 
Applications -> Ubuntu Software Center
(Centro di Software di Ubuntu || [www.freetranslation.com](www.freetranslation.com))

Lei usa: Manager di Pacchetto sinaptico
Non usare ciò!

Please,
```
wine --version
```

---

### Post by realac0 on 2009-11-19
> **Xog said:**
> Lei deve usare: 
Applications -> Ubuntu Software Center
(Centro di Software di Ubuntu || [www.freetranslation.com]("http://www.freetranslation.com"))

Lei usa: Manager di Pacchetto sinaptico
Non usare ciò!

Please,
```
wine --version
```

okok :) :popcorn:

i have done it ;)

```
realac0@realac0-desktop:~$ wine --version
wine-1.1.33

```:p:popcorn::KS

re-downloading client DAOC now

---

### Post by Xog on 2009-11-19
> **realac0 said:**
> okok :) :popcorn:

i have done it ;)

```
realac0@realac0-desktop:~$ wine --version
wine-1.1.33

```:p:popcorn::KS

re-downloading client DAOC now


[http://appdb.winehq.org/objectManager.php?sClass=application&iId=443](http://appdb.winehq.org/objectManager.php?sClass=application&iId=443)

Enjoy. :-)

Usare il di scaricare lei scarica. Lei dovrebbe essere giusto col normale installa da ciò. No i redige/cambiamenti a niente.

---

### Post by realac0 on 2009-11-19
> **Xog said:**
> [http://appdb.winehq.org/objectManager.php?sClass=application&iId=443](http://appdb.winehq.org/objectManager.php?sClass=application&iId=443)

Enjoy. :-)

Usare il di scaricare lei scarica. Lei dovrebbe essere giusto col normale installa da ciò. No i redige/cambiamenti a niente.

:(

nothing changed :(

same error on terminal

```
wine: Unhandled page fault on read access to 0x00000014 at address 0x7a777b7c (thread 0019), starting debugger...
Unhandled exception: page fault on read access to 0x00000014 in 32-bit code (0x7a777b7c).
Register dump:
 CS:0023 SS:002b DS:002b ES:002b FS:0063 GS:006b
 EIP:7a777b7c ESP:0033eeec EBP:00000000 EFLAGS:00210246(  R- --  I  Z- -P- )
 EAX:00000001 EBX:00000000 ECX:00000000 EDX:00000000
 ESI:0000000b EDI:7c23d8e8
Stack dump:
0x0033eeec:  7a8f7859 00000000 7c6acc18 7c666820
0x0033eefc:  00000000 00000000 00000000 0000000b
0x0033ef0c:  7a8f7605 00000008 00000018 00000000
0x0033ef1c:  7b7a9894 0000000b 7b7af824 7c23d988
0x0033ef2c:  00000000 7c7ccc00 7c7aae20 7c8665c0
0x0033ef3c:  00000000 00000000 7a7672a4 7c23d8e8
Backtrace:
=>0 0x7a777b7c in fglrx_dri.so (+0x817b7c) (0x00000000)
0x7a777b7c: movl    0x14(%edx),%eax
Modules:
Module    Address            Debug info    Name (120 modules)
PE      3a0000-  3bb000    Deferred        mssds3d.m3d
PE      400000- 23b1000    Deferred        game
PE    10000000-100a4000    Deferred        libxml2
PE    21100000-21164000    Deferred        mss32
PE    22100000-22122000    Deferred        mssa3d.m3d
PE    22300000-2232c000    Deferred        msseax.m3d
PE    22400000-22419000    Deferred        msssoft.m3d
PE    22600000-2261f000    Deferred        mssdx7.m3d
PE    22700000-22768000    Deferred        mssrsx.m3d
PE    24100000-24120000    Deferred        mssdsp.flt
PE    26400000-26439000    Deferred        mssvoice.asi
PE    26f00000-26f2c000    Deferred        mssmp3.asi
ELF    79f60000-7b800000    Export          fglrx_dri.so
ELF    7b800000-7b972000    Deferred        kernel32<elf>
  \-PE    7b820000-7b972000    \               kernel32
ELF    7bc00000-7bcb2000    Deferred        ntdll<elf>
  \-PE    7bc10000-7bcb2000    \               ntdll
ELF    7bf00000-7bf04000    Deferred        <wine-loader>
ELF    7c14d000-7c19a000    Deferred        dsound<elf>
  \-PE    7c150000-7c19a000    \               dsound
ELF    7c99a000-7c9c6000    Deferred        libatiadlxx.so
ELF    7d1e6000-7d278000    Deferred        libgl.so.1
ELF    7d278000-7d3a6000    Deferred        wined3d<elf>
  \-PE    7d280000-7d3a6000    \               wined3d
ELF    7d3fb000-7d419000    Deferred        libgcc_s.so.1
ELF    7d438000-7d46b000    Deferred        d3d9<elf>
  \-PE    7d440000-7d46b000    \               d3d9
ELF    7d46b000-7d481000    Deferred        psapi<elf>
  \-PE    7d470000-7d481000    \               psapi
ELF    7d548000-7d55e000    Deferred        midimap<elf>
  \-PE    7d550000-7d55e000    \               midimap
ELF    7d55e000-7d584000    Deferred        msacm32<elf>
  \-PE    7d560000-7d584000    \               msacm32
ELF    7d584000-7d59c000    Deferred        msacm32<elf>
  \-PE    7d590000-7d59c000    \               msacm32
ELF    7dd9d000-7dda4000    Deferred        libogg.so.0
ELF    7dda4000-7ddcf000    Deferred        libvorbis.so.0
ELF    7ddcf000-7dec9000    Deferred        libvorbisenc.so.2
ELF    7dec9000-7df19000    Deferred        libflac.so.8
ELF    7df19000-7df52000    Deferred        libdbus-1.so.3
ELF    7df52000-7dfbe000    Deferred        libsndfile.so.1
ELF    7dfbe000-7dfc7000    Deferred        libwrap.so.0
ELF    7dfc7000-7dfcd000    Deferred        libxtst.so.6
ELF    7dfcd000-7e017000    Deferred        libpulsecommon-0.9.19.so
ELF    7e017000-7e057000    Deferred        libpulse.so.0
ELF    7e057000-7e060000    Deferred        librt.so.1
ELF    7e060000-7e128000    Deferred        libasound.so.2
ELF    7e147000-7e17e000    Deferred        winealsa<elf>
  \-PE    7e150000-7e17e000    \               winealsa
ELF    7e1bf000-7e1f2000    Deferred        uxtheme<elf>
  \-PE    7e1d0000-7e1f2000    \               uxtheme
ELF    7e1f2000-7e1fd000    Deferred        libxcursor.so.1
ELF    7e1fd000-7e203000    Deferred        libxfixes.so.3
ELF    7e203000-7e207000    Deferred        libxcomposite.so.1
ELF    7e207000-7e210000    Deferred        libxrandr.so.2
ELF    7e210000-7e21a000    Deferred        libxrender.so.1
ELF    7e21a000-7e220000    Deferred        libxxf86vm.so.1
ELF    7e220000-7e225000    Deferred        libxdmcp.so.6
ELF    7e225000-7e243000    Deferred        libxcb.so.1
ELF    7e243000-7e372000    Deferred        libx11.so.6
ELF    7e372000-7e382000    Deferred        libxext.so.6
ELF    7e382000-7e39d000    Deferred        libice.so.6
ELF    7e39d000-7e3a6000    Deferred        libsm.so.6
ELF    7e3a6000-7e445000    Deferred        winex11<elf>
  \-PE    7e3b0000-7e445000    \               winex11
ELF    7e492000-7e4b9000    Deferred        libexpat.so.1
ELF    7e4b9000-7e4e6000    Deferred        libfontconfig.so.1
ELF    7e4e6000-7e4fc000    Deferred        libz.so.1
ELF    7e4fc000-7e57b000    Deferred        libfreetype.so.6
ELF    7e57b000-7e582000    Deferred        libasound_module_pcm_pulse.so
ELF    7e59a000-7e5af000    Deferred        system.drv16.so
PE    7e5a0000-7e5af000    Deferred        system.drv16
ELF    7e5af000-7e67d000    Deferred        comctl32<elf>
  \-PE    7e5c0000-7e67d000    \               comctl32
ELF    7e67d000-7e80d000    Deferred        shell32<elf>
  \-PE    7e690000-7e80d000    \               shell32
ELF    7e80d000-7e86a000    Deferred        shlwapi<elf>
  \-PE    7e820000-7e86a000    \               shlwapi
ELF    7e86a000-7e88b000    Deferred        imm32<elf>
  \-PE    7e870000-7e88b000    \               imm32
ELF    7e88b000-7e8e2000    Deferred        ddraw<elf>
  \-PE    7e890000-7e8e2000    \               ddraw
ELF    7e8e2000-7e969000    Deferred        winmm<elf>
  \-PE    7e8f0000-7e969000    \               winmm
ELF    7e969000-7e9d6000    Deferred        rpcrt4<elf>
  \-PE    7e980000-7e9d6000    \               rpcrt4
ELF    7e9d6000-7ea76000    Deferred        gdi32<elf>
  \-PE    7e9f0000-7ea76000    \               gdi32
ELF    7ea76000-7ebbe000    Deferred        user32<elf>
  \-PE    7ea90000-7ebbe000    \               user32
ELF    7ebbe000-7ecb9000    Deferred        ole32<elf>
  \-PE    7ebe0000-7ecb9000    \               ole32
ELF    7ecb9000-7ecf2000    Deferred        dinput<elf>
  \-PE    7ecc0000-7ecf2000    \               dinput
ELF    7ecf2000-7ed60000    Deferred        msvcrt<elf>
  \-PE    7ed00000-7ed60000    \               msvcrt
ELF    7ed60000-7edb9000    Deferred        advapi32<elf>
  \-PE    7ed70000-7edb9000    \               advapi32
ELF    7edb9000-7edcd000    Deferred        libresolv.so.2
ELF    7edcd000-7edd0000    Deferred        libxinerama.so.1
ELF    7edd8000-7edec000    Deferred        shfolder<elf>
  \-PE    7ede0000-7edec000    \               shfolder
ELF    7edec000-7ee0c000    Deferred        iphlpapi<elf>
  \-PE    7edf0000-7ee0c000    \               iphlpapi
ELF    7ee0c000-7ee36000    Deferred        ws2_32<elf>
  \-PE    7ee10000-7ee36000    \               ws2_32
ELF    7ee36000-7ee51000    Deferred        wsock32<elf>
  \-PE    7ee40000-7ee51000    \               wsock32
ELF    7ee51000-7ee5d000    Deferred        libnss_files.so.2
ELF    7ee5d000-7ee68000    Deferred        libnss_nis.so.2
ELF    7ee68000-7ee70000    Deferred        libnss_compat.so.2
ELF    7ee71000-7ee75000    Deferred        libxau.so.6
ELF    7efbb000-7efe1000    Deferred        libm.so.6
ELF    7efe9000-7f000000    Deferred        libnsl.so.1
ELF    f7421000-f7426000    Deferred        libuuid.so.1
ELF    f7427000-f742b000    Deferred        libdl.so.2
ELF    f742b000-f756f000    Deferred        libc.so.6
ELF    f7570000-f7589000    Deferred        libpthread.so.0
ELF    f75a8000-f76e3000    Deferred        libwine.so.1
ELF    f76e5000-f7703000    Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
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
00000018 (D) C:\Dark Age of Camelot - Labyrinth of the Minotaur\game.dll
    0000001f    0
    0000001e   15
    0000001d   15
    0000001c    0
    00000019    0 <==
0000001a 
    0000001b    0
Backtrace:
=>0 0x7a777b7c in fglrx_dri.so (+0x817b7c) (0x00000000)

```

maybe a problem on my VGA?

---

### Post by Sticky_Bit on 2009-11-19
> **Xog said:**
> [http://ubuntuforums.org/showthread.php?t=885111](http://ubuntuforums.org/showthread.php?t=885111)

 Go to your C:\ in wine and copy any games/applications you have to another part of your drive. Then un-install wine, remove the ~.wine dir and reinstall it.


What is the point of copying of any games and apps to another part of your drive if you have to re-install them all anyway? Is it possible to move the game and app folders out, un-install wine, remove the .wine folder, re-install wine and then move the games and apps back into the .wine folder?

Sorry I'm a noob as well. I'm just trying to understand your posts. It would be great if you could do that.

---

### Post by realac0 on 2009-11-19
what is this and what mean?
taken from WineHQ about DAOC

[CENTER]**Using FBO as the ORM crashes with fglrx drivers**[/CENTER]
   This is not a Wine bug, it is a fglrx bug.  Please do not open a bug for this, it will just be closed.
   See the [fglrx bug]("http://ati.cchtml.com/show_bug.cgi?id=1571") for more details, or check the HOWTO for this app for a workaround.

---

### Post by Xog on 2009-11-19
> **realac0 said:**
> what is this and what mean?
taken from WineHQ about DAOC

[CENTER]**Using FBO as the ORM crashes with fglrx drivers**[/CENTER]
   This is not a Wine bug, it is a fglrx bug.  Please do not open a bug for this, it will just be closed.
   See the [fglrx bug]("http://ati.cchtml.com/show_bug.cgi?id=1571") for more details, or check the HOWTO for this app for a workaround.

the fix as mentioned in the bug thread: [http://bugs.winehq.org/show_bug.cgi?id=18794](http://bugs.winehq.org/show_bug.cgi?id=18794) ;
Change OffscreenRenderingMode to "backbuffer".

i'm not quite sure how to do that though, anyone here mind lending some assistance? :)

---

### Post by realac0 on 2009-11-20
> **Xog said:**
> the fix as mentioned in the bug thread: [http://bugs.winehq.org/show_bug.cgi?id=18794](http://bugs.winehq.org/show_bug.cgi?id=18794) ;
Change OffscreenRenderingMode to "backbuffer".

i'm not quite sure how to do that though, anyone here mind lending some assistance? :)


hope some one help me  ;(
maybe all my problem are from this.

so is all coming from my ATI VGA? or i am wrong?

---

### Post by Xog on 2009-11-20
Yeah, it's an ATI video card bug. Nvidia users don't experience this problem.

---

### Post by realac0 on 2009-11-20
can't believe this!!!
NOW WORKKKKKKKKKKKKKK!!
i try to explain:

i had tryied to change what u suggested:
-------------
the fix as mentioned in the bug thread: [http://bugs.winehq.org/show_bug.cgi?id=18794](http://bugs.winehq.org/show_bug.cgi?id=18794) ;
Change OffscreenRenderingMode to "backbuffer".
-------------

... with my old wine installation (with dx9) but nothing changed.

so, after what u said me to do (clean all and reinstall) finally this fix worked!!

the only thing i can say u is a big big THANKS!!!!!!!!!!!!!!!!!!!!!!!!

now there are some minor things to fix, on resolution, visual effects, ecc, things that i can adjust myself.

i'd like ask u some other things that i don't understand (if u want help me):

- from my (small) experience seem that run Wine with a virtual desktop is better than full screen. u agree?

- for launch DAOC and autoconnect to a shar server i have follow a howto and is working using this on a terminal:

```
cd /home/realac0/.wine/drive_c
cd Dark\ Age\ of\ Camelot\ -\ Labyrinth\ of\ the\ Minotaur/
cd Laucher
wine DOLLoader game.dll 88.198.56.21 10300 1 user password 
```

so now i just copy/paste this to a terminal taken from a file done with gedit and all work.

why i can't create a launcher? i have tryied a lot but every time i try to make a launcher with a similar script wine don't work (even if is flagged on the proprieties: run as a terminal). what is the problem?

anyway thx a lot u rox!!

---

### Post by Xog on 2009-11-20
> **realac0 said:**
> can't believe this!!!
NOW WORKKKKKKKKKKKKKK!!
i try to explain:

i had tryied to change what u suggested:
-------------
the fix as mentioned in the bug thread: [http://bugs.winehq.org/show_bug.cgi?id=18794](http://bugs.winehq.org/show_bug.cgi?id=18794) ;
Change OffscreenRenderingMode to "backbuffer".
-------------

... with my old wine installation (with dx9) but nothing changed.

so, after what u said me to do (clean all and reinstall) finally this fix worked!!

the only thing i can say u is a big big THANKS!!!!!!!!!!!!!!!!!!!!!!!!

now there are some minor things to fix, on resolution, visual effects, ecc, things that i can adjust myself.

i'd like ask u some other things that i don't understand (if u want help me):

- from my (small) experience seem that run Wine with a virtual desktop is better than full screen. u agree?

- for launch DAOC and autoconnect to a shar server i have follow a howto and is working using this on a terminal:

```
cd /home/realac0/.wine/drive_c
cd Dark\ Age\ of\ Camelot\ -\ Labyrinth\ of\ the\ Minotaur/
cd Laucher
wine DOLLoader game.dll 88.198.56.21 10300 1 user password 
```

so now i just copy/paste this to a terminal taken from a file done with gedit and all work.

why i can't create a launcher? i have tryied a lot but every time i try to make a launcher with a similar script wine don't work (even if is flagged on the proprieties: run as a terminal). what is the problem?

anyway thx a lot u rox!!

[IMG]http://z.about.com/d/linux/1/0/_/1/desktop02p06.jpg[/IMG]

To create a launcher on the Desktop, right-click on an empty area on the Desktop and select the item "Create Launcher". Enter the Name and the Command to run and if you want you can select an icon for it by clicking on the icon button. 

Are you using "wine NAME_OF_PROGRAM" in the terminal to open from the launcher? *Nevermind, just read your post. Give me a few.

After a few minutes edit:

Does your DAOC folder (in C:\Program Files\) have all permissions set to Create and Delete files? Try that. Also set that to your Launcher.
*To set permissions, right click on the folder, go to Properties. Change permissions, and then click ENABLE PERMISSIONS, then click OK.

---

