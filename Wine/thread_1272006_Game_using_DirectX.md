---
title: "Game using DirectX"
date: 2009-09-21
forum: Wine
---

### Post by IamGibby on 2009-09-21
Curious if anyone had a solution for me. I was wondering if I could use a game client I've used for almost 6+ years on Windows on linux through Wine. I know for a fact it requires DirectX, dunno if that is what's causing the issue or not.. the url to the gameclient download is located [here]("http://www.secretsofmirage.com").

(I really only log onto this to talk to the community but the game has it's ups and downs)

any help is greatly appreciated. Thanks.

Chris.

---

### Post by hikaricore on 2009-09-21
DX is included in WINE so you should never install it, there sometimes is a need for an missing dx library to be added but this is rare and only needs to be done on a per game basis.

I checked the WINE appdb and found no mention of your title.

You're going to need to provide much more info for anyone to even attempt assisting you.
Terminal output or any game error messages would be a good place to start.

Also if your game uses any type of rootkit such as game guard you're out of luck.

---

### Post by IamGibby on 2009-09-21
Terminal output when running Wine > Client.exe :

```

wine ~/documents/somx/somx.exe
err:module:import_dll Library MSVBVM60.DLL (which is needed by L"Z:\\home\\chris\\documents\\somx\\somx.exe") not found
err:module:LdrInitializeThunk Main exe initialization for L"Z:\\home\\chris\\documents\\somx\\somx.exe" failed, status c0000135

```

---

### Post by hikaricore on 2009-09-21
You can easily install missing libraries with winetricks: [http://wiki.winehq.org/winetricks](http://wiki.winehq.org/winetricks)

---

### Post by IamGibby on 2009-09-21
Thanks I've gotten that and also downloaded the CABEXTRACT thing too just to be safe, I know how to run that in the console but I'm affraid I'm still learning this entire thing (linux and everything) but I have to say I feel I am catching on pretty quick.. I've looked through the Winetricks for the " MSVBVM60.DLL" and it returned the following:

```

sh winetricks MSVBVM60.DLL
Unknown arg MSVBVM60.DLL
Usage: winetricks [options] package [package] ...
This script can help you prepare your system for Windows applications
that mistakenly assume all users' systems have all the needed
redistributable runtime libraries or fonts.
Some options require the Linux 'cabextract' program.

Options:
 -q         quiet.  You must have already agreed to the EULAs.
 -v         verbose
 -V         display Version
Packages:
 art2kmin      MS Access 2000 runtime.  Requires Access 2000 Dev license!
 atmlib        Adobe Type Manager. Needed for Adobe CS4
 colorprofile  Standard RGB color profile
 comctl32      MS common controls 5.80
 comctl32.ocx  MS comctl32.ocx and mscomctl.ocx, comctl32 wrappers for VB6
 controlpad    MS ActiveX Control Pad
 corefonts     MS Arial, Courier, Times fonts
 cygwin        Unix apps for Windows (needed by some build scripts)
 d3dx9         MS d3dx9_??.dll (from DirectX 9 user redistributable)
 dcom98        MS DCOM (ole32, oleaut32); requires Win98 license!
 dinput8       MS dinput8.dll (from DirectX 9 user redistributable)
 dirac0.8      the obsolete Dirac 0.8 directshow filter
 directplay    MS DirectPlay (from DirectX 9 user redistributable)
 directx9      MS DirectX 9 user redistributable (not recommended! use d3dx9 instead)
 divx          divx video codec
 dotnet11      MS .NET 1.1 (requires Windows license)
 dotnet20      MS .NET 2.0 (requires Windows license)
 dotnet30      MS .NET 3.0 (requires Windows license, does not work yet)
 droid         Droid fonts (on LCD, looks better with fontsmooth-rgb)
 ffdshow       ffdshow video codecs
 flash         Adobe Flash Player ActiveX and firefox plugins
 fm20          MS Forms 2.0 Object Library
 fontfix       Fix bad fonts which cause crash in some apps (e.g. .net).
 fontsmooth-disable    Disables font smoothing
 fontsmooth-gray       Enables grayscale font smoothing
 fontsmooth-rgb        Enables subpixel smoothing for RGB LCDs
 fontsmooth-bgr        Enables subpixel smoothing for BGR LCDs
 gdiplus       MS gdiplus.dll (from powerpoint viewer)
 gecko         The HTML rendering Engine (Mozilla)
 gecko-dbg     The HTML rendering Engine (Mozilla), with debugging symbols
 hosts         Adds empty C:\windows\system32\drivers\etc\{hosts,services} files
 icodecs       Intel Codecs (Indeo)
 jet40         MS Jet 4.0 Service Pack 8
 liberation    Red Hat Liberation fonts (Sans, Serif, Mono)
 mdac25        MS MDAC 2.5: Microsoft ODBC drivers, etc.
 mdac27        MS MDAC 2.7
 mdac28        MS MDAC 2.8
 mfc40         MS mfc40 (Microsoft Foundation Classes from Visual C++ 4)
 mfc42         MS mfc42 (same as vcrun6 below)
 mono20        mono-2.0.1
 mono22        mono-2.2
 mono24        mono-2.4
 msi2          MS Installer 2.0
 mshflxgd      MS Hierarchical Flex Grid Control
 msls31        MS Line Services 3.1 (needed by native riched?)
 msmask        MS Masked Edit Control
 msscript      MS Script Control
 msxml3        MS XML version 3
 msxml4        MS XML version 4
 msxml6        MS XML version 6
 ogg           ogg filters/codecs: flac, theora, speex, vorbis, schroedinger
 ole2          MS 16 bit OLE
 openwatcom    Open Watcom C/C++ compiler (can compile win16 code!)
 pdh           MS pdh.dll (Performance Data Helper)
 psdk2003      MS Platform SDK 2003 (crashes at end, but seems to work)
 psdkvista     MS Vista SDK (does not install yet)
 psdkwin7      MS Windows 7 SDK (does not install yet)
 python26      Python 2.6.2 (and pywin32)
 quicktime72   Apple Quicktime 7.2
 riched20      MS riched20 and riched32
 riched30      MS riched30
 shockwave     Adobe Shockwave Player
 tahoma        MS Tahoma font (not part of corefonts)
 urlmon        MS urlmon.dll
 vb2run        MS Visual Basic 2 runtime
 vb3run        MS Visual Basic 3 runtime
 vb4run        MS Visual Basic 4 runtime
 vb5run        MS Visual Basic 5 runtime
 vb6run        MS Visual Basic 6 runtime
 vc2005trial   MS Visual C++ 2005 Trial
 vc2005express MS Visual C++ 2005 Express
 vcrun6        MS Visual C++ 6 sp4 libraries (mfc42, msvcp60, msvcrt)
 vcrun2003     MS Visual C++ 2003 libraries (mfc71,msvcp71,msvcr71)
 vcrun2005     MS Visual C++ 2005 sp1 libraries (mfc80,msvcp80,msvcr80)
 vcrun2008     MS Visual C++ 2008 libraries (mfc90,msvcp90,msvcr90)
 vjrun20       MS Visual J# 2.0 SE libraries (requires dotnet20)
 wininet       MS wininet.dll (requires Windows license)
 wme9          MS Windows Media Encoder 9 (requires Windows license)
 wmp9          MS Windows Media Player 9 (requires Windows license)
 wmp10         MS Windows Media Player 10 (requires Windows license)
 wenquanyi     WenQuanYi CJK font (on LCD looks better with fontsmooth-rgb)
 wsh56         MS Windows Scripting Host 5.6
 wsh56js       MS Windows scripting 5.6, jscript only, no cscript
 wsh56vb       MS Windows scripting 5.6, vbscript only, no cscript
 xact          MS XACT Engine (x3daudio?_?.dll, xactengine?_?.dll)
 xvid          xvid video codec
Apps:
 autohotkey    Autohotkey (open source gui scripting language)
 firefox       Firefox
 ie6           Microsoft Internet Explorer 6.0
 kde           KDE for Windows installer
 mpc           Media Player Classic
 vlc           VLC media player
Pseudopackages:
 allfonts      All listed fonts (corefonts, tahoma, liberation)
 allcodecs     All listed codecs (xvid, ffdshow, icodecs)
 fakeie6       Set registry to claim IE6sp1 is installed
 native_mdac   Override odbc32 and odbccp32
 native_oleaut32 Override oleaut32
 nt40          Set windows version to nt40
 win98         Set windows version to Windows 98
 win2k         Set windows version to Windows 2000
 winxp         Set windows version to Windows XP
 vista         Set windows version to Windows Vista
 winver=       Set windows version to default (winxp)
 volnum        Rename drive_c to harddiskvolume0 (needed by some installers)

```

---

### Post by hikaricore on 2009-09-21
> **IamGibby said:**
> Thanks I've gotten that and also downloaded the CABEXTRACT thing too just to be safe, I know how to run that in the console but I'm affraid I'm still learning this entire thing (linux and everything) but I have to say I feel I am catching on pretty quick.. I've looked through the Winetricks for the "_MS**VB**VM**6**0.DLL_" and it returned the following:

```

** vb6run        MS Visual Basic 6 runtime**

```

I think you overlooked the obvious.  :)

---

### Post by IamGibby on 2009-09-21
> **hikaricore said:**
> I think you overlooked the obvious.  :)

:oops:...hey hey hey now, I never claimed to be smart!

(Thanks going to try this, i'll post my results)

Chris.

---

### Post by IamGibby on 2009-09-21
Double posting to create a new post icon instead of editing --several hours later:

So I've made it another step and got the client to actually execute uptill the update installer section, which is another exe in the client.. it executes it just fine and attempts to connect/start downloading but hangs.. any suggestions as to why?

```

fixme:ole:OLEPictureImpl_FindConnectionPoint no connection point for {33ad4f92-6699-11cf-b70c-00aa0060d393}
fixme:ole:OLEPictureImpl_FindConnectionPoint no connection point for {33ad4ed2-6699-11cf-b70c-00aa0060d393}
fixme:ole:OLEPictureImpl_FindConnectionPoint no connection point for {33ad4f92-6699-11cf-b70c-00aa0060d393}
fixme:ole:OLEPictureImpl_FindConnectionPoint no connection point for {33ad4f92-6699-11cf-b70c-00aa0060d393}
fixme:ole:OLEPictureImpl_FindConnectionPoint no connection point for {33ad4ed2-6699-11cf-b70c-00aa0060d393}
fixme:ole:OLEPictureImpl_FindConnectionPoint no connection point for {33ad4f92-6699-11cf-b70c-00aa0060d393}
fixme:ole:OLEPictureImpl_FindConnectionPoint no connection point for {33ad4ed2-6699-11cf-b70c-00aa0060d393}
fixme:ole:OLEPictureImpl_FindConnectionPoint no connection point for {33ad4ed2-6699-11cf-b70c-00aa0060d393}
fixme:ole:OLEPictureImpl_FindConnectionPoint no connection point for {33ad4ed2-6699-11cf-b70c-00aa0060d393}
fixme:ole:OLEPictureImpl_FindConnectionPoint no connection point for {33ad4f92-6699-11cf-b70c-00aa0060d393}
fixme:ole:OLEPictureImpl_FindConnectionPoint no connection point for {33ad4ed2-6699-11cf-b70c-00aa0060d393}
fixme:ole:OLEPictureImpl_FindConnectionPoint no connection point for {33ad4ed2-6699-11cf-b70c-00aa0060d393}
fixme:ole:OLEPictureImpl_FindConnectionPoint no connection point for {33ad4ed2-6699-11cf-b70c-00aa0060d393}
fixme:ole:OLEPictureImpl_FindConnectionPoint no connection point for {33ad4f92-6699-11cf-b70c-00aa0060d393}
fixme:ole:OLEPictureImpl_FindConnectionPoint no connection point for {33ad4f92-6699-11cf-b70c-00aa0060d393}
fixme:ole:OLEPictureImpl_FindConnectionPoint no connection point for {33ad4ed2-6699-11cf-b70c-00aa0060d393}
fixme:ole:OLEPictureImpl_FindConnectionPoint no connection point for {33ad4f92-6699-11cf-b70c-00aa0060d393}
fixme:ole:OLEPictureImpl_FindConnectionPoint no connection point for {33ad4f92-6699-11cf-b70c-00aa0060d393}
fixme:ole:OLEPictureImpl_FindConnectionPoint no connection point for {33ad4ed2-6699-11cf-b70c-00aa0060d393}
fixme:ole:OLEPictureImpl_FindConnectionPoint no connection point for {33ad4ed2-6699-11cf-b70c-00aa0060d393}
fixme:ole:OLEPictureImpl_FindConnectionPoint no connection point for {33ad4ed2-6699-11cf-b70c-00aa0060d393}
fixme:ole:OLEPictureImpl_FindConnectionPoint no connection point for {33ad4ed2-6699-11cf-b70c-00aa0060d393}
fixme:ole:OLEPictureImpl_FindConnectionPoint no connection point for {33ad4f92-6699-11cf-b70c-00aa0060d393}
fixme:ole:OLEPictureImpl_FindConnectionPoint no connection point for {33ad4ed2-6699-11cf-b70c-00aa0060d393}
fixme:ole:OLEPictureImpl_FindConnectionPoint no connection point for {33ad4ed2-6699-11cf-b70c-00aa0060d393}
fixme:ole:OLEPictureImpl_FindConnectionPoint no connection point for {33ad4ed2-6699-11cf-b70c-00aa0060d393}
fixme:ole:OLEPictureImpl_FindConnectionPoint no connection point for {33ad4ed2-6699-11cf-b70c-00aa0060d393}
fixme:ole:OLEPictureImpl_FindConnectionPoint no connection point for {33ad4f92-6699-11cf-b70c-00aa0060d393}
fixme:ole:OLEPictureImpl_FindConnectionPoint no connection point for {33ad4ed2-6699-11cf-b70c-00aa0060d393}
fixme:ole:OLEPictureImpl_FindConnectionPoint no connection point for {33ad4ed2-6699-11cf-b70c-00aa0060d393}
fixme:ole:OLEPictureImpl_FindConnectionPoint no connection point for {33ad4f92-6699-11cf-b70c-00aa0060d393}
fixme:ole:OLEPictureImpl_FindConnectionPoint no connection point for {33ad4f92-6699-11cf-b70c-00aa0060d393}
fixme:ole:OLEPictureImpl_FindConnectionPoint no connection point for {33ad4f92-6699-11cf-b70c-00aa0060d393}
fixme:ole:OLEPictureImpl_FindConnectionPoint no connection point for {33ad4ed2-6699-11cf-b70c-00aa0060d393}
fixme:ole:OLEPictureImpl_FindConnectionPoint no connection point for {33ad4ed2-6699-11cf-b70c-00aa0060d393}
fixme:ole:OLEPictureImpl_FindConnectionPoint no connection point for {33ad4f92-6699-11cf-b70c-00aa0060d393}
fixme:ole:OLEPictureImpl_FindConnectionPoint no connection point for {33ad4f92-6699-11cf-b70c-00aa0060d393}
fixme:ole:OLEPictureImpl_FindConnectionPoint no connection point for {33ad4f92-6699-11cf-b70c-00aa0060d393}
fixme:ole:OLEPictureImpl_FindConnectionPoint no connection point for {33ad4f92-6699-11cf-b70c-00aa0060d393}
fixme:ole:OLEPictureImpl_FindConnectionPoint no connection point for {33ad4f92-6699-11cf-b70c-00aa0060d393}
fixme:ole:OLEPictureImpl_FindConnectionPoint no connection point for {33ad4f92-6699-11cf-b70c-00aa0060d393}
fixme:ole:OLEPictureImpl_FindConnectionPoint no connection point for {33ad4f92-6699-11cf-b70c-00aa0060d393}
fixme:ole:OLEPictureImpl_FindConnectionPoint no connection point for {33ad4f92-6699-11cf-b70c-00aa0060d393}
fixme:ole:OLEPictureImpl_FindConnectionPoint no connection point for {33ad4ed2-6699-11cf-b70c-00aa0060d393}
fixme:ole:OLEPictureImpl_FindConnectionPoint no connection point for {33ad4f92-6699-11cf-b70c-00aa0060d393}
fixme:ole:OLEPictureImpl_FindConnectionPoint no connection point for {33ad4f92-6699-11cf-b70c-00aa0060d393}
fixme:ole:OLEPictureImpl_FindConnectionPoint no connection point for {33ad4ed2-6699-11cf-b70c-00aa0060d393}
fixme:ole:OLEPictureImpl_FindConnectionPoint no connection point for {33ad4ed2-6699-11cf-b70c-00aa0060d393}
fixme:ole:OLEPictureImpl_FindConnectionPoint no connection point for {33ad4f92-6699-11cf-b70c-00aa0060d393}
fixme:ole:OLEPictureImpl_FindConnectionPoint no connection point for {33ad4f92-6699-11cf-b70c-00aa0060d393}
fixme:ole:OLEPictureImpl_FindConnectionPoint no connection point for {33ad4ed2-6699-11cf-b70c-00aa0060d393}
fixme:ole:OLEPictureImpl_FindConnectionPoint no connection point for {33ad4ed2-6699-11cf-b70c-00aa0060d393}
fixme:ole:OLEPictureImpl_FindConnectionPoint no connection point for {33ad4ed2-6699-11cf-b70c-00aa0060d393}
fixme:ole:OLEPictureImpl_FindConnectionPoint no connection point for {33ad4f92-6699-11cf-b70c-00aa0060d393}
fixme:ole:OLEPictureImpl_FindConnectionPoint no connection point for {33ad4ed2-6699-11cf-b70c-00aa0060d393}
fixme:ole:OLEPictureImpl_FindConnectionPoint no connection point for {33ad4ed2-6699-11cf-b70c-00aa0060d393}
fixme:ole:OLEPictureImpl_FindConnectionPoint no connection point for {33ad4ed2-6699-11cf-b70c-00aa0060d393}
fixme:ole:OLEPictureImpl_FindConnectionPoint no connection point for {33ad4ed2-6699-11cf-b70c-00aa0060d393}
fixme:ole:OLEPictureImpl_FindConnectionPoint no connection point for {33ad4f92-6699-11cf-b70c-00aa0060d393}
fixme:ole:OLEPictureImpl_FindConnectionPoint no connection point for {33ad4f92-6699-11cf-b70c-00aa0060d393}
fixme:ole:OLEPictureImpl_FindConnectionPoint no connection point for {33ad4ed2-6699-11cf-b70c-00aa0060d393}
fixme:ole:OLEPictureImpl_FindConnectionPoint no connection point for {33ad4ed2-6699-11cf-b70c-00aa0060d393}
fixme:ole:OLEPictureImpl_FindConnectionPoint no connection point for {33ad4ed2-6699-11cf-b70c-00aa0060d393}
fixme:ole:OLEPictureImpl_FindConnectionPoint no connection point for {33ad4ed2-6699-11cf-b70c-00aa0060d393}
fixme:ole:OLEPictureImpl_FindConnectionPoint no connection point for {33ad4ed2-6699-11cf-b70c-00aa0060d393}
fixme:ole:OLEPictureImpl_FindConnectionPoint no connection point for {33ad4ed2-6699-11cf-b70c-00aa0060d393}
fixme:ole:OLEPictureImpl_FindConnectionPoint no connection point for {33ad4ed2-6699-11cf-b70c-00aa0060d393}
fixme:ole:OLEPictureImpl_FindConnectionPoint no connection point for {33ad4ed2-6699-11cf-b70c-00aa0060d393}
fixme:ole:OLEPictureImpl_FindConnectionPoint no connection point for {33ad4ed2-6699-11cf-b70c-00aa0060d393}
fixme:ole:OLEPictureImpl_FindConnectionPoint no connection point for {33ad4f92-6699-11cf-b70c-00aa0060d393}
fixme:ole:OLEPictureImpl_FindConnectionPoint no connection point for {33ad4f92-6699-11cf-b70c-00aa0060d393}
fixme:ole:OLEPictureImpl_FindConnectionPoint no connection point for {33ad4ed2-6699-11cf-b70c-00aa0060d393}
fixme:ole:OLEPictureImpl_FindConnectionPoint no connection point for {33ad4ed2-6699-11cf-b70c-00aa0060d393}
fixme:ole:OLEPictureImpl_FindConnectionPoint no connection point for {33ad4f92-6699-11cf-b70c-00aa0060d393}
fixme:ole:OLEPictureImpl_FindConnectionPoint no connection point for {33ad4f92-6699-11cf-b70c-00aa0060d393}
fixme:ole:OLEPictureImpl_FindConnectionPoint no connection point for {33ad4ed2-6699-11cf-b70c-00aa0060d393}
fixme:ole:OLEPictureImpl_FindConnectionPoint no connection point for {33ad4ed2-6699-11cf-b70c-00aa0060d393}
fixme:ole:OLEPictureImpl_FindConnectionPoint no connection point for {33ad4f92-6699-11cf-b70c-00aa0060d393}
fixme:ole:OLEPictureImpl_FindConnectionPoint no connection point for {33ad4f92-6699-11cf-b70c-00aa0060d393}
fixme:ole:OLEPictureImpl_FindConnectionPoint no connection point for {33ad4f92-6699-11cf-b70c-00aa0060d393}
fixme:ole:OLEPictureImpl_FindConnectionPoint no connection point for {33ad4f92-6699-11cf-b70c-00aa0060d393}
fixme:ole:OLEPictureImpl_FindConnectionPoint no connection point for {33ad4f92-6699-11cf-b70c-00aa0060d393}
fixme:ole:OLEPictureImpl_FindConnectionPoint no connection point for {33ad4f92-6699-11cf-b70c-00aa0060d393}
fixme:ole:OLEPictureImpl_FindConnectionPoint no connection point for {33ad4f92-6699-11cf-b70c-00aa0060d393}
fixme:ole:OLEPictureImpl_FindConnectionPoint no connection point for {33ad4ed2-6699-11cf-b70c-00aa0060d393}
fixme:ole:OLEPictureImpl_FindConnectionPoint no connection point for {33ad4ed2-6699-11cf-b70c-00aa0060d393}
fixme:ole:OLEPictureImpl_FindConnectionPoint no connection point for {33ad4ed2-6699-11cf-b70c-00aa0060d393}
fixme:ole:OLEPictureImpl_FindConnectionPoint no connection point for {33ad4f92-6699-11cf-b70c-00aa0060d393}
fixme:ole:OLEPictureImpl_FindConnectionPoint no connection point for {33ad4ed2-6699-11cf-b70c-00aa0060d393}
fixme:ole:OLEPictureImpl_FindConnectionPoint no connection point for {33ad4ed2-6699-11cf-b70c-00aa0060d393}
fixme:ole:OLEPictureImpl_FindConnectionPoint no connection point for {33ad4ed2-6699-11cf-b70c-00aa0060d393}
fixme:ole:OLEPictureImpl_FindConnectionPoint no connection point for {33ad4ed2-6699-11cf-b70c-00aa0060d393}
fixme:ole:OLEPictureImpl_FindConnectionPoint no connection point for {33ad4ed2-6699-11cf-b70c-00aa0060d393}
fixme:ole:OLEPictureImpl_FindConnectionPoint no connection point for {33ad4ed2-6699-11cf-b70c-00aa0060d393}
fixme:ole:OLEPictureImpl_FindConnectionPoint no connection point for {33ad4ed2-6699-11cf-b70c-00aa0060d393}
fixme:ole:OLEPictureImpl_FindConnectionPoint no connection point for {33ad4f92-6699-11cf-b70c-00aa0060d393}
fixme:ole:OLEPictureImpl_FindConnectionPoint no connection point for {33ad4ed2-6699-11cf-b70c-00aa0060d393}
fixme:ole:OLEPictureImpl_FindConnectionPoint no connection point for {33ad4f92-6699-11cf-b70c-00aa0060d393}
fixme:ole:OLEPictureImpl_FindConnectionPoint no connection point for {33ad4f92-6699-11cf-b70c-00aa0060d393}
fixme:ole:OLEPictureImpl_FindConnectionPoint no connection point for {33ad4f92-6699-11cf-b70c-00aa0060d393}
fixme:ole:OLEPictureImpl_FindConnectionPoint no connection point for {33ad4ed2-6699-11cf-b70c-00aa0060d393}
fixme:ole:OLEPictureImpl_FindConnectionPoint no connection point for {33ad4ed2-6699-11cf-b70c-00aa0060d393}
fixme:ole:OLEPictureImpl_FindConnectionPoint no connection point for {33ad4ed2-6699-11cf-b70c-00aa0060d393}
fixme:ole:OLEPictureImpl_FindConnectionPoint no connection point for {33ad4ed2-6699-11cf-b70c-00aa0060d393}
fixme:ole:OLEPictureImpl_FindConnectionPoint no connection point for {33ad4ed2-6699-11cf-b70c-00aa0060d393}
fixme:ole:OLEPictureImpl_FindConnectionPoint no connection point for {33ad4ed2-6699-11cf-b70c-00aa0060d393}
fixme:ole:OLEPictureImpl_FindConnectionPoint no connection point for {33ad4ed2-6699-11cf-b70c-00aa0060d393}
fixme:ole:OLEPictureImpl_FindConnectionPoint no connection point for {33ad4ed2-6699-11cf-b70c-00aa0060d393}
fixme:ole:OLEPictureImpl_FindConnectionPoint no connection point for {33ad4ed2-6699-11cf-b70c-00aa0060d393}
fixme:ole:OLEPictureImpl_FindConnectionPoint no connection point for {33ad4ed2-6699-11cf-b70c-00aa0060d393}
fixme:ole:OLEPictureImpl_FindConnectionPoint no connection point for {33ad4ed2-6699-11cf-b70c-00aa0060d393}
fixme:ole:OLEPictureImpl_FindConnectionPoint no connection point for {33ad4ed2-6699-11cf-b70c-00aa0060d393}
fixme:ole:OLEPictureImpl_FindConnectionPoint no connection point for {33ad4ed2-6699-11cf-b70c-00aa0060d393}
fixme:ole:OLEPictureImpl_FindConnectionPoint no connection point for {33ad4ed2-6699-11cf-b70c-00aa0060d393}
fixme:ole:OLEPictureImpl_FindConnectionPoint no connection point for {33ad4ed2-6699-11cf-b70c-00aa0060d393}
fixme:richedit:IRichEditOle_fnInPlaceDeactivate stub 0x16c3320
fixme:richedit:IRichEditOle_fnInPlaceDeactivate stub 0x16c3db8
fixme:richedit:IRichEditOle_fnInPlaceDeactivate stub 0x16c4850
fixme:richedit:IRichEditOle_fnInPlaceDeactivate stub 0x16c52e8
fixme:richedit:IRichEditOle_fnInPlaceDeactivate stub 0x16c5d80
fixme:richedit:IRichEditOle_fnInPlaceDeactivate stub 0x16c6818
fixme:richedit:IRichEditOle_fnInPlaceDeactivate stub 0x16c72b0
fixme:richedit:IRichEditOle_fnInPlaceDeactivate stub 0x16c7d48
fixme:richedit:IRichEditOle_fnInPlaceDeactivate stub 0x16c87e0
fixme:richedit:IRichEditOle_fnInPlaceDeactivate stub 0x16c9278
fixme:richedit:IRichEditOle_fnInPlaceDeactivate stub 0x16c9d10
fixme:richedit:IRichEditOle_fnInPlaceDeactivate stub 0x16c9d10
fixme:richedit:IRichEditOle_fnInPlaceDeactivate stub 0x16ca7a8
chris@Gibson:~$ fixme:ole:OleLoadPictureEx (0xa5e9ac,54868,1,{7bf80980-bf32-101a-8bbb-00aa00300cab},x=0,y=0,f=0,0x33faf0), partially implemented.
fixme:ole:OleLoadPictureEx (0xa5e9ac,3646,0,{7bf80980-bf32-101a-8bbb-00aa00300cab},x=0,y=0,f=0,0x33faf0), partially implemented.
fixme:ole:OleLoadPictureEx (0xa5e9ac,3161,1,{7bf80980-bf32-101a-8bbb-00aa00300cab},x=0,y=0,f=0,0x33fac0), partially implemented.
fixme:ole:OleLoadPictureEx (0xa5e9ac,2126,1,{7bf80980-bf32-101a-8bbb-00aa00300cab},x=0,y=0,f=0,0x33fac0), partially implemented.
fixme:ole:OleLoadPictureEx (0xa5e9ac,1835,1,{7bf80980-bf32-101a-8bbb-00aa00300cab},x=0,y=0,f=0,0x33fac0), partially implemented.
fixme:ole:OleLoadPictureEx (0xa5e9ac,2126,1,{7bf80980-bf32-101a-8bbb-00aa00300cab},x=0,y=0,f=0,0x33fac0), partially implemented.
fixme:ole:OleLoadPictureEx (0xa5e9ac,1915,1,{7bf80980-bf32-101a-8bbb-00aa00300cab},x=0,y=0,f=0,0x33fac0), partially implemented.
fixme:ole:OleLoadPictureEx (0xa5e9ac,2233,1,{7bf80980-bf32-101a-8bbb-00aa00300cab},x=0,y=0,f=0,0x33fac0), partially implemented.
fixme:ole:OleLoadPictureEx (0xa5e9ac,2633,1,{7bf80980-bf32-101a-8bbb-00aa00300cab},x=0,y=0,f=0,0x33fac0), partially implemented.
fixme:ole:OleLoadPictureEx (0xa5e9ac,3161,1,{7bf80980-bf32-101a-8bbb-00aa00300cab},x=0,y=0,f=0,0x33fac0), partially implemented.
fixme:ole:OLEPictureImpl_SaveAsFile (0x139f88)->(0x151778, 0, (nil)), hacked stub.
fixme:urlmon:ObtainUserAgentString (0, 0x33e723, 0x33e714): stub
fixme:urlmon:ObtainUserAgentString (0, 0x1c55b0, 0x33e714): stub
fixme:wininet:InternetLockRequestFile STUB

```

Note: This is the last part of the terminal output that comes in result of the update starting (or trying to)

Thanks in advance.

Chris

---

### Post by IamGibby on 2009-09-22
Anyone?

Chris.

---

