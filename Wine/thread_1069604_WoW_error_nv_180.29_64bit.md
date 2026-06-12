---
title: "WoW error nv 180.29 64bit"
date: 2009-02-14
forum: Wine
---

### Post by panaut0lordv on 2009-02-14
Anybody gets this error too? For me WoW was working fine before I've mass updated system.

Jaunty 9.04
```
panaut0lordv@panaut0lordv:~/Gry/World of Warcraft$ wine WoW.exe -opengl
fixme:mixer:ALSA_MixerInit No master control found on SAA7134, disabling mixer
NVIDIA: could not open the device file /dev/nvidiactl (Permission denied).
fixme:advapi:SetSecurityInfo stub
archive Data\enGB\patch-enGB.MPQ opened
archive Data\patch.MPQ opened
archive Data\enGB\patch-enGB-2.MPQ opened
archive Data\patch-2.MPQ opened
archive Data\expansion.MPQ opened
archive Data\lichking.MPQ opened
archive Data\common.MPQ opened
archive Data\common-2.MPQ opened
archive Data\enGB\locale-enGB.MPQ opened
archive Data\enGB\speech-enGB.MPQ opened
archive Data\enGB\expansion-locale-enGB.MPQ opened
archive Data\enGB\lichking-locale-enGB.MPQ opened
archive Data\enGB\expansion-speech-enGB.MPQ opened
archive Data\enGB\lichking-speech-enGB.MPQ opened
fixme:powrprof:DllMain (0x7dda0000, 1, (nil)) not fully implemented
fixme:ntdll:NtPowerInformation Unimplemented NtPowerInformation action: 11
fixme:powrprof:DllMain (0x7dda0000, 0, (nil)) not fully implemented
fixme:win:EnumDisplayDevicesW ((null),0,0x39edbc,0x00000000), stub!
NVIDIA: could not open the device file /dev/nvidiactl (Permission denied).
fixme:win:EnumDisplayDevicesW ((null),0,0x39ebe0,0x00000000), stub!
```

And WoW error log
```
==============================================================================
World of WarCraft (build 9551)

Exe:      Z:\home\panaut0lordv\Gry\World of Warcraft\WoW.exe
Time:     Feb 14, 2009  1:18:06.623 PM
User:     panaut0lordv
Computer: panaut0lordv
------------------------------------------------------------------------------

This application has encountered a critical error:

ERROR #132 (0x85100084) Fatal Exception
Program:	Z:\home\panaut0lordv\Gry\World of Warcraft\WoW.exe
Exception:	0xC0000005 (ACCESS_VIOLATION) at 0023:00000000

The instruction at "0x00000000" referenced memory at "0x00000000".
The memory could not be "written".


WoWBuild: 9551
Settings: 
SET readTOS "-1"
SET readEULA "-1"
SET readScanning "-1"
SET readContest "-1"
SET readTerminationWithoutNotice "-1"
SET installType "Retail"
SET checkAddonVersion "1"
SET locale "enGB"
SET expansionMovie "1"
SET movie "1"
SET showToolsUI "1"
SET portal "eu"
SET realmList "eu.logon.worldofwarcraft.com"
SET patchlist "eu.version.worldofwarcraft.com"
SET coresDetected "1"
------------------------------------------------------------------------------

----------------------------------------
    x86 Registers
----------------------------------------

EAX=00000000  EBX=7E7DFFF4  ECX=0039EAD8  EDX=00000001  ESI=7E7E0E30
EDI=7E7C3CE0  EBP=0039EAEC  ESP=0039EA00  EIP=00000000  FLG=00010246
CS =0023      DS =002B      ES =002B      SS =002B      FS =0063      GS =006B


----------------------------------------
    Stack Trace (Manual)
----------------------------------------

Address  Frame    Logical addr  Module

Showing 1/1 threads...

--- Thread ID: 71 [Current Thread] ---
00000000 0039EAEC 0000:00000000 Z:\home\panaut0lordv\Gry\World of Warcraft\WoW.exe
7E72CCF7 0039F0AC 0001:0005BCF7 C:\windows\system32\wined3d.dll
7E7B1B52 0039F0DC 0001:000E0B52 C:\windows\system32\wined3d.dll
7E7F83C0 0039F10C 0001:000073C0 C:\windows\system32\d3d9.dll
005DE85A 0039F120 0001:001DD85A Z:\home\panaut0lordv\Gry\World of Warcraft\WoW.exe
005D96C7 0039F738 0001:001D86C7 Z:\home\panaut0lordv\Gry\World of Warcraft\WoW.exe
006A3492 0039FB64 0001:002A2492 Z:\home\panaut0lordv\Gry\World of Warcraft\WoW.exe
0069F3D0 0039FC10 0001:0029E3D0 Z:\home\panaut0lordv\Gry\World of Warcraft\WoW.exe
004066F0 0039FE5C 0001:000056F0 Z:\home\panaut0lordv\Gry\World of Warcraft\WoW.exe
004068D7 0039FE6C 0001:000058D7 Z:\home\panaut0lordv\Gry\World of Warcraft\WoW.exe
00406958 0039FF08 0001:00005958 Z:\home\panaut0lordv\Gry\World of Warcraft\WoW.exe
7B879428 0039FFE8 0001:00058428 C:\windows\system32\KERNEL32.dll

----------------------------------------
    Stack Trace (Using DBGHELP.DLL)
----------------------------------------

Showing 1/1 threads...

--- Thread ID: 71 [Current Thread] ---
7E72CCF7 wined3d.dll  InitAdapters+58103 (0x00000000,0x00110000,0x0000000A,0x7BC34C41)
7E7B1B52 wined3d.dll  WineDirect3DCreate+34 (0x00000009,0x0013CF50,0x00000010,0x7B869E0D)
7E7F83C0 d3d9.dll     Direct3DCreate9+112 (0x00000020,0x00000000,0x00000000,0x0039F738)
005DE85A WoW.exe      <unknown symbol>+0 (0x0039F730,0x0039F734,0x011F2638,0x011F263A)
005D96C7 WoW.exe      <unknown symbol>+0 (0x011F2638,0x011F263A,0x011F263C,0x011F2640)
006A3492 WoW.exe      <unknown symbol>+0 (0x011F2638,0x011F2949,0x00973CA0,0x00973CAC)
0069F3D0 WoW.exe      <unknown symbol>+0 (0x0039FC24,0x00000001,0x00000001,0x6C726F57)
004066F0 WoW.exe      <unknown symbol>+0 (0x00000001,0x00000001,0x0039FF08,0x00406958)
004068D7 WoW.exe      <unknown symbol>+0 (0x0040ABB9,0x00400000,0x00000000,0x00111AC0)
00406958 WoW.exe      <unknown symbol>+0 (0x7FFDF000,0x00000000,0x00000000,0x00000000)
7B879428 KERNEL32.dll <unknown symbol>+0 (0x00000000,0x00000000,0x00000000,0x00000000)
F7E9AD77              wine_switch_to_stack+23 (0x00000000,0x00000000,0x00000000,0x00000000)


----------------------------------------
    Loaded Modules
----------------------------------------

0x00400000 - 0x01391000  Z:\home\panaut0lordv\Gry\World of Warcraft\WoW.exe
0x10000000 - 0x10069000  Z:\home\panaut0lordv\Gry\World of Warcraft\DivxDecoder.dll
0x7B820000 - 0x7B940000  C:\windows\system32\KERNEL32.dll
0x7BC10000 - 0x7BCB1000  C:\windows\system32\ntdll.dll
0x7CCF0000 - 0x7CD30000  C:\windows\system32\dbghelp.dll
0x7DDA0000 - 0x7DDB1000  C:\windows\system32\psapi.dll
0x7DDE0000 - 0x7DE08000  C:\windows\system32\uxtheme.dll
0x7DE40000 - 0x7DE45000  C:\windows\system32\midimap.dll
0x7DF20000 - 0x7DF29000  C:\windows\system32\msacm32.drv
0x7DF30000 - 0x7DF60000  C:\windows\system32\winealsa.drv
0x7DFC0000 - 0x7E045000  C:\windows\system32\winex11.drv
0x7E1A0000 - 0x7E1FB000  C:\windows\system32\rpcrt4.dll
0x7E220000 - 0x7E30D000  C:\windows\system32\ole32.dll
0x7E310000 - 0x7E336000  C:\windows\system32\msacm32.dll
0x7E340000 - 0x7E363000  C:\windows\system32\ws2_32.dll
0x7E370000 - 0x7E42A000  C:\windows\system32\comctl32.dll
0x7E440000 - 0x7E5B4000  C:\windows\system32\shell32.dll
0x7E5C0000 - 0x7E611000  C:\windows\system32\shlwapi.dll
0x7E620000 - 0x7E634000  C:\windows\system32\mpr.dll
0x7E640000 - 0x7E685000  C:\windows\system32\wininet.dll
0x7E690000 - 0x7E6A6000  C:\windows\system32\imm32.dll
0x7E6B0000 - 0x7E6C1000  C:\windows\system32\version.dll
0x7E6D0000 - 0x7E7E3000  C:\windows\system32\wined3d.dll
0x7E7F0000 - 0x7E814000  C:\windows\system32\d3d9.dll
0x7EA10000 - 0x7EA86000  C:\windows\system32\opengl32.dll
0x7EA90000 - 0x7EADB000  C:\windows\system32\advapi32.dll
0x7EAF0000 - 0x7EB7C000  C:\windows\system32\gdi32.dll
0x7EBA0000 - 0x7ECCA000  C:\windows\system32\user32.dll
0x7ECE0000 - 0x7ED5E000  C:\windows\system32\winmm.dll
0x7EFF0000 - 0x7EFFE000  C:\windows\system32\lz32.dll


----------------------------------------
    Memory Dump
----------------------------------------

Code: 16 bytes starting at (EIP = 00000000)

00000000: <can't read from this address>


Stack: 1024 bytes starting at (ESP = 0039EA00)

* = addr  **                                                  *               
0039EA00: B0 DF 71 7E  01 00 00 00  D8 EA 39 00  58 80 00 00  ..q~......9.X...
0039EA10: 04 00 00 00  04 00 00 00  00 00 00 00  E1 80 00 00  ................
0039EA20: 67 83 00 00  00 00 00 00  2D 20 00 00  00 01 00 00  g.......- ......
0039EA30: A6 68 8A 7E  01 00 00 00  72 38 00 00  01 00 00 00  .h.~....r8......
0039EA40: 7C B7 FF 7D  68 EA 39 00  3A 1C C6 7E  E0 DD CA 7D  |..}h.9.:..~...}
0039EA50: E0 DD CA 7D  2D 20 00 00  00 01 00 00  EC EA 39 00  ...}- ........9.
0039EA60: AF 42 C3 7B  E0 DD CA 7D  F4 CF 03 7E  7C EA 39 00  .B.{...}...~|.9.
0039EA70: 80 42 01 7E  A0 08 04 7E  DC EA 39 00  D8 EA 39 00  .B.~...~..9...9.
0039EA80: 95 C3 FF 7D  E0 DD CA 7D  00 01 00 00  30 0E 7E 7E  ...}...}....0.~~
0039EA90: DC EA 39 00  54 00 11 00  00 00 00 00  C0 16 00 00  ..9.T...........
0039EAA0: DC 12 7C 7E  F4 FF C6 7E  E0 EB 39 00  EC EA 39 00  ..|~...~..9...9.
0039EAB0: 50 97 C1 7E  FE 2B 03 7E  A4 04 04 7E  E0 4B 03 7E  P..~.+.~...~.K.~
0039EAC0: B5 2B 03 7E  01 00 00 00  54 E3 13 00  00 00 00 00  .+.~....T.......
0039EAD0: 00 00 00 00  04 00 00 00  70 00 00 00  01 00 00 00  ........p.......
0039EAE0: F4 FF 7D 7E  00 00 00 00  18 00 00 00  AC F0 39 00  ..}~..........9.
0039EAF0: F7 CC 72 7E  20 03 00 00  70 00 00 00  00 00 00 00  ..r~ ...p.......
0039EB00: 01 00 00 00  88 EF 39 00  8C EF 39 00  65 64 62 30  ......9...9.edb0
0039EB10: 01 00 00 00  01 00 00 00  5C F1 39 00  C6 60 C4 7B  ........\.9..`.{
0039EB20: E0 87 D6 F7  14 FD CA 7B  1F E0 DA 7D  18 00 00 00  .......{...}....
0039EB30: 14 FD CA 7B  C0 12 04 7E  00 0B 7E 7E  4B 3B 7C 7E  ...{...~..~~K;|~
0039EB40: 34 FC 7B 7E  A0 99 7D 7E  00 0B 7E 7E  4B 3B 7C 7E  4.{~..}~..~~K;|~
0039EB50: E7 10 7C 7E  78 EB 39 00  8F 99 D6 F7  9C EB 39 00  ..|~x.9.......9.
0039EB60: D4 84 D6 F7  E7 00 CB 7B  DB 9A D3 F7  F4 8F E5 F7  .......{........
0039EB70: 4B 3B 7C 7E  84 34 7C 7E  60 34 7C 7E  F6 13 7C 7E  K;|~.4|~`4|~..|~
0039EB80: 80 EF 39 00  F0 0A 7E 7E  06 3B 7C 7E  D8 34 7C 7E  ..9...~~.;|~.4|~
0039EB90: 9C EF 39 00  8C EF 39 00  88 EF 39 00  78 EF 39 00  ..9...9...9.x.9.
0039EBA0: 50 EF 39 00  28 EF 39 00  80 0D 7E 7E  4C 0E 7E 7E  P.9.(.9...~~L.~~
0039EBB0: 30 0E 7E 7E  68 18 7E 7E  84 1C 7E 7E  20 03 00 00  0.~~h.~~..~~ ...
0039EBC0: 55 00 00 00  0A 00 00 00  48 3D D0 7D  2D 1B 7C 7E  U.......H=.}-.|~
0039EBD0: A0 9D 7D 7E  6D 46 00 00  9C B5 D5 7D  9F 12 04 7E  ..}~mF.....}...~
0039EBE0: 48 03 00 00  5C 00 5C 00  2E 00 5C 00  44 00 49 00  H...\.\...\.D.I.
0039EBF0: 53 00 50 00  4C 00 41 00  59 00 31 00  00 00 DA 7D  S.P.L.A.Y.1....}
0039EC00: 00 00 00 00  00 00 00 00  00 00 00 00  D4 D9 E9 F7  ................
0039EC10: 50 F3 39 00  C0 FF FF FF  00 00 00 00  E1 75 E9 F7  P.9..........u..
0039EC20: 00 F2 39 00  58 00 31 00  31 00 20 00  57 00 69 00  ..9.X.1.1. .W.i.
0039EC30: 6E 00 64 00  6F 00 77 00  69 00 6E 00  67 00 20 00  n.d.o.w.i.n.g. .
0039EC40: 53 00 79 00  73 00 74 00  65 00 6D 00  00 00 C9 7B  S.y.s.t.e.m....{
0039EC50: 20 89 E5 F7  00 00 00 00  28 ED 39 00  27 5B C3 7B   .......(.9.'[.{
0039EC60: 00 00 00 00  FF FF FF FF  00 00 00 00  FF FF FF FF  ................
0039EC70: 43 FC CA 7B  F8 FE 39 00  30 5C C3 7B  F4 4F C9 7B  C..{..9.0\.{.O.{
0039EC80: 00 00 00 00  3A 1C C6 7E  C8 EC 39 00  95 58 C3 7B  ....:..~..9..X.{
0039EC90: C0 78 F5 F7  C0 67 F5 F7  01 00 00 00  F4 4F C9 7B  .x...g.......O.{
0039ECA0: E8 EC 39 00  D3 B4 E6 F7  26 00 00 00  7C 59 C3 7B  ..9.....&...|Y.{
0039ECB0: E8 FC CA 7B  2C FD CA 7B  00 00 00 00  FF FF FF FF  ...{,..{........
0039ECC0: 3A 1C C6 7E  60 ED 39 00  E8 EC 39 00  E8 FC CA 7B  :..~`.9...9....{
0039ECD0: E0 F8 CA 7B  00 00 00 00  06 FD CA 7B  F4 4F C9 7B  ...{.......{.O.{
0039ECE0: 1E 00 00 00  3A 1C C6 7E  18 ED 39 00  10 5A C3 7B  ....:..~..9..Z.{
0039ECF0: 3A 1C C6 7E  60 ED 39 00  61 F9 C8 7E  2A 1F C6 7E  :..~`.9.a..~*..~
0039ED00: 05 00 00 00  05 00 00 00  01 00 00 00  F4 9F FB F7  ................
0039ED10: 60 F9 C8 7E  00 00 00 00  48 ED 39 00  49 82 E9 F7  `..~....H.9.I...
0039ED20: 00 00 00 00  15 00 00 00  00 00 C6 7E  F4 7F 8B 7B  ...........~...{
0039ED30: 01 00 00 00  B0 F6 39 00  88 ED 39 00  E9 21 86 7B  ......9...9..!.{
0039ED40: 40 99 FB F7  00 00 00 00  04 F0 39 00  01 00 00 00  @.........9.....
0039ED50: B0 F6 39 00  80 00 00 00  00 00 00 00  00 00 00 00  ..9.............
0039ED60: 75 50 EB F7  00 00 00 00  BC ED 39 00  94 56 C6 7B  uP........9..V.{
0039ED70: 17 00 00 00  FF FF FF FF  05 A6 E3 F7  F4 FF C6 7E  ...............~
0039ED80: 01 00 00 00  04 F1 39 00  18 F1 39 00  6B 99 C1 7E  ......9...9.k..~
0039ED90: 00 00 00 00  00 00 00 00  04 F0 39 00  FF FF FF FF  ..........9.....
0039EDA0: B0 F6 39 00  80 00 00 00  00 00 00 00  00 00 00 00  ..9.............
0039EDB0: 53 86 D6 F7  C8 0A DF FF  03 00 00 00  48 03 00 00  S...........H...
0039EDC0: 5C 00 5C 00  2E 00 5C 00  44 00 49 00  53 00 50 00  \.\...\.D.I.S.P.
0039EDD0: C2 B9 C4 7B  F4 9F FB F7  10 00 00 00  FC ED 39 00  ...{..........9.
0039EDE0: C7 BD E9 F7  00 00 00 00  F0 F4 39 00  CB 87 C8 7B  ..........9....{
0039EDF0: F4 4F C9 7B  10 0F 11 00  0C 01 CB 7B  1C EE 39 00  .O.{.......{..9.


------------------------------------------------------------------------------

======================================================================
Hardware/Driver Information:
Processor:              0x0
Page Size:              4096
Min App Address:        0x10000
Max App Address:        0x7ffeffff
Processor Mask:         0x1
Number of Processors:   1
Processor Type:         586
Allocation Granularity: 65536
Processor Level:        15
Processor Revision:     1802
Os Version:             5.1
Os Service Pack:        4.0

Percent memory used:    41
Total physical memory:  2083905536
Free Memory:            1215246336
Page file:              3957854208
Total virtual memory:   2147352575

```

---

### Post by hikaricore on 2009-02-14
Did you reboot or atleast relog after installing new video drivers?

---

### Post by panaut0lordv on 2009-02-14
Yes of course, I'm not such n00b and I can do some troubleshooting ;)

My xorg.
```

# nvidia-settings: X configuration file generated by nvidia-settings
# nvidia-settings:  version 1.0  (buildd@crested)  Sun Feb  1 20:25:37 UTC 2009

# xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# Note that some configuration settings that could be done previously
# in this file, now are automatically configured by the server and settings
# here are ignored.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "ServerLayout"
    Identifier     "Default Layout"
    Screen      0  "Screen0" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "ServerFlags"
    Option         "IgnoreABI" "True"
    Option         "DontZap" "off"
    Option         "Xinerama" "0"
EndSection

Section "InputDevice"
    # generated from default
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection

Section "InputDevice"
    # generated from default
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "Monitor"
    Identifier     "Configured Monitor"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "LG F900P"
    HorizSync       30.0 - 111.0
    VertRefresh     50.0 - 160.0
EndSection

Section "Device"
    Identifier     "Configured Video Device"
    Driver         "nvidia"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 9600 GT"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "Configured Video Device"
    Monitor        "Configured Monitor"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "metamodes" "1280x1024_85 +0+0; 1280x1024 +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection
```

---

### Post by cb951303 on 2009-02-14
AFAIK -opengl flag is no more used. 
you should add **SET gxApi "opengl"** to your config.wtf
however I doubt this is the problem

I see some permission errors, it looks like something to do with nvidia drivers. could you try to run it as root and see if it works?

---

### Post by panaut0lordv on 2009-02-14
It was in my config. Sudoing made it work but it's poor workaround which destroys all security of wine&ubuntu ;(

---

### Post by hikaricore on 2009-02-14
While there may be little to no danger running WoW with sudo, I suggest you use this as a short term solution and try and find a fix in the mean time.

Better safe than sorry.

Also any files that WINE or WoW create while being run as root will probably have incorrect ownership and will also need to be corrected later.

---

### Post by cb951303 on 2009-02-14
> **panaut0lordv said:**
> It was in my config. Sudoing made it work but it's poor workaround which destroys all security of wine&ubuntu ;(

it was only meant to see if this is a permission problem. not a solution :)
now that we know it has something to do with permissions
> 
NVIDIA: could not open the device file /dev/nvidiactl (Permission denied).


you can try to change the /dev/nvidiactl's permission/owner and see if it works

cheers

---

### Post by panaut0lordv on 2009-02-14
Changing chmod of nvidiactl & nvidia0 fixed problems. Thanks for your help

---

### Post by Ferrat on 2009-02-14
if it works with you running with sudo then you probably ran it at somepoint with sudo or some other program you shouldn't, when the program then writes on a file sudo privs are needed to use it again, try changing owers etc on wow files and remove and reinstall wine. 
WINE should never ever run with sudo

---

### Post by dcstar on 2009-05-01
Same problem on my (fresh) 9.04 64-bit install, do this:

```
gksudo gedit /etc/rc.local
```

Add the following before "exit 0":

**chmod 666 /dev/nvidia* &**

In my case it brought up an error in VMware server when launching an XP VM.

[https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-180/+bug/370249](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-180/+bug/370249)

---

### Post by Tamaris on 2009-05-01
Hi,

More simply, you can try to add your username into the video group.
Log off, log in, and it's ready.

To do this : 
```
sudo adduser $USER video
```

++

---

### Post by asdfoo on 2009-05-02
You should upgrade to atleast 180.44 too, it has some stability fixes for Wine.

---

### Post by wayward4now on 2009-07-31
[quote=dcstar;7189369]Same problem on my (fresh) 9.04 64-bit install, do this:

```
gksudo gedit /etc/rc.local
```Add the following before "exit 0":

**chmod 666 /dev/nvidia* &**

In my case it brought up an error in VMware server when launching an XP VM.

I had the very same problem upgrading to karmic with kubuntu. My games started audio stuttering like mad. So, I bit the bullet, installed AMD64 Kubuntu Karmic from scratch. Then I installed warzone2100 and once it ran, it still stuttered, top shows warzone eating up half of the cpu and x the other half. I ran it from command line and noted :

wayward4now@iam: warzone2100
NVIDIA: could not open the device file /dev/nvidiactl (Permission denied).
NVIDIA: Direct rendering failed; attempting indirect rendering.
error   : [rebuildSearchPath] Failed to remove path /home/wayward4now/.warzone2100-2.1/ again, because of Files still open
error   : [rebuildSearchPath] Failed to remove path /usr/data/ again, because of No such entry in search path
error   : [rebuildSearchPath] Failed to remove path /usr/share/warzone2100/ again, because of No such entry in search path
AL lib: alSource.c:2362: alcDestroyContext(): deleting 2 Source(s)
AL lib: alBuffer.c:1079: exit(): deleting 67 Buffer(s)

Yes, I installed the 64bit version of nvidia from nvidia. For whatever reason, envyng doesn't work any more, but it is there in the synaptic to be dnloaded. I never had a problem using it. Ever. WTH? Ric
:confused:

---

### Post by wayward4now on 2009-07-31
[quote=dcstar;7189369]Same problem on my (fresh) 9.04 64-bit install, do this:

```
gksudo gedit /etc/rc.local
```Add the following before "exit 0":

**chmod 666 /dev/nvidia* &**

In my case it brought up an error in VMware server when launching an XP VM.

[]("https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-180/+bug/370249")OK, that seemed to help. It's still stuttering like mad though. Now I get these errors calling up warzone2100 on a command line. 

wayward4now@iam:~$ warzone2100
error   : [rebuildSearchPath] Failed to remove path /usr/data/ again, because of No such entry in search path
error   : [rebuildSearchPath] Failed to remove path /usr/share/warzone2100/ again, because of No such entry in search path
AL lib: alSource.c:2362: alcDestroyContext(): deleting 1 Source(s)
AL lib: alBuffer.c:1079: exit(): deleting 34 Buffer(s)

It seems alsa isn't playing nicely. Any ideas?

---

