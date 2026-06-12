---
title: "Someone help me...my friend needs solid proof Mac isn't open-source"
date: 2009-10-11
forum: The Cafe
---

### Post by myk02k on 2009-10-11
So my argumentative friend is trying to prove to me that Mac is open-source.  He keeps pointing to several articles like an OS called "Darwin" to try to prove his point.  For someone that knows Mac and its software, could somebody help me give him some solid reasoning?  He's a Devry graduate and refuses any logic that I spoke to him thus far.

---

### Post by RiceMonster on 2009-10-11
A large number of OSX components ARE open source. WebKit, HFS, XNU, grand central dispatch, CUPS, etc.

---

### Post by TheNessus on 2009-10-11
hurdle him to the nearest apple store and let him ask if he can acquire OS X for free.

---

### Post by RiceMonster on 2009-10-11
> **TheNessus said:**
> hurdle him to the nearest apple store and let him ask if he can acquire OS X for free.

Price has nothing to do with being open source. Go and see if you can get RHEL for free.

---

### Post by Bachstelze on 2009-10-11
> **myk02k said:**
> So my argumentative friend is trying to prove to me that Mac is open-source.  He keeps pointing to several articles like an OS called "Darwin" to try to prove his point.  For someone that knows Mac and its software, could somebody help me give him some solid reasoning?  He's a Devry graduate and refuses any logic that I spoke to him thus far.

Darwin is the base upon which Mac OS is build.

[http://en.wikipedia.org/wiki/Darwin_%28operating_system%29](http://en.wikipedia.org/wiki/Darwin_%28operating_system%29)

If you type [font="monospace"]uname[/font] in your OS X terminal, it will return [font="monospace"]Darwin[/font].

---

### Post by myk02k on 2009-10-11
his latest reply

The OS thats open source Darwin is Mac, look it up its not a program for MAC OS X, its what MAC created for OPEN SOURCE developers if you would like a version of a MAC OS X

see [http://developer.apple.com/Darwin/](http://developer.apple.com/Darwin/)
& [http://lists.apple.com/mailman/listinfo/darwin-dev](http://lists.apple.com/mailman/listinfo/darwin-dev)

---

### Post by tc3000 on 2009-10-11
It's both: the kernel is open, but the GUI and most of the stuff on the top is closed.

---

### Post by -grubby on 2009-10-11
[http://ubuntuforums.org/showpost.php?p=7347446&postcount=1](http://ubuntuforums.org/showpost.php?p=7347446&postcount=1)

See: "CS: Mac OS X is closed source"

---

### Post by fela on 2009-10-11
It's a proprietary operating system that has lots of open source components; however what actually makes the operating system unique is all closed source - such as its GUI toolkit, compositor, desktop environment, and that's about it. All the stuff under that is open source IIRC. But alot of that is also in alot of Linux distributions, such as CUPS, sudo, vim, and alot of other GNU utilities included in OSX.

About Darwin - it's the 'base' operating system of OSX, upon which the rest of OSX (the bit you use directly as opposed to indirectly) is based. Darwin isn't just a kernel (as I've heard alot of people say), you can use Darwin on its own if you want (Apple even let you download the source code from their website), and it compiles for x86 as well as PPC architectures (of course).

---

### Post by myk02k on 2009-10-11
> **RiceMonster said:**
> Price has nothing to do with being open source. Go and see if you can get RHEL for free.

Granted, another argument I'm making is that Linux software is mostly copyrighted under the General Public License, which allows free distribution and modification of its software.

---

### Post by Bachstelze on 2009-10-11
> **myk02k said:**
> Granted, another argument I'm making is that Linux software is mostly copyrighted under the General Public License, which allows free distribution and modification of its software.

/facepalm

You were told the truth: some parts of Mac OS X are open source, some aren't. No need to argue anymore...

---

### Post by Bachstelze on 2009-10-11
> **fela said:**
> IAll the stuff under that is open source IIRC. But alot of that is also in alot of Linux distributions, such as CUPS, sudo, vim, and alot of other GNU utilities included in OSX.

Neither CUPS, nor sudo, nor vim are "GNU utilities".

---

### Post by schauerlich on 2009-10-11
See the link in my sig. It explains what parts of Mac OS X are and aren't open source.

---

### Post by RichardLinx on 2009-10-11
Mac OSX can't be considered opensource if it's under a proprietry license like the EULA. 

> Granted, another argument I'm making is that Linux software is mostly copyrighted under the General Public License
"copyrighted" some how doesn't seem like the correct terminology for this.

---

### Post by schauerlich on 2009-10-11
> **RichardLinx said:**
> Mac OSX **as a whole** can't be considered **free software** if it's **distributed** under a proprietary license like the EULA.

Fixed that for you.

---

### Post by Bachstelze on 2009-10-11
> **RichardLinx said:**
> 
"copyrighted" some how doesn't seem like the correct terminology for this.

Too bad, because it is.

---

### Post by myk02k on 2009-10-11
> **RichardLinx said:**
> Mac OSX can't be considered opensource if it's under a proprietry license like the EULA. 


"copyrighted" some how doesn't seem like the correct terminology for this.

Agreed.  Copylefted?  lol

---

### Post by j.bell730 on 2009-10-11
> **myk02k said:**
> Agreed.  Copylefted?  lol

No, copylefted is what GNU/Linux is considered.

---

### Post by RichardLinx on 2009-10-11
> **Bachstelze said:**
> Too bad, because it is.

> another argument I'm making is that Linux software is mostly copyrighted under the General Public License

As opposed to:
> another argument I'm making is that Linux software is mostly ***provided*** under the General Public License

Just saying, it doesn't sound "right" to me. But I guess it is.

> Fixed that for you.
Cheers. :)

---

### Post by Mateo on 2009-10-11
So basically you're asking us to help you prove a negative?

---

### Post by sertse on 2009-10-11
We can't help you unless you can accept not all things are black or white.

EDavidBurg's thread is one of the most well researched and documented thread about Apple/Mac and it's interaction with FLOSS. Read it, it's even documents all it's evidence if you don't trust it. 

Reality is that some parts of its practices are FLOSS.

---

### Post by fela on 2009-10-11
> **Bachstelze said:**
> Neither CUPS, nor sudo, nor vim are "GNU utilities".

I guess I should have said 'other, often GNU, utilities' - I never meant to imply that those were made by GNU. CUPS is actually made by Apple mainly!

---

### Post by fela on 2009-10-11
> **Bachstelze said:**
> Too bad, because it is.

Why's that bad? It's copyright, just not in the general sense :) It's sort of the opposite I guess, because it **forces** you to let other people modify your work, rather than **prevent** that happening.

---

### Post by hoppipolla on 2009-10-11
> **sertse said:**
> We can't help you unless you can't accept all things are black or white.

EDavidBurg's thread is one of the most well researched and documented thread about Apple/Mac and it's interaction with FLOSS. Read it, it's even documents all it's evidence if you don't trust it. 

Reality is that some parts of it's practice are FLOSS.

These guys said it better than I ever could :)

Assuming of course that they are correct, which it seems like they are :)

---

### Post by fela on 2009-10-11
> **sertse said:**
> We can't help you unless you can't accept all things are black or white.

EDavidBurg's thread is one of the most well researched and documented thread about Apple/Mac and it's interaction with FLOSS. Read it, it's even documents all it's evidence if you don't trust it. 

Reality is that some parts of it's practice are FLOSS.

FLOSS??? Don't you mean FOSS? Sorry, I'm pedantic :P

---

### Post by Bachstelze on 2009-10-11
> **fela said:**
> FLOSS??? Don't you mean FOSS? Sorry, I'm pedantic :P

[http://en.wikipedia.org/wiki/FLOSS](http://en.wikipedia.org/wiki/FLOSS)

> Free and open-source software, also F/OSS, FOSS, or **FLOSS (free/libre/open source software)** is software that is liberally licensed to grant the right of users to study, change, and improve its design through the availability of its source code.

---

### Post by Mateo on 2009-10-11
x

---

### Post by hoppipolla on 2009-10-11
> **fela said:**
> FLOSS??? Don't you mean FOSS? Sorry, I'm pedantic :P

[http://en.wikipedia.org/wiki/Dental_floss](http://en.wikipedia.org/wiki/Dental_floss) :D

---

### Post by Frak on 2009-10-11
Stack Mac OS X from bottom to top, where the bottom is underlying system components causing the system to operate, and then stack on top of that all of the proprietary Human Interface objects. You'll be able to draw a line through the middle, where nearly everything below the line is open source and everything above the line is proprietary. Even Apple's killer Grand Central Dispatch is open source.

It's hard to prove something that isn't true. Hell, it's hard to prove anything at all.

---

### Post by Dimitriid on 2009-10-11
Tell your friend to contact apple and request the source code for the aforementioned parts that aren't open source.

---

### Post by Frak on 2009-10-11
> **Dimitriid said:**
> Tell your friend to contact apple and request the source code for the aforementioned parts that aren't open source.
But if they ever offer the Open Source components, please ignore them.

---

### Post by Bachstelze on 2009-10-11
> **Frak said:**
> 
Hell, it's hard to prove anything at all.

[img]http://imgs.xkcd.com/comics/certainty.png[/img]

---

### Post by Exodist on 2009-10-11
Behold the power of Google!

[http://www.apple.com/legal/sla/]("http://www.apple.com/legal/sla/")

---

### Post by earthpigg on 2009-10-11
OS X is non-free software.

Darwin is free software.

arguments about bits and pieces of this and that are silly - 'parts' of North Korea are free and democratic, you know....


....yeah, exactly.

also, if your friend insists that Darwin = OS X, then ask him kindly to install iTunes or iWhatever on Darwin and prove it.

---

### Post by Bachstelze on 2009-10-11
> **earthpigg said:**
> OS X is non-free software.

Darwin is free software.

arguments about bits and pieces of this and that are silly

And how are they silly? OS X is not just one huge blob, it's made of several pieces, just like Ubuntu. And just like Ubuntu, all its pieces are not licensed under the same terms.

---

### Post by hanzomon4 on 2009-10-11
OSX as in the total package is non-free, however major parts of it are made up of foss bits. It's both, you can't have OSX with out foss nor could you have OSX with out the closed parts.

---

### Post by hoppipolla on 2009-10-11
> **Dimitriid said:**
> Tell your friend to contact apple and request the source code for the aforementioned parts that aren't open source.

Well said :)

---

### Post by hoppipolla on 2009-10-11
> **earthpigg said:**
> also, if your friend insists that Darwin = OS X, then ask him kindly to install iTunes or iWhatever on Darwin and prove it.

xD Also well said!

---

### Post by Frak on 2009-10-11
> **hoppipolla said:**
> Well said :)

> **hoppipolla said:**
> xD Also well said!

-1

Both of those quotes lack ground. It's like saying XChat is closed source because their Windows port is proprietary. As for the iTunes one, there's a reason why we can't just drop in binaries and expect them to work. They have dependencies on other libraries. Some of those libraries are proprietary to Apple, just as libraries are proprietary to Microsoft. Hell, even RedHat and Suse have their own proprietary libraries to certain products, it's just how the cookie crumbles in real life.

Look, Apple does maintain some Open Source components, but they want to keep some things to themselves. Leave it to that. It's what makes Apple Apple, and not Apple, the originator of source X and lead to products Y and Z from company B.

---

### Post by fela on 2009-10-11
> **hoppipolla said:**
> xD Also well said!

And THAT is well said :)

---

### Post by hoppipolla on 2009-10-11
> **Frak said:**
> -1

Both of those quotes lack ground. It's like saying XChat is closed source because their Windows port is proprietary. As for the iTunes one, there's a reason why we can't just drop in binaries and expect them to work. They have dependencies on other libraries. Some of those libraries are proprietary to Apple, just as libraries are proprietary to Microsoft. Hell, even RedHat and Suse have their own proprietary libraries to certain products, it's just how the cookie crumbles in real life.

Look, Apple does maintain some Open Source components, but they want to keep some things to themselves. Leave it to that. It's what makes Apple Apple, and not Apple, the originator of source X and lead to products Y and Z from company B.

But in reference the OP's question, there are clearly fairly large components of Mac OSX which are closed source...

---

### Post by Frak on 2009-10-11
> **hoppipolla said:**
> But in reference the OP's question, there are clearly fairly large components of Mac OSX which are closed source...

But the underlying OS is Open Source. You can build the Darwin OS (the core of Mac OS X), and it will run fine without Apple's bits. Is it binary compatible with OS X, yes it is. Can it run OS X executables, no it cannot. Again, that's what separates Apple from the rest of the pack, proprietary add-ins to make it a little sweeter.

---

### Post by Dimitriid on 2009-10-11
> **Frak said:**
> -1

Both of those quotes lack ground. 

Maybe the other one but can you call apple and obtain source code for the entire OS then? Then the OS itself is not open source. Its like saying "My car is brand new" because I just put a brand new engine and transmission on it. Either everything its brand new or the car is not brand new.

So either everything is open source or the entire OS is not open source. Yes this means that distros like Mint are actually not open source.

---

### Post by Warpnow on 2009-10-11
Darwin is a tiny fraction of OSX. It is like putting a random page of a novel under creative commons, its not very useful without the rest.

---

### Post by Frak on 2009-10-11
I like how people keep ignoring that there's more than Darwin. In fact, a large portion of the OS is open source, and would run fine without the proprietary bits.

---

### Post by hoppipolla on 2009-10-11
> **Frak said:**
> I like how people keep ignoring that there's more than Darwin. In fact, a large portion of the OS is open source, and would run fine without the proprietary bits.

Isn't the entire graphical interface closed source?


From Wikipedia:

> **Mac OS X**

Company / developer:	Apple Inc.
OS family:	Unix (Mac OS X 10.5 and later)[1][2]
Unix-like (all previous versions)
Working state:	Current
Source model:	**Closed source (with open source components)**
Latest stable release:	10.6.1  (2009-09-10; 31 days ago) [+/&#8722;]
Supported platforms:	IA-32, x86-64, PowerPC (32-bit & 64-bit up to version 10.5), ARMv6 and ARMv7-A (for iPhone OS)
Kernel type:	Hybrid kernel based on the Mach microkernel
Default user interface:	Aqua
License:	Proprietary EULA

So :P

---

### Post by sertse on 2009-10-11
> **Warpnow said:**
> Darwin is a tiny fraction of OSX. It is like putting a random page of a novel under creative commons, its not very useful without the rest.

If it's going to use analogies, it's more like putting out a rough screenplay of what's eventually a movie. In this example, yes while there are significance between it and the final product, you can see the connection, and how central it is. 

Not token at all.

---

### Post by schauerlich on 2009-10-11
It seems many people are misinformed with the architecture of OS X. Here are two relevant quotes from the FAQ in my sig.

> **EDavidBurg said:**
> **CS: Mac OS X is closed source.**
MAD: Parts of it are, parts of it aren't. Much of the core of OS X is [fully open source](http://www.apple.com/opensource/). Apple maintains a Unix distribution known as [Darwin](http://developer.apple.com/Darwin/), which serves as the base for each release of OS X. Until recently, Darwin was distributed in binary form and available on Apple's website to download. Currently you can download Darwin's source in full [here](http://www.opensource.apple.com/). _Apple has never intended Darwin to be a distribution for every day use_; however, a community effort called [PureDarwin](http://www.puredarwin.org/) has sprung up to make it more usable. Mac OS X is proprietary, there is no doubt about it. However, proprietary does not necessarily mean that it does not contain open source components which are released for modification and redistribution. [Mac OS Forge](http://www.macosforge.org/) is a community project that helps develop the FOSS components of Mac OS X.

Apple has also released several of their own projects under FOSS licenses. The most recent and most significant example of this is [Grand Central Dispatch](http://www.apple.com/macosx/technology/#grandcentral). GCD is an extension of C (and C based languages such as Objective-C, C++, etc) in the form of libdispatch which makes it easy for programmers to make their apps multi-threaded. [...] For a much better summary of the technology, see the [Ars Technica review of Mac OS X 10.6](http://arstechnica.com/apple/reviews/2009/08/mac-os-x-10-6.ars/12), as well as [Apple's Developer Connection page on it](http://developer.apple.com/mac/articles/cocoa/introblocksgcd.html). Apple's motive for open sourcing one of the main selling points of Snow Leopard is unclear, but the consensus seems to be that their use of [blocks](http://en.wikipedia.org/wiki/Blocks_(C_language_extension)) is a non-standard extension of C, and encouraging other Unix based systems to adopt it would benefit everyone.

[...]

**CS: Mac OS X is "just BSD with a shiny exterior," or "just an expensive version of Linux."**
MAD: Apple has incorporated a good amount of BSD code into Darwin. [...] However, to say that Mac OS X is simply BSD with a shiny exterior, or an expensive version of Linux, is misleading at best. OS X is based on the [XNU kernel](http://en.wikipedia.org/wiki/XNU), a [Mach](http://en.wikipedia.org/wiki/Mach_kernel)/[BSD](http://en.wikipedia.org/wiki/BSD#4.3BSD) hybrid kernel (with Apple's additions in [I/O Kit](http://en.wikipedia.org/wiki/I/O_Kit)), and incorporates a good amount of the base system from FreeBSD and various Unixes (although there are some GNU programs in there, such as screen and bash). There is a standard [POSIX](http://en.wikipedia.org/wiki/Posix) environment, but most of the more visible portions of the OS are either descended from [NeXTSTEP](http://en.wikipedia.org/wiki/Nextstep) or [made](http://en.wikipedia.org/wiki/Core_Foundation) [in-house](http://en.wikipedia.org/wiki/Quartz_(graphics_layer)) [by](http://en.wikipedia.org/wiki/Aqua_(user_interface)) [Apple](http://en.wikipedia.org/wiki/Carbon_(API)).

The most visible contribution Apple has made to OS X is the [Cocoa API](http://en.wikipedia.org/wiki/Cocoa_(API)). Written in Objective-C, Cocoa was based off of the [OpenStep API](http://en.wikipedia.org/wiki/OpenStep) developed for NeXTSTEP. [...] A FOSS implementation of the OpenStep API exists, named [GNUstep](http://en.wikipedia.org/wiki/Gnustep).

See [here](http://developer.apple.com/macosx/architecture/index.html) for more information about Mac OS X's architecture.

---

### Post by Warpnow on 2009-10-11
> **sertse said:**
> If it's going to use analogies, it's more like putting out a rough screenplay of what's eventually a movie. In this example, yes while there are significance between it and the final product, you can see the connection, and how central it is. 

Not token at all.


If we're honestly in an analogy off, its totally more like distributing a handout giving details of the setting, without mention of plot or characters. ;)

---

### Post by hoppipolla on 2009-10-11
> **Warpnow said:**
> If we're honestly in an analogy off, its totally more like distributing a handout giving details of the setting, without mention of plot or characters. ;)

Hehe this is weird isn't it? On one thread me and you are arguing like anything, and on another we are in almost complete agreement! hehe ^_^

---

### Post by Warpnow on 2009-10-11
> **hoppipolla said:**
> Hehe this is weird isn't it? On one thread me and you are arguing like anything, and on another we are in almost complete agreement! hehe ^_^

Both gnome and KDE kick OSXs ***. Its like watching giants fight a midget, with Darwin (aka the blind deaf mute paralyzed comatose guy) being used as a flail-like weapon in an attempt to level the playing field.

---

### Post by hoppipolla on 2009-10-11
> **Warpnow said:**
> Both gnome and KDE kick OSXs ***. Its like watching giants fight a midget, with Darwin (aka the blind deaf mute paralyzed comatose guy) being used as a flail-like weapon in an attempt to level the playing field.

I tell you man these metaphors and analogies are getting WEIRDER O.O  lol

It is cool we agree on some stuff though ^_^

---

### Post by myk02k on 2009-10-12
I think it's fair enough to say that I have enough information to invalidate much of his statements like this: "The OS thats open source Darwin is Mac, look it up its not a program for MAC OS X, its what MAC created for OPEN SOURCE developers if you would like a version of a MAC OS X".  After discrediting his claims I'll simply spin my argument as if we were speaking of the OS as a whole not being open-source because I'm quite positive he was under the assumption that the whole OS was open-source from the above comment.  Since the whole reason of this argument was that he claims I should've just switched to Mac instead of Ubuntu, I'll also throw in the benefits of general public licensing over proprietary licensing.

---

### Post by myk02k on 2009-10-12
Oh yea, thanks for the clarification :popcorn:

---

### Post by hoppipolla on 2009-10-12
> **myk02k said:**
> I think it's fair enough to say that I have enough information to invalidate much of his statements like this: "The OS thats open source Darwin is Mac, look it up its not a program for MAC OS X, its what MAC created for OPEN SOURCE developers if you would like a version of a MAC OS X".  After discrediting his claims I'll simply spin my argument as if we were speaking of the OS as a whole not being open-source because I'm quite positive he was under the assumption that the whole OS was open-source from the above comment.  Since the whole reason of this argument was that he claims I should've just switched to Mac instead of Ubuntu, I'll also throw in the benefits of general public licensing over proprietary licensing.

If it were me I'd just ask him to check it's "Source Model" on Wikipedia!

[http://en.wikipedia.org/wiki/Mac_OS_X](http://en.wikipedia.org/wiki/Mac_OS_X)


Job done eh? :)

---

### Post by myk02k on 2009-10-12
> **hoppipolla said:**
> If it were me I'd just ask him to check Wikipedia!

[http://en.wikipedia.org/wiki/Mac_OS_X](http://en.wikipedia.org/wiki/Mac_OS_X)


Job done eh? :)

I agree with you that your solution should work with most people, but the kid has this issue where he is only concerned in proving himself right over researching any fallacies that may exist in either side of the argument.  He's the kind of individual that would say something like, "smoking cigars don't cause cancer, cigarettes do" and rationalize it by listing cigar smokers who died of natural causes.  This argument hit a nerve when he said I know nothing about computers compared to him after bashing Linux claiming "it does nothing and can't run even Word".

---

### Post by hoppipolla on 2009-10-12
> **myk02k said:**
> I agree with you that your solution should work with most people, but the kid has this issue where he is only concerned in proving himself right over researching any fallacies that may exist in either side of the argument.  He's the kind of individual that would say something like, "smoking cigars don't cause cancer, cigarettes do" and rationalize it by listing cigar smokers who died of natural causes.  This argument hit a nerve when he said I know nothing about computers compared to him after bashing Linux claiming "it does nothing and can't run even Word".

*nods*

Some people are like that, and I don't know why either. I have a friend like that, and there is usually a lot of ignorance and intolerance in their "arguments" but for some reason they just can't see it. For my friend it might be a pride thing, I'm not sure.

But yeah, if he is determined to argue even with Wikipedia, then maybe you wanna go for the longer approach! lol

---

### Post by schauerlich on 2009-10-12
> **hoppipolla said:**
> If it were me I'd just ask him to check it's "Source Model" on Wikipedia!

[http://en.wikipedia.org/wiki/Mac_OS_X](http://en.wikipedia.org/wiki/Mac_OS_X)


Job done eh? :)

After all, one line out of a summary box on Wikipedia is such an authoritative source, and makes further research into the matter completely unnecessary. 

It's apparent to me that you've either not read or not understood the sections of the FAQ I've both linked to and directly quoted. You might want to do that. [http://ubuntuforums.org/showpost.php?p=8090464&postcount=46](http://ubuntuforums.org/showpost.php?p=8090464&postcount=46)

---

### Post by hanzomon4 on 2009-10-12
> **hoppipolla said:**
> *nods*

But yeah, if he is determined to argue **even with Wikipedia**, then maybe you wanna go for the longer approach! lol


#-o

---

### Post by unknownPoster on 2009-10-12
> **hoppipolla said:**
> *nods*


But yeah, if he is determined to argue even with Wikipedia, then maybe you wanna go for the longer approach! 

/facepalm

If it were Encyclopedia Brittanica, Webster's Dictionary, or some other reputable source, you'd have a point...

Wikipedia is not entirely reputable in it's information.

---

### Post by keplerspeed on 2009-10-12
Well, I wouldn't try referencing Wikipedia for an assignment. Dont take Wiki as truth - only believe what has proof or legit references.

Please read this before posting: [http://ubuntuforums.org/showpost.php?p=7347446&postcount=1](http://ubuntuforums.org/showpost.php?p=7347446&postcount=1)

EDavidBurg keeps linking, but you really NEED to read it!

---

### Post by hoppipolla on 2009-10-12
> **keplerspeed said:**
> Well, I wouldn't try referencing Wikipedia for an assignment. Dont take Wiki as truth - only believe what has proof or legit references.

Please read this before posting: [http://ubuntuforums.org/showpost.php?p=7347446&postcount=1](http://ubuntuforums.org/showpost.php?p=7347446&postcount=1)

EDavidBurg keeps linking, but you really NEED to read it!

I know but believe it or not there are OTHER avenues to discuss this by!! lol

The number of times I have been linked to that one page... lol  I have already acknowledged it once! xD

And I know that Wikipedia is only a wiki but somehow I think the Mac OSX page is fairly well maintained!

---

### Post by sertse on 2009-10-12
> **myk02k said:**
> I agree with you that your solution should work with most people, but the kid has this issue where he is only concerned in proving himself right over researching any fallacies that may exist in either side of the argument.  

Ironic. As others have linked to, there a thread where some one has slowly, methodologically researched, documented many of those issues, which you seemingly ignored because you also believe you are correct. Even without going into details (you can read the thread for that), he has provided more evidence, and than you have here. 

A note on wikipedia: It's not definitive, but even the article acknowledges Apple's examples of FLOSS. I actually agree, he should read it. It'll help them understand Apple (floss and no floss) more, and realise the conclusion lies in the middle, and that your view isn't completely right as well.

Reality is not clear cut. Detractors here basically go back down to the argument but it's not 100% FLOSS in every way hence they are evil. This attitude is wrong. 

The open minded correct answer is to acknowledge Apple is proprietary, in many ways but gives credit where it's due. It's not that hard,

---

### Post by hoppipolla on 2009-10-12
> **sertse said:**
> Ironic. As others have linked to, there a thread where some one has slowly, methodologically researched, documented many of those issues, which you seemingly ignored because you also believe you are correct. Even without going into details (you can read the thread for that), he has provided more evidence, and than you have here. 

A note on wikipedia: It's not definitive, but even the article acknowledges Apple's examples of FLOSS. I actually agree, he should read it. It'll help them understand Apple (floss and no floss) more, and realise the conclusion lies in the middle, and that your view isn't completely right as well.

Reality is not clear cut. Detractors here basically go back down to the argument but it's not 100% FLOSS in every way hence they are evil. This attitude is wrong. 

The open minded correct answer is to acknowledge Apple is proprietary, in many ways but gives credit where it's due. It's not that hard,

I think that's what most people have said though, no-one has argued it's totally open or totally closed source (other than myk02k's mate! lol)

---

### Post by Frak on 2009-10-12
> **hoppipolla said:**
> I think that's what most people have said though, no-one has argued it's totally open or totally closed source (other than myk02k's mate! lol)

But it isn't completely closed source, so claiming it's not open-source is a bunk argument.

---

### Post by Xbehave on 2009-10-12
> **Frak said:**
> But it isn't completely closed source, so claiming it's not open-source is a bunk argument.
How?
The claim that mac os X is not opensource is perfectly valid:
**FACT:** mac os x in the form distributed by apple (the only thing that can be called mac os x) is not open-source.


If we want to argue about how closed open it is, then it is not OPs question (that has already been answered, the proof on the link in the first page) then we could consider how much software for mac os x, darwin can run, the answer is next to zero.
itunes,safari,finder? <b>nope</b>
While the kernel is open and there are open utils & frameworks, i think a key test is that you cannot run any GUI app without going through closed parts of the stack.

If you write a program GUI for osX you cannot distribute enough of os X to run the program on a PC without os X installed, this can be done for an open-source operating system (bsd,hakiu,open solaris,etc)

---

### Post by 3rdalbum on 2009-10-12
It sounds like nothing you say will convince this person. He's probably trolling you. Ignore him. If it's impossible to ignore him, tell him that he should either provide you with a copy of the full source to OS X, or rearrange the letters "SUTF".

---

### Post by Warpnow on 2009-10-12
> **sertse said:**
> Ironic. As others have linked to, there a thread where some one has slowly, methodologically researched, documented many of those issues, which you seemingly ignored because you also believe you are correct. Even without going into details (you can read the thread for that), he has provided more evidence, and than you have here. 

A note on wikipedia: It's not definitive, but even the article acknowledges Apple's examples of FLOSS. I actually agree, he should read it. It'll help them understand Apple (floss and no floss) more, and realise the conclusion lies in the middle, and that your view isn't completely right as well.

Reality is not clear cut. Detractors here basically go back down to the argument but it's not 100% FLOSS in every way hence they are evil. This attitude is wrong. 

The open minded correct answer is to acknowledge Apple is proprietary, in many ways but gives credit where it's due. It's not that hard,

That thread is usually linked without replies to avoid the bothersome fact that its largely untrue and most of the people responding prove this.

---

### Post by schauerlich on 2009-10-12
> **Warpnow said:**
> That thread is usually linked without replies to avoid the bothersome fact that its largely untrue and most of the people responding prove this.

...And if you actually read the OP of that thread, you would know that it's changed *significantly* since 75% of those replies were written. 

If you still have a problem with my FAQ, I invite you to respond to that thread with your concerns. I've taken a lot of the feedback I received in the first few pages and worked it into the current version. If you know your stuff, chances are I'll take your feedback and use it to edit the OP. The whole goal of the post is to find common ground between the two sides of the argument - facts that can be verified, in order to cut through the FUD coming from both sides.

---

### Post by keiichidono on 2009-10-12
> **hoppipolla said:**
> *nods*

Some people are like that, and I don't know why either. I have a friend like that, and there is usually a lot of ignorance and intolerance in their "arguments" but for some reason they just can't see it. For my friend it might be a pride thing, I'm not sure.

**But yeah, if he is determined to argue even with Wikipedia, then maybe you wanna go for the longer approach! lol**

Yeah, anyone who argues with Wikipedia's facts are ignorant! :P

---

### Post by schauerlich on 2009-10-12
> **CalvinB said:**
> Yeah, anyone who argues with Wikipedia's facts are ignorant! :P

[http://en.wikipedia.org/wiki/Wikiality#Wikipedia_references](http://en.wikipedia.org/wiki/Wikiality#Wikipedia_references)

:)

---

### Post by Groucho Marxist on 2009-10-12
> **TheNessus said:**
> hurdle him to the nearest apple store and let him ask if he can acquire OS X for free.

=D> Exactly. That, and ask him a how-to for changing the default system colours from "Military-Industrial Complex Grey" to {insert colour here}.

On another note, third party programs may be FLOSS, but that does not impact whether or not the operating system is FLOSS or not.

---

### Post by Warpnow on 2009-10-12
Its just incorrect to claim OSX is open source. Its not a misunderstanding, its incorrect.

It has Open Source components, but OSX, as an operating system. As the operating system everyone knows as OSX, is closed source. There really isn't any room to argue. If Microsoft started releasing random blocks of code under an open source license, Windows XP would still be closed source. Or, more accurately, them announcing they are open sourcing DOS, does that make Windows XP open source? 

Now, Darwin is Open source. However, Darwin is no more OSX than BSD is OSX, or Unix is OSX. Just because it is in the creation hiearchy does not make it the same. There's a reason its called Darwin, rather than OSX Open Source Edition, because, while they are related, its no more open source than Windows is.

---

### Post by schauerlich on 2009-10-12
> **Warpnow said:**
> Its just incorrect to claim OSX is open source. Its not a misunderstanding, its incorrect.

It has Open Source components, but OSX, as an operating system. As the operating system everyone knows as OSX, is closed source. 

Claiming that Ubuntu is under the GPL is equally as incorrect. There is plenty of code in there that isn't GPL, or even BSD.

Treating an OS (which is a collection of many, many different pieces of software) as if it is one large piece of software, and then trying to label it as open or closed source, makes no sense.

Is a tree brown or green?

---

### Post by hoppipolla on 2009-10-12
> **Warpnow said:**
> Its just incorrect to claim OSX is open source. Its not a misunderstanding, its incorrect.

It has Open Source components, but OSX, as an operating system. As the operating system everyone knows as OSX, is closed source. There really isn't any room to argue. If Microsoft started releasing random blocks of code under an open source license, Windows XP would still be closed source. Or, more accurately, them announcing they are open sourcing DOS, does that make Windows XP open source? 

Now, Darwin is Open source. However, Darwin is no more OSX than BSD is OSX, or Unix is OSX. Just because it is in the creation hiearchy does not make it the same. There's a reason its called Darwin, rather than OSX Open Source Edition, because, while they are related, its no more open source than Windows is.

OSX is no more open source than Windows? o.O

But yeah anyway I think this argument is SO over... lol

I think the OP has more than enough evidence to make the case that not all of OSX is open source, and huge chunks are closed source. Phew. hehe :)

---

### Post by hoppipolla on 2009-10-12
> **EDavidBurg said:**
> Claiming that Ubuntu is under the GPL is equally as incorrect. There is plenty of code in there that isn't GPL, or even BSD.

Treating an OS (which is a collection of many, many different pieces of software) as if it is one large piece of software, and then trying to label it as open or closed source, makes no sense.

Is a tree brown or green?

Well, I never said Mac OSX was closed source, Wikipedia did lol

I said it had open source and closed source components, and so I don't really feel it can be labelled as EITHER. His friend is therefore incorrect.

End of! lol

---

### Post by Warpnow on 2009-10-12
> **hoppipolla said:**
> OSX is no more open source than Windows? o.O


I said if Microsoft open sourced parts, its a conditional phrase.

And, true, OSs consist of many parts, but OSX is the name given to the entire, complete operating system. The open source component is Darwin.

And I never claimed ubuntu was GPL, nor did I see where anyone did (though they might have, I'm not searching the thread).

However, Ubuntu is all (to the best of my knowledge) open source, even if distributed under various licenses.

---

### Post by Bachstelze on 2009-10-12
> **Warpnow said:**
> 
And, true, OSs consist of many parts, but OSX is the name given to the entire, complete operating system. The open source component is Darwin.

Darwin is one of the open source components. There are many others.

> **Warpnow said:**
> However, Ubuntu is all (to the best of my knowledge) open source, even if distributed under various licenses.

Then I wonder why the FSF bothers with gNewSense...

---

### Post by Warpnow on 2009-10-12
> **Bachstelze said:**
> Darwin is one of the open source components. There are many others.

My point still stands. When people think of OSX they think of the complete OS, not its individual bits and parts, just like when people think of a Ford Focus, they aren't considering the muffler or the steering collumn. Its a finished product.


> **Bachstelze said:**
> 
Then I wonder why the FSF bothers with gNewSense...

I was under the impression that while ubuntu did not include closed source programs it did include closed license programs, and that is why gNewSense exists. Is this incorrect?

I admit I have not checked all of ubuntu's packages for being open source, though I did believe such was the case.

---

### Post by Bachstelze on 2009-10-12
> **Warpnow said:**
> 
I admit I have not checked all of ubuntu's packages for being open source, though I did believe such was the case.

The nvidia Xorg libraries for example (the kernel module is open source), or the rar utility.

---

### Post by schauerlich on 2009-10-12
> **Warpnow said:**
> My point still stands. When people think of OSX they think of the complete OS, not its individual bits and parts, just like when people think of a Ford Focus, they aren't considering the muffler or the steering collumn. Its a finished product.

I think you're confusing the terms *closed source* and *proprietary*. 

Closed source means what you think it means - the source code is not available. This is not true of a significant portion of the OS, and it is a poor term to describe the entire OS. It is a term that generally is used to refer to specific pieces of software, and is inappropriate in this context.

Proprietary means that the modification and redistribution of the project is not freely allowed. While this term is used to describe specific pieces of software, it is also used to describe distributions of bundled software - such as an operating system - as its definition refers specifically to its mode of distribution. 

As I stated in the FAQ, Mac OS X is indisputably proprietary. However, closed source is not an appropriate term for it, as its source model is mixed.

---

### Post by hoppipolla on 2009-10-12
> **Warpnow said:**
> My point still stands. When people think of OSX they think of the complete OS, not its individual bits and parts, just like when people think of a Ford Focus, they aren't considering the muffler or the steering collumn. Its a finished product.

Wait wait wait, are you arguing that Mac OSX is "closed source"? You're not right? As that's what EDavidBurg just implied and I always thought surely you were arguing that it can't be labelled as "open source" either, which I would imagine everyone agrees with.

Is there something I'm missing? Can't we just agree? lol :)

> **EDavidBurg said:**
> As I stated in the FAQ, Mac OS X is indisputably proprietary. However, closed source is not an appropriate term for it, as its source model is mixed.

Precisely :)  And neither is "open source" :)

---

### Post by Frak on 2009-10-12
> **Xbehave said:**
> How?
The claim that mac os X is not opensource is perfectly valid:
**FACT:** mac os x in the form distributed by apple (the only thing that can be called mac os x) is not open-source.


If we want to argue about how closed open it is, then it is not OPs question (that has already been answered, the proof on the link in the first page) then we could consider how much software for mac os x, darwin can run, the answer is next to zero.
itunes,safari,finder? <b>nope</b>
While the kernel is open and there are open utils & frameworks, i think a key test is that you cannot run any GUI app without going through closed parts of the stack.

If you write a program GUI for osX you cannot distribute enough of os X to run the program on a PC without os X installed, this can be done for an open-source operating system (bsd,hakiu,open solaris,etc)

GUI, IMO, is not considered part of the underlying operating system, the part that actually does the work. The GUI is just an interface to the system, but underlying user-interfaces are freely open source, such as bash. You can recompile a majority of the source components of OS X and come up with a functional OS, with or without a GUI, still using Apple source code that was derived from the Mac OS X Operating System.

Also, whoever said Open Source = Free is incorrect. RAR is open source, but you aren't allowed to change and redistribute it. The GPL is Free and Open Source Software, but you may still have to buy the software with actual capital. If you want absolutely free software, it's best to look elsewhere.

---

### Post by Warpnow on 2009-10-12
My opinion is that if the core part of a project that makes it closed source is closed, then the project is for all intents and purpose closed. You cannot get the same experience from OSX's open source components. It is not the same product.

OSX is a product. The parts of the product which make it identifiable are closed source. It is true that it has open source components, I will not argue otherwise, nor would I claim that it is an entirely closed source application.

Thinks of it like any normal product.

---

### Post by steev182 on 2009-10-12
Get him to read the legal messages and the EULA that comes with OSX, he'll see the evidence then...

---

### Post by Frak on 2009-10-12
> **steev182 said:**
> Get him to read the legal messages and the EULA that comes with OSX, he'll see the evidence then...
I can put crazy stuff in my license too. Doesn't make it any less Open Source.

---

### Post by Warpnow on 2009-10-12
> **Frak said:**
> I can put crazy stuff in my license too. Doesn't make it any less Open Source.

Unless its:

1. You may not look at my source code. Its in a tar.gz file, but don't look at it. You'll ruin the honor system for everyone.

;)

---

### Post by hoppipolla on 2009-10-12
I think I will have to agree to disagree with a few views here :)

Personally I think Mac OSX is the "whole package", GUI and all... so I'll have to disagree with you there **Frak** :)

I will also have to disagree with **Warpnow** a little in that I as I have said wouldn't regard OSX as open or closed, but a combination.

Oh well, nothing wrong with having different views on something :)

---

### Post by Dr. C on 2009-10-12
A good place to start is the License for Mac OS X [http://store.apple.com/Catalog/US/Images/MacOSX.htm]("http://store.apple.com/Catalog/US/Images/MacOSX.htm")
What you have is a propriety OS with some FLOSS components as mentioned in section 12B of the license for example:
> B. The Apple Software includes certain software owned by the Free Software Foundation, Inc. (”FSF”) and licensed by Apple. You may obtain a complete machine-readable copy of the source code for the FSF Software under the terms of the GNU General Public License, without charge except for the cost of media, shipping, and handling, upon written request to Apple. The FSF Software is distributed in the hope that it will be useful, but WITHOUT ANY WARRANTY, without even the implied warranty of MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE. A copy of the GNU General Public License is included with the Apple Software.
 
The presence of some FLOSS code does not make the OS FLOSS. One can also download components for Windows XP from [Microsoft]("http://www.microsoft.com/downloads/details.aspx?FamilyID=896C9688-601B-44F1-81A4-02878FF11778&displaylang=en"), including GPL'd code owned by the FSF but that does not make Windows XP FLOSS.

---

### Post by Frak on 2009-10-12
> **FineE said:**
> A good place to start is the License for Mac OS X [http://store.apple.com/Catalog/US/Images/MacOSX.htm]("http://store.apple.com/Catalog/US/Images/MacOSX.htm")
What you have is a propriety OS with some FLOSS components as mentioned in section 12B of the license for example:
 
The presence of some FLOSS code does not make the OS FLOSS. One can also download components for Windows XP from [Microsoft]("http://www.microsoft.com/downloads/details.aspx?FamilyID=896C9688-601B-44F1-81A4-02878FF11778&displaylang=en"), including GPL'd code owned by the FSF but that does not make Windows XP FLOSS.
So, since Ubuntu contains proprietary components, that makes it proprietary too?

**Everybody, Ubuntu is proprietary!**

---

### Post by Xbehave on 2009-10-12
> GUI, IMO, is not considered part of the underlying operating system,
I'm not talking about the GUI apps, but the actual framework, I consider xorg pretty integral to any desktop linux distribution.

> You can recompile a majority of the source components of OS X and come up with a functional OS, with or without a GUI, still using Apple source code that was derived from the Mac OS X Operating System.
OS X has 5  APIs:
carbon - [closed]("http://en.wikipedia.org/wiki/Carbon_%28API%29") (what you used for a native look)
cacoa  - [closed]("http://en.wikipedia.org/wiki/Cocoa_%28API%29") (what you use for a native look)
java   - Not native
X11    - Not native
posix  - Not GUI

But most of all the fact the [only windowing system and window manager]("http://en.wikipedia.org/wiki/Quartz_Compositor") for mac os X is closed source means that there is no way to get GUI applications from just the open source stuff!

> RAR is open source, but you aren't allowed to change and redistribute it.That is by definition closed source!

> So, since Ubuntu contains proprietary components, that makes it proprietary too? Not only does the os have no APIs that are closed, in addition ubuntu contains no propriety components by default.

---

### Post by Bachstelze on 2009-10-12
> **Frak said:**
> RAR is open source, but you aren't allowed to change and redistribute it.

Is not.

[http://www.rarlab.com/download.htm](http://www.rarlab.com/download.htm) Download the Linux version, extract it, you just get a binary.

> **Xbehave said:**
> 
That is by definition closed source!


Nope. It's what makes open source software different from free software. When you can see the source but not touch it, it is open source, but not free. When you can do both, it is open source *and* free.

---

### Post by Dr. C on 2009-10-12
> **Frak said:**
> So, since Ubuntu contains proprietary components, that makes it proprietary too?

**Everybody, Ubuntu is proprietary!**

If one takes the propriety components out of Ubuntu one gets a perfectly viable OS, that is virtually identical to Ubuntu. Its called [gNewSense]("http://www.gnewsense.org/") If I install GNU/Emacs on Windows Vista that does not make Vista FLOSS anymore than installing Adobe Flash on gNewSense would make gNewSense propriety. 

Ubuntu is a FLOSS OS with some (very few) propriety components and the ability to easily install propriety components.

---

### Post by Bachstelze on 2009-10-12
> **FineE said:**
> GNU/Emacs

That's priceless. People are so worket up on the "GNU slash" thing that they don't even understand what it means, and therefore use it incorrectly for anything.

FYI, it is GNU Emacs, or just Emacs.

---

### Post by Frak on 2009-10-12
> **Xbehave said:**
> But most of all the fact the [only windowing system and window manager]("http://en.wikipedia.org/wiki/Quartz_Compositor") for mac os X is closed source means that there is no way to get GUI applications from just the open source stuff!

That is by definition closed source!

 Not only does the os have no APIs that are closed, in addition ubuntu contains no propriety components by default.

Gnome builds and runs on Darwin just fine.

As for Ubuntu, it contains proprietary drivers along with some questionable software (open source or otherwise).

> **Bachstelze said:**
> Is not.

[http://www.rarlab.com/download.htm](http://www.rarlab.com/download.htm) Download the Linux version, extract it, you just get a binary.



Nope. It's what makes open source softwa

First off, caught ya in the middle of an edit ;)

Secondly, I could have sworn I stumbled upon the unRAR source code somewhere. It said it was free to study, but you were not allowed to modify or redistribute it.

---

### Post by Bachstelze on 2009-10-12
> **Frak said:**
> 
Secondly, I could have sworn I stumbled upon the unRAR source code somewhere. It said it was free to study, but you were not allowed to modify or redistribute it.

unrar, yeah. rar, nope.

---

### Post by Dr. C on 2009-10-12
> **Bachstelze said:**
> That's priceless. People are so worket up on the "GNU slash" thing that they don't even understand what it means, and therefore use it incorrectly for anything.

FYI, it is GNU Emacs, or just Emacs.

Actually GNU Emacs is the correct term since there are non GNU versions of Emacs.

---

### Post by aysiu on 2009-10-12
I think people are getting a bit caught up in semantics here.

You are not free to take Mac OS X as a whole, modify parts of it, and then redistribute it as an new OS... not unless you want Apple's legal team after you.

You are, however, free to take Ubuntu as a whole, modify parts of it, and then redistribute it as a new OS, as long as you don't call it somethingbuntu (the Ubuntu trademark policy insists you call it *Ubuntu something Remix*).

Yes, many parts of OS X are released under some kind of open source license. But who cares? Darwin without all the proprietary components on top is *nothing* like OS X. gNewSense is, however, very similar to Ubuntu (if maybe lacking in some hardware functionality).

---

### Post by Bachstelze on 2009-10-12
> **aysiu said:**
> You are, however, free to take Ubuntu as a whole, modify parts of it, and then redistribute it as a new OS, as long as you don't call it somethingbuntu (the Ubuntu trademark policy insists you call it *Ubuntu something Remix*).

Also as long as I remove, for example, the official Firefox branding, since Mozilla forbids redistribution of Firefox builds using it and granted Ubuntu (and other distros) special permission to do so.

> **aysiu said:**
> 
Yes, many parts of OS X are released under some kind of open source license. But who cares? 

I think people who want to develop software for OS X are very glad to be able to look at the kernel source.

---

### Post by Frak on 2009-10-12
> **bachstelze said:**
> i think people who want to develop software for os x are very glad to be able to look at the kernel source.

+1

---

### Post by aysiu on 2009-10-12
> **Bachstelze said:**
> Also as long as I remove, for example, the official Firefox branding, since Mozilla forbids redistribution of Firefox builds using it and granted Ubuntu (and other distros) special permission to do so.



I think people who want to develop software for OS X are very glad to be able to look at the kernel source.
Actually, I think it should be fine. From [the Mozilla trademark FAQ](http://www.mozilla.org/foundation/trademarks/faq.html): > **Can I distribute any of the Mozilla software from my website, by CD, or to my friends, employees or students?**
    If you are redistributing unchanged official stable binaries downloaded from mozilla.org, to anyone in any way and for any purpose, no further permissions are required from us. We request that you distribute the latest stable version (and of course, we believe that it's in your best interest to do so as well). The notification requirements of the MPL have been met for our binaries, so although it's a good idea, you are not required to ship source code. I highly doubt Mozilla is going to come after you if you modify Ubuntu and redistribute it (in fact, I've done so, and Mozilla has done nothing to stop me).

If you're really worried about it, you can actually download the official Firefox binary from the Mozilla site and use that in place of the Ubuntu Firefox.

---

### Post by Bachstelze on 2009-10-12
> **aysiu said:**
> Actually, I think it should be fine. From [the Mozilla trademark FAQ](http://www.mozilla.org/foundation/trademarks/faq.html):  I highly doubt Mozilla is going to come after you if you modify Ubuntu and redistribute it (in fact, I've done so, and Mozilla has done nothing to stop me).

If you're really worried about it, you can actually download the official Firefox binary from the Mozilla site and use that in place of the Ubuntu Firefox.

And what if the modifications I want to make to Ubuntu include modifying Firefox? Blammo, I can't. I don't care whether or not mozilla will actually come after me, the point is that I'm doing something illegal.

---

### Post by aysiu on 2009-10-12
> **Bachstelze said:**
> And what if the modifications I want to make to Ubuntu include modifying Firefox? Blammo, I can't. I don't care whether or not mozilla will actually come after me, the point is that I'm doing something illegal.
Then strip out the Mozilla branding (icons, naming).

Blammo. You can.

---

### Post by Bachstelze on 2009-10-12
> **aysiu said:**
> Then strip out the Mozilla branding (icons, naming).

Blammo. You can.

The point it that I can't modify Ubuntu as I wish, since I can't modify the source of Mozilla and keep the official branding.

Is Firefox part of Ubuntu? I don't think so. But since you seem to think that what comes installed by default with an OS is the OS itself, then I'm sorry, but by that logic Ubuntu is not free.

---

### Post by river226 on 2009-10-12
> **Frak said:**
> I like how people keep ignoring that there's more than Darwin. In fact, a large portion of the OS is open source, and would run fine without the proprietary bits.

well, actually as far as i know the Darwin isn't ready to run on x86, on PPC, cause apple cuts out the bit of the code needed for Intel comparability... i unfortunately don't have a link to back that statement, but when i was in a similar argument a while ago, i came across an article on it...

anyways, Darwin is FOSS, and the liscence is approved by the FSF in 2003: [http://en.wikipedia.org/wiki/Darwin_%28operating_system%29](http://en.wikipedia.org/wiki/Darwin_%28operating_system%29)

and end this, this is the official list of open source software: 
[http://www.apple.com/opensource/](http://www.apple.com/opensource/)

besides apple OS X is not Open Source, the apple eula basically confirms, it as well as the psystar trial, so some parts may be Open Source/Free, but the OS is a proprietary operating system, and since it's made by apple. If that surprises you, then i guess you really should read up on apple, they like control to much to go completely "free". Hell, i think Microsoft windows will be completely Open Source before apple makes the switch (granted that's a long shot)

---

### Post by aysiu on 2009-10-12
> **Bachstelze said:**
> The point it that I can't modify Ubuntu as I wish, since I can't modify the source of Mozilla and keep the official branding.

Is Firefox part of Ubuntu? I don't think so. But since you seem to think that what comes installed by default with an OS is the OS itself, then I'm sorry, but by that logic Ubuntu is not free.
Now you're just playing word games to sound clever.

---

### Post by schauerlich on 2009-10-12
> **river226 said:**
> and end this, this is the official list of open source software: 
[http://www.apple.com/opensource/](http://www.apple.com/opensource/)

There's even more here
[http://www.opensource.apple.com/](http://www.opensource.apple.com/)

---

### Post by Bachstelze on 2009-10-12
> **aysiu said:**
> Now you're just playing word games to sound clever.

Or maybe *you*'re just oversimplifying things with your manichaeism. As was stated countless times in this thread, nothing is entirely black or white.

---

### Post by t0p on 2009-10-12
OMG read EDavidBurg's FAQ!  He wrote it, he continually links to it, so it *must* be right!  LMAO!!  :p

> **Bachstelze said:**
>  As was stated countless times in this thread, nothing is entirely black or white.

I'll tell you *one* thing that's black and white... the fact you're WRONG!

> **Bachstelze said:**
> Nope. It's what makes open source software different from free software. When you can see the source but not touch it, it is open source, but not free. 

What you're describing there is *not* open source.  Microsoft wanted that to become the definition of open source.  But it isn't.  Being open spource means you can *modify* the code.  For heaven's sake, that's what the Open Source Definition is all about!!
From the [Open Source Definition]("http://www.opensource.org/docs/osd"):

> Open source doesn't just mean access to the source code. The distribution terms of open-source software must comply with the following criteria:
[...]
The license must allow modifications and derived works, and must allow them to be distributed under the same terms as the license of the original software.

Semi-informed argument is often worse than just being totally wrong.

---

### Post by Frak on 2009-10-12
> **t0p said:**
> OMG read EDavidBurg's FAQ!  He wrote it, he continually links to it, so it *must* be right!  LMAO!!  :p



I'll tell you *one* thing that's black and white... the fact you're WRONG!



From the [Open Source Definition]("http://www.opensource.org/docs/osd"):



What you're describing there is *not* open source.  Microsoft wanted that to become the definition of open source.  But it isn't.  Being open spource means you can *modify* the code.  For heaven's sake, that's what the Open Source Definition is all about!!

Semi-informed argument is often worse than just being totally wrong.
^^this

I didn't see it, but, wow, you are absolutely 100% right. I mean, being able to read ***and*** modify the source code! Wow, I thought they called that FOSS, but, wow, you must be right.

---

### Post by sertse on 2009-10-12
I'm sure everyone is smart and know the the flossness or not of Apple etc.

The key argument in answering the OP is whether a proprietary system using floss as a base is still floss. 

if we're going to play semantics however, OP has already lost. He needs "solid" reasoning, one side is correct over the other. We've proven at the very least, that it's a arguable topic at least. This can't be debated.

Maybe I just can't over the attitude the OP is making about his friend etc.

---

### Post by schauerlich on 2009-10-12
> **t0p said:**
> OMG read EDavidBurg's FAQ!  He wrote it, he continually links to it, so it *must* be right!  LMAO!!  :p

As I've stated repeatedly and included several times in the FAQ, I invite any and all constructive criticism/feedback on the FAQ, and have used much of the feedback I've received to make it better. I encourage you to respond to the thread, quoting the sections you take issue with, and giving your view on the matter. If your claim has substance, it's likely that I'll incorporate it into the FAQ.

The goal of that page is not to be a rant, but a place to establish common ground between both sides of the argument.

---

### Post by Xbehave on 2009-10-12
> **Bachstelze said:**
> Or maybe *you*'re just oversimplifying things with your manichaeism. As was stated countless times in this thread, nothing is entirely black or white.
Sorry  but weather something is open-source or not is pretty well defined and it has nothing to do with trademark policy.

If we do something simple like define mac os X as what you pay apple money for and they sell you on a disk.
And ubuntu as what you get on a default ubuntu install.

Then it is quite clear that one can be modified and redistributed(patent and trademark issues are not withstanding) and one can not.

> It's what makes open source software different from free software. When you can see the source but not touch it,No being able to look at the source does not make a license open-source (at least by any definition that matters). To be open source you have to be allowed to modify (which you can do anyway) and redistribute modified code. Now you can make up your own definition but even microsoft accepts the [OSD]("http://en.wikipedia.org/wiki/Open_Source_Definition")

---

### Post by Bachstelze on 2009-10-12
> **t0p said:**
> 
What you're describing there is *not* open source.  Microsoft wanted that to become the definition of open source.  But it isn't.  Being open spource means you can *modify* the code.  For heaven's sake, that's what the Open Source Definition is all about!!

There are several definitions of open source. Just because some organization called itself the open source group and decided that open source means something doesn't mean people have to agree with them. The definition of open source by the OSI is pretty much equivalent to free software by the FSF. The fact that the OSI approved some licenses the FSF did not (and vice versa) is just legal nitpicking.

> **Xbehave said:**
> 
If we do something simple like define mac os X as what you pay apple money for and they sell you on a disk.
And ubuntu as what you get on a default ubuntu install.

Then it is quite clear that one can be modified and redistributed(patent and trademark issues are not withstanding) and one can not.

And no one said otherwise...

---

### Post by Frak on 2009-10-12
> **Xbehave said:**
> Sorry  but weather something is open-source or not is pretty well defined and it has nothing to do with trademark policy.

Yes, if you believe what the FSF says, then you're right, but there are more people defining what Open Source means.

---

### Post by t0p on 2009-10-12
> **sertse said:**
> 
Maybe I just can't over the attitude the OP is making about his friend etc.

That's one of the wonderful things about friendship: you can slag each other to high heaven, and at the end of the day you're still friends.

---

### Post by t0p on 2009-10-12
> **Bachstelze said:**
> There are several definitions of open source. Just because some organization called itself the open source group and decided that open source means something doesn't mean people have to agree with them. The definition of open source by the OSI is pretty much equivalent to free software by the FSF. The fact that the OSI approved some licenses the FSF did not (and vice versa) is just legal nitpicking.


Actually, the OSI got legal protection for the term "open source".  Their definition is the *only* legal definition (in the USA, Europe and other territories).  That means it is illegal to call your software open source if it does not meet the OSI's definition.

---

### Post by Xbehave on 2009-10-12
> **Frak said:**
> I didn't see it, but, wow, you are absolutely 100% right. I mean, being able to read ***and*** modify the source code! Wow, I thought they called that FOSS, but, wow, you must be right.
Free software is what free software is as defined by FSF
Open source is what is defined by OSD and is recognised by everybdoy including microsoft.

Free software is open source
but open source software is not necessarily free software

It would be silly if free software was started over the right to see but not modify programs as it all began over some lisp code (which I believe is interpreted so you can always see the source) which while RMS could see, he could not modify to produce a unified lisp system.

---

### Post by Frak on 2009-10-12
> **Xbehave said:**
> Free software is what free software is as defined by FSF
Open source is what is defined by OSD and is recognised by everybdoy including microsoft.

Free software is open source
but open source software is not necessarily free software

It would be silly if free software was started over the right to see but not modify programs as it all began over some lisp code (which I believe is interpreted so you can always see the source) which while RMS could see, he could not modify to produce a unified lisp system.
Again, I can name an Open Source program that cannot be modified or redistributed, unrar. The source is open for study, but you cannot modify or redistribute it without permission.

---

### Post by Bachstelze on 2009-10-12
> **t0p said:**
> Actually, the OSI got legal protection for the term "open source".

Orly? Source, please.

---

### Post by Frak on 2009-10-12
> **Bachstelze said:**
> Orly? Source, please.
But, but, but, you can't modify it and stuff, yo!

---

### Post by Bachstelze on 2009-10-12
> **Frak said:**
> Again, I can name an Open Source program that cannot be modified or redistributed, unrar. The source is open for study, but you cannot modify or redistribute it without permission.

Actually, distribution of unmodified unrar source, either alone or as part as another application, is permitted.

```
   2. The UnRAR sources may be used in any software to handle RAR
      archives without limitations free of charge, but cannot be used
      to re-create the RAR compression algorithm, which is proprietary.
      Distribution of modified UnRAR sources in separate form or as a
      part of other software is permitted, provided that it is clearly
      stated in the documentation and source comments that the code may
      not be used to develop a RAR (WinRAR) compatible archiver.

```

---

### Post by Frak on 2009-10-12
> **Bachstelze said:**
> Actually, distribution of unmodified unrar source, either alone or as part as another application, is permitted.

```
   2. The UnRAR sources may be used in any software to handle RAR
      archives without limitations free of charge, but cannot be used
      to re-create the RAR compression algorithm, which is proprietary.
      Distribution of modified UnRAR sources in separate form or as a
      part of other software is permitted, provided that it is clearly
      stated in the documentation and source comments that the code may
      not be used to develop a RAR (WinRAR) compatible archiver.

```
rawrawrawrawrawrawr

---

### Post by fela on 2009-10-12
> **Frak said:**
> It's like saying XChat is closed source because their Windows port is proprietary.

If the windows port contained separate, closed source code from the original, it would essentially be a different program, and yes, closed source.

---

### Post by fela on 2009-10-12
> **Frak said:**
> Again, that's what separates Apple from the rest of the pack, proprietary add-ins to make it a little sweeter.

Or a bit sourer, depending on who you ask. But I agree that OSX's closed source components are killers and I confess that I'd love to see them ported to Linux and open sourced :)

---

### Post by t0p on 2009-10-12
> **Bachstelze said:**
> Orly? Source, please.

Okay, well it appears that the OSI has [recently lost corporate status]("http://ldn.linuxfoundation.org/article/the-open-source-initiative%E2%80%99s-corporate-status-suspended-1"), which means "The ability of the Open Source Initiative to steward the Open Source Definition and police the use of the term open source as it relates to software is in doubt."  So the definition may lack legal standing.

But that doesn't change the fact that "open source" has a definition the same as "free software".  Anyone who seeks to dilute that meaning is doing it for self-serving purposes.  Such as to rip people off, or to win arguments in web forums with sly semantic games.  :p

---

### Post by Bachstelze on 2009-10-12
> **t0p said:**
> 
But that doesn't change the fact that "open source" has a definition the same as "free software".  Anyone who seeks to dilute that meaning is doing it for self-serving purposes.  Such as to rip people off, or to win arguments in web forums with sly semantic games.  :p

Eh, one has to keep entertained. Anyway, I'm supposed to be studying for some exams, so I guess I'll call it a day. As a side note, I don't think the OSI ever had any legal ownership of the term "open source". I could find nothing that indicates so.

---

### Post by Xbehave on 2009-10-12
> **Frak said:**
> Again, I can name an Open Source program that cannot be modified or redistributed, unrar. The source is open for study, but you cannot modify or redistribute it without permission.
unRAR is not open source by anybodies definition, except yours and nobody cares what your definition is, not me, not canonical, not microsoft.

> shareware versions of this program are also available for GNU/Linux, Mac OS X, DOS, OS/2, and FreeBSD, though they are all called simply "RAR". RARLAB distributes the source code and binaries for a freeware command-line "unrar" program,[7] **although it is not under a free software license.** This program can only decompress/extract, not create RAR files.Now you can look at the code but that doesn't make it open source (again ignoring your personal definition). There are many programs that have a view but do not touch policy, they are not open source (again ignoring your personal definition)

---

### Post by Frak on 2009-10-12
> **Xbehave said:**
> unRAR is not open source by anybodies definition, except yours and nobody cares what your definition is, not me, not canonical, not microsoft.

Now you can look at the code but that doesn't make it open source (again ignoring your personal definition). There are many programs that have a view but do not touch policy, they are not open source (again ignoring your personal definition)
Free Software != Open Source

Bunk argument is bunk.

---

### Post by Xbehave on 2009-10-12
> **Frak said:**
> Free Software != Open Source

Bunk argument is bunk.
right but open source is well defined and unrar is not open source (again ignoring your definition)

Look but can't touch != open source
You have the right to look (and modify but not distribute) at the code of any program you own

---

### Post by Bachstelze on 2009-10-12
> **Frak said:**
> Free Software != Open Source

Bunk argument is bunk.

Way to ignore the last few posts. :p There are several definitions of open source around, and sine none has an official status, the term can mean pretty much anything.

---

### Post by Xbehave on 2009-10-12
> **Bachstelze said:**
> Way to ignore the last few posts. :p There are several definitions of open source around, and sine none has an official status, the term can mean pretty much anything.
There are many definitions of red around however it can not mean [COLOR="Blue"]blue[/COLOR], all the recognised definitions of open source require that you can redistribute modified code (or something to that effect)

---

### Post by sertse on 2009-10-12
I should say, I use FLOSS mainly so I don't offend anyone though. Though reading this thread I'm willing to amend that might be OSS but not FLOSS, if FLOSS is the RMS 100% pure uber definition.

---

### Post by Xbehave on 2009-10-12
> **sertse said:**
> I should say, I use FLOSS mainly so I don't offend anyone though. Though reading this thread I'm willing to amend that might be OSS but not FLOSS, if FLOSS is the RMS 100% pure uber definition.
By FLOSS I think you mean free software, FLOSS is a catch all term but AFAIK it is not well defined like open-source and free software.

---

### Post by t0p on 2009-10-12
> **Xbehave said:**
> unRAR is not open source by anybodies definition, except yours and nobody cares what your definition is, not me, not canonical, not microsoft.

Now you can look at the code but that doesn't make it open source (again ignoring your personal definition). There are many programs that have a view but do not touch policy, they are not open source (again ignoring your personal definition)

Even a cursory google for "open source definitions" throws up many definitions that all demand the source must be available for both inspection *and* modification.  For example: [searchenterpriselinux.com says]("http://searchenterpriselinux.techtarget.com/sDefinition/0,,sid39_gci212709,00.html"):

> In general, open source refers to any program whose source code is made available for use **or modification as users or other developers see fit**. Open source software is usually developed as a public collaboration and made freely available.[Webopedia.com says]("http://www.webopedia.com/TERM/O/open_source.html"):

> Generically, *open source* refers to a program in which the source code is available to the general public for use **and/or modification from its original design** free of charge, i.e., [open]("http://www.webopedia.com/TERM/O/open.html").[The Digital Curation Center says]("http://www.dcc.ac.uk/FAQs/open-source/#q1"):

> The open source community recognises a range of individual off-the-shelf open source licenses. In order to qualify, a license must satisfy the open source definition, and offer users the right to freely obtain, use, **reuse and distribute** licensed code.This is just a small survey of search results for "open source definition|".  There are lots of other examples that specify the need to be able to modify the source code.  And of course (to get back on topic :) ) OSX meets none of these definitions.  Just look at the EULA you must agree to in order to use OSX.  Apple keep strict control over the software that they allow you to use.

---

### Post by schauerlich on 2009-10-12
> **t0p said:**
> This is just a small survey of search results for "open source definition|".  There are lots of other examples that specify the need to be able to modify the source code.  And of course (to get back on topic :) ) OSX meets none of these definitions.  Just look at the EULA you must agree to in order to use OSX.  Apple keep strict control over the software that they allow you to use.

Once again, you're treating OS X as a single unit. It's a more complex issue than that.

---

### Post by Viva on 2009-10-12
Opensource is not a matter of license, but development model imo. I wouldn't consider Chrome opensource because it does not use a community-based development model. If somebody forks chrome and accepts code from the community, then the resulting browser will be opensource. It is free software though, because it gives you freedom.

---

### Post by stmiller on 2009-10-12
Apple does release the sources to the core 'darwin' parts:

[http://opensource.apple.com/](http://opensource.apple.com/)

Sources are released under their BSD-like APSL license.

There used to be an 'open darwin' project to build an OS from the sources, but that fizzled out:

[http://en.wikipedia.org/wiki/Darwin_%28operating_system%29](http://en.wikipedia.org/wiki/Darwin_%28operating_system%29)

But.... Apple apps and other components are not open sourced, so don't think you can go compile iMovie or something like that. :)

FWIW to the poster remarking to try and go download RHEL: anyone can download the redhat source rpms. They release those for free to comply with the GPL. Just look on their public ftp server. That is where centos gets their sources to make centos.

---

### Post by Xbehave on 2009-10-12
> **Viva said:**
> Opensource is not a matter of license, but development model imo. I wouldn't consider Chrome opensource because it does not use a community-based development model. If somebody forks chrome and accepts code from the community, then the resulting browser will be opensource. It is free software though, because it gives you freedom.
Dear god **PLEASE** read the last couple of pages, what you described was cathedral vs bazaar development models and nothing to do with free software **OR** open source in their common usage. Additionally you have got the general usage of the terms backwards.
Free software (which is usually described by RMS) is more strict and generally requires the requirement to distribute source
Open Source (which is well defined [see last few pages]) is less strict but generally requires the ability to modify & redistribute the program (at a minimum this is BSD)

development of all software free software/open source/proprietary can be done using either community-based model (crowd sourcing when done fore prop code) or closed model (OpenOffice for example is Open Source but the development is fairly close to sun)

---

### Post by Dimitriid on 2009-10-12
> **EDavidBurg said:**
> Once again, you're treating OS X as a single unit. It's a more complex issue than that.

Can you build a working system without using the proprietary parts? From what I understood you would be left with a crippled, gui-less system.

---

### Post by schauerlich on 2009-10-13
> **Dimitriid said:**
> Can you build a working system without using the proprietary parts? From what I understood you would be left with a crippled, gui-less system.

By that definition, Ubuntu Server is crippled.

It's sort of like installing a *BSD base system - you don't have a whole lot, but you have enough, and you have what you need to get the rest working.

---

### Post by Dimitriid on 2009-10-13
> **stmiller said:**
> Apple does release the sources to the core 'darwin' **parts**


So part of OS-X its open source. Thats like saying my keyboard its metallic because parts of it are made from metal. Its misleading so again, a very quick way to stop bickering about is this: can you build a working system without any of the proprietary parts?

---

### Post by Dimitriid on 2009-10-13
> **EDavidBurg said:**
> By that definition, Ubuntu Server is crippled.

People can set up a server with Ubuntu server edition. OS-X sever edition might not be crippled ( if there is such a thing ) but nobody purchases an ibook to run a command line only, hence without the proprietary parts its crippled, just as windows would be without a graphical interface or Ubuntu Desktop would be without xorg.

---

### Post by schauerlich on 2009-10-13
> **Dimitriid said:**
> Thats like saying my keyboard its metallic because parts of it are made from metal.

[My keyboard](http://imgur.com/ZTaLr.jpg) is metallic.

> Its misleading so again, a very quick way to stop bickering about is this: can you build a working system without any of the proprietary parts?

Yes.

---

### Post by Dimitriid on 2009-10-13
> **EDavidBurg said:**
> 
Yes.

And its not crippled in any way? What about the GUI its open source then?

---

### Post by schauerlich on 2009-10-13
> **Dimitriid said:**
> And its not **crippled** in any way? What about the GUI its open source then?

You keep using that word. I do not think it means what you think it means.

---

### Post by Dimitriid on 2009-10-13
> **EDavidBurg said:**
> You keep using that word. I do not think it means what you think it means.
I mean this:
> crippled
 - 5 dictionary results
crip&#8901;ple
&#8194;&#8194;/&#712;kr&#618;p&#601;l/ Show Spelled Pronunciation [krip-uhl] Show IPA noun, verb, -pled, -pling, adjective
&#8211;noun
1. 	Sometimes Offensive.
a. 	a person or animal that is partially or totally unable to use one or more limbs; a lame or disabled person or animal.
b. 	a person who is disabled or impaired in any way: a mental cripple.
**2. 	anything that is impaired or flawed.**
3. 	a wounded animal, esp. one shot by a hunter.
4. 	Carpentry. any structural member shorter than usual, as a stud beneath a window sill.
5. 	Delaware Valley. a swampy, densely overgrown tract of land.
&#8211;verb (used with object)
6. 	to make a cripple of; lame.
**7. 	to disable; impair; weaken.**
&#8211;adjective
8. 	Carpentry. jack 1 (def. 27). 

---

### Post by Frak on 2009-10-13
> **Dimitriid said:**
> And its not crippled in any way? What about the GUI its open source then?
Build Gnome or KDE. If you want something free, you may have to work for it. It is, though, fully usable without a GUI.

---

### Post by Dimitriid on 2009-10-13
> **Frak said:**
> Build Gnome or KDE.

Then its not OS-X.

---

### Post by sertse on 2009-10-13
In any case, the OP has lost. The fact there is a 14 (edit 15) page thread about it means no solid proof exists, otherwise it won't be so hotly debated with. OP should admit that. End thread. 

The rest of it is your usual Mac discussion about nuances and the exact details. So time for  me to leave this thread. And if you're arguing by nuances, it means it isn't solid.

---

### Post by Frak on 2009-10-13
> **Dimitriid said:**
> Then its not OS-X.
Depends on how you want to look at it. It still has all the operating components. Can't run the same programs, but that's only because Apple adds-in snippets that makes their OS an Apple OS.

---

### Post by schauerlich on 2009-10-13
> **Dimitriid said:**
> I mean this:

It was a [Princess Bride](http://www.imdb.com/title/tt0093779/quotes) reference. 

Darwin is not crippled. It is a functional system. It's not the same type of system as OS X. It's not meant to replace OS X. It's not meant to be a graphical distribution, or even a particularly useful distribution. It was released as a binary at first, but when there was basically no interest in it, they stopped expending the effort and just put up the source. It now mostly exists as a group of FOSS projects, put together for the sake of organization. However, there is a community project to turn Darwin into a more useful system, called PureDarwin.

All of this is explained in the FAQ that I keep linking too. It's in my sig. 

I recommend you read it. If you have question or concerns, feel free to respond to the thread.

---

### Post by Dimitriid on 2009-10-13
> **EDavidBurg said:**
> It was a [Princess Bride](http://www.imdb.com/title/tt0093779/quotes) reference. 

Darwin is not crippled. It is a functional system. **It's not the same type of system as OS X.** It's not meant to replace OS X. 

Then the question is answered: OS X is not open source.

---

### Post by schauerlich on 2009-10-13
> **Dimitriid said:**
> Then the question is answered: OS X is not open source.

Here we go again...

"Open source" and "closed source" are not appropriate terms to describe an entire OS.

"Free" and "proprietary", however, are.

Mac OS X is proprietary.

However, it contains both open source and closed source components.

Darwin is a collection of those open source components, which forms a fully functional operating system.

---

### Post by Frak on 2009-10-13
> **Dimitriid said:**
> Then the question is answered: OS X is not open source.
OS X has Open Source components, such as the kernel and utilities needed to build a system.

There, it cannot be called definitely closed source, since it contains open source components.

---

### Post by KiwiNZ on 2009-10-13
This discussion could make me dizzy :P

---

### Post by jamieleshaw on 2009-10-13
> **KiwiNZ said:**
> This discussion could make me dizzy :P

I agree, I'm a little confused. :confused:

---

### Post by UltraZone on 2009-10-13
I'm confusted too... please explain it to me from the top :guitar:

---

### Post by Dimitriid on 2009-10-13
> **EDavidBurg said:**
> Here we go again...

"Open source" and "closed source" are not appropriate terms to describe an entire OS.


Yes they are, [there are systems entirely open source:]("http://www.gnewsense.org/")

If you don't want to be strict about it and use common sense, many other linux distros like Debian are open source since all mayor components and functionality is available with 100% open source software packages, drivers, kernel, etc.

---

### Post by SofaSmarties on 2009-10-13
why do you have to prove your right?
as long as you know you are (or think you are) who cares?
i had a discussion about linux and OSX.
i said they were two different operating systems that were both unix/unix-like
he said they were the EXACT same thing(why would you shell out 6 grand on a mac then?:))
but the other guy was very convinced i was wrong and he was right and there was no way in budging him in the other direction. so i just said screw it and forgot about it. did i get any where from being right?no. did he get any where for not knowing a thing he said? no. so whats the point?
I got no where with it and it was a waste of my time. and im guessing you will get no where with this one and it will also be a waste of your time.

---

### Post by schauerlich on 2009-10-13
> **Dimitriid said:**
> Yes they are, [there are systems entirely open source:]("http://www.gnewsense.org/")

If you don't want to be strict about it and use common sense, many other linux distros like Debian are open source since all mayor components and functionality is available with 100% open source software packages, drivers, kernel, etc.

There is no point in me continuing this particular tangent. It is evident that nothing productive will come of it.

---

### Post by Frak on 2009-10-13
> **Dimitriid said:**
> Yes they are, [there are systems entirely open source:]("http://www.gnewsense.org/")

If you don't want to be strict about it and use common sense, many other linux distros like Debian are open source since all mayor components and functionality is available with 100% open source software packages, drivers, kernel, etc.
Brick Wall

That is all.

I'm sorry, but everything I've said was just ignored from the get-go. It's like building a ship and all the other person wants to make sure of is that it comes with a sail, even though it has a motor.

---

### Post by sertse on 2009-10-13
> **Dimitriid said:**
> Yes they are, [there are systems entirely open source:]("http://www.gnewsense.org/")

I

Gnewsense is Free. Being the OS endorsed sponsored by the FSF, with with RMS at its helm, it regards Free to NOT be open source.

The few other posters expressing their confusion is evidence enough the OP's question can't proven with "solid proof". The rest is recurring discussions stuff.

---

### Post by Dimitriid on 2009-10-13
> **UltraZone said:**
> I'm confusted too... please explain it to me from the top :guitar:

1 ) OP presents a question: Its OS X really open source?

2 ) Several key parts to the OS are not open source according to previous posters

3 ) OS X is therefore not open source

4) People challenge that saying that there is a free version, Darwin

5 ) Darwin is not OS X, not even close

6 ) People try to discredit the original question instead of accepting the answer: OS X is not open source.

7 ) Simple, concise, logic-backed explanations are provided

8 ) Derail attempts continue

9 ) You got confused.

The question is simple: Is OS X open source? The answer its simple: No it is not, as you cannot get a working, non-crippled system that resembles OS X without the parts that are not open source.

Whenever or not open source is a narrow definition is not in question here for any purposes other than an ineffective rhetoric argument.

---

### Post by Dimitriid on 2009-10-13
> **sertse said:**
> Gnewsense is Free, ad endorsed sponsored by the FSF, which with RMS at its helm regards Free to NOT be open source.

Thus his point stands.

RMS politics are not in questions: can you get all source code for Gnewsense? The answer its yes you can, so its open source. It happens to be Free software ( with everything that implies as well ) but that is inconsequential to the fact that you are able to obtain the source code of all components in its entirety.

---

### Post by Dharmachakra on 2009-10-13
I think you should smack your friend.

---

### Post by schauerlich on 2009-10-13
> **Dharmachakra said:**
> I think you should smack your friend.

Violence is always the answer. :)

---

### Post by sertse on 2009-10-13
> **Dimitriid said:**
> 1 ) OP presents a question: Its OS X really open source?

2 ) Several key parts to the OS are not open source according to previous posters

3 ) OS X is therefore not open source

The question is simple: Is OS X open source? The answer its simple: No it is not, as you cannot get a working, non-crippled system that resembles OS X without the parts that are not open source.

Whenever or not open source is a narrow definition is not in question here for any purposes other than an ineffective rhetoric argument.

Thanks for providing your train of thought. We dispute your thinking from point 2 to point 3. You dismiss it as derailing. There having several part in the OS which is not open source, does not mean the "whole thing" is not open source. It means it lies somewhere between open source and not open source.

---

### Post by KiwiNZ on 2009-10-13
> **Dimitriid said:**
> RMS politics are not in questions: can you get all source code for Gnewsense? The answer its yes you can, so its open source. It happens to be Free software ( with everything that implies as well ) but that is inconsequential to the fact that you are able to obtain the source code of all components in its entirety.

Please tolerate the views that may differ to yours. I have removed a recent post you made that was somewhat  inflammatory.

---

### Post by Dimitriid on 2009-10-13
> **KiwiNZ said:**
> Please tolerate the views that may differ to yours. I have removed a recent post you made that was somewhat  inflammatory.

How is that inflammatory? I made no positive or negative connotation towards RMS views, I merely said that, to me, they are not in question since gnewsense source code can be obtained entirely.

---

### Post by Dimitriid on 2009-10-13
> **sertse said:**
> Thanks for providing your train of thought. We dispute your thinking from point 2 to point 3. You dismiss it as derailing. There having several part in the OS which is not open source, does not mean the "whole thing" is not open source. It means it lies somewhere between open source and not open source.

I acknowledged the gray area, and asked if a non-crippled version can be made without said points of contest, the answer I obtained was a definitive no, if you disagree and want to make the claim that Darwin its, for all intends and purposes, OS X then go ahead. We were discussing ( I believe ) that without GUI to me it really cannot be called "OS X" but only "OS X Like". 

Having an OS X Like that is open source ( Darwin ) does not makes OS X open source as well as the practical differences are too significant for me to reasonably equate Darwin to OS X.

---

### Post by sledge73 on 2009-10-13
this might help [http://freedomwareproject.org/enter/?p=29](http://freedomwareproject.org/enter/?p=29)

---

### Post by Xbehave on 2009-10-13
> **sertse said:**
> Thanks for providing your train of thought. We dispute your thinking from point 2 to point 3. You dismiss it as derailing. There having several part in the OS which is not open source, does not mean the "whole thing" is not open source. It means it lies somewhere between open source and not open source.
stop resorting to convoluted definitions to avoid defete.
OS X is what you pay apple for, what comes on the disk/ a new mac computer.
The source code for this disk is not avalible .'. it is not open source

The same logic can be used on mac os X server, is the source code for the entire disk available (and modifiable)... AFAIK NO, .'. mac os x server is not open source.
Windows...NO the source code for the entire windows xp/vista/7 you pay for is not avalible .'. it is not open source
ubuntu...Yes the entire disk you get with 1st party utilities is available 

(ubuntu It may not be all free software, seriously go back 3 pages free software = open source, and that is why gnewsense exists)

Linux & ubuntu are not well defined (so for meaningful discussion you have to define the words before continuing, and debating of meanings is something best left for lawyers)
mac os X & windows are well defined
open source is somewhere in between but generally anybody who is not trying to be difficult, will accept the definition is somewhat akin to what i posted above.

Now the only way you guys can keep this argument going (and i have no doubt you will), is by questioning my definition of open source or mac os X. Well the definition of open source i am using is that 
> the right to distribute modified versions of the program (this right does not imply the right to use the original programs name/logo/reputation)QUOTE] this is open source as described by anybody, debian through to Microsoft (including apple)

my definition of mac os X is:
[QUOTE]What you pay for when you buy mac os X
This (or some close variant) is what is defined in the EULA by the apple legal team.

---

### Post by fela on 2009-10-13
Few computer operating systems are 100% open source. I'm running a completely-closed source graphics driver for instance, otherwise my graphics card won't function, or will function with a very loud fan and no 3D.

---

