---
title: "How do we know if GPL is being adhered to?"
date: 2009-08-28
forum: The Cafe
---

### Post by suitedaces on 2009-08-28
I mean the part of the GPL that states when code is used or modified, the new code must be disclosed. How can we be sure that there aren't closed source software developers who are using chunks of the code but not divulging this?
I'm not suggesting I know of any who are, or even that there are any who do, I just began thinking after that thread the other day about allowing close-source companies to use the Linux code.

---

### Post by lykwydchykyn on 2009-08-28
Obviously, we can't know this, normally, unless it involves something exposed to the user with obvious fingerprints (e.g., blackbox shell, which has been the subject of numerous GPL-enforcement lawsuits).

---

### Post by eragon100 on 2009-08-28
> **suitedaces said:**
> I mean the part of the GPL that states when code is used or modified, the new code must be disclosed. How can we be sure that there aren't closed source software developers who are using chunks of the code but not divulging this?
I'm not suggesting I know of any who are, or even that there are any who do, I just began thinking after that thread the other day about allowing close-source companies to use the Linux code.

One of the reasons why the GPL isn't very usefull, IMHO. There is no way to proof that it has been violated without being able to review the code, for which you need to be granted permission by a judge, which will want to see reasonable grounds for suspicion before giving you this permission. He is giving you permission to look into someone else's IP after all, not an easily-made decision.

---

### Post by Chronon on 2009-08-28
They don't have to grant the plaintiff review over the code.  A neutral third party could be brought in to review the claim.

I agree that it's problematic, though.  It's why piracy is a big problem for free software, as I see it.  The only thing that enforces the GPL is copyright.  Once that goes out the window there's absolutely no reason for someone to respect the GPL.  People who release their code under the GPL basically have to just trust that it will be respected.  Of course, this is also true for any source code that's released, no matter what the license.

---

### Post by BuffaloX on 2009-08-28
Programmers are generally very good at recognizing their own code, even without access to the source code.
In some cases GPL violations has been proven using disassemblers. No source code is needed.

Even "Black Boxes" have had their ROMS disassembled, to show GPL violations.

The risk of getting captured is quite high, and the more a company tries to hide what they are doing, the harder they get scrutinized.

---

### Post by Bachstelze on 2009-08-28
lrn2strings ;)

For example, there's this program called [DVDFab]("http://www.dvdfab.com/"), made by some random Chinese company:

```
firas@aoba ~ % strings .wine/drive_c/Program\ Files/DVDFab\ 6/codecs.dll | grep -C 1 XviD
UUUUUU
This software is derived from the GNU GPL XviD codec (1.1.0).
Your software distributor has to give access to its source code.

```

Source code where? o.o

---

