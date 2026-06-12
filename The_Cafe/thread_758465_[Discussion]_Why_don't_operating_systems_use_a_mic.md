---
title: "[Discussion] Why don't operating systems use a microkernel?"
date: 2008-04-18
forum: The Cafe
---

### Post by Zdravko on 2008-04-18
[FONT=Times New Roman][SIZE=3]I wondered why is the microkernel approach neglected?

Windows uses an enormous monolithic kernel (in terms of hundreds of megabytes, or even close to gigabytes). Linux  uses a big monolithic kernel (in terms of several megabytes).

Windows is continuously supported by cash income and does not really need to be discussed. It is up to the M$ developers to handle such a big kernel.

I am concerned about Linux. Its kernel is growing more and more. And it will not be the far future when the Linux kernel also reaches the gigabyte field.

Have a look at: [http://en.wikipedia.org/wiki/Microkernel](http://en.wikipedia.org/wiki/Microkernel) and you will quickly understand why a microkernel is much better than a monolithic one. The most important feature of a microkernel is its security and absolute stability. There might be a small speed penalty, however. Read [http://en.wikipedia.org/wiki/L4_microkernel](http://en.wikipedia.org/wiki/L4_microkernel) and you will see that in fact it should work much better because of intelligent implementations.

I even read somewhere an interview with Linus about the historical development of Linux. He said that he made a mistake by choosing a monolithic kernel for Linux. Now it is too late to fix this. Linux will keep growing and become more and more bloated.

In fact, I think that it is already bloated. What happens when a driver has a bug? The system crashes. Why? Because the driver is located in the kernel land.

Do we have any alternatives? I see only the MINIX from Andy Tannenbaum. However it is far away from the general purpose Linux has achieved. Why is it so difficult to build a modern operating system? The GNU Hurd project seems to have been developing for 10 or even 15 years. Do we have a working microkernel? Or at least one that a general user can use, to run a user application like GUI etc.?

I feel truly sorry for Linux. It is a great community-driven project. But it just walks the wrong path.

I also wonder why do people happen to adore Linux. It is free, it has many applications, yes... But it follows the same wrong approach - monolithic kernel. Why isn't there a single person to stand up and say loudly and proudly: 

[B]"Enough with this monolithic kernel!" Let's turn the page and start a brand new story!"

[/B]I am sure that this world would be a much better place if there was a microkernel approach in the design of operating systems. 

My 3rd and last question here is: do the people intentionally avoid intelligent and elegant solutions and prefer the obviously wrong and insecure stuff?

Enough talking. It is your turn.[/SIZE][/FONT]

---

### Post by uknowho008 on 2008-04-18
i dont know too much abut kernels. but this sounds interesting.

---

### Post by LightB on 2008-04-18
My turn? Ok, well, where can I start?

I think  you might have the foggiest idea of what you're talking about, but I wouldn't bet anything of much value on it. The Linux kernel is 'several megabytes'? Strange because I'm only seeing a couple of MB of it here, the rest are modules. 

Also, you say Linus said he regrets going with a monolithic kernel and wishes he would have gone with microkernel. He never said such thing. I don't know if you're making things up, twisting things out of context, or have just plain misunderstood some quote. I know there is some famous debate that Linus had on the subject, even then he clearly defends going with a monolithic kernel which you can read [here](http://www.oreilly.com/catalog/opensources/book/appa.html).

The way I understand it, basically it has to do with memory address space. The monolithic kernel works from a more centralized point of view while a microkernel splits up the work to different processes. The main idea with the microkernel seems to be about reliability through a sort of built in process redundancy. Going by that alone, the concept of security is more subjective. The main argument in favor of a monolithic kernel is performance and less complication of the development. For what it's worth, I think Linus made the right choice. I think that paradoxically Linux would have been less reliable had it been developed as a microkernel because it would be more difficult to develop.

And it's funny because I remember some calling Windows a microkernel, not monolithic. Is it a case of the simple fact that it's closed and it was just confusion, or did something change since then? Well, that's a rhetorical question. Linux is monolithic and a far more capable design in a free range environment.

---

### Post by 3rdalbum on 2008-04-18
Linux isn't exactly monolothic. Things like loadable kernel modules and FUSE filesystem drivers make Linux a hybrid kernel, not a monolithic kernel.

---

### Post by LightB on 2008-04-18
True, and if we keep going, we're deep in a semantics nightmare. Still, a hybrid kernel is in effect monolithic, or at least it doesn't have the touted properties of a microkernel.

---

### Post by jeffus_il on 2008-04-18
Linux did not develop from the Minix kernel because of performance problems, that is interprocess communications, between the different kernel "programs" like the memory manager, task scheduler, device drivers and all the other OS functions. Today may be the right time to build Linux out of Minix because the hardware is much more powerful than it was then, want to give it a try?

Minix is a great OS teaching tool, because the OS functionality stares you straight in the eye, and is probably more stable if the kernel memory is not shared by all the OS modules.

---

### Post by thrice upon a time on 2008-04-18
Andy, is that you? LOL

Most of (but granted, not all) what I read in the OP is pure FUD and misguided speculation, if at least ignorantly unintentional, stated as fact. 

There are a couple of high-level microkernel OSs, but they're main-frame level. Singularity is a micro-kernel project by MS. 

There are also drawbacks to the microkernel approach ;) Every time a new "micro-kernels are superior" argument comes up, ie: portability, etc... it's usually proven false shortly thereafter ;)

But, if you're so smart, and know just how Linus has it all wrong, why not just fix it yourself? You obviously have all of the answers. I'll even give you a headstart - the NEW Minix :guitar:

Why, just WITNESS the power of the microkernel! 

[http://www.minix3.org/doc/screenies.html](http://www.minix3.org/doc/screenies.html)

BTW: I still have a complete Linux distro that fits on a floppy disk. That's not exactly bloatware ;) I'm pretty sure Linus knows more-or-less what he's doing. It may be worth your while to check out "his" side of the story - you'll GREATLY inform yourself, not to mention chuckle as he pwnz in typical Linux fashion :lolflag:

---

### Post by Xbehave on 2008-04-18
because linus wanted a working kernel, not a blue print. There are technical arguments too, but while a microkernel may have technical benifits, a macrokernel is faster to develop.

"I can (well, almost) hear you asking yourselves 'why?'. Hurd will be out in a year (or two, or next month, who knows)" - linus 1991
The Hurd 0.0 was released in August 1996. (by which time linux was already on 1.1.x )

while the linux kernel is growing its not really as big as you claim, you have to remember that ubuntu is compiled with support for the kitchen sink, if you compiled your own kernel, which is effectively just the parts of the kernel you use it will be much smaller. 

besides kernel level arguments are fairly pointless when  you consider that a current system is about 5GB, its rarely a kernel bug that causes you problems.

---

### Post by phrostbyte on 2008-04-18
The advantages of a microkernel melted away even more once open source got popular. For instance, while a microkernel makes sense if you don't have access to the kernel source code and wish to customize it, the Linux kernel can be compiled to perform all sorts of tasks, and even to fit into a single floppy disk as someone said.

---

### Post by richardjennings on 2008-04-18
To answer your question, It is too difficult to develop. I think Richard Stallman made this quite clear with the hurd project.

---

### Post by Darkhack on 2008-04-18
There is tons and tons of literature on the subject and it's a heated debate.  I'm on the fence myself.  I'm not a kernel developer, so me having an opinion on it is about as legitimate as a monkey have an opinion on brain surgery or rocket science.  Anyways, the fact that Linux made it big despite The HURDs head start says something about the development complexities in microkernels.  In the documentary, Revolution OS, Richard Stallman talks about how difficult it was to debug the microkernel due to messaging passing and the way he describes it sounds an awful lot like spaghetti code; the only difference is it being done via IPC.

---

### Post by Erunno on 2008-04-18
> **phrostbyte said:**
> The advantages of a microkernel melted away even more once open source got popular. For instance, while a microkernel makes sense if you don't have access to the kernel source code and wish to customize it, the Linux kernel can be compiled to perform all sorts of tasks, and even to fit into a single floppy disk as someone said.

Being open or closed source has nothing to do with kernel design in general and micro kernels in particular.

---

### Post by K.Mandla on 2008-04-18
> **Darkhack said:**
> I'm not a kernel developer, so me having an opinion on it is about as legitimate as a monkey have an opinion on brain surgery or rocket science.
Don't feel bad. I'm in that same category with you. When I start contributing to the kernel I'll start wondering about mono- versus micro-.

---

### Post by Zdravko on 2008-04-18
> **richardjennings said:**
> To answer your question, It is too difficult to develop. I think Richard Stallman made this quite clear with the hurd project.
From above replies this one was the only one that makes sense. Thanks.

---

### Post by raul_ on 2008-04-18
Micro kernels are better and more stable, it' s a fact, but I think it would require starting (almost) from scratch.

---

### Post by aimran on 2008-04-18
A micro kernel sounds like a solution that a Linux-geek would take, as opposed to Mono-kernels which Microsoft would use. Simplicity :)

But then again upon reading wikipedia about microkernels, it does sound easier to talk about it than implement it XDDD

---

### Post by Zdravko on 2008-04-18
> **raul_ said:**
> Micro kernels are better and more stable, it' s a fact, but I think it would require starting (almost) from scratch.
I read somewhere that writing an OS from scratch will take an awful amount of time. On the other side, modifying an existing OS would save time.
I also would like to see an OS evolve from scratch, however. :(

---

### Post by unbuntu on 2008-04-18
> **thrice upon a time said:**
> 
Why, just WITNESS the power of the microkernel! 

[http://www.minix3.org/doc/screenies.html](http://www.minix3.org/doc/screenies.html)


LOL...You can witness the power of microkernel by screenies?

---

### Post by Blue Heron on 2008-04-18
Isn't that a great question to discuss in an university?

---

### Post by init1 on 2008-04-18
Heh, if you want a microkernel, try Minix :D
[www.minix3.org](www.minix3.org)

---

### Post by LightB on 2008-04-18
> **Zdravko said:**
> From above replies this one was the only one that makes sense. Thanks.

IOW, the only one you understood. You might try working up to the actual truth one.

---

### Post by raul_ on 2008-04-18
Everything that absolutely NEEDS to work (airplane software, for example) uses microkernels. Anything that can crash uses monolithic kernels. 

And yes, Linux crashes too, but it's a matter of pressing the reset button. It's not like an airplane crashing

EDIT: That's a Tanembaum quote btw

---

### Post by samjh on 2008-04-18
There is a definitive must-read mailing list thread on this.

Tanenbaum vs Torvalds (aka. Minix vs Linux):
[http://www.oreilly.com/catalog/opensources/book/appa.html](http://www.oreilly.com/catalog/opensources/book/appa.html)

Probably more info than you can poke a stick at. ;)

---

### Post by Foster Grant on 2008-04-18
> **raul_ said:**
> Micro kernels are better and more stable, it' s a fact, but I think it would require starting (almost) from scratch.

At least one person disagrees with you, and quite vehemently. Mr. Chairman, I yield the remainder of my time to Linus Torvalds.

[http://www.realworldtech.com/forums/index.cfm?action=detail&id=66630&threadid=66595&roomid=2](http://www.realworldtech.com/forums/index.cfm?action=detail&id=66630&threadid=66595&roomid=2)

[quote=Linus Torvalds]It's ludicrous how micro-
kernel proponents claim that their system is "simpler" than
a traditional kernel. It's not. It's much much more
complicated, exactly because of the barriers that it has
raised between data structures.

The fundamental result of access space separation is that
you can't share data structures. That means that you can't
share locking, it means that you must copy any shared data,
and that in turn means that you have a much harder time
handling coherency. All your algorithms basically end up
being distributed algorithms.

And anybody who tells you that distributed algorithms
are "simpler" is just so full of sh*t that it's not even
funny.

Microkernels are much harder to write and maintain
exactly because of this issue. You can do simple
things easily - and in particular, you can do things where
the information only passes in one direction quite easily,
but anythign else is much much harder, because there is
no "shared state" (by design). And in the absense of shared
state, you have a hell of a lot of problems trying to make
any decision that spans more than one entity in the
system.

And I'm not just saying that. This is a fact. It's a fact
that has been shown in practice over and over again, not
just in kernels. But it's been shown in operating systems
too - and not just once. The whole "microkernels are
simpler" argument is just bull, and it is clearly shown to
be bull by the fact that whenever you compare the speed
of development of a microkernel and a traditional kernel,
the traditional kernel wins. By a huge amount, too.

The whole argument that microkernels are somehow "more
secure" or "more stable" is also total crap. The fact that
each individual piece is simple and secure does not make
the aggregate either simple or secure. And the
argument that you can "just reload" a failed service and
not take the whole system down is equally flawed.[/quote]

Of course, this also refutes the original post.

---

### Post by raul_ on 2008-04-18
> **Foster Grant said:**
> At least one person disagrees with you, and quite vehemently. Mr. Chairman, I yield the remainder of my time to Linus Torvalds.

[http://www.realworldtech.com/forums/index.cfm?action=detail&id=66630&threadid=66595&roomid=2](http://www.realworldtech.com/forums/index.cfm?action=detail&id=66630&threadid=66595&roomid=2)



Of course, this also refutes the original post.

I think Mr. Linus Torvalds should *sometimes* stick to designing kernels :P

Nevertheless, I'm sure the points that he makes (as well as Prof. Tanembaum's) are very pertinent, as I don't understand half of what they are talking about :)

---

### Post by Whiffle on 2008-04-18
Looks like it boils down because what works in theory, does not always work well in practice.

/me stands up loudly and proudly and declares "Someone set us up the bomb!"

---

### Post by Iandefor on 2008-04-18
> **Zdravko said:**
> [FONT=Times New Roman][SIZE=3]I wondered why is the microkernel approach neglected?

Windows uses an enormous monolithic kernel (in terms of hundreds of megabytes, or even close to gigabytes). Linux  uses a big monolithic kernel (in terms of several megabytes).[/SIZE][/FONT]Linux is not a strictly monolithic kernel. It's more of a hybrid than anything else. The way it usually goes on Linux systems is that there's a main kernel (vmlinuz), with all the bits necessary to boot, and a set of modules that get loaded later. The main kernel is usually pretty small; my current vmlinuz doesn't even use two megabytes.

Also, I'm fairly certain that Vista's kernel got more modular. I recall this being one of the improvements to Vista- if one part of the  went down the whole thing didn't necessarily go down.

EDIT: In addition, if anybody wants to try an OS based off of a microkernel, I know that Debian is working on a [port]("http://www.debian.org/ports/hurd/") of Debian to the HURD.

---

### Post by Omnios on 2008-04-18
A micro kernel is superior in one aspect.
 
 I want to try and use it. Does not matter if ts better or complicated. Simple fact I want to try and use it. 
 
 If users and developers jump on board any argument against will be irrelevent.
 
 Look at BSD it might be more stable and more secure but I do not want to use it. 
 
 Same argument with windows its not better but people want to use it which is backfiring with Vista as a lot of people do not want tot use it lol.
 
 Also this argument sounds similar to the old object orientated programming argument when it was being developed. I think once a acceptable workig system implimented there any argument will be irrelevent.

---

### Post by Tundro Walker on 2008-04-19
> **3rdalbum said:**
> Linux isn't exactly monolothic. Things like loadable kernel modules and FUSE filesystem drivers make Linux a hybrid kernel, not a monolithic kernel.

Exactly.  That's the way I understood it from the articles I've read, too.  You can pick and choose the modules to compile the kernel with, so it is sort of microkernel.  However, once you have it compiled, you're kind of stuck with those modules unless you recompile and replace.  So, it's sort of monolithic in that sense.

I thought that was what Linus was shooting for, so he'd have the flexibility of both worlds.

EDIT:

I think the OP needs to also understand that nobody's perfect; we're all just human.  Maybe there was an article where Linus said he regretted something being the way it is in Linux.  Hindsight is 20/20, but nobody is wise enough to fore-see all things, especially since Linux was just a small, hackish OS when Linus put it together.  He never thought it was going to explode into this, otherwise he might have tossed more fore-thought into it.  However, the fact that it has exploded into this shows that he did put quite a bit of fore-thought of its functionality (or at least its ability to mimic Unix's already solid functionality), and he's stuck with it and changed it to suit the needs over time.

---

### Post by Zdravko on 2008-04-19
Okay. I have to agree with you. Thank you for the replies. Discussion is over.

---

