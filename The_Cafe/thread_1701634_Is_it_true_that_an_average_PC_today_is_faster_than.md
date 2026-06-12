---
title: "Is it true that an average PC today is faster than the best supercomputer in 1990?"
date: 2011-03-06
forum: The Cafe
---

### Post by brawnypandora0 on 2011-03-06
If not, then which year? 1980? 1970?

---

### Post by Dustin2128 on 2011-03-06
> **brawnypandora0 said:**
> If not, then which year? 1980? 1970?
Well if we're talking pure FLOPS, my GPU alone is more powerful than anything that comes around before '96.

---

### Post by brawnypandora0 on 2011-03-08
so does that mean FLOPS is a meaningless benchmark?

---

### Post by 3Miro on 2011-03-08
> **brawnypandora0 said:**
> so does that mean FLOPS is a meaningless benchmark?

FLOPS measure raw power, another question is whether or not your program can correctly utilize the architecture to use those FLOPS. In the case of GPU for example, making a program that uses the FLOPS is harder, there are many algorithms that simply don't run well on it.

CPU flops should be a good indicator since there hasn't been any significant difference in CPU architecture for quite some time. Technically Ubuntu should run on a 386 machine (Terminal not graphics).

Supercomputer clusters, also have hard time solving some problems, so it is not always possible to reach the maximum number of FLOPS.

In terms of FLOPS, yet the average PC today is more powerful than the supercomputers of 1990 (maybe not the best one, you will have to look at actual statistics).

---

### Post by handy on 2011-03-08
Apparently the average family car has more computer power (since around 1986) than Apollo 11, had when it landed on the Moon in 1969.

Hard for my little brain to fathom, that...

---

### Post by c_cinq on 2011-03-08
the average pc today - no. 
  
FLOPS for the #1 supercomputer in 1993 starts at 10^12. [http://upload.wikimedia.org/wikipedia/commons/thumb/5/5d/Top500.svg/2000px-Top500.svg.png](http://upload.wikimedia.org/wikipedia/commons/thumb/5/5d/Top500.svg/2000px-Top500.svg.png)

---

### Post by Dustin2128 on 2011-03-08
> **c_cinq said:**
> the average pc today - no. 
  
FLOPS for the #1 supercomputer in 1993 starts at 10^12. [http://upload.wikimedia.org/wikipedia/commons/thumb/5/5d/Top500.svg/2000px-Top500.svg.png](http://upload.wikimedia.org/wikipedia/commons/thumb/5/5d/Top500.svg/2000px-Top500.svg.png)
Not the *average* PC then. Best way to maximize your FLOPS seems to be GPUs, the new radeon HD 6990 has an orgasmic 5.4 teraflops (5.4 x 10^12 floating point operations a second... my god..) max computing power alone.... *drools*...

---

### Post by 3Miro on 2011-03-08
> **Dustin2128 said:**
> Not the *average* PC then. Best way to maximize your FLOPS seems to be GPUs, the new radeon HD 6990 has an orgasmic 5.4 teraflops (5.4 x 10^12 floating point operations a second... my god..) max computing power alone.... *drools*...

Wow, they go over 1 teraflop even on double-precision ... I need paper-towel.

Too bad the architecture is restrictive on what kind of algorithm you can run on it.

---

### Post by Dustin2128 on 2011-03-08
> **3Miro said:**
> Wow, they go over 1 teraflop even on double-precision ... I need paper-towel.

Too bad the architecture is restrictive on what kind of algorithm you can run on it.
With that kind of power, let alone what you'd get if you crossfired a few of them (with 200 of these, less than 160,000$ I could have a petaflop in my basement!), I would be hopeful about the future of GPGPUs (general purpose GPUs) except for the mass proliferation of integrated models.

---

### Post by mips on 2011-03-08
> **handy said:**
> Apparently the average family car has more computer power (since around 1986) than Apollo 11, had when it landed on the Moon in 1969.

Hard for my little brain to fathom, that...

[http://en.wikipedia.org/wiki/Apollo_Guidance_Computer](http://en.wikipedia.org/wiki/Apollo_Guidance_Computer)

My calculator from school days in the 80's was more powerful but needless to say it never got me to the moon and back :lolflag:

---

### Post by jerenept on 2011-03-08
> **Dustin2128 said:**
> With that kind of power, let alone what you'd get if you crossfired a few of them (with 200 of these, less than 160,000$ I could have a petaflop in my basement!), I would be hopeful about the future of GPGPUs (general purpose GPUs) except for the mass proliferation of integrated models.

Well, you could put all those FLOPS to good use u know.... (see sig) unfortunately, gpu folding only works in windows afaik..

---

### Post by Dustin2128 on 2011-03-08
> **jerenept said:**
> Well, you could put all those FLOPS to good use u know.... (see sig) unfortunately, gpu folding only works in windows afaik..
I think I had the option (SETI@Home though) to use an nvidia GPU to do it. Had a Ti 4800 at the time though, so I figured it wouldn't be new enough.

---

### Post by 3Miro on 2011-03-08
> **jerenept said:**
> Well, you could put all those FLOPS to good use u know.... (see sig) unfortunately, gpu folding only works in windows afaik..

There is no way you cannot cluster GPUs under Linux. Supercomputing and Hollywood CGI (which is more supercomputing) are both Linux dominated.

Come to think of it, I don't see anything special about it. MPI should be able to handle this out-of-the-box.

---

### Post by jerenept on 2011-03-08
> **3Miro said:**
> There is no way you cannot cluster GPUs under Linux. Supercomputing and Hollywood CGI (which is more supercomputing) are both Linux dominated.

Come to think of it, I don't see anything special about it. MPI should be able to handle this out-of-the-box.

GPU folding, as in, Folding@Home. There is currently no FAH GPU client.

---

### Post by 3Miro on 2011-03-08
> **jerenept said:**
> GPU folding, as in, Folding@Home. There is currently no FAH GPU client.

Just read it. They are using the Internet to connect ... well they might as well use windows as the OS. This may be a cool idea, but  you will never be able to do anything practical on this.

You can build your own home cluster with or without GPUs using Linux (or windows) and it will outperform Folding@Home at every reasonable problem.

---

### Post by jerenept on 2011-03-08
> **3Miro said:**
> Just read it. They are using the Internet to connect ... well they might as well use windows as the OS. This may be a cool idea, but  you will never be able to do anything practical on this.

You can build your own home cluster with or without GPUs using Linux (or windows) and it will outperform Folding@Home at every reasonable problem.
[https://secure.wikimedia.org/wikipedia/en/wiki/Folding@home]("https://secure.wikimedia.org/wikipedia/en/wiki/Folding%40home")
???
You don't know FAH too well, it seems :P.
More FLOPS than the top 5 supercomputers COMBINED. (I think even top 10)
and they already have a GPU client, and a PS3 client, so you would be hard-pressed to surpass them on your own budget, with your own computers, i'd think.

---

### Post by 3Miro on 2011-03-08
> **jerenept said:**
> [https://secure.wikimedia.org/wikipedia/en/wiki/Folding@home]("https://secure.wikimedia.org/wikipedia/en/wiki/Folding%40home")
???
You don't know FAH too well, it seems :P.
More FLOPS than the top 5 supercomputers COMBINED. (I think even top 10)
and they already have a GPU client, and a PS3 client, so you would be hard-pressed to surpass them on your own budget, with your own computers, i'd think.

Have you ever programmed for a cluster? Pure FLOPS are secondary to the communication speed and that is when dual 1Gb LAN is too slow. With the Internet, they can never sync two machines to work on the same problem fast enough, that is unless it is a very and I mean VERY special problem. Folding@Home does work on a very special problem. It is unfair to compare FAH to any general purpose supercomputer.

---

### Post by jerenept on 2011-03-08
> **3Miro said:**
> Have you ever programmed for a cluster? Pure FLOPS are secondary to the communication speed and that is when dual 1Gb LAN is too slow. With the Internet, they can never sync two machines to work on the same problem fast enough, that is unless it is a very and I mean VERY special problem. Folding@Home does work on a very special problem. It is unfair to compare FAH to any general purpose supercomputer.

Yesh, those problems are called "Embarrassingly parallel" and there's a Wikipedia article on it too.....

Now, topic, back on it, can we go?

---

### Post by Dustin2128 on 2011-03-08
Offtopic again, but what's with the proprietary license on F@H? What do they have to gain by it?

---

### Post by jerenept on 2011-03-08
> **handy said:**
> Apparently the average family car has more computer power (since around 1986) than Apollo 11, had when it landed on the Moon in 1969.

Hard for my little brain to fathom, that...

the average family car has more computer power than the Space Shuttle, so, your point?

---

### Post by jerenept on 2011-03-08
> **Dustin2128 said:**
> Offtopic again, but what's with the proprietary license on F@H? What do they have to gain by it?

If they release it with an oss license, they'd have to provide the source, and that would make competitive folding pointless. [FAQ]("http://folding.stanford.edu/English/FAQ-OpenSource")?

---

### Post by amysmith28 on 2011-03-08
> **3Miro said:**
> FLOPS measure raw power, another question is whether or not your program can correctly utilize the architecture to use those FLOPS. In the case of GPU for example, making a program that uses the FLOPS is harder, there are many algorithms that simply don't run well on it.
 
CPU flops should be a good indicator since there hasn't been any significant difference in CPU architecture for quite some time. Technically Ubuntu should run on a 386 machine (Terminal not graphics).
 
Supercomputer clusters, also have hard time solving some problems, so it is not always possible to reach the maximum number of FLOPS.
 
In terms of FLOPS, yet the average PC today is more powerful than the supercomputers of 1990 (maybe not the best one, you will have to look at actual statistics).
 
I think so

---

### Post by Dustin2128 on 2011-03-08
> **jerenept said:**
> If they release it with an oss license, they'd have to provide the source, and that would make competitive folding pointless. [FAQ]("http://folding.stanford.edu/English/FAQ-OpenSource")?
Eh, lame excuse. I shall continue donating excess C/GPU to SETI@Home!

---

### Post by handy on 2011-03-08
> **mips said:**
> [http://en.wikipedia.org/wiki/Apollo_Guidance_Computer](http://en.wikipedia.org/wiki/Apollo_Guidance_Computer)

My calculator from school days in the 80's was more powerful but needless to say it never got me to the moon and back :lolflag:

You are obviously younger than I am mips. They hadn't even invented hand held calculators when I went to school! :shock:

I think many of our teachers still thought that the Earth was flat & the entire universe revolved around it. ***[edit:]** No, they thought it revolved around them.*

---

### Post by cascade9 on 2011-03-09
GigaFLOPS, LOL. Old but well worth the read- 

[http://www.dansdata.com/gz017.htm](http://www.dansdata.com/gz017.htm)

> **handy said:**
> Apparently the average family car has more computer power (since around 1986) than Apollo 11, had when it landed on the Moon in 1969.

Hard for my little brain to fathom, that...

Maybe if you just look at numbers, but the strength of the apollo computers was software, not hardware- 

[http://downloadsquad.switched.com/2009/07/20/how-powerful-was-the-apollo-11-computer/](http://downloadsquad.switched.com/2009/07/20/how-powerful-was-the-apollo-11-computer/)

---

### Post by disabledaccount on 2011-03-09
> **jerenept said:**
> the average family car has more computer power than the Space Shuttle, so, your point?Thats actually not true or at least not provable - car computers are very simple, highly specialized PLDs that can easily be called "dumb" chips.  You can compute A+B, but B+A is not supported :) - its even hard to tell how much MIPS they have...
Even such subsytems like ABS or ASR are very simple - what doesn't change the fact that it took decades to invent algorithms, sensors and chips.

---

### Post by HermanAB on 2011-03-09
PC are fast when you want to add 1+1 and get approximately 2.  

They are however not able to keep up with the massive I/O capabilities of even 1970s era mainframes.

---

### Post by Paqman on 2011-03-09
Comparing benchmarks of a general purpose PC to a supercomputer is apples and oranges. Supercomputers are generally optimised to deal with certain specific types of data sets, so looking at a simple metric like FLOPS doesn't tell the whole story.

---

### Post by handy on 2011-03-09
> **cascade9 said:**
> 
...
Maybe if you just look at numbers, but the strength of the apollo computers was software, not hardware-  

It had to be!

I try to convince my wife about the value of software as opposed to hardware. Thus far to no avail...

---

### Post by Sean Moran on 2011-03-09
I'd take a rough "stab-in-the-dark" guess that it's not true, because the average 1990 supercomputer users didn't have to waste most of their time on FaceBook or Twitter or social networking forums like this.;)

---

