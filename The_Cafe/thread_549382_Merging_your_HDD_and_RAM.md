---
title: "Merging your HDD and RAM"
date: 2007-09-12
forum: The Cafe
---

### Post by casperlingus on 2007-09-12
For those of you who don't read slashdot.org, here is an interesting article that, with some luck, will pan out to be true.

[http://www.nytimes.com/2007/09/11/technology/11storage.html?_r=1&ref=technology&oref=slogin](http://www.nytimes.com/2007/09/11/technology/11storage.html?_r=1&ref=technology&oref=slogin)

If this technology matures, it sounds like standard computer configurations could have 30-terabyte drives, which would provide both RAM and long-term storage.

I don't know much about hardware or the kernel, but it's not difficult to see profound implications for computing in general.   My problem is, I can't visualize the results since I have no experience.

Is it likely that there would no longer be a need for "RAM" at all?  Rather, the disk would just be one giant address space where everything at all times is considered "Random access memory", even the long term memory?  Or would it still be partitioned into separate partitions for short- and long-term memory.  I suppose it would really all be called "long-term memory" since it would maintain its state even after losing power.  There would probably be no more booting.

Mostly, I'd just like to hear some discussion from knowledgeable people about the future of computing if technology like this matures.

---

### Post by asmoore82 on 2007-09-12
the writer of the article seems wide-eyed and naive ...

RAM isn't going anywhere because of the extreme speed of memory
needed to keep up with a CPU.
memory is layered in a desperate effort to keep cost down and performance up.

The fastest memory in any given system is the L1 cache. Naturally,
it is also one of the most expensive components so it is the memory
you have the least of. Next larger, slower and cheaper is the L2 cache;
next larger and cheaper is the RAM (which is 10 times slower than cache);
and finally you come down to cheap and non-volatile memory
the hard drive(which is 1000 times slower than RAM)((also, a device
that must have onboard cache of its own, in the interest of performance)).

likewise the logic behind this cost/performance balancing scheme
is the meaning of the term 'cache,' for you see the CPU never  actually
communticates with the RAM; it accesses the cache which
in turn accesses the RAM which in turn through DMA can contain
cached data from the hard disk.

If they can fit the entire Library of Congress into an iPod(slow strorage),
that would be *cute*;
but my boss's brand new rig with dual core CPU and 2 Gigs of RAM
still has only 64 *kilo*bytes(KB) of L1 Cache(fast storage).

---

### Post by user1397 on 2007-09-12
> **asmoore82 said:**
> the writer of the article seems wide-eyed and naive ...

RAM isn't going anywhere because of the extreme speed of memory
needed to keep up with a CPU.
memory is layered in a desperate effort to keep cost down and performance up.

The fastest memory in any given system is the L1 cache. Naturally,
it is also one of the most expensive components so it is the memory
you have the least of. Next larger, slower and cheaper is the L2 cache;
next larger and cheaper is the RAM (which is 10 times slower than cache);
and finally you come down to cheap and non-volatile memory
the hard drive(which is 1000 times slower than RAM)((also, a device
that must have onboard cache of its own, in the interest of performance)).

likewise the logic behind this cost/performance balancing scheme
is the meaning of the term 'cache,' for you see the CPU never  actually
communticates with the RAM; it accesses the cache which
in turn accesses the RAM which in turn through DMA can contain
cached data from the hard disk.

If they can fit the entire Library of Congress into an iPod(slow strorage),
that would be *cute*;
but my boss's brand new rig with dual core CPU and 2 Gigs of RAM
still has only 64 *kilo*bytes(KB) of L1 Cache(fast storage).how can u check how much L1 and L2 cache you have in ur PC? (in windows i mean)

---

### Post by hessiess on 2007-09-12
if a hard drive is 1000 times slower than ram, couldent you just run 1000 small ones as an array?

---

### Post by regomodo on 2007-09-12
@ asmoore - the reason why you get small cache is not just price but also to do with distances (induction in tracks at high frequencies?) between the memory and cpu

@ ubuntumann - cat /proc/cpuinfo (just fully read your question - use sisandra)

---

### Post by conehead77 on 2007-09-12
> **hessiess said:**
> if a hard drive is 1000 times slower than ram, couldent you just run 1000 small ones as an array?

That wouldnt work. The processor exchanges data only with the cache which is very fast. The data in the cache was taken from the RAM before and from HD to RAM.
But the most important thing is the amount of data transfers. The CPU communicates with the cache very often. Cache requests to RAM are less frequent, RAM requests to HD even more.
So if you would communicate directly from CPU to HD it would slow down too much to do sthg useful, because the CPU would have to do all data transfer to the slow HD.

My english isnt the best, but maybe you get the idea...

---

### Post by Rui Pais on 2007-09-29
> **ubuntuman001 said:**
> how can u check how much L1 and L2 cache you have in ur PC? (in windows i mean)

> **regomodo said:**
> 
@ ubuntumann - cat /proc/cpuinfo (just fully read your question - use sisandra)

hi, i know this is a little old, but anyway...
one simple way to check L1 qnd L" cache size under Linux is using lshw. It's under cpu section.

hth

---

