---
title: "I will take this chip... AND EAT IT!!!"
date: 2010-03-18
forum: The Cafe
---

### Post by Psumi on 2010-03-18
... in light of a post in the Intel graphics thread, I would like to learn more about the difference between GPUs and CPUs and discuss everything about them.

First off, since GPUs aren't the same as CPUs, as referenced in the Intel thread... how do we compare them to one another in the form of processing power? Also, can someone explain to me why my 32-bit processor tastes like plain and greasy while my 64-bit chip tastes baked and good?

---

### Post by NCLI on 2010-03-18
Yagami-kun?

Anyway, IIRC, GPUs are amazing at running many specialized processes simultaneously, while the CPU is fairly good with anything you throw at it.

---

### Post by Psumi on 2010-03-18
> **NCLI said:**
> Yagami-kun?

Anyway, IIRC, GPUs are amazing at running many specialized processes simultaneously, while the CPU is fairly good with anything you throw at it.

You'd think it would be that the CPU would be only good at what its name suggests: processing.

Which leads me to believe, will the GPU be merged into some form of Super-CPU?

Oh wait, they did that already, with the PS2's Emotion Engine and Graphics Synth.

---

### Post by NCLI on 2010-03-18
> **Psumi said:**
> You'd think it would be that the CPU would be only good at what its name suggests: processing.

Which leads me to believe, will the GPU be merged into some form of Super-CPU?

Oh wait, they did that already, with the PS2's Emotion Engine and Graphics Synth.

That is what both Intel, AMD and nVidia are working towards, and it may very well fuse back into one chip in the future.

---

### Post by Psumi on 2010-03-18
> **NCLI said:**
> That is what both Intel, AMD and nVidia are working towards, and it may very well fuse back into one chip in the future.

That won't be good for ATI then. :D

---

### Post by swoll1980 on 2010-03-18
edit
I mis read the op.

---

### Post by swoll1980 on 2010-03-18
> **Psumi said:**
> Also, can someone explain to me why my 32-bit processor tastes like plain and greasy while my 64-bit chip tastes baked and good?

The only real difference your going to notice with 64 bit is the memory addressing capabilities.

---

### Post by whiskeylover on 2010-03-18
> **swoll1980 said:**
> The only real difference your going to notice with 64 bit is the memory addressing capabilities.

Unless you use Franks Red Hot sauce.

---

### Post by NCLI on 2010-03-18
> **Psumi said:**
> That won't be good for ATI then. :D
ATi is owned by AMD now ;)
> **whiskeylover said:**
> Unless you use Franks Red Hot sauce.

I couldn't taste anything for three days after I tried that thing!

---

### Post by Psumi on 2010-03-18
> **whiskeylover said:**
> Unless you use Franks Red Hot sauce.

How much does that upgrade cost? :D

---

### Post by NCLI on 2010-03-18
> **Psumi said:**
> How much does that upgrade cost? :D

Don't do it!!
> **Psumi said:**
> That won't be good for ATI then. :D
ATI is owned by AMD now ;)

---

### Post by swoll1980 on 2010-03-18
> **NCLI said:**
> 

I couldn't taste anything for three days after I tried that thing!

I've gotten so immune to hot sauce I can't even feel it anymore. I'm currently using Mike's Insanity Sauce which is made with habanero peppers. At first it was a little hot, but now it's like vinegar. Other people put a drop on their tongue, and wished they were dead. Time for me to find something hotter.

---

### Post by alexfish on 2010-03-18
> **Psumi said:**
> That won't be good for ATI then. :D


Hi

A little bit of reading , also try cuda for linux it will put you in good stead for the future

**Hybrid solutions**

 This newer class of GPUs competes with integrated graphics in the  low-end desktop and notebook markets. The most common implementations of  this are ATI's [HyperMemory]("http://en.wikipedia.org/wiki/HyperMemory") and NVIDIA's [TurboCache]("http://en.wikipedia.org/wiki/TurboCache").  Hybrid graphics cards are somewhat more expensive than integrated  graphics, but much less expensive than dedicated graphics cards. These  share memory with the system and have a small dedicated memory cache, to  make up for the high [latency]("http://en.wikipedia.org/wiki/Memory_latency") of the system RAM. Technologies  within PCI Express can make this possible. While these solutions are  sometimes advertised as having as much as 768MB of RAM, this refers to  how much can be shared with the system memory.
 **[[edit]("http://en.wikipedia.org/w/index.php?title=Graphics_processing_unit&action=edit&section=15")] Stream  Processing and General Purpose GPUs (GPGPU)**

 Main articles: [GPGPU]("http://en.wikipedia.org/wiki/GPGPU") and [Stream processing]("http://en.wikipedia.org/wiki/Stream_processing")
 A new concept is to use a [general purpose  graphics processing unit]("http://en.wikipedia.org/wiki/GPGPU") as a modified form of [stream processor]("http://en.wikipedia.org/wiki/Stream_processing"). This concept turns the massive [floating-point]("http://en.wikipedia.org/wiki/Floating-point")  computational power of a modern graphics accelerator's shader pipeline  into general-purpose computing power, as opposed to being hard wired  solely to do graphical operations. In certain applications requiring  massive vector operations, this can yield several orders of magnitude  higher performance than a conventional CPU. The two largest discrete  (see "Dedicated graphics cards" above) GPU designers, [ATI]("http://en.wikipedia.org/wiki/ATI_Technologies") and [NVIDIA]("http://en.wikipedia.org/wiki/NVIDIA"), are beginning to pursue  this new approach with an array of applications. Both nVidia and ATI  have teamed with [Stanford University]("http://en.wikipedia.org/wiki/Stanford_University") to create a GPU-based client for the  [Folding@Home]("http://en.wikipedia.org/wiki/Folding@Home") distributed  computing project, for protein folding calculations. In certain  circumstances the GPU calculates forty times faster than the  conventional CPUs traditionally used by such applications.[[10]]("http://en.wikipedia.org/wiki/Graphics_processing_unit#cite_note-9")[[11]]("http://en.wikipedia.org/wiki/Graphics_processing_unit#cite_note-10")
 Recently NVidia began releasing cards supporting an API extension to  the [C]("http://en.wikipedia.org/wiki/C_%28programming_language%29") programming language [CUDA]("http://en.wikipedia.org/wiki/CUDA") ("Compute  Unified Device Architecture"), which allows specified functions from a  normal C program to run on the GPU's stream processors. This makes C  programs capable of taking advantage of a GPU's ability to operate on  large matrices in parallel, while still making use of the CPU when  appropriate. CUDA is also the first API to allow CPU-based applications  to access directly the resources of a GPU for more general purpose  computing without the limitations of using a graphics API.
 Since 2005 there has been interest in using the performance offered  by GPUs for [evolutionary computation]("http://en.wikipedia.org/wiki/Evolutionary_computation") in  general, and for accelerating the [fitness]("http://en.wikipedia.org/wiki/Fitness_%28genetic_algorithm%29")  evaluation in [genetic programming]("http://en.wikipedia.org/wiki/Genetic_programming") in particular.  There is a short introduction on pages 90–92 of A Field Guide To Genetic  Programming. Most approaches compile [linear]("http://en.wikipedia.org/wiki/Linear_genetic_programming") or [tree programs]("http://en.wikipedia.org/wiki/Genetic_programming") on the host PC and transfer the  executable to the GPU to be run. Typically the performance advantage is  only obtained by running the single active program simultaneously on  many example problems in parallel, using the GPU's [SIMD]("http://en.wikipedia.org/wiki/SIMD")  architecture[[12]]("http://en.wikipedia.org/wiki/Graphics_processing_unit#cite_note-11")[[13]]("http://en.wikipedia.org/wiki/Graphics_processing_unit#cite_note-12").  However, substantial acceleration can also be obtained by not compiling  the programs, and instead transferring them to the GPU, to be  interpreted there[[14]]("http://en.wikipedia.org/wiki/Graphics_processing_unit#cite_note-13")[[15]]("http://en.wikipedia.org/wiki/Graphics_processing_unit#cite_note-14").  Acceleration can then be obtained by either interpreting multiple  programs simultaneously, simultaneously running multiple example  problems, or combinations of both. A modern GPU (*e.g.* [8800 GTX]("http://en.wikipedia.org/wiki/GeForce_8_Series") or later) can readily simultaneously interpret  hundreds of thousands of very small programs.


[http://en.wikipedia.org/wiki/Graphics_processing_unit](http://en.wikipedia.org/wiki/Graphics_processing_unit)

Regards


alexfish

---

### Post by Phrea on 2010-03-18
[http://www.youtube.com/watch?v=0udMBdo0Rac](http://www.youtube.com/watch?v=0udMBdo0Rac)

---

### Post by Post Monkeh on 2010-03-18
> **Psumi said:**
> You'd think it would be that the CPU would be only good at what its name suggests: processing.

Which leads me to believe, will the GPU be merged into some form of Super-CPU?

Oh wait, they did that already, with the PS2's Emotion Engine and Graphics Synth.

i'm pretty sure the gpu does some processing as well.

---

### Post by _h_ on 2010-03-18
Thread title is misleading and false advertising. I thought it was something about a potato chip, but was sadly disappointed by the mislead. :(

---

### Post by Psumi on 2010-03-18
> **_h_ said:**
> Thread title is misleading and false advertising. I thought it was something about a potato chip, but was sadly disappointed by the mislead. :(

Read last sentence of the op.

---

### Post by markbuntu on 2010-03-18
GPUs have more flavor because of their multiple stream processors which provide for more flavor and a very nuanced taste experience. The new ones are especially tasty, They have 600+ floating point stream processors and are best experienced with the very best vintage wines.

CPUs with a measly 4 to 16 streams are just tasteless bulk food, like tofu. They need a decent dose of Franks, or half a bottle of Sriracha. Best paired with the cheapest beer you can find.

---

### Post by NightwishFan on 2010-03-18
I assumed Death Note when I saw the title as well. Epic line, his Japanese voice actor goes all out.

---

### Post by dragos240 on 2010-03-18
> **NightwishFan said:**
> I assumed Death Note when I saw the title as well. Epic line, his Japanese voice actor goes all out.

The English dub version is more famous for [this]("http://www.youtube.com/watch?v=kaoy1QKxGQs") particular line.

---

### Post by NightwishFan on 2010-03-18
The english dub was better than most, but still a bit embarrassing.

---

### Post by Kenny_Strawn on 2010-03-18
The difference is that a GPU has **512 4-bit cores**, while a CPU has **1-4 64-bit cores**.

You see, a GPU is designed for one thing: to do matrix algebra and do it well. It CANNOT do much more than compute a GUI, which is what it is designed for.

In contrast, your regular CPU is designed for much more than that. It can do all sorts of calculations, which is why it runs your main board, not the GPU.

---

### Post by Jarmen_Deffs on 2010-03-18
> **swoll1980 said:**
> The only real difference your going to notice with 64 bit is the memory addressing capabilities.

Not so.  You also get more registers, wider registers, and wider data paths, all of which **can **(and I stress the can; they are not always taken advantage of) be used to improve performance.

---

### Post by Frak on 2010-03-18
> **Psumi said:**
> That won't be good for ATI then. :D
AMD is merging ATi technology into their chips. That's where they're deriving their GPU power and architecture from.

---

### Post by TheNessus on 2010-03-18
> **Psumi said:**
> You'd think it would be that the CPU would be only good at what its name suggests: processing.


Central PROCESSING unit
Graphic PROCESSING unit

both do processing, son.

---

### Post by dragos240 on 2010-03-18
> **TheNessus said:**
> Central PROCESSING unit
Graphic PROCESSING unit

both do processing, son.

I am disappoint.

---

### Post by Psumi on 2010-03-18
> **TheNessus said:**
> Central PROCESSING unit
Graphic PROCESSING unit

both do processing, son.

Central Processing Unit is for "Everything" though, hence "Central."

---

### Post by samh785 on 2010-03-18
> **Psumi said:**
> Central Processing Unit is for "Everything" though,  hence "Central."
Which is why it's better at taking everything that is thrown at it.

> **Psumi said:**
> You'd think it would be that the CPU would be only  good at what its name suggests: processing.

---

### Post by aklo on 2010-03-18
Why do you want to know about this? Just know that gpu is for graphics and cpu is for other processing. yes cpu can do graphic processing but they suck at it.

Just search for mythbusters nvidia video on youtube.

Also you really don't have to care about 32/64 bit just know that the higher the better. Yes you don't have to be a tech person like some of the guys in this thread to get an idea of the difference...

Ok so from my understanding of an average computer user (me)

64bits supports more memory i believe the max is cap at 3-4GB for 32bit.
Yes 64bits processor is faster but not all applications utilize the power of 64bit processing due to how they program their programs (not that sure on this)

Oh i read all these through various tech sites last time. 

Tomshardware.com is a good website...i'm not advertising but it should be one of the best computer sites out there.

---

### Post by Psumi on 2010-03-18
> **aklo said:**
> yes cpu can do graphic processing but they suck at it.

Oh? I remember seeing this little (less than 1 KB) file here on ubuntu forums that did a graphics render, all done by the CPU. The CPU barely went over 1% and the graphics were even better than the Intel Infoscape.

---

### Post by Post Monkeh on 2010-03-18
> **Psumi said:**
> Oh? I remember seeing this little (less than 1 KB) file here on ubuntu forums that did a graphics render, all done by the CPU. The CPU barely went over 1% and the graphics were even better than the Intel Infoscape.

it'll do some things alright, but a dedicated gpu is better at things like 3d rendering and effects .
it's probably all about the architechture of the chips. cpus are restricted by trying to keep backwards compatibility with older operating systems, programs,and motherboards, i think maybe gpus can use more up to date technology that allows them to do the tasks they do at a superior rate to a normal cpu

---

### Post by the yawner on 2010-03-18
All I know is that 64 is double of 32. Mind boggling.

---

### Post by swoll1980 on 2010-03-18
> **Jarmen_Deffs said:**
> Not so.  You also get more registers, wider registers, and wider data paths, all of which **can **(and I stress the can; they are not always taken advantage of) be used to improve performance.

Increase the performance of what?

---

### Post by aklo on 2010-03-18
> **Psumi said:**
> Oh? I remember seeing this little (less than 1 KB) file here on ubuntu forums that did a graphics render, all done by the CPU. The CPU barely went over 1% and the graphics were even better than the Intel Infoscape.

Give me a break. I state in my post i am not a tech guy just an average user and my interpretations may not be correct but the idea is there. Call it graphic processing or graphic 3d rendering  but to me they all mean the same. 

I've created this thread sometime ago , which show perfectly how a cpu sucks at doing these things on inkscape. A simple blur effect in inkscape if zoomed in and you will see why cpu sucks at doing graphics. I'm not saying if inkscapes supports gpu the performace will certainly be better...but i'm hoping...

[http://ubuntuforums.org/showthread.php?t=1424618](http://ubuntuforums.org/showthread.php?t=1424618)
If you have inkscape just download the svg file and open it. Then just zoom in, i'll be suprise if somebody tells me that it is smooth as a lub.

---

### Post by Frak on 2010-03-18
> **swoll1980 said:**
> Increase the performance of what?
Anything that decides to use the extra width given to it.

---

### Post by Jarmen_Deffs on 2010-03-18
> **swoll1980 said:**
> Increase the performance of what?

"What" you were referring to here:* "The only real difference your going to notice with 64 bit is the memory addressing capabilities."*

If what you actually wanted to say was that you think I'm wrong, I'd be happy to explain.

---

### Post by swoll1980 on 2010-03-18
> **Jarmen_Deffs said:**
> "What" you were referring to here:* "The only real difference your going to notice with 64 bit is the memory addressing capabilities."*

If what you actually wanted to say was that you think I'm wrong, I'd be happy to explain.

No I'm asking what does it increase the performance of noticeably, and it has to be a noticeable difference.

---

### Post by Jarmen_Deffs on 2010-03-19
> **swoll1980 said:**
> No I'm asking what does it increase the performance of noticeably, and it has to be a noticeable difference.

Oh, **noticeably**...

Video encoding and rendering spring to mind.  
You may also notice the difference in compiling, file de/compression, flash (if you use the 64 bit version), boot times if you're lucky, and as has already been said, anything written to take advantage of it (V8 for example).

---

### Post by swoll1980 on 2010-03-19
> **Jarmen_Deffs said:**
> Oh, **noticeably**...

Video encoding and rendering spring to mind.  
You may also notice the difference in compiling, file de/compression, flash (if you use the 64 bit version), boot times if you're lucky, and as has already been said, anything written to take advantage of it (V8 for example).

Not trying to be a Dick. I asked my teacher this question about 3 weeks ago, and his answer was "The only thing your going to notice is the memory addressing" This guy was an engineer for Bell Labs for 30 years. They wrote operating systems,compression algorithms, talked to computers in assembly language, and all kinds of impressive things. He just doesn't seem like the kind of guy to be wrong about something like this. This is why I ask.

---

### Post by Frak on 2010-03-19
> **swoll1980 said:**
> Not trying to be a Dick. I asked my teacher this question about 3 weeks ago, and his answer was "The only thing your going to notice is the memory addressing" This guy was an engineer for Bell Labs for 30 years. They wrote operating systems,compression algorithms, talked to computers in assembly language, and all kinds of impressive things. He just doesn't seem like the kind of guy to be wrong about something like this. This is why I ask.
90% of the time it's just memory addressing. Some applications that utilize 64-bit may still not have a noticeable difference. 3dsmax under Windows comes to mind. The 32 and 64 bit versions run the same on my machine.

---

### Post by Jarmen_Deffs on 2010-03-19
> **swoll1980 said:**
> Not trying to be a Dick. I asked my teacher this question about 3 weeks ago, and his answer was "The only thing your going to notice is the memory addressing" This guy was an engineer for Bell Labs for 30 years. They wrote operating systems,compression algorithms, talked to computers in assembly language, and all kinds of impressive things. He just doesn't seem like the kind of guy to be wrong about something like this. This is why I ask.

Perhaps he meant the average consumer will never know that some of the speed increase they gained when they bought their first 64 bit machine was partly due to the fact that it's 64 bit, they just know they can fit more memory in than they could before? I don't know, I can' t try to second guess someone else's meaning...

You can try it for yourself by using 64 bit software on 64 bit hardware, and you should notice improvements, or even better learn to write assembly code; you will know how and why 64 bit can offer a performance increase if you spend a bit of time increasing your knowledge there. ;)

---

### Post by Frak on 2010-03-19
> **Jarmen_Deffs said:**
> Perhaps he meant the average consumer will never know that some of the speed increase they gained when they bought their first 64 bit machine was partly due to the fact that it's 64 bit, they just know they can fit more memory in than they could before? I don't know, I can' t try to second guess someone else's meaning...

You can try it for yourself by using 64 bit software on 64 bit hardware, and you should notice improvements, or even better learn to write assembly code; you will know how and why 64 bit can offer a performance increase if you spend a bit of time increasing your knowledge there. ;)
Or use a better compiler.

---

### Post by cascade9 on 2010-03-19
> **Jarmen_Deffs said:**
> Oh, **noticeably**...

Video encoding and rendering spring to mind.  
You may also notice the difference in compiling, file de/compression, flash (if you use the 64 bit version), boot times if you're lucky, and as has already been said, anything written to take advantage of it (V8 for example).

Pretty much. In a lot of things (probably most, apart from the few 'wow that was faster' programs), you will see a 5-10% increase (eg boot likes, flash). I admit, I dont really notice the difference in boot timess (30 seconds vs 28.5...wow, thats huge:| ) but where you will really notice the difference is on anything that takes a lot of processing. Graphics rendering gets a big boost. Even things like apache get more from 64bit. 

[http://www.tuxradar.com/content/ubuntu-904-32-bit-vs-64-bit-benchmarks](http://www.tuxradar.com/content/ubuntu-904-32-bit-vs-64-bit-benchmarks)

[http://www.phoronix.com/scan.php?page=article&item=ubuntu_32_pae&num=1](http://www.phoronix.com/scan.php?page=article&item=ubuntu_32_pae&num=1)

BTW, its only been the last 2-3 years hat 64bit has really got to where it is. If you check benchmarks from 2006, 64 bit was pretty much the same as 32bit (some things slower, some things faster, not a huge margin either way). IMO 64bit will continue to mature, and will gain a bit more performance over the next year or two, but probably not as dramaticly as the increase as over the last few years.

---

### Post by snova on 2010-03-19
> **Kenny_Strawn said:**
> The difference is that a GPU has **512 4-bit cores**, while a CPU has **1-4 64-bit cores**.

You see, a GPU is designed for one thing: to do matrix algebra and do it well. It CANNOT do much more than compute a GUI, which is what it is designed for.

In contrast, your regular CPU is designed for much more than that. It can do all sorts of calculations, which is why it runs your main board, not the GPU.

On the contrary. Take [shaders]("http://en.wikipedia.org/wiki/Shader"), or [GPGPU]("http://en.wikipedia.org/wiki/GPGPU")- GPU's excel at anything parallelizable, and are every bit as programmable as an average processor. And they are only getting more powerful.

At the same time, CPU's are introducing more instruction SIMD instruction sets. The difference is blurring. I am beginning to wonder whether the only unique thing CPU's do is run operating systems. (Referring to memory protection.)

---

### Post by Frak on 2010-03-19
> **snova said:**
> On the contrary. Take [shaders]("http://en.wikipedia.org/wiki/Shader"), or [GPGPU]("http://en.wikipedia.org/wiki/GPGPU")- GPU's excel at anything parallelizable, and are every bit as programmable as an average processor. And they are only getting more powerful.

At the same time, CPU's are introducing more instruction SIMD instruction sets. The difference is blurring. I am beginning to wonder whether the only unique thing CPU's do is run operating systems. (Referring to memory protection.)
It's only a matter of time before memory protection is yet another programmable instruction. And yes, I did say that as stupid and unrealistic as it sounds.

---

