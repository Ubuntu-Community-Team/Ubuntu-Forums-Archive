---
title: "Wine crashes with everything"
date: 2009-05-25
forum: Wine
---

### Post by any.linux12 on 2009-05-25
Hi!

I realy need to have wine running on my laptop and it's not to play it's to work. I want to programm machines running wine because I don't want to use windows virtual machines anymore. The thing is that everything crashes. From the software I use "Indel" until the simple msn messenger. I already tryed a lot of howto's but I didn't get it running yet so I think that your guy can help me


Ubuntu Distro: 8.10 64bits
Laptop: HP Compaq 6715b
Wine version: 1.1.22

I don't know if it's important to refer grafic and sound settings because the software I need is very simple

I don't know what else I can post because I've no idea about the problem.

Thanks in advance

---

### Post by asdfoo on 2009-05-25
which application crashes? please include terminal output including the backtrace as well as your video card and driver version

---

### Post by any.linux12 on 2009-05-25
> **asdfoo said:**
> which application crashes? please include terminal output including the backtrace as well as your video card and driver version

Grafic card: ATI Radeon X1250
Driver: FGLRX
Software: Indel Master Desk

The error message is attached


wine: Unhandled page fault on read access to 0x00000000 at address 0x5f42fdcc (thread 0041), starting debugger...
Unhandled exception: page fault on read access to 0x00000000 in 32-bit code (0x5f42fdcc).
Register dump:
 CS:0023 SS:002b DS:002b ES:002b FS:0063 GS:006b
 EIP:5f42fdcc ESP:0032bf94 EBP:0032bfbc EFLAGS:00010246(  R- --  I  Z- -P- )
 EAX:00000000 EBX:001ade4c ECX:00000000 EDX:0012eeb0
 ESI:001ab850 EDI:00000000
Stack dump:
0x0032bf94:  00000000 00000000 00000000 001add30
0x0032bfa4:  001ab6c8 0122ab10 0012fb50 0032c098
0x0032bfb4:  5f497c73 00000000 0032c010 5f421e4b
0x0032bfc4:  001ab988 001add58 5f423e36 001adc70
0x0032bfd4:  5f42f913 001add30 001adfd8 001add58
0x0032bfe4:  01221020 ffff8302 ffff8302 ffff82fe

Backtrace:
=>0 0x5f42fdcc in mfc42 (+0x2fdcc) (0x0032bfbc)
  1 0x5f421e4b in mfc42 (+0x21e4b) (0x0032c010)
  2 0x01221b5b in treegrid (+0x11b5b) (0x0032c0a4)
  3 0x5f401aff in mfc42 (+0x1aff) (0x0032c0c4)
  4 0x5f42d65f in mfc42 (+0x2d65f) (0x0032c0ec)
  5 0x5f401a88 in mfc42 (+0x1a88) (0x0032c14c)
  6 0x5f401a10 in mfc42 (+0x1a10) (0x0032c168)
  7 0x012232b6 in treegrid (+0x132b6) (0x0032c194)
  8 0x7edf308a WINPROC_wrapper+0x1a() in user32 (0x0032c1c4)
  9 0x7edf34da WINPROC_wrapper+0x46a() in user32 (0x0032c204)
  10 0x7edf97a7 in user32 (+0xb97a7) (0x0032c244)
  11 0x7edb70b1 in user32 (+0x770b1) (0x0032c2a4)
  12 0x7edbc3a5 in user32 (+0x7c3a5) (0x0032c304)
  13 0x7edbc863 SendMessageA+0x53() in user32 (0x0032c344)
.....(still more)

Module  Address                 Debug info      Name (108 modules)
PE        440000-  447000       Deferred        ism_inco_32
PE        450000-  4ad000       Deferred        ignux
PE        4b0000-  4c0000       Deferred        csh
PE        950000-  95e000       Deferred        outwin
PE       1210000- 1231000       Export          treegrid
PE       1760000- 17a6000       Export          incoexp
PE       2000000- 2040000       Deferred        codemax
PE       2800000- 2868000       Export          imex
PE       3000000- 318c000       Deferred        mdux
PE      10000000-10041000       Deferred        inco_32
PE      11000000-1106d000       Deferred        ict
PE      202b0000-20346000       Deferred        comctl32
PE      212f0000-21323000       Deferred        tabctl32
PE      40000000-40021000       Deferred        imd
PE      5f400000-5f4f2000       Export          mfc42
PE      60000000-6000a000       Deferred        bugslayerutil
PE      6a850000-6a9a2000       Deferred        msvbvm60
PE      780a0000-780b2000       Deferred        msvcirt
PE      780c0000-78121000       Deferred        msvcp60
ELF     7b800000-7b948000       Deferred        kernel32<elf>
(still more)

Sorry but I cant post it all
Thanks

---

### Post by Duskao on 2009-05-25
You might be better to try the stable version of wine. 1.0.1. Or perhaps just not the newest wine 1.1.22. Try 1.1.19 or 1.1.20. I have found 1.1.22 to be rather unstable myself. Seems like it is crashing loads of apps all over the place. Look up wine 1.1.22 and crash and they seem to go together like jam and peanut butter :D.

---

### Post by any.linux12 on 2009-05-27
Bump

Com'on guys. I need this to work

Doesn't work with any version. Could it be libraries and can winetools help

---

### Post by asdfoo on 2009-05-27
> **any.linux12 said:**
> Bump

Com'on guys. I need this to work

Doesn't work with any version. Could it be libraries and can winetools help

If it doesnt' work, it doesn't work. Not everything works with Wine.

---

### Post by any.linux12 on 2009-05-27
> **asdfoo said:**
> If it doesnt' work, it doesn't work. Not everything works with Wine.

But the problem is that nothing works with wine.

like:

-MSN
-eDrawings
-Solidworks
-Office 2000
-2 diferentes financial software

and there was a guy that had the app in want to run with wine with no problem but I told me that everytime he updated wine I had to do everything again

---

### Post by NightMKoder on 2009-05-27
- MSN - wont work: [http://appdb.winehq.org/objectManager.php?sClass=version&iId=11389](http://appdb.winehq.org/objectManager.php?sClass=version&iId=11389)
- eDrawings - not even in appdb, good chance that it wont work
- MS Office 2k - works with new wine: [http://appdb.winehq.org/objectManager.php?sClass=version&iId=5124](http://appdb.winehq.org/objectManager.php?sClass=version&iId=5124)
- Solidworks 2008 - wont work: [http://appdb.winehq.org/objectManager.php?sClass=version&iId=15224](http://appdb.winehq.org/objectManager.php?sClass=version&iId=15224)
- search appdb for the others

make sure you're using the latest wine and start with a clean prefix. Also, when wine upgrades it doesn't change your configuration, so whatever you did to make it work will work after an upgrade (unless wine regressed).

---

### Post by any.linux12 on 2009-05-27
> **NightMKoder said:**
> - MSN - wont work: [http://appdb.winehq.org/objectManager.php?sClass=version&iId=11389](http://appdb.winehq.org/objectManager.php?sClass=version&iId=11389)
- eDrawings - not even in appdb, good chance that it wont work
- MS Office 2k - works with new wine: [http://appdb.winehq.org/objectManager.php?sClass=version&iId=5124](http://appdb.winehq.org/objectManager.php?sClass=version&iId=5124)
- Solidworks 2008 - wont work: [http://appdb.winehq.org/objectManager.php?sClass=version&iId=15224](http://appdb.winehq.org/objectManager.php?sClass=version&iId=15224)
- search appdb for the others

make sure you're using the latest wine and start with a clean prefix. Also, when wine upgrades it doesn't change your configuration, so whatever you did to make it work will work after an upgrade (unless wine regressed).

Hey thanks a lot for the useful reply and for the links because this is part of my job and those links help me to stop.

---

### Post by hikaricore on 2009-05-27
Have you considered running VM on top of linux so that you can run these programs properly?

---

