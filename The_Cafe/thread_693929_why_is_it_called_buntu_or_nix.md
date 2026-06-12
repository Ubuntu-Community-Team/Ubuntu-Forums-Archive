---
title: "why is it called *buntu or *nix"
date: 2008-02-11
forum: The Cafe
---

### Post by Cew27 on 2008-02-11
as the title says, why is this ??

---

### Post by Mithrilhall on 2008-02-11
*buntu is a simple way of writing Ubuntu/Kubuntu/Xubuntu/etc...

*nix is a simple way of writing Unix/Linux

---

### Post by Cew27 on 2008-02-11
ahhh so what is unix put in simple terms 
thanks for the hasty reply

---

### Post by SunnyRabbiera on 2008-02-11
Yeh, its mainly because there are so many variations of both unix/ linux and ubuntu.
Its a jungle out there :D

---

### Post by macogw on 2008-02-11
* is what's used in regular expressions to match any character, and any number of them (0 to infinity).

---

### Post by aimran on 2008-02-11
eg: *phobia

---

### Post by Linuxratty on 2008-02-12
> **SunnyRabbiera said:**
> Yeh, its mainly because there are so many variations of both unix/ linux and ubuntu.
Its a jungle out there :D

And here is the proof!
[http://distrowatch.com/stats.php?section=popularity](http://distrowatch.com/stats.php?section=popularity)

---

### Post by k2t0f12d on 2008-02-12
> **Cew27 said:**
> as the title says, why is this ??

The star/asterisk symbol is used for globbing in regular expressions (as was mentioned previously).  When seeing it used, one may mentally replace it with the word "any" for an approimate English translation, e.g. *any*Buntu or *any*nix.

The [Single UNIX Specification]("http://en.wikipedia.org/wiki/Single_UNIX_Specification") is a design standard for computer operating systems to qualify under the title Unix.  At this point there is no longer one collection of operating systems software that one could call *the* UNIX operating system.  Any operating system that attempts to follow the design is called a UNIX, and are referred to collectively as *nix.  The only actively developed systems that possibly contain any original code from the first UNIX system are the Berkeley Software Distributions, FreeBSD, NetBSD, OpenBSD, etc.  SCO UNIX, an operating system developed by the Santa Cruz Operation II, also may contain original UNIX source code that the now defunct SCO licensed from Novell.

---

### Post by Cew27 on 2008-02-13
so they are unix based because they follow the linux of unix ?

---

### Post by scorp123 on 2008-02-13
> **Cew27 said:**
> ... because they follow the linux of unix ? Huh? What? You may want to lookup things in Wikipedia, it's all there. Linux is a "UNIX-like" operating system (i.e. it contains no original UNIX source code by Bell Labs or AT&T, it was written from scratch) written by then-student Linus Torvalds .. because he needed some form of UNIX on his Intel 80386 PC but he could not afford the then-expensive UNIX licenses. So he wrote the stuff himself and that's how Linux started in the early 1990's. 

Why "Linux"? Because its creator's name is Linus Torvalds, and it is a UNIX-like OS ... so they named it after him and placed a "X" on the end so people would get the idea that it is some form of UNIX just like the other *nix'es. (Torvalds wanted to call his creation "FreaX" as in "free", "freaky" and "X" for UNIX ...)

As I said ... all this stuff can easily be looked up in Wikipedia.

---

### Post by Pekkalainen on 2008-02-13
The * in *nix was originally used for trademark reasons. Since the SCO case is over and lost the point of it is redundant.

---

### Post by scorp123 on 2008-02-13
> **Pekkalainen said:**
> The * in *nix was originally used for trademark reasons. Since the SCO case is over and lost the point of it is redundant. The trademark was never held by SCO to begin with, it's held by "The OpenGroup". 

[http://en.wikipedia.org/wiki/UNIX#Branding](http://en.wikipedia.org/wiki/UNIX#Branding)

"Sometimes a representation like "Un*x", "*NIX", or "*N?X" is used to indicate all operating systems similar to Unix. This comes from the use of the "*" and "?" characters as "wildcard" characters in many utilities. This notation is also used to describe other Unix-like systems, e.g. Linux, BSD, etc., that have not met the requirements for UNIX® branding from the Open Group."

[http://en.wikipedia.org/wiki/The_Open_Group#Certification](http://en.wikipedia.org/wiki/The_Open_Group#Certification)

"The Open Group is also the owner of the UNIX trademark."

---

### Post by Pekkalainen on 2008-02-13
> **scorp123 said:**
> The trademark was never held by SCO to begin with, it's held by "The OpenGroup". 

[http://en.wikipedia.org/wiki/UNIX#Branding](http://en.wikipedia.org/wiki/UNIX#Branding)

"Sometimes a representation like "Un*x", "*NIX", or "*N?X" is used to indicate all operating systems similar to Unix. This comes from the use of the "*" and "?" characters as "wildcard" characters in many utilities. This notation is also used to describe other Unix-like systems, e.g. Linux, BSD, etc., that have not met the requirements for UNIX® branding from the Open Group."

[http://en.wikipedia.org/wiki/The_Open_Group#Certification](http://en.wikipedia.org/wiki/The_Open_Group#Certification)

"The Open Group is also the owner of the UNIX trademark."

Same **** different name ;)

---

### Post by scorp123 on 2008-02-13
> **Pekkalainen said:**
> Same **** different name ;) Not really. Linux does not contain any portions of UNIX code (no matter what BS was claimed by SCO on this subject) ... so from a "genetic" point of view, it is not a UNIX. Technically it's probably best described as "UNIX Emulator" (no kidding!) ... It behaves like a UNIX, it feels like a UNIX, it thus emulates a UNIX ... So Linux is "UNIX-like", but not a UNIX, not in a genetic sense (no code was ever copied over from UNIX) and not in a technical sense.

Correct would be:

Similar sh**, similar name, everyone knows what's meant with it. :)

---

### Post by Trail on 2008-02-13
Should be "GNU/Linux", tbh :)

---

### Post by hyper_ch on 2008-02-13
Wouldn't UNIX and LINUX be POSIX?

---

### Post by Trail on 2008-02-13
POSIX is an interface, like specifications on how to behave on certain aspects.

They are POSIX-compatible. (Well, mostly anyway)

---

### Post by k2t0f12d on 2008-02-13
> **Cew27 said:**
> so they are unix based because they follow the linux of unix ?

Okay I think this is getting a little confusing.  What I meant to get across in my post was that there is no specific operating system one can point to and say *"This is **the one true** UNIX."*  Any system that attempts to follow the Single UNIX Specification *is* a UNIX.  POSIX is a different standard that revolves around interoperability and following it doesn't make a system a UNIX.  Even Microsoft Windows observes some  of the POSIX standards in their NT software series.

---

### Post by scorp123 on 2008-02-13
> **Trail said:**
> Should be "GNU/Linux", tbh :) Yes, technically "Linux" is just the kernel, the userland around it is "GNU". So yes, correctly it probably should be called "GNU/Linux".

---

### Post by scorp123 on 2008-02-13
> **k2t0f12d said:**
>  "This is **the one true** UNIX." **UNIX-PDP7**, ca. 1969 :lolflag:

Or how about **UNIX System V Release 4**, ca. 1988 .... Every UNIX-like OS that is around now --with the notable exception of the BSD's-- go back to this and in fact claim to be "SysV" and use System V's init procedures ... :)

[http://upload.wikimedia.org/wikipedia/en/1/11/Unix-history.svg](http://upload.wikimedia.org/wikipedia/en/1/11/Unix-history.svg)

---

