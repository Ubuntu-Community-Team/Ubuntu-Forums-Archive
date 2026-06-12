---
title: "Howto: Dapper, Wine, Starcraft"
date: 2006-04-30
forum: Wine
---

### Post by Nikusan on 2006-04-30
**1 Install wine**
```
sudo apt-get install wine
```

**2 Setup disc drives in wine**
```
winecfg
```
Go to the Drives tab.
Press the Autodetect button.
Press the Show Advanced button.
Change the type of your CD drive(s) to CD-ROM.

**3 Test audio in wine**
```
winecfg
```
Go to the Audio tab.
If it crashes follow the instructions [here]("http://www.ubuntuforums.org/showpost.php?p=846165&postcount=7"). 

**4 Install Starcraft and Brood War**
Insert the Starcraft CD.
The CD should automatically open in nautilus. If not, navigate to it.
Right click install.exe and choose Open with "Wine Windows Emulator".
If that is not listed choose Open with Other Application... then choose "Use a custom command" and enter wine.

Optionally, assuming your starcraft cd is inserted in /media/cdrom you could simply:
```
wine /media/cdrom/install.exe
```
Do exactly the same for the Brood War CD.

**5 Update to version 1.13f**
```
wget http://ftp.blizzard.com/pub/broodwar/patches/PC/BW-113f.exe
wine BW-113f.exe
```

**6 Set Starcraft to run windowed**
I've had trouble with starcraft running full screen because when it exits it messes up all the applets and things on my panels. To set it to run windowed:
```
winecfg
```
Go to the Applications tab.
Press Add application...
Navigate to "Program Files\Starcraft\starcraft.exe"
Go to the Graphics tab.
Tick "Emulate a virtual desktop".


**7 Run it!**
```
wine ~/.wine/drive_c/Program Files/Starcraft/starcraft.exe
```

**8 Optionally place a launcher in the menu**
Navigate to Applications > Accessories > Alacarte Menu Editor
Click on the games category.
Click on File > New Entry.
Name: "Starcraft"
Comment: "National Sport of South Korea"
Command: "wine ~/.wine/drive_c/Program Files/Starcraft/starcraft.exe"
For an icon you can use the file sc.ico from the Starcraft CD, or you can use one of the kickass icons [here]("http://www.customize.org/details/19646").

---

### Post by sYs^ on 2006-04-30
Hi, 

nice howto, but I have a little problem with starcraft + wine, it uses 100% CPU even in the menu. Any ideas? Is that a problem if my starcraft was installed on Windows XP and I'm running it from a ntfs partition? Thanks!

---

### Post by Nikusan on 2006-04-30
[QUOTE=sYs^]Hi, 

nice howto, but I have a little problem with starcraft + wine, it uses 100% CPU even in the menu. Any ideas? Is that a problem if my starcraft was installed on Windows XP and I'm running it from a ntfs partition? Thanks![/QUOTE]

Mine does that too, however you wouldn't notice it from playing the game. Unless you have folding or something running in the background I guess it's an issue we can conveniently ignore?

---

### Post by sYs^ on 2006-04-30
Unfortunately I notice it, my units are moving like snails. :D

---

### Post by Nikusan on 2006-04-30
[QUOTE=sYs^]Unfortunately I notice it, my units are moving like snails. :D[/QUOTE]

Hmmm sorry, I don't have a solution.

---

### Post by sYs^ on 2006-04-30
Of course it isn't your fault so you don't have to say sorry, that's why I have dual boot, Ubuntu + Windows XP :p

---

### Post by duality on 2006-05-18
nice man, thnx alot

---

### Post by Carrots171 on 2006-05-20
If Starcraft is slow for you, you can add:
```
nice -20
```
to the end of the command used to run Starcraft. It made Starcraft a lot less choppy for me.

Oh yeah, there's another HOWTO for Starcraft on Wine here:

[http://www.linux-gamers.net/modules/wiwimod/index.php?page=HOWTO+Starcraft&back=HOWTO+INDEX+Wine+Games]("http://www.linux-gamers.net/modules/wiwimod/index.php?page=HOWTO+Starcraft&back=HOWTO+INDEX+Wine+Games")

It has instructions on getting Battle.net working. The interface doesn't work properly (It's a known bug in WINE), but once you join a game, everything works fine.

---

### Post by La_Frenezo on 2006-06-01
Hi!

Thanks for the instructions! I tried them but I still encounter a bunch of problems:

1) I'm able to play the game in singleplayer, but the mousecursor is choppy as hell.
2) When I try to login, b.net it says:"Can't determine version...". The strange thing is: it has already worked for 1start - right after I added the patch I was able to login BUT...
3)The whole b.net screen looks black :/
4)After an error like "Can't determine version.." WINE ALWAYS crashes (screen gets black) ...

Does anyone has clue?

---

### Post by souled on 2006-06-01
Starcraft works with emulated desktop, but changing the resolution has no effect. Even if I change the resolution to 1024x768, the game plays at 800x600 (I think), but it's too small for me. Anyone experiencing this?

---

### Post by ELD on 2006-06-02
Thanks for the great how-to, will have to try whenever i get my ubuntubox setup again.

---

### Post by ELD on 2006-06-02
The game actually only works for me if i start it up from the install.exe from one of the cd's :S

---

### Post by noiz on 2006-06-03
I have got broodwar installed fine but i was wondering if there is any way to get it to run full screen?  right now when it does run full screen it only shows the game in the top left corner of the screen.

-noiz

---

### Post by jdong on 2006-06-03
The 100% CPU thing is Starcraft behavior... even in Windows Starcraft eats CPU while idle.


I've yet to see Battle.net work with WINE. Multiplayer LAN is just fine.


Starcraft only runs at one resolution... :)

---

### Post by mat1t on 2006-06-05
Starcraft is only written in 800x600, so that's all it will run in. Bummer isn't it? :P

---

### Post by andb on 2006-06-06
The trick to get it to run fast... Create an iso from the broodwar disk and mount the iso using -o loop. Setup the mount point in winecfg as a cdrom. All should run fine, its worked on every machine I tried it on. Seems that the CD access is what slows it all down. Starting it in a different X server can get you around the terrible video mangling. Easy way to this is just to log in a second time using Applications > System Tools > New Login (hidden by default in Dapper, right-click on Applications, Edit Menues to get it)

The wine page [http://appdb.winehq.org/appview.php?versionId=149](http://appdb.winehq.org/appview.php?versionId=149) comments that it performs better in 16bit color, I havent tried yet...

The comments about the graphics show how brilliant the game is. It actually runs in 640x480!!! The game is completely 2 dimensional, unless you concider having "high ground" and "low ground" 3d ;) But the ballance between races, the game play, its just unmatched. 

If you are a real fan, check out sclegacy.com and youll be amazed. Watch the "Pimpest Plays". I love the attention this game gets in South Korea, like basketball in the States!

There have been a few attempts to write a native linux version, shame nothing came of them... Anyone up for the task?

---

### Post by eighthate on 2006-06-09
Thanks for this HOWTO. And BTw LOL (comment: national korea sport)
:p

---

### Post by noiz on 2006-06-11
well, since i want to play this game in full screen i have it so now i can change my X resolution to 640x480 and then it plays just like in windows, but i was wondering if there is any way i could write a script to automate playing this game.  what im talking about is if there is a way to write a script that pretty much does this:

1. change X resolution to 640x480
2. run the command "wine starcraft.exe"
3. after i have exited starcraft or i press a key combination (like ctrl+alt+s), change the X resolution back to 1024x768

anyone know if there is a way to write a script i can run that will do the three things i just mentioned?

-noiz

---

### Post by Omnisilver on 2006-06-17
Hi, i'm a french Ubunteros, and i love Starcraft :)

I have created a tutorial in french about Starcraft with Wine, and i use this one, so i want to thanks the autor (Nikusan)

I added some tips, for example i changed :
wine ~/.wine/drive_c/**Program\ Files**/Starcraft/starcraft.exe

Good job ;)

---

### Post by andb on 2006-06-18
Ive recently been playing around with Qemu instead of wine and I am very happy. Far less hickups, great switch to go between full screen and windowed mode. Im working on networking, there is a TUN/TAP Qemu howto thats really good, but a bit much, I hoping to get the VM connected to the net using just a simple network bridge. If you have a decent machine, this way is really good. As soon as I get my net issue worked out, Ill make a howto...

---

### Post by jdong on 2006-06-18
ouch; that sounds like it wants a hefty CPU!

---

### Post by Raos on 2006-07-04
> 1) I'm able to play the game in singleplayer, but the mousecursor is choppy as hell.

That's the same problem I have, but the sound is also choppy.  When I run the game from terminal, I get:

> fixme:ddraw:Main_DirectDraw_SetCooperativeLevel (0x7fd6fbc8)->(0x10022,00000013)
fixme:x11drv:X11DRV_desktop_SetCurrentMode Cannot change screen BPP from 32 to 8
fixme:x11drv:X11DRV_desktop_SetCurrentMode Cannot change screen BPP from 32 to 8
fixme:x11drv:X11DRV_DDHAL_CreatePalette stub
ALSA lib pcm_dmix.c:762:(snd_pcm_dmix_open) The dmix plugin supports only playback stream
ALSA lib seq_hw.c:456:(snd_seq_hw_open) open /dev/snd/seq failed: No such file or directory
This sound card's driver does not support direct access
The (slower) DirectSound HEL mode will be used instead.
fixme:wave:ESD_AddRingMessage two fast messages in the queue!!!!


with the last line repeating about once a second.  For a while I also got

> fixme:dsound:DSOUND_MixOne problem with underrun detection (mixlen=896 < primary_done=22880)

over an over a bunch of times.  I've tried the nice -20 thing, and that didn't help at all, nor did running wine from a window vs. full screen.

---

### Post by xander848 on 2006-07-04
Hey I got a problem when i tried to install it. after putting in my cd key i got an error message that said 
exp1:Error3: Path not found

Does anyone know why this is happening and how to fix it?

EDIT: I just thought of this... I use the linux version of picasa which apparently uses some specialized version of wine to run. Could this be a problem?

---

### Post by pharcyde on 2006-07-05
PIcasa was just ported over using winelib.  It is independent of wine.

I had the same sound issue before I installed some alsa libs.  I can't remember what they were exactly.  I'm on amd64 Ubuntu though.  I think it was lib32asound2.  Basically I went to the audio tab in winecfg and selected alsa as the driver and all my sound problems and chopiness went away.  Hope this helps.

---

### Post by RedKrieg on 2006-07-29
I'm having some trouble with sound in Starcraft...  There isn't any.

I was having the crash when you click the audio tab, but fixed that thanks to the linked article in this thread.

I have tried ALSA and OSS, using Full accelleration and Emulation, as well as having the "emulate driver" box checked and unchecked for each.  Nothing I do seems to allow me to hear sounds.  I'm using wine 0.9.17.

ALSA works fine with everything but wine.

---

### Post by wdj on 2006-08-10
I had no problem installing or trying to run StarCraft BW on my machine. I found that the sound was the problem. Try turning on down the hardware accel and turn on Driver Emulation on the sound tab of winecfg for the game. That fixed it on my computer.

---

### Post by sandpaperback on 2006-08-23
Hi,

I've got Starcraft running alright under Wine (sound is fine too), but I still these errors when I start it up:

> fixme:ddraw:Main_DirectDraw_SetCooperativeLevel (0x7fd71198)->(0x10022,00000013)
fixme:x11drv:X11DRV_desktop_SetCurrentMode Cannot change screen BPP from 32 to 8
fixme:x11drv:X11DRV_desktop_SetCurrentMode Cannot change screen BPP from 32 to 8
fixme:x11drv:X11DRV_DDHAL_CreatePalette stub


Any idea how to resolve those?

---

### Post by jdong on 2006-08-23
If it works, ignore the errors :)

---

### Post by MakLeod on 2006-08-24
Wanted to say thank you for writing this HOWTO.  I have Starcraft up and running perfectly visually.  However, sound doesn't work and when I try to configure it using winecfg this is the error message I get...

ALSA lib seq_hw.c:456:(snd_seq_hw_open) open /dev/snd/seq failed: No such file or directory
fixme:jack:JACK_drvLoad error loading the jack library libjack.so, please install this library to use jack
ALSA lib seq_hw.c:456:(snd_seq_hw_open) open /dev/snd/seq failed: No such file or directory
macleod@jedd:~$

Any ideas on how to fix that?  Thanks.

---

### Post by MakLeod on 2006-08-24
Bah!  Fixed it myself, sorry for the post.

---

### Post by DeamonAxe on 2006-09-04
Did someone fixed the :

fixme:jack:JACK_drvLoad error loading the jack library libjack.so, please install this library to use jack

Error?

Using ALSA and EsounD drivers I have weird sound, Like skipping...

Thank,
Wine 0.9.20 - StarCraft 1.14 - Ubuntu 6.06 LTS - the Dapper Drake

---

### Post by precinto on 2006-09-10
I managed to install and run SC just fine. But I've noticed that i cannot save games when run as normal user, i have to use sudo or the game crashes when saving and exits.

Does someone know why is that?

Everytime i run it (sudo or not) it gives me this error:
err:virtual:NtProtectVirtualMemory Unsupported on other process

and proceeds to the command line. But it starts and works fine.

When run without privileges and try to save it outputs the following:

```
 fixme:d3d:IWineD3DDeviceImpl_GetAvailableTextureMem (0x182118) : stub, simulating 64MB for now, returning 64MB left
fixme:ddraw:IDirectDrawImpl_SetCooperativeLevel (0x1818d0)->(0x10024,00000013)
fixme:xrandr:X11DRV_XRandR_SetCurrentMode Cannot change screen BPP from 32 to 8
precinto@ubuntu:~$ wine: Unhandled page fault on read access to 0x00000034 at ad dress 0x7efa9c33 (thread 000b), starting debugger...
WineDbg starting on pid 0xa
Unhandled exception: page fault on read access to 0x00000034 in 32-bit code (0x7efa9c33).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:003b GS:0033
 EIP:7efa9c33 ESP:0034f88c EBP:0034f8a4 EFLAGS:00210212(   - 00      - RIA1)
 EAX:00000020 EBX:7eff5280 ECX:004f9870 EDX:00000024
 ESI:00000020 EDI:0034f92b
Stack dump:
0x0034f88c:  004c9774 0000001f 004c7a66 00000001
0x0034f89c:  00000001 0034f92b 0034f8bc 004c972e
0x0034f8ac:  00000020 004dfda4 00000000 00000001
0x0034f8bc:  00000000 004d15ce 0034f8f4 00000036
0x0034f8cc:  00000001 00000000 0049bd0c 00000000
0x0034f8dc:  02a700e7 02a700e7 02a700ec 00000001
fixme:ntdll:RtlNtStatusToDosErrorNoTeb no mapping for c0000119
Backtrace:
=>1 0x7efa9c33 RtlEnterCriticalSection+0x1a in ntdll (0x7efa9c33)
  2 0x004c972e in starcraft (+0xc972e) (0x004c972e)
  3 0x004d15ce in starcraft (+0xd15ce) (0x004d15ce)
0x7efa9c33 RtlEnterCriticalSection+0x1a in ntdll: movl  0x14(%esi),%eax
Modules:
Module  Address                 Debug info      Name (99 modules)
PE      400000-6bd000   Export          starcraft
PE      1240000-1261000 Deferred        standard.snp
PE      2000000-2011000 Deferred        local
PE      10000000-1001a000       Deferred        smackw32
PE      15000000-15054000       Deferred        storm
ELF     778a6000-778c3000       Deferred        tapi32<elf>
  \-PE  778b0000-778c3000       \               tapi32
ELF     77bf6000-77cab000       Deferred        libasound.so.2
ELF     77cab000-77cf3000       Deferred        dsound<elf>
  \-PE  77cb0000-77cf3000       \               dsound
ELF     7bf00000-7bf03000       Deferred        <wine-loader>
ELF     7bf3d000-7bf52000       Deferred        midimap<elf>
  \-PE  7bf40000-7bf52000       \               midimap
ELF     7bf78000-7c000000       Deferred        winmm<elf>
  \-PE  7bf80000-7c000000       \               winmm
ELF     7cc9a000-7ccb2000       Deferred        msacm32<elf>
  \-PE  7cca0000-7ccb2000       \               msacm32
ELF     7ccb2000-7ccdb000       Deferred        winealsa<elf>
  \-PE  7ccc0000-7ccdb000       \               winealsa
ELF     7ccdb000-7cd51000       Deferred        libglu.so.1
ELF     7cd51000-7cdfe000       Deferred        wined3d<elf>
  \-PE  7cd60000-7cdfe000       \               wined3d
ELF     7cdfe000-7ce48000       Deferred        ddraw<elf>
  \-PE  7ce10000-7ce48000       \               ddraw
ELF     7cf59000-7cf5d000       Deferred        libgpg-error.so.0
ELF     7cf5d000-7cfa9000       Deferred        libgcrypt.so.11
ELF     7cfa9000-7cfb9000       Deferred        libtasn1.so.2
ELF     7cfb9000-7cfe6000       Deferred        libcrypt.so.1
ELF     7cff9000-7d062000       Deferred        libgnutls.so.12
ELF     7d062000-7d090000       Deferred        libcups.so.2
ELF     7d0c2000-7d0f4000       Deferred        uxtheme<elf>
  \-PE  7d0d0000-7d0f4000       \               uxtheme
ELF     7d0f4000-7d0f9000       Deferred        libxfixes.so.3
ELF     7d0f9000-7d102000       Deferred        libxcursor.so.1
ELF     7d102000-7d11e000       Deferred        imm32<elf>
  \-PE  7d110000-7d11e000       \               imm32
ELF     7d11e000-7d121000       Deferred        libxrandr.so.2
ELF     7d121000-7d129000       Deferred        libxrender.so.1
ELF     7d9a9000-7d9b1000       Deferred        librt.so.1
ELF     7da7e000-7e37a000       Deferred        fglrx_dri.so
ELF     7e37a000-7e41a000       Deferred        libgl.so.1
ELF     7e41a000-7e500000       Deferred        libx11.so.6
ELF     7e500000-7e50d000       Deferred        libxext.so.6
ELF     7e50d000-7e525000       Deferred        libice.so.6
ELF     7e525000-7e5a7000       Deferred        winex11<elf>
  \-PE  7e530000-7e5a7000       \               winex11
ELF     7e5a7000-7e5c6000       Deferred        libexpat.so.1
ELF     7e5c6000-7e5f4000       Deferred        libfontconfig.so.1
ELF     7e5f4000-7e608000       Deferred        libz.so.1
ELF     7e608000-7e671000       Deferred        libfreetype.so.6
ELF     7e671000-7e685000       Deferred        lz32<elf>
  \-PE  7e680000-7e685000       \               lz32
ELF     7e685000-7e69e000       Deferred        version<elf>
  \-PE  7e690000-7e69e000       \               version
ELF     7e69e000-7e6cd000       Deferred        winspool<elf>
  \-PE  7e6b0000-7e6cd000       \               winspool
ELF     7e6cd000-7e78f000       Deferred        comctl32<elf>
  \-PE  7e6e0000-7e78f000       \               comctl32
ELF     7e78f000-7e7a2000       Deferred        libresolv.so.2
ELF     7e7a2000-7e7c1000       Deferred        iphlpapi<elf>
  \-PE  7e7b0000-7e7c1000       \               iphlpapi
ELF     7e7c1000-7e810000       Deferred        rpcrt4<elf>
  \-PE  7e7d0000-7e810000       \               rpcrt4
ELF     7e810000-7e81a000       Deferred        libgcc_s.so.1
ELF     7e8ef000-7e9a1000       Deferred        gdi32<elf>
  \-PE  7e900000-7e9a1000       \               gdi32
ELF     7e9a1000-7ead3000       Deferred        user32<elf>
  \-PE  7e9c0000-7ead3000       \               user32
ELF     7ead3000-7eb63000       Deferred        ole32<elf>
  \-PE  7eae0000-7eb63000       \               ole32
ELF     7eb63000-7ebb9000       Deferred        shlwapi<elf>
  \-PE  7eb70000-7ebb9000       \               shlwapi
ELF     7ebb9000-7ec9f000       Deferred        shell32<elf>
  \-PE  7ebd0000-7ec9f000       \               shell32
ELF     7ec9f000-7ed3a000       Deferred        comdlg32<elf>
  \-PE  7ecb0000-7ed3a000       \               comdlg32
ELF     7ed3a000-7ed7e000       Deferred        advapi32<elf>
  \-PE  7ed50000-7ed7e000       \               advapi32
ELF     7ed7e000-7ede0000       Deferred        msvcrt<elf>
  \-PE  7ed90000-7ede0000       \               msvcrt
ELF     7ede0000-7edfa000       Deferred        crtdll<elf>
  \-PE  7edf0000-7edfa000       \               crtdll
ELF     7edfa000-7ee04000       Deferred        libnss_files.so.2
ELF     7ee04000-7ee0d000       Deferred        libnss_nis.so.2
ELF     7ee0d000-7ee22000       Deferred        libnsl.so.1
ELF     7ee22000-7ee2b000       Deferred        libnss_compat.so.2
ELF     7ee5e000-7ef60000       Deferred        kernel32<elf>
  \-PE  7ee80000-7ef60000       \               kernel32
ELF     7ef60000-7ef82000       Deferred        libm.so.6
ELF     7ef82000-7f000000       Export          ntdll<elf>
  \-PE  7ef90000-7f000000       \               ntdll
ELF     b7d12000-b7d15000       Deferred        libdl.so.2
ELF     b7d15000-b7e44000       Deferred        libc.so.6
ELF     b7e44000-b7e56000       Deferred        libpthread.so.0
ELF     b7e5a000-b7e5d000       Deferred        libxau.so.6
ELF     b7e5d000-b7e62000       Deferred        libxxf86vm.so.1
ELF     b7e62000-b7e6a000       Deferred        libsm.so.6
ELF     b7e6a000-b7f7a000       Deferred        libwine.so.1
ELF     b7f7d000-b7f93000       Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
0000000d
        0000000e    0
0000000a (D) C:\Program Files\Starcraft\starcraft.exe
        00000011    2
        00000010    0
        0000000f   15
        0000000c    1
        0000000b    0 <==

```

Any idea?

---

### Post by juve on 2006-09-11
Here's my version:
I have an ATI r300 (R9700) and have problems with wine > 0.9.15
to run Starcraft flawlessly i use the following setup:
[LIST=1]
[*]download wine 0.9.15 debs from winehq
[*]remove newer wine packages, install 0.9.15
[*]```
you@home:~$ **/usr/bin/wine** --version
Wine 0.9.15
```
[*]**/usr/bin/wine winecfg**
[LIST]
[*]*audio:* choose alsa
[*]*graphics:* doublebuffering ON, VertexShader HW, PixelShader OFF
[*]*Version:* Win98
[*]*Drives:* autodetect
[/LIST]
[*]**/usr/bin/wine regedit** and create the Keys: *AppDefaults\Starcraft.exe\X11 Driver*
in *HKCU\Software\Wine*
[*]add the following strings there:
"Desktop"="N"
"DXGrab"="N"
"Managed"="Y"
"useDGA"="N"
"useXRandR"="Y"
"useXVidMode"="N"
[*]to run Starcraft i use the following shell-script:
```
#!/bin/sh
*# just to verify i'm running the right version:*
winebin=**/usr/bin/wine**
**$winebin** --version

*#run starcraft (demo)*
**$winebin** "c:\games\scdemo\starcraft.exe"

[I]#reset to my preferred resolution after wine finished
#because wine sometines messes up the display or refreshrate[/I]
**sleep** 2 && **xrandr** -s 0
```
[/LIST]

take care to always use **/usr/bin/wine** and not just simple **wine** if you have other version of WINE installed beside the /usr/bin version.

i.e. I have the latest CVS installed to /usr/local/bin and
**wine --version** results in **Wine 0.9.20**

I hope this helps some of you who have trouble with newer WINEs
Good Luck,
Juve

---

### Post by Enverex on 2006-09-11
> **DeamonAxe said:**
> Did someone fixed the :

fixme:jack:JACK_drvLoad error loading the jack library libjack.so, please install this library to use jack

Error?

Using ALSA and EsounD drivers I have weird sound, Like skipping...

Thank,
Wine 0.9.20 - StarCraft 1.14 - Ubuntu 6.06 LTS - the Dapper Drake


You need to use the OSS driver, it's the only really 'supported' driver. The others are all more buggy and have issues. The fixme about jack isn't an error, it's a warning that you can safely ignore.

precinto: Are you using the latest version of Wine? (0.9.20) If not then try upgrading to that and see is that works. Apparently that error is caused by an app trying to write to another apps memory area inside Wine, normally caused by hack/trainer programs. So.. stop trying to cheat! If that doesn't work then try "sudo chmod -R 700 ~/.wine" .

---

### Post by Inhumane on 2006-09-11
I tried running it as an ISO, it didn't solve my very sluggish gameplay problem. How do I make it 16 bit?

---

### Post by iLoVe.cF- on 2006-09-12
Intel video cards cannot run starcraft in ubuntu

Does bwlauncher work well with starcraft(havnt tried :P)
starcraft start but can u guys try it ?

[www.bwprogrammers.com](www.bwprogrammers.com)

---

### Post by jdmpike on 2006-10-20
Hello all,

Running wine 0.9.22 on Edgy. StarCraft installed like a charm, no performance problems at all when playing.

I however can't connect to battle.net - it crashes instantly. Below is the log.

```
fixme:advapi:SetSecurityInfo stub
fixme:d3d:IWineD3DDeviceImpl_GetAvailableTextureMem (0x17d970) : stub, simulating 64MB for now, returning 64MB left
fixme:ddraw:IDirectDrawImpl_SetCooperativeLevel (0x17d188)->(0x10024,00000013)
fixme:x11drv:X11DRV_desktop_SetCurrentMode Cannot change screen BPP from 16 to 8
wine: Unhandled page fault on write access to 0x0129c000 at address 0x3e0594 (thread 0009), starting debugger...
Modules:
Cannot get info on module while no process is loaded
Threads:
process  tid      prio (all id:s are in hex)
0000000b 
        0000000d    0
        0000000c    0
00000008 (D) (null)
        00000014   15
        00000013    2
        00000011    0
        0000000f   15
        0000000a    1
        00000009    0

```

Any help would be greatly appreciated!

Thanks,

jdmpike

---

### Post by Consumed on 2006-10-22
jdmpike, have you installed the MS fonts?  Look at one of my other posts and it has the command to install the MS fonts and that should solve the problem.

---

### Post by MotK on 2006-11-05
I have installed the MS fonts and installed SC according to this guide but whenever I try to join a game on b.net, wine hangs with a black screen and nothing ever happens...I have wine running in the window, if that helps. 

If I left out any info, let me know...im running edgy with latest wine version.

---

### Post by CasB on 2006-11-15
Hmmz, sound doesn't work here :( And I can't start the game using starcraft.exe in my program files, I have to run setup.exe or install.exe on the cd... :S

---

### Post by WaveMyBlackFlag on 2006-12-05
](*,) 

okay, my problem:  I get everything installed and updated...

when I attempt to start the game I get an error saying it cannot find a needed file.  I realize this is probably due to the fact that I tried to install the program in my home folder.  So erased all and tried to install it to C:/ (drive_c) as listed in Wine.  It tells me the drive or path is write protected and I should try typing a drive letter before I attempt to install.  I did, it says same thing.  I am still way new at Wine and honestly have about a quarter of a clue as to what I'm doing.

---

### Post by WaveMyBlackFlag on 2006-12-05
nevermind.  figured it out-  works great - 600x480 sucks, but hey, I dont have any of the sound or video choppyness issues Ive been seeing.  thanks for the how to

---

### Post by blastradius on 2006-12-11
ok tried it but I get an exception error after entering the CD key, (yes it is legit!), says something about not finding the path.

Please help, it's a great game!

---

### Post by haxality on 2006-12-21
I seem to be unable to change the video resolution on my monitor. Is it because it's a laptop? I would like to be able to play starcraft in fullscreen, is all.

---

### Post by asantainnasa on 2007-03-13
> **souled said:**
> Starcraft works with emulated desktop, but changing the resolution has no effect. Even if I change the resolution to 1024x768, the game plays at 800x600 (I think), but it's too small for me. Anyone experiencing this?

haha, yea i had that too
but now i just use my own script
```
#!/bin/bash
xrandr -s 800x600
wine '/media/sda2/Program Files/Starcraft/starcraft.exe' -nice 20
wait
xrandr -s 1024x768
```
works well =]

---

### Post by asantainnasa on 2007-03-13
> **blastradius said:**
> ok tried it but I get an exception error after entering the CD key, (yes it is legit!), says something about not finding the path.

Please help, it's a great game!

can you give the exact error please?

---

### Post by rayofash on 2007-03-14
I'm getting an error (from the game) when it tries to create files. How do I fix this?

Edit: Oh, I fixed it by adding 'sudo' to the beginning of my launch script.

Wow, it's slow. Unplayably slow.

---

### Post by blastradius on 2007-03-15
Mine works perfectly after running wine under root.

Wow, it's slow. Unplayably slow.[/QUOTE]

Have you got your 3D drivers running ok?

I've got an ATI Radeon 9600 and that took a bit of fiddling to get sorted.

---

### Post by rayofash on 2007-03-20
> **blastradius said:**
> [quote=rayofash]Wow, it's slow. Unplayably slow.

Mine works perfectly after running wine under root.

Have you got your 3D drivers running ok?

I've got an ATI Radeon 9600 and that took a bit of fiddling to get sorted.[/QUOTE]

They're running fine. I get what feels like 60 frames a second in Enemy Territory. I have a GeForce FX 5200.

---

### Post by fearpi on 2007-03-20
> **asantainnasa said:**
> haha, yea i had that too
but now i just use my own script
```
#!/bin/bash
xrandr -s 800x600
wine '/media/sda2/Program Files/Starcraft/starcraft.exe' -nice 20
wait
xrandr -s 1024x768
```
works well =]

I have a laptop with a native (widescreen) resolution of 1280x800, so I used your script with an appropriately modified last line. However, when the game starts, the screen resizes such that the width fits, but the height is too much. It aligns fine with the top of the screen but goes off the bottom. Basically, the 4:3 screen is not stretching to match the aspect ratio of my monitor. How would I fix this?

---

### Post by Plantmiester on 2007-05-23
I'm getting the error message:

> exp1:Error 0x00000003:Path not found

right after I enter the CD-key in installation.

I'm completely new to Wine, so I may be a bit clueless with this one.

---

### Post by blastradius on 2007-05-24
> **Plantmiester said:**
> I'm getting the error message:



right after I enter the CD-key in installation.

I'm completely new to Wine, so I may be a bit clueless with this one.

I had the same problem, it's a while ago now but I think I fixed it by running the starcraft install script as **root** through wine.

Try that.

---

### Post by thegrimgod on 2007-06-02
I tried almost all of the suggestions , hope i didn't miss any , the nice stuff didn't work , juve's regedit stuff might of did something ,but i deleted the register just to see if there was something ,and i have the same speed as with the register, overall, i can get to battlenet , i have good sound , but the game is laggy as hell, pls help , im using wine 0.9.37 and i can play warcraft tft solo games with no problem, so starcraft... bah..

---

### Post by dnzz on 2007-06-02
I used to have a lot of 2D graphic problems while using generic kernel. I changed it to 386i kernel and everything solved. This is only an idea.

My problem is with screen resolution. My laptop changes resolution to 640x480 perfectly but i can not see the bottom of the screen. I have a wide screen laptop. Do you have any idea how to fix this?

---

### Post by LinuxNewb51 on 2007-07-28
I got Starcraft installed easily. But when I try to run it, the wine desktop comes up for a few seconds then it disapears. This happens every time I try to run it. I think this is easy to fix I just don't know what to do.

---

### Post by bowsercake on 2007-08-21
Starcraft runs slow even with the nice -20 option.  Starcraft runs 3rd graphics work for everything else its just that Starcraft runs at a really slow pace.  I had it working before but I reinstalled Fiesty.  Last time I had some libraries set up but I forget what the configurations were.  Does anyone have any insight into this problem?

EDIT: I added the -gl option and it helped but it is still slow, just not dead slow.

---

### Post by carlosalvatore on 2008-03-27
Hello!

My Starcraft is running like in windows.

I didn't install StarCraft again 'cause i had my starcraft installed in a partition of my hard drive when i had windows, but it will be the same. The only difference was to add the reg info to the wine registry, but i guess it won't be a problem if you're making a new clean installation.

The key avoiding starcraft get slow is disabling "Allow the window manager to control the windows" on WineConfig, or disabling the gnome visual effects (System -> Appearance -> Visual Effects -> None. (But i rather prefer the first option).

To see Starcraft on full screen do NOT use the virtual desktop (also an option in WineConfig).*

I can play both single player and multiplayer with the last blizzard patch (to run UDP protocol on LAN).

If you still have problems with Starcraft you should trying the info on the winehq plus what I've told you.

If you don't want to use your cdrom you alway can do and iso image, and use a no CD app (Be aware that you must have the original CD, if don't you might be violating the law!). I use acetoneISO2 to mount easy and quickly.

Greetings! and I hope this info helps you!

-
* I strongly recommend using the virtual desktop when you're installing something with Wine, in case it freezes, and the first time you run it. Once you've test the application well, you can run it without the virtual desktop.

This tip works also for Diablo 2 + Expansion.

---

