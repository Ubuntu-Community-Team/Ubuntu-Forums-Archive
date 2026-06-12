---
title: "Upgrading memory in the eeepc"
date: 2008-01-06
forum: The Cafe
---

### Post by mendieta on 2008-01-06
Hi 

I am planning to upgrade the memory on my eeepc. My main question is: does a better timing in the memory really help ? Has anyone upgraded to a CAS-3  memory stick, for instance ? Did you notice any improvements ? (i am running geekbench to test the eee). 

Since the FSB is running, at most, at 100 mhz, you can only use 400Mhz. This means that any DDR2 stick you'll find will have enough bandwidth. The question is:is it worthwhile to spend the extra bck and get a CAS-3 memory or better ?

Many thanks in advance!

---

### Post by mendieta on 2008-01-06
Let me just add, in case it helps someone else: there is a very useful hardware FAQ here:

[http://wiki.eeeuser.com/eee_hardware_faq](http://wiki.eeeuser.com/eee_hardware_faq)

The memory section is related to this discussion. They do suggest that better timings are an important factor, but they provide no numbers. Oh well ...

---

### Post by HermanAB on 2008-01-06
2GB SODIMM, PC2-5300, 667MHz, non-ECC, Unbuffered.

In other words, El Cheapo notebook memory.

Remove power cable, remove battery, remove two screws at the bottom of the case, remove old memory, snap in new memory, re-assemble, then sell old memory on Ebay for a profit...

Linux is quite frugal with disk space and Open Office files are typically a quarter to a tenth the size of similar MS Office files, but if you do manage to fill her up with crud, buy a large camera SD card, plug it in and leave it there.

---

### Post by mendieta on 2008-01-06
> **HermanAB said:**
> 2GB SODIMM, PC2-5300, 667MHz, non-ECC, Unbuffered.


Thanks Herman! I assume that's what you are using, the issue I am tryingto decide really is latency. Should I pay for it ? What's your CAS/CL ? Do you have the model number ? Have you run geek bench ? I have mine overclocked to FSB @105 Mhz stable (with xandros). This is my entry (still using the memory it came with, no idea what's the cas, I assume 5):

[http://browse.geekbench.ca/geekbench2/view/31416](http://browse.geekbench.ca/geekbench2/view/31416)

I also have an entry with the FSB@ 100Mhz

[http://browse.geekbench.ca/geekbench2/view/31411](http://browse.geekbench.ca/geekbench2/view/31411)

Anyways, thanks, any info is appreciated!

---

### Post by mendieta on 2008-02-02
Ok, I finally bought the cheapest 1GB 200 pin DDR2 RAM I could find. 

[http://www.google.com/products?q=Kingston+1GB+PC2-5300+667MHz+200-pin+SO-DIMM+DDR2+Laptop+Memory&ie=UTF-8&oe=utf-8&rls=org.mozilla:en-US:official&client=firefox-a&um=1](http://www.google.com/products?q=Kingston+1GB+PC2-5300+667MHz+200-pin+SO-DIMM+DDR2+Laptop+Memory&ie=UTF-8&oe=utf-8&rls=org.mozilla:en-US:official&client=firefox-a&um=1)

When I bought it, it cost me  USD10 including free shipping (with a google checkout -10$ promotion at buy.com - but their prices fluctuate up and down). 

This memory is CAS 5, 667 Mhz. I read in eeeuser.com some comments suggesting that the memory runs automatically at a lower CAS if used at a lower freq (400 Mhz in this case).  I can't confirm that.  And I doubt ASUS will ever provide a BIOS that allows to select the memory timings.

Performance is similar as before (3% better in geekbench). For my usage, the original 512 Mb was just fine, but now I have extra room if I happen to have many applications open, and for 10bucks, I am the happier camper :-)

For the record, this is my latest geekbench @ 100 Mhz with the new memory module:
[http://browse.geekbench.ca/geekbench2/view/36477](http://browse.geekbench.ca/geekbench2/view/36477)

---

