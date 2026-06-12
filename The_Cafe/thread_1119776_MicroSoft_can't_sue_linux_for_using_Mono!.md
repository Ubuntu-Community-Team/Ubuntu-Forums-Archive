---
title: "MicroSoft can't sue linux for using Mono!"
date: 2009-04-08
forum: The Cafe
---

### Post by wildman4god on 2009-04-08
I have heard many people complain about the use of mono in Linux, saying that Microsoft could sue Linux. Well I found a website that said that Microsoft made .net in a way that allowed developers to make their own version on any platform:

[http://www.eweek.com/c/a/Application-Development/Using-MoMA-to-Port-from-Windows-NET-to-Mono-on-Linux-184710/](http://www.eweek.com/c/a/Application-Development/Using-MoMA-to-Port-from-Windows-NET-to-Mono-on-Linux-184710/)

So all the paranoid people can now breath.

---

### Post by eragon100 on 2009-04-08
> **wildman4god said:**
> I have heard many people complain about the use of mono in Linux, saying that Microsoft could sue Linux. Well I found a website that said that Microsoft made .net in a way that allowed developers to make their own version on any platform:

[http://www.eweek.com/c/a/Application-Development/Using-MoMA-to-Port-from-Windows-NET-to-Mono-on-Linux-184710/](http://www.eweek.com/c/a/Application-Development/Using-MoMA-to-Port-from-Windows-NET-to-Mono-on-Linux-184710/)

So all the paranoid people can now breath.

They assist the mono developers. With specs and test scenarios and such.

All the people can already breath, they just choose to sophicate :wink:

---

### Post by Johnsie on 2009-04-08
Oh I'm pretty sure they could choose to sue over some elements in Linux that may breach patenting rules. The question is not if they CAN sue, it's whether or not they WILL sue.

---

### Post by Simian Man on 2009-04-08
I don't think very many people actually believe Mono is a liability.  They just can't accept the fact that Microsoft actually designed something decent and opened the standard - they'd much rather rave about how Microsoft are Satan incarnate.  Why let facts get in the way of a great conspiracy theory?

---

### Post by Firestem4 on 2009-04-08
> **Simian Man said:**
> I don't think very many people actually believe Mono is a liability.  They just can't accept the fact that Microsoft actually designed something decent and opened the standard -** they'd much rather rave about how Microsoft are Satan incarnate.  Why let facts get in the way of a great conspiracy theory?**

But...but...Its just so fun and easy to do!

---

### Post by Tibuda on 2009-04-08
Mono follows an ECMA standard if I'm not wrong. There are more stuff they can sue Linux for, like FAT/NTFS support, Wine and double-click.

---

### Post by 2cute4u on 2009-04-08
> **Simian Man said:**
> I don't think very many people actually believe Mono is a liability.  They just can't accept the fact that Microsoft actually designed something decent and opened the standard - they'd much rather rave about how Microsoft are Satan incarnate.  Why let facts get in the way of a great conspiracy theory?
The problem is that they didn't design something decent.  Mono and .Net are major bloatware, that eat system resources unnessesarily.  Even if both Mono and .NET were GPL 3, and software patents didn't exist; Mono would still suck.

---

### Post by Methuselah on 2009-04-08
> **2cute4u said:**
> The problem is that they didn't design something decent.  Mono and .Net are major bloatware, that eat system resources unnessesarily.  Even if both Mono and .NET were GPL 3, and software patents didn't exist; Mono would still suck.

Thanks.

And furthermore not ALL of what is commonly considered .NET is an ECMA standard.
Some portions (like Windows Forms or ASP.NET) might, in fact, be considered microsoft intellectual property still.

As I say, for compatibility I'm fine with it.
It makes no sense for critical open source software to depend on it when there are mature alternatives that do the same thing.
I don't get it.

---

### Post by Mehall on 2009-04-08
ASP.NET is getting released under MSFT's new Open Source license.

---

### Post by Methuselah on 2009-04-08
> **Mehall said:**
> ASP.NET is getting released under MSFT's new Open Source license.


Interesting, I didn't know that.
Is this license compatible with the open source licenses common in the community or are there encumberances?

Edit: are you sure it's not just a single part of ASP.NET?
[http://tech.slashdot.org/article.pl?sid=09/04/02/1845214&from=rss](http://tech.slashdot.org/article.pl?sid=09/04/02/1845214&from=rss)

---

### Post by saulgoode on 2009-04-08
> **danielrmt said:**
> Mono follows an ECMA standard if I'm not wrong.
Being an ECMA standard does nothing to ensure patent indemnity.

> **Mehall said:**
> ASP.NET is getting released under MSFT's new Open Source license.
Only the ASP.NET **MVC (model view controller)** is being released under Microsoft's anti-GPL, pro-proprietary MS-PL.

---

### Post by Simian Man on 2009-04-08
> **2cute4u said:**
> The problem is that they didn't design something decent.  Mono and .Net are major bloatware, that eat system resources unnessesarily.  Even if both Mono and .NET were GPL 3, and software patents didn't exist; Mono would still suck.

.NET and Mono actually don't suck.  If you are using an ancient computer, perhaps the overhead of such a system would be problem, but for the rest of us, the benefits outweigh the costs.  Why are Banshee, F-Spot and Tomboy (all great apps) written in Mono if it sucks so bad?


[quote=Methuselah]And furthermore not ALL of what is commonly considered .NET is an ECMA standard.
Some portions (like Windows Forms or ASP.NET) might, in fact, be considered microsoft intellectual property still.[/quote]
So a library using a particular language and platform are not open, therefore the language and platform are proprietary?  There are many C libraries that are proprietary, therefore C shouldn't be used?

[quote=Methuselah]As I say, for compatibility I'm fine with it.
It makes no sense for critical open source software to depend on it when there are mature alternatives that do the same thing.
I don't get it.[/quote]
Yeah but the alternatives also have their flaws.  Coding in C or C++ sucks ***.  Python is nice, but is slower than JIT languages like C# (it amuses me how people love to complain about the speed of C# and Java, but never mention Python despite being an order of magnitude slower).  And Java sucks much harder than .NET/Mono by any fair comparison.

---

### Post by smbm on 2009-04-08
> **Simian Man said:**
> Why are Banshee, F-Spot and Tomboy (all great apps) written in Mono if it sucks so bad?

Not to mention Gnome-do, Docky has become integral to my computing work flow since it was released.

---

### Post by gnomeuser on 2009-04-08
> **saulgoode said:**
> 

Only the ASP.NET **MVC (model view controller)** is being released under Microsoft's anti-GPL, pro-proprietary MS-PL.

do you have a problem with the MIT X11 license?

If you don't then you should also know that MS-PL is the X11 license plus a patent grant. It's OSI approved as living up to the requirements to be called Open Source.

Aside that .NET is governed by an ECMA standard and Microsoft have put significant portions of their current and past specifications under their Open Specification Promise - this is a legally binding, no revokable promise to never sue. They continue to increase the amount of code they put under OSI approved licenses and they donate to projects like Apache. They even ship and support other peoples Open Source code, most notably JQuery.

I am happy to see these developments.

---

### Post by directhex on 2009-04-08
> **gnomeuser said:**
> do you have a problem with the MIT X11 license?

“If it ain’t GNU/GPL v.3 ain’t FOSS”

(from the comments on a certain idiot blog)

---

### Post by gnomeuser on 2009-04-08
> **directhex said:**
> “If it ain’t GNU/GPL v.3 ain’t FOSS”

(from the comments on a certain idiot blog)

I am impressed you can actually stand reading that vile tripe. You are truly a braver man than I good sir, I shall buy you a round.

---

### Post by zolookas on 2009-04-08
> **Simian Man said:**
> .NET and Mono actually don't suck.  If you are using an ancient computer, perhaps the overhead of such a system would be problem, but for the rest of us, the benefits outweigh the costs.  Why are Banshee, F-Spot and Tomboy (all great apps) written in Mono if it sucks so bad?


I have been using Banshee for a while and I have noticed that it uses more CPU compared to other players by looking at the CPU load applet (though, i was not huge). There was a comparision somewhere between file indexers and you could clearly see differences between tracker (written in C) and beage (written in C#) in terms of memory and CPU usage. Things like that are important when you use laptops/netbooks/mobile devices.

---

### Post by Twitch6000 on 2009-04-08
> **directhex said:**
> “If it ain’t GNU/GPL v.3 ain’t FOSS”

(from the comments on a certain idiot blog)

That made me laugh so hard I cried I must thank you for the good laugh.

---

### Post by directhex on 2009-04-08
> **gnomeuser said:**
> I am impressed you can actually stand reading that vile tripe. You are truly a braver man than I good sir, I shall buy you a round.

> **Twitch6000 said:**
> That made me laugh so hard I cried I must thank you for the good laugh.

These replies are related ;)

Don't get mad at that site for posting maddeningly stupid things - laugh at it. It's hilarious.

Look at Occam's Razor, and use it to answer the question "why does that site's author act like a dick"
Then look at Hanlon's razor, and apply it to your answer from above. The riddle solved!

---

### Post by directhex on 2009-04-08
> **zolookas said:**
> I have been using Banshee for a while and I have noticed that it uses more CPU compared to other players by looking at the CPU load applet (though, i was not huge). There was a comparision somewhere between file indexers and you could clearly see differences between tracker (written in C) and beage (written in C#) in terms of memory and CPU usage. Things like that are important when you use laptops/netbooks/mobile devices.

Beagle was removed as default desktop indexer, due to Tracker being faster & more stable. Generally speaking, Ubuntu uses apps which are technically best - regardless of framework or language.

As for Banshee, it's more RAM-hungry than Rhythmbox, but not as hungry as Songbird or Exaile. CPU-wise it should be about the same for all of those - they all use gstreamer for playback

---

### Post by gnomeuser on 2009-04-08
> **directhex said:**
> Beagle was removed as default desktop indexer, due to Tracker being faster & more stable. Generally speaking, Ubuntu uses apps which are technically best - regardless of framework or language.

As for Banshee, it's more RAM-hungry than Rhythmbox, but not as hungry as Songbird or Exaile. CPU-wise it should be about the same for all of those - they all use gstreamer for playback

And Tracker was removed because despite all this talk about how Indexers were going to make life great nobody integrated and used that functionality. 

That being said I prefer Beagle, it is far more stable for me and does not have this tendency to get stuck in 100% CPU load scenerios (it used to but it got fixed). Sadly Novell doesn't have anyone actively developing it anymore and the community member who has taken over is running out of time. I am happy though that it is fairly complete as it is.

Overall the whole indexing thing really needs to get integrated and for that we need Xesam.. which seems to never be able to hit 1.0 for some reason. It is to bad this area showed a lot of promise but it just seems to keep hitting road blocks and never reaching the point where it is actually useful for many of the things that were envisioned.

---

### Post by directhex on 2009-04-08
> **gnomeuser said:**
> It is to bad this area showed a lot of promise but it just seems to keep hitting road blocks and never reaching the point where it is actually useful for many of the things that were envisioned.

How many years has Microsoft been failing to make Desktop Search happen & not suck? Nearly 20? We've got a long way to go before we suck on that level

---

### Post by saulgoode on 2009-04-08
> **gnomeuser said:**
> do you have a problem with the MIT X11 license?

If you don't then you should also know that MS-PL is the X11 license plus a patent grant. It's OSI approved as living up to the requirements to be called Open Source.
I have no problem whatsoever with the MIT and X11 licenses, neither of which is designed to be incompatible with the GPL (and thus two-thirds of the world's Free Software). The Microsoft Permissive License IS incompatible with the GPL; and, unlike the GPL, the MS-PL provides an incentive for distributors NOT to share the source code.

The patent grant incorporated into the MS-PL is indeed admirable, but it is not sufficient to overcome the fact that the license is entirely incompatible with the majority of Free Software currently available (and intentionally so). 

You are welcome to your opinion about how wonderful Microsoft's Open Source efforts may be, but the MS-PL is not comparable to the Free Software permissive licenses such as BSD, MIT, and X11.

> **gnomeuser said:**
> Aside that .NET is governed by an ECMA standard and Microsoft have put significant portions of their current and past specifications under their Open Specification Promise - this is a legally binding, no revokable promise to never sue.

Does any such "promise" exist for the **core** ECMA 335 standard (that is to say, implementations thereof)? If so, please provide a link that we might examine the terms one must fulfill to benefit from that "promise".

---

### Post by directhex on 2009-04-08
> **saulgoode said:**
> I have no problem whatsoever with the MIT and X11 licenses, neither of which is designed to be incompatible with the GPL (and thus two-thirds of the world's Free Software). The Microsoft Permissive License IS incompatible with the GPL; and, unlike the GPL, the MS-PL provides an incentive for distributors NOT to share the source code.

The patent grant incorporated into the MS-PL is indeed admirable, but it is not sufficient to overcome the fact that the license is entirely incompatible with the majority of Free Software currently available (and intentionally so). 

You are welcome to your opinion about how wonderful Microsoft's Open Source efforts may be, but the MS-PL is not comparable to the Free Software permissive licenses such as BSD, MIT, and X11.

It's still not entirely clear to me why Ms-PL is not GPL-compatible - it was previously marked as v3-compatible, but this was changed by the FSF without notice or comment. I suspect 3)d) is the issue - however, there's a big difference between "you may only do so under this license" (GPL-incompatible copyleft) and "you may only do so under a license that complies with this license" (compatibility requirement from the actual license)

---

### Post by saulgoode on 2009-04-08
> **directhex said:**
> It's still not entirely clear to me why Ms-PL is not GPL-compatible - it was previously marked as v3-compatible, but this was changed by the FSF without notice or comment. I suspect 3)d) is the issue - however, there's a big difference between "you may only do so under this license" (GPL-incompatible copyleft) and "you may only do so under a license that complies with this license" (compatibility requirement from the actual license)
The requirement of the MS-PL is that: **"If you distribute any portion of the software in source code form, you may do so only under this license..."**.

Since the GPL basically *requires* that you distribute "in source code form" --  -- there is no way to fulfill both the GPL requirements (retaining GPL licensing) and the MS-PL requirements (distribute under MS-PL).

---

### Post by gnomeuser on 2009-04-08
> **directhex said:**
> How many years has Microsoft been failing to make Desktop Search happen & not suck? Nearly 20? We've got a long way to go before we suck on that level

I haven't used Windows in over a decade, so I honestly wouldn't know.

However I would not be surprised if we can do it better than them.. 40 years and sucking harder than a perfect vaccuum

---

### Post by directhex on 2009-04-08
> **saulgoode said:**
> The requirement of the MS-PL is that: **"If you distribute any portion of the software in source code form, you may do so only under this license..."**.

Since the GPL basically *requires* that you distribute "in source code form" --  -- there is no way to fulfill both the GPL requirements (retaining GPL licensing) and the MS-PL requirements (distribute under MS-PL).

What's wrong with distributing source files under their own licenses, exactly? Plenty of apps use different licenses in their source - as long as the combined work can be combined legally when compiled, and follows the requirements of the combined work, then where's the issue?

Unless of course the issue is "the combined binary is GPL, so the source code needs to be distributed as GPL"

In which case the GPL is the douche license in that scenario

---

### Post by JordyD on 2009-04-08
The question is not will they/can they sue, it is who do they sue.

---

### Post by saulgoode on 2009-04-08
> **directhex said:**
> What's wrong with distributing source files under their own licenses, exactly? Plenty of apps use different licenses in their source - as long as the combined work can be combined legally when compiled, and follows the requirements of the combined work, then where's the issue?
[INDENT]"If you distribute any portion of the software in source code form, you may do so **[SIZE="3"]only[/SIZE]** under this license..."[/INDENT]

Perhaps you have a different interpretation, but that would seem to preclude any offer of dual-licensing on source code.

---

### Post by wildman4god on 2009-04-08
Wow!!!

I really didn't know what I was unleashing by posting this. lol

---

### Post by Methuselah on 2009-04-08
> So a library using a particular language and platform are not open, therefore the language and platform are proprietary? There are many C libraries that are proprietary, therefore C shouldn't be used?

But why use a neutered .NET when we have other turing complete programming languages? C# is not that special.

It amuses me that the Open Source community is running to MS for programming technology and when I was using windows I had to run to gcc and mingw to find a C/C++ compiler that was both standard compliant and wouldn't cost me an arm and a leg.

---

### Post by frankhevans on 2009-04-08
> **2cute4u said:**
> The problem is that they didn't design something decent.  Mono and .Net are major bloatware, that eat system resources unnessesarily.

If you're comparing Mono to C, yeah Mono is fat. But it holds up well to any other stack. For me, its the best balance of performance, stability, and ease of use. I can run java classes in Mono via IKVM. I can run C++ classes via SWIG. These tools border on automagic, which makes Mono a freak'n polyglot Mecca.

That said, I agree, anyone can sue anyone; which is precisely why I don't worry about it.

Here are some numbers.

[http://shootout.alioth.debian.org/u32q/benchmark.php?test=all&lang=csharp&lang2=java&box=1](http://shootout.alioth.debian.org/u32q/benchmark.php?test=all&lang=csharp&lang2=java&box=1)
[http://shootout.alioth.debian.org/u32q/benchmark.php?test=all&lang=csharp&lang2=javaxint&box=1](http://shootout.alioth.debian.org/u32q/benchmark.php?test=all&lang=csharp&lang2=javaxint&box=1)
[http://shootout.alioth.debian.org/u32q/benchmark.php?test=all&lang=csharp&lang2=gpp&box=1](http://shootout.alioth.debian.org/u32q/benchmark.php?test=all&lang=csharp&lang2=gpp&box=1)

---

### Post by Simian Man on 2009-04-08
> **Methuselah said:**
> But why use a neutered .NET when we have other turing complete programming languages? C# is not that special.


First of all don't go down the road to the "Turing Tarpit".  Secondly how is Mono neutered?  It actually does have an implementation of WinForms and it is working on Moonlight.  I can't really think of anything major .Net has that Mono is without, though I'm sure there are some things.

---

### Post by directhex on 2009-04-09
> **Simian Man said:**
> First of all don't go down the road to the "Turing Tarpit".  Secondly how is Mono neutered?  It actually does have an implementation of WinForms and it is working on Moonlight.  I can't really think of anything major .Net has that Mono is without, though I'm sure there are some things.

Only people with no interest in .NET moan about it being "neutered", because it's a stupid point for them to argue for.

e.g. if Mono's WinForms implementation sucks, who cares? Only crap Windows apps use WinForms - and no app developed for Linux uses WinForms.

Mono was designed first and foremost to make the lives of Linux developers easy - who gives a crap about Windows-centric bits when they have GTK#, Cairo#, Tao, and so on?

Only people who are looking for ammo - the BN liar brigade.

---

### Post by Methuselah on 2009-04-10
> **Simian Man said:**
> First of all don't go down the road to the "Turing Tarpit".  Secondly how is Mono neutered?  It actually does have an implementation of WinForms and it is working on Moonlight.  I can't really think of anything major .Net has that Mono is without, though I'm sure there are some things.

I don't know 'Turing Tarpit' you're talking about.
C# is a part-C++ and part-Java chimaera that is designed to compete with both. There is nothing special about it as a programming language.
But, this is besides the point.

You later go on to support my side of the issue.
The completely kosher Mono *should* be neutered.
There should be no WinForms implementation.

IIRC, Winforms is not part of the standard MS offered.
Winforms might very well be Microsoft IP; that would be for a court to decide if the issue came up.
(Last time I checked basic WinForms sucked anyway. 
Who wants to position everything absolutely by hand or in a designer when someone invented layout managers?)

So the Mono developers have to choose between staying within the scraps Microsoft has so generously offered for standardization or striving for full compatibility with the windows reference implementation while risking more uncertain legal standing.
Wonderful! This is the framework we should be writing all open source apps in from now on!

I have no problem with the mono project itself just as I have no problem with Wine.
Giving unix-like OSes the ability to run applications built for either .NET or the windows API is very useful and cool.
However, I would not think it wise for many open source projects primarily intended for native use on 'freenices' to become *dependent* on either of them.
I am getting to the point where I am starting to question the motives of those who vociferously argue for the very opposite.

If widely adopted. Mono becomes an unnecessary dependency on something the community does not fully control. Something partially controlled by a corporation that would certainly rather see the open source community disappear or become irrelevant.

And if one says the above sentence is paranoia I will not be looking up quotes but will refer you to [http://www.google.com](http://www.google.com) and 'Balmer 200 patents'.
Granted, software patents are an almost unavoidable minefield but one should not build his house where weather has exposed them.
One so foolish deserves to have his feet blown off.

---

### Post by Mr. Picklesworth on 2009-04-10
Dropping in quickly (I vowed never to partake in one of these discussions again) to point out another bright side to Mono: It's an opportunity for the open source community to apply "embrace, extend, extinguish" with a Microsoft technology. Mono is a wider-reaching implementation of the technology than Microsoft .Net, now being applied even on portable devices like the iPhone. It is poised to become the leader, simply because it is a more sensible choice if someone wants a cross platform development environment.

Eventually, with love and spreading, Mono could start calling the shots and MS .Net becomes secondary. Maybe some execs in Redmond would start to realize the value of real openness then ;)

Of course, such cut-throat tactics are mean and should be unnecessary, etc. etc...

---

### Post by Methuselah on 2009-04-10
> **Mr. Picklesworth said:**
> Dropping in quickly (I vowed never to partake in one of these discussions again) to point out another bright side to Mono: It's an opportunity for the open source community to apply "embrace, extend, extinguish" with a Microsoft technology. Mono is a wider-reaching implementation of the technology than Microsoft .Net, now being applied even on portable devices like the iPhone. It is poised to become the leader, simply because it is a more sensible choice if someone wants a cross platform development environment.

Eventually, with love and spreading, Mono could start calling the shots and MS .Net becomes secondary. Maybe some execs in Redmond would start to realize the value of real openness then ;)

Interesting take; thanks for breaking your vow.

---

### Post by bigbrovar on 2009-04-10
> **2cute4u said:**
> The problem is that they didn't design something decent.  Mono and .Net are major bloatware, that eat system resources unnessesarily.  Even if both Mono and .NET were GPL 3, and software patents didn't exist; Mono would still suck.

I really miss the thankyou button right now.. you would have gotten one from me. Mono apps suck big time when it comes to memory consumption. Tomboy? i dont use it i prefer ZIM, and f-stop is included in my apt-get remove --purge list of my fresh install setup script i replace it with gthump. Mono imho would still come back to bite us in the A** just like Fart (pun intended)

---

### Post by gnomeuser on 2009-04-10
> **Mr. Picklesworth said:**
> Dropping in quickly (I vowed never to partake in one of these discussions again) to point out another bright side to Mono: It's an opportunity for the open source community to apply "embrace, extend, extinguish" with a Microsoft technology. Mono is a wider-reaching implementation of the technology than Microsoft .Net, now being applied even on portable devices like the iPhone. It is poised to become the leader, simply because it is a more sensible choice if someone wants a cross platform development environment.

Eventually, with love and spreading, Mono could start calling the shots and MS .Net becomes secondary. Maybe some execs in Redmond would start to realize the value of real openness then ;)

Of course, such cut-throat tactics are mean and should be unnecessary, etc. etc...

Mono.SIMD, Mono.Options, Mono.Tasklet as well as support for 64bit arrays.

We are already doing just that already.

just a few references:

[http://tirania.org/blog/archive/2009/Apr-09.html](http://tirania.org/blog/archive/2009/Apr-09.html)
[http://tirania.org/blog/archive/2008/Nov-03.html](http://tirania.org/blog/archive/2008/Nov-03.html)

Now what is still needed is to take this work back to ECMA and have it made a part of the standard. The Mono community has expressed a great interest in polishing SIMD some more then submitting it to be part of the ECMA standard, others should follow.

---

### Post by directhex on 2009-04-10
> **Methuselah said:**
> The completely kosher Mono *should* be neutered.
There should be no WinForms implementation.

IIRC, Winforms is not part of the standard MS offered.
Winforms might very well be Microsoft IP; that would be for a court to decide if the issue came up.
(Last time I checked basic WinForms sucked anyway. 
Who wants to position everything absolutely by hand or in a designer when someone invented layout managers?)

So the Mono developers have to choose between staying within the scraps Microsoft has so generously offered for standardization or striving for full compatibility with the windows reference implementation while risking more uncertain legal standing.
Wonderful! This is the framework we should be writing all open source apps in from now on!

You have both.

Mono on Debian/Ubuntu is highly split, precisely to ensure that WinForms is never installed without reason (and could be eliminated entirely if need be). A default Ubuntu install does not include it. Some people DO want it, though, as an aid to porting apps - just not the desktop team

---

### Post by Danny Dubya on 2009-04-10
> **Only** crap Windows apps use WinForms 
Paint.NET. And it was, at least at one point in time, being ported to Linux.

---

### Post by directhex on 2009-04-10
> **Danny Dubya said:**
> it was, at least at one point in time, being ported to Linux.

As a test of Mono's WinForms implementation

---

### Post by Danny Dubya on 2009-04-10
> **directhex said:**
> As a test of Mono's WinForms implementation
Irrelevant. It's a quality application and many people wanted to, and still want to, use it on Linux, not just the Mono developers as you imply. There are 120+ threads in this forum that mention Paint.NET, the majority of those mentions being positive.

---

### Post by directhex on 2009-04-10
> **Danny Dubya said:**
> Irrelevant. It's a quality application and many people wanted to, and still want to, use it on Linux, not just the Mono developers as you imply. There are 120+ threads in this forum that mention Paint.NET, the majority of those mentions being positive.

It's still a **** toolkit. If the people in those 120+ threads cared, they could help fix up the port so it reaches a sufficient quality to warrant packaging - it's been pretty much abandoned now since the port was being made purely for testing WinForms support - and it's done that already

---

### Post by Danny Dubya on 2009-04-10
EDIT : Forget it, I'm a hypocrite.

---

### Post by Methuselah on 2009-04-10
> 
You have both.

Mono on Debian/Ubuntu is highly split, precisely to ensure that WinForms is never installed without reason (and could be eliminated entirely if need be). A default Ubuntu install does not include it. Some people DO want it, though, as an aid to porting apps - just not the desktop team


You can have both but not in the same installation context.
That's like saying I can have my coffee black or with cream.
Both options exist, but I cannot have them both at once.
Once you put cream, coffee is not black; once you add WinForms Mono is not ...

As I said, I have nothing against the existence of the Mono project.
But for open source projects to become dependent on even partially encumbered proprietary frameworks seems to go against the entire spirit of the community.
And this for no significant gain at all; .NET does not make more hardware devices work or any such magic.

Maybe the aim is to win over windows developers in which case it makes a bit more sense.
Though they use a lot of WinForms and ASP.NET technologies which Microsoft, in its monopolistic wisdom, had held back.

The direction of taking the standard parts and adding open source technology hooks to fill the gaps (like GTK+ for GUIs, SIMD extensions) seems more sensible as a base to build on.
Though Mono, as a development platform, is, IMO, still not filling any real need except maybe an emotional one.

---

### Post by directhex on 2009-04-10
> **Methuselah said:**
> The direction of taking the standard parts and adding open source technology hooks to fill the gaps (like GTK+ for GUIs, SIMD extensions) seems more sensible as a base to build on.

And it's the direction Mono has been taking for 7 years.

> Though Mono, as a development platform, is, IMO, still not filling any real need except maybe an emotional one.

The opposite is true. Every alternative the anti-Mono crowd propose has SERIOUS downsides - if they didn't, there'd never have needed to be a reason to make Mono in the first place. It's much smaller than Java (in terms of RAM use and disk use), as well as MUCH MUCH better for things like interop with system libraries. It's orders of magniture (i.e. up to about a hundred times) faster than Python. It's MUCH easier (and therefore faster) for development than C++, since you don't need to worry about manual memory management. Vala's probably the best-set alternative, but is a poor coursin with many many missing features (and features which are simply impossible to fill without the JIT engine backing it). It's the "anything but Mono" crowd which is emotive.

---

### Post by Methuselah on 2009-04-10
Well, I guess everything has been said; we'll see how things play out.

BTW, I'm not sure which application niche needs to be faster than python but slower than C++.
And Python + Glade Designer = Development cake.

---

### Post by directhex on 2009-04-10
> **Methuselah said:**
> BTW, I'm not sure which application niche needs to be faster than python but slower than C++.

Evolution.

Mono exists because Evolution sucks - a huge, bloated monster written in pure C. Imagine writing an app the size of Evolution in Python, given the speed required of dealing with multi-thousand-message inboxes. Imagine dealing with memory management for it manually.

That's the niche, that's why Mono was created. Because Evolution sucks.

---

### Post by bakedbeans4life on 2009-04-10
> **directhex said:**
> Evolution.

Mono exists because Evolution sucks - a huge, bloated monster written in pure C. Imagine writing an app the size of Evolution in Python, given the speed required of dealing with multi-thousand-message inboxes. Imagine dealing with memory management for it manually.

That's the niche, that's why Mono was created. Because Evolution sucks.

So you like the way Microsoft do things. The Linux community, both voluntarily and commercial, have it all wrong. Is your first name Miguel by any chance?

---

### Post by directhex on 2009-04-10
> **bakedbeans4life said:**
> So you like the way Microsoft do things. The Linux community, both voluntarily and commercial, have it all wrong. Is your first name Miguel by any chance?

You're not very bright, it seems

Where did I mention Microsoft?

---

### Post by Giant Speck on 2009-04-10
> **bakedbeans4life said:**
> So you like the way Microsoft do things. The Linux community, both voluntarily and commercial, have it all wrong. Is your first name Miguel by any chance?

1.) He never specifically mentioned Microsoft.
2.) He never specifically mentioned the Linux community.
3.) Who cares if someone likes the way Microsoft does things anyway?

---

### Post by handy on 2009-04-11
Who's Linux?

---

### Post by Twitch6000 on 2009-04-11
> **bakedbeans4life said:**
> So you like the way Microsoft do things. The Linux community, both voluntarily and commercial, have it all wrong. Is your first name Miguel by any chance?

Where did he mention Microsoft or Linux in his post?

He is just stating his honest opinion which in some cases is the truth.

If you have a problem with his thoughts why not argue with some facts instead of being a fanboy...

---

### Post by SKLP on 2009-04-11
Mono is an awesome platform technically, and one of the great things about it is it's good support for multiple languages (including dynamic lanugages with the coming soon dynamic keyword in C# and the DLR). In theory, if all the desktop libraries (for instance Gtk) were primarily made available as either a a) static mono assembly, or in a dynamic language running on mono( ironpython, ironruby etc), then those libraries would be available from all mono static and dynamic libraries in a seamless fashion ( without the need for creating and updating a lot of bindings etc).
So if one person likes C# and does a library for, say, accessing iPods, that would be available to at least C#, Boo, VB.Net, IronPython, IronRuby, and many more. Same thing if someone made a library in IronPython, where it would be available to all dynamic languages, and also from all the static languages ( as long as they have added IDynamicObject integration, like C# 4.0 does with the dynamic keyword)
No other plafrom that I'm aware of offers this kind of multi-language integration, which is one of the things that seems so great about it.

Other good features are obviously that it's a lot faster than python or similiar languages, and better than C/C++ for many things...

About the MS-PL license, well I guess it's not perfect... but as long as a license is free software, and it does not impose any restrictions on dynamically linking with it, I'd consider it a good license.
GPL is the bad guy here, just imagine if there were *two* very similair licenses, the GPL, and some other one. If they happened to be non-compatible with each other due to some tiny difference, and both were very popular licenses, it would be very bad for the open source world.
That's the reason I much prefer licenses which does not restrict linking in the way the GPL does it (be it LGPL, MS-PL, Apache license, BSD, MIT or whatever).
Although more free == good in my opinion, So I still prefer MIT over say LGPL.

---

### Post by Tibuda on 2009-04-11
> **SKLP said:**
> About the MS-PL license, well I guess it's not perfect... but as long as a license is free software, and it does not impose any restrictions on dynamically linking with it, I'd consider it a good license.
GPL is the bad guy here, just imagine if there were *two* very similair licenses, the GPL, and some other one. If they happened to be non-compatible with each other due to some tiny difference, and both were very popular licenses, it would be very bad for the open source world.
That's the reason I much prefer licenses which does not restrict linking in the way the GPL does it (be it LGPL, MS-PL, Apache license, BSD, MIT or whatever).
Although more free == good in my opinion, So I still prefer MIT over say LGPL.

But Mono is not under MS-PL license, but [GPL, LGPL and MIT X11]("http://mono-project.com/License").

---

### Post by saulgoode on 2009-04-11
> **SKLP said:**
> No other plafrom that I'm aware of offers this kind of multi-language integration, which is one of the things that seems so great about it.

Well, there's [this one]("http://en.wikipedia.org/wiki/Executable_and_Linkable_Format"). ;)

> **SKLP said:**
> GPL is the bad guy here, just imagine if there were *two* very similair licenses, the GPL, and some other one. If they happened to be non-compatible with each other due to some tiny difference, and both were very popular licenses, it would be very bad for the open source world.
The GPL demands that free software always remain free. The university licenses permit software to be free AND permit (but not demand) requiring that the software will always remain free. The MS-PL permits software to be free BUT removes the right to guarantee the software will always remain free.

So you think the "GPL is the bad guy" because it requires that the software always and forever will remain free -- that it is worse "for the open source world" than the MS-PL, a license which *requires* that the software always and forever will be allowed to become non-free? 

I can understand (but do not agree with) the argument that denying the right to derive non-free software is in some ways a restriction on that software's freedom; but the idea that restricting that right of denial would somehow be even more free is ludicrous.

> **SKLP said:**
> Although more free == good in my opinion, So I still prefer MIT over say LGPL.
I certainly agree that more free == good, but I suspect I use a different definition for "freedom" than you. Rather than the anarchical, anything-goes "freedom" which you seem to adopt, I prefer to embrace the concept as put forth in the *[Declaration of the Rights of Man and of the Citizen]("http://www.hrcr.org/docs/frenchdec.html")* wherein:

[INDENT]*Liberty consists in the freedom to do everything which injures no one else; hence the exercise of **the natural rights of each man has no limits except those which assure to the other members of the society the enjoyment of the same rights**. These limits can only be determined by law.*[/INDENT]

The GNU General Public License embraces THAT definition of freedom: lawful limits are placed upon rights *only* to assure that others enjoy those same rights.

But regardless of whether you believe in anarchical freedom or lawful freedom, the limits prescribed by the "Microsoft Public License" do not foster freedom.

---

### Post by Methuselah on 2009-04-11
> **directhex said:**
> Evolution.

Mono exists because Evolution sucks - a huge, bloated monster written in pure C. Imagine writing an app the size of Evolution in Python, given the speed required of dealing with multi-thousand-message inboxes. Imagine dealing with memory management for it manually.

That's the niche, that's why Mono was created. Because Evolution sucks.

Ah, I certainly don't know enough about evolution to argue with that.

Although I can't help but feel that a movement away from certain principles creates some needs that didn't exist before.
I could certainly imagine the speed critical portions of evolution written in C/C++ with a front-end constructed in Python/Glade.

But I'm willing to concede that it might be easier to write evolution as a monolithic application in C#/Mono than in C and it would run faster than a Python implementation.

---

### Post by Methuselah on 2009-04-11
> 
The GNU General Public License embraces THAT definition of freedom: lawful limits are placed upon rights only to assure that others enjoy those same rights.


Well said. 
The restrictions of the GPL just prevent free software from becoming proprietary.
Once free, always free.

It's hard to imagine the linux kernel would as as full featured and free as it is today if it were not published under the GPL.
The Wine project started out with anarchic freedom but their experience with WineX/Cedega highlighted the usefulness of the LGPL.
If it's one's intention to do free work for for-profit corporations in a way that allows them to claim ownership of your work then the GPL licenses can be ignored.

---

### Post by SKLP on 2009-04-11
Obviously, there are merits to both GPL and BSD-style licenses, however I prefer MIT/BSD-style. Mainly because a) It will not hurt me if someone uses my software in any way whatsoever, including linking with a proprietary application 
b) It is very impractical to have two or more licenses that restrict linking like the GPL does. Meaning that if they were not the same license, or VERY similiar, they wouldn't be compatible. So if one library was under the GPL and the app that wanted to use the library was under the other license, it would not be legal to link them. Even though both are "free software". 

I'm happy to use GPL applications (but I consider GPL libraries harmful)...

Regarding using the ELF instead of Mono, that's just silly as it does not offer any of the features I listed...

---

### Post by SKLP on 2009-04-11
> **danielrmt said:**
> But Mono is not under MS-PL license, but [GPL, LGPL and MIT X11]("http://mono-project.com/License").
True. However they were talking about the Ms-PL earlier in this thread. 

However DLR is probably going to be included in Mono and that's MS-PL.
IronPython and IronRuby are MS-PL. ASP.NET MVC is MS-PL. The controls in moonlight 2 are Ms-PL.

---

### Post by SKLP on 2009-04-11
> **saulgoode said:**
> 
The GNU General Public License embraces THAT definition of freedom: lawful limits are placed upon rights *only* to assure that others enjoy those same rights.
I would not confuse essential civil liberties with the license of a piece of software... But whatever... "Liberty consists in the freedom to do everything which injures no one else"
It does not hurt anyone if someone uses my software in ANY way( including linking with a proprietary application)

[QUOTE=saulgoode]
But regardless of whether you believe in anarchical freedom or lawful freedom, the limits prescribed by the "Microsoft Public License" do not foster freedom.[/QUOTE]
I'm not an MS-PL advocate, I'm just stating my opinion that the GPL is bad because it restricts linking. I have no problem using software under either license, and I'm happy to disagree with you on this (or any) issue.

Btw sorry for multi posting

---

### Post by saulgoode on 2009-04-12
> **SKLP said:**
> It does not hurt anyone if someone uses my software in ANY way( including linking with a proprietary application)
So you think the GPL is bad because no matter how people use that software, nobody is hurt? Would you not then also apply that to proprietary-licensed software? People can install a single copy of Windows on more than one machine, share it with friends, post it as a free download; and nobody is hurt, not even Microsoft? 

> **SKLP said:**
> I'm not an MS-PL advocate, I'm just stating my opinion that the GPL is bad because it restricts linking.
Yet the MS-PL restricts linking with LGPL libraries *if you share your source code* (but permits it if you only share compiled versions of your code). Does that mean you consider the MS-PL to be "less bad"? To me, that makes it very much worse.

> **SKLP said:**
> I have no problem using software under either license, and I'm happy to disagree with you on this (or any) issue.
I've appreciated our conversation, though we may disagree. Regards.

---

### Post by SKLP on 2009-04-12
> **saulgoode said:**
> So you think the GPL is bad because no matter how people use that software, nobody is hurt? Would you not then also apply that to proprietary-licensed software? People can install a single copy of Windows on more than one machine, share it with friends, post it as a free download; and nobody is hurt, not even Microsoft? 
Good point. Microsoft could be considered to be hurt by that though, because they expected to get paid for every copy of the software when they invested money in developing it. However it would only hurt them indirectly, not directly. If I made available software under MIT and someone included it in a proprietary application, it would not hurt me since I didn't expect anything in particular (money or otherwise) when I released the software.
[QUOTE=saulgoode]Yet the MS-PL restricts linking with LGPL libraries *if you share your source code* (but permits it if you only share compiled versions of your code). Does that mean you consider the MS-PL to be "less bad"? To me, that makes it very much worse.
 [/QUOTE]I'm not a legal expert, but in my mind "If you distribute any portion of the software in source code form, you may do so only under this license by including a complete copy of this license with your distribution." does not mean it restricts linking. It does not state anything about derivative works or similiar (which the GPL does, IIRC). What is the problem with having different files under different free licenses in a certain project?

---

### Post by saulgoode on 2009-04-12
> **SKLP said:**
> I'm not a legal expert, but in my mind "If you distribute any portion of the software in source code form, you may do so only under this license by including a complete copy of this license with your distribution." does not mean it restricts linking. It does not state anything about derivative works or similiar (which the GPL does, IIRC).
[INDENT]Consider the following (note that this is NOT legal analysis, advice, or even opinion; it is a *hypothesis*):[/INDENT]

That dynamic linking of software to GPLed code can be restricted under copyright law is premised on the idea that the software being linked would be considered a derived work of the code (regardless of whether it is "bundled" with the GPLed code). There has been no absolute edict that this is true, but there is a preponderance of analysis by all sides that seems to at least accept this as a worthy argument. (You yourself gave indication of such a sentiment: "*I much prefer licenses which does not restrict linking in the way the GPL does it*".)

To simplify the discussion, allow me to present the hypothesis while calling the LGPLed code being linked to, "my code", and the software linking to it, "your software" (your software to be released under a license of your choosing). If your software can be legally linked to my code should my code be LGPLed -- but not if my code were released under the GPL -- this would indicate that your software should be considered (under copyright law) to be a derived work of my code. Indeed the major distinction between the LGPL and the GPL is this allowance for dynamic linking. 

So if you choose to release your software under the MS-PL -- but NOT share the source code to your software -- it would fall under the second sentence of section 3D) in the MS-PL ("...you may only do so **under a license that complies with this license**"). Ignoring the rather nonsensical concept that one license "complies with" another -- *actions* comply with a license, not other licenses -- let's assume that by this Microsoft intends that your *usage* of my LGPL code be compliant with the MS-PL. From the standpoint of the LGPL, there is no problem with your doing this; the LGPL permits you to link to my code without you having to release the source for your software. But take note, nothing has been said about whether or not your software is a derivation of my code -- the assumption should remain that it is (given the argument posited in my first paragraph). 

Now let's alter this such that you choose to release your software under the MS-PL, but choose to share the source code as well. Nothing changes on my end; the LGPL still permits your software to link to my code. HOWEVER, from the standpoint of the MS-PL your software now falls under the terms you cited in the *first* sentence of section 3D), "you may do so only **under this license**". Since the presumption that your software is a derivative work based upon my code is still valid, my code would be required (by the MS-PL terms) to be released under the MS-PL. I am unable to find anything in the LGPL which would permit you to change the license of my code to the MS-PL. Should it be considered a failing of the LGPL that it does not permit changing the license? Or would it be more in keeping with your criticism of the GPL to blame the MS-PL for demanding a license change? 

> **SKLP said:**
> What is the problem with having different files under different free licenses in a certain project?

I won't draw any conclusions from the preceding hypothesis (these forums have a rather esoteric policy regarding opinions of legalities), but ask that you consider for yourself the ramifications of Mono incorporating MS-PLed software into their project (such as the aforementioned DLR) given the LGPLv2 licensing of the Mono runtime.

---

### Post by directhex on 2009-04-12
> **saulgoode said:**
> I won't draw any conclusions from the preceding hypothesis (these forums have a rather esoteric policy regarding opinions of legalities), but ask that you consider for yourself the ramifications of Mono incorporating MS-PLed software into their project (such as the aforementioned DLR) given the LGPLv2 licensing of the Mono runtime.

runtime != classlib

---

### Post by bakedbeans4life on 2009-04-12
It would seem as if I'm on a short leash here, whatever.

Don't amuse yourself by contemplating what you think Microsoft can, and can not do. Do not find comfort in that mindset either.

Microsoft know their enemy, that enemy is Linux. You know, that OS with the penguin mascot, you may remember it from time to time.

Small hitch is I'm speaking to a Linux forum that worships all things Microsoft more than any Microsoft forum does.

---

### Post by SKLP on 2009-04-13
> **saulgoode said:**
>  Indeed the major distinction between the LGPL and the GPL is this allowance for dynamic linking.  Indeed this is why I stated I dislike the GPL.

Consider this:

Let's say I have created an MSPL-licensed application that uses the win32 api (which is available only under Windows EULA or something).
I'm AFAIK still allowed to distribute either the source or the binary (of my application), even though one might consider my application to then be a derivative work of the win32 libraries.
Same thing should apply if my application are using system libraries in GNU/Linux that, say, are licensed under the LGPL.

If the system libraries were released under the GPL, in my limited understanding of all of this, on the other hand, my software would still be possible to release, but if someone downloaded it and executed it, it would be linked to the GPL library in memory (which would afaik, be illegal unless my software was released under a GPL-compatible license)
This is what I consider bad about it (the GPL), but in my understanding of things (which may of course be wrong), an MS-PL application can be dynamically linked to a library released under ANY license.[unless the license of that library restricts dynamic linking like the GPL]

Correct me if I'm wrong :-)

---

### Post by SKLP on 2009-04-13
> **directhex said:**
> runtime != classlib

"The release for the DLR is done under the terms of the Microsoft Permissive License (MsPL) which is by all means an open source license. This means that we can use and distribute the DLR as part of Mono without having to build it from scratch. A brilliant move by Microsoft. "[0] - Miguel de Icaza

[0: [http://tirania.org/blog/archive/2007/May-01.html]](http://tirania.org/blog/archive/2007/May-01.html])

---

### Post by directhex on 2009-04-13
> **SKLP said:**
> "The release for the DLR is done under the terms of the Microsoft Permissive License (MsPL) which is by all means an open source license. This means that we can use and distribute the DLR as part of Mono without having to build it from scratch. A brilliant move by Microsoft. "[0] - Miguel de Icaza

[0: [http://tirania.org/blog/archive/2007/May-01.html]](http://tirania.org/blog/archive/2007/May-01.html])

So what?

runtime still != classlib. The DLR is a set of libs

---

### Post by SKLP on 2009-04-13
> **directhex said:**
> So what?

runtime still != classlib. The DLR is a set of libsLet me clarify: I'm not disagreeing with you

---

### Post by saulgoode on 2009-04-13
> **SKLP said:**
> Consider this:

Let's say I have created an MSPL-licensed application that uses the win32 api (which is available only under Windows EULA or something).
I'm AFAIK still allowed to distribute either the source or the binary (of my application), even though one might consider my application to then be a derivative work of the win32 libraries.
If the one doing the considering is a presiding judge ruling on whether your distribution complies with the license, you might need to look further for you knowledge. What you may want the license to say is not going to be what the courts base their decision upon.

> **SKLP said:**
> If the system libraries were released under the GPL, in my limited understanding of all of this, on the other hand, my software would still be possible to release, but if someone downloaded it and executed it, it would be linked to the GPL library in memory (which would afaik, be illegal unless my software was released under a GPL-compatible license)
My grammatical interpretation of what the GNU licenses state about this is  that your source code, distributed in isolation from the (L)GPL code and merely including links to that code (i.e., you didn't copy any functional code), would not be considered a derivative work (see Section 5 of the [LGPLv2.1]("http://www.gnu.org/licenses/old-licenses/lgpl-2.1.html")). However, *compiled* versions of your program, which would be linked to the (L)GPL code, would be considered derivative.

> **SKLP said:**
> This is what I consider bad about it (the GPL), but in my understanding of things (which may of course be wrong), an MS-PL application can be dynamically linked to a library released under ANY license.[unless the license of that library restricts dynamic linking like the GPL]
I would question how you came to your understanding of the MS-PL. Did you use the actual wording of the license in drawing a conclusion? Or are you basing it on someone else's opinion?

> **SKLP said:**
> Correct me if I'm wrong :-)
You are obviously a thoughtful person and, given the problematic policies of this forum with regard to voicing opinions on such things, I shall leave you to consider on your own the various interpretations available (perhaps consider whether incorporating BSD-licensed code into an MS-PL project is permitted, should the BSD author have included patented code without providing a grant for the patents ;) ). 

I would correct you on your continued characterization of the GPL as "bad". The GPL only *grants* rights to recipients of the software; it does not take away any rights. Many of these rights are granted unilaterally with no obligation whatsoever, though some are granted only conditionally. To claim that this is "bad" is like calling someone who gives food to half the population "bad" for not providing more.

---

### Post by SKLP on 2009-04-13
> **saulgoode said:**
> My grammatical interpretation of what the GNU licenses state about this is  that your source code, distributed in isolation from the (L)GPL code and merely including links to that code (i.e., you didn't copy any functional code), would not be considered a derivative work (see Section 5 of the [LGPLv2.1]("http://www.gnu.org/licenses/old-licenses/lgpl-2.1.html")). However, *compiled* versions of your program, which would be linked to the (L)GPL code, would be considered derivative. Yes, you are probably right. Still, what I dislike about the GPL remains the same, namely that it still restricts my released binary from merely dynamically linking (referencing) to the GPL code/API, if it's not under a "GPL-compatible" license.
> I would question how you came to your understanding of the MS-PL. Did you use the actual wording of the license in drawing a conclusion? Or are you basing it on someone else's opinion?```
If you distribute any portion of the software in source code form, you may do so only under this license by including a complete copy of this license with your distribution. If you distribute any portion of the software in compiled or object code form, you may only do so under a license that complies with this license.
```In my mind, this text does not imply that any libraries which are referenced must be under the same license.
> You are obviously a thoughtful person and, given the problematic policies of this forum with regard to voicing opinions on such things, I shall leave you to consider on your own the various interpretations available (perhaps consider whether incorporating BSD-licensed code into an MS-PL project is permitted, should the BSD author have included patented code without providing a grant for the patents ;) ). 
I would think that the patent stuff is pretty similiar to Apache license? Anyways, I thank you for this interesting discussion, but I will now draw my own conclusions as you say.
> 
I would correct you on your continued characterization of the GPL as "bad". The GPL only *grants* rights to recipients of the software; it does not take away any rights. Many of these rights are granted unilaterally with no obligation whatsoever, though some are granted only conditionally. To claim that this is "bad" is like calling someone who gives food to half the population "bad" for not providing more.Well, I happen to disagree with you and I will continue to prefer to use the BSD/MIT style licenses. I would not generally consider the GPL bad, however I happen to like it less than more permissive licenses.

---

### Post by bp1509 on 2009-04-13
d

---

### Post by So Tough on 2009-04-13
> **danielrmt said:**
> Mono follows an ECMA standard if I'm not wrong. There are more stuff they can sue Linux for, like FAT/NTFS support, Wine and double-click.


Is WINE an actual part of Linux though, i understood it to be an independent piece of software?

:confused:

---

### Post by Tibuda on 2009-04-13
> **So Tough said:**
> Is WINE an actual part of Linux though, i understood it to be an independent piece of software?Mono is independent too, unless [this get finished]("http://www.tuxradar.com/content/ubuntu-rewrite-linux-kernel-using-mono").

---

### Post by directhex on 2009-04-13
> **bp1509 said:**
> Lol.  So projects being written in mono are proof it doesn't suck? Zim, keepnote, and now gnote (tomboy ported to C#), all do the exact same crap as tomboy with a fraction of the resources.  Being wasteful for the sake of being wasteful with system resources is sloppy, lazy, and saying "i don't give a flip" about your userbase.

Ignoring the legal issues that surround it, GNote is nowhere near as functional as Tomboy yet - it doesn't support WikiWords, has no documentation, no syncing to anywhere, and no integration with any other apps. Its RAM consumption IS better (9.8M versus 23.4M out of the box), as long as you don't mind the lack of functionality.

> And as for F-spot.. it's really not that great of an app.  At all.  And what exactly does banshee do that just about all of the linux highend audio management apps don't?

Banshee? Believe it or not (I think it's clear you'll vote "not"), it's the most lightweight media library app for GNOME with an active development community - Rhythmbox is pretty much dead-end, the Python apps are all far more bloated (Songbird is even worse), so what do you suggest? Rhythmbox is as good as it will ever be, whilst other apps are always improving - and Banshee is the most lightweight of the bunch. See [http://ubuntuforums.org/showpost.php?p=6376519&postcount=35](http://ubuntuforums.org/showpost.php?p=6376519&postcount=35) for recorded numbers.

---

### Post by gnomeuser on 2009-04-13
> **directhex said:**
> Ignoring the legal issues that surround it, GNote is nowhere near as functional as Tomboy yet - it doesn't support WikiWords, has no documentation, no syncing to anywhere, and no integration with any other apps. Its RAM consumption IS better (9.8M versus 23.4M out of the box), as long as you don't mind the lack of functionality.


Aside that, being as new as it there is no track record of stability or security. There is also nothing to show that the development in terms of new features and the focus will be at the same pace as Tomboy. 

I always wondered about one thing though, people who say that "foo could just as easily have been implemented in bar instead of Mono", yet they fail to realise that this is very rarely the case. Mono grants developers tools to focus on innovation, before Mono there was no gnome-do nor a Tomboy just to mention a few. This is totally being ignored, yes you can reimplement something is C and it will possibly be more effective and lighter on ressources but the original program wouldn't be there without Mono. It remains a reimplentation and the innovation happens elsewhere. By actively working against Mono for this reason one directly undercuts innovation without providing a feasable alternative.

Mono allows us to write good programs that do interesting things, it allows us to do it quickly and with fewer errors as well as improved base security.

---

### Post by saulgoode on 2009-04-13
> **SKLP said:**
> I would think that the patent stuff is pretty similiar to Apache license?
The current version of the Apache license includes a patent licensing requirement. My interest lies in whether or not a license that does not offer a patent grant -- such as the BSD license -- would "comply with" a license which requires that such patent grants are provided. 

> **SKLP said:**
> Anyways, I thank you for this interesting discussion, but I will now draw my own conclusions as you say.
Likewise.

---

### Post by Mokoma on 2009-04-13
isnt moonlight by novell??

arent they in partnership with microsoft??

so how could they sue??

---

### Post by oomingmak on 2009-04-14
> **danielrmt said:**
> There are more stuff they can sue Linux for, like .... **double-click.**
Indeed.

Although personally I'd love it if Microsoft sued Linux for breaching their double-click patents, because I absolutely *hate *double-clicking and I would be so happy to see it got rid of.

\\:D/

---

### Post by handy on 2009-04-29
I always find it amusing that MS has the ability to peruse FOSS, yet no one can peruse more than a tiny bit of MS's software.

I expect that MS will never release most of their code as OSS, due to the amount of it that has very likely been based on stolen code.

---

