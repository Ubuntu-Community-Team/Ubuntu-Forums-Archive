---
title: "World of Warcraft -opengl issue using radeon drivers"
date: 2010-12-02
forum: Wine
---

### Post by Shai_- on 2010-12-02
Hello everyone i've been trying to make WOW work on my FC14 laptop. 
i know i'm on a ubuntu forum so why the hell would i complain here ? i think ubuntu counts many gamers and since i followed a "tutorial" from a ubuntu user i'm sure someone can help me here :)
 
the game crashes when i enter the realm and sometimes i can play 15 minutes before it crashes. 
 
here's what you need, if you need something else just tell me [IMG]http://forum.winehq.org/images/smiles/icon_smile.gif[/IMG] 

wine 1.3.8
 
lspci -vv 
 
01:00.0 VGA compatible controller: ATI Technologies Inc M76 [Radeon Mobility HD 2600 Series] (prog-if 00 [VGA controller]) 
	Subsystem: Toshiba America Info Systems Device ff00 
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+ 
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx- 
	Latency: 0, Cache Line Size: 64 bytes 
	Interrupt: pin A routed to IRQ 47 
	Region 0: Memory at d0000000 (32-bit, prefetchable) [size=256M] 
	Region 1: I/O ports at 2000 [size=256] 
	Region 2: Memory at c7ef0000 (32-bit, non-prefetchable) [size=64K] 
	[virtual] Expansion ROM at c7e00000 [disabled] [size=128K] 
	Capabilities: <access denied> 
	Kernel driver in use: radeon 
	Kernel modules: radeon 
 
for the skeptics : 
 glxinfo | grep rendering 
direct rendering: Yes 
 
 
the error : 
[http://pastebin.ca/2008886](http://pastebin.ca/2008886) 
 
my config.wtf 
[http://pastebin.ca/2008889](http://pastebin.ca/2008889) 
 
my xorg.conf 
[http://pastebin.ca/2008888](http://pastebin.ca/2008888) 
 
thx for reading ! [IMG]http://forum.winehq.org/images/smiles/icon_smile.gif[/IMG]

---

