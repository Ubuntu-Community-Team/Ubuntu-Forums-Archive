---
title: "Random 32 Bit Question"
date: 2007-12-26
forum: The Cafe
---

### Post by Black Mage on 2007-12-26
I'm doing some research on 32 vs 64, and I came across a question that  I'm not really sure what the answer is. Is the maximum amount of ram allowed in 32 bit 4 gigabytes?

---

### Post by -grubby on 2007-12-26
I believe that it's 3 GB. it's technically 4 GB but I think it's reserved for something or other. Just wait until someone else can give a better answer

---

### Post by p_quarles on 2007-12-26
From wikipedia:
> Most CPUs are currently (as of 2005) designed so that the contents of a single integer register can store the [address]("http://en.wikipedia.org/wiki/Memory_address") (location) of any datum in the computer's [virtual memory]("http://en.wikipedia.org/wiki/Virtual_memory"). Therefore, the total number of addresses in the virtual memory &#8211; the total amount of data the computer can keep in its working area &#8211; is determined by the width of these registers. Beginning in the 1960s with the [IBM]("http://en.wikipedia.org/wiki/IBM") [System/360]("http://en.wikipedia.org/wiki/System/360"), then (amongst many others) the [DEC]("http://en.wikipedia.org/wiki/Digital_Equipment_Corporation") [VAX]("http://en.wikipedia.org/wiki/VAX") minicomputer in the [1970s]("http://en.wikipedia.org/wiki/1970s"), and then with the [Intel 80386]("http://en.wikipedia.org/wiki/Intel_80386") in the mid-[1980s]("http://en.wikipedia.org/wiki/1980s"), a *de facto* consensus developed that 32 bits was a convenient register size. A 32-bit register meant that 232 addresses, or 4 [gigabytes]("http://en.wikipedia.org/wiki/Gigabyte") of [RAM]("http://en.wikipedia.org/wiki/Random_Access_Memory"), could be referenced. At the time these architectures were devised, 4 gigabytes of memory was so far beyond the typical quantities available in installations that this was considered to be enough "headroom" for addressing. 4-gigabyte addresses were considered an appropriate size to work with for another important reason: 4 billion integers are enough to assign unique references to most physically countable things in applications like [databases]("http://en.wikipedia.org/wiki/Database").
[Full article]("http://en.wikipedia.org/wiki/64-bit")

---

### Post by Black Mage on 2007-12-26
Alright, so 64 bit processor can support 16 exabytes, which is larger than 16 gigabytes then....how large is an exabyte in terms of gigabytes?

---

### Post by p_quarles on 2007-12-26
Well, like the article says, 16 exabytes is roughly equivalent ot 17 billion gigabytes. 

16 exabytes ought to be enough for anyone. :D

---

### Post by Steveway on 2007-12-26
If you are doing researches then why don't you use wikipedia?
It has all been answered there allready, go and use it.

---

### Post by -grubby on 2007-12-26
> **p_quarles said:**
> 

16 exabytes ought to be enough for anyone. :D
:lolflag:

---

### Post by new2*buntu on 2007-12-26
> **p_quarles said:**
> Well, like the article says, 16 exabytes is roughly equivalent ot 17 billion gigabytes. 

16 exabytes ought to be enough for anyone. :D

And that's what they thought of 4 GB when they developed it. Who knows, maybe Microsoft is planning their latest and greatest Windoze to use about 10 billion gigabytes :lolflag:

---

### Post by p_quarles on 2007-12-26
> **new2*buntu said:**
> And that's what they thought of 4 GB when they developed it. Who knows, maybe Microsoft is planning their latest and greatest Windoze to use about 10 billion gigabytes :lolflag:
Yeah, I know. I was alluding to this: [http://en.wikiquote.org/wiki/Bill_Gates#Misattributed](http://en.wikiquote.org/wiki/Bill_Gates#Misattributed)

---

### Post by new2*buntu on 2007-12-26
> **p_quarles said:**
> Yeah, I know. I was alluding to this: [http://en.wikiquote.org/wiki/Bill_Gates#Misattributed](http://en.wikiquote.org/wiki/Bill_Gates#Misattributed)

I see now.

---

### Post by bufsabre666 on 2007-12-26
> **p_quarles said:**
> Yeah, I know. I was alluding to this: [http://en.wikiquote.org/wiki/Bill_Gates#Misattributed](http://en.wikiquote.org/wiki/Bill_Gates#Misattributed)

ahh good ole billy

---

### Post by Black Mage on 2007-12-27
Okay, I decided I'm going to buy a warehouse, lay everything with RAM connectors, and try to connect 17 billion sticks of RAM.

Who wants to join me? Afterwards we'll play all three versions of halo at the same time and not worry about memory.

---

### Post by forrestcupp on 2007-12-27
> **p_quarles said:**
> From wikipedia:

[Full article]("http://en.wikipedia.org/wiki/64-bit")

That depends on how you figure 1 GB.  Some say that 1 GB is exactly 1 billion bytes and some figure it as around 1.07 billion bytes which is 1028 to the power of 3.

For that reason, a 32-bit OS can really only access around 3.74 GB.

---

### Post by p_quarles on 2007-12-27
> **forrestcupp said:**
> That depends on how you figure 1 GB.  Some say that 1 GB is exactly 1 billion bytes and some figure it as around 1.07 billion bytes which is 1028 to the power of 3.

For that reason, a 32-bit OS can really only access around 3.74 GB.
I think the current standard is to use "gigabyte" (GB) for 1 billion bytes, and "gibibyte" (GiB) for 1.073 billion bytes.

---

### Post by GSF1200S on 2007-12-27
> **forrestcupp said:**
> That depends on how you figure 1 GB.  Some say that 1 GB is exactly 1 billion bytes and some figure it as around 1.07 billion bytes which is 1028 to the power of 3.

For that reason, a 32-bit OS can really only access around 3.74 GB.

I was building a laptop just for fun (on dells site I think) and of course, since you dont have an option, it had vista basic. I selected 4GB of RAM, and it actually says that the task manager will only show 3.5GB as a result of 32bit limitations. That seems to support what you say here...

---

### Post by toupeiro on 2007-12-27
> **p_quarles said:**
> 
16 exabytes ought to be enough for anyone. :D

> 
640k ought to be enough for anyone -Bill Gates 

hehe, sorry p_quarles, I just I love these assumptions.. :-D 

Here's a little estimation I throw out there just by doing support.

Data is much more valuable than hardware.  The cheaper the cost to store one gigabyte becomes, and the larger a single disk becomes, combined with commodity RAID storage , larger dataspaces will be required, the  larger software footprints will become.  That software footprint will need to be accessed efficiently, indexed, and cached, so  more RAM will be needed to serve the data stored on arrays configured of multi-terrabyte disks.  This is just todays analysis, with numbers reflecting todays situation.  

People will buy another hard drive and RAM before they delete anything anymore, and so will companies.  Now, take that statement and  step from the home world into the business world and take a company with a data footprint in multiple petabytes today.  Is it still practical that 16exabytes should be enough for anyone?

In my experience, the first development company that assumes to be able to profile the computing demands of the world and attempts to enforce their profile on their customers is the same development company that ends up hamstringing themselves down the line for their assumptions, rather than develop with their eyes looking forward and their ears and minds open, listening to what the computing industry is asking for.

long story short, no limit to data storage or data access is ever *enough* because demand to store generated data will never stop.  64-bit hardware has been around a long while now.  Just recently in commodity hardware.  Its time will come.  Most likely much sooner than we all think.

thats just my .02 as an end user at home that also does enterprise support for a living.  :)

:edit:
  For all practical purposes today, the chances of someone ever addressing 16 exabytes in a single machine is unlikely for quite some time, so I know what p_quarles meant.  I'm just taking that idea a little bit further into the future.

---

### Post by p_quarles on 2007-12-27
Umm, what? I think I already explained that I was humorously alluding to the Gates mis-quote (he claims never to have said that, and there's no evidence that he did). Jokes != assumptions.

---

### Post by toupeiro on 2007-12-27
> **p_quarles said:**
> Umm, what? I think I already explained that I was humorously alluding to the Gates mis-quote (he claims never to have said that, and there's no evidence that he did). Jokes != assumptions.

hehe ok, take it easy!  I wasn't attacking you, I was just elaborating on statements like that.  So you were joking, thats fine.  I != took that statement seriously from you.

---

### Post by Black Mage on 2007-12-27
So right now my computer is a Quad Core Q660 and my motherboard is Gigabyte and I'm running a 64-bit version of Ubuntu with the full 8 gigabytes of RAM my motherboard can hold. If I installed a 32-bit version of Ubuntu, I would only be able to use the 4 gigs even though my hardware can support 64 bits?

---

### Post by gn2 on 2007-12-27
> **Black Mage said:**
> So right now my computer is a Quad Core Q660 and my motherboard is Gigabyte and I'm running a 64-bit version of Ubuntu with the full 8 gigabytes of RAM my motherboard can hold. If I installed a 32-bit version of Ubuntu, I would only be able to use the 4 gigs even though my hardware can support 64 bits?

Have you checked that all 8gb is recognised and used?

How much RAM can be used by 32 bit is dependent on the OS.
It varies from one to another.

---

### Post by p_quarles on 2007-12-27
> **Black Mage said:**
> So right now my computer is a Quad Core Q660 and my motherboard is Gigabyte and I'm running a 64-bit version of Ubuntu with the full 8 gigabytes of RAM my motherboard can hold. If I installed a 32-bit version of Ubuntu, I would only be able to use the 4 gigs even though my hardware can support 64 bits?
Correct. If you installed the 32-bit version, you would be using the processor as though it were 32 bits wide -- the OS would not be capable of making use of the extra width, and therefore it would not be able to address more than 4GB/3.7GiB of memory. 

I recall, however, that there are kernel hacks that can allows 32-bit systems to make partial use of memory beyond 4GB, but I don't know much about that.

---

### Post by Steveway on 2007-12-27
> **p_quarles said:**
> Correct. If you installed the 32-bit version, you would be using the processor as though it were 32 bits wide -- the OS would not be capable of making use of the extra width, and therefore it would not be able to address more than 4GB/3.7GiB of memory. 

I recall, however, that there are kernel hacks that can allows 32-bit systems to make partial use of memory beyond 4GB, but I don't know much about that.

Yes, that is correct. It is often reffered to as a bigmen or  highmem-kernel.
This allows 32bit systems to address more than the usual 4 gigs of memory, the only drawback is that it is slower than the usual way.

---

