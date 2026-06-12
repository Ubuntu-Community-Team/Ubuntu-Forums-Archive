---
title: "Company Of Heroes, doesn't run"
date: 2009-11-07
forum: Wine
---

### Post by thehighnotes on 2009-11-07
hey there, 

I am a new Linux user, and I have been stupidly figuring out how to get my COH working. Turns out i misread one line on a guide which made me run in circles... or so I thought.

Eventually I corrected myself, and did exactly as the guide on WineHQ said, however, now COH starts, but quits before any screen has appeared (except for the Blue wine screen).. So I ran it from the terminal, to see what was going on, but out of this I couldn't make any sense.. 

I have followed these instructions (on a clean 'Windows' wine version): [WineHQ appdb]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=18109")
This is the output in the Terminal.
```
fixme:heap:HeapSetInformation (nil) 1 (nil) 0
fixme:heap:HeapSetInformation 0x2720000 0 0x114fc74 4
fixme:heap:HeapSetInformation 0x2a50000 0 0x114fc5c 4
fixme:heap:HeapSetInformation 0x2b60000 0 0x114fc5c 4
fixme:heap:HeapSetInformation 0x2d80000 0 0x114fca0 4
fixme:heap:HeapSetInformation 0x3700000 0 0x114fc40 4
fixme:heap:HeapSetInformation 0x3810000 0 0x114fc40 4
fixme:heap:HeapSetInformation 0x3920000 0 0x114fc40 4
fixme:heap:HeapSetInformation 0x3a30000 0 0x114fca0 4
fixme:heap:HeapSetInformation 0x3b40000 0 0x114fcfc 4
fixme:heap:HeapSetInformation 0x3c50000 0 0x114fcfc 4
fixme:heap:HeapSetInformation 0x3d60000 0 0x114fdc0 4
fixme:heap:HeapSetInformation 0x3e70000 0 0x114fdc0 4
fixme:imm:ImmDisableTextFrameService Stub
fixme:ole:CoCreateInstance no instance created for interface {3e90ade3-7594-4cb0-bb58-69628f5f458c} of class {529a9e6b-6587-4f23-ab9e-9c7d683e3c50}, hres is 0x80004002
fixme:imm:ImmGetOpenStatus (0x1476a8): semi-stub
fixme:imm:ImmReleaseContext (0x10030, 0x1476a8): stub
fixme:heap:HeapSetInformation 0x4470000 0 0x114fb6c 4
fixme:heap:HeapSetInformation 0x4770000 0 0x114e5e0 4

```Other information: 
Version Wine: V 1.1.31  EDIT: Updated to 1.1.32, no change in output or result. 
Version ubuntu: 9.10 (newly installed)
Geforce 9800 XXX
Used latest winetricks
Installed D3Dx9 with winetricks
Have not adjusted any Register data yet using "wine regedit"

If someone could tell me, or point me in the right direction, I will be forever grateful! I have looked around for clues on this problem for 3 days now, including this website, but, no luck so far..

EDIT:
Solved it!!!! Finally after 3 days!!

I made the repeated mistake of installing the game also under Wine, this time I deleted ./wine, started over, and just copied the game from my windows partition.. works like a charm..

---

### Post by shunt31 on 2010-12-21
To anybody else still getting an error, try: 
```
wine RelicCOH.exe -minvidmem 0
```

---

