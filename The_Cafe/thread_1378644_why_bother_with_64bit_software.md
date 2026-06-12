---
title: "why bother with 64bit software"
date: 2010-01-11
forum: The Cafe
---

### Post by yester64 on 2010-01-11
Attention, this might be a nerd talk.:tongue:

The reason i am asking this myself is this.
Every time i run a 64bit OS, i discover over time that most of the software still sticks with 32bit libraries to function under 64bit.
The only benefits i see for using 64bit is that the OS can address more memory that it could under 32bit.
Hardware goes 64 but software not necessarily.
I find this finding a little unsettling since my ultimate hope was to run real 64bit software.
Ok, there are 64bit software but for some commerical software its 32bit only, but will run under 64bit with use of 32bit libraries.
Is there hope for 64bit at all or how long have users to wait until software is available to 64bit standart?
It really nailed my windows experience that i bought 64bit system and in the end most software was 32bit. haha..
The most answer was always, well there are not a lot of people using 64bit as of now.
Great.
So why bother with 64bit at all.
I am not saying that nothing runs but i wished i could use the real 64bit power.
Or perhaps i am just over saturating the situation.

---

### Post by Techsnap on 2010-01-11
>  i discover over time that most of the software still sticks with 32bit libraries to function under 64bit.

Out of interest which programs are you trying to install which pull in x86 libraries? Surely there aren't many, if there are you must be able to compile them from source? Also I thought Ubuntu was multilib out of the box?

---

### Post by Xbehave on 2010-01-11
recent benchmarks put ubuntu 64bit as significantly faster than ubuntu 32bit on many workloads (with same hw)

I've been running linux x86_64 since getting a 64bit PC and have no idea what your talking about, none of my software uses 32bit libs (not even flash)

---

### Post by NoaHall on 2010-01-11
GNU/Linux can run purely on 64 bit, Mac can to some extend - windows can not. A lot of applications are still 32 bit on Windows. 64 bit should always been used where possible. It makes the world so much faster.

---

### Post by Redache on 2010-01-11
It used to be the case that you'd have to install 32-bit libs under a 64-bit OS bit this is gradually changing as software is modified to work with 64-bit OS's natively.

I find Ubuntu 64-bit performs much faster than 32-bit on my System. I also find it the same with Windows 7 64-bit.

---

### Post by JDShu on 2010-01-11
Anything that requires a lot of calculation, such as 3D rendering and video editing greatly benefits from 64bit. For me, blender runs much faster in a 64 bit OS than 32 bit.

---

### Post by Barrucadu on 2010-01-11
> **yester64 said:**
> Every time i run a 64bit OS, i discover over time that most of the software still sticks with 32bit libraries to function under 64bit.

&#8216;most&#8217;? How many years ago did you last try x86_64 Linux?

---

### Post by amauk on 2010-01-11
there's a fair few common operations that benefit from being written for 64-bit processors

Eg.
The radix sort gains a massive speed advantage on 64bit

---

### Post by insane_alien on 2010-01-11
64-bit FLIES when using something that requires double precision calculations often when compared to the same task on 32-bit. good 130-140% faster at the least.

and if your program is pulling in lib32's then its not a 64-bit piece of software. some software isn't ported to 64-bit for various reasons

skype because its proprietry
wine because the 64-bit port currently makes winME look rock solid but it's being worked on.

and so on.

but 99.99% of software in the repos is available as all 64-bit, no mixed libraries.

not that mixed libraries are really a problem with a good package manager. the allow you to run software that might otherwise be unavailable at the cost of a few megs of HDD space.

all software will eventually get ported to 64-bit. especially as medium range computers are being sold with 4GB RAM now. by next year the preinstalled 32-bit OS should be in the minority(finally, i'm of the opinion it should have died a while back). another year will also see lowend machines get up to around 4GB. then there's just no excuse.

anyway, 32-bit hardware is well on its way into decline. i still run some but when it dies its getting replaced with 64-bit.

and if you have 64-bit, why would you purposefully choose to not use it?

do you buy a ferrari and take out half the sparkplugs?

---

### Post by SteveHillier on 2010-01-11
Why shoudn't we.
I admit it is a bit of a mess at the moment as no one is sure which standard we should go to and until some major player in the market place ( I think you know who I mean ) decides that 64 bit is the standard we will continue in this muddle.
Remind ourselves what caused the demise of 16 bit - it was when support for it was withdrawn.  The same will happen with the 32 / 64 bit agrument.
At that point in time those of us who have embraced and understand 64 bit will have a much better understanding of it.
This sort of argument means that at some time in the past someone could have said "what is the point of the internal combustion engine when we have perfectly good steam engines that work?"

---

### Post by Twitch6000 on 2010-01-11
> **insane_alien said:**
> 
and if your program is pulling in lib32's then its not a 64-bit piece of software. some software isn't ported to 64-bit for various reasons

skype because its proprietry




Uhmm talk about bullcrap. The reason they only make a 32bit version is most people still use 32bit hardware. It has nothing to due with if they are closed or open source.

---

### Post by NoaHall on 2010-01-11
> **Twitch6000 said:**
> Uhmm talk about bullcrap. The reason they only make a 32bit version is most people still use 32bit hardware. It has nothing to due with if they are closed or open source.

Really? I disagree - far, far more open source applications are ported to 64 bit. I can run my entire GNU/Linux system, only on 64 bit. I can't say the same for Windows, and I can half say the same for Mac - I have a few older apps on Mac.

---

### Post by amauk on 2010-01-11
x86_64 has been around for 7 years

x86 (32bit) has not seen a new processor on the market for 6 years, apart from the early Atoms
but even the Atom (I believe) has now moved to 64bit

Most people today (I assume) have a machine less than 6 years old
so most people do not have 32bit hardware

---

### Post by yester64 on 2010-01-11
I think i over saturated and i shouldn't even posted this thread.
Anyway, i think my main issue was with some commercial software and yes, most on linux is 64bit as well. But i never seen this really taken off in the windows world.
Since i used to be a heavy gamer (not anymore really) most software was 32bit and is to this day.

---

### Post by amauk on 2010-01-11
The Windows world have a problem with moving to 64bit

It takes time & effort to produce 64bit drivers for hardware, and most companies are not willing to commit to providing 64bit drivers for older hardware

This is particularly visible with printers and scanners and other such hardware that doesn't outdate for a long time

One of the downsides to proprietary software, I'm afraid

The open source world seamlessly (well almost seamlessly) moved to 64bit, but Windows is stuck in a limbo

---

### Post by blueshiftoverwatch on 2010-01-11
Are the 64 bit versions for apps like Firefox, Transmission, Thunderbird, Pidgin any faster or more efficient under 64 bit than 32? It seems like even if they're not very resource intensive they'd still be 100% more efficient because if Firefox went to send a message to my CPU it could transmit the data 64 bits at a time instead of 32. Which would take half as much time to do and allow the CPU to return to an idle state where it's not processing any data 2x as fast. Which would mean that other applications that might be running would have to wait in line half as long to use the CPU for a given task. So why is it that people are saying the only difference between 32 and 64 bit only noticeable when doing very intensive tasks like rendering, compressing, encoding, etc? With the exception of the current hard drive bottleneck, wouldn't every task that didn't have to access that hard drive instantly become 2x as fast as soon as it was properly compiled to take advantage of a 64 bit architecture?

---

### Post by amauk on 2010-01-11
most consumer applications will not see any significant speed increases
(only because they're not very processor intensive - an increase of X% for operation Y will not be noticeable if the operation only takes 2/10ths sec.)

it's mainly stuff like video encoding, image editing, etc. that gains perceivable performance increases

Having said that, the move to 64bit brings other things that end-users will notice
(like the ability to use more than 3.5GB of RAM, and being able to memory map large files)

---

### Post by Twitch6000 on 2010-01-11
> **NoaHall said:**
> Really? I disagree - far, far more open source applications are ported to 64 bit. I can run my entire GNU/Linux system, only on 64 bit. I can't say the same for Windows, and I can half say the same for Mac - I have a few older apps on Mac.

Good for you its all 64bit. It still doesn't matter if it is closed or open source. It depends on the programmers for the program and if they want to worry about a 64 bit version or not.

Heck even adobe just recently released a 64 bit version of flash.

Why did it take so long, simple more 32bit users and more demand for 32bit.

---

### Post by NoaHall on 2010-01-11
> **Twitch6000 said:**
> Good for you its all 64bit. It still doesn't matter if it is closed or open source. It depends on the programmers for the program and if they want to worry about a 64 bit version or not.

Heck even adobe just recently released a 64 bit version of flash.

Why did it take so long, simple more 32bit users and more demand for 32bit.

And yet if it were open source, a 64 bit version would have been released in half the time. In fact, as soon as a competent programmer wanted a 64 bit version, or gives in to the demands of the users. I'm afraid I have to disagree with you.

---

### Post by Twitch6000 on 2010-01-11
> **NoaHall said:**
> And yet if it were open source, a 64 bit version would have been released in half the time. In fact, as soon as a competent programmer wanted a 64 bit version, or gives in to the demands of the users. I'm afraid I have to disagree with you.

Oh really lol. Look at pclinuxos for a good example. Its open source yet the devs still have not made a 64bit. 

Oh and you say you cant run windows 64 bit. You are certainly wrong there aswell. I have a friend who bought windows 7 64 bit and it has all 64bit software.

---

### Post by NoaHall on 2010-01-11
> **Twitch6000 said:**
> Oh really lol. Look at pclinuxos for a good example. Its open source yet the devs still have not made a 64bit. 

Oh and you say you cant run windows 64 bit. You are certainly wrong there aswell. I have a friend who bought windows 7 64 bit and it has all 64bit software.

They have not switched over yet. They are trying to keep it to one main architecture at a time. Easier to support.

And, no, you can't. Windows Live messenger? 32 bit. Skype? 32 bit. Chrome? 32 bit. Stereo control panel(part of nvidia)? 32 bit. Games? 32 bit. Adobe products? 32 bit. Steam? 32 bit. So if you use anything worth using Windows for, you can't.

---

### Post by Dark Aspect on 2010-01-11
> **Twitch6000 said:**
> Oh and you say you cant run windows 64 bit. You are certainly wrong there aswell. I have a friend who bought windows 7 64 bit and it has all 64bit software.

How did you buy 64-bit Windows 7? I ask because my commercial disc has both x86 & 64-bit and I thought that both versions have been merged to a single disc?

BTW, I have windows 7 ultimate, so maybe thats why.

---

### Post by NoaHall on 2010-01-11
> **Dark Aspect said:**
> How do you buy 64-bit Windows 7? I ask because my commercial disc has both x86 & 64-bit and I thought that both versions have been merged to a single disc?

BTW, I have windows 7 ultimate, so maybe thats why.

No, there's two disks in the case. One is 32 bit, the other is 64 bit.

---

### Post by lukeiamyourfather on 2010-01-11
> **yester64 said:**
> Attention, this might be a nerd talk.:tongue:

The reason i am asking this myself is this.
Every time i run a 64bit OS, i discover over time that most of the software still sticks with 32bit libraries to function under 64bit.
The only benefits i see for using 64bit is that the OS can address more memory that it could under 32bit.
Hardware goes 64 but software not necessarily.
I find this finding a little unsettling since my ultimate hope was to run real 64bit software.
Ok, there are 64bit software but for some commerical software its 32bit only, but will run under 64bit with use of 32bit libraries.
Is there hope for 64bit at all or how long have users to wait until software is available to 64bit standart?
It really nailed my windows experience that i bought 64bit system and in the end most software was 32bit. haha..
The most answer was always, well there are not a lot of people using 64bit as of now.
Great.
So why bother with 64bit at all.
I am not saying that nothing runs but i wished i could use the real 64bit power.
Or perhaps i am just over saturating the situation.

For the average end user it doesn't matter, ***yet***. I don't get why you say "64-bit power" because its not any faster, just allows access to more memory. If you don't need more than 4GB of memory then use 32-bit operating system and hardware. If you need more then 4GB of memory then use 64-bit operating system and hardware and know that some applications are 32-bit and can use only 4GB of memory. Not a big deal because most applications that need the extra memory access are already 64-bit (e.g. computer animation, graphics and video editing, simulation and dynamics). In time other end user applications will migrate to native 64-bit like web browsers and media players as the need arises (but a lot already have 64-bit versions). Cheers!

---

### Post by Twitch6000 on 2010-01-11
> **NoaHall said:**
> They have not switched over yet. They are trying to keep it to one main architecture at a time. Easier to support.

And, no, you can't. Windows Live messenger? 32 bit. Skype? 32 bit. Chrome? 32 bit. Stereo control panel(part of nvidia)? 32 bit. Games? 32 bit. Adobe products? 32 bit. Steam? 32 bit. So if you use anything worth using Windows for, you can't.

Ahh,but they can all still run on a 64bit version though.

Oh and where did I say he used any of those o.o?

He just uses the computer to play runescape and for email lol..

So if he doesn't use those things he shouldn't use windows? Odd cause I find no other os better for what he does.

Oh and might I add you have yet to give proof that skype is not available as 64 bit because it isnt open source.

---

### Post by FuturePilot on 2010-01-11
> **lukeiamyourfather said:**
> For the average end user it doesn't matter, ***yet***. I don't get why you say "64-bit power" because its not any faster, just allows access to more memory. If you don't need more than 4GB of memory then use 32-bit operating system and hardware. If you need more then 4GB of memory then use 64-bit operating system and hardware and know that some applications are 32-bit and can use only 4GB of memory. Not a big deal because most applications that need the extra memory access are already 64-bit (e.g. computer animation, graphics and video editing, simulation and dynamics). In time other end user applications will migrate to native 64-bit like web browsers and media players as the need arises (but a lot already have 64-bit versions). Cheers!

To say that the only benefit to 64bit is the ability to address more RAM, is just false. It may be one of the more obvious benefits to 64bit, but it is certainly not the only benefit. And [yes, it is faster.](http://www.phoronix.com/scan.php?page=article&item=ubuntu_32_pae&num=1")

---

### Post by NoaHall on 2010-01-11
> **Twitch6000 said:**
> Ahh,but they can all still run on a 64bit version though.

Oh and where did I say he used any of those o.o?

He just uses the computer to play runescape and for email lol..

So if he doesn't use those things he shouldn't use windows? Odd cause I find no other os better for what he does.

Oh and might I add you have yet to give proof that skype is not available as 64 bit because it isnt open source.

So what? They aren't 64 bit, they slow down the system.

I'm saying, most people who USE their Windows for Windows applications can't run pure 64 bit.

---

### Post by Twitch6000 on 2010-01-11
> **NoaHall said:**
> So what? They aren't 64 bit, they slow down the system.

I'm saying, most people who USE their Windows for Windows applications can't run pure 64 bit.

1. Say what hahah I notice no speed different when he uses it.

2. YES THEY ******* CAN LOL. It just depends on what they use it for lol..

3. YOU STILL HAVEN'T proved that skype doesn't have a 64bit due to them being closed source you have just stated the obvious honestly lol.

---

### Post by NoaHall on 2010-01-11
> **Twitch6000 said:**
> 1. Say what hahah I notice no speed different when he uses it.

2. YES THEY ******* CAN LOL. It just depends on what they use it for lol..

3. YOU STILL HAVEN'T proved that skype doesn't have a 64bit due to them being closed source you have just stated the obvious honestly lol.

I'm not going to engage with you anymore because it's not worth getting a infraction for. You clearly can't justify your argument.

---

### Post by Twitch6000 on 2010-01-11
> **NoaHall said:**
> I'm not going to engage with you anymore because it's not worth getting a infraction for. You clearly can't justify your argument.

I have . Also you cannot justify yours either. Atleast I have not seen you do it

Oh if are afraid of proving me wrong due to an infraction that is lame dude just lame.

I am not afraid of being proved wrong so if you can do it please do so. I like to learn new things :).

---

### Post by 00ber n00b on 2010-01-11
Ladies!

---

### Post by lukeiamyourfather on 2010-01-11
> **FuturePilot said:**
> To say that the only benefit to 64bit is the ability to address more RAM, is just false. It may be one of the more obvious benefits to 64bit, but it is certainly not the only benefit. And [yes, it is faster.](http://www.phoronix.com/scan.php?page=article&item=ubuntu_32_pae&num=1")

True that 64-bit Ubuntu is typically faster than 32-bit Ubuntu (not arguing that). Largely though its from other instructions and optimizations that aren't available in 32-bit hardware for example SSE4. In other words its not inherently faster because its 64-bit alone.

New users should go 64-bit if their hardware supports it. Though I'd still say the same if an average user is using 32-bit Ubuntu and doesn't need more than 4GB of memory then its probably not worth the time to reinstall 64-bit Ubuntu (because the average end user doesn't use POV-Ray and GraphicsMagick). Cheers!

---

### Post by qalimas on 2010-01-11
> **Twitch6000 said:**
> I have . Also you cannot justify yours either. Atleast I have not seen you do it

Oh if are afraid of proving me wrong due to an infraction that is lame dude just lame.

I am not afraid of being proved wrong so if you can do it please do so. I like to learn new things :).

If Skype were open-source, I could compile it on my 64-bit Ubuntu install and have a 64-bit version.

So yes, being closed source prevents a 64bit port by people other than non-caring developers (non-caring in Skype's case, anyway).

---

### Post by Xbehave on 2010-01-11
> **Twitch6000 said:**
> 3. YOU STILL HAVEN'T proved that skype doesn't have a 64bit due to them being closed source you have just stated the obvious honestly lol.
How major many linux open source program don't have a 64bit builds? I'd guess 1 (wine). This is because it's a whole lot easier to recompile and fix build errors than it is to write the program from scratch, so there is a whole host of non-developer (or at least developers not good enough to write the program itself) who can port it, just look at debian with it's 1o supported linux ports, while underlying software (such as firefox) isn't even available for anything other than x86/x86_64. If skype were opensource there would definitely be a 64bit linux build.

---

### Post by NoaHall on 2010-01-11
Thank you, you two, for having the patience to answer him and save me a infraction in my temper :D

---

### Post by juancarlospaco on 2010-01-11
No, BTW 64bit fix the 2038 Unix Bug too...

---

### Post by Twitch6000 on 2010-01-11
> **qalimas said:**
> If Skype were open-source, I could compile it on my 64-bit Ubuntu install and have a 64-bit version.

So yes, being closed source prevents a 64bit port by people other than non-caring developers (non-caring in Skype's case, anyway).

I don't think compiling a 32bit program makes it 64bit. Thats a guess if you could show me why it does or how that would be nice lol.

Anyways you just stated why it isn't because of skype being closed soure doesn't effect rather it is 64bit or not.

It is the dev's fault. They are to lazy or just don't think there is enough users in the 64bit to care. Rather they are right is a different argument.

Oh and look at it this way  even if what you are saying is true.(the persom compiling it themself and such).

That still doesn't mean there will be an offical 64bit build.

---

### Post by Xbehave on 2010-01-11
> **Twitch6000 said:**
> I don't think compiling a 32bit program makes it 64bit. Thats a guess if you could show me why it does or how that would be nice lol.
Yes it does, a binary is architecture specific object code (well usually), if you have the source code and a compiler you can compile a "32bit program" (the code itself is architecture independent) to any object code your compiler supports. The code will not be optimized for 64bit specific tweaks, like it may have been for 32bit specific ones, but it will be 64bit and any compiler optimizations will be applied. Some code may break (i don't think there is anything available to 32bit that isn't for 64bit, so this is more relevant for arm/ppc/m68k/sh/etc ports, but if the developers do pointer arithmetic a 2 might need changing to a 4 and small bugs like that), but fixing small bugs isn't that hard (i.e even I can do it and i barely know c/c++)

> Anyways you just stated why it isn't because of skype being closed soure doesn't effect rather it is 64bit or not.
Because it's closed source nobody but the developers can port it, if it was opensource everybody with a 64bit OS (well actually you only need a 64bit compatible compiler which everybody with gcc has) could port it.

> That still doesn't mean there will be an official 64bit build.Who cares if it official (there are no official 64bit Firefox releases), it will exist and run that's all most people care about. And if the developers are smart they will accept the patches to fix building it on 64bit (if any are needed) and so releasing an official build would be easier.

edit:
Recently I couldn't get pyFragTools to run on 64bit python*, but because jdong had opensourced it (can a script be closed source :S) I fixed a couple of bugs and helped at least one other person use the tool.

*pysco is another 32bit only OSS program btw so the count is up to 2.

---

### Post by Twitch6000 on 2010-01-11
> **Xbehave said:**
> Yes it does, a binary is architecture specific object code (well usually), if you have the source code and a compiler you can compile a "32bit program" (the code itself is architecture independent) to any object code your compiler supports. The code will not be optimized for 64bit specific tweaks, like it may have been for 32bit specific ones, but it will be 64bit and any compiler optimizations will be applied. Some code may break (i don't think there is anything available to 32bit that isn't for 64bit, so this is more relevant for arm/ppc/m68k/sh/etc ports, but if the developers do pointer arithmetic a 2 might need changing to a 4 and small bugs like that), but fixing small bugs isn't that hard (i.e even I can do it and i barely know c/c++)


Because it's closed source nobody but the developers can port it, if it was opensource everybody with a 64bit OS (well actually you only need a 64bit compatible compiler which everybody with gcc has) could port it.

Who cares if it official (there are no official 64bit Firefox releases), it will exist and run that's all most people care about. And if the developers are smart they will accept the patches to fix building it on 64bit (if any are needed) and so releasing an official build would be easier.

edit:
Recently I couldn't get pyFragTools to run on 64bit python*, but because jdong had opensourced it (can a script be closed source :S) I fixed a couple of bugs and helped at least one other person use the tool.

*pysco is another 32bit only OSS program btw so the count is up to 2.

Well thanks for that info see I got proven wrong and learned something lol..

Oh and I am one who cares it is official. As someone could add bad code or bad things in a unofficial version. Unlikey yes,but it can happen.

---

### Post by SteveHillier on 2010-01-12
> **yester64 said:**
> But i never seen this really taken off in the windows world.

Isn't this my point from my first post.

XP 64 bit was available but no software to run on it.  I used a copy once where I was building a simple file server which relied only on system software and required no third party s/ware to run.

---

### Post by SteveHillier on 2010-01-12
> **blueshiftoverwatch said:**
> It seems like even if they're not very resource intensive they'd still be 100% more efficient because if Firefox went to send a message to my CPU it could transmit the data 64 bits at a time instead of 32. Which would take half as much time to do and allow the CPU to return to an idle state where it's not processing any data 2x as fast. 

I am not chip designer, nor a hardware person really but I think this is a simplistic view.
I know it not as simple as getting stuff back and forth twice as fast.  There is an overhead which detracts from the theoretical maths used in the post.

---

### Post by SteveHillier on 2010-01-12
> **Dark Aspect said:**
> How did you buy 64-bit Windows 7? I ask because my commercial disc has both x86 & 64-bit and I thought that both versions have been merged to a single disc?

I buy OEM in the UK and the two versions are packaged separately.  The retail packages have both versions.

---

### Post by cascade9 on 2010-01-12
> **amauk said:**
> x86_64 has been around for 7 years

x86 (32bit) has not seen a new processor on the market for 6 years, apart from the early Atoms
but even the Atom (I believe) has now moved to 64bit

Most people today (I assume) have a machine less than 6 years old
so most people do not have 32bit hardware

Nope, the 1st Intel Core series (Core Duo and Core Solo) came out in 2006 and are 32bit only. 

Not all new release Atoms are 64bit, the Z5xx series (still being released in 2009) and N2xx (same) are 32bit only. Both are 2.5Watt TDP and ower CPUs, though, so your only going to find them in netbooks and ultra-moblie PCs. 

> **insane_alien said:**
> and if you have 64-bit, why would you purposefully choose to not use it?

I'm with this 100% if your system supports 64bit, why not use it? Not like its a pain in the butt liek is was a few years ago...

---

### Post by markbuntu on 2010-01-12
64 bit is faster, no doubt about it. Except for consumer applications everything else has moved to 64 bit years ago and many large scale/computation intensive users have been moving to 128 bit for a while now. Yes there are 128 bit cpus and next year AMD will release some into the consumer market. These will already be supported by linux.

AMD has been making 64 bit cpus since the 1990s.

---

### Post by hessiess on 2010-01-12
While X86-64 is still a complete mess of an architecture compared to RISC designs, its still better than plain X86. X86 processors only have 8 registers whereas X86-64 has 16. The more registers a CPU has, the more it can do without having to do a slow memory read/write, which can massively improve system performance. Additionally working with 64 bit values improves calculation accuracy and the available addressable memory.

Although absolute performance is of little use these days, because most computers spend almost all of there time in idle loops anyway (check your CPU load, it will rarely go much above 1 or 2 percent).

---

### Post by Xbehave on 2010-01-12
> **SteveHillier said:**
> I am not chip designer, nor a hardware person really but I think this is a simplistic view.
I know it not as simple as getting stuff back and forth twice as fast.  There is an overhead which detracts from the theoretical maths used in the post.
The only overhead to running 64bit is that pointers and integers are bigger, so as a result binaries are bigger and it takes more memory to move that data to/from ram, however if you have >32bits of data you can need process, 64bit processors will be able to do that faster than a 32bit processor, only when you are moving a lot small data to/from the CPU will the 64bit processor be slower (even then the bottleneck is ram->cpu bandwidth not the processor itself).

> While X86-64 is still a complete mess of an architecture compared to RISC designs, its still better than plain X86I read somewhere (probably a forum so not that reliable) that modern CISC chips are effectively a bunch of RISC cores with CISC being emulated over the top, because CISC doesn't scale well enough but won the war by being mass produced and windows compatible, so now we're stuck with it.

---

### Post by SteveHillier on 2010-01-12
Genuine question here.

> **hessiess said:**
> The more registers a CPU has, the more it can do without having to do a slow memory read/write

Yes, I can understand this but are there not processes where instructions are executed that don't need all those registers?  And if this is the case then unless you can parallel process another instruction using another set of registers does this reduce the theoretical output?  And if you can parallel process how do you deal with processing sequential data?  I suppose this is the point of multi threading?

Now a comment

> **hessiess said:**
> (check your CPU load, it will rarely go much above 1 or 2 percent).

and if it does then you worry about what is taking up all the processor time and doing something to reduce it's demand on the system.

And another

The real thing is that is you have a job that is processor bound (ie where you need large amounts on computational power (graphics for example)) then there is a marked advantage to 64 bit.  If your job in disk bound or keyboard (input) bound then we will see no real advantage.  How many mflops have passed in the time it takes to press the keys needed to write this post?

It makes me laugh to hear people worrying about having the latest, fastest mahcine they can get and then wonder why it still takes just as long to download images from the internet.

---

### Post by Xbehave on 2010-01-12
> **SteveHillier said:**
>  If your job in disk boundYou can memory map larger files (not really an option on 32bit where address space is so limited), so while the program wont be faster it will be easier to write and .'. more likely to be bug free.

---

### Post by Techsnap on 2010-01-12
> How did you buy 64-bit Windows 7? I ask because my commercial disc has both x86 & 64-bit and I thought that both versions have been merged to a single disc?

With Vista x86 and x64 keys worked on either architecture. If you contact Microsoft they can send you the x64 media for a postage fee if you've already got the x86 version.

---

### Post by toupeiro on 2010-01-12
In a nutshell.  your 64-bit OS memory space can allow you to run more 32-bit applications simultaneously, even if a single 32-bit application may have memory address limits lower than the platform its running on.  The reason to run 64-bit software is obvious, it scales higher as your needs grow and as software footprints increase.  You're less likely to outgrow a 64-bit application from a capacity standpoint than a 32-bit application.   Functionally, it makes more sense to run 64-bit if its available to you. 64-bit computing in UNIX/Linux is not alltogether that new...  Its kind of funny to me why people would still desire to run a 32-bit operating system if their hardware has more to offer.  Just stay on your 32-bit hardware if thats your logic...  You obviously have no reason to upgrade for a very, very, very long time.

---

### Post by running_rabbit07 on 2010-01-12
> **NoaHall said:**
> Really? I disagree - far, far more open source applications are ported to 64 bit. I can run my entire GNU/Linux system, only on 64 bit. I can't say the same for Windows, and I can half say the same for Mac - I have a few older apps on Mac.> **toupeiro said:**
> Just stay on your 32-bit hardware if thats your logic... You obviously have no reason to upgrade for a very, very, very long time.

That's odd being 64bit flash works great on Windows, yet it runs like crap on linux. Funny how I can get programs that are only written for 32 bit to run on 64bit Windows 7, but I can't do it in Ubuntu. (Please don't try to explain how to get flash to work. I have tried numerous ways and the only thing that brings the quality, is restarting and choosing Windows 7 when I want to watch vids or go to my school's flash based site.)

For the small speed gain I would say it is more functional to run 32 bit Ubuntu over 64 bit any day. If I didn't have multiple .vdi files that won't run on 32bit, I would have downgraded by now.

---

### Post by gn2 on 2010-01-12
Why bother with 64?
Same reason for bothering with 32.
Technology moves onwards and upwards.

---

### Post by NoaHall on 2010-01-12
That's insane. That's all I'm saying.

Also, there's no 64 bit version of Flash for Windows. It's a 32 bit version. You could do that just as easily in GNU/Linux.

---

### Post by SeanHodges on 2010-01-12
> **running_rabbit07 said:**
> That's odd being 64bit flash works great on Windows, yet it runs like crap on linux.

I beg to differ, 64bit Flash runs just fine on my 64bit installation.

---

### Post by hessiess on 2010-01-12
> 
I read somewhere (probably a forum so not that reliable) that modern CISC chips are effectively a bunch of RISC cores with CISC being emulated over the top, because CISC doesn't scale well enough but won the war by being mass produced and windows compatible, so now we're stuck with it.

The problems with X86 are much deeper than a simple CISC vs RISC argument. The design of the architecture is basically a stack of extensions hacking the architecture into a state where it is somewhat up to date with modern practice. a 64 bit extension to a 32 bit extension to a 16 bit architecture.

Its so complicated that emulation is the only way to implement it in a cost effective way, which is extremely power inefficient(which is why X86 runs so hot) and is proof enough that the architecture has outlived its useful lifespan and should be discarded ASAP.

Computing as a whole cannot improve much further while dragging along this amount of legacy garbage, and has already become pretty stagnant.

> 
Yes, I can understand this but are there not processes where instructions are executed that don't need all those registers? And if this is the case then unless you can parallel process another instruction using another set of registers does this reduce the theoretical output? And if you can parallel process how do you deal with processing sequential data? I suppose this is the point of multi threading?


Registers are just small (normally 1 word) extremely fast blocks of memory. Say you have an imaginary RISC(load/store) CPU with 8 general propose registers, r0 to r7, one instruction could add the values in r0 and r1 then store the result in r2, then a folowing instruction could add r3 and r4, storing in r6 and finally a 3rd instruction could devide r2 and r6, storing in r7. At this point all the registers have bean used and a memory IO must be preformed.
More registers means that the CPU can do more without having to do an IO and IO operations can be batched together.

This gets more complicated with subroutines because registers have to be pushed onto/popped off the stack to save there previous state, more registers would potentially take longer to store or reload. This is especially true in the case of code consisting of a huge number of very small subroutines, though such code would be very inefishent even on an architecture with few registers.


Multi-threading is running separate application sub-processes which execute simultaneously(at least in theory) on separate processing cores, each of which has there own registers.

Yes higher performance is good for graphics and other highly CPU intensive tasks, however most people do not do these things with there computers. Modern games are one exception here.

---

### Post by gn2 on 2010-01-12
> **running_rabbit07 said:**
> Please don't try to explain how to get flash to work. 

Ok. I'll just tell you that it works perfectly and is really easy to sort out using a simple GUI method.

---

### Post by running_rabbit07 on 2010-01-12
> **NoaHall said:**
> That's insane. That's all I'm saying.

Also, there's no 64 bit version of Flash for Windows. It's a 32 bit version. You could do that just as easily in GNU/Linux.
That is another plus for MS for getting a 32bit product to work right on a 64bit system. If it is so easy to install 32bit software on 64bit Ubuntu, someone could have offered to help in the thread I had a while back that led me to reinstall Windows 7, because nobody was willing to help.
> **SeanHodges said:**
> I beg to differ, 64bit Flash runs just fine on my 64bit installation.
And I am sure you had to modify it from its original state.

---

### Post by NoaHall on 2010-01-12
> **running_rabbit07 said:**
> That is another plus for MS for getting a 32bit product to work right on a 63bit system. If it is so easy to install 32bit software on 64bit Ubuntu, someone could have offered to help in the thread I had a while back that led me to reinstall Windows 7, because nobody was willing to help.

And I am sure you had to modify it from its original state.

I promise, it's easy :) Let me know if you want a hand, in the future. But hey, use what works for you. I'm using Windows 7 64 bit, too, but I'm finding Flash a little slow.

---

### Post by running_rabbit07 on 2010-01-12
> **NoaHall said:**
> I promise, it's easy :) Let me know if you want a hand, in the future. But hey, use what works for you. I'm using Windows 7 64 bit, too, but I'm finding Flash a little slow.
Thanks. I also like being able to save the vids while watching them with RealPlayer.

---

### Post by SeanHodges on 2010-01-13
> **running_rabbit07 said:**
> And I am sure you had to modify it from its original state.

Maybe I wasn't clear. So here it is again:

64bit Flash runs just fine on my 64bit installation with no modification whatsoever. 

I only had to pick "Adobe Flash Player" in the automatic installer that appeared when I visited a Flash site.

---

### Post by Xbehave on 2010-01-13
> **SeanHodges said:**
> Maybe I wasn't clear. So here it is again:

64bit Flash runs just fine on my 64bit installation with no modification whatsoever. 

I only had to pick "Adobe Flash Player" in the automatic installer that appeared when I visited a Flash site.anything but specificially looking for the [64bit linux alpha]("http://labs.adobe.com/downloads/flashplayer10.html") will give you a 32bit player.

---

### Post by NoaHall on 2010-01-13
> **SeanHodges said:**
> Maybe I wasn't clear. So here it is again:

64bit Flash runs just fine on my 64bit installation with no modification whatsoever. 

I only had to pick "Adobe Flash Player" in the automatic installer that appeared when I visited a Flash site.

That's the 32 bit plugin(which is slower), running in a wrapper.

---

### Post by SeanHodges on 2010-01-13
> **Xbehave said:**
> anything but specificially looking for the [64bit linux alpha]("http://labs.adobe.com/downloads/flashplayer10.html") will give you a 32bit player.

The Beta is for Flash 10.1

The repository has Flash 10.0, including binaries for 64bit:

[http://packages.ubuntu.com/karmic/flashplugin-nonfree](http://packages.ubuntu.com/karmic/flashplugin-nonfree)

> Package: flashplugin-nonfree (10.0.42.34ubuntu0.9.10.1)

Perhaps the binaries are 32bit and made to work in 64bit with a wrapper, but until now I've never had to check because it has just worked.

when visiting the Flash website, it confirms that I'm running the 10.0 plugin:

[http://www.adobe.com/software/flash/about/](http://www.adobe.com/software/flash/about/)

> You have version 10,0,42,34 installed

---

### Post by NoaHall on 2010-01-13
> **SeanHodges said:**
> The Beta is for Flash 10.1

The repository has Flash 10.0, including binaries for 64bit:

[http://packages.ubuntu.com/karmic/flashplugin-nonfree](http://packages.ubuntu.com/karmic/flashplugin-nonfree)



Perhaps the binaries are 32bit and made to work in 64bit with a wrapper, but until now I've never had to check because it has just worked.

when visiting the Flash website, it confirms that I'm running the 10.0 plugin:

[http://www.adobe.com/software/flash/about/](http://www.adobe.com/software/flash/about/)

The binaries are 32 bit. You are using the 32 bit flash.

---

### Post by SeanHodges on 2010-01-13
> **NoaHall said:**
> That's the 32 bit plugin(which is slower), running in a wrapper.

Thanks for the info. Perhaps it benchmarks as slower (compared to 32bit), but it works just fine on my system. Are there others who find it excessively slow?

---

### Post by NoaHall on 2010-01-13
> **SeanHodges said:**
> Thanks for the info. Perhaps it benchmarks as slower (compared to 32bit), but it works just fine on my system. Are there others who find it excessively slow?

I did, compared to the proper 64 bit version :) But hey, if it works for you, stick with it :)

---

### Post by yester64 on 2010-01-13
> **Twitch6000 said:**
> Oh really lol. Look at pclinuxos for a good example. Its open source yet the devs still have not made a 64bit. 

Oh and you say you cant run windows 64 bit. You are certainly wrong there aswell. I have a friend who bought windows 7 64 bit and it has all 64bit software.

Beware, i had as an example Acdsee for Vista and its a 32bit app which is Vista certified.
Which means, it runs under Vista or so it should.
There is not a lot of software that is truely 64. One software i had which was indeed 64 was 7zip, Ventrilo, Dopus. The rest was just 32 bit and thats only 4 month ago. I don't think it changed since then.
Of course it depends what software you run. But most software does come in 32bit code and not 64bit. That is most true in the game software.
Of course this in the Windows world where i had experience. Can't say anything else about Mac. On linux it is indeed mostly 64bit (which i am very happy) and just some exceptions are 32bit.

---

### Post by hyperdude111 on 2010-01-13
Adobe have released an official flash for 64 bit beta. (NOT in wrapper).

Speed is equal with the 32 bit version and it is easy to install. There is currently only a 64bit version for Linux, not windows or mac.

However not using 64bit because not all apps take full advantage of it (even though the vast majority of Linux apps do) is similar to not using multi core pocessors when they were first introduced, because some apps had not been esigned to work with more than one core.

---

### Post by Kai69 on 2010-01-18
Hi all sorry to butt in here but SKYPE has a 64bit install.....
[http://www.skype.com/download/skype/linux/choose/](http://www.skype.com/download/skype/linux/choose/)

---

### Post by dwflo on 2010-01-18
> **Kai69 said:**
> Hi all sorry to butt in here but SKYPE has a 64bit install.....
[http://www.skype.com/download/skype/linux/choose/](http://www.skype.com/download/skype/linux/choose/)

Says for Ubuntu 8.10, not sure why no 9.10!!!

Regards,

Dave

---

### Post by Kai69 on 2010-01-21
Im using ubuntu 9.10 64bit and using skype 64bit no problems. As for a new skype version they are working on it .

---

### Post by Psumi on 2010-01-21
Why bother with 128-bit for Windows 8?

---

### Post by samh785 on 2010-01-21
> **dwflo said:**
> Says for Ubuntu 8.10, not sure why no 9.10!!!

Regards,

Dave
it says 8.10+ which signifies 8.10 and up.

---

### Post by mikewhatever on 2010-01-21
> **Kai69 said:**
> Im using ubuntu 9.10 64bit and using skype 64bit no problems. As for a new skype version they are working on it .

Take a look at the link below. There isn't a 64bit Skype yet, and with there pace of development, I wouldn't expect one for another couple of years.
[http://share.skype.com/sites/linux/2009/09/some_explanations.html](http://share.skype.com/sites/linux/2009/09/some_explanations.html)

---

### Post by MaxIBoy on 2010-01-21
If you want to use more than 4 gigs of RAM, but you don't need any one program to have that much, you can use a 32-bit PAE (Physical Address Extension) kernel, AKA a "bigmem" kernel, which can address up to 64 gigs. However, PAE kernels are somewhat slower than normal 32-bit kernels, and few people use them.

Eventually, it will be commonplace for some individual programs to use more than 4 gigs of RAM (such as editing long HD videos.) 64-bit OSs are a prerequisite for this. 

Also, (though this is specific to the x86 architecture,) 64-bit software can run faster since more CPU registers are available. And I think paging might be more efficient in 64-bit mode too.

However, the performance boost is relatively minor and not the main benefit. First of all, when loading software and moving lots of data around, the bottleneck is and always will be the speed of your storage. Even if storage was insanely fast, RAM speed would become the bottleneck. This is why L1, L2, and L3 cache exist. Even a CPU from two or three years ago could easily exhaust the maximum I/O speed of today's latest RAM. Doubling the data rate the CPU can take does not help this (and CPUs have had well over 64bit RAM buses anyway since the Pentium days, if I remember correctly.) And while the extra registers make your CPU just a bit faster, on the whole whole the performance of your CPU stays very roughly the same. Of course, this depends on the type of operations you perform and how good your compiler is.

---

