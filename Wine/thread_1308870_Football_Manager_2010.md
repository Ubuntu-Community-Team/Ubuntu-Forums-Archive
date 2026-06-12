---
title: "Football Manager 2010"
date: 2009-11-01
forum: Wine
---

### Post by moujik on 2009-11-01
Hello manager!

I've managed to install an iso version of full 2010 (multi). It requires no validation if you play with DVD. But somehow wine doesn't seem to see a drive I've created as DVD-rom and asks to insert the disc on start up.

Progress so far:

wine 1.1.14 at least (I tried wine 1.1.31) is needed to be able to run setup. winecfg to Windows2008.

But then you need to uninstall wine and reinstall stable 1.0.1 to actually start fm.exe. winecfg Xp or Windows 2008.

The game starts and gets to the LoadGame, NewGame etc. screen. A note pops up saying you need to insert disc and retry or cancel.

On windows the same iso runs through daemon tools with success. Do you think I need to install daemon tools under wine or am I missing something?

---

### Post by moujik on 2009-11-01
There's a Crack (NoCD) for 10.1 patch.

It works, but appears to want the disc. Never mind that, it saves the game.

IMPORTANT: uncheck "Compress save file" in Preferences otherwise it really wants the disc when you try to load a saved game!

   *I messed around with Liverpool, Premiership only, small data, played one game vs Reserves 4-0. Almost sold Lucas to Sunderland for £15mil, made new tactics, searched for players. Saved and Resumed. Everything worked OK.*

If anyone runs into trouble installing post here, and I'll try to help.

---

### Post by gosam on 2009-11-01
I'm having trouble activating the game (I went for a digital download through gamersgate). I managed to get the activation window to show up after installing ie6 with winetricks but now it simply always fails with a -1036 error whatever the key I type in (i.e it doesn't even get to the point of verifying it).

Here's the console output after I try to submit the key : 
```

fixme:seh:_abnormal_termination (void)stub
fixme:seh:_abnormal_termination (void)stub
fixme:seh:_abnormal_termination (void)stub
err:ole:CoGetClassObject class {81397204-f51a-4571-8d7b-dc030521aabd} not registered
err:ole:CoGetClassObject no class object {81397204-f51a-4571-8d7b-dc030521aabd} could be created for context 0x1
fixme:seh:_abnormal_termination (void)stub                                                                      
err:ole:CoGetClassObject class {81397204-f51a-4571-8d7b-dc030521aabd} not registered                            
err:ole:CoGetClassObject no class object {81397204-f51a-4571-8d7b-dc030521aabd} could be created for context 0x1
fixme:toolhelp:CreateToolhelp32Snapshot Unimplemented: heap list snapshot                                       
err:ole:CoGetClassObject class {81397204-f51a-4571-8d7b-dc030521aabd} not registered                            
err:ole:CoGetClassObject no class object {81397204-f51a-4571-8d7b-dc030521aabd} could be created for context 0x1
err:ole:CoGetClassObject class {81397204-f51a-4571-8d7b-dc030521aabd} not registered                            
err:ole:CoGetClassObject no class object {81397204-f51a-4571-8d7b-dc030521aabd} could be created for context 0x1
fixme:ole:CoInitializeSecurity ((nil),-1,(nil),(nil),0,3,(nil),0,(nil)) - stub!                                 
fixme:wbemprox:wbem_locator_ConnectServer 0x77b59d8, L"ROOT\\CIMV2", (null), (null), (null), 0x00000000, (null), (nil), 0x328a4f8)
fixme:mountmgr:harddisk_ioctl unsupported ioctl 41018                                                                             
fixme:mountmgr:harddisk_ioctl unsupported ioctl 4d004                                                                             
fixme:ole:Context_CC_ContextCallback (0x1b16a8/0x1b16ac)->(0x79f277a5, 0x869dfdc, {d7174f82-36b8-4aa8-800a-e963ab2dfab9}, 2, (nil))
fixme:seh:_abnormal_termination (void)stub                                                                                         
fixme:seh:_abnormal_termination (void)stub                                                                                         
fixme:seh:_abnormal_termination (void)stub                                                                                         
fixme:seh:_abnormal_termination (void)stub                                                                                         
fixme:seh:_abnormal_termination (void)stub                                                                                         
fixme:seh:_abnormal_termination (void)stub                                                                                         
fixme:seh:_abnormal_termination (void)stub                                                                                         
fixme:seh:_abnormal_termination (void)stub                                                                                         
err:ole:CoGetClassObject class {6c736db1-bd94-11d0-8a23-00aa00b58e10} not registered                                               
err:ole:CoGetClassObject no class object {6c736db1-bd94-11d0-8a23-00aa00b58e10} could be created for context 0x1                   
fixme:seh:_abnormal_termination (void)stub                                                                                                                                                                               
fixme:wininet:GetUrlCacheEntryInfoExW Undocumented flag(s): 100                                                                    
fixme:wininet:GetUrlCacheEntryInfoExW Undocumented flag(s): 100                                                                    
fixme:wininet:CommitUrlCacheEntryInternal entry already in cache - don't know what to do!                                          
fixme:seh:_abnormal_termination (void)stub                                                                                         
fixme:seh:_abnormal_termination (void)stub                                                                                         
fixme:seh:_abnormal_termination (void)stub                                                                                         
fixme:seh:_abnormal_termination (void)stub                                                                                         
fixme:seh:_abnormal_termination (void)stub                                                                                         
fixme:seh:_abnormal_termination (void)stub                                                                                         
fixme:seh:_abnormal_termination (void)stub


```

Any ideas?

---

### Post by muddey on 2009-11-01
I copied the DVD to the hard drive and installed FM fine with WINE. I then installed the patch OK, but when I run the game I get a blank screen after the loading images (Kick racism out, etc). 

I've set WINE to run under Win 2008 since it didn't load the game at all under XP. 

I'm running Ubuntu 9.10 with WINE 1.0.1 and have installed both .net and dxirectx9 with winetricks.

I've also tried to play the game without the patch, but with the same result.

Any ideas?

---

### Post by moujik on 2009-11-01
> **muddey said:**
> I copied the DVD to the hard drive and installed FM fine with WINE. I then installed the patch OK, but when I run the game I get a blank screen after the loading images (Kick racism out, etc). 

I've set WINE to run under Win 2008 since it didn't load the game at all under XP. 

I'm running Ubuntu 9.10 with WINE 1.0.1 and have installed both .net and dxirectx9 with winetricks.

I've also tried to play the game without the patch, but with the same result.

Any ideas?

Sorry, for some reason I couldn't log in.. Try to install vcrun6 etc with winetricks. I have vbrun as well. I'm not sure that it's possible to play with DVD under Linux. But there is a crack which works so you can at least play.

---

### Post by moujik on 2009-11-01
> **gosam said:**
> I'm having trouble activating the game (I went for a digital download through gamersgate)

Any ideas?

Not tried that. There is a way of playing it without authentication as mentioned above.

---

### Post by moujik on 2009-11-01
> **muddey said:**
> I copied the DVD to the hard drive and installed FM fine with WINE. I then installed the patch OK, but when I run the game I get a blank screen after the loading images (Kick racism out, etc). 

I've set WINE to run under Win 2008 since it didn't load the game at all under XP. 

I'm running Ubuntu 9.10 with WINE 1.0.1 and have installed both .net and dxirectx9 with winetricks.

I've also tried to play the game without the patch, but with the same result.

Any ideas?

The reason I had to install wine 1.1.31 is because 1.0.1 didn't provide d3dx9_41.dll, only up to 40, but that was during install. Still might be worth getting it..

---

### Post by tbugge on 2009-11-02
> **moujik said:**
> Hello manager!

I've managed to install an iso version of full 2010 (multi). It requires no validation if you play with DVD. But somehow wine doesn't seem to see a drive I've created as DVD-rom and asks to insert the disc on start up.

Progress so far:

wine 1.1.14 at least (I tried wine 1.1.31) is needed to be able to run setup. winecfg to Windows2008.

But then you need to uninstall wine and reinstall stable 1.0.1 to actually start fm.exe. winecfg Xp or Windows 2008.

The game starts and gets to the LoadGame, NewGame etc. screen. A note pops up saying you need to insert disc and retry or cancel.

On windows the same iso runs through daemon tools with success. Do you think I need to install daemon tools under wine or am I missing something?

I tried this approach and the installation worked like a charm - no errors. Then I degraded to wine1.0.1 and tried to run the game. But I just get a white screen and nothing happens so i guess its a problem with the graphics. Any suggestions what to do? :|

---

### Post by The_Aegidius on 2009-11-02
Hi!

Before to install the game, I installed d3dx9 as suggest on [WineHQ site]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=18235&iTestingId=46101"), but when i try to start the game i get this error.

```

fixme:powrprof:DllMain (0x7a8c0000, 1, (nil)) not fully implemented
wine: Call from 0x7b8453f0 to unimplemented function pdh.dll.PdhMakeCounterPathW, aborting
wine: Unimplemented function pdh.dll.PdhMakeCounterPathW called at address 0x7b8453f0 (thread 0019), starting debugger...
Unhandled exception: unimplemented function pdh.dll.PdhMakeCounterPathW called in 32-bit code (0x7b845442).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:7b845442 ESP:0032f28c EBP:0032f2f0 EFLAGS:00200246(   - 00      - IZP1)
 EAX:7b82ecc9 EBX:7b8b6ff4 ECX:00000000 EDX:80000100
 ESI:80000100 EDI:0222b200
Stack dump:
0x0032f28c:  0032f310 00000008 0000003c 80000100
0x0032f29c:  00000001 00000000 7b8453f0 00000002
0x0032f2ac:  741661c0 74166726 00000000 00000000
0x0032f2bc:  00139e20 00000000 00110000 0000000a
0x0032f2cc:  00000000 00000000 00000000 00110014
0x0032f2dc:  00000000 00000000 7b8453fa 00000000
Backtrace:
=>1 0x7b845442 in kernel32 (+0x25442) (0x0032f2f0)
  2 0x74166145 in pdh (+0x6145) (0x0032f320)
  3 0x74162a54 in pdh (+0x2a54) (0x00000000)
0x7b845442: subl    $4,%esp
Modules:
Module    Address            Debug info    Name (139 modules)
PE      330000-  3ba000    Deferred        saauditmt
PE      400000- 2326000    Deferred        fm
PE     2cf0000- 2d16000    Deferred        intellaptopgamingxp
PE    10000000-1041a000    Deferred        d3dx9_41
PE    3b400000-3b41d000    Deferred        steam_api
ELF    60000000-6001d000    Deferred        ld-linux.so.2
ELF    6001d000-60153000    Deferred        libwine.so.1
ELF    60153000-60157000    Deferred        libdl.so.2
ELF    60157000-6017d000    Deferred        libm.so.6
ELF    6017d000-60185000    Deferred        libnss_compat.so.2
ELF    60185000-6019c000    Deferred        libnsl.so.1
ELF    6019c000-601a7000    Deferred        libnss_nis.so.2
ELF    601a7000-601b3000    Deferred        libnss_files.so.2
ELF    601b3000-601e4000    Deferred        d3d9<elf>
  \-PE    601c0000-601e4000    \               d3d9
ELF    601e4000-60283000    Deferred        gdi32<elf>
  \-PE    601f0000-60283000    \               gdi32
ELF    60283000-602d5000    Deferred        advapi32<elf>
  \-PE    60290000-602d5000    \               advapi32
ELF    602d5000-602ea000    Deferred        faultrep<elf>
  \-PE    602e0000-602ea000    \               faultrep
ELF    602ea000-6030b000    Deferred        imm32<elf>
  \-PE    602f0000-6030b000    \               imm32
ELF    6030b000-60338000    Deferred        ws2_32<elf>
  \-PE    60310000-60338000    \               ws2_32
ELF    60338000-60357000    Deferred        iphlpapi<elf>
  \-PE    60340000-60357000    \               iphlpapi
ELF    60357000-6036c000    Deferred        wtsapi32<elf>
  \-PE    60360000-6036c000    \               wtsapi32
ELF    6036c000-603b8000    Deferred        dbghelp<elf>
  \-PE    60370000-603b8000    \               dbghelp
ELF    603b8000-603ce000    Deferred        psapi<elf>
  \-PE    603c0000-603ce000    \               psapi
ELF    603ce000-60419000    Deferred        dsound<elf>
  \-PE    603e0000-60419000    \               dsound
ELF    60419000-6047c000    Deferred        rpcrt4<elf>
  \-PE    60430000-6047c000    \               rpcrt4
ELF    6047c000-604d7000    Deferred        shlwapi<elf>
  \-PE    60490000-604d7000    \               shlwapi
ELF    604d7000-60540000    Deferred        setupapi<elf>
  \-PE    604e0000-60540000    \               setupapi
ELF    60540000-60555000    Deferred        lz32<elf>
  \-PE    60550000-60555000    \               lz32
ELF    60555000-60578000    Deferred        mpr<elf>
  \-PE    60560000-60578000    \               mpr
ELF    60578000-6063b000    Deferred        comctl32<elf>
  \-PE    60580000-6063b000    \               comctl32
ELF    6063b000-606a5000    Deferred        crypt32<elf>
  \-PE    60650000-606a5000    \               crypt32
ELF    606a5000-6074b000    Deferred        oleaut32<elf>
  \-PE    606c0000-6074b000    \               oleaut32
ELF    6074b000-607f9000    Deferred        comdlg32<elf>
  \-PE    60750000-607f9000    \               comdlg32
ELF    607f9000-60830000    Deferred        winspool<elf>
  \-PE    60800000-60830000    \               winspool
ELF    60830000-608af000    Deferred        libfreetype.so.6
ELF    608af000-608c5000    Deferred        libz.so.1
ELF    608c5000-608f2000    Deferred        libfontconfig.so.1
ELF    608f2000-60919000    Deferred        libexpat.so.1
ELF    60919000-60922000    Deferred        libsm.so.6
ELF    60922000-6093d000    Deferred        libice.so.6
ELF    6093d000-60943000    Deferred        libxxf86vm.so.1
ELF    60943000-60953000    Deferred        libxext.so.6
ELF    60953000-60958000    Deferred        libuuid.so.1
ELF    60958000-6095c000    Deferred        libxau.so.6
ELF    6095c000-60961000    Deferred        libxdmcp.so.6
ELF    60961000-60964000    Deferred        libxinerama.so.1
ELF    60964000-6096e000    Deferred        libxrender.so.1
ELF    6096e000-60972000    Deferred        libxcomposite.so.1
ELF    60972000-6097d000    Deferred        libxcursor.so.1
ELF    6097d000-609b4000    Deferred        winealsa<elf>
  \-PE    60990000-609b4000    \               winealsa
ELF    609b4000-60a7b000    Deferred        libasound.so.2
ELF    60a7b000-60a84000    Deferred        librt.so.1
ELF    60a87000-60ac7000    Deferred        libpulse.so.0
ELF    60ac7000-60ad0000    Deferred        libwrap.so.0
ELF    60ad0000-60b3c000    Deferred        libsndfile.so.1
ELF    60b3c000-60b75000    Deferred        libdbus-1.so.3
ELF    60b75000-60bc5000    Deferred        libflac.so.8
ELF    60bc5000-60cbf000    Deferred        libvorbisenc.so.2
ELF    60cbf000-60cea000    Deferred        libvorbis.so.0
ELF    60cea000-60cf1000    Deferred        libogg.so.0
ELF    60cf1000-60cf8000    Deferred        libasound_module_pcm_pulse.so
ELF    60cf8000-60d10000    Deferred        msacm32<elf>
  \-PE    60d00000-60d10000    \               msacm32
ELF    60d10000-60d38000    Deferred        msacm32<elf>
  \-PE    60d20000-60d38000    \               msacm32
ELF    60d38000-60d4e000    Deferred        midimap<elf>
  \-PE    60d40000-60d4e000    \               midimap
ELF    60d4e000-60d81000    Deferred        uxtheme<elf>
  \-PE    60d50000-60d81000    \               uxtheme
ELF    60d81000-60dae000    Deferred        libgssapi_krb5.so.2
ELF    60dae000-60e56000    Deferred        libgnutls.so.26
ELF    60e56000-60f08000    Deferred        libkrb5.so.3
ELF    60f08000-60f33000    Deferred        libk5crypto.so.3
ELF    60f33000-60f37000    Deferred        libcom_err.so.2
ELF    60f37000-60f3b000    Deferred        libkeyutils.so.1
ELF    60f3b000-60f4d000    Deferred        libtasn1.so.3
ELF    60f4d000-60fc9000    Deferred        libgcrypt.so.11
ELF    60fc9000-60fce000    Deferred        libgpg-error.so.0
ELF    610be000-610c4000    Deferred        libxfixes.so.3
ELF    617a1000-617b2000    Deferred        libavahi-client.so.3
ELF    63487000-634a5000    Deferred        libxcb.so.1
ELF    6b31a000-6b32e000    Deferred        libresolv.so.2
ELF    6b47c000-6b485000    Deferred        libkrb5support.so.0
ELF    6c406000-6c421000    Deferred        version<elf>
  \-PE    6c410000-6c421000    \               version
ELF    6c554000-6c5fa000    Deferred        ole32<elf>
  \-PE    6c560000-6c5fa000    \               ole32
ELF    6d3f6000-6d3fc000    Deferred        libxtst.so.6
ELF    71b56000-71b6f000    Deferred        libpthread.so.0
ELF    727cf000-727db000    Deferred        libavahi-common.so.3
ELF    72bd0000-72ce0000    Deferred        wined3d<elf>
  \-PE    72be0000-72ce0000    \               wined3d
ELF    73d26000-73e6a000    Deferred        libc.so.6
ELF    74150000-7416b000    Export          pdh<elf>
  \-PE    74160000-7416b000    \               pdh
ELF    747ba000-7480a000    Deferred        wininet<elf>
  \-PE    747c0000-7480a000    \               wininet
ELF    75b56000-75ca1000    Deferred        user32<elf>
  \-PE    75b70000-75ca1000    \               user32
ELF    767fc000-76841000    Deferred        libcups.so.2
ELF    76a75000-76b0f000    Deferred        winex11<elf>
  \-PE    76a80000-76b0f000    \               winex11
PE    78000000-78044000    Deferred        msvcrt
ELF    79060000-790aa000    Deferred        libpulsecommon-0.9.19.so
ELF    790d0000-790d9000    Deferred        libxrandr.so.2
ELF    793b4000-794e3000    Deferred        libx11.so.6
ELF    79a55000-79b69000    Deferred        shell32<elf>
  \-PE    79a70000-79b69000    \               shell32
ELF    7a8bf000-7a8d5000    Deferred        powrprof<elf>
  \-PE    7a8c0000-7a8d5000    \               powrprof
ELF    7adad000-7ae41000    Deferred        winmm<elf>
  \-PE    7adc0000-7ae41000    \               winmm
ELF    7b800000-7b93c000    Export          kernel32<elf>
  \-PE    7b820000-7b93c000    \               kernel32
ELF    7bc00000-7bca7000    Deferred        ntdll<elf>
  \-PE    7bc10000-7bca7000    \               ntdll
ELF    7bf00000-7bf04000    Deferred        <wine-loader>
Threads:
process  tid      prio (all id:s are in hex)
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
00000018 (D) C:\Programmi\Sports Interactive\Football Manager 2010\fm.exe
    00000019    0 <==
Backtrace:
=>1 0x7b845442 in kernel32 (+0x25442) (0x0032f2f0)
  2 0x74166145 in pdh (+0x6145) (0x0032f320)
  3 0x74162a54 in pdh (+0x2a54) (0x00000000)
err:seh:raise_exception Unhandled exception code 80000100 flags 1 addr 0x7b8453f0

```Is it really possible to run this game under Wine?

---

### Post by muddey on 2009-11-02
> **moujik said:**
> Sorry, for some reason I couldn't log in.. Try to install vcrun6 etc with winetricks. I have vbrun as well. I'm not sure that it's possible to play with DVD under Linux. But there is a crack which works so you can at least play.

Thanks for your help moujik. I installed vcrun6 and vb6run with winetricks, but no joy. The logos (i.e. Sigames) are loading really slow and the game never gets to the real loading screen (Where it's saying loading in different languages), just shows a blank screen. 

I'd say it's a DirectX problem, or I just need to update wine to the latest version.

Just found another application, based on Wine, called PlayOnLinux which offers to install FM10 for you. Haven't tried it yet but will as soon as I get a chance.

---

### Post by moujik on 2009-11-02
> **The_Aegidius said:**
> Hi!

Before to install the game, I installed d3dx9 as suggest on [WineHQ site]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=18235&iTestingId=46101"), but when i try to start the game i get this error.

Is it really possible to run this game under Wine?

My guess is installing a few things with winetricks should help
and have you tried the latest wine?

---

### Post by moujik on 2009-11-02
> **tbugge said:**
> I tried this approach and the installation worked like a charm - no errors. Then I degraded to wine1.0.1 and tried to run the game. But I just get a white screen and nothing happens so i guess its a problem with the graphics. Any suggestions what to do? :|

Is your degrading to wine 1.0.1 as good as reinstall. Truth be told I'm running Mandriva (with plf packages) so I just 'urpme' the old wine. I decided to post here cause I myself found help on FM only on here. Do you run fm.exe from shell, what does it say?

For me it errs i.e. err:ole:COMPOBJ_DllList_Add couldn't load in-process dll L"wbemprox.dll but still runs. As long as it doesn't give Bad Descriptor error 15 or 17.

Good Luck!

---

### Post by moujik on 2009-11-02
> **muddey said:**
> Thanks for your help moujik. I installed vcrun6 and vb6run with winetricks, but no joy. The logos (i.e. Sigames) are loading really slow and the game never gets to the real loading screen (Where it's saying loading in different languages), just shows a blank screen. 

I'd say it's a DirectX problem, or I just need to update wine to the latest version.

Just found another application, based on Wine, called PlayOnLinux which offers to install FM10 for you. Haven't tried it yet but will as soon as I get a chance.

Hey don't give up try to install other vcruns and vbruns, msxmls and dotnets!
I'm not sure what exactly FM wants.

---

### Post by The_Aegidius on 2009-11-02
I tried to install it with PlayOnLinux and now it starts showing introducing screens but then appear a black screen. Moving the mouse, the punter change in hand so it's working but there are some problems with graphic acceleration.

---

### Post by moujik on 2009-11-03
> **The_Aegidius said:**
> I tried to install it with PlayOnLinux and now it starts showing introducing screens but then appear a black screen. Moving the mouse, the punter change in hand so it's working but there are some problems with graphic acceleration.

I had this as well at some stage only once though. The next time it wouldn't even get that far before I installed loads of winetricks' media.

---

### Post by The_Aegidius on 2009-11-03
What winetricks' media did you install? It's worked?

---

### Post by sionco on 2009-11-03
I've got it working.

I installed PlayonLinux via Ubuntu-tweak, and installed Football manager 2010 from their, it updated wine and installed Directx(well that what it said it was doing). However, it didn't load the first time, but after I closed the process and loaded it again it worked, but kept asking for the CD.

As, I'm using a copied version, I downloaded the patch and patched the game, before copying the crack to the installation directory.  I also unticked compress saved game files.



The only thing, I can't get working is the game editor, as I really want to run that, anybody know how? or what extra I have to get to install to get it running?

---

### Post by moujik on 2009-11-03
> **The_Aegidius said:**
> What winetricks' media did you install? It's worked?

directx_aug2009_redist.exe
dotnet20/
ie6setup.exe
ie6sites.dat
InstMsiA.exe
msvbvm50.exe
msxml4-KB936181-enu.exe
msxml4.msi
msxml6_x86.msi
pdhinst.exe
vb3run.exe
vb4run.exe
VBRUN200.EXE
vbrun60.exe
vc6redistsetup_enu.exe
vcredist.exe*
vcrun2005/
vcrun2005-ms09-035/
vcrun2005sp1/
vcrun2008-ms09-035/
VisualBasic6-KB896559-v1-ENU.exe

---

### Post by moujik on 2009-11-03
> **sionco said:**
> I've got it working.

I installed PlayonLinux via Ubuntu-tweak, and installed Football manager 2010 from their, it updated wine and installed Directx(well that what it said it was doing). However, it didn't load the first time, but after I closed the process and loaded it again it worked, but kept asking for the CD.

As, I'm using a copied version, I downloaded the patch and patched the game, before copying the crack to the installation directory.  I also unticked compress saved game files.



The only thing, I can't get working is the game editor, as I really want to run that, anybody know how? or what extra I have to get to install to get it running?

well done! Editor never worked for me under Linux.. *I know some players are overrated and I would also like to tweak them down. i.e. Forwards who you know can't dribble past one defender in real life having 16+ dribbling etc.*

---

### Post by muddey on 2009-11-03
I can't get this to work, even though I've tried everything suggested. 

I uninstalled wine and deleted the configs to start from scratch. 

1. Installed Wine through Ubuntu Software Center (v. 1.0.1)
2. Installed winetricks
3. Installed everything from moujik's winetricks list.
4. Installed the game ok. Wasn't sure if to choose "update directx after install" or not? I said yes anyhow. 
5. At this point after multiple install attempts I didn't even bother with the FM patch, since that's note the issue.
6. The game didn't run so I had to go in to wine config and change from Win XP to Win 2008.
7. The game is only loading the first few images (Sigames etc), then it just gets black.

I've tried to set Visual effects to none as well, but it didn't make a difference.

I give up!

Oh, and I tried with PlayOnLinux like sionco, but that just gives me a white screen when i load the game so it was a step back.

*edit* I read on fmtux.net that I shouldn't let FM update dirext x, so I uninstalled everything, deleted cache and configs and redid everything without having FM updating directx. In FMTUX's [guide]("http://www.fmtux.net/index.php/topic,254.0.html") to install the demo they provide d3dx9_36.dll which should be placed in the system32 folder. I didn't create a new prefix as they suggest since I assume that is if you want separate settings for different apps, but since I'm not running anything but FM on wine I don't care.

The game still won't load, but I can now load it as far as the sigames logo with wine running as WinXP as well as 2008.

---

### Post by The_Aegidius on 2009-11-04
I think it depends by the graphic card, cause under the black screen the game is working.

---

### Post by duman84 on 2009-11-10
hi, i installed the FM2010 by Playonlinux... The game starting but i take the error on the picture, and than the game was started but without 3d... so i couldn't watch the matches on the pitch.. i use acer aspire 5720 with Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
any idea??? thanks
p.s. compiz was closed..

[IMG]http://img130.imageshack.us/img130/964/ekrangrnts.jpg[/IMG]

---

### Post by Spongeroberto on 2009-12-02
I used a clean wineprefix

```
export WINEPREFIX=$HOME/.wine-fm10
```

then i added the direct3d part of directx9 and pdh using winetricks

```
sh winetricks d3dx9 pdh
```

After that the game runs, but it is still very sluggish compared to the performance in Windows.

---

### Post by crank_it_up on 2009-12-05
Guys, Im sorry to ask such a basic question, but could someone post me a link to where I can get the no-CD crack file (or it's torrent)

I have installed fm2010 sucessfully but have fallen at the last hurdle, which on the face of it should be the easy part!! Every link seems to redirect to a pay download site. I feel like an idiot but I can't get round it!

Any help appreciated!

---

### Post by crank_it_up on 2009-12-06
Hi, I found the crack file. Everything is working fine. In case anyone is interested my settings are:

Latest Wine
config set to win2008
virtual desktop
lastest vbrun
latest vcrun
direct x

---

### Post by benjaminjames on 2009-12-13
For anyone still struggling with installing football manager 2010 , its VERY easily done 
. If you go into the Ubuntu software center and install "play on Linux" they have an automated process that installs it perfectly :)[COLOR="black"][/COLOR]

---

### Post by Pever on 2009-12-18
Interesting that PlayonLinux worked for you.  The program installed perfectly, but when it comes to actually running the program, there is nothing.  Nothing pops up.  No window.  No intro even.  No evidence of the program even starting.

Same with WINE.  Installs perfectly, but nothing works.  The only evidence in WINE is that a bar on the bottom of the screen indicates that a FM2010 window has been created, but it closes within a few seconds and there is nothing.

Any hints anyone?

---

### Post by RickJC on 2009-12-20
> **Pever said:**
> Interesting that PlayonLinux worked for you.  The program installed perfectly, but when it comes to actually running the program, there is nothing.  Nothing pops up.  No window.  No intro even.  No evidence of the program even starting.

Same with WINE.  Installs perfectly, but nothing works.  The only evidence in WINE is that a bar on the bottom of the screen indicates that a FM2010 window has been created, but it closes within a few seconds and there is nothing.

Any hints anyone?


I've got the same trouble as you, I've installed FM10 using both Wine and PlayOnLinux but nothing happens. They install fine on both but when I try to open/play FM10 nothing actually happens. Could this be a direct x issue maybe?

Any help would be great!

---

### Post by RickJC on 2009-12-20
Ok weird thing happened, after I finished writing the above post the game actually started from when I tried to play it! So basically it does start but it takes just over 5 minutes to start!

Anyway even though it 'start' it's actually only using like the bottom left part of the screen, also the buttons don't seem to work. Anyone else had this?

---

### Post by Amilo1718 on 2009-12-27
I tried to install fm 2010 in linux...

wine 1.1.35 (the needed .dll is present there)

wine: xp mode

fm install 1.0
patch install 1.2

launch fm.exe
=> nothing happens

install directx 9.0c
launch fm.exe
=> black screen after the logon splash screens

so... what did i forget to do ?

---

### Post by TRF on 2010-01-04
same here
a ball-mouse and "black-screen" ... nothing happens

---

### Post by moujik on 2010-01-08
> **RickJC said:**
> Ok weird thing happened, after I finished writing the above post the game actually started from when I tried to play it! So basically it does start but it takes just over 5 minutes to start!

Anyway even though it 'start' it's actually only using like the bottom left part of the screen, also the buttons don't seem to work. Anyone else had this?
Change you screen resolution to lower and try again. You can change in-game resolution to what you normally have, or keep lowering screen resolution before playing if you want bigger letters..

---

### Post by TRF on 2010-01-09
got it running 
but have an obvious problem ... screen - split
see screenshot ...
[[IMG]http://ubuntu-pics.de/thumb/37303/2010_01_09_171606_1280x800_scrot_lEmiQN.png[/IMG]]("http://ubuntu-pics.de/bild/37303/2010_01_09_171606_1280x800_scrot_lEmiQN.png")

---

### Post by RickJC on 2010-01-09
Ok had to format Laptop the other day so I've had to try and reinstall FM but I'm getting a different error than what I've had before. Anyone had this:

[B]An unexpected error has been detected by Java Runtime Environment:

EXCEPTION_ACCESS_

Java VM: Java HotS
Problematic frame:
C[/B]

Anyone?

---

### Post by indieboymatt on 2010-01-21
how do you get fm2010 to work on ubuntu 9.10? what do i need to do?

i have managed to install it, but it won't open, nothing happens. and if it does manage to open it is only a black screen

---

### Post by FinnMcCool on 2010-01-29
I'm in the very same boat as IndyboyMatt above.
 
I'm an absolute beginner to this ubuntu malarky although I really like it so far. But Football Manager 2010 is something I'm definitely going to need. Any help?

---

### Post by KriZo on 2010-01-30
Has anyone had any succes running the data editor?

---

### Post by Tha-Fox on 2010-02-09
I also tried to install using both Wine and PlayOnLinux. Both install fine. On PlayOnLinux, nothing happens after starting the game. On Wine itself I get the ball cursor but the screen remains black. If I move the cursor around I get the pointing finger cursor on some spots. So I think the game is running well under that black veil. I have Acer 5024 with Ati Mobility Radeon x700, could this be the issue?

I'm using 9.10 with Wine 1.1.32.

---

### Post by tnoc87 on 2010-02-16
Using a downloaded iso:
Wine installed, couldn't get it to run, at all.
PlayonLinux installed and could start, to new game, load game etc, needed no cd crack, as soon as it was applied, it wouldn't run anymore, and it was the same if i updated with any official patch!? anyone got any ideas?

---

### Post by mR0 on 2010-02-17
I installed FM 2010 on wine. When starting the game it always ask me to Insert the DVD, although I mounted the ISO through Gmount-iso.
Is here anyone know how to mount FM 2010 ISO to wine?

---

### Post by bluewigan on 2010-02-22
You can mount an image using Gmount-iso from Ubuntu Software Centre. I can find no way of mounting an iso to work with Wine. Use playonlinux and install FM2010 through there. 

Have the image mounted to a DVD using Gmount vefore hand. When playonlinux asks you where it is mounted to, you can then tell it.

PROBLEM:

When I do this, I get the following error message in the terminal:



EXCEPTION_ACCESS_VIOLATION (0xc0000005) at pc=0x53c119d2, pid=28, tid=42
#
# Java VM: Java HotSpot(TM) Client VM (11.0-b16 mixed mode windows-x86)
# Problematic frame:
# C  [wined3d.dll+0x319d2]
#
# An error report file with more information is saved as:
# C:\windows\temp\I1266870175\Windows\hs_err_pid28.log


Can anyone help me with this? It is getting ridiculous how much time I have spent trying to get FM to work with Ubuntu 9.10. ARRGH!!

---

### Post by rcayea on 2010-02-22
I, too, am trying to install FM2010 through Steam. I was wondering how do I know what DLLs to override? Is there a command that will tell me which ones are not "clicking"?

Thanks!

---

### Post by The_Aegidius on 2010-03-05
Did you solve the black screen problem?

---

### Post by Dmck23 on 2010-03-17
Hi, 

Was wondering has anyone managed to get the 3d matchs to work. I'm only able to watch matchs in 2d as when i try to watch them in 3d all i get is a black pitch with the out line o the goals.

I've installed all the directx packages from winetricks but still no joy. 

I think it's a problem with setting up Directx in Regedit in wine as there is no settings for it in my Regedit. Could someone who has got the 3d match engine to run please post the settings of the HKEY_CURRENT_USER\Software\Wine\Direct3d folder so i can set mine to see if this fixes any issues..

thanks
Dmck23

---

### Post by sionco on 2010-04-12
The new update seems to of made the mouse invsibile.

Also, I got the editor working by running it and waiting 6 or 7 minutes for it to load, and if it hasn't by that time, I use killall editor.exe and then try running it again until it does load.  Shame it takes so long to open and the resolution of the editor is stretched on my wide-screen laptop.

---

### Post by X_Splinter on 2010-04-21
It works well if you follow the instructions of fmtux.com

Also check wine hq [http://appdb.winehq.org/objectManager.php?sClass=version&iId=18235&iTestingId=50525]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=18235&iTestingId=50525")

The last test was made by me, everything works except the 3D game view.

I didnt tested with playonlinux yet and with Crossover Linux

---

### Post by jackfranklin on 2010-05-06
Hey,

Got it working - yet it takes about 10 minutes to load, any idea how I can shorten this? Just installed it with Wine.

Another thing - it does not show FM in the WINE menu - any idea why?

---

### Post by X_Splinter on 2010-05-06
> **jackfranklin said:**
> Hey,

Got it working - yet it takes about 10 minutes to load, any idea how I can shorten this? Just installed it with Wine.

Another thing - it does not show FM in the WINE menu - any idea why?

Go to fmtux.com and download the nowait intro or something with a name like that.

That fixes that problem

---

### Post by Flegmatik on 2010-05-14
> **X_Splinter said:**
> It works well if you follow the instructions of fmtux.com

Also check wine hq [http://appdb.winehq.org/objectManager.php?sClass=version&iId=18235&iTestingId=50525]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=18235&iTestingId=50525")

The last test was made by me, everything works except the 3D game view.

I didnt tested with playonlinux yet and with Crossover Linux
It's [www.fmtux.net](www.fmtux.net) :)

---

### Post by apostra on 2010-06-12
Hello all,

I have last version wine, xp mode, 10.04 ubuntu, installed wow works smooth, however FM10loads on backgroun, only visable on System Monitor screen, doesnt load at all. What i done so far is:

1)install it with wine and cds, installation was fine, when i start it, i see it running on System monitor but nothing on my screen. console gives me this result:

"err:ole:CoGetClassObject class {9a5ea990-3034-4d6f-9128-01f3c61022bc} not registered"
"err:ole:CoGetClassObject no class object {9a5ea990-3034-4d6f-9128-01f3c61022bc} could be created for context 0x1"

FM runs on background. I see it on System monitor.

2) Install it with PoL, installation was fine, when i try to run it i got a message from PoL that i dont have 3d, kinda wierd since everything is fine considering wow plays smoothly and fm runs on background once again, only visable on System monitor.

I have all the .dll etc etc that needed.

Any ideas plz? thanks in advance.

---

### Post by Jay105 on 2010-06-13
hi

i have a similar problem to one above. installation was fine using playonlinux and winetricks as suggested, but the mouse cursor is invisible. very annoying!

any suggestions?

---

### Post by martinrousev on 2010-08-08
Hi,

I'm not ubuntu user but I see you have a nice discussion going so I decided to write. I use Wine 1.2 on openSUSE 11.3. The game installs OK and then when I try to run it I get the following message: 

err:ole:CoGetClassObject class {9a5ea990-3034-4d6f-9128-01f3c61022bc} not registered
err:ole:CoGetClassObject no class object {9a5ea990-3034-4d6f-9128-01f3c61022bc} could be created for context 0x1
fixme:wtsapi:WTSRegisterSessionNotification Stub 0x1006c 0x00000000
Xlib:  extension "NV-GLX" missing on display ":0.0".
err:winediag:X11DRV_WineGL_InitOpenglInfo Direct rendering is disabled, most likely your OpenGL drivers haven't been installed correctly
fixme:d3d_caps:wined3d_guess_card_vendor Received unrecognized GL_VENDOR "nouveau". Returning HW_VENDOR_NVIDIA.
fixme:d3d_caps:select_card_nvidia_mesa Card selection not handled for Mesa Nouveau driver
X Error of failed request:  BadRequest (invalid request code or no such operation)
  Major opcode of failed request:  154 (GLX)
  Minor opcode of failed request:  179 ()
  Serial number of failed request:  1714
  Current serial number in output stream:  1715


Can somebody, please, help with that?

Thanks,
Martin

---

### Post by martinrousev on 2010-08-11
Hi,

I managed to get past the last error message and several others, but now I get this:

```
fixme:powrprof:GetActivePwrScheme (0x32fb08) stub!
err:ole:CoGetClassObject class {9a5ea990-3034-4d6f-9128-01f3c61022bc} not registered
err:ole:CoGetClassObject no class object {9a5ea990-3034-4d6f-9128-01f3c61022bc} could be created for context 0x1
fixme:wtsapi:WTSRegisterSessionNotification Stub 0x1006c 0x00000000
fixme:win:EnumDisplayDevicesW ((null),0,0x2eae244,0x00000000), stub!
fixme:wtsapi:WTSRegisterSessionNotification Stub 0x20072 0x00000000
fixme:d3d:swapchain_init Add OpenGL context recreation support to context_validate_onscreen_formats
fixme:d3dx:D3DXCompileShader (0x2b78390, 2790, (nil), (nil), "main_vs", "vs_3_0", 10000, 0x2eae45c, 0x2eae380, 0x2eae37c): stub
wine: Unhandled page fault on read access to 0x00000000 at address 0x1124e16 (thread 001b), starting debugger...
Unhandled exception: page fault on read access to 0x00000000 in 32-bit code (0x01124e16).
Register dump:
 CS:0023 SS:002b DS:002b ES:002b FS:0063 GS:006b
 EIP:01124e16 ESP:02eae378 EBP:7ea77f46 EFLAGS:00210286(  R- --  I S - -P- )
 EAX:00000000 EBX:00000000 ECX:00000000 EDX:00000000
 ESI:02b80199 EDI:0000000f
Stack dump:
0x02eae378:  00000000 00000000 00000000 029f8000
0x02eae388:  00000000 00000000 7bc48aab 7bc48aa0
0x02eae398:  00000000 00000af0 00000af0 015118e3
0x02eae3a8:  02546000 00000000 00000af0 02eae47c
0x02eae3b8:  00000aef 0000000f 02eae3d8 0150fa8e
0x02eae3c8:  00000af0 fffe0300 00000100 ffff0300
Backtrace:
=>0 0x01124e16 in fm (+0xd24e16) (0x7ea77f46)
0x01124e16: movl        0x0(%eax),%ecx
Modules:
Module  Address                 Debug info      Name (118 modules)
PE        3d0000-  3f6000       Deferred        intellaptopgamingxp
PE        400000- 2326000       Export          fm
PE      10000000-1008a000       Deferred        saauditmt
PE      3b400000-3b41d000       Deferred        steam_api
ELF     7a2d0000-7b800000       Deferred        libnvidia-glcore.so.256.35
ELF     7b800000-7b981000       Deferred        kernel32<elf>
  \-PE  7b810000-7b981000       \               kernel32
ELF     7bc00000-7bcc8000       Deferred        ntdll<elf>
  \-PE  7bc10000-7bcc8000       \               ntdll
ELF     7bf00000-7bf04000       Deferred        <wine-loader>
ELF     7d598000-7d663000       Deferred        libgl.so.1
ELF     7d681000-7d697000       Deferred        powrprof<elf>
  \-PE  7d690000-7d697000       \               powrprof
ELF     7d6bb000-7d6f2000       Deferred        uxtheme<elf>
  \-PE  7d6c0000-7d6f2000       \               uxtheme
ELF     7d6f2000-7d6ff000       Deferred        libnss_files.so.2
ELF     7d6ff000-7d70b000       Deferred        libnss_nis.so.2
ELF     7d70b000-7d725000       Deferred        libnsl.so.1
ELF     7d725000-7d72e000       Deferred        libnss_compat.so.2
ELF     7d72e000-7d745000       Deferred        libresolv.so.2
ELF     7d745000-7d749000       Deferred        libkeyutils.so.1
ELF     7d749000-7d752000       Deferred        libkrb5support.so.0
ELF     7d752000-7d77a000       Deferred        libk5crypto.so.3
ELF     7d77a000-7d842000       Deferred        libkrb5.so.3
ELF     7d842000-7d9e2000       Deferred        libcrypto.so.1.0.0
ELF     7d9e2000-7da39000       Deferred        libssl.so.1.0.0
ELF     7da39000-7da70000       Deferred        libgssapi_krb5.so.2
ELF     7da70000-7dabd000       Deferred        libcups.so.2
ELF     7dac5000-7dac7000       Deferred        libnvidia-tls.so.256.35
ELF     7db09000-7dbc2000       Deferred        comdlg32<elf>
  \-PE  7db10000-7dbc2000       \               comdlg32
ELF     7dbc2000-7dccb000       Deferred        oleaut32<elf>
  \-PE  7dbe0000-7dccb000       \               oleaut32
ELF     7dccb000-7dd76000       Deferred        crypt32<elf>
  \-PE  7dce0000-7dd76000       \               crypt32
ELF     7dd76000-7de70000       Deferred        comctl32<elf>
  \-PE  7dd80000-7de70000       \               comctl32
ELF     7de70000-7e058000       Deferred        shell32<elf>
  \-PE  7de80000-7e058000       \               shell32
ELF     7e058000-7e07d000       Deferred        mpr<elf>
  \-PE  7e060000-7e07d000       \               mpr
ELF     7e07d000-7e0e0000       Deferred        wininet<elf>
  \-PE  7e090000-7e0e0000       \               wininet
ELF     7e0e0000-7e0f4000       Deferred        lz32<elf>
  \-PE  7e0f0000-7e0f4000       \               lz32
ELF     7e0f4000-7e10e000       Deferred        version<elf>
  \-PE  7e100000-7e10e000       \               version
ELF     7e10e000-7e148000       Deferred        winspool<elf>
  \-PE  7e120000-7e148000       \               winspool
ELF     7e148000-7e1ab000       Deferred        setupapi<elf>
  \-PE  7e150000-7e1ab000       \               setupapi
ELF     7e1ab000-7e1cd000       Deferred        iphlpapi<elf>
  \-PE  7e1b0000-7e1cd000       \               iphlpapi
ELF     7e1cd000-7e239000       Deferred        shlwapi<elf>
  \-PE  7e1e0000-7e239000       \               shlwapi
ELF     7e239000-7e2ce000       Deferred        winmm<elf>
  \-PE  7e240000-7e2ce000       \               winmm
ELF     7e2ce000-7e31c000       Deferred        dsound<elf>
  \-PE  7e2e0000-7e31c000       \               dsound
ELF     7e31c000-7e332000       Deferred        psapi<elf>
  \-PE  7e320000-7e332000       \               psapi
ELF     7e332000-7e390000       Deferred        dbghelp<elf>
  \-PE  7e340000-7e390000       \               dbghelp
ELF     7e390000-7e3a6000       Deferred        wtsapi32<elf>
  \-PE  7e3a0000-7e3a6000       \               wtsapi32
ELF     7e3a6000-7e3d7000       Deferred        ws2_32<elf>
  \-PE  7e3b0000-7e3d7000       \               ws2_32
ELF     7e3d7000-7e3f5000       Deferred        pdh<elf>
  \-PE  7e3e0000-7e3f5000       \               pdh
ELF     7e3f5000-7e3fb000       Deferred        libxfixes.so.3
ELF     7e3fb000-7e407000       Deferred        libxcursor.so.1
ELF     7e407000-7e40b000       Deferred        libxcomposite.so.1
ELF     7e40b000-7e414000       Deferred        libxrandr.so.2
ELF     7e414000-7e41f000       Deferred        libxrender.so.1
ELF     7e41f000-7e425000       Deferred        libxxf86vm.so.1
ELF     7e425000-7e429000       Deferred        libxinerama.so.1
ELF     7e429000-7e44c000       Deferred        imm32<elf>
  \-PE  7e430000-7e44c000       \               imm32
ELF     7e44c000-7e450000       Deferred        libxau.so.6
ELF     7e450000-7e470000       Deferred        libxcb.so.1
ELF     7e470000-7e476000       Deferred        libuuid.so.1
ELF     7e476000-7e491000       Deferred        libice.so.6
ELF     7e491000-7e5cc000       Deferred        libx11.so.6
ELF     7e5cc000-7e5d5000       Deferred        libsm.so.6
ELF     7e5d7000-7e5dc000       Deferred        libcom_err.so.2
ELF     7e5dc000-7e5f1000       Deferred        faultrep<elf>
  \-PE  7e5e0000-7e5f1000       \               faultrep
ELF     7e5f3000-7e6a0000       Deferred        winex11<elf>
  \-PE  7e600000-7e6a0000       \               winex11
ELF     7e769000-7e793000       Deferred        libexpat.so.1
ELF     7e793000-7e7c9000       Deferred        libfontconfig.so.1
ELF     7e7c9000-7e7dd000       Deferred        libz.so.1
ELF     7e7dd000-7e864000       Deferred        libfreetype.so.6
ELF     7e864000-7e876000       Deferred        libxext.so.6
ELF     7e882000-7e8ff000       Deferred        rpcrt4<elf>
  \-PE  7e890000-7e8ff000       \               rpcrt4
ELF     7e8ff000-7ea29000       Deferred        ole32<elf>
  \-PE  7e920000-7ea29000       \               ole32
ELF     7ea29000-7ea93000       Deferred        d3dx9_36<elf>
  \-PE  7ea30000-7ea93000       \               d3dx9_36
ELF     7ea93000-7eaf6000       Deferred        advapi32<elf>
  \-PE  7eaa0000-7eaf6000       \               advapi32
ELF     7eaf6000-7eb8e000       Deferred        gdi32<elf>
  \-PE  7eb00000-7eb8e000       \               gdi32
ELF     7eb8e000-7ecd5000       Deferred        user32<elf>
  \-PE  7eba0000-7ecd5000       \               user32
ELF     7ecd5000-7ee23000       Deferred        wined3d<elf>
  \-PE  7ece0000-7ee23000       \               wined3d
ELF     7ee23000-7ee5c000       Deferred        d3d9<elf>
  \-PE  7ee30000-7ee5c000       \               d3d9
ELF     7efb8000-7efe2000       Deferred        libm.so.6
ELF     7efe4000-7effe000       Deferred        d3dx9_41<elf>
  \-PE  7eff0000-7effe000       \               d3dx9_41
ELF     f74a3000-f74a8000       Deferred        libdl.so.2
ELF     f74a8000-f7613000       Deferred        libc.so.6
ELF     f7613000-f762e000       Deferred        libpthread.so.0
ELF     f764c000-f778e000       Deferred        libwine.so.1
ELF     f778f000-f77b0000       Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
00000008 (D) C:\Program Files\Football Manager 2010\fm.exe
        0000001b    0 <==
        0000001a    0
        00000009    0
0000000e services.exe
        00000015    0
        00000014    0
        00000010    0
        0000000f    0
00000011 winedevice.exe
        00000017    0
        00000016    0
        00000013    0
        00000012    0
00000018 explorer.exe
        00000019    0
Backtrace:
=>0 0x01124e16 in fm (+0xd24e16) (0x7ea77f46)
```

Any ideas will be greatly appreciated!

---

### Post by DiscoKiller on 2010-08-11
> **moujik said:**
> 
 
*I messed around with Liverpool, Premiership only, small data, played one game vs Reserves 4-0. **Almost sold Lucas to Sunderland for £15mil**, made new tactics, searched for players. Saved and Resumed. Everything worked OK.*
 

 
 
If only... :)
 
Peace, 
DK

---

### Post by Hawhaw1 on 2010-08-21
Hey.
Just downloaded FM 2010  (RELOADED) but have no idea how to get it to work.
Also, when I done this on Windows, a lot of .rar files appeared that i simply extracted, but on this download there appears to be none, any ideas?
Is there anything i need to install to get this to work?

---

### Post by jackhynes on 2010-09-04
Don't forget to turn off pixel shading in wine configuration else you'll just get a black screen if your hardware doesn't support it.

---

### Post by wild_oscar on 2010-10-16
> **The_Aegidius said:**
> Did you solve the black screen problem?

Did you have compiz running while having the black screen issue?

I had a black screen in windowed mode, but this problem was solved by going to system-preferences-appearence-visual effects and changing to "none".


Don't know yet what makes this problem appear when visual effects are turned on though...

---

### Post by PompeyGibbs on 2010-11-16
> **benjaminjames said:**
> For anyone still struggling with installing football manager 2010 , its VERY easily done 
. If you go into the Ubuntu software center and install "play on Linux" they have an automated process that installs it perfectly :)

A little late to this forum, but I'm new to Ubuntu ;)

I have run this process, then when I launch the app.... Nothing!

I have edited the Wine config to make the app run in windowed config, when I launch the app I end up with a windowed blue screen... I am running the game from the DVD disk, but my machine doesn't try to access the disk!

My thoughts after playing with settings and installing and running all tips/tricks in many forums are that maybe the game isn't happy on 10.04...?

Any ideas from anybody? (All assuming anybody is taking any notice of this thread anymore :P)

---

### Post by weetabix1 on 2012-02-23
> **PompeyGibbs said:**
> A little late to this forum, but I'm new to Ubuntu ;)

I have run this process, then when I launch the app.... Nothing!

Any ideas from anybody? (All assuming anybody is taking any notice of this thread anymore :P)

Well, my solution to problem:
Winecfg:
windows: Windows2008
libraries: bunch of native d3dx9_xx.dll, msvcr80, msvcr90 (install directx9 with winetrics)
graphics: window settings: only emulate virtual desktop selected (same as native resolution in use), direct3d: hardware  and  "allow pixel shaders" = DO NOT SELECT 

regedit
HKEY_CURRENT_USER / Software / Wine / Direct3D:
DirectDrawRenderer = gdi
Multisampling = disabled
OffscreenRenderingMode = backbuffer
PixelShaderMode = disabled
UseGLSL = disabled

The "all blue after startup and nothing happens", solution is the OffscreenRenderingMode = backbuffer and PixelShaderMode = disabled together . 

Start the game from command line, so you can Ctrl+C if it doesn't start the first time (just try again).

Then for me the game simply turns "white screen" in some random time middle of playing game but the game is still working because i can save (when i know where to push and how to select save) and can quit also. 
"White screen issue" is fixed with DirectDrawRenderer = gdi (opengl makes this).

---

