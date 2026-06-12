---
title: "Civilization V (Steam) - Anyone Had Any Luck in Wine?"
date: 2010-09-27
forum: Wine
---

### Post by plinydogg on 2010-09-27
Hi everyone,

I was wondering if anyone was having any luck getting the Steam version of Civilization 5 to run in Wine?

My own experience is that the demo ran almost flawlessly in Wine 1.3.3 out of the box, but the full version does not run at all.

When I start the game, I get the normal choice to choose between DX9 and whatever the other one is, but when I choose DX9, I get an error that says something to the effect of "CivilizationV.exe has encountered a problem and needs to close...."

Thanks!

---

### Post by Half-Left on 2010-09-27
Retail version works here perfectly and a friend of mine says the full Steam version works just fine.

Have you tried installing the latest DirectX for the dll overides or vcrun packages?

---

### Post by rchille on 2010-09-27
I have the Steam release of Civ V and everything seems to work well except sound. The sound crashed before I can actually get into a game.

---

### Post by plinydogg on 2010-09-27
Well, no, I'm not sure I have all of the proper overrides although I think I do since the demo worked fine. Hopefully someone with the Steam version can list what overrides they have here eventually.

---

### Post by Half-Left on 2010-09-27
> **plinydogg said:**
> Well, no, I'm not sure I have all of the proper overrides although I think I do since the demo worked fine. Hopefully someone with the Steam version can list what overrides they have here eventually.

If you install the latest DirectX, Wine will use the dll's and you'll see them in the Wine Configuration.

Attached a screenshot of mine.

---

### Post by plinydogg on 2010-09-27
Thanks for the screenshot. Unfortunately, the only DirectX latest version I can find is a websetup version that doesn't work in WINE...I'll keep looking for the whole enchilada (i.e., not the websetup version). Thanks!

---

### Post by Half-Left on 2010-09-27
Try [This]("http://www.microsoft.com/downloads/en/details.aspx?FamilyID=3b170b25-abab-4bc3-ae91-50ceb6d8fa8d")

Just run the exe and extract to a directory and run the setup installer in there.

---

### Post by plinydogg on 2010-09-27
Thanks for the link but sadly I still couldn't get it to work. I installed DirectX and verified that I had all of the things you had in Winecfg.

Weird. Weird especially since the demo worked fine. Oh well....

---

### Post by plinydogg on 2010-09-27
Oddly enough, Civilization IV doesn't work anymore either (i.e., since I upgraded to Wine 1.3.3).

Here's the errors I get when I try to run Civ 5:


> fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.Windows.Common-Controls" (6.0.0.0)
fixme:wbemprox:wbem_locator_ConnectServer 0x81c0748, L"\\\\.\\root\\cimv2", (null), (null), (null), 0x00000000, (null), (nil), 0x85c91b4)
fixme:dsound:IKsPrivatePropertySetImpl_Get unsupported property: {f2957840-260c-11d1-a4d8-00c04fc28aca}
fixme:win:EnumDisplayDevicesW ((null),0,0x323e90,0x00000000), stub!
fixme:win:EnumDisplayDevicesW (L"\\\\.\\DISPLAY1",0,0x323b48,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),1,0x323e90,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x324170,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x323e18,0x00000000), stub!
wine: Unhandled page fault on write access to 0x209df3d4 at address 0x79408d (thread 0009), starting debugger...
Unhandled exception: page fault on write access to 0x209df3d4 in 32-bit code (0x0079408d).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:0079408d ESP:00328f18 EBP:008edf08 EFLAGS:00210283(  R- --  I S - - -C)
 EAX:00329068 EBX:00000003 ECX:00329068 EDX:00329068
 ESI:00328f54 EDI:206b636c
Stack dump:
0x00328f18:  206b6369 00328f54 007923e9 206b636c
0x00328f28:  78556870 0000000e 0000003d 00000000
0x00328f38:  006813e3 206b6369 00000003 008edf08
0x00328f48:  00000000 00b60778 00329474 00329068
0x00328f58:  00000000 626f7250 736d656c 72657720
0x00328f68:  6f662065 20646e75 74206e69 73206568
Backtrace:
=>0 0x0079408d in civilizationv (+0x39408d) (0x008edf08)
  1 0x0000000a (0x00203d20)
0x0079408d: movb	$0x0,0x0(%edi,%eax,1)
Modules:
Module	Address			Debug info	Name (116 modules)
PE	  330000-  343000	Deferred        zlib1
PE	  350000-  378000	Deferred        lua51_win32
PE	  390000-  3fb000	Deferred        mss32
PE	  400000- 6c80000	Export          civilizationv
PE	 6c80000- 72dd000	Deferred        cvgamecoredllfinal release
PE	 72e0000- 73ae000	Deferred        cvlocalizationwin32final releaseC:\Program Files\Steam\steamapps\common\sid meier's civilization v\CvLocalizationWin32Final Release.dll
PE	 73b0000- 79c4000	Deferred        cvgamedatabasewin32final releaseC:\Program Files\Steam\steamapps\common\sid meier's civilization v\CvGameDatabaseWin32Final Release.dll
PE	 8500000- 86b5000	Deferred        dxdiagn
PE	10000000-101e5000	Deferred        d3dx9_42
PE	3b400000-3b41d000	Deferred        steam_api
ELF	68000000-68140000	Deferred        libwine.so.1
ELF	68140000-68159000	Deferred        libpthread.so.0
ELF	68159000-682b3000	Deferred        libc.so.6
ELF	682b3000-682d9000	Deferred        libm.so.6
ELF	682d9000-682e1000	Deferred        libnss_compat.so.2
ELF	682e1000-682f8000	Deferred        libnsl.so.1
ELF	682f8000-68302000	Deferred        libnss_nis.so.2
ELF	68302000-6830e000	Deferred        libnss_files.so.2
ELF	6830e000-683a3000	Deferred        winmm<elf>
  \-PE	68320000-683a3000	\               winmm
ELF	683a3000-684d5000	Deferred        user32<elf>
  \-PE	683c0000-684d5000	\               user32
ELF	684d5000-68561000	Deferred        gdi32<elf>
  \-PE	684e0000-68561000	\               gdi32
ELF	68561000-685bc000	Deferred        advapi32<elf>
  \-PE	68570000-685bc000	\               advapi32
ELF	685bc000-6861f000	Deferred        shlwapi<elf>
  \-PE	685d0000-6861f000	\               shlwapi
ELF	6861f000-68641000	Deferred        imm32<elf>
  \-PE	68630000-68641000	\               imm32
ELF	68641000-68742000	Deferred        ole32<elf>
  \-PE	68660000-68742000	\               ole32
ELF	68742000-687b7000	Deferred        rpcrt4<elf>
  \-PE	68750000-687b7000	\               rpcrt4
ELF	687b7000-687cd000	Deferred        psapi<elf>
  \-PE	687c0000-687cd000	\               psapi
ELF	687cd000-68826000	Deferred        dbghelp<elf>
  \-PE	687e0000-68826000	\               dbghelp
ELF	68826000-68a0f000	Deferred        shell32<elf>
  \-PE	68840000-68a0f000	\               shell32
ELF	68a0f000-68aca000	Deferred        comdlg32<elf>
  \-PE	68a20000-68aca000	\               comdlg32
ELF	68aca000-68b02000	Deferred        winspool<elf>
  \-PE	68ad0000-68b02000	\               winspool
ELF	68b02000-68bec000	Deferred        oleaut32<elf>
  \-PE	68b20000-68bec000	\               oleaut32
ELF	68bec000-68c05000	Deferred        version<elf>
  \-PE	68bf0000-68c05000	\               version
ELF	68c05000-68c32000	Deferred        ws2_32<elf>
  \-PE	68c10000-68c32000	\               ws2_32
ELF	68c32000-68c66000	Deferred        d3d9<elf>
  \-PE	68c40000-68c66000	\               d3d9
ELF	68c66000-68d9e000	Deferred        wined3d<elf>
  \-PE	68c70000-68d9e000	\               wined3d
ELF	68d9e000-68db3000	Deferred        libz.so.1
ELF	68db3000-68de3000	Deferred        libfontconfig.so.1
ELF	68de3000-68e0a000	Deferred        libexpat.so.1
ELF	68e0a000-68eb2000	Deferred        winex11<elf>
  \-PE	68e20000-68eb2000	\               winex11
ELF	68eb2000-68ebb000	Deferred        libsm.so.6
ELF	68ebb000-68ed4000	Deferred        libice.so.6
ELF	68ed4000-68ff1000	Deferred        libx11.so.6
ELF	68ff1000-68ff6000	Deferred        libuuid.so.1
ELF	68ff6000-69010000	Deferred        libxcb.so.1
ELF	69010000-69014000	Deferred        libxau.so.6
ELF	69014000-6901a000	Deferred        libxdmcp.so.6
ELF	6901a000-6901e000	Deferred        libxinerama.so.1
ELF	6901e000-69024000	Deferred        libxxf86vm.so.1
ELF	69024000-6902e000	Deferred        libxrender.so.1
ELF	6902e000-69036000	Deferred        libxrandr.so.2
ELF	69036000-6903a000	Deferred        libxcomposite.so.1
ELF	6903a000-69040000	Deferred        libxfixes.so.3
ELF	69040000-6904a000	Deferred        libxcursor.so.1
ELF	6904a000-69091000	Deferred        libcups.so.2
ELF	69091000-690c0000	Deferred        libgssapi_krb5.so.2
ELF	690c0000-6915b000	Deferred        libgnutls.so.26
ELF	6915b000-69167000	Deferred        libavahi-common.so.3
ELF	69167000-69178000	Deferred        libavahi-client.so.3
ELF	69178000-69229000	Deferred        libkrb5.so.3
ELF	69229000-6924d000	Deferred        libk5crypto.so.3
ELF	6924d000-69251000	Deferred        libcom_err.so.2
ELF	69251000-69259000	Deferred        libkrb5support.so.0
ELF	69259000-6926d000	Deferred        libresolv.so.2
ELF	6926d000-6927e000	Deferred        libtasn1.so.3
ELF	6927e000-692f1000	Deferred        libgcrypt.so.11
ELF	692f1000-6932a000	Deferred        libdbus-1.so.3
ELF	6932a000-69333000	Deferred        librt.so.1
ELF	69333000-69338000	Deferred        libgpg-error.so.0
ELF	69338000-6934e000	Deferred        wbemprox<elf>
  \-PE	69340000-6934e000	\               wbemprox
ELF	6934e000-693ac000	Deferred        setupapi<elf>
  \-PE	69360000-693ac000	\               setupapi
ELF	693ac000-693f5000	Deferred        dsound<elf>
  \-PE	693b0000-693f5000	\               dsound
ELF	693f5000-694ba000	Deferred        libgl.so.1
ELF	694ba000-6aaca000	Deferred        libglcore.so.1
ELF	6b5e7000-6b604000	Deferred        ld-linux.so.2
ELF	6eddc000-6ee5f000	Deferred        msvcrt<elf>
  \-PE	6edf0000-6ee5f000	\               msvcrt
ELF	6f534000-6f5aa000	Deferred        libfreetype.so.6
ELF	6ffa1000-6ffa5000	Deferred        libkeyutils.so.1
PE	71590000-71617000	Deferred        comctl32
ELF	71629000-7162b000	Deferred        libnvidia-tls.so.1
ELF	71c93000-71ca7000	Deferred        lz32<elf>
  \-PE	71ca0000-71ca7000	\               lz32
ELF	71d23000-71d33000	Deferred        libxext.so.6
ELF	71ff4000-71ff8000	Deferred        libdl.so.2
PE	78480000-7850e000	Deferred        msvcp90
PE	78520000-785c3000	Deferred        msvcr90
ELF	78fbc000-78fe4000	Deferred        winhttp<elf>
  \-PE	78fc0000-78fe4000	\               winhttp
ELF	7b800000-7b976000	Deferred        kernel32<elf>
  \-PE	7b810000-7b976000	\               kernel32
ELF	7bc00000-7bcb9000	Deferred        ntdll<elf>
  \-PE	7bc10000-7bcb9000	\               ntdll
ELF	7bf00000-7bf04000	Deferred        <wine-loader>
Threads:
process  tid      prio (all id:s are in hex)
00000008 (D) C:\Program Files\Steam\steamapps\common\sid meier's civilization v\CivilizationV.exe
	00000009    0 <==
0000000e services.exe
	00000016    0
	00000015    0
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
=>0 0x0079408d in civilizationv (+0x39408d) (0x008edf08)
  1 0x0000000a (0x00203d20)
[email]ben@ben-desktop:~/.wine[/email]/drive_c/Program Files/Steam/steamapps/common/sid meier's civilization v$ 

[EDIT: Looks like others have experienced this too. See "Maxime Thurston on Friday September 24th 2010, 9:29" on this page:
[http://appdb.winehq.org/objectManager.php?sClass=version&iId=21465](http://appdb.winehq.org/objectManager.php?sClass=version&iId=21465) ].

---

### Post by Half-Left on 2010-09-27
Yeah, looks like some patching indeed. I generally don't bother with full games from Steam since it auto patches and may well screw things up using Wine.

I'll have to check Civ5 and see if it's ok myself.

---

### Post by plinydogg on 2010-09-27
I've had great success with most games that I get working (i.e., if they work, they usually don't break subsequently) but you never can be sure...

---

### Post by Half-Left on 2010-09-28
I do actually remember having a similar issue with Civ5 not starting. I reinstalled the vcrun packages and it worked.

---

### Post by plinydogg on 2010-09-28
Didn't work for me :(

---

### Post by mrbryan on 2010-09-28
Just want to report that it worked fantastically well for me on 10.04 once I added the ppa for wine and installed 1.33.  I'm on a dell latitude e6400 with nvidia quadro graphics. The sound did stop working, however.  I created an entry on appdb, too

This was from a DVD install, BTW -- not planning on letting steam interfere

---

### Post by plinydogg on 2010-09-28
Glad it's working for someone, mrbyran! 

I too have added the Wine PPA and have Wine 1.3.3 installed but to no avail. 

I hope I'm not forced to purchase the DVD too(!)

---

### Post by Half-Left on 2010-09-28
You could always remove Wine and then reinstall it with Steam and don't let it auto update, i.e remove the .wine directory or just back it up.

---

### Post by plinydogg on 2010-09-28
I had the same idea and have already tried reinstalling Wine twice!

---

### Post by roggenschrotbrot on 2010-10-01
hi there. i am trying to get civ5 to work. neither steam nor civ are installed via wine atm as my /home drive is lacking enough free space, so i use my windows installation (dvd), which works fine for halflife2 and mount&blade. when i try to run civ5 i get an "incomplete installation (2)" error, so i got a few questions:
[LIST][*]is it possible to fix this without reinstalling either one? 
[*]will reinstalling steam and civ5 to my windows drive via wine fix it without breaking steam when using windows? (that&#8217;s how i install most of win in wine without scarifying drive space)
[*]will a second installation of steam to an other mounted drive via wine fix it?
[/LIST]

---

### Post by parsim on 2010-10-17
Also had "Incomplete installation (2)", and your post gave me an idea... my steamapps directory was a symlink, so I deleted the symlink and moved the steamapps directory over. Voila!

---

### Post by YokoZar on 2010-10-17
> **roggenschrotbrot said:**
> hi there. i am trying to get civ5 to work. neither steam nor civ are installed via wine atm as my /home drive is lacking enough free space, so i use my windows installation (dvd), which works fine for halflife2 and mount&blade. when i try to run civ5 i get an "incomplete installation (2)" error, so i got a few questions:
[LIST][*]is it possible to fix this without reinstalling either one? 
[*]will reinstalling steam and civ5 to my windows drive via wine fix it without breaking steam when using windows? (that’s how i install most of win in wine without scarifying drive space)
[*]will a second installation of steam to an other mounted drive via wine fix it?
[/LIST]

Linking like this works for some apps and doesn't work for others.  A similar thing happens on Windows itself -- some apps only care about the files in their folder, others look for things in the registry and elsewhere on the disk.  That's what the "incomplete" warning most likely is.

Try installing directly into Wine rather than running off the Windows disk.

---

### Post by Losergamer04 on 2010-10-17
I am also having issues with Civ 5.  I've tried uninstalling wine and Civ 5 a number of times and tried the wine configuration change in addition to installing the run times using winetricks.

I have had 2 issues.  One is when it loads the game it doesn't finish; Iit sits at the intro page.  The other is the grey map people have been reporting.

Now I am running it through steam.  And I am using wine 1.3.5 since that's what it updated me to.  I have also tried to installing DX9 via the Micro$oft download.  Thus far I have only made a step backwards, and that was from adding the exception and it broke my audio :(

Soooo, any other ideas?

---

### Post by Newbie_777 on 2010-10-19
I removed Wine a couple of months ago. Now that I have seen that Civilization 5 is out, I am certainly going to try and install it. I have Ubuntu Lucid Lynx 10.04. Which Wine version should I choose? The latest or?

---

### Post by Losergamer04 on 2010-10-19
The most successful people I have heard playing Civ are running 10.04 Ubuntu and 1.3.3 wine.  I'm running 10.10 and 1.3.5 and it "almost" works.

---

### Post by parsim on 2010-10-19
The demo at least works for me on 10.04 with stock Wine, which is 1.1.42. The only problems I see are some cinematics not displaying properly and occasionally the sound dropping out.

Does run a LOT slower than Civ IV, though.

For more user feedback you should probably see here:

[http://appdb.winehq.org/objectManager.php?sClass=application&iId=12117](http://appdb.winehq.org/objectManager.php?sClass=application&iId=12117)

---

### Post by Newbie_777 on 2010-10-20
By "almost" you mean, I guess, you are having problems with sound, video display or slower gameplay? Or does it occasionaly crash?

---

### Post by Hairy_Palms on 2010-10-20
got civ5 here, works fineafter using winetricks to install d3d9 and vcrun2008 no problems other than it sometimes crashes if i change desktop, sounds fine, videos fine. the mod manager doesnt work , it complains about microsoft Bits not running, but thats no big deal, i just download and unzip as you did in civ4 and before

---

### Post by Half-Left on 2010-10-20
Strange. Well I installed Civ5 on my fresh Maverick with Wine 1.3.5 and it just worked and no need to for Wine tricks.

Seems to be smoother as well, especially the cut scenes where you meet a nation leader.

---

### Post by Losergamer04 on 2010-10-21
By almost it's mostly the grey problem.  But after a few clicks and actions in-game with no clue what I am doing it tends to crash.  Audio is working ATM.  I've tried most texture settings and no change.

---

