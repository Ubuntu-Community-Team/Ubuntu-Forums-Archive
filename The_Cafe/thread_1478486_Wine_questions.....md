---
title: "Wine questions...."
date: 2010-05-09
forum: The Cafe
---

### Post by dragos240 on 2010-05-09
I just thought of something..... could you run windows in wine? Or would everything in wine work if you replaced all the native DLLs with official DLLs? Just a few questions I thought of. What do you think.

---

### Post by chriswyatt on 2010-05-09
I don't know much about the innards of the OS but my guess would be you couldn't because Windows itself doesn't run on Windows natively, it consists of a kernel which interfaces with a BIOS, not Windows.  Though I'd guess maybe it's possible to run Explorer and a bunch of other native Windows software on there.

But I dunno.

---

### Post by RiceMonster on 2010-05-09
No, you can't run Windows in wine, because wine is a compatibility layer for the windows api. It doesn't emulate a hardware platform, which is what would be required to run an OS.

---

### Post by kmsalex on 2010-05-09
you can't run windows on windows because windows isn't a program its an os that needs direct access to the hardware its running on. 

But the idea of replacing all of the wine dlls with real windows dlls is a cool idea i've thought of before but never attempted, or even know how to attempt. but i don't think that that the wine developers would like, as it goes agents there ideology of making better replacement dlls then the originals.

---

### Post by BslBryan on 2010-05-09
The .dll thing has been done before.  If you frequent WineHQ and the bugs there, you'll see that many people suggest downloading, or somehow obtaining, some .dll file and hope the bug gets fixed.  I've also put several .dll files into my WINE install directory, which helps sometimes.

---

### Post by amauk on 2010-05-09
Wine can be compiled and installed in windows

Wine devs used to (do they still do this?) install a native version of windows, then install Wine
They can then flip-flop between running programs natively, or "through" wine on windows

This was a good way to see if Wine exactly replicated what native Win32 was doing

---

### Post by 3rdalbum on 2010-05-09
Some of the Wine DLLs call Linux system calls. Obviously those can't be replaced. The ones that just call other Wine or Windows DLLs can be replaced with genuine Windows ones.

---

### Post by praveesh on 2010-05-10
> **3rdalbum said:**
> Some of the Wine DLLs call Linux system calls. Obviously those can't be replaced. The ones that just call other Wine or Windows DLLs can be replaced with genuine Windows ones.

Replacing dlls helps run more apps . But you can't replace all . There is a list of  dlls that you can't replace in wine's website .

---

### Post by Khakilang on 2010-05-10
I think Wine is made to run Window application and not OS. So that is why they have Virtual Box or Virtual Machine to run Windows OS separately.

---

### Post by 3Miro on 2010-05-10
If you want to run Windows from inside Linux, use Virtual Box.

If you want to run a windows program (i.e. some game) from inside Linux, use Wine.

As for the .dll files, not everything works, but many things do. There are two competing philosophies: the official WineHQ which says that their goal is to make the use of extra .dll files unnecessary; and winetricks, that says do whatever it takes to make things working.

---

