---
title: "SUSE/Novell Removes all Non-GPL kernel modules"
date: 2006-02-13
forum: The Cafe
---

### Post by jdong on 2006-02-13
For those who haven't heard yet, Novell has announced that it's no longer going to ship any non-GPL kernel modules:

[http://lists.opensuse.org/archive/opensuse-announce/2006-Feb/0004.html](http://lists.opensuse.org/archive/opensuse-announce/2006-Feb/0004.html)
> 
non-GPL kernel modules:
=======================

Most developers of the kernel community consider non-GPL kernel
modules to be infringing on their copyright. Novell does respect this
position, and will no longer distribute non-GPL kernel modules as part of
future products. Novell is working with vendors to find alternative
ways to provide the functionality that was previously only available
with non-GPL kernel modules. 



The biggest effect is that SUSE will no longer have a built-in installer for NVidia/ATI video cards.

---

### Post by void_false on 2006-02-13
OMG... Looks like I wont go from my SUSE10.0 any further. :confused:

---

### Post by akurashy on 2006-02-13
just while i was reading thought the same thing "well there goes nvidia/ati support" i wonder how they going to do now?

---

### Post by gord on 2006-02-13
so they make a new compositing manager using your graphics card that you can't use because your graphics card isn't supported by default? funky

---

### Post by Brunellus on 2006-02-13
...which puts it right in line with Ubuntu, which doesn't have built-in nvidia or ati support either.  (or atheros wifi for that matter).

This is all part of the move to OpenSUSE and away from the SuSE-in-a-box model.  When they sold a commercial SuSE, they could include the non-GPL modules.  now, no longer, by default.  

That's my read anyhow

---

### Post by jdong on 2006-02-13
No, it doesn't make it like Ubuntu. Ubuntu DOES include non GPL drivers (linux-restricted-modules) in its repository.

Novell is saying, like most kernel devs, any kernel module that isn't GPL'd is a violation of the GPL, and as a result not legal. I certainly hope Ubuntu doesn't take this stance or betting 3D acceleration on these popular cards will be a pain.

I'm not sure if VMWare's kernel modules are GPL'd or not, but man is this licensing stuff a pain to deal with ;)

---

### Post by Brunellus on 2006-02-13
I misinterpreted this, then.  Because vanilla ubuntu installs do not have nvidia/ati binary drivers installed by default;  they must be added later.

---

### Post by jdong on 2006-02-13
Basically this means Novell will not be shipping the closed-source kernel modules or have it in any of their repositories. I'm sure 3rd party packagers will be providing these packages, but that's just more configuration than currently.

this is roughly comparable with the Ubuntu stand on win32codecs: We won't do anything to purposely stop people from using them (ahem, Novell), but get them yourself :)

---

### Post by xequence on 2006-02-13
They seem to be doing alot of things that makes it to the news latly, eh?

---

### Post by Lord Illidan on 2006-02-13
[quote=jdong]No, it doesn't make it like Ubuntu. Ubuntu DOES include non GPL drivers (linux-restricted-modules) in its repository.

Novell is saying, like most kernel devs, any kernel module that isn't GPL'd is a violation of the GPL, and as a result not legal. I certainly hope Ubuntu doesn't take this stance or betting 3D acceleration on these popular cards will be a pain.

I'm not sure if VMWare's kernel modules are GPL'd or not, but man is this licensing stuff a pain to deal with ;)[/quote] 
I hate this licensing stuff too. Sometimes I think that RMS is taking things too far. Some things just cannot be GPLed, and those are video card drivers. 
 Well, that is one distro I don't think I will use in the future then!

---

### Post by az on 2006-02-13
[QUOTE=jdong]For those who haven't heard yet, Novell has announced that it's no longer going to ship any non-GPL kernel modules:

.[/QUOTE]


This is a good thing.

:)

Are they going to start using deb packages, too?

---

### Post by az on 2006-02-13
[QUOTE=Lord Illidan]Some things just cannot be GPLed, and those are video card drivers. 
 [/QUOTE]

Completely false.

---

### Post by Brunellus on 2006-02-13
[QUOTE=azz]Completely false.[/QUOTE]
azz:  the sense of the statement was probably closer to:  "it is unlikely that the vendors of those video cards will provide Free drivers."  It was NOT "it is IMPOSSIBLE to make this software Free."

---

### Post by imagine on 2006-02-13
Quite simple: Some hardware manufacturers do not want to release the source of their drivers or better yet their specifications, and many kernel hackers or more general free software authors do not want proprietary code in or around their software.
This is a constant battle which takes place since years. Just look at the interface changes in every new kernel release, which usually break proprietary drivers that rely on them. I'm no kernel hacker, but I don't have the impression that there are always strong technical reasons for those API changes ; )
That said the position of the kernel developers obviously becomes more powerful if the Linux market share grows and less powerful if it shrinks. However until now the market share only grew and continues to grow : )

You can already see the complaints from some companies rolling, not only because those non-free kernel modules were removed by Novell, but also because the USB subsystem was marked GPL-only, so the proprietary drivers either have to be opened or wander off into the userspace.

---

### Post by az on 2006-02-13
[QUOTE=Brunellus]azz:  the sense of the statement was probably closer to:  "it is unlikely that the vendors of those video cards will provide Free drivers."  It was NOT "it is IMPOSSIBLE to make this software Free."[/QUOTE]

I agree.  It is important to make that distinction because there is no law that says that any software has to be proprietary.  Some people think there is.

Heck, some people still think you are breaking the law by removing Windows from your computer.  This is the same kind of misunderstanding.

---

### Post by mstlyevil on 2006-02-13
[QUOTE=azz]I agree.  It is important to make that distinction because there is no law that says that any software has to be proprietary.  Some people think there is.

Heck, some people still think you are breaking the law by removing Windows from your computer.  This is the same kind of misunderstanding.[/QUOTE]

I am still waiting for the Windows Gestapo to come and break down my door and shoot me. ;)

---

### Post by xequence on 2006-02-13
> Heck, some people still think you are breaking the law by removing Windows from your computer. This is the same kind of misunderstanding.

Wow, never heard that one before. Amazing what crazy things people can think.

---

### Post by jdong on 2006-02-13
[QUOTE=azz]
Heck, some people still think you are breaking the law by removing Windows from your computer.  This is the same kind of misunderstanding.[/QUOTE]


LOL, I've heard a lot worse from some of the MS techies I've come across. They tend to associate Linux / Open Source with mass piracy and illegal activities... Took a Knoppix and a Ubuntu LiveCD to convince them otherwise ;)

---

### Post by asimon on 2006-02-14
Absolutely great, I like SUSE more and more. (Seriously)

---

### Post by Leo_01 on 2006-02-14
Anyone feel there should be some changes to the GPL to allow Closed-Sourced apps and drivers?
The whole Free software idea is to have "freedom" in the software we use.
I really don't see how having NON-GPL-ed app or driver will affect Linux.

---

### Post by BoyOfDestiny on 2006-02-14
[QUOTE=Leo_01]Anyone feel there should be some changes to the GPL to allow Closed-Sourced apps and drivers?
The whole Free software idea is to have "freedom" in the software we use.
I really don't see how having NON-GPL-ed app or driver will affect Linux.[/QUOTE]

[http://www.gnu.org/copyleft/lesser.html](http://www.gnu.org/copyleft/lesser.html)

As for software freedom, part of the freedom is to tinker/change software. Something you can't normally do with a proprietary and closed solution (not necessarly non-gpl, there are a lot of software licenses that are considered open source by osi [[http://www.opensource.org/licenses/])](http://www.opensource.org/licenses/]))...

---

### Post by Leo_01 on 2006-02-14
Don't you think that licence should be changed?
That is basically WHY not many companies are willing to port their software over to Linux platform.
There is NO way a graphics company will be willing to port their 500 bucks software for free in Linux.
We should be looking at real world situation rather than just "hoping" for a "free" future.

---

### Post by Lovechild on 2006-02-14
I wish they would have included a list of affected modules with that statement.

---

### Post by nickle on 2006-02-14
So what does all this mean for the "Joe Blogs" linux user (like me). Will it become easier or more difficult to install and use?

---

### Post by Lovechild on 2006-02-14
[QUOTE=nickle]So what does all this mean for the "Joe Blogs" linux user (like me). Will it become easier or more difficult to install and use?[/QUOTE]

It will probably remain about the same, most of the drivers needed for a basic system are already GPL'ed.

but it does mean fewer drivers.

I would say it's a step towards better computing, it means removing failure points due to closed parts (firmware mostly) and eventually we will reverse engineer the needed parts and clean room implement them. And these will be easy to maintain and adapt due to API changes and such.

But there will be growing pains.

---

### Post by LordBug on 2006-02-14
> There is NO way a graphics company will be willing to port their 500 bucks software for free in Linux
Who said Linux software HAS to be free?  If they want to port their $500 software package to Linux and then charge $500 for it, they're allowed to.  There's already commercial software out there for Linux (Cedega, most iD games, Codeweavers, others).

---

### Post by az on 2006-02-14
[QUOTE=Leo_01]Don't you think that licence should be changed?.[/QUOTE]
No.  It would be easy to disregard human rights when it makes the situation easier for you or your government, no?  This is the same thing.

The strength of Ubuntu and all other free-libre software is that it protects your freedoms.  You have a right to know what your computer is doing.  You have a right to be able to change the software.  You have a right to be able to redistribute those changes.

It is easy to disregard on the basis of something that works right now, but many people have suffered the pain of having a company drop support for a certain technology.  It is also a very powerful developmental model.

Not a lot of people would be contributing to ubuntu today if it were not for those ideals, actualy. 

[QUOTE=Leo_01]
That is basically WHY not many companies are willing to port their software over to Linux platform.
There is NO way a graphics company will be willing to port their 500 bucks software for free in Linux..[/QUOTE]

You cannot consider free-libre software in the same way as proprietary software.  Software is not property.  If you are selling software, of course that does not make sense to you.

If you are making money from producing and supporting software, that is a different story.  Novell make money (I hope) but contributing to the free-libre software ecosystem, and by charging for professional services and support.

[QUOTE=Leo_01]
We should be looking at real world situation rather than just "hoping" for a "free" future.[/QUOTE]

Free-libre software is real.  Here and now people are making a lot of money from it.  Mark Shuttleworth made millions using free software (he provided a web service)  IBM has millions of dollars invested in linux ("unbreakable linux")  Yahoo uses free-libre software.  Pixar, the list goes on and on.

You have to realise that most of the software that is made in the world is not going to be shrink-wrapped boxed programs on a cd with a manual, but software that makes the world go 'round.  In that context, to see software as something that is not someone's property is not such a crazy idea.

---

### Post by az on 2006-02-14
[QUOTE=Lovechild]I wish they would have included a list of affected modules with that statement.[/QUOTE]

If you look at what is in linux-restricted modules, you should have a good idea.  There are no other non-free-libre kernel modules in the Ubutu kernel.

You can remove that package to run a completely GPL'ed Ubuntu system, so long as you only use packages from main and universe (not restricted or multiverse)

---

### Post by az on 2006-02-14
[QUOTE=nickle]So what does all this mean for the "Joe Blogs" linux user (like me). Will it become easier or more difficult to install and use?[/QUOTE]

Short term: more difficult for a user - more hoops to jump through.  Long term:  more vendors providing proper FLOSS drivers - which will lead to an easier time for all users.

---

### Post by imagine on 2006-02-14
A little bit more information: The non-free modules and drivers will be removed from all Novell Linux products (Opensuse, Suse Linux Enterprise Server, Novell Linux Desktop). However Novell will provide links/instructions for customers on how to get proprietary drivers from third party sources and offer support to hardware manufacturers for developing opensource drivers or for moving proprietary drivers into the userspace.

So the approach is similar to the one of Ubuntu, just that Ubuntu hosts the proprietary stuff on its own servers.

---

### Post by KiwiNZ on 2006-02-14
If Nvidia chose to release a "pay for" Linux driver that gave the full potential of the card I would buy it

---

### Post by az on 2006-02-14
[QUOTE=KiwiNZ]If Nvidia chose to release a "pay for" Linux driver that gave the full potential of the card I would buy it[/QUOTE]
If you dist-upgrade your system to a new kernel after one year, you have to pay linuxant for their modem driver again.

Why would it be different for Nvidia?  How many times do you want to pay for this Nvidia driver?

---

### Post by KiwiNZ on 2006-02-14
As the need arises, as I do for Windows.

---

### Post by Lovechild on 2006-02-14
[QUOTE=KiwiNZ]If Nvidia chose to release a "pay for" Linux driver that gave the full potential of the card I would buy it[/QUOTE]

I can't say I agree - I'm not about to stick a closed source module into my kernel - I'd rather buy a card with a proper open driver and suffer a bit - then tell the manufactor why I went with their card.

---

### Post by imagine on 2006-02-14
[QUOTE=Leo_01]Anyone feel there should be some changes to the GPL to allow Closed-Sourced apps and drivers?[/QUOTE]The GPL does of course allow non-free applications, it cannot forbid them. It just doesn't allow you to modify or extend proprietary software with code that is licensed under the GPL, and then release the result partly or completely under a proprietary licence again.
The whole point of the GPL is to be able to release free code which *stays* free, ie nobody can come and include this code into his proprietary software. That's called copyleft: [http://www.gnu.org/copyleft/](http://www.gnu.org/copyleft/)

Applied to Linux (the kernel) itself which is licensed under the GPL: If you take the kernel and add some stuff to it, then the result has to be licensed under a GPL-compatible licence too - ie the whole thing has to be opensource. (Now ignoring that it is controversial if loading a module is actually extending or modifying a software).


And lastly some reasons why proprietary drivers are usually not what users want: [http://lkml.org/lkml/2005/11/7/31](http://lkml.org/lkml/2005/11/7/31)

---

### Post by rjwood on 2006-02-14
Thanks azz, imagine and everyone else for the info. I learned alot in this thread.

---

### Post by mstlyevil on 2006-02-14
[QUOTE=KiwiNZ]If Nvidia chose to release a "pay for" Linux driver that gave the full potential of the card I would buy it[/QUOTE]

As far as I am concerned, I paid for those drivers and their updates when I shelled out good money to buy a graphics card that only cost a fraction of what I paid to make. The rest of the cost was for the drivers to properly run it. I am dead set against having to pay for them over and over again.

---

### Post by jdong on 2006-02-14
[QUOTE=Leo_01]Don't you think that licence should be changed?
That is basically WHY not many companies are willing to port their software over to Linux platform.
There is NO way a graphics company will be willing to port their 500 bucks software for free in Linux.
We should be looking at real world situation rather than just "hoping" for a "free" future.[/QUOTE]

No, the software does't HAVE to be free. The NVidia driver is actually a good example. It uses source code wrappers around a binary "firmware" (blob of code that's the actual driver). However, they need to GPL the source for the kernel module:

> 
nv.c:
/* _NVRM_COPYRIGHT_BEGIN_
 *
 * Copyright 1999-2001 by NVIDIA Corporation.  All rights reserved.  All
 * information contained herein is proprietary and confidential to NVIDIA
 * Corporation.  Any use, reproduction, or disclosure without the written
 * permission of NVIDIA Corporation is prohibited.
 *
 * _NVRM_COPYRIGHT_END_
 */


---

