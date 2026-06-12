---
title: "Kernel 4.0"
date: 2010-10-19
forum: The Cafe
---

### Post by as2000 on 2010-10-19
If this was possible, what would you think it should be?

---

### Post by conundrumx on 2010-10-19
Of course it's possible, but how long would it take to reach this point?  Will Linux even exist by then?  We've been in the 2.x series for a long time (over ten years), and one would assume some pretty radical changes would be necessary to shift to 3.x.

Computers as we know them may be fundamentally different by the time a 4.0 kernel would be appropriate

---

### Post by amauk on 2010-10-19
the 2.6 bit of recent kernels (post-2004) is pretty much superfluous. It's a throwback from the previous development model

There will never be a 2.7, or 3.0, or 4.0
Such version numbers are not needed with the current development model

---

### Post by Slug71 on 2010-10-19
> **amauk said:**
> the 2.6 bit of recent kernels (post-2004) is pretty much superfluous. It's a throwback from the previous development model

There will never be a 2.7, or 3.0, or 4.0
Such version numbers are not needed with the current development model

This.

If they did ever change to anything else i hope the major stuff is, debloat and bugs. Especially since tech wise, its pretty good right now and already supports a lot of upcoming technologies.

---

### Post by CarpKing on 2010-10-19
Hurd.

---

### Post by Arex Bawrin on 2010-10-19
Can someone please post a link on what the numbers actually represent on the linux kernel version. Why (after ten years) are they still on version 2.x?

---

### Post by amauk on 2010-10-19
The kernel's original development model used odd numbers for development releases, and even numbers for stable releases

- A new stable kernel, 2.2 was released, expected to be maintained for a number of years and would receive only bug & security fixes

- Linus opens 2.3, and development of new features would commence

- At some point, it's decided that 2.3 would not receive any new features, and focus was moved to stabilising the new version

- At some point, it's considered stable, named 2.4 and released, expected to be maintained for a number of years and would receive only bug & security fixes

- Linus opens 2.5, and development of new features would commence

......
....
..


When 2.6 was released, they changed the development model
There were lots of things considered "wrong" or difficult with the even/odd model - not least that new stable kernels appeared every couple of years, and this was a long time for something that needs to keep up with the latest hardware developments

The new model shifted to faster, more incremental releases
The idea of a "stable" and a "development" kernel was abolished, and instead every release is considered "stable"

the 2.6 prefix just got carried over to the new model

---

### Post by Slug71 on 2010-10-20
[http://www.daniweb.com/news/story218605.html](http://www.daniweb.com/news/story218605.html)

---

### Post by mips on 2010-10-20
> **Slug71 said:**
> This.

If they did ever change to anything else i hope the major stuff is, **debloat and bugs**. Especially since tech wise, its pretty good right now and already supports a lot of upcoming technologies.

My wish would be for a modern microkernel.

---

### Post by Oxwivi on 2010-10-20
If 3 is ever to appear I hope it'd a completely debloated version of those before. I think it's essential to have debloating teams on the development team that analyzes the code periodically. Resulting in the leanest and meanest kernel ever! :D

---

### Post by RATM_Owns on 2010-10-20
[http://lkml.org/lkml/2005/3/2/247](http://lkml.org/lkml/2005/3/2/247)
> 
 - 2.6.<odd>: still a stable kernel, but accept bigger changes leading up 
   to it (timeframe: a month or two).
 - 2.<odd>.x: aim for big changes that may destabilize the kernel for 
   several releases (timeframe: a year or two)
 - <odd>.x.x: Linus went crazy, broke absolutely _everything_, and rewrote
   the kernel to be a microkernel using a special message-passing version 
   of Visual Basic. (timeframe: "we expect that he will be released from
   the mental institution in a decade or two").


---

### Post by danbuter on 2010-10-20
> **mips said:**
> My wish would be for a modern microkernel.

If you read Linus' book, you'll see he thinks microkernels suck. :P

---

### Post by Slug71 on 2010-10-20
> **Slug71 said:**
> This.

If they did ever change to anything else i hope the major stuff is, debloat and bugs. Especially since tech wise, its pretty good right now and already supports a lot of upcoming technologies.

> **mips said:**
> My wish would be for a modern microkernel.

> **Oxwivi said:**
> If 3 is ever to appear I hope it'd a completely debloated version of those before. I think it's essential to have debloating teams on the development team that analyzes the code periodically. Resulting in the leanest and meanest kernel ever! :D

Yup. 
Even Linus admits the Kernel is bloated. Hopefully some focus will be shifted towards it in upcoming releases.

---

### Post by mips on 2010-10-22
> **danbuter said:**
> If you read Linus' book, you'll see he thinks microkernels suck. :P

The good thing is that the word of Linus does not constitute gospel ;)

All HURD kernels looked at so far in recent years were of the microkernel variety, Mach microkernel, L4 microkernel, Coyotos & Viengoos

I like this article, [http://www.coyotos.org/docs/misc/linus-rebuttal.html](http://www.coyotos.org/docs/misc/linus-rebuttal.html)

---

### Post by Zestypanda on 2013-02-28
Wow it's hilarious to read these only threads of people saying "kernel 3.0 it'll never happen. Let alone kernel 2.9. See we're now on kernel 3.8 so hahahahah to those ignorant people who said 3.0 would never happen.

---

### Post by philinux on 2013-02-28
Back to sleep.

---

