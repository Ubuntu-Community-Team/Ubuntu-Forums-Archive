---
title: "Are there any advantages to using non-GNU command-line utilities?"
date: 2019-08-06
forum: Ubuntu, Linux and OS Chat
---

### Post by arseniogut on 2019-08-06
I often hear that [GNU coreutils]("https://www.gnu.org/software/coreutils/") are bloat, and that opting instead for [Plan 9 from User Space]("https://9fans.github.io/plan9port/") is somehow less "harmful." I've often heard the same about [FONT=courier new]bash[/FONT], that UNIX users should instead opt for [FONT=courier new]mksh[/FONT].

Are these just bad memes, or is there some merit to using less feature-rich programs?

---

### Post by mastablasta on 2019-08-06
use what works for you. if you need features or you might need features at some point then go with "bloat". if basic is good enough, then use basic.

---

### Post by SeijiSensei on 2019-08-06
Honestly, in these days of very large disk drives, "bloat" is really not an issue.  All of Ubuntu can fit inside a 10 GB partition.

People who talk about "bloat" nowadays are more likely trying to show off.

---

### Post by mastablasta on 2019-08-07
indeed bloat on control units, controllers, electronic i could understand, but on desktop PC...

---

### Post by freemedia2018 on 2019-08-07
I use IceWM, it predates Open Source. (By less than a year.)

Things open and close instantaneously. On Antix, it is even faster.

Bloat is the thing that makes things slower. To know how slow something really is, you have to compare it to something faster. So yes, bloat always exists. It's nice to get rid of it, so you don't have to wait for things. Computers are so fast now-- that having to wait just feels silly. Lighter software makes tasks feel faster. Of course not everybody cares about that, but that doesn't mean it's a silly thing to want.

---

### Post by SeijiSensei on 2019-08-07
For me, SSD's have made much more of a difference than the software they contain.

---

### Post by cruzer001 on 2019-08-07
i7 + ssd - bloat runs really fast on my system :) but I still do not allow it and roll my own to insure this.

I have seen these core packages offered here and there.  I get the impression they are more for builders of computer controlled devices like maybe a robot and not really meant to be used for a full blown operating system.

---

### Post by mastablasta on 2019-08-08
we once had control units. they usually have very low memory (compared to PC or even arduino or similar boards). they then had to add plenty of languages in that small memory (seem they added more that was originally anticipated). result was crashing control units at consumers, recalls and replacements and all sorts of organised chaos. i bet they wished they could have just used a program with less bloat :)

---

### Post by tasket on 2020-01-22
Hi, I'm new to the forum but I found this post really funny.

GNU coreutils are 15Kbytes..... decompressed. :D

The GNU programs do have "many" features added which are not included in POSIX or Unix specifications. Last time I checked, Unix **sort** could not operate on an arbitrarily large list of input files, nor could it sort as fast as GNU sort. Those turned out to be import things for me (and that's just one command). Writing addition script code to make up for the features missing in Unix can rather vexing as well – which is the point of adding those features: they can help a lot.

People should remember what "GNU" means: GNU is Not Unix. But that is a negative statement. It could also be called "GIIOS": GNU Is Its Own System.

---

### Post by johnsingam on 2020-01-23
> **SeijiSensei said:**
> Honestly, in these days of very large disk drives, "bloat" is really not an issue.  All of Ubuntu can fit inside a 10 GB partition.

People who talk about "bloat" nowadays are more likely trying to show off.

You are right.

---

