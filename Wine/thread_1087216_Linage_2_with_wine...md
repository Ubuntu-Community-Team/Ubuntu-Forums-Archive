---
title: "Linage 2 with wine.."
date: 2009-03-04
forum: Wine
---

### Post by Anixs on 2009-03-04
Yes, ive read the HowTo. it didnt help me at all..
Ive followed the steps, and configured wine, installed that patches, updated, and all the good stuff.
But when i run Launcher, it updates the files, everything goes normal,
then i close it, run L2.exe, and i get this error..

2009.3.4 19:37:45
OS : Windows Vista 6.0 (Build: 6000)
CPU : GenuineIntel Celeron M Processor @ 1730 MHz with 1007MB RAM
Video : No Video
PosCode : LS1:0:0:0 2/0

General protection fault!

History: FL2GameData::LoadL2DataBin <- FL2GameData::EulaLoad <- FL2GameData::Load <- UGameEngine::Init <- InitEngine

Is it because Wine doesnt recognize my graphics card?

system:
Ubuntu 8.10
2Gb ram
Genuine Intel(R) CPU T2250 @ 1.73GHz x2
Wine 1.1.16
GeForce Go 7600 (177.82)

---

### Post by cogadh on 2009-03-04
Have you installed the restricted drivers for your video card yet? If you have and Wine still isn't picking the device ID correctly, you can try setting it manually in the registry. Details here:
[http://wiki.winehq.org/UsefulRegistryKeys](http://wiki.winehq.org/UsefulRegistryKeys)

---

### Post by Anixs on 2009-03-04
Well im going through that, but im not exactly sure what i should do.
WINE runs other games like SPORE, but when i run L2, it says no video...

---

### Post by Anixs on 2009-03-04
[[IMG]http://img515.imageshack.us/img515/9716/screenshotu.th.png[/IMG]](http://img515.imageshack.us/my.php?image=screenshotu.png)

---

### Post by cogadh on 2009-03-04
Try running the game from the terminal and post Wine's output here. To be honest, error messages from the game aren't nearly as useful as the error messages that Wine produces, which may explain exactly what is happening.

---

### Post by Anixs on 2009-03-04
fixme:reg:GetNativeSystemInfo (0x1a20787) using GetSystemInfo()
fixme:toolhelp:CreateToolhelp32Snapshot Unimplemented: heap list snapshot
fixme:thread:NtSetInformationThread info class 17 not supported yet
fixme:debugstr:CheckRemoteDebuggerPresent (0xffffffff)->(0x1a8902e): Stub!
fixme:process:GetProcessWorkingSetSize (0xffffffff,0x32e848,0x32e844): stub
fixme:win:EnumDisplayDevicesW ((null),0,0x32e7ac,0x00000000), stub!


Thats what i get, then the error pops up, then i hit okay on the error, it just closes.
a SS:
[[IMG]http://img10.imageshack.us/img10/2087/screenshot1k.th.png[/IMG]](http://img10.imageshack.us/my.php?image=screenshot1k.png)

---

### Post by binbash on 2009-03-05
[http://www.lotrolinux.com/ULL/](http://www.lotrolinux.com/ULL/)

---

