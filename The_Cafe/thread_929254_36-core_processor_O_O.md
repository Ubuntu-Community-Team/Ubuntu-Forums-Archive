---
title: "36-core processor O_O"
date: 2008-09-24
forum: The Cafe
---

### Post by Lord Xeb on 2008-09-24
[http://www.maximumpc.com/article/news/tilera_adds_36core_chip_its_arsenal](http://www.maximumpc.com/article/news/tilera_adds_36core_chip_its_arsenal)


I just thought that this was a little interesting. I wonder about if I can run linux on it if I can get one :D

---

### Post by zmjjmz on 2008-09-24
Intel wasn't kidding when they were talking about a ******** of cores on future processors.

---

### Post by smartboyathome on 2008-09-24
Now THAT is power. I would take that with 24 gigs ram. ;)

---

### Post by Lord Xeb on 2008-09-24
Same here :D Hell, I would see if it would overclock and see how well it works on games >_> LOL like that will happen.

---

### Post by smartboyathome on 2008-09-24
How about that 36 core processor in [this computer]("http://www.mil-embedded.com/news/db/?12016")? That would be pure awesomeness. :D

---

### Post by Lord Xeb on 2008-09-24
Hmmm... interesting.

---

### Post by zmjjmz on 2008-09-24
> **smartboyathome said:**
> How about that 36 core processor in [this computer]("http://www.mil-embedded.com/news/db/?12016")? That would be pure awesomeness. :D

They cannot possibly be running XP on that.

---

### Post by bruce89 on 2008-09-24
> **zmjjmz said:**
> They cannot possibly be running XP on that.

No-one would find out if "only" 8 or something cores were being used.

---

### Post by Lord Xeb on 2008-09-24
Hell no. It will be a custom made OS :D

---

### Post by MaxIBoy on 2008-09-24
> Intel and AMD needn't be worried though, as the Tilera doesn't target servers and home PCs, as the architecture would get summarily thumped by today's fastest chips. But for its targeted applications, the tiled RISC processing core puts out a bit of pep when configured in a distributed network, and the new 36-core version only sips between 10 to 16 watts. Not only that, most games aren't optimized for multithreaded processing and only use one or two cores in a multicore system.

---

### Post by zmjjmz on 2008-09-24
> **MaxIBoy said:**
> Not only that, most games aren't optimized for multithreaded processing and only use one or two cores in a multicore system.

It's probably better for intense VM'ing.

---

### Post by Mr. Picklesworth on 2008-09-24
My favourite part of this computer is when they mention that the reason for "only" having 36 cores is because that's the maximum Windows supports at the moment, noting that Linux supports (theoretically) any number of cores.
Owned! :P

---

### Post by hardyn on 2008-09-25
> **Lord Xeb said:**
> Hell no. It will be a custom made OS :D

I bet with enough hacking you could get linux to do it.

---

### Post by MaxIBoy on 2008-09-25
Linux will run quite comfortably on most modern automotive engines, I don't see why much hacking would be needed at all.

---

### Post by ChanServ on 2008-09-25
EPIC nerdgasim

---

### Post by toupeiro on 2008-09-25
Fantastic feat, definite a game changer, but right now, even in the applicable fields, does it make sense?

36 cores
3.2 MB of cache

I admit I'm not the greatest in math, I usually always double and triple check my math, or have someone check it for me and I haven't done so here, but from what I can calculate, a parallel job where you would actually use all cores on a single chip like this with only 3.2MB of cache, you could only commit 91K Cache per core, and thats if you aren't trying to compute any single threaded or serial jobs.  

I guess its really cool bragging rights, but I'm trying to think of where would you really use this over current multi-socket multi-core systems.

If I needed a lot of cores, I'd still opt for an 8-way quad core server, like a Sunfire X4600-M2 or a Proliant DL-785.  If I needed a lot of threads, I'd still consider a chip like the UltraSPARC T2+, (128 simultaneous threads on a single chip!) over this.  

I'm excited to see that [Moore's Law]("http://en.wikipedia.org/wiki/Moore%27s_law") is alive and well all these years later, but right now I think this processor is eye-candy.  The worlds not ready for as many cores as are available now, and for supercomputing, you still want the socket dedicated RAM for faster core to memory channel I/O, the super fast hypertransport, and CACHE!

---

### Post by hardyn on 2008-09-25
highly parallelized CPUs and putting graphics back into the CPU die is what intel has been talking about for a little while, maybe not 32 cores, but 16 i think has been in their (intel) explanation of technology.  16 non-specialized cores that can be programmed to perform graphics or system computation.  As i understand from another paper that i read (no i cannot find it again) is the reason that AMD "had" to buy ATI, to acquire graphics technology to keep up with concept of high parallelization.  According to that paper in the future CPUs will be built more like GPUs, and i would have to do my homework to find out exactly how GPUs are different than CPUs.

---

### Post by MaxIBoy on 2008-09-25
GPUs are more specialized and more complex (there's a piece of the chip here for shaders, a piece of the chip there for rasterization, etc.) The hardware in a GPU can be used for general-purpose computing, but only with difficulty.

---

### Post by th-busch on 2008-09-25
interesting view on the multicore gaming thing by the co-founder of epic games: [http://arstechnica.com/articles/paedia/gpu-sweeney-interview.ars](http://arstechnica.com/articles/paedia/gpu-sweeney-interview.ars)

anyways, i would install suse linux on a computer with this cpu just to see the startup screen filled with all those penguins :lolflag:

---

### Post by lisati on 2008-09-25
Depending on where development takes this beast, would we need one of our older machines to act as a terminal?
(And yes, I first learnt ASM on an IBM 370)

---

### Post by EnGorDiaz on 2008-09-25
> **Lord Xeb said:**
> Same here :D Hell, I would see if it would overclock and see how well it works on games >_> LOL like that will happen.

you woulnt nee broaban youll only nee 1k ownloa an uploa

---

### Post by toupeiro on 2008-09-25
> **MaxIBoy said:**
> GPUs are more specialized and more complex (there's a piece of the chip here for shaders, a piece of the chip there for rasterization, etc.) The hardware in a GPU can be used for general-purpose computing, but only with difficulty.

NVidia is already using GPU for compute cycles in their Tesla line.  Pretty powerful stuff, but can be tricky to program for them.  I think if Intel wants to focus on GPU computing, they're going to have a lot stiffer competition from NVidia, who has been offering GPU blades for compute power for close to a year now commercially, if not longer.

---

### Post by jespdj on 2008-09-25
Intel already has a 80-core processor (currently only for research purposes):

[Intel Tests Chip Design With 80-Core Processor](http://www.pcworld.com/article/128924/intel_tests_chip_design_with_80core_processor.html) - 'Teraflops research chip' provides tremendous horsepower for designing and testing future PCs

[YouTube video about Intel's 80-core chip](http://www.youtube.com/watch?v=97uSsjjoSNM)

---

### Post by uberdonkey5 on 2008-09-25
within portugal they are linking large work stations together, I think there are about 3 large networks with around 120-240 in each network. However, although its great for lots of parallelised (I presume you don't say paralised) work they are still trying to work out what the optimum number is because with around 500 work stations the communications time is the limiting factor and thus it is usually optimum to work with fewer.

Isn't this the same with cores? I mean, splitting the task of opening gmail between 36 cores is probably slower than just opening it with one core. I seriously can't see practical application for the home above around 4 cores.

---

### Post by regomodo on 2008-09-25
#

---

### Post by Lord Xeb on 2008-09-25
That one sucks. This one is better.

---

### Post by hessiess on 2008-09-25
who caires, verry few aplications are actualy capable of using so meny cores.

---

### Post by uberdonkey5 on 2008-09-25
> **hessiess said:**
> who caires, verry few aplications are actualy capable of using so meny cores.

+1 (but love my duo core)
ok, I realised you said not to comment on your spelling, (I have no excuse :D) but I'm interested, does the contrast of the computer screen make it worse?? Just cos I remember when I was young a friend of mine used to use colour acetate sheets over black and white paper to reduce the contrast and seemed to help.

---

### Post by MaxIBoy on 2008-09-25
> **uberdonkey5 said:**
> within portugal they are linking large work stations together, I think there are about 3 large networks with around 120-240 in each network. However, although its great for lots of parallelised (I presume you don't say paralised) work they are still trying to work out what the optimum number is because with around 500 work stations the communications time is the limiting factor and thus it is usually optimum to work with fewer.

Isn't this the same with cores? I mean, splitting the task of opening gmail between 36 cores is probably slower than just opening it with one core. I seriously can't see practical application for the home above around 4 cores.


In theory, if the task is what is called "embarrassingly parallel," you can add as many computers to the network as you want. A good example would be a rendering farm. You can divide feature-length animated film into frames and have each computer work on rendering one at a time (or even part of one at a time,) until all the frames are fully rendered. The more computers on the network, the faster the process goes, all the way up to one computer for every pixel of every frame.:)

---

### Post by uberdonkey5 on 2008-09-25
> **MaxIBoy said:**
> In theory, if the task is what is called "embarrassingly parallel," you can add as many computers to the network as you want. A good example would be a rendering farm. You can divide feature-length animated film into frames and have each computer work on rendering one at a time (or even part of one at a time,) until all the frames are fully rendered. The more computers on the network, the faster the process goes, all the way up to one computer for every pixel of every frame.:)

yeh, good point. Suppose my tasks are not embarassingly parallel (its a spatial grid but there needs to be communication between different parts of the grid with each round of calculations), however, surely the rendering process would be better done if the software recognised that each frame was likely to be similar to the last? Who knows, I need to get a life and stop posting...

---

### Post by Lord Xeb on 2008-09-25
> **MaxIBoy said:**
> In theory, if the task is what is called "embarrassingly parallel," you can add as many computers to the network as you want. A good example would be a rendering farm. You can divide feature-length animated film into frames and have each computer work on rendering one at a time (or even part of one at a time,) until all the frames are fully rendered. The more computers on the network, the faster the process goes, all the way up to one computer for every pixel of every frame.:)
Good point.

---

### Post by hessiess on 2008-09-25
> **uberdonkey5 said:**
> +1 (but love my duo core)
ok, I realised you said not to comment on your spelling, (I have no excuse :D) but I'm interested, does the contrast of the computer screen make it worse?? Just cos I remember when I was young a friend of mine used to use colour acetate sheets over black and white paper to reduce the contrast and seemed to help.

I already have my GTK theme and firefox set to Grey backgrounds. it adds greatly to the readability, but doesn't affect the spelling. i spell everything exactly now it sounds, and fortunately firefox is able to correct most of my errors, but not all of them.
> 
In theory, if the task is what is called "embarrassingly parallel," you can add as many computers to the network as you want. A good example would be a rendering farm. You can divide feature-length animated film into frames and have each computer work on rendering one at a time (or even part of one at a time,) until all the frames are fully rendered. The more computers on the network, the faster the process goes, all the way up to one computer for every pixel of every frame.

if you had a computer for every single pixel, there would be a lot of overhead recombining all the pixels again. also you would probably run into bandwidth limitations.

---

### Post by MaxIBoy on 2008-09-25
The one computer per pixel model is theoretical. Obviously you don't want to scale up that much. 

However, you can split it up into 20-by-20 pixel tiles or something like that. Bandwidth isn't much of an issue unless you're using a network which can't handle that many computers (and in that case it's your fault for not getting a good enough network.) 


Algorithms for recompiling into a finished piece efficiently aren't hard to come up with.

---

### Post by uberdonkey5 on 2008-09-26
> **hessiess said:**
> I already have my GTK theme and firefox set to Grey backgrounds. it adds greatly to the readability, but doesn't affect the spelling. i spell everything exactly now it sounds, and fortunately firefox is able to correct most of my errors, but not all of them.

thanks hessiess P.S. saw that pandora.. seems very cheap.

---

