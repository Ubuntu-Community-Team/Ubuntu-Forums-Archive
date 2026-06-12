---
title: "Sse2"
date: 2007-04-27
forum: The Cafe
---

### Post by sushii. on 2007-04-27
Sorry for the n00b question, but what is SSE2, and can I get it without having to buy a new processor?

---

### Post by %hMa@?b&lt;C on 2007-04-27
[http://en.wikipedia.org/wiki/SSE2](http://en.wikipedia.org/wiki/SSE2)
no, you cannot download sse2, just as you cant download new ram.  it is part of the hardware.  Most new processors, such as my opteron have sse3 now-adays.

---

### Post by reclusivemonkey on 2007-04-28
> **sushii. said:**
> Sorry for the n00b question, but what is SSE2, and can I get it without having to buy a new processor?

Are you sure you don't have it?

```

cat /proc/cpuinfo | grep flags

```

If it appears there, you have it.

---

### Post by Ampi on 2008-04-08
Hmm, I have the exact same problem. Apparently I do have sse, is it possible to upgrade to sse2??

---

### Post by igknighted on 2008-04-08
> **Ampi said:**
> Hmm, I have the exact same problem. Apparently I do have sse, is it possible to upgrade to sse2??

Yup... with a new chip.  Pretty much any chip from the last 4 years has SSE2.

---

### Post by Ampi on 2008-04-08
being a complete n00b over here :)

new chip, means I have to buy something, right?? And what exactly?
And it that the only way to get matlab running? (I'm guessing yes :()

---

### Post by igknighted on 2008-04-08
> **Ampi said:**
> being a complete n00b over here :)

new chip, means I have to buy something, right?? And what exactly?
And it that the only way to get matlab running? (I'm guessing yes :()

Yes, it does mean buying something.  If you can post your hardware specs we could probably point you to a chip that would be a drop in replacement (probably under $50) for your current setup.  It's a dead simple upgrade (only slightly more difficult than adding ram) if you wanna give it a shot.

*note, this is assuming your mobo can handle a newer chip... not necessarily a given.  Thats why we need your precise specs.

---

### Post by Ampi on 2008-04-09
I am not really sure what my specs are so here is the output of commands that seem to give this kind of information...

How does a new chip compare to buying a new computer?

Except for my computer box, I have nice hardware. My computer box is simply seven years old and working surprisingly well (=quick) and can handle a lot. But I can imagine that it is old. 
The only thing with the sse2 is that I need this kind of software, but I am not really willing to go back to Intel on my desktop. 

So the **real question** is if I consider buying a new computer then I'll have a "good" chip but does buying a "good" chip alone allow me the postpone the new computer for a couple years? 

```

$ cat /proc/meminfo

MemTotal:       255944 kB
MemFree:         17324 kB
Buffers:          6244 kB
Cached:         113356 kB
SwapCached:         40 kB
Active:         154820 kB
Inactive:        57892 kB
HighTotal:           0 kB
HighFree:            0 kB
LowTotal:       255944 kB
LowFree:         17324 kB
SwapTotal:      746980 kB
SwapFree:       712268 kB
Dirty:             384 kB
Writeback:           0 kB
AnonPages:       93108 kB
Mapped:          46076 kB
Slab:            12196 kB
SReclaimable:     5524 kB
SUnreclaim:       6672 kB
PageTables:       1488 kB
NFS_Unstable:        0 kB
Bounce:              0 kB
CommitLimit:    874952 kB
Committed_AS:   395388 kB
VmallocTotal:   770040 kB
VmallocUsed:     26648 kB
VmallocChunk:   740340 kB

```

```

$ cat 

processor       : 0
vendor_id       : AuthenticAMD
cpu family      : 6
model           : 6
model name      : AMD Athlon(tm) Processor
stepping        : 2
cpu MHz         : 1150.037
cache size      : 256 KB
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 1
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 mmx fxsr sse syscall mp mmxext 3dnowext 3dnow up ts
bogomips        : 2302.49
clflush size    : 32

```

---

