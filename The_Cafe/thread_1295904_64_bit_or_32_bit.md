---
title: "64 bit or 32 bit?"
date: 2009-10-20
forum: The Cafe
---

### Post by running_rabbit07 on 2009-10-20
Which do believe runs faster?

---

### Post by keiichidono on 2009-10-20
I foresee this thread ending up in reccuring discussions.

---

### Post by Simian Man on 2009-10-20
Assuming you mean x86 vs. x86-64 instruction sets on common processors, it depends very much on the applications.  For any CPU intensive benchmarks, 64 bits can be much faster because of the increased processor bandwidth.  The x86-64 ISA includes other improvements such as more addressable registers which can prevent memory spills.  On memory bound processes, however, the extra memory traffic of 64-bit instructions can degrade performance of caches.

---

### Post by running_rabbit07 on 2009-10-20
> **CalvinB said:**
> I foresee this thread ending up in reccuring discussions.

Probably. Or, being merged with the [2011 32 bit systems becomes junkies...]("http://ubuntuforums.org/showthread.php?t=1295723")

---

### Post by RiceMonster on 2009-10-20
Real geeks use 256 bit

---

### Post by Skripka on 2009-10-20
> **RiceMonster said:**
> Real geeks use 256 bit

Hah.  I have a 364 & 2/3-bit CPU in my toaster that runs HURD with E17.  HAH!

---

### Post by coldReactive on 2009-10-20
I'm going to refrain from voting in this poll, because a 32-bit system CAN run faster than a 64-bit system that runs faster than another 32-bit system that runs faster than a............

---

### Post by Xbehave on 2009-10-20
Whats the point of this thread? who cares what people believe, what about facts:
[LIST][COLOR="Lime"][*][/COLOR]64bit systems can map large files to memory (e.g if you use a VM/deal with dvds,etc)
[COLOR="Lime"][*][/COLOR]64bit systems can handle 64bits at a time(e.g media processing/databases, etc)
[COLOR="Red"][*][/COLOR]however 64bit systems use more memory (i don't know how much, but probably not much)
[COLOR="Blue"][*][/COLOR]64bit has a bigger address space so may be more secure (I just made this one up but if ASLR worked properly this would be true)
[COLOR="Blue"][*][/COLOR]64bit can use more ram (however 32bit systems with PAE can do this too)
[/LIST]

---

