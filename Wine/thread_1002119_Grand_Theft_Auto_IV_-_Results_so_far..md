---
title: "Grand Theft Auto IV - Results so far."
date: 2008-12-04
forum: Wine
---

### Post by hikaricore on 2008-12-04
I ripped the contents of my discs to a local drive just to make things simpler.
Tho when the 2nd disc was needed I had to enter a path, but it accepted the same path
that I'd been using with no problems.  Installation completed all the way through including
the Games for ***dows Live crap which shocked me.  After installing a few more files the
Release Date Check popped up and has been sitting at 30% for the last 10 minutes.
Having gotten tired of looking at it I clicked cancel and was able to finish the installation dialog.

So it seems the game can be installed and that's all I know so far.
I'll be testing a few things and reporting back good/bad luck.
Anyone who has any input on this title is welcome to join in.

[COLOR="DarkRed"]Please do not use this thread to discuss piracy or cracks![/COLOR]

Well it seems the release date check constantly does nothing and sits at 30%.
So I've improvised a little in my attempt at making progress, this we will not discuss.

Moving right along on first run of **wine LaunchGTAIV.exe** from the install directory I get several DLL errors:

> err:module:import_dll Library **MSVCR90.dll** (which is needed by L"C:\\windows\\system32\\xlive.dll") not found
err:module:import_dll Library **MSASN1.dll** (which is needed by L"C:\\windows\\system32\\xlive.dll") not found
err:module:import_dll Library **MSVCP90.dll** (which is needed by L"C:\\windows\\system32\\xlive.dll") not found
err:module:import_dll Library **xlive.dll** (which is needed by L"F:\\GTA4\\Grand Theft Auto IV\\GTAIV.exe") not found
err:module:import_dll Library **WMASF.DLL** (which is needed by L"F:\\GTA4\\Grand Theft Auto IV\\WMVCore.DLL") not found
err:module:import_dll Library **WMVCore.DLL** (which is needed by L"F:\\GTA4\\Grand Theft Auto IV\\GTAIV.exe") not found


I downloaded each of these libraries having mostly no clue if I'm even using the correct version and to be on the safe side
found the copy of xlive.dll in my ~/.wine/drive_c/windows/system32 directory and copied it to the game dir.  No clue why it's
not being noticed in the system dir, but whatever.  After adding the needed dlls I test the launcher again.. still no dice:

> err:module:attach_process_dlls **"MSVCR90.dll"** failed to initialize, aborting
[img]http://img.photobucket.com/albums/v414/hikari_corgan/doh.png[/img]
Possibly I'm using the wrong version?  *shrug*  I also get something real finally.. an error dialog >.<  lol.

Due to the random libraries I grabbed, the tinkering I've done, and the "improvisation" there's no telling if this little
roadblock is normal at this point or more likely if I have caused it.

[COLOR="DarkGreen"]Don't get me wrong I don't expect this game to even run for a long time, but I figured it couldn't hurt to play around and test.[/COLOR]

---

### Post by roland.b on 2008-12-05
Maybe install directx 10 to wine would work?

---

### Post by hikaricore on 2008-12-05
No.

---

### Post by Disparition on 2008-12-05
Cedega will probably support it.

---

### Post by solitaire on 2008-12-05
I'd be surprised if even GTA IV will work with Cedega... Since even PC users can't get it to install properly!! There are LOADS of people having isues with the PC version of GTA IV 

[http://www.1up.com/do/newsStory?cId=3171648](http://www.1up.com/do/newsStory?cId=3171648)
[http://games.slashdot.org/article.pl?sid=08/12/05/0840238](http://games.slashdot.org/article.pl?sid=08/12/05/0840238)

---

### Post by forest.r on 2008-12-07
Maybe installation through steam would work? Although I wouldn't get my hopes up.
Also, never install DirectX on WINE, it comes with it's own version that breaks if you install over it.

---

### Post by Allochtoon on 2008-12-10
> **solitaire said:**
> I'd be surprised if even GTA IV will work with Cedega... Since even PC users can't get it to install properly!! There are LOADS of people having isues with the PC version of GTA IV 

[http://www.1up.com/do/newsStory?cId=3171648](http://www.1up.com/do/newsStory?cId=3171648)
[http://games.slashdot.org/article.pl?sid=08/12/05/0840238](http://games.slashdot.org/article.pl?sid=08/12/05/0840238)

lol surprise surprise.


thread subscribed.

---

### Post by -siGGi- on 2008-12-15
after experementing a little i got this:
```
siggi@desktop:~/.wine/drive_c/Programme/Rockstar Games/Grand Theft Auto IV$ wine LaunchGTAIV.exe
fixme:powrprof:DllMain (0x7e1a0000, 1, 0x1) not fully implemented
fixme:advapi:RegisterTraceGuidsA 0x1a90faa (nil) 0x19c5864 3 0x1fe673c (null) (null) 0x1ff47d8
fixme:advapi:LookupAccountNameW (null) L"siggi" (nil) 0x33f608 (nil) 0x33f600 0x33f5f0 - stub
fixme:advapi:LookupAccountNameW (null) L"siggi" 0x147168 0x33f608 0x144a10 0x33f600 0x33f5f0 - stub
fixme:advapi:RegisterEventSourceW ((null),L"XLive"): stub
fixme:advapi:ReportEventW (0xcafe4242,0x0002,0x0000,0x80000002,(nil),0x0004,0x00000000,0x33e75c,(nil)): stub
fixme:advapi:DeregisterEventSource (0xcafe4242) stub
wine: Call from 0x7b8456b0 to unimplemented function advapi32.dll.UnregisterTraceGuids, aborting
wine: Unimplemented function advapi32.dll.UnregisterTraceGuids called at address 0x7b8456b0 (thread 001b), starting debugger...
Unhandled exception: unimplemented function advapi32.dll.UnregisterTraceGuids called in 32-bit code (0x7b845723).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:7b845723 ESP:0033f76c EBP:0033f7d0 EFLAGS:00000246(   - 00      - IZP1)
 EAX:7b82f005 EBX:7b8b7ff4 ECX:00000000 EDX:0033f7f8
 ESI:0033f7f8 EDI:80004005
Stack dump:
0x0033f76c:  0033f7f8 00000008 0000003c 80000100
0x0033f77c:  00000001 00000000 7b8456b0 00000002
0x0033f78c:  7ec71ae0 7ec71e39 00000000 00000000
0x0033f79c:  00000000 00000000 00000000 00000000
0x0033f7ac:  00000000 00000000 00000000 002c0031
0x0033f7bc:  00300020 0020002c 7b8456ba 00000000
Backtrace:
=>1 0x7b845723 in kernel32 (+0x25723) (0x0033f7d0)
  2 0x7ec71a45 in advapi32 (+0x31a45) (0x0033f800)
  3 0x7ec43d6c in advapi32 (+0x3d6c) (0x0033fcc8)
  4 0x01fd3a9e in xlive (+0x613a9e) (0x0033fcd8)
  5 0x005864a4 in gtaiv (+0x1864a4) (0x0033ff08)
  6 0x7b878c28 in kernel32 (+0x58c28) (0x0033ffe8)
  7 0xb7dc6d37 wine_switch_to_stack+0x17() in libwine.so.1 (0x00000000)
0x7b845723: subl	$4,%esp
Modules:
Module	Address			Debug info	Name (135 modules)
PE	  350000-  366000	Deferred        xinput1_3
PE	  400000- 19b5000	Export          gtaiv
PE	 19c0000- 2764000	Export          xlive
PE	 2770000- 2b27000	Deferred        d3dx9_37
PE	11c70000-11caa000	Deferred        wmasf
PE	15110000-1536c000	Deferred        wmvcore
PE	18000000-18039000	Deferred        binkw32
PE	27500000-2760d000	Deferred        msidcrl40
PE	77af0000-77b02000	Deferred        msasn1
PE	78480000-7850d000	Deferred        msvcp90
PE	78520000-785c3000	Deferred        msvcr90
ELF	7b800000-7b940000	Export          kernel32<elf>
  \-PE	7b820000-7b940000	\               kernel32
ELF	7bc00000-7bcac000	Deferred        ntdll<elf>
  \-PE	7bc10000-7bcac000	\               ntdll
ELF	7bf00000-7bf04000	Deferred        <wine-loader>
PE	7c630000-7c64b000	Deferred        atl80
ELF	7dae6000-7daf5000	Deferred        libgcc_s.so.1
ELF	7daf5000-7db5e000	Deferred        libgcrypt.so.11
ELF	7db5e000-7db70000	Deferred        libtasn1.so.3
ELF	7db70000-7dc0d000	Deferred        libgnutls.so.26
ELF	7dc22000-7dc4b000	Deferred        msacm32<elf>
  \-PE	7dc30000-7dc4b000	\               msacm32
ELF	7dc4b000-7dc64000	Deferred        msacm32<elf>
  \-PE	7dc50000-7dc64000	\               msacm32
ELF	7dc64000-7dcb4000	Deferred        libpulse.so.0
ELF	7dcb4000-7dcc9000	Deferred        midimap<elf>
  \-PE	7dcc0000-7dcc9000	\               midimap
ELF	7dcc9000-7dcd2000	Deferred        librt.so.1
ELF	7dcd2000-7dd9a000	Deferred        libasound.so.2
ELF	7dda4000-7dda8000	Deferred        libgpg-error.so.0
ELF	7dda8000-7ddaf000	Deferred        libasound_module_pcm_pulse.so
ELF	7ddaf000-7dde6000	Deferred        winealsa<elf>
  \-PE	7ddc0000-7dde6000	\               winealsa
ELF	7de13000-7de17000	Deferred        libcap.so.1
ELF	7de2a000-7de5d000	Deferred        uxtheme<elf>
  \-PE	7de30000-7de5d000	\               uxtheme
ELF	7de5d000-7de66000	Deferred        libxcursor.so.1
ELF	7de66000-7de6b000	Deferred        libxfixes.so.3
ELF	7de6b000-7de6f000	Deferred        libxcomposite.so.1
ELF	7de6f000-7de76000	Deferred        libxrandr.so.2



ELF	7de76000-7de80000	Deferred        libxrender.so.1
ELF	7de80000-7de86000	Deferred        libxxf86vm.so.1
ELF	7de86000-7de89000	Deferred        libxinerama.so.1
ELF	7de89000-7de8e000	Deferred        libxdmcp.so.6
ELF	7de8e000-7dea7000	Deferred        libxcb.so.1
ELF	7dea7000-7deaa000	Deferred        libxcb-xlib.so.0
ELF	7deaa000-7dead000	Deferred        libxau.so.6
ELF	7dead000-7df9c000	Deferred        libx11.so.6
ELF	7df9c000-7dfab000	Deferred        libxext.so.6
ELF	7dfab000-7dfc3000	Deferred        libice.so.6
ELF	7dfc3000-7dfcc000	Deferred        libsm.so.6
ELF	7dfe1000-7e07d000	Deferred        winex11<elf>
  \-PE	7dff0000-7e07d000	\               winex11
ELF	7e0a2000-7e0c9000	Deferred        libexpat.so.1
ELF	7e0c9000-7e0f6000	Deferred        libfontconfig.so.1
ELF	7e0f6000-7e10c000	Deferred        libz.so.1
ELF	7e10c000-7e182000	Deferred        libfreetype.so.6
ELF	7e197000-7e1ad000	Deferred        powrprof<elf>
  \-PE	7e1a0000-7e1ad000	\               powrprof
ELF	7e1ad000-7e1e5000	Deferred        dinput<elf>
  \-PE	7e1c0000-7e1e5000	\               dinput
ELF	7e1e5000-7e1ff000	Deferred        dinput8<elf>
  \-PE	7e1f0000-7e1ff000	\               dinput8
ELF	7e1ff000-7e320000	Deferred        wined3d<elf>
  \-PE	7e210000-7e320000	\               wined3d
ELF	7e320000-7e351000	Deferred        d3d9<elf>
  \-PE	7e330000-7e351000	\               d3d9
ELF	7e351000-7e39d000	Deferred        dsound<elf>
  \-PE	7e360000-7e39d000	\               dsound
ELF	7e39d000-7e3b1000	Deferred        sensapi<elf>
  \-PE	7e3a0000-7e3b1000	\               sensapi
ELF	7e3b1000-7e3c7000	Deferred        oleacc<elf>
  \-PE	7e3c0000-7e3c7000	\               oleacc
ELF	7e3c7000-7e431000	Deferred        setupapi<elf>
  \-PE	7e3d0000-7e431000	\               setupapi
ELF	7e431000-7e49e000	Deferred        msvcrt<elf>
  \-PE	7e440000-7e49e000	\               msvcrt
ELF	7e49e000-7e4bf000	Deferred        imm32<elf>
  \-PE	7e4a0000-7e4bf000	\               imm32
ELF	7e4bf000-7e5ab000	Deferred        oleaut32<elf>
  \-PE	7e4e0000-7e5ab000	\               oleaut32
ELF	7e5ab000-7e612000	Deferred        rpcrt4<elf>
  \-PE	7e5c0000-7e612000	\               rpcrt4
ELF	7e612000-7e723000	Deferred        ole32<elf>
  \-PE	7e630000-7e723000	\               ole32
ELF	7e723000-7e746000	Deferred        winhttp<elf>
  \-PE	7e730000-7e746000	\               winhttp
ELF	7e746000-7e761000	Deferred        version<elf>
  \-PE	7e750000-7e761000	\               version
ELF	7e761000-7e78e000	Deferred        ws2_32<elf>
  \-PE	7e770000-7e78e000	\               ws2_32
ELF	7e78e000-7e7a2000	Deferred        libresolv.so.2
ELF	7e7a2000-7e7c2000	Deferred        iphlpapi<elf>
  \-PE	7e7b0000-7e7c2000	\               iphlpapi
ELF	7e7c2000-7e7e9000	Deferred        netapi32<elf>
  \-PE	7e7d0000-7e7e9000	\               netapi32
ELF	7e7e9000-7e813000	Deferred        secur32<elf>
  \-PE	7e7f0000-7e813000	\               secur32
ELF	7e813000-7e840000	Deferred        wintrust<elf>
  \-PE	7e820000-7e840000	\               wintrust
ELF	7e840000-7e8d4000	Deferred        winmm<elf>
  \-PE	7e850000-7e8d4000	\               winmm
ELF	7e8d4000-7e99b000	Deferred        comctl32<elf>
  \-PE	7e8e0000-7e99b000	\               comctl32
ELF	7e99b000-7eac6000	Deferred        shell32<elf>
  \-PE	7e9b0000-7eac6000	\               shell32
ELF	7eac6000-7eb23000	Deferred        shlwapi<elf>
  \-PE	7ead0000-7eb23000	\               shlwapi
ELF	7eb23000-7eb46000	Deferred        mpr<elf>
  \-PE	7eb30000-7eb46000	\               mpr
ELF	7eb46000-7eb97000	Deferred        wininet<elf>
  \-PE	7eb50000-7eb97000	\               wininet
ELF	7eb97000-7ec15000	Deferred        crypt32<elf>
  \-PE	7eba0000-7ec15000	\               crypt32
ELF	7ec15000-7ec2b000	Deferred        psapi<elf>
  \-PE	7ec20000-7ec2b000	\               psapi
ELF	7ec2b000-7ec80000	Export          advapi32<elf>
  \-PE	7ec40000-7ec80000	\               advapi32
ELF	7ec80000-7ed20000	Deferred        gdi32<elf>
  \-PE	7ec90000-7ed20000	\               gdi32
ELF	7ed20000-7ee6e000	Deferred        user32<elf>
  \-PE	7ed40000-7ee6e000	\               user32
ELF	7ee6e000-7ee87000	Deferred        libnsl.so.1
ELF	7ee87000-7ee90000	Deferred        libnss_compat.so.2
ELF	7ee90000-7eea5000	Deferred        lz32<elf>
  \-PE	7eea0000-7eea5000	\               lz32
ELF	7efc5000-7efeb000	Deferred        libm.so.6
ELF	7eff4000-7f000000	Deferred        libnss_files.so.2
ELF	b7c22000-b7c2d000	Deferred        libnss_nis.so.2
ELF	b7c2e000-b7c32000	Deferred        libdl.so.2
ELF	b7c32000-b7d90000	Deferred        libc.so.6
ELF	b7d91000-b7daa000	Deferred        libpthread.so.0
ELF	b7dbf000-b7ef6000	Export          libwine.so.1
ELF	b7ef8000-b7f15000	Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
00000008 
	00000019    0
	00000018    0
	00000009    0
0000000c 
	00000013    0
	00000012    0
	0000000e    0
	0000000d    0
0000000f 
	00000015    0
	00000014    0
	00000011    0
	00000010    0
00000016 
	00000017    0
0000001a (D) C:\Programme\Rockstar Games\Grand Theft Auto IV\GTAIV.exe
	0000001b    0 <==
Backtrace:
=>1 0x7b845723 in kernel32 (+0x25723) (0x0033f7d0)
  2 0x7ec71a45 in advapi32 (+0x31a45) (0x0033f800)
  3 0x7ec43d6c in advapi32 (+0x3d6c) (0x0033fcc8)
  4 0x01fd3a9e in xlive (+0x613a9e) (0x0033fcd8)
  5 0x005864a4 in gtaiv (+0x1864a4) (0x0033ff08)
  6 0x7b878c28 in kernel32 (+0x58c28) (0x0033ffe8)
  7 0xb7dc6d37 wine_switch_to_stack+0x17() in libwine.so.1 (0x00000000)
wine: Call from 0x7b8456b0 to unimplemented function advapi32.dll.UpdateTraceA, aborting
fixme:powrprof:DllMain (0x7e1a0000, 0, 0x1) not fully implemented

```

this is when i launch in win 2000 mode if i launch in win xp mode it tells this error:
[IMG]http://i37.tinypic.com/zxwa39.jpg[/IMG]

this has somehting to do with Service Pack 3.

Rockstar Games Social Club is not launching because of .Net Framework 3 (not installable)

---

### Post by vhozard on 2008-12-16
I had the same error on another game (Warhammer Soulstorm) and installing M$ Visual bla bla bla solved it:
```
wget www.kegel.com/wine/winetricks && sh winetricks vcrun2005 && sh winetricks vcrun2005sp1
```

[[COLOR="DarkRed"]Here can the link[/COLOR]]("http://appdb.winehq.org/commentview.php?iAppId=1918&iVersionId=10571&iThreadId=34936") be found to WineHQ of Soulstorm-fix.

Greets Vhozard,

PS This is the fix for the first error on this thread

---

### Post by hikaricore on 2008-12-16
I'll test this out when I get home and see if it makes any difference. ^_^:p

---

### Post by hikaricore on 2008-12-16
Well I wouldn't call it progress so much as a different outcome...

Starting from scratch today, I installed the following via winetricks (which I'd never used before):

```

vcrun2005
vcrun2005sp1
vcrun2008

```

Grabbed the following dll files:
[http://www.tweaksforgeeks.com/files/msasn1.dll](http://www.tweaksforgeeks.com/files/msasn1.dll)
[http://www.dlldump.com/dllfiles/W/wmvcore.dll](http://www.dlldump.com/dllfiles/W/wmvcore.dll)
[http://www.dlldump.com/dllfiles/W/wmidx.dll](http://www.dlldump.com/dllfiles/W/wmidx.dll)
[http://www.dlldump.com/dllfiles/W/wmasf.dll](http://www.dlldump.com/dllfiles/W/wmasf.dll)
[http://www.dlldump.com/dllfiles/D/drmclien.dll](http://www.dlldump.com/dllfiles/D/drmclien.dll)

Now that I'm past the vcr90 dll error I get:

> err:module:attach_process_dlls "ATL80.DLL" failed to initialize, aborting

[IMG]http://img.photobucket.com/albums/v414/hikari_corgan/meh1.png[/IMG]

We've a long road ahead of us folks :p

---

### Post by mememe on 2008-12-18
Hm, that doesn't look good. I was thinking about buying that game but I wouldn't play it anywhere else than in Wine..
What's the progress so far?

---

### Post by free-martin on 2008-12-19
Hey Guys,

even if it seems to be a hard job, I think it is a nice idea to make it possible running GTA 4 on Linux. 
One of the biggest problems seems to be this DirectX-issue to me, I think you can fix that dll-stuff ;-)

Maybe this link(german language) can give you more information about getting around. 
[http://www.gtavision.com/index.php?section=downloads&site=download&id=1113](http://www.gtavision.com/index.php?section=downloads&site=download&id=1113)

They created a deb-package, which somehow installs GTA SA and makes it playable. It does not use DirectX. It is not very well documented, but maybe you can contact the developer using this link:
[http://gtaubuntu.gt.funpic.de/?page_id=12](http://gtaubuntu.gt.funpic.de/?page_id=12)

Anyhow, keep it up
Greets
Martin

---

### Post by hikaricore on 2008-12-19
martin... GTA SA works just fine for me.... I don't see how that's relevant.

The problem with GTA4 is not DirectX, at least not completely...

As for the progress it's still pretty much the same.

---

### Post by Shaythong on 2009-01-18
Hey hikaricore, doesn't GTA IV run on SM3.0? But WINE supports only SM2.0 is that right? :confused:

---

### Post by albertz on 2009-01-21
Hi there,

I am using Gentoo myself, but I think that probably doesn't matter that much here.

Atm, I am also stuck with the missing Manifest problem but that is not really related to GTA4 and should be fixable somehow, there are a lot of possitive reports about similar problems with missing manifests and also successfull workarounds.

Just for reference, I tried wine-1.1.11, wine-1.1.13, cedega-6.0.2 and cedega-6.1. I used cedega for the installation and trying to get a correct installation of the MSVC*-stuff with wine right now.

When I called the VC80 setup last, I have an output similar to:

> az@acompneu ~/.cedega/GTA4/drive_c/Program Files/Rockstar Games/Grand Theft Auto IV $ wine GTAIV.exe
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC80.CRT"
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC90.CRT"
err:module:import_dll Library MSVCR90.dll (which is needed by L"C:\\Program Files\\Rockstar Games\\Grand Theft Auto IV\\xlive.dll") not found
err:module:import_dll Library MSVCP90.dll (which is needed by L"C:\\Program Files\\Rockstar Games\\Grand Theft Auto IV\\xlive.dll") not found
err:module:import_dll Library xlive.dll (which is needed by L"C:\\Program Files\\Rockstar Games\\Grand Theft Auto IV\\GTAIV.exe") not found
err:module:LdrInitializeThunk Main exe initialization for L"C:\\Program Files\\Rockstar Games\\Grand Theft Auto IV\\GTAIV.exe" failed, status c0000135


The VC80 setup doesn't really seem to work. It first asks me for licence agreement but just quits after. I get this on console:
> az@acompneu /mnt/tmp/GTAIV/Redistributable $ wine vcredist_x86.exe 
fixme:advapi:DecryptFileA "C:\\windows\\temp\\IXP000.TMP\\" 00000000
fixme:advapi:DecryptFileA "C:\\windows\\temp\\IXP001.TMP\\" 00000000
fixme:advapi:LookupAccountNameW (null) L"az" (nil) 0x33f77c (nil) 0x33f780 0x33f774 - stub
fixme:advapi:LookupAccountNameW (null) L"az" 0x131558 0x33f77c 0x12d4b8 0x33f780 0x33f774 - stub
fixme:msi:ACTION_HandleStandardAction unhandled standard action L"SetODBCFolders"
fixme:msi:msi_unimplemented_action_stub RemoveExistingProducts -> 1 ignored L"Upgrade" table values
fixme:msi:msi_unimplemented_action_stub MsiUnpublishAssemblies -> 10 ignored L"MsiAssembly" table values
fixme:mscoree:LoadLibraryShim (0x7ec166ac L"fusion.dll", (nil), (nil), 0x33f868): semi-stub


Even worse, it seems that the VC80 setup has deleted all my manifests:
> az@acompneu ~/.cedega/GTA4 $ ls drive_c/windows/winsxs/manifests/
x86_microsoft.windows.common-controls_6595b64144ccf1df_6.0.2600.2982_none_deadbeef.manifest


The VC90 setup (via winetricks) seems to work though (if you set the OS to WinXP). After running it, I have all the correct manifest files for VC90:
> az@acompneu ~/.cedega/GTA4 $ ls drive_c/windows/winsxs/manifests/
x86_Microsoft.VC90.ATL_1fc8b3b9a1e18e3b_9.0.21022.8_x-ww_312cf0e9.cat
x86_Microsoft.VC90.ATL_1fc8b3b9a1e18e3b_9.0.21022.8_x-ww_312cf0e9.manifest
x86_Microsoft.VC90.CRT_1fc8b3b9a1e18e3b_9.0.21022.8_x-ww_d08d0375.cat
x86_Microsoft.VC90.CRT_1fc8b3b9a1e18e3b_9.0.21022.8_x-ww_d08d0375.manifest
x86_Microsoft.VC90.MFC_1fc8b3b9a1e18e3b_9.0.21022.8_x-ww_a173767a.cat
x86_Microsoft.VC90.MFC_1fc8b3b9a1e18e3b_9.0.21022.8_x-ww_a173767a.manifest
x86_Microsoft.VC90.MFCLOC_1fc8b3b9a1e18e3b_9.0.21022.8_x-ww_11f3ea3a.cat
x86_Microsoft.VC90.MFCLOC_1fc8b3b9a1e18e3b_9.0.21022.8_x-ww_11f3ea3a.manifest
x86_Microsoft.VC90.OpenMP_1fc8b3b9a1e18e3b_9.0.21022.8_x-ww_ecc42bd1.cat
x86_Microsoft.VC90.OpenMP_1fc8b3b9a1e18e3b_9.0.21022.8_x-ww_ecc42bd1.manifest
x86_microsoft.windows.common-controls_6595b64144ccf1df_6.0.2600.2982_none_deadbeef.manifest


With VC90 correctly installed, I only get the VC80 error:
> az@acompneu ~/.cedega/GTA4/drive_c/Program Files/Rockstar Games/Grand Theft Auto IV $ wine GTAIV.exe
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC80.CRT"
fixme:powrprof:DllMain (0x7dfc0000, 1, 0x1) not fully implemented
err:module:attach_process_dlls "ATL80.DLL" failed to initialize, aborting
err:module:LdrInitializeThunk Main exe initialization for L"C:\\Program Files\\Rockstar Games\\Grand Theft Auto IV\\GTAIV.exe" failed, status c0000142


I really think that this VC80 setup problem could be overcome somehow. But after that, there are probably some more problems.

There is already a bug filled in in the Wine-bugtracker about GTA4:
[http://bugs.winehq.org/show_bug.cgi?id=16328](http://bugs.winehq.org/show_bug.cgi?id=16328)

Some patches were already made in current Git. You'll also find a xlive dummy wrapper there (as a replacement for Xlive). The latest reported problem is something with DirectX, so perhaps I have some luck with Cedega there.

I'll report back after some more process.

- Albert

---

### Post by albertz on 2009-01-21
Ok, I had success in getting VC80 correctly installed by forcing mscoree to native (in winecfg). Then while using Win2000, it installed successfully (at least the manifest files where there):

> az@acompneu /mnt/tmp/GTAIV/Redistributable $ wine vcredist_x86.exe 
fixme:advapi:DecryptFileA "C:\\windows\\temp\\IXP000.TMP\\" 00000000
fixme:advapi:DecryptFileA "C:\\windows\\temp\\IXP001.TMP\\" 00000000
fixme:advapi:LookupAccountNameW (null) L"az" (nil) 0x33f77c (nil) 0x33f780 0x33f774 - stub
fixme:advapi:LookupAccountNameW (null) L"az" 0x1314e8 0x33f77c 0x12d448 0x33f780 0x33f774 - stub
fixme:msi:ACTION_HandleStandardAction unhandled standard action L"SetODBCFolders"
fixme:msi:msi_unimplemented_action_stub RemoveExistingProducts -> 1 ignored L"Upgrade" table values
fixme:msi:msi_unimplemented_action_stub MsiUnpublishAssemblies -> 10 ignored L"MsiAssembly" table values
err:msi:ITERATE_Actions Execution halted, action L"InstallFinalize" returned 1627
err:msi:ITERATE_Actions Execution halted, action L"ExecuteAction" returned 1627


> az@acompneu ~/.cedega/GTA4 $ ls drive_c/windows/winsxs/manifests/
x86_Microsoft.VC80.ATL_1fc8b3b9a1e18e3b_8.0.50727.762_x-ww_cbb27474.cat
x86_Microsoft.VC80.ATL_1fc8b3b9a1e18e3b_8.0.50727.762_x-ww_cbb27474.manifest
x86_Microsoft.VC80.CRT_1fc8b3b9a1e18e3b_8.0.50727.762_x-ww_6b128700.cat
x86_Microsoft.VC80.CRT_1fc8b3b9a1e18e3b_8.0.50727.762_x-ww_6b128700.manifest
x86_Microsoft.VC80.MFC_1fc8b3b9a1e18e3b_8.0.50727.762_x-ww_3bf8fa05.cat
x86_Microsoft.VC80.MFC_1fc8b3b9a1e18e3b_8.0.50727.762_x-ww_3bf8fa05.manifest
x86_Microsoft.VC80.MFCLOC_1fc8b3b9a1e18e3b_8.0.50727.762_x-ww_91481303.cat
x86_Microsoft.VC80.MFCLOC_1fc8b3b9a1e18e3b_8.0.50727.762_x-ww_91481303.manifest
x86_Microsoft.VC80.OpenMP_1fc8b3b9a1e18e3b_8.0.50727.762_x-ww_6c18549a.cat
x86_Microsoft.VC80.OpenMP_1fc8b3b9a1e18e3b_8.0.50727.762_x-ww_6c18549a.manifest
x86_microsoft.windows.common-controls_6595b64144ccf1df_6.0.2600.2982_none_deadbeef.manifest


---

### Post by albertz on 2009-01-21
Running GTA4 failed now with an mscoree.dll error:
> az@acompneu ~/.cedega/GTA4/drive_c/Program Files/Rockstar Games/Grand Theft Auto IV $ wine GTAIV.exe
fixme:powrprof:DllMain (0x7e070000, 1, 0x1) not fully implemented
fixme:dsalsa:IDsDriverBufferImpl_SetVolumePan (0x147100,0x147018): stub
err:module:import_dll Library mscoree.dll (which is needed by L"C:\\Program Files\\Rockstar Games\\Rockstar Games Social Club\\RGSCLauncher.exe") not found
err:module:LdrInitializeThunk Main exe initialization for L"C:\\Program Files\\Rockstar Games\\Rockstar Games Social Club\\RGSCLauncher.exe" failed, status c0000135
fixme:powrprof:DllMain (0x7e070000, 0, 0x1) not fully implemented


But setting mscoree back to builtin solved also this. Now I was getting this error:
> az@acompneu ~/.cedega/GTA4/drive_c/Program Files/Rockstar Games/Grand Theft Auto IV $ wine GTAIV.exe
fixme:powrprof:DllMain (0x7e090000, 1, 0x1) not fully implemented
fixme:dsalsa:IDsDriverBufferImpl_SetVolumePan (0x147100,0x147018): stub
fixme:powrprof:DllMain (0x7e090000, 0, 0x1) not fully implemented
install the Windows version of Mono to run .NET executables


Setting the Windows version back to WinXP gives me this:
> az@acompneu ~/.cedega/GTA4/drive_c/Program Files/Rockstar Games/Grand Theft Auto IV $ wine GTAIV.exe
fixme:powrprof:DllMain (0x7e080000, 1, 0x1) not fully implemented
fixme:powrprof:DllMain (0x7e080000, 0, 0x1) not fully implemented


And a window popping up says "GTA IV FATAL ERROR: RMN40".

---

### Post by albertz on 2009-01-21
> **albertz said:**
> Running GTA4 failed now with an mscoree.dll error:


But setting mscoree back to builtin solved also this. Now I was getting this error:


Setting the Windows version back to WinXP gives me this:


And a window popping up says "GTA IV FATAL ERROR: RMN40".

Oh, interesting: If I use Windows Vista, I get this: "GTA IV FATAL ERROR: RMN20"

---

### Post by albertz on 2009-01-21
Ok, all these messages are saying that it wants a higher service pack. For example RMN40 means, it requires SP3 on WinXP to run.

All error codes are described here:
[http://www.rockstargames.com/support/gta4pc/GTAIV_Error_Codes_ALL_EN.html](http://www.rockstargames.com/support/gta4pc/GTAIV_Error_Codes_ALL_EN.html)

So, how can I make it think that I have service pack 3?

---

### Post by Allochtoon on 2009-01-22
> **albertz said:**
> Ok, all these messages are saying that it wants a higher service pack. For example RMN40 means, it requires SP3 on WinXP to run.

All error codes are described here:
[http://www.rockstargames.com/support/gta4pc/GTAIV_Error_Codes_ALL_EN.html](http://www.rockstargames.com/support/gta4pc/GTAIV_Error_Codes_ALL_EN.html)

So, how can I make it think that I have service pack 3?

Install it with wine?:p

---

### Post by delfick on 2009-01-22
> **albertz said:**
> Ok, all these messages are saying that it wants a higher service pack. For example RMN40 means, it requires SP3 on WinXP to run.

All error codes are described here:
[http://www.rockstargames.com/support/gta4pc/GTAIV_Error_Codes_ALL_EN.html](http://www.rockstargames.com/support/gta4pc/GTAIV_Error_Codes_ALL_EN.html)

So, how can I make it think that I have service pack 3?

try the third post here [http://www.gtaforums.com/index.php?showtopic=380258](http://www.gtaforums.com/index.php?showtopic=380258)

it worked for me when I installed gta4 on my version of windows server 2003

(as a uni student I can download that for free, and I didn't want to actually buy windows :p)

Though if the suggested numbers don't work, try these ones :

Major Version : 6
Minor Version : 1
Build number : 3790
Service pack major : 3
Service pack minor : 1
Suite mask : 0
Product type : 0
CSD version : leave blank

assuming of course that appverifier even works in wine :p

---

### Post by hikaricore on 2009-01-22
I don't think trying to install a windows service pack under WINE is going to do much more than make a mess or at very best not work.

---

### Post by Allochtoon on 2009-01-24
> **hikaricore said:**
> I don't think trying to install a windows service pack under WINE is going to do much more than make a mess or at very best not work.

i know, but that is what gta4 has to think.

---

### Post by veaudaux on 2009-02-03
Any new developments?

*TLDR: I really hope so.*

I'm currently on an older WinXP machine with an OEM license. I've been planning for several months to build a new machine, and it's getting close to time. I preordered GTA IV through Steam back in November, because I was hoping by the time I was ready to build my Ubuntu box, some brave souls would have already pioneered the way to get it working (that, and it came with a free copy of Vice City).

So, since GTA IV was the catalyst for building a new machine in the first place, I'm kinda disappointed that it looks like I'm going to have to buy another Windows license to be able to play (I've said for years that when Linux installation got as friendly as Windows installation, I'd never buy another copy of Windows - Ubuntu definitely got us well beyond that mark, but it looks like GTA's gonna make a liar out of me).

---

### Post by albertz on 2009-02-04
Some more information can be found here: [http://bugs.winehq.org/show_bug.cgi?id=16328](http://bugs.winehq.org/show_bug.cgi?id=16328)

You can fake a SP3 by doing that:

Change value "CSDVersion" in
"HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\Windows".

The default value is 0x00000200 (I think for SP2), set it to 0x00000300 (for SP3).

Anyway, I have other problems now with Rockstar Games Social Club, it crashes always for me. And GTA4 is then complaining that it is not running (or it tries to run it itself which does not work).

---

### Post by Colo2 on 2009-02-22
Any further success? :D I am also very interested in getting GTA IV working in wine or cedega. This would allow me to ditch Windows all together :D

Thanks

Tom

---

### Post by albertz on 2009-02-22
One of the major problems are currently to get Rockstar Games Social Club to work. That is hard because it requires .NET3 which currently does not work with Wine.

If somebody knows a way to overcome RGSC, that would be nice to read.

The game itself seems to have some problems with DirectX but there are good chances that these problems will be fixed in near future. (Or to be more clear: The problems are not yet implemented functions in DirectX, so somebody has to implement those, just a matter of time and work.)

---

### Post by Colo2 on 2009-02-22
Well, I will keep checking back :) Im afraid I can't help much as Im about as useless as a dried up stick.

good luck! :D


Tom

---

### Post by Colo2 on 2009-03-01
Maybe Im just a fool, but is this any use???

[http://ubuntuforums.org/showthread.php?p=6784693](http://ubuntuforums.org/showthread.php?p=6784693)

---

### Post by albertz on 2009-03-01
> **Colo2 said:**
> Maybe Im just a fool, but is this any use???

[http://ubuntuforums.org/showthread.php?p=6784693](http://ubuntuforums.org/showthread.php?p=6784693)

I tried also using winetricks but at least RGSC exited with some .Net error, so I guess it's a problem with .Net.

The best and easiest way would be if we just find out a way to start GTA4 without RGSC because we don't need .Net for GTA4 itself.

---

### Post by garrettc134 on 2009-03-16
How would you use that to get it to install with 2003 x64?

---

### Post by Agent.Logic_ on 2009-03-17
> **albertz said:**
> I tried also using winetricks but at least RGSC exited with some .Net error, so I guess it's a problem with .Net.

The best and easiest way would be if we just find out a way to start GTA4 without RGSC because we don't need .Net for GTA4 itself.

I guess bypassing RGSC would be as good as cracking, if you look at it in the abstract. So I think we can safely say that we are down to either bypassing RGSC or waiting for .NET 3.0 support in WINE. :( VBox/VMware is out of the question, the game barely gets 30 FPS on my 2.5 ghz "overclocked" dual core!

---

### Post by albertz on 2009-03-17
> **Agent.Logic_ said:**
> I guess bypassing RGSC would be as good as cracking, if you look at it in the abstract. So I think we can safely say that we are down to either bypassing RGSC or waiting for .NET 3.0 support in WINE. :( VBox/VMware is out of the question, the game barely gets 30 FPS on my 2.5 ghz "overclocked" dual core!

At least in Germany, there is no problem in bypassing such a problem by cracking if you cannot make it work otherwise.

Also, if one would just think a bit natural/logical, I don't see why there should be a problem in cracking if you cannot make it work otherwise.

Whereby I haven't found any crack for bypassing RGSC. If I would have some more time, I could perhaps try to hack that myself and provide a patch here.

---

### Post by Ice799 on 2009-03-18
Could always try to install it from a ***dows OS on another drive install it to  user/home/ and copy over the dlls and make regs.  just a thought

---

### Post by hikaricore on 2009-03-18
Personally I had no trouble installing it so copying it over is a moot point.
The game will not run thus far.

---

### Post by Agent.Logic_ on 2009-03-18
> **albertz said:**
> At least in Germany, there is no problem in bypassing such a problem by cracking if you cannot make it work otherwise.

Also, if one would just think a bit natural/logical, I don't see why there should be a problem in cracking if you cannot make it work otherwise.

Whereby I haven't found any crack for bypassing RGSC. If I would have some more time, I could perhaps try to hack that myself and provide a patch here.

I completely agree with your take on thinking about it logically, but not everyone wants to be logical mate. ;)

I'm still somewhat a newbie to programming, but from what I know, RGSC is bundled with the game, so it mustn't be that hard to fool GTA IV into thinking that RGSC is running, so that it will launch.

---

### Post by steevz on 2009-04-29
There is a crack out now for the 1.03 patch of GTA IV that bypasses RGSC. Maybe someone should try that out.

I might when I get the patience to install GTA IV on Linux.

steevz

---

### Post by omax on 2009-05-03
I've also been trying to get this to work without success.

So far I get this error:
```
err:module:attach_process_dlls "ATL80.DLL" failed to initialize, aborting
```

Anyone else found a solution?

---

### Post by HavocXphere on 2009-05-03
It was a performance disaster on Windows, so I wouldn't hold my breath for WINE. People with monster PCs are getting lag. Although patch 1.03 apparently makes it more bearable.

Graphics are worse than Crysis and yet it runs slower than Crysis. That takes some doing.:confused:

Those wishing to run it under linux might have more luck if they replace the paul.dll file with a version from elsewhere.;-) Not that I've got it working under *nix...but I suspect that that file is the source of various issues.

---

### Post by veaudaux on 2009-05-03
> **HavocXphere said:**
> It was a performance disaster on Windows, so I wouldn't hold my breath for WINE. People with monster PCs are getting lag. Although patch 1.03 apparently makes it more bearable.

Graphics are worse than Crysis and yet it runs slower than Crysis. That takes some doing.:confused:

This is a misconception. I preordered, and have had the game since launch. The day it came out, it ran (play-ably, but not enjoyably in firefights, etc) on my single core 3ghz with 1 GB RAM and an NVIDIA 8400GS.

On a box I built for under $600 (2.4ghz Kentsfield Quad, 4GB RAM, single NVIDIA 9800GT - no SLI here) it runs flawlessly, and has since before any of the patches.

It doesn't take a "monster PC" at all.

---

### Post by omax on 2009-05-04
> **veaudaux said:**
> This is a misconception. I preordered, and have had the game since launch. The day it came out, it ran (play-ably, but not enjoyably in firefights, etc) on my single core 3ghz with 1 GB RAM and an NVIDIA 8400GS.

On a box I built for under $600 (2.4ghz Kentsfield Quad, 4GB RAM, single NVIDIA 9800GT - no SLI here) it runs flawlessly, and has since before any of the patches.

It doesn't take a "monster PC" at all.

I would have to disagree. AFAIK GTA IV is a port from PS3, and not code optimized at all. It requires a lot from your computer, in my case; just to load it takes 1.3Gb of RAM. That's a vast amount of memory, for non-raytraced graphics.

---

### Post by Colo2 on 2009-06-04
This has not been tried. But if I have understood right... GTA IV will only launch if RGSC.exe is running? Running as a process? Can't we spoof a process?? Like, Run some other .exe in wine, but re-name it to RGSC.exe. Is it checking for the process or something else?

If not, there must be some sort of crack to bypass RGSC.exe 

-.- The moment this is worked out, i can finally ditch windows for good.

---

### Post by hikaricore on 2009-06-04
> **Colo2 said:**
> This has not been tried. But if I have understood right... GTA IV will only launch if RGSC.exe is running? Running as a process? Can't we spoof a process?? Like, Run some other .exe in wine, but re-name it to RGSC.exe. Is it checking for the process or something else?

If not, there must be some sort of crack to bypass RGSC.exe 

-.- The moment this is worked out, i can finally ditch windows for good.

You mean until GTA V comes out and refuses to run on anything but genuine Windows 7.. lol

---

### Post by Dark Aspect on 2009-06-05
> **Colo2 said:**
> -.- The moment this is worked out, i can finally ditch windows for good.

> **hikaricore said:**
> You mean until GTA V comes out and refuses to run on anything but genuine Windows 7.. lol

GTA IV isn't even that great of a game, I would rather have Dead space running and better support for left4dead and cod5. By the way, on GTAIV I got this, which I believe is a rather early error that you can get past to another error:

```
gtaiv.exe failed, status c0000135

```

---

### Post by lukeozade on 2009-06-05
Left4Dead runs fine under wine, GTA IV i sjust need to patience to do get past the Disc Two check.

---

### Post by Dark Aspect on 2009-06-05
> **lukeozade said:**
> Left4Dead runs fine under wine.

I get a consistent frame rate on windows vista of all things with high settings. I have to turn everything off too get Left4dead half way playable under wine. Simply because the game loads under wine doesn't mean wine fully supports it, speed is a factor too.

---

### Post by Colo2 on 2009-06-06
GTA IV is going to be an abolute nightmare under Wine isn't it :( 2FPS

---

### Post by hikaricore on 2009-06-06
> **Colo2 said:**
> GTA IV is going to be an abolute nightmare under Wine isn't it :( 2FPS

If anyone could get it running at 2fps 6 months after release I'd be amazed.  :p

---

### Post by lukeozade on 2009-06-12
DarkApspect: Left 4 Dead is perfectly playable on my Kubuntu box, have played many games (campaign, 16 player versus ect), no problems there. Tested under wine 1.0.1 - 1.2.1 - 1.2.2 and 1.2.3.

Grand theft auto still does not get good fps on my old windows install either, it's a nightmare and a half. Seeing this work under wine would be amazing, literally.

---

### Post by Agent.Logic_ on 2009-06-12
> **lukeozade said:**
> DarkApspect: Left 4 Dead is perfectly playable on my Kubuntu box, have played many games (campaign, 16 player versus ect), no problems there. Tested under wine 1.0.1 - 1.2.1 - 1.2.2 and 1.2.3.

Grand theft auto still does not get good fps on my old windows install either, it's a nightmare and a half. Seeing this work under wine would be amazing, literally.
I think the FPS could be a per-computer issue rather than a general issue. I get a fairly decent FPS on a core2duo 2.2ghz machine with 2GB memory. If someone could reverse engineer the RGSC program in an older .NET version that runs on wine, it could work. Atleast, *some* progress could be made beyond just the installation of GTA IV on linux.

---

### Post by Colo2 on 2009-07-19
ANY NEWS on when the new .net framework will be included in wine?

---

### Post by tghe-retford on 2010-01-09
There has been some progress finally to get GTA IV to work with Wine. Someone has managed to get the game to run in windowed mode, with some graphical problems, and it will only use one CPU core, but its progress:

Bug report: [http://bugs.winehq.org/show_bug.cgi?id=16328](http://bugs.winehq.org/show_bug.cgi?id=16328)
Screenshots: [http://appdb.winehq.org/screenshots.php?iAppId=8757&iVersionId=](http://appdb.winehq.org/screenshots.php?iAppId=8757&iVersionId=)

Might try myself later once the radio programme I am currently listening to is over at 23:00 (UK time).

P.S. Requires Wine source to be patched with the latest patch in the bug report to work.

---

### Post by hikaricore on 2010-01-10
That's fantastic news!

---

