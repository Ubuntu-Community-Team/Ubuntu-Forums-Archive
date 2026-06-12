---
title: "Rainbow six Vegas...compatible or not?"
date: 2009-02-21
forum: Wine
---

### Post by omni504 on 2009-02-21
I been reading through the ubuntu forums about rainbow six vegas and whatnot, and most people seem to be saying it doesnt work on wine. But then i go to the winehq site, and it tells me that it's ok, and will run (though with some minor issues). So i thought why not try it myself.

I installed wine 1.0.1, and tried to install it.... The install shield wizard would come up, and then itd just exit and display this message in the terminal.

```
fro@fro-laptop:~$ wine /media/cdrom0/Setup.exe
fro@fro-laptop:~$ wine: Unhandled page fault on read access to 0x80000044 at address 0x7bc42042 (thread 001a), starting debugger...
Unhandled exception: page fault on read access to 0x80000044 in 32-bit code (0x7bc42042).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:7bc42042 ESP:0033e020 EBP:0033e048 EFLAGS:00210286(   - 00      -RISP1)
 EAX:80000000 EBX:7bc8aff4 ECX:65faf1f0 EDX:65f22392
 ESI:80000000 EDI:80000000
Stack dump:
0x0033e020:  00000000 00f2001c 0033e038 7bc3adba
0x0033e030:  00000000 00f20018 0033e0f0 7bc8aff4
0x0033e040:  00000000 00f20154 0033e0a8 7bc4407c
0x0033e050:  0033e010 b7eb0fa4 00110014 7bc33f61
0x0033e060:  00110000 00000030 0033e0f8 7bc3368f
0x0033e070:  00110014 0033e0b0 7bc8aff4 00000000
Backtrace:
=>1 0x7bc42042 in ntdll (+0x32042) (0x0033e048)
  2 0x7bc4407c RtlAllocateHeap+0x1c() in ntdll (0x0033e0a8)
err:dbghelp:pe_load_dbg_file -Unable to peruse .DBG file "ole32.dbg" ("")
```



Then it would go down and list the modules (all of em were labeled "deferred") keep backtracing on down to #14 and stop there. Am i missing something?

---

### Post by hikaricore on 2009-02-21
From the looks of it on the appdb, most of the tom clancy games have a trash rating:
[http://appdb.winehq.org/appbrowse.php?catId=16](http://appdb.winehq.org/appbrowse.php?catId=16)

I'm curious to see where exactly you saw that "it was ok".

---

### Post by omni504 on 2009-02-21
[http://appdb.winehq.org/objectManager.php?sClass=version&iId=8149](http://appdb.winehq.org/objectManager.php?sClass=version&iId=8149)

---

### Post by cogadh on 2009-02-21
Depends on your definition of "OK". For me, anything less than gold on AppDB is not OK. I don't see RS:V rated higher than silver and most of the time it seems to be rated bronze or garbage.

---

### Post by hikaricore on 2009-02-21
Seems the game is the a different catagory than it's friends.  >.<

Have you tried any other software titles under WINE?
Did you install using the howto listed on the appdb?

---

### Post by omni504 on 2009-02-21
Ya i used the howto to install wine. But i haven't tried any other games on wine yet. I'm not much of a gamer... I'm just addicted to rainbow six (rainbow six, and rainbow six 2 on 360), but since i spend more time with my laptop (they'll one day make all game systems completely portable), i wanted to be able to play it on my laptop when im at school. So i could play as a study break or just while im at school (usually just be too lazy to come back home til late night).

Heh, well i guess i gotta stick to 360. I'll try out some other games and see if there are any gold supported 1st person shooters that could replace R6 for me.

---

### Post by u235sentinel on 2009-02-25
> **omni504 said:**
> Ya i used the howto to install wine. But i haven't tried any other games on wine yet. I'm not much of a gamer... I'm just addicted to rainbow six (rainbow six, and rainbow six 2 on 360), but since i spend more time with my laptop (they'll one day make all game systems completely portable), i wanted to be able to play it on my laptop when im at school. So i could play as a study break or just while im at school (usually just be too lazy to come back home til late night).

Heh, well i guess i gotta stick to 360. I'll try out some other games and see if there are any gold supported 1st person shooters that could replace R6 for me.

I have a bunch of games running great on multiple computers.  We have 6 Ubuntu 8.04 computers running WINE 1.0.1 with a wide range of games.  Stuff from Starcraft to Star Trek Amarda, several Source games including Half Life 2, Counterstrike Source, Team Fortress 2, other's like Oblivion run great.

I don't consider a purchase until the game has a rating of Gold or higher.  Anything less will give you problems (I've tried Splinter Cell 2 and it was a mess).

Anyway, give Counterstrike Source a try.  It installed under Steam just fine or from CD (I've done both).  The ONLY thing I'm struggling with is getting the mic to work.  it works great under Ubuntu but not under WINE / ALSA unfortunately. But everything else works great.  Graphics, sounds, all amazing!

---

