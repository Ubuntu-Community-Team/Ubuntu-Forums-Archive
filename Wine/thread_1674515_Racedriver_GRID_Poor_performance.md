---
title: "Racedriver GRID: Poor performance"
date: 2011-01-24
forum: Wine
---

### Post by shreepads on 2011-01-24
Hi

System Details
- 64 bit Ubuntu 10.04.1 LTS (Lucid)
- Intel DG33FB motherboard (PCI Express v1.1)
- Intel C2D E7200 @ 2.53Ghz
- 2 GB RAM (DDR2 800)
- Palit GT 240 1GB DDR5 Sonic PCIe card (factory overclocked)
- Latest NVidia proprietary drivers (260.19.29)
- Default Wine install (1.2) from repositories

From what I can see on the box the system should easily run Racedriver GRID (at least on Windows). Also other stuff that uses the card (Compiz, Games from the repository, Celestia, VDPAU) are very stable.

I've also got Commandos 2 running on Wine with no problems with the above setup.

Installing Racedriver GRID from disk was fairly smooth, got it done on the first attempt with no issues.

Running it from the default desktop icon was smooth as well, was running full-screen 1440x900 res with no issues, that is until I started the first race...

The first few seconds were fine but then started getting stuttering sound and the game soon went unresponsive, requiring a hard boot.

Next up, I first tried reducing the in-game settings in steps all the way down to 800x600, Low detail. Now while the game didn't completely freeze up, I was able to race a bit longer before the sound stuttering and freezing up issues started, but was able to exit safely but with a very badly lagging system.

Tried some of the recommended Wine performance tweaks to no avail.
- Registry Entries:
  -> Alsa Driver: 
    -> UseDirectHW set to y
  -> Direct3D:
    -> VideoMemorySize set to 512 and 1024
    -> DirectDrawRenderer set to opengl, but then deleted as it didn't help
- Commandline, used WINEDEBUG=-all

Also tried running Wine in the desktop emulation mode (800x600) with no luck. At this stage I also tried changing the process priority to -10 but no luck.

Observations:
- The CPU is maxed out while actively playing (both cores). When I stop the race e.g. while using the menu options, one core is maxed out at a time
- The graphics card seems relatively unstressed. While it does move to the performance mode (seen via NVidia Settings) it definitely doesn't heat up too much (approx 55 deg C as opposed to approx 70 deg C in extended VDPAU usage)

Any suggestions?

---

### Post by Halzen on 2011-01-24
The following needs to be overriden for Grid to work: xinput1_3.dll, d3dx9_36.dll, openal32.dll, and wrap_oal.dll.

If it's still not running well even at low settings, try finding the following document: /Codemasters/GRID/hardwaresettings/hardware_settings_config.xml

In there, disable multisampling, post processing, and shadows.

---

### Post by shreepads on 2011-01-25
> **Halzen said:**
> The following needs to be overriden for Grid to work: xinput1_3.dll, d3dx9_36.dll, openal32.dll, and wrap_oal.dll.

If it's still not running well even at low settings, try finding the following document: /Codemasters/GRID/hardwaresettings/hardware_settings_config.xml

In there, disable multisampling, post processing, and shadows.

Thanks for that!

I'm not too familiar with the whole DLL override process so let me tell you what I did (after some Googling around)

- Copied xinput1_3.dll, d3dx9_36.dll, opengl32.dll (couldn't find openal32.dll so assume that's a typo?) from my dual boot Win XP (SP3) windows/system32 folder to ~/.wine/drive_c/Program Files/Codemasters/GRID

- I couldn't find wrap_oal.dll anywhere in my WinXp install so left that out

- Modified the default GRID desktop launcher so that it reads:

```
env WINEPREFIX="/home/user/.wine" WINEDEBUG="-all" WINEDLLOVERRIDES="xinput1_3,d3dx9_36,opengl32=n" wine C:\\Program\ Files\\Codemasters\\GRID\\GRID.exe
``` 

- And then ran the above from the command line

Resulting performance is a bit better, was able to complete a lap but the frame rate was definitely lagging at times and sound was completely stuttering.

Anything else I can try?

TIA!

---

### Post by shreepads on 2011-01-25
Tried again after setting DirectDrawRenderer to opengl again.. Seems to be stable with a LITTLE better performance (hard to tell)..

But at least I could finish the first Toyota Supra race coming in 7th / 8, although 23 secs behind 1st!!

---

### Post by Halzen on 2011-01-25
Well, when we say "override" in Wine, we usually mean the following process:

1. Open a terminal and type "winecfg" (without quotes, of course).
2. Choose the application profile you want to modify in the Applications tab, then switch to the Libraries tab.
3. In the "New override for library" box, type in the item you wish to override (for example, "xinput1_3.dll" without quotes) and click Add.
4. Normally, the default "(native, builtin)" will do the job. If not, click on your new override in the "Existing overrides" list and select Edit to pick out a new parameter.

Try following those steps with the overrides I suggested.

---

### Post by shreepads on 2011-01-25
Deleted the DLLs dropped into the GRID folder, followed your instructions above, launched from the default launcher and its all working perfectly!

Bumped up to 1024x768, all settings turned to Low/ Off and still delivering very good video and audio... 

Thanks a ton!! Now if only I could improve my driving that easily....... ;)

Only bother now is the DVD drive which must spin up at start each time, it creates a real racket and I'm worried the vibrations will affect my precious HDDs...

---

### Post by Halzen on 2011-01-25
> **shreepads said:**
> Deleted the DLLs dropped into the GRID folder, followed your instructions above, launched from the default launcher and its all working perfectly!

Bumped up to 1024x768, all settings turned to Low/ Off and still delivering very good video and audio... 

Thanks a ton!! Now if only I could improve my driving that easily....... ;)

Only bother now is the DVD drive which must spin up at start each time, it creates a real racket and I'm worried the vibrations will affect my precious HDDs...

Good to hear that worked for you. It's always good when we get by with the easy fixes. :P

I hate DVDs. I use Steam for my gaming nowadays, so I haven't had to use a physical disc in a good long time. For anything else, I've always ripped the ISOs or found a no-CD patch. You might consider doing the same.

---

### Post by shreepads on 2011-01-25
> **Halzen said:**
> 
I hate DVDs. I use Steam for my gaming nowadays, so I haven't had to use a physical disc in a good long time. For anything else, I've always ripped the ISOs or found a no-CD patch. You might consider doing the same.

I did try to create an ISO image using Brasero and then mount it using isomount and then point Wine to it in 'Drives'... But the SecuROM protection jinxed it and I have a 6.4 GB image that is blank when mounted...

Any ideas of other tools? I am able to rip DVD videos without any problems using Handbrake...

---

### Post by Halzen on 2011-01-26
> **shreepads said:**
> I did try to create an ISO image using Brasero and then mount it using isomount and then point Wine to it in 'Drives'... But the SecuROM protection jinxed it and I have a 6.4 GB image that is blank when mounted...

Any ideas of other tools? I am able to rip DVD videos without any problems using Handbrake...

SecuROM will probably thwart most ripping methods. A no-CD patch will do you better in this case.

---

### Post by shreepads on 2011-01-26
Thanks!

Now for some more drama, got a Wine update earlier today and after applying it my beautifully working GRID is now crashing :mad:

Have attached the completely unhelpful screen message.

Ran it from the terminal and got the following. 

Any ideas what went wrong? From what little I saw in Update Manager the Wine update was a security related one, nothing to the effect that 'THIS WILL CRASH WORKING APPS'...

```

user@UbuntuD64Lucid:~$ env WINEPREFIX="/home/user/.wine" WINEDEBUG="-all" wine C:\\Program\ Files\\Codemasters\\GRID\\GRID.exe 

wine: Unhandled page fault on read access to 0x00000000 at address 0x7e0ae734 (thread 0009), starting debugger...
Unhandled exception: page fault on read access to 0x00000000 in 32-bit code (0x7e0ae734).
Register dump:
 CS:0023 SS:002b DS:002b ES:002b FS:0063 GS:006b
 EIP:7e0ae734 ESP:021d8b10 EBP:021d8d08 EFLAGS:00010246(  R- --  I  Z- -P- )
 EAX:00000000 EBX:7e0f1ff4 ECX:ffffffff EDX:00000000
 ESI:7e0f9fb8 EDI:00000000
Stack dump:
0x021d8b10:  00001f03 03c000ea 7c5b1028 ffffffff
0x021d8b20:  00000001 00000001 00000000 00000018
0x021d8b30:  00000001 7c53f7a8 00002200 021d8b60
0x021d8b40:  00000000 00000000 00000000 7c5b1028
0x021d8b50:  7c5a7330 000001ff 03c000ea 00000000
0x021d8b60:  00000002 7bc9cff4 021d8cd8 f75ab011
Backtrace:
=>0 0x7e0ae734 in winex11 (+0x3e734) (0x021d8d08)
  1 0x7e0b1337 X11DRV_wglGetProcAddress+0x26() in winex11 (0x021d8d58)
  2 0x7eb38cc9 wglGetProcAddress+0x68() in gdi32 (0x021d8da8)
  3 0x7ecfe7a3 in wined3d (+0x4e7a2) (0x021d9448)
  4 0x7ed1308a in wined3d (+0x63089) (0x021d9468)
  5 0x7ed9baba WineDirect3DCreate+0x59() in wined3d (0x021d94a8)
  6 0x7ede8d2d Direct3DCreate9+0x5c() in d3d9 (0x021d94d8)
  7 0x0162c1c8 in grid (+0x122c1c7) (0x021d951c)
  8 0x0162c608 in grid (+0x122c607) (0x021dab5c)
  9 0x01356447 in grid (+0xf56446) (0x021ef89c)
  10 0x01249c1a in grid (+0xe49c19) (0x021efd44)
  11 0x00000008 (0x015c349d)
  12 0x5d8b5351 (0xec8b55c3)
0x7e0ae734: repne scasb	%es:(%edi)
Modules:
Module	Address			Debug info	Name (110 modules)
PE	  230000-  246000	Deferred        xinput1_3
PE	  400000- 1ce4000	Export          grid
PE	 21f0000- 25a7000	Deferred        d3dx9_37
PE	10000000-10019000	Deferred        openal32
PE	18000000-18033000	Deferred        binkw32
ELF	7a14f000-7b800000	Deferred        libnvidia-glcore.so.260.19.29
ELF	7b800000-7b97d000	Deferred        kernel32<elf>
  \-PE	7b810000-7b97d000	\               kernel32
ELF	7bc00000-7bcb9000	Deferred        ntdll<elf>
  \-PE	7bc10000-7bcb9000	\               ntdll
ELF	7bf00000-7bf04000	Deferred        <wine-loader>
ELF	7da37000-7db00000	Deferred        libgl.so.1
ELF	7db41000-7db75000	Deferred        uxtheme<elf>
  \-PE	7db50000-7db75000	\               uxtheme
ELF	7db75000-7db7a000	Deferred        libgpg-error.so.0
ELF	7db7a000-7db83000	Deferred        librt.so.1
ELF	7db83000-7dbbc000	Deferred        libdbus-1.so.3
ELF	7dbbc000-7dc2f000	Deferred        libgcrypt.so.11
ELF	7dc2f000-7dc40000	Deferred        libtasn1.so.3
ELF	7dc40000-7dc44000	Deferred        libkeyutils.so.1
ELF	7dc44000-7dc4c000	Deferred        libkrb5support.so.0
ELF	7dc4c000-7dc50000	Deferred        libcom_err.so.2
ELF	7dc50000-7dc74000	Deferred        libk5crypto.so.3
ELF	7dc74000-7dd25000	Deferred        libkrb5.so.3
ELF	7dd25000-7dd36000	Deferred        libavahi-client.so.3
ELF	7dd36000-7dd42000	Deferred        libavahi-common.so.3
ELF	7dd42000-7dddd000	Deferred        libgnutls.so.26
ELF	7dddd000-7de0c000	Deferred        libgssapi_krb5.so.2
ELF	7de0c000-7de53000	Deferred        libcups.so.2
ELF	7de86000-7de90000	Deferred        libxcursor.so.1
ELF	7de90000-7de96000	Deferred        libxfixes.so.3
ELF	7de96000-7de9a000	Deferred        libxcomposite.so.1
ELF	7de9a000-7dea2000	Deferred        libxrandr.so.2
ELF	7dea2000-7deac000	Deferred        libxrender.so.1
ELF	7deac000-7deb2000	Deferred        libxxf86vm.so.1
ELF	7deb2000-7deb6000	Deferred        libxinerama.so.1
ELF	7deb6000-7ded8000	Deferred        imm32<elf>
  \-PE	7dec0000-7ded8000	\               imm32
ELF	7ded8000-7dede000	Deferred        libxdmcp.so.6
ELF	7dede000-7dee2000	Deferred        libxau.so.6
ELF	7dee2000-7defc000	Deferred        libxcb.so.1
ELF	7defc000-7e019000	Deferred        libx11.so.6
ELF	7e019000-7e032000	Deferred        libice.so.6
ELF	7e032000-7e03b000	Deferred        libsm.so.6
ELF	7e03b000-7e03d000	Deferred        libnvidia-tls.so.260.19.29
ELF	7e058000-7e0fb000	Export          winex11<elf>
  \-PE	7e070000-7e0fb000	\               winex11
ELF	7e151000-7e178000	Deferred        libexpat.so.1
ELF	7e178000-7e1a8000	Deferred        libfontconfig.so.1
ELF	7e1a8000-7e1bd000	Deferred        libz.so.1
ELF	7e1bd000-7e233000	Deferred        libfreetype.so.6
ELF	7e233000-7e238000	Deferred        libuuid.so.1
ELF	7e238000-7e248000	Deferred        libxext.so.6
ELF	7e250000-7e26b000	Deferred        wsock32<elf>
  \-PE	7e260000-7e26b000	\               wsock32
ELF	7e26b000-7e354000	Deferred        oleaut32<elf>
  \-PE	7e280000-7e354000	\               oleaut32
ELF	7e354000-7e3d6000	Deferred        msvcrt<elf>
  \-PE	7e370000-7e3d6000	\               msvcrt
ELF	7e3d6000-7e40f000	Deferred        dinput<elf>
  \-PE	7e3e0000-7e40f000	\               dinput
ELF	7e40f000-7e4fa000	Deferred        comctl32<elf>
  \-PE	7e420000-7e4fa000	\               comctl32
ELF	7e4fa000-7e55c000	Deferred        shlwapi<elf>
  \-PE	7e510000-7e55c000	\               shlwapi
ELF	7e55c000-7e736000	Deferred        shell32<elf>
  \-PE	7e570000-7e736000	\               shell32
ELF	7e736000-7e76e000	Deferred        winspool<elf>
  \-PE	7e740000-7e76e000	\               winspool
ELF	7e76e000-7e7cd000	Deferred        setupapi<elf>
  \-PE	7e780000-7e7cd000	\               setupapi
ELF	7e7cd000-7e7e1000	Deferred        libresolv.so.2
ELF	7e7e3000-7e7fe000	Deferred        dinput8<elf>
  \-PE	7e7f0000-7e7fe000	\               dinput8
ELF	7e7fe000-7e81f000	Deferred        iphlpapi<elf>
  \-PE	7e800000-7e81f000	\               iphlpapi
ELF	7e81f000-7e833000	Deferred        lz32<elf>
  \-PE	7e820000-7e833000	\               lz32
ELF	7e833000-7e8a8000	Deferred        rpcrt4<elf>
  \-PE	7e840000-7e8a8000	\               rpcrt4
ELF	7e8a8000-7e9a8000	Deferred        ole32<elf>
  \-PE	7e8c0000-7e9a8000	\               ole32
ELF	7e9a8000-7ea3d000	Deferred        winmm<elf>
  \-PE	7e9b0000-7ea3d000	\               winmm
ELF	7ea3d000-7ea85000	Deferred        dsound<elf>
  \-PE	7ea40000-7ea85000	\               dsound
ELF	7ea85000-7eae0000	Deferred        advapi32<elf>
  \-PE	7ea90000-7eae0000	\               advapi32
ELF	7eae0000-7eb6c000	Export          gdi32<elf>
  \-PE	7eaf0000-7eb6c000	\               gdi32
ELF	7eb6c000-7ec9d000	Deferred        user32<elf>
  \-PE	7eb80000-7ec9d000	\               user32
ELF	7ec9d000-7edd5000	Export          wined3d<elf>
  \-PE	7ecb0000-7edd5000	\               wined3d
ELF	7edd5000-7ee09000	Export          d3d9<elf>
  \-PE	7ede0000-7ee09000	\               d3d9
ELF	7ee09000-7ee36000	Deferred        ws2_32<elf>
  \-PE	7ee10000-7ee36000	\               ws2_32
ELF	7ef9a000-7efa6000	Deferred        libnss_files.so.2
ELF	7efa6000-7efbd000	Deferred        libnsl.so.1
ELF	7efbd000-7efe3000	Deferred        libm.so.6
ELF	7efe6000-7efff000	Deferred        version<elf>
  \-PE	7eff0000-7efff000	\               version
ELF	f7404000-f740e000	Deferred        libnss_nis.so.2
ELF	f740f000-f7413000	Deferred        libdl.so.2
ELF	f7413000-f756d000	Deferred        libc.so.6
ELF	f756e000-f7587000	Deferred        libpthread.so.0
ELF	f7588000-f7590000	Deferred        libnss_compat.so.2
ELF	f75a4000-f76e4000	Deferred        libwine.so.1
ELF	f76e6000-f7704000	Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
00000008 (D) C:\Program Files\Codemasters\GRID\GRID.exe
	00000009    0 <==
0000000e services.exe
	00000014    0
	00000010    0
	0000000f    0
00000011 winedevice.exe
	00000017    0
	00000016    0
	00000013    0
	00000012    0
00000023 explorer.exe
	00000024    0
Backtrace:
=>0 0x7e0ae734 in winex11 (+0x3e734) (0x021d8d08)
  1 0x7e0b1337 X11DRV_wglGetProcAddress+0x26() in winex11 (0x021d8d58)
  2 0x7eb38cc9 wglGetProcAddress+0x68() in gdi32 (0x021d8da8)
  3 0x7ecfe7a3 in wined3d (+0x4e7a2) (0x021d9448)
  4 0x7ed1308a in wined3d (+0x63089) (0x021d9468)
  5 0x7ed9baba WineDirect3DCreate+0x59() in wined3d (0x021d94a8)
  6 0x7ede8d2d Direct3DCreate9+0x5c() in d3d9 (0x021d94d8)
  7 0x0162c1c8 in grid (+0x122c1c7) (0x021d951c)
  8 0x0162c608 in grid (+0x122c607) (0x021dab5c)
  9 0x01356447 in grid (+0xf56446) (0x021ef89c)
  10 0x01249c1a in grid (+0xe49c19) (0x021efd44)
  11 0x00000008 (0x015c349d)
  12 0x5d8b5351 (0xec8b55c3)
user@UbuntuD64Lucid:~$ 


```

---

### Post by Halzen on 2011-01-26
That appears to be a DX9 error. Let's try adding DX9 through winetricks, and then putting in some native dll overrides.

1. In your Terminal, type in sh winetricks. Don't close this terminal window until you're done with Winetricks.

2. In the Winetricks window, select d3dx9, d3dx9_36, d3dx9_42, d3dxof, devenum, dinput8, and directx9. Then hit Ok and let Winetricks do its thing, following any instructions that come up.

3. Close that and type winecfg into your Terminal. Add the following native overrides, just like we did before: d3d9, d3dx9_36, d3dx9_42, d3dxof, dinput, and dinput8. Apply and close.

---

### Post by shreepads on 2011-01-26
Tried again after
- Removing the DirectDrawRenderer (set to opengl) value from the registry
- Removing all the GRID specific Wine Config (DLL overrides, Virtual desktop settings)
- Removing WINEDEBUG="-all" from the command line

Running GRID from terminal without WINEDEBUG="-all":

```

user@UbuntuD64Lucid:~/pitivi/pitivi-0.13.5$ env WINEPREFIX="/home/user/.wine" wine C:\\Program\ Files\\Codemasters\\GRID\\GRID.exe 

fixme:ntdll:NtQuerySystemInformation info_class SYSTEM_HANDLE_INFORMATION
fixme:ntdll:NtQueryObject Unsupported information class 3
err:rpc:I_RpcGetBuffer no binding
wine: Unhandled page fault on read access to 0x00000000 at address 0x7e051734 (thread 0009), starting debugger...
Unhandled exception: page fault on read access to 0x00000000 in 32-bit code (0x7e051734).
Register dump:
 CS:0023 SS:002b DS:002b ES:002b FS:0063 GS:006b
 EIP:7e051734 ESP:021d8b10 EBP:021d8d08 EFLAGS:00010246(  R- --  I  Z- -P- )
 EAX:00000000 EBX:7e094ff4 ECX:ffffffff EDX:00000000
 ESI:7e09cfb8 EDI:00000000
Stack dump:
0x021d8b10:  00001f03 03c000ea 7c1903e0 ffffffff
0x021d8b20:  00000001 00000001 00000000 00000018
0x021d8b30:  00000001 7da3e420 00002200 021d8b60
0x021d8b40:  00000000 00000000 00000000 7c1903e0
0x021d8b50:  7daa6970 000001ff 03c000ea 00000000
0x021d8b60:  00000002 7bc9cff4 021d8cd8 f763b011
Backtrace:
=>0 0x7e051734 in winex11 (+0x41734) (0x021d8d08)
  1 0x7e054337 X11DRV_wglGetProcAddress+0x26() in winex11 (0x021d8d58)
  2 0x7eb38cc9 wglGetProcAddress+0x68() in gdi32 (0x021d8da8)
  3 0x7ecfe7a3 in wined3d (+0x4e7a2) (0x021d9448)
  4 0x7ed1308a in wined3d (+0x63089) (0x021d9468)
  5 0x7ed9baba WineDirect3DCreate+0x59() in wined3d (0x021d94a8)
  6 0x7ede8d2d Direct3DCreate9+0x5c() in d3d9 (0x021d94d8)
  7 0x0162c1c8 in grid (+0x122c1c7) (0x021d951c)
  8 0x0162c608 in grid (+0x122c607) (0x021dab5c)
  9 0x01356447 in grid (+0xf56446) (0x021ef89c)
  10 0x01249c1a in grid (+0xe49c19) (0x021efd44)
  11 0x00000008 (0x015c349d)
  12 0x5d8b5351 (0xec8b55c3)
0x7e051734: repne scasb	%es:(%edi)
Modules:
Module	Address			Debug info	Name (112 modules)
PE	  230000-  246000	Deferred        xinput1_3
PE	  400000- 1ce4000	Export          grid
PE	 21f0000- 25a7000	Deferred        d3dx9_37
PE	18000000-18033000	Deferred        binkw32
ELF	7b800000-7b97d000	Deferred        kernel32<elf>
  \-PE	7b810000-7b97d000	\               kernel32
ELF	7bc00000-7bcb9000	Deferred        ntdll<elf>
  \-PE	7bc10000-7bcb9000	\               ntdll
ELF	7bf00000-7bf04000	Deferred        <wine-loader>
ELF	7c289000-7d93a000	Deferred        libnvidia-glcore.so.260.19.29
ELF	7d93a000-7da03000	Deferred        libgl.so.1
ELF	7dad8000-7db0c000	Deferred        uxtheme<elf>
  \-PE	7dae0000-7db0c000	\               uxtheme
ELF	7db0c000-7db11000	Deferred        libgpg-error.so.0
ELF	7db11000-7db4a000	Deferred        libdbus-1.so.3
ELF	7db4a000-7dbbd000	Deferred        libgcrypt.so.11
ELF	7dbbd000-7dbce000	Deferred        libtasn1.so.3
ELF	7dbce000-7dbd2000	Deferred        libkeyutils.so.1
ELF	7dbd2000-7dbda000	Deferred        libkrb5support.so.0
ELF	7dbda000-7dbde000	Deferred        libcom_err.so.2
ELF	7dbde000-7dc02000	Deferred        libk5crypto.so.3
ELF	7dc02000-7dcb3000	Deferred        libkrb5.so.3
ELF	7dcb3000-7dcc4000	Deferred        libavahi-client.so.3
ELF	7dcc4000-7dcd0000	Deferred        libavahi-common.so.3
ELF	7dcd0000-7dd6b000	Deferred        libgnutls.so.26
ELF	7dd6b000-7dd9a000	Deferred        libgssapi_krb5.so.2
ELF	7dd9a000-7dde1000	Deferred        libcups.so.2
ELF	7de14000-7de1e000	Deferred        libxcursor.so.1
ELF	7de1e000-7de24000	Deferred        libxfixes.so.3
ELF	7de24000-7de28000	Deferred        libxcomposite.so.1
ELF	7de28000-7de30000	Deferred        libxrandr.so.2
ELF	7de30000-7de3a000	Deferred        libxrender.so.1
ELF	7de3a000-7de40000	Deferred        libxxf86vm.so.1
ELF	7de40000-7de44000	Deferred        libxinerama.so.1
ELF	7de44000-7de66000	Deferred        imm32<elf>
  \-PE	7de50000-7de66000	\               imm32
ELF	7de66000-7de6c000	Deferred        libxdmcp.so.6
ELF	7de6c000-7de70000	Deferred        libxau.so.6
ELF	7de70000-7de8a000	Deferred        libxcb.so.1
ELF	7de8a000-7de8f000	Deferred        libuuid.so.1
ELF	7de8f000-7dfac000	Deferred        libx11.so.6
ELF	7dfac000-7dfbc000	Deferred        libxext.so.6
ELF	7dfbc000-7dfd5000	Deferred        libice.so.6
ELF	7dfd5000-7dfde000	Deferred        libsm.so.6
ELF	7dfde000-7dfe0000	Deferred        libnvidia-tls.so.260.19.29
ELF	7dffb000-7e09e000	Export          winex11<elf>
  \-PE	7e010000-7e09e000	\               winex11
ELF	7e0df000-7e106000	Deferred        libexpat.so.1
ELF	7e106000-7e136000	Deferred        libfontconfig.so.1
ELF	7e136000-7e14b000	Deferred        libz.so.1
ELF	7e14b000-7e1c1000	Deferred        libfreetype.so.6
ELF	7e1de000-7e1f9000	Deferred        wsock32<elf>
  \-PE	7e1e0000-7e1f9000	\               wsock32
ELF	7e1f9000-7e2e2000	Deferred        oleaut32<elf>
  \-PE	7e210000-7e2e2000	\               oleaut32
ELF	7e2e2000-7e364000	Deferred        msvcrt<elf>
  \-PE	7e2f0000-7e364000	\               msvcrt
ELF	7e364000-7e39d000	Deferred        dinput<elf>
  \-PE	7e370000-7e39d000	\               dinput
ELF	7e39d000-7e488000	Deferred        comctl32<elf>
  \-PE	7e3b0000-7e488000	\               comctl32
ELF	7e488000-7e4ea000	Deferred        shlwapi<elf>
  \-PE	7e4a0000-7e4ea000	\               shlwapi
ELF	7e4ea000-7e6c4000	Deferred        shell32<elf>
  \-PE	7e500000-7e6c4000	\               shell32
ELF	7e6c4000-7e6fc000	Deferred        winspool<elf>
  \-PE	7e6d0000-7e6fc000	\               winspool
ELF	7e6fc000-7e75b000	Deferred        setupapi<elf>
  \-PE	7e710000-7e75b000	\               setupapi
ELF	7e75b000-7e76f000	Deferred        libresolv.so.2
ELF	7e76f000-7e790000	Deferred        iphlpapi<elf>
  \-PE	7e780000-7e790000	\               iphlpapi
ELF	7e790000-7e799000	Deferred        librt.so.1
ELF	7e799000-7e7e7000	Deferred        libopenal.so.1
ELF	7e7e9000-7e804000	Deferred        dinput8<elf>
  \-PE	7e7f0000-7e804000	\               dinput8
ELF	7e804000-7e81f000	Deferred        openal32<elf>
  \-PE	7e810000-7e81f000	\               openal32
ELF	7e81f000-7e833000	Deferred        lz32<elf>
  \-PE	7e820000-7e833000	\               lz32
ELF	7e833000-7e8a8000	Deferred        rpcrt4<elf>
  \-PE	7e840000-7e8a8000	\               rpcrt4
ELF	7e8a8000-7e9a8000	Deferred        ole32<elf>
  \-PE	7e8c0000-7e9a8000	\               ole32
ELF	7e9a8000-7ea3d000	Deferred        winmm<elf>
  \-PE	7e9b0000-7ea3d000	\               winmm
ELF	7ea3d000-7ea85000	Deferred        dsound<elf>
  \-PE	7ea40000-7ea85000	\               dsound
ELF	7ea85000-7eae0000	Deferred        advapi32<elf>
  \-PE	7ea90000-7eae0000	\               advapi32
ELF	7eae0000-7eb6c000	Export          gdi32<elf>
  \-PE	7eaf0000-7eb6c000	\               gdi32
ELF	7eb6c000-7ec9d000	Deferred        user32<elf>
  \-PE	7eb80000-7ec9d000	\               user32
ELF	7ec9d000-7edd5000	Export          wined3d<elf>
  \-PE	7ecb0000-7edd5000	\               wined3d
ELF	7edd5000-7ee09000	Export          d3d9<elf>
  \-PE	7ede0000-7ee09000	\               d3d9
ELF	7ee09000-7ee36000	Deferred        ws2_32<elf>
  \-PE	7ee10000-7ee36000	\               ws2_32
ELF	7ef9a000-7efa6000	Deferred        libnss_files.so.2
ELF	7efa6000-7efbd000	Deferred        libnsl.so.1
ELF	7efbd000-7efe3000	Deferred        libm.so.6
ELF	7efe6000-7efff000	Deferred        version<elf>
  \-PE	7eff0000-7efff000	\               version
ELF	f7494000-f749e000	Deferred        libnss_nis.so.2
ELF	f749f000-f74a3000	Deferred        libdl.so.2
ELF	f74a3000-f75fd000	Deferred        libc.so.6
ELF	f75fe000-f7617000	Deferred        libpthread.so.0
ELF	f7618000-f7620000	Deferred        libnss_compat.so.2
ELF	f7634000-f7774000	Deferred        libwine.so.1
ELF	f7776000-f7794000	Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
00000008 (D) C:\Program Files\Codemasters\GRID\GRID.exe
	00000009    0 <==
0000000e services.exe
	00000019    0
	00000015    0
	00000014    0
	00000010    0
	0000000f    0
00000011 winedevice.exe
	00000017    0
	00000016    0
	00000013    0
	00000012    0
00000023 explorer.exe
	00000024    0
Backtrace:
=>0 0x7e051734 in winex11 (+0x41734) (0x021d8d08)
  1 0x7e054337 X11DRV_wglGetProcAddress+0x26() in winex11 (0x021d8d58)
  2 0x7eb38cc9 wglGetProcAddress+0x68() in gdi32 (0x021d8da8)
  3 0x7ecfe7a3 in wined3d (+0x4e7a2) (0x021d9448)
  4 0x7ed1308a in wined3d (+0x63089) (0x021d9468)
  5 0x7ed9baba WineDirect3DCreate+0x59() in wined3d (0x021d94a8)
  6 0x7ede8d2d Direct3DCreate9+0x5c() in d3d9 (0x021d94d8)
  7 0x0162c1c8 in grid (+0x122c1c7) (0x021d951c)
  8 0x0162c608 in grid (+0x122c607) (0x021dab5c)
  9 0x01356447 in grid (+0xf56446) (0x021ef89c)
  10 0x01249c1a in grid (+0xe49c19) (0x021efd44)
  11 0x00000008 (0x015c349d)
  12 0x5d8b5351 (0xec8b55c3)

user@UbuntuD64Lucid:~/pitivi/pitivi-0.13.5$ 


```

And on running Wine config I got an alert that the Audio drivers were not set so they would be set automatically. On the Audio tab I can see 'ALSA Driver' is selected, but when I hit the 'Test Sound' button I get a 'Audio test failed!' error dialog... Screenshot attached

winecfg from terminal:

```

user@UbuntuD64Lucid:~/pitivi/pitivi-0.13.5$ winecfg

fixme:wave:ALSA_ComputeCaps Device has a minimum of 2 channels
fixme:wave:ALSA_ComputeCaps Device has a minimum of 2 channels
fixme:mixer:ALSA_MixerInit No master control found on HDA NVidia, disabling mixer
fixme:mixer:ALSA_MixerInit No master control found on HDA NVidia, disabling mixer
user@UbuntuD64Lucid:~/pitivi/pitivi-0.13.5$ 


```

---

### Post by shreepads on 2011-01-26
> **Halzen said:**
> That appears to be a DX9 error. Let's try adding DX9 through winetricks, and then putting in some native dll overrides.

1. In your Terminal, type in sh winetricks. Don't close this terminal window until you're done with Winetricks.

2. In the Winetricks window, select d3dx9, d3dx9_36, d3dx9_42, d3dxof, devenum, dinput8, and directx9. Then hit Ok and let Winetricks do its thing, following any instructions that come up.

3. Close that and type winecfg into your Terminal. Add the following native overrides, just like we did before: d3d9, d3dx9_36, d3dx9_42, d3dxof, dinput, and dinput8. Apply and close.

Sorry missed this post from you while I was messing around with my last.. Will do...

EDIT:

Can't seem to get winetricks running. Is not in the repository, should it have been automatically installed along with Wine?

```

sysadmin@UbuntuD64Lucid:~$ sh winetricks
sh: Can't open winetricks
sysadmin@UbuntuD64Lucid:~$ echo $PATH
/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games
sysadmin@UbuntuD64Lucid:~$ 

```

EDIT:

Please ignore, got winetricks running...

---

### Post by shreepads on 2011-01-27
Sorry it didn't work...

Winetricks ran fine, installing all the selected components

Then I ran winecfg and the Libraries tab already had several overrides in place. Just tried running GRID from the default launcher with these overrides but crashed same as before.

Seeing that the default setup already had several overrides in place (first attachment) I though I'll setup a separate GRID specific override setup so I added GRID to the application list and then setup the overrides mentioned in your post (second attachment).

Ran GRID from the default launcher and terminal, same crash behaviour, but the messages in terminal are slightly different.

Anything I can do differently? Also the Test Sound option is still generating an error as described before.

[I]EDIT:

Added devenum to the override list for GRID, same result...[/I]


```

user@UbuntuD64Lucid:~$ env WINEPREFIX="/home/user/.wine" wine C:\\Program\ Files\\Codemasters\\GRID\\GRID.exe 

fixme:ntdll:NtQuerySystemInformation info_class SYSTEM_HANDLE_INFORMATION
fixme:ntdll:NtQueryObject Unsupported information class 3
err:rpc:I_RpcGetBuffer no binding
fixme:win:EnumDisplayDevicesW ((null),0,0x21d8e3c,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),1,0x21d8e3c,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x21d8e3c,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),1,0x21d8e3c,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x21d8c50,0x00000000), stub!
wine: Call from 0x7bc4c220 to unimplemented function GDI32.dll.GdiEntry1, aborting
wine: Unimplemented function GDI32.dll.GdiEntry1 called at address 0x7bc4c220 (thread 0009), starting debugger...
Unhandled exception: unimplemented function GDI32.dll.GdiEntry1 called in 32-bit code (0x7bc4c220).
Register dump:
 CS:0023 SS:002b DS:002b ES:002b FS:0063 GS:006b
 EIP:7bc4c220 ESP:021d8520 EBP:021d8584 EFLAGS:00000202(   - --  I   - - - )
 EAX:003babbe EBX:7bc9cff4 ECX:001243c0 EDX:001243fc
 ESI:021d852c EDI:00000000
Stack dump:
0x021d8520:  0000000b 00000003 f748c252 80000100
0x021d8530:  00000001 00000000 7bc4c220 00000002
0x021d8540:  003babf4 003babbe 00000000 021d8c00
0x021d8550:  7ed20ffa 00000027 00000000 00000000
0x021d8560:  00000000 00000000 00000000 00000000
0x021d8570:  00000000 00000000 00000000 001243f4
Backtrace:
=>0 0x7bc4c220 in ntdll (+0x3c220) (0x021d8584)
  1 0x003f000f (0x021d8de0)
  2 0x0025ae42 in d3d9 (+0x2ae41) (0x021d9194)
  3 0x0025c445 in d3d9 (+0x2c444) (0x021d91bc)
  4 0x00259f35 in d3d9 (+0x29f34) (0x021d93c0)
  5 0x0025a5dd in d3d9 (+0x2a5dc) (0x021d94d8)
  6 0x0162c1c8 in grid (+0x122c1c7) (0x021d951c)
  7 0x0162c608 in grid (+0x122c607) (0x021dab5c)
  8 0x01356447 in grid (+0xf56446) (0x021ef89c)
  9 0x01249c1a in grid (+0xe49c19) (0x021efd44)
  10 0x00000008 (0x015c349d)
  11 0x5d8b5351 (0xec8b55c3)
0x7bc4c220: subl	$4,%esp
Modules:
Module	Address			Debug info	Name (104 modules)
PE	  230000-  3d9000	Export          d3d9
PE	  3e0000-  3e5000	Deferred        d3d8thk
PE	  400000- 1ce4000	Export          grid
PE	 21f0000- 2206000	Deferred        xinput1_3
PE	 2210000- 22be000	Deferred        dinput8
PE	 22c0000- 2677000	Deferred        d3dx9_37
PE	18000000-18033000	Deferred        binkw32
ELF	7b800000-7b97d000	Deferred        kernel32<elf>
  \-PE	7b810000-7b97d000	\               kernel32
ELF	7bc00000-7bcb9000	Export          ntdll<elf>
  \-PE	7bc10000-7bcb9000	\               ntdll
ELF	7bf00000-7bf04000	Deferred        <wine-loader>
ELF	7dcd1000-7dd05000	Deferred        uxtheme<elf>
  \-PE	7dce0000-7dd05000	\               uxtheme
ELF	7dd05000-7dd0a000	Deferred        libgpg-error.so.0
ELF	7dd0a000-7dd43000	Deferred        libdbus-1.so.3
ELF	7dd43000-7ddb6000	Deferred        libgcrypt.so.11
ELF	7ddb6000-7ddc7000	Deferred        libtasn1.so.3
ELF	7ddc7000-7ddcb000	Deferred        libkeyutils.so.1
ELF	7ddcb000-7ddd3000	Deferred        libkrb5support.so.0
ELF	7ddd3000-7ddd7000	Deferred        libcom_err.so.2
ELF	7ddd7000-7ddfb000	Deferred        libk5crypto.so.3
ELF	7ddfb000-7deac000	Deferred        libkrb5.so.3
ELF	7deac000-7debd000	Deferred        libavahi-client.so.3
ELF	7debd000-7dec9000	Deferred        libavahi-common.so.3
ELF	7dec9000-7df64000	Deferred        libgnutls.so.26
ELF	7df64000-7df93000	Deferred        libgssapi_krb5.so.2
ELF	7df93000-7dfda000	Deferred        libcups.so.2
ELF	7dfda000-7dfe4000	Deferred        libxcursor.so.1
ELF	7dfe4000-7dfea000	Deferred        libxfixes.so.3
ELF	7dfea000-7dfee000	Deferred        libxcomposite.so.1
ELF	7dfee000-7dff6000	Deferred        libxrandr.so.2
ELF	7dff6000-7e000000	Deferred        libxrender.so.1
ELF	7e000000-7e006000	Deferred        libxxf86vm.so.1
ELF	7e006000-7e00a000	Deferred        libxinerama.so.1
ELF	7e00a000-7e02c000	Deferred        imm32<elf>
  \-PE	7e010000-7e02c000	\               imm32
ELF	7e02c000-7e032000	Deferred        libxdmcp.so.6
ELF	7e032000-7e036000	Deferred        libxau.so.6
ELF	7e036000-7e050000	Deferred        libxcb.so.1
ELF	7e050000-7e055000	Deferred        libuuid.so.1
ELF	7e055000-7e172000	Deferred        libx11.so.6
ELF	7e172000-7e182000	Deferred        libxext.so.6
ELF	7e182000-7e19b000	Deferred        libice.so.6
ELF	7e19b000-7e1a4000	Deferred        libsm.so.6
ELF	7e1c1000-7e264000	Deferred        winex11<elf>
  \-PE	7e1d0000-7e264000	\               winex11
ELF	7e29c000-7e2c3000	Deferred        libexpat.so.1
ELF	7e2c3000-7e2f3000	Deferred        libfontconfig.so.1
ELF	7e2f3000-7e308000	Deferred        libz.so.1
ELF	7e308000-7e37e000	Deferred        libfreetype.so.6
ELF	7e39b000-7e484000	Deferred        oleaut32<elf>
  \-PE	7e3b0000-7e484000	\               oleaut32
ELF	7e484000-7e56f000	Deferred        comctl32<elf>
  \-PE	7e490000-7e56f000	\               comctl32
ELF	7e56f000-7e5d1000	Deferred        shlwapi<elf>
  \-PE	7e580000-7e5d1000	\               shlwapi
ELF	7e5d1000-7e7ab000	Deferred        shell32<elf>
  \-PE	7e5e0000-7e7ab000	\               shell32
ELF	7e7ab000-7e7e3000	Deferred        winspool<elf>
  \-PE	7e7b0000-7e7e3000	\               winspool
ELF	7e7e3000-7e842000	Deferred        setupapi<elf>
  \-PE	7e7f0000-7e842000	\               setupapi
ELF	7e842000-7e856000	Deferred        libresolv.so.2
ELF	7e856000-7e877000	Deferred        iphlpapi<elf>
  \-PE	7e860000-7e877000	\               iphlpapi
ELF	7e877000-7e8c5000	Deferred        libopenal.so.1
ELF	7e8c7000-7e8e2000	Deferred        wsock32<elf>
  \-PE	7e8d0000-7e8e2000	\               wsock32
ELF	7e8e2000-7e8fd000	Deferred        openal32<elf>
  \-PE	7e8f0000-7e8fd000	\               openal32
ELF	7e8fd000-7e972000	Deferred        rpcrt4<elf>
  \-PE	7e910000-7e972000	\               rpcrt4
ELF	7e972000-7ea72000	Deferred        ole32<elf>
  \-PE	7e990000-7ea72000	\               ole32
ELF	7ea72000-7eaba000	Deferred        dsound<elf>
  \-PE	7ea80000-7eaba000	\               dsound
ELF	7eaba000-7eb4f000	Deferred        winmm<elf>
  \-PE	7eac0000-7eb4f000	\               winmm
ELF	7eb4f000-7eb63000	Deferred        lz32<elf>
  \-PE	7eb50000-7eb63000	\               lz32
ELF	7eb63000-7eb7c000	Deferred        version<elf>
  \-PE	7eb70000-7eb7c000	\               version
ELF	7eb7c000-7ebd7000	Deferred        advapi32<elf>
  \-PE	7eb90000-7ebd7000	\               advapi32
ELF	7ebd7000-7ec63000	Deferred        gdi32<elf>
  \-PE	7ebe0000-7ec63000	\               gdi32
ELF	7ec63000-7ed94000	Deferred        user32<elf>
  \-PE	7ec80000-7ed94000	\               user32
ELF	7ed94000-7ee16000	Deferred        msvcrt<elf>
  \-PE	7edb0000-7ee16000	\               msvcrt
ELF	7ee16000-7ee43000	Deferred        ws2_32<elf>
  \-PE	7ee20000-7ee43000	\               ws2_32
ELF	7efa7000-7efb3000	Deferred        libnss_files.so.2
ELF	7efb3000-7efbd000	Deferred        libnss_nis.so.2
ELF	7efbd000-7efe3000	Deferred        libm.so.6
ELF	7efe9000-7f000000	Deferred        libnsl.so.1
ELF	f7440000-f7448000	Deferred        libnss_compat.so.2
ELF	f7449000-f744d000	Deferred        libdl.so.2
ELF	f744d000-f75a7000	Deferred        libc.so.6
ELF	f75a8000-f75c1000	Deferred        libpthread.so.0
ELF	f75cb000-f75d4000	Deferred        librt.so.1
ELF	f75de000-f771e000	Deferred        libwine.so.1
ELF	f7720000-f773e000	Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
00000008 (D) C:\Program Files\Codemasters\GRID\GRID.exe
	00000009    0 <==
0000000e services.exe
	00000018    0
	00000015    0
	00000014    0
	00000010    0
	0000000f    0
00000011 winedevice.exe
	00000017    0
	00000016    0
	00000013    0
	00000012    0
00000023 explorer.exe
	00000024    0
Backtrace:
=>0 0x7bc4c220 in ntdll (+0x3c220) (0x021d8584)
  1 0x003f000f (0x021d8de0)
  2 0x0025ae42 in d3d9 (+0x2ae41) (0x021d9194)
  3 0x0025c445 in d3d9 (+0x2c444) (0x021d91bc)
  4 0x00259f35 in d3d9 (+0x29f34) (0x021d93c0)
  5 0x0025a5dd in d3d9 (+0x2a5dc) (0x021d94d8)
  6 0x0162c1c8 in grid (+0x122c1c7) (0x021d951c)
  7 0x0162c608 in grid (+0x122c607) (0x021dab5c)
  8 0x01356447 in grid (+0xf56446) (0x021ef89c)
  9 0x01249c1a in grid (+0xe49c19) (0x021efd44)
  10 0x00000008 (0x015c349d)
  11 0x5d8b5351 (0xec8b55c3)
wine: Call from 0x7bc4c220 to unimplemented function GDI32.dll.GdiEntry1, aborting
wine: Call from 0x7bc4c220 to unimplemented function GDI32.dll.GdiEntry1, aborting
user@UbuntuD64Lucid:~$ 


```

---

### Post by shreepads on 2011-01-28
Did a few searches on this error "wine: Unimplemented function GDI32.dll.GdiEntry1" and it looks like its caused as I'm using the native d3d9 and the suggested solution is to use the built-in.

But when I use the built-in one the program crashes with the previously reported page fault error, so looks like the fault is in the wine update.

To test this, I created a new user id, which presumably would come with its own fresh Wine config. 

Installed GRID from DVD as before:

```

guest@UbuntuD64Lucid:/media/GRID$ wine setup.exe

wine: created the configuration directory '/home/guest/.wine'
fixme:system:SetProcessDPIAware stub!
fixme:dwmapi:DwmIsCompositionEnabled 0x33cfdc
fixme:file:MoveFileWithProgressW MOVEFILE_WRITE_THROUGH unimplemented
fixme:advapi:SetNamedSecurityInfoW L"C:\\windows\\system32\\gecko\\1.0.0\\wine_gecko\\components\\xpti.dat" 1 536870916 (nil) (nil) 0x1f24a4 (nil)
fixme:iphlpapi:NotifyAddrChange (Handle 0xa62e8d8, overlapped 0xa62e8e0): stub
fixme:file:MoveFileWithProgressW MOVEFILE_WRITE_THROUGH unimplemented
fixme:advapi:SetNamedSecurityInfoW L"C:\\windows\\system32\\gecko\\1.0.0\\wine_gecko\\components\\compreg.dat" 1 536870916 (nil) (nil) 0x1e5166c (nil)
wine: configuration in '/home/guest/.wine' has been updated.
guest@UbuntuD64Lucid:/media/GRID$ fixme:storage:create_storagefile Storage share mode not implemented.
fixme:mscoree:GetCORVersion (0x325c98, 600, 0x325c84): semi-stub!
fixme:mscoree:LoadLibraryShim (0x2ab31b0 L"fusion.dll", (nil), (nil), 0x3254bc): semi-stub
fixme:mscoree:GetCORVersion (0x323ed4, 600, 0x323ec0): semi-stub!
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
fixme:mscoree:LoadLibraryShim (0x2ab31b0 L"fusion.dll", (nil), (nil), 0x3252fc): semi-stub
fixme:mscoree:GetCORVersion (0x323664, 600, 0x323650): semi-stub!
fixme:mscoree:LoadLibraryShim (0x2ab31b0 L"fusion.dll", (nil), (nil), 0x3252fc): semi-stub
fixme:mscoree:LoadLibraryShim (0x2ab31b0 L"fusion.dll", (nil), (nil), 0x3252fc): semi-stub
fixme:mscoree:LoadLibraryShim (0x2ab31b0 L"fusion.dll", (nil), (nil), 0x3252fc): semi-stub
fixme:mscoree:LoadLibraryShim (0x2ab31b0 L"fusion.dll", (nil), (nil), 0x3252fc): semi-stub
fixme:mscoree:LoadLibraryShim (0x2ab31b0 L"fusion.dll", (nil), (nil), 0x3252fc): semi-stub
fixme:mscoree:LoadLibraryShim (0x2ab31b0 L"fusion.dll", (nil), (nil), 0x3252fc): semi-stub
fixme:mscoree:LoadLibraryShim (0x2ab31b0 L"fusion.dll", (nil), (nil), 0x3252fc): semi-stub
fixme:mscoree:LoadLibraryShim (0x2ab31b0 L"fusion.dll", (nil), (nil), 0x3252fc): semi-stub
fixme:mscoree:LoadLibraryShim (0x2ab31b0 L"fusion.dll", (nil), (nil), 0x3257dc): semi-stub
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
fixme:hnetcfg:fw_app_put_ProcessImageFileName 0x210fa78, L"C:\\Program Files\\Codemasters\\GRID\\GRID.exe"
fixme:hnetcfg:fw_app_put_Name 0x210fa78, L"GRID"
fixme:hnetcfg:fw_apps_Add 0x14063f0, 0x210fa78
err:module:import_dll Library binkw32.dll (which is needed by L"C:\\Program Files\\Codemasters\\GRID\\GRID.exe") not found
err:ole:CoGetClassObject class {9a5ea990-3034-4d6f-9128-01f3c61022bc} not registered
err:ole:CoGetClassObject no class object {9a5ea990-3034-4d6f-9128-01f3c61022bc} could be created for context 0x1
fixme:shdocvw:IEParseDisplayNameWithBCW stub: 0x0 L"http://www.codemasters.com/codem" 0x13dd08 0x325028
fixme:shdocvw:IEParseDisplayNameWithBCW stub: 0x0 L"http://www.racedrivergrid.com" 0x13dd08 0x325028
fixme:shdocvw:IEParseDisplayNameWithBCW stub: 0x0 L"http://www.codemasters.com/cheats" 0x2241d98 0x325028
fixme:shell:IShellLinkA_fnGetPath (0x14060e0): WIN32_FIND_DATA is not yet filled.
fixme:shell:IShellLinkA_fnGetPath (0x14060e0): WIN32_FIND_DATA is not yet filled.
fixme:shell:IShellLinkA_fnGetPath (0x2158478): WIN32_FIND_DATA is not yet filled.
fixme:shell:IShellLinkA_fnGetPath (0x2158478): WIN32_FIND_DATA is not yet filled.
fixme:shell:IShellLinkA_fnGetPath (0x13ddd8): WIN32_FIND_DATA is not yet filled.
fixme:shell:IShellLinkA_fnGetPath (0x13ddd8): WIN32_FIND_DATA is not yet filled.
fixme:shell:IShellLinkA_fnGetPath (0x2216f90): WIN32_FIND_DATA is not yet filled.
fixme:shell:IShellLinkA_fnGetPath (0x2216f90): WIN32_FIND_DATA is not yet filled.
fixme:shdocvw:IEParseDisplayNameWithBCW stub: 0x0 L"http://www.codemasters.com/codem" 0x22170b0 0x325e68
fixme:shell:IShellLinkA_fnGetPath (0x223d6a8): WIN32_FIND_DATA is not yet filled.
fixme:shell:IShellLinkA_fnGetPath (0x223d6a8): WIN32_FIND_DATA is not yet filled.
fixme:shdocvw:IEParseDisplayNameWithBCW stub: 0x0 L"http://www.racedrivergrid.com" 0x13dd70 0x325e68
fixme:shell:IShellLinkA_fnGetPath (0x2216cd0): WIN32_FIND_DATA is not yet filled.
fixme:shell:IShellLinkA_fnGetPath (0x2216cd0): WIN32_FIND_DATA is not yet filled.
fixme:shdocvw:IEParseDisplayNameWithBCW stub: 0x0 L"http://www.codemasters.com/cheats" 0x210e0b8 0x325e68
fixme:shell:IShellLinkA_fnGetPath (0x223d658): WIN32_FIND_DATA is not yet filled.
fixme:shell:IShellLinkA_fnGetPath (0x223d658): WIN32_FIND_DATA is not yet filled.
^C
guest@UbuntuD64Lucid:/media/GRID$ 


```


But I'm back to the page fault error on running it!

```

guest@UbuntuD64Lucid:~$ env WINEPREFIX="/home/guest/.wine" wine C:\\Program\ Files\\Codemasters\\GRID\\GRID.exe 

fixme:ntdll:NtQuerySystemInformation info_class SYSTEM_HANDLE_INFORMATION
fixme:ntdll:NtQueryObject Unsupported information class 3
err:rpc:I_RpcGetBuffer no binding
wine: Unhandled page fault on read access to 0x00000000 at address 0x7e052734 (thread 0009), starting debugger...
Unhandled exception: page fault on read access to 0x00000000 in 32-bit code (0x7e052734).
Register dump:
 CS:0023 SS:002b DS:002b ES:002b FS:0063 GS:006b
 EIP:7e052734 ESP:021d8b10 EBP:021d8d08 EFLAGS:00010246(  R- --  I  Z- -P- )
 EAX:00000000 EBX:7e095ff4 ECX:ffffffff EDX:00000000
 ESI:7e09dfb8 EDI:00000000
Stack dump:
0x021d8b10:  00001f03 03e000ea 7d270678 ffffffff
0x021d8b20:  00000001 00000001 00000000 00000018
0x021d8b30:  00000001 7d1fe408 00002200 021d8b60
0x021d8b40:  00000000 00000000 00000000 7d270678
0x021d8b50:  7d266980 000001ff 03e000ea 00000000
0x021d8b60:  00000002 7bc9cff4 021d8cd8 f767c011
Backtrace:
=>0 0x7e052734 in winex11 (+0x42734) (0x021d8d08)
  1 0x7e055337 X11DRV_wglGetProcAddress+0x26() in winex11 (0x021d8d58)
  2 0x7eb38cc9 wglGetProcAddress+0x68() in gdi32 (0x021d8da8)
  3 0x7ecfe7a3 in wined3d (+0x4e7a2) (0x021d9448)
  4 0x7ed1308a in wined3d (+0x63089) (0x021d9468)
  5 0x7ed9baba WineDirect3DCreate+0x59() in wined3d (0x021d94a8)
  6 0x7ede8d2d Direct3DCreate9+0x5c() in d3d9 (0x021d94d8)
  7 0x0162c1c8 in grid (+0x122c1c7) (0x021d951c)
  8 0x0162c608 in grid (+0x122c607) (0x021dab5c)
  9 0x01356447 in grid (+0xf56446) (0x021ef89c)
  10 0x01249c1a in grid (+0xe49c19) (0x021efd44)
  11 0x00000008 (0x015c349d)
  12 0x5d8b5351 (0xec8b55c3)
0x7e052734: repne scasb	%es:(%edi)
Modules:
Module	Address			Debug info	Name (112 modules)
PE	  230000-  246000	Deferred        xinput1_3
PE	  400000- 1ce4000	Export          grid
PE	 21f0000- 25a7000	Deferred        d3dx9_37
PE	18000000-18033000	Deferred        binkw32
ELF	7a14f000-7b800000	Deferred        libnvidia-glcore.so.260.19.29
ELF	7b800000-7b97d000	Deferred        kernel32<elf>
  \-PE	7b810000-7b97d000	\               kernel32
ELF	7bc00000-7bcb9000	Deferred        ntdll<elf>
  \-PE	7bc10000-7bcb9000	\               ntdll
ELF	7bf00000-7bf04000	Deferred        <wine-loader>
ELF	7d9cf000-7da98000	Deferred        libgl.so.1
ELF	7dad9000-7db0d000	Deferred        uxtheme<elf>
  \-PE	7dae0000-7db0d000	\               uxtheme
ELF	7db0d000-7db12000	Deferred        libgpg-error.so.0
ELF	7db12000-7db4b000	Deferred        libdbus-1.so.3
ELF	7db4b000-7dbbe000	Deferred        libgcrypt.so.11
ELF	7dbbe000-7dbcf000	Deferred        libtasn1.so.3
ELF	7dbcf000-7dbd3000	Deferred        libkeyutils.so.1
ELF	7dbd3000-7dbdb000	Deferred        libkrb5support.so.0
ELF	7dbdb000-7dbdf000	Deferred        libcom_err.so.2
ELF	7dbdf000-7dc03000	Deferred        libk5crypto.so.3
ELF	7dc03000-7dcb4000	Deferred        libkrb5.so.3
ELF	7dcb4000-7dcc5000	Deferred        libavahi-client.so.3
ELF	7dcc5000-7dcd1000	Deferred        libavahi-common.so.3
ELF	7dcd1000-7dd6c000	Deferred        libgnutls.so.26
ELF	7dd6c000-7dd9b000	Deferred        libgssapi_krb5.so.2
ELF	7dd9b000-7dde2000	Deferred        libcups.so.2
ELF	7de15000-7de1f000	Deferred        libxcursor.so.1
ELF	7de1f000-7de25000	Deferred        libxfixes.so.3
ELF	7de25000-7de29000	Deferred        libxcomposite.so.1
ELF	7de29000-7de31000	Deferred        libxrandr.so.2
ELF	7de31000-7de3b000	Deferred        libxrender.so.1
ELF	7de3b000-7de41000	Deferred        libxxf86vm.so.1
ELF	7de41000-7de45000	Deferred        libxinerama.so.1
ELF	7de45000-7de67000	Deferred        imm32<elf>
  \-PE	7de50000-7de67000	\               imm32
ELF	7de67000-7de6d000	Deferred        libxdmcp.so.6
ELF	7de6d000-7de71000	Deferred        libxau.so.6
ELF	7de71000-7de8b000	Deferred        libxcb.so.1
ELF	7de8b000-7de90000	Deferred        libuuid.so.1
ELF	7de90000-7dfad000	Deferred        libx11.so.6
ELF	7dfad000-7dfbd000	Deferred        libxext.so.6
ELF	7dfbd000-7dfd6000	Deferred        libice.so.6
ELF	7dfd6000-7dfdf000	Deferred        libsm.so.6
ELF	7dfdf000-7dfe1000	Deferred        libnvidia-tls.so.260.19.29
ELF	7dffc000-7e09f000	Export          winex11<elf>
  \-PE	7e010000-7e09f000	\               winex11
ELF	7e0df000-7e106000	Deferred        libexpat.so.1
ELF	7e106000-7e136000	Deferred        libfontconfig.so.1
ELF	7e136000-7e14b000	Deferred        libz.so.1
ELF	7e14b000-7e1c1000	Deferred        libfreetype.so.6
ELF	7e1de000-7e1f9000	Deferred        wsock32<elf>
  \-PE	7e1e0000-7e1f9000	\               wsock32
ELF	7e1f9000-7e2e2000	Deferred        oleaut32<elf>
  \-PE	7e210000-7e2e2000	\               oleaut32
ELF	7e2e2000-7e364000	Deferred        msvcrt<elf>
  \-PE	7e2f0000-7e364000	\               msvcrt
ELF	7e364000-7e39d000	Deferred        dinput<elf>
  \-PE	7e370000-7e39d000	\               dinput
ELF	7e39d000-7e488000	Deferred        comctl32<elf>
  \-PE	7e3b0000-7e488000	\               comctl32
ELF	7e488000-7e4ea000	Deferred        shlwapi<elf>
  \-PE	7e4a0000-7e4ea000	\               shlwapi
ELF	7e4ea000-7e6c4000	Deferred        shell32<elf>
  \-PE	7e500000-7e6c4000	\               shell32
ELF	7e6c4000-7e6fc000	Deferred        winspool<elf>
  \-PE	7e6d0000-7e6fc000	\               winspool
ELF	7e6fc000-7e75b000	Deferred        setupapi<elf>
  \-PE	7e710000-7e75b000	\               setupapi
ELF	7e75b000-7e76f000	Deferred        libresolv.so.2
ELF	7e76f000-7e790000	Deferred        iphlpapi<elf>
  \-PE	7e780000-7e790000	\               iphlpapi
ELF	7e790000-7e799000	Deferred        librt.so.1
ELF	7e799000-7e7e7000	Deferred        libopenal.so.1
ELF	7e7e9000-7e804000	Deferred        dinput8<elf>
  \-PE	7e7f0000-7e804000	\               dinput8
ELF	7e804000-7e81f000	Deferred        openal32<elf>
  \-PE	7e810000-7e81f000	\               openal32
ELF	7e81f000-7e833000	Deferred        lz32<elf>
  \-PE	7e820000-7e833000	\               lz32
ELF	7e833000-7e8a8000	Deferred        rpcrt4<elf>
  \-PE	7e840000-7e8a8000	\               rpcrt4
ELF	7e8a8000-7e9a8000	Deferred        ole32<elf>
  \-PE	7e8c0000-7e9a8000	\               ole32
ELF	7e9a8000-7ea3d000	Deferred        winmm<elf>
  \-PE	7e9b0000-7ea3d000	\               winmm
ELF	7ea3d000-7ea85000	Deferred        dsound<elf>
  \-PE	7ea40000-7ea85000	\               dsound
ELF	7ea85000-7eae0000	Deferred        advapi32<elf>
  \-PE	7ea90000-7eae0000	\               advapi32
ELF	7eae0000-7eb6c000	Export          gdi32<elf>
  \-PE	7eaf0000-7eb6c000	\               gdi32
ELF	7eb6c000-7ec9d000	Deferred        user32<elf>
  \-PE	7eb80000-7ec9d000	\               user32
ELF	7ec9d000-7edd5000	Export          wined3d<elf>
  \-PE	7ecb0000-7edd5000	\               wined3d
ELF	7edd5000-7ee09000	Export          d3d9<elf>
  \-PE	7ede0000-7ee09000	\               d3d9
ELF	7ee09000-7ee36000	Deferred        ws2_32<elf>
  \-PE	7ee10000-7ee36000	\               ws2_32
ELF	7ef9a000-7efa6000	Deferred        libnss_files.so.2
ELF	7efa6000-7efbd000	Deferred        libnsl.so.1
ELF	7efbd000-7efe3000	Deferred        libm.so.6
ELF	7efe7000-7f000000	Deferred        version<elf>
  \-PE	7eff0000-7f000000	\               version
ELF	f74d5000-f74df000	Deferred        libnss_nis.so.2
ELF	f74e0000-f74e4000	Deferred        libdl.so.2
ELF	f74e4000-f763e000	Deferred        libc.so.6
ELF	f763f000-f7658000	Deferred        libpthread.so.0
ELF	f7658000-f7660000	Deferred        libnss_compat.so.2
ELF	f7675000-f77b5000	Deferred        libwine.so.1
ELF	f77b7000-f77d5000	Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
00000008 (D) C:\Program Files\Codemasters\GRID\GRID.exe
	00000009    0 <==
0000000e services.exe
	00000018    0
	00000015    0
	00000014    0
	00000010    0
	0000000f    0
00000011 winedevice.exe
	00000017    0
	00000016    0
	00000013    0
	00000012    0
00000023 explorer.exe
	00000024    0
Backtrace:
=>0 0x7e052734 in winex11 (+0x42734) (0x021d8d08)
  1 0x7e055337 X11DRV_wglGetProcAddress+0x26() in winex11 (0x021d8d58)
  2 0x7eb38cc9 wglGetProcAddress+0x68() in gdi32 (0x021d8da8)
  3 0x7ecfe7a3 in wined3d (+0x4e7a2) (0x021d9448)
  4 0x7ed1308a in wined3d (+0x63089) (0x021d9468)
  5 0x7ed9baba WineDirect3DCreate+0x59() in wined3d (0x021d94a8)
  6 0x7ede8d2d Direct3DCreate9+0x5c() in d3d9 (0x021d94d8)
  7 0x0162c1c8 in grid (+0x122c1c7) (0x021d951c)
  8 0x0162c608 in grid (+0x122c607) (0x021dab5c)
  9 0x01356447 in grid (+0xf56446) (0x021ef89c)
  10 0x01249c1a in grid (+0xe49c19) (0x021efd44)
  11 0x00000008 (0x015c349d)
  12 0x5d8b5351 (0xec8b55c3)


```

---

### Post by shreepads on 2011-01-28
One thing, the Sound Test from winecfg is working fine from this setup...

Googling around a bit more found another person who had solved the page fault problem by installing directx9 from winetricks instead of d3dx9

```
guest@UbuntuD64Lucid:~$ sh winetricks

Executing wget -O directx_feb2010_redist.exe -nd -c --read-timeout=300 --retry-connrefused --header Accept-Encoding: gzip,deflate http://download.microsoft.com/download/E/E/1/EE17FF74-6C45-4575-9CF4-7FC2597ACD18/directx_feb2010_redist.exe
--2011-01-29 01:42:39--  http://download.microsoft.com/download/E/E/1/EE17FF74-6C45-4575-9CF4-7FC2597ACD18/directx_feb2010_redist.exe
Resolving download.microsoft.com... 210.212.26.8, 210.212.26.16
Connecting to download.microsoft.com|210.212.26.8|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 109072752 (104M) [application/octet-stream]
Saving to: `directx_feb2010_redist.exe'

100%[=====================================>] 10,90,72,752  146K/s   in 14m 29s =

2011-01-29 01:57:09 (123 KB/s) - `directx_feb2010_redist.exe' saved [109072752/109072752]

You probably shouldn't be using this. It's VERY invasive.
Use 'winetricks d3dx9' instead.
DELETE - HKLM\Software\Microsoft\Windows\CurrentVersion SubVersionNumber 0 0 1
Error: The system was unable to find the specified registry key or value
DELETE - HKLM\Software\Microsoft\Windows\CurrentVersion VersionNumber 0 0 1
Error: The system was unable to find the specified registry key or value
DELETE - HKLM\Software\Microsoft\Windows NT\CurrentVersion CSDVersion 0 0 1
The operation completed successfully
DELETE - HKLM\Software\Microsoft\Windows NT\CurrentVersion CurrentBuildNumber 0 0 1
The operation completed successfully
DELETE - HKLM\Software\Microsoft\Windows NT\CurrentVersion CurrentVersion 0 0 1
The operation completed successfully
DELETE - HKLM\System\CurrentControlSet\Control\ProductOptions ProductType 0 0 1
The operation completed successfully
DELETE - HKLM\System\CurrentControlSet\Control\ServiceCurrent OS 0 0 1
Error: The system was unable to find the specified registry key or value
DELETE - HKLM\System\CurrentControlSet\Control\Windows CSDVersion 0 0 1
The operation completed successfully
DELETE - HKCU\Software\Wine Version 0 0 1
Error: The system was unable to find the specified registry key or value
Setting Windows version to win2k
Executing early_wine regedit c:\winetrickstmp\set-winver.reg
Executing wine /home/guest/.cache/winetricks/directx_feb2010_redist.exe /t:c:\winetrickstmp
fixme:advapi:DecryptFileA "c:\\winetrickstmp\\" 00000000
Using native override for following DLLs: d3dim d3drm d3dx8 d3dx9_24 d3dx9_25 d3dx9_26 d3dx9_27 d3dx9_28 d3dx9_29
Executing early_wine regedit c:\winetrickstmp\override-dll.reg
Using native override for following DLLs: d3dx9_30 d3dx9_31 d3dx9_32 d3dx9_33 d3dx9_34 d3dx9_35 d3dx9_36 d3dx9_37
Executing early_wine regedit c:\winetrickstmp\override-dll.reg
Using native override for following DLLs: d3dx9_38 d3dx9_39 d3dx9_40 d3dx9_41 d3dx9_42 d3dxof
Executing early_wine regedit c:\winetrickstmp\override-dll.reg
Using native override for following DLLs: dciman32 ddrawex devenum dmband dmcompos dmime dmloader dmscript dmstyle
Executing early_wine regedit c:\winetrickstmp\override-dll.reg
Using native override for following DLLs: dmsynth dmusic dmusic32 dnsapi dplay dplayx dpnaddr dpnet dpnhpast dpnlobby
Executing early_wine regedit c:\winetrickstmp\override-dll.reg
Using native override for following DLLs: dswave dxdiagn mscoree msdmo qcap quartz streamci
Executing early_wine regedit c:\winetrickstmp\override-dll.reg
Using native override for following DLLs: dxdiag.exe
Executing early_wine regedit c:\winetrickstmp\override-dll.reg
Using builtin override for following DLLs: d3d8 d3d9 dinput dinput8 dsound
Executing early_wine regedit c:\winetrickstmp\override-dll.reg
Executing wine c:\winetrickstmp/DXSETUP.exe
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
DELETE - HKLM\Software\Microsoft\Windows\CurrentVersion SubVersionNumber 0 0 1
Error: The system was unable to find the specified registry key or value
err:rundll32:wWinMain Unable to load L"streamci"
err:rundll32:wWinMain Unable to load L"streamci"
err:rundll32:wWinMain Unable to load L"streamci"
err:rundll32:wWinMain Unable to load L"streamci"
err:rundll32:wWinMain Unable to load L"streamci"
err:rundll32:wWinMain Unable to load L"streamci"
err:rundll32:wWinMain Unable to load L"streamci"
err:rundll32:wWinMain Unable to load L"streamci"
err:rundll32:wWinMain Unable to load L"streamci"
DELETE - HKLM\Software\Microsoft\Windows\CurrentVersion VersionNumber 0 0 1
Error: The system was unable to find the specified registry key or value
DELETE - HKLM\Software\Microsoft\Windows NT\CurrentVersion CSDVersion 0 0 1
The operation completed successfully
DELETE - HKLM\Software\Microsoft\Windows NT\CurrentVersion CurrentBuildNumber 0 0 1
The operation completed successfully
DELETE - HKLM\Software\Microsoft\Windows NT\CurrentVersion CurrentVersion 0 0 1
The operation completed successfully
DELETE - HKLM\System\CurrentControlSet\Control\ProductOptions ProductType 0 0 1
Error: The system was unable to find the specified registry key or value
DELETE - HKLM\System\CurrentControlSet\Control\ServiceCurrent OS 0 0 1
Error: The system was unable to find the specified registry key or value
DELETE - HKLM\System\CurrentControlSet\Control\Windows CSDVersion 0 0 1
The operation completed successfully
DELETE - HKCU\Software\Wine Version 0 0 1
Error: The system was unable to find the specified registry key or value
Setting Windows version to winxp
Executing early_wine regedit c:\winetrickstmp\set-winver.reg
Using builtin,native override for following DLLs: mscoree
Executing early_wine regedit c:\winetrickstmp\override-dll.reg
Install of directx9 done
You gave the --optin option, so reporting 'directx9' to the winetricks maintainer so he knows which winetricks verbs get used and which don't.  Use --optout to disable future reports.
winetricks done.
guest@UbuntuD64Lucid:~$ 

```

Now I get a slightly different error message re 32-bit code..

```

guest@UbuntuD64Lucid:~$ env WINEPREFIX="/home/guest/.wine" wine C:\\Program\ Files\\Codemasters\\GRID\\GRID.exe 

fixme:ntdll:NtQuerySystemInformation info_class SYSTEM_HANDLE_INFORMATION
fixme:ntdll:NtQueryObject Unsupported information class 3
err:rpc:I_RpcGetBuffer no binding
wine: Unhandled page fault on read access to 0x00000000 at address 0x7e05c734 (thread 0009), starting debugger...
Unhandled exception: page fault on read access to 0x00000000 in 32-bit code (0x7e05c734).
Register dump:
 CS:0023 SS:002b DS:002b ES:002b FS:0063 GS:006b
 EIP:7e05c734 ESP:021d8b10 EBP:021d8d08 EFLAGS:00010246(  R- --  I  Z- -P- )
 EAX:00000000 EBX:7e09fff4 ECX:ffffffff EDX:00000000
 ESI:7e0a7fb8 EDI:00000000
Stack dump:
0x021d8b10:  00001f03 048000ea 7d4af660 ffffffff
0x021d8b20:  00000001 00000001 00000000 00000018
0x021d8b30:  00000001 7d43d3f0 00002200 021d8b60
0x021d8b40:  00000000 00000000 00000000 7d4af660
0x021d8b50:  7d4a5968 000001ff 048000ea 00000000
0x021d8b60:  00000002 7bc9cff4 021d8cd8 f7686011
Backtrace:
=>0 0x7e05c734 in winex11 (+0x4c734) (0x021d8d08)
  1 0x7e05f337 X11DRV_wglGetProcAddress+0x26() in winex11 (0x021d8d58)
  2 0x7eb45cc9 wglGetProcAddress+0x68() in gdi32 (0x021d8da8)
  3 0x7ed0b7a3 in wined3d (+0x5b7a2) (0x021d9448)
  4 0x7ed2008a in wined3d (+0x70089) (0x021d9468)
  5 0x7eda8aba WineDirect3DCreate+0x59() in wined3d (0x021d94a8)
  6 0x7edf5d2d Direct3DCreate9+0x5c() in d3d9 (0x021d94d8)
  7 0x0162c1c8 in grid (+0x122c1c7) (0x021d951c)
  8 0x0162c608 in grid (+0x122c607) (0x021dab5c)
  9 0x01356447 in grid (+0xf56446) (0x021ef89c)
  10 0x01249c1a in grid (+0xe49c19) (0x021efd44)
  11 0x00000008 (0x015c349d)
  12 0x5d8b5351 (0xec8b55c3)
0x7e05c734: repne scasb	%es:(%edi)
Modules:
Module	Address			Debug info	Name (112 modules)
PE	  230000-  246000	Deferred        xinput1_3
PE	  400000- 1ce4000	Export          grid
PE	 21f0000- 25a7000	Deferred        d3dx9_37
PE	18000000-18033000	Deferred        binkw32
ELF	7a14f000-7b800000	Deferred        libnvidia-glcore.so.260.19.29
ELF	7b800000-7b97d000	Deferred        kernel32<elf>
  \-PE	7b810000-7b97d000	\               kernel32
ELF	7bc00000-7bcb9000	Deferred        ntdll<elf>
  \-PE	7bc10000-7bcb9000	\               ntdll
ELF	7bf00000-7bf04000	Deferred        <wine-loader>
ELF	7d9d9000-7daa2000	Deferred        libgl.so.1
ELF	7dae3000-7db17000	Deferred        uxtheme<elf>
  \-PE	7daf0000-7db17000	\               uxtheme
ELF	7db17000-7db1c000	Deferred        libgpg-error.so.0
ELF	7db1c000-7db55000	Deferred        libdbus-1.so.3
ELF	7db55000-7dbc8000	Deferred        libgcrypt.so.11
ELF	7dbc8000-7dbd9000	Deferred        libtasn1.so.3
ELF	7dbd9000-7dbdd000	Deferred        libkeyutils.so.1
ELF	7dbdd000-7dbe5000	Deferred        libkrb5support.so.0
ELF	7dbe5000-7dbe9000	Deferred        libcom_err.so.2
ELF	7dbe9000-7dc0d000	Deferred        libk5crypto.so.3
ELF	7dc0d000-7dcbe000	Deferred        libkrb5.so.3
ELF	7dcbe000-7dccf000	Deferred        libavahi-client.so.3
ELF	7dccf000-7dcdb000	Deferred        libavahi-common.so.3
ELF	7dcdb000-7dd76000	Deferred        libgnutls.so.26
ELF	7dd76000-7dda5000	Deferred        libgssapi_krb5.so.2
ELF	7dda5000-7ddec000	Deferred        libcups.so.2
ELF	7de1f000-7de29000	Deferred        libxcursor.so.1
ELF	7de29000-7de2f000	Deferred        libxfixes.so.3
ELF	7de2f000-7de33000	Deferred        libxcomposite.so.1
ELF	7de33000-7de3b000	Deferred        libxrandr.so.2
ELF	7de3b000-7de45000	Deferred        libxrender.so.1
ELF	7de45000-7de4b000	Deferred        libxxf86vm.so.1
ELF	7de4b000-7de4f000	Deferred        libxinerama.so.1
ELF	7de4f000-7de71000	Deferred        imm32<elf>
  \-PE	7de60000-7de71000	\               imm32
ELF	7de71000-7de77000	Deferred        libxdmcp.so.6
ELF	7de77000-7de7b000	Deferred        libxau.so.6
ELF	7de7b000-7de95000	Deferred        libxcb.so.1
ELF	7de95000-7de9a000	Deferred        libuuid.so.1
ELF	7de9a000-7dfb7000	Deferred        libx11.so.6
ELF	7dfb7000-7dfc7000	Deferred        libxext.so.6
ELF	7dfc7000-7dfe0000	Deferred        libice.so.6
ELF	7dfe0000-7dfe9000	Deferred        libsm.so.6
ELF	7dfe9000-7dfeb000	Deferred        libnvidia-tls.so.260.19.29
ELF	7e006000-7e0a9000	Export          winex11<elf>
  \-PE	7e010000-7e0a9000	\               winex11
ELF	7e0dc000-7e103000	Deferred        libexpat.so.1
ELF	7e103000-7e133000	Deferred        libfontconfig.so.1
ELF	7e133000-7e148000	Deferred        libz.so.1
ELF	7e148000-7e1be000	Deferred        libfreetype.so.6
ELF	7e1db000-7e1f6000	Deferred        wsock32<elf>
  \-PE	7e1e0000-7e1f6000	\               wsock32
ELF	7e1f6000-7e2df000	Deferred        oleaut32<elf>
  \-PE	7e210000-7e2df000	\               oleaut32
ELF	7e2df000-7e361000	Deferred        msvcrt<elf>
  \-PE	7e2f0000-7e361000	\               msvcrt
ELF	7e361000-7e39a000	Deferred        dinput<elf>
  \-PE	7e370000-7e39a000	\               dinput
ELF	7e39a000-7e485000	Deferred        comctl32<elf>
  \-PE	7e3a0000-7e485000	\               comctl32
ELF	7e485000-7e4e7000	Deferred        shlwapi<elf>
  \-PE	7e490000-7e4e7000	\               shlwapi
ELF	7e4e7000-7e6c1000	Deferred        shell32<elf>
  \-PE	7e500000-7e6c1000	\               shell32
ELF	7e6c1000-7e6f9000	Deferred        winspool<elf>
  \-PE	7e6d0000-7e6f9000	\               winspool
ELF	7e6f9000-7e758000	Deferred        setupapi<elf>
  \-PE	7e700000-7e758000	\               setupapi
ELF	7e758000-7e76c000	Deferred        libresolv.so.2
ELF	7e76c000-7e78d000	Deferred        iphlpapi<elf>
  \-PE	7e770000-7e78d000	\               iphlpapi
ELF	7e78d000-7e7db000	Deferred        libopenal.so.1
ELF	7e7dd000-7e7f8000	Deferred        dinput8<elf>
  \-PE	7e7e0000-7e7f8000	\               dinput8
ELF	7e7f8000-7e813000	Deferred        openal32<elf>
  \-PE	7e800000-7e813000	\               openal32
ELF	7e813000-7e827000	Deferred        lz32<elf>
  \-PE	7e820000-7e827000	\               lz32
ELF	7e827000-7e840000	Deferred        version<elf>
  \-PE	7e830000-7e840000	\               version
ELF	7e840000-7e8b5000	Deferred        rpcrt4<elf>
  \-PE	7e850000-7e8b5000	\               rpcrt4
ELF	7e8b5000-7e9b5000	Deferred        ole32<elf>
  \-PE	7e8d0000-7e9b5000	\               ole32
ELF	7e9b5000-7ea4a000	Deferred        winmm<elf>
  \-PE	7e9c0000-7ea4a000	\               winmm
ELF	7ea4a000-7ea92000	Deferred        dsound<elf>
  \-PE	7ea50000-7ea92000	\               dsound
ELF	7ea92000-7eaed000	Deferred        advapi32<elf>
  \-PE	7eaa0000-7eaed000	\               advapi32
ELF	7eaed000-7eb79000	Export          gdi32<elf>
  \-PE	7eb00000-7eb79000	\               gdi32
ELF	7eb79000-7ecaa000	Deferred        user32<elf>
  \-PE	7eb90000-7ecaa000	\               user32
ELF	7ecaa000-7ede2000	Export          wined3d<elf>
  \-PE	7ecb0000-7ede2000	\               wined3d
ELF	7ede2000-7ee16000	Export          d3d9<elf>
  \-PE	7edf0000-7ee16000	\               d3d9
ELF	7ee16000-7ee43000	Deferred        ws2_32<elf>
  \-PE	7ee20000-7ee43000	\               ws2_32
ELF	7efa7000-7efb3000	Deferred        libnss_files.so.2
ELF	7efb3000-7efbd000	Deferred        libnss_nis.so.2
ELF	7efbd000-7efe3000	Deferred        libm.so.6
ELF	7efe9000-7f000000	Deferred        libnsl.so.1
ELF	f74e1000-f74e9000	Deferred        libnss_compat.so.2
ELF	f74ea000-f74ee000	Deferred        libdl.so.2
ELF	f74ee000-f7648000	Deferred        libc.so.6
ELF	f7649000-f7662000	Deferred        libpthread.so.0
ELF	f766c000-f7675000	Deferred        librt.so.1
ELF	f767f000-f77bf000	Deferred        libwine.so.1
ELF	f77c1000-f77df000	Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
00000008 (D) C:\Program Files\Codemasters\GRID\GRID.exe
	00000009    0 <==
0000000e services.exe
	00000019    0
	00000015    0
	00000014    0
	00000010    0
	0000000f    0
00000011 winedevice.exe
	00000017    0
	00000016    0
	00000013    0
	00000012    0
00000023 explorer.exe
	00000024    0
Backtrace:
=>0 0x7e05c734 in winex11 (+0x4c734) (0x021d8d08)
  1 0x7e05f337 X11DRV_wglGetProcAddress+0x26() in winex11 (0x021d8d58)
  2 0x7eb45cc9 wglGetProcAddress+0x68() in gdi32 (0x021d8da8)
  3 0x7ed0b7a3 in wined3d (+0x5b7a2) (0x021d9448)
  4 0x7ed2008a in wined3d (+0x70089) (0x021d9468)
  5 0x7eda8aba WineDirect3DCreate+0x59() in wined3d (0x021d94a8)
  6 0x7edf5d2d Direct3DCreate9+0x5c() in d3d9 (0x021d94d8)
  7 0x0162c1c8 in grid (+0x122c1c7) (0x021d951c)
  8 0x0162c608 in grid (+0x122c607) (0x021dab5c)
  9 0x01356447 in grid (+0xf56446) (0x021ef89c)
  10 0x01249c1a in grid (+0xe49c19) (0x021efd44)
  11 0x00000008 (0x015c349d)
  12 0x5d8b5351 (0xec8b55c3)

guest@UbuntuD64Lucid:~$ 


```

---

### Post by shreepads on 2011-01-28
Tried changing library overrides for dxd9, dinput,dinput8 to native, but no luck....

Can only conclude that I shouldn't have applied the damned wine update...:(

---

### Post by Halzen on 2011-01-28
Sounds like it, yeah. I'd do an apt-purge (or mark for complete removal in Synaptic) to get rid of Wine, then reinstall the stable version and take another crack at it. If you're having sound errors, you might give something other than PulseAudio a crack.

---

### Post by shreepads on 2011-01-29
> **Halzen said:**
> Sounds like it, yeah. I'd do an apt-purge (or mark for complete removal in Synaptic) to get rid of Wine, then reinstall the stable version and take another crack at it. If you're having sound errors, you might give something other than PulseAudio a crack.

Hmm the problem is that I think I AM on the stable version the upgrade was a dot release to the stable version (from 1.2 to 1.2.2). From the synaptic log, highlighted in **bold**:

```

Commit Log for Wed Jan 26 12:03:09 2011


Upgraded the following packages:
at (3.1.11-1ubuntu5) to 3.1.11-1ubuntu5.1
bsdutils (1:2.17.2-0ubuntu1) to 1:2.17.2-0ubuntu1.10.04.1
fuse-utils (2.8.1-1.1ubuntu2.1) to 2.8.1-1.1ubuntu2.2
hpijs (3.10.2-2ubuntu2.1) to 3.10.2-2ubuntu2.2
hplip (3.10.2-2ubuntu2.1) to 3.10.2-2ubuntu2.2
hplip-data (3.10.2-2ubuntu2.1) to 3.10.2-2ubuntu2.2
libblkid1 (2.17.2-0ubuntu1) to 2.17.2-0ubuntu1.10.04.1
libfuse2 (2.8.1-1.1ubuntu2.1) to 2.8.1-1.1ubuntu2.2
libhpmud0 (3.10.2-2ubuntu2.1) to 3.10.2-2ubuntu2.2
liblircclient-dev (0.8.6-0ubuntu4.1) to 0.8.6-0ubuntu4.2
liblircclient0 (0.8.6-0ubuntu4.1) to 0.8.6-0ubuntu4.2
libuuid1 (2.17.2-0ubuntu1) to 2.17.2-0ubuntu1.10.04.1
libvlc2 (1.0.6-1ubuntu1.3) to 1.0.6-1ubuntu1.4
libvlccore2 (1.0.6-1ubuntu1.3) to 1.0.6-1ubuntu1.4
linux-firmware (1.34.1) to 1.34.3
media-player-info (6-1) to 12-1~lucid1
mount (2.17.2-0ubuntu1) to 2.17.2-0ubuntu1.10.04.1
openssh-client (1:5.3p1-3ubuntu4) to 1:5.3p1-3ubuntu5
ssh-askpass-gnome (1:5.3p1-3ubuntu4) to 1:5.3p1-3ubuntu5
sudo (1.7.2p1-1ubuntu5.2) to 1.7.2p1-1ubuntu5.3
tomboy (1.2.1-0ubuntu1) to 1.2.2-0ubuntu1
ttf-mscorefonts-installer (3.2) to 3.2ubuntu0.1
ttf-symbol-replacement (1.2-0ubuntu6~lucid5) to 1.2.2-0ubuntu2~lucid1
util-linux (2.17.2-0ubuntu1) to 2.17.2-0ubuntu1.10.04.1
uuid-runtime (2.17.2-0ubuntu1) to 2.17.2-0ubuntu1.10.04.1
vlc (1.0.6-1ubuntu1.3) to 1.0.6-1ubuntu1.4
vlc-data (1.0.6-1ubuntu1.3) to 1.0.6-1ubuntu1.4
vlc-nox (1.0.6-1ubuntu1.3) to 1.0.6-1ubuntu1.4
vlc-plugin-pulse (1.0.6-1ubuntu1.3) to 1.0.6-1ubuntu1.4
**wine1.2 (1.2-0ubuntu6~lucid5) to 1.2.2-0ubuntu2~lucid1**
xserver-common (2:1.7.6-2ubuntu7.4) to 2:1.7.6-2ubuntu7.5
xserver-xorg-core (2:1.7.6-2ubuntu7.4) to 2:1.7.6-2ubuntu7.5

Installed the following packages:
ttf-droid (1.00~b112+dfsg+1-0ubuntu1)
ttf-umefont (411-1)


```

So even if I was to purge and reinstall I would be back to this version and presumably the same problem. 

In Synaptic -> wine1.2 -> Properties -> Versions, the following are listed (attached screenshot)
- 1.2.2
- 1.1.42

So I'm not sure how to go back to wine1.2

---

### Post by shreepads on 2011-01-29
Filed a bug report:

[https://bugs.launchpad.net/ubuntu/+source/wine1.2/+bug/709660](https://bugs.launchpad.net/ubuntu/+source/wine1.2/+bug/709660)

---

### Post by shreepads on 2011-02-01
OK now I feel really stupid...

Fixed by a couple of simple updates..

a. Update Manager upgraded the kernel from 2.6.32-27-generic to 2.6.32-28-generic. On restart, as expected, the NVidia proprietary drivers weren't working.

b. So instead of re-using the driver file I already had (version 260.19.29) I installed the latest one (260.19.36)

Now both Commandos 2 and Racedriver GRID are working perfectly fine. Tweaked registry and DLL overrides as before to get Racedriver up to speed again..

Question is what fixed the problem the kernel update or the NVidia driver update? Rest of the updates via Update Manager seemed unrelated (apparmor etc)

---

### Post by Halzen on 2011-02-01
Well, you went from one outdated generic kernel to another, so I probably wouldn't give that too much credit (in comparision, I'm using Liquorix's 2.6.37 kernel, so 2.6.32 is definitely old news). I'd probably give the nod to the new Nvidia driver - every now and then, some serious optimizations get thrown into the changelog. Good to hear things are looking up.

---

