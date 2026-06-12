---
title: "what technically is so bad about Windows?"
date: 2007-03-07
forum: Windows
---

### Post by billdotson on 2007-03-07
Granted Windows usually "just works", programs are generally easy to install and uninstall and there is a wide range of hardware support and software for Windows what makes Windows so bad?
[Some problems I have noticed in Windows: isn't as easily customizable as a Linux distro, the software is mostly not free, there are the possibility of getting viruses and spyware + adware, the Windows registry is not a good idea, Windows has to be maintained by defragging harddrives, etc.]

But what makes a Linux distro or another OS a viable alternative to Windows?  What things does Windows does so poorly that would drive you to a different OS?

So overall what is really that bad about Windows and why do people bash it so often?  I use Windows XP SP2 for some things and generally it is a very stable system that requires little maintenance.  I have seen things on websites like microsuck.com that say things like the OS keeps a hidden folder of all your visited websites, etc. and all your email correspondents and stuff like that and sens it back to Microsoft but things like that seem a bit extreme and biased coming from a website called microsuck.com

Also, apart from general reasons why Windows is deemed bad what are some more technical reasons for Windows being deemed "bad".. like for instance what are things that Windows does/does not do that are inefficient or just the source code of the OS is poorly written in some way?

---

### Post by Abhi Kalyan on 2007-03-07
WOW, Thats a whole bunch of questions packed in a bomb.
I can probably tell you what i feel, The end judgement is in all probability yours to make.
"There is a huge differance betwee the architectures of these above mentioned OS's." this comment is normal, but some times people tend to put a whole lot of emphasis by making the above comment into the one below: 
"The Architectural differance between Linux and Windows is so huge that you can probably put the red sea and the artic ocean between them."

This is only a matter of perspective.

Technically we cannot even compare the architectures in most of its individual layers.

Conceptually There are loads of holes in windows whihc need thirdpary seals. You cannot do anything about it cause there is nothing else one can do.
So you pay for the holes and also pay for the seals.

In linux you have holes, But with knowledge you could seal them yourselves. Hence you are in control of the OS and not Viceversa.

A very big reason why some feel linux is far better than windows is because of the "Monopoly" of windows. As is sometimes true Competetion alone brings out the best.

If windows were far better, why does it have to borrow ideas from the opensource community?

Why create propratory wares if you believe in democracy?

Pleas post your views.
Lets Talk

---

### Post by tenn on 2007-03-07
Really I think if you yourself cant see a problem with Microsoft made OS's than there is no point people trying to point out what they think is wrong with it.
I think all the Open source programmers out there are far better at there job than MS.

---

### Post by Quillz on 2007-03-07
From a technical standpoint, the Registry is really not such a great idea. It creates a single point of error. If something goes wrong there, your entire system may be compromised. While there are some advantages to a centralized concept like the Registry, the negatives outweigh the positives, I think.

---

### Post by Trebuchet on 2007-03-07
The problem comes largely because different people have different ideas about what constitutes "better." Windows' ubiquitousness is seen as an advantage by many simply because it means getting computer help from a friend/neighbor/co-worker is easy. For people uninterested in customization, ease of customization is a non-issue. Programs to do almost anything are available for Windows. Even things that are seen as annoyances by many in the Linux community, such as using anti-virus/anti-malware programs, aren't seen by many Windows users as a flaw in Windows but rather as just the cost of doing business. It's as routine as buying gas and changing the oil in a car.

If "better" were alway the same for everyone, Linux would have only one distro instead of being as fragmented as protestant churches.

---

### Post by moore.bryan on 2007-03-07
*for many, the simple philosophy of open vs. closed source is enough of a persuader.  as for particulars both affirmative and negative points about windows, i can only speak to my own experiences.  since going completely ubuntu, my computer has only ever worked... not a single problem with anything.  i can't say the same thing about my long-time windows experience...*

---

### Post by karellen on 2007-03-07
technically speaking....I think the most important it's the kernel architecture. linux has a monolithic kernel, windows (nt,xp,vista) has a hybrid kernel. and there are a lot of differences between these two concepts.
see more here:
[http://en.wikipedia.org/wiki/Monolithic_kernel]("http://en.wikipedia.org/wiki/Monolithic_kernel")
[http://en.wikipedia.org/wiki/Hybrid_kernel]("http://en.wikipedia.org/wiki/Hybrid_kernel")

---

### Post by billdotson on 2007-03-07
so in very simple terms.. 

*nix OSes and others with monolithic kernels have ALL the drivers, etc. needed to run any necessary hardware in the kernel along with what is needed to communicate with the processor and do memory management, etc.--- so I am guessing that is the reason why you don't have to install drivers for hardware..

Windows and other OSes that use a "hybrid kernel" (if there are others other than Windows) have all the necessary things to communicate w/ the processor and do memory management, etc. along with the drivers for basic hardware services like USB and firewire, whereas things like the nVidia driver are required to be installed.

Haiku OS, BeOS and those that use the microkernel have to be wary of how they do the IPC stuff because if it isn't done right there will be a major performance hit.  Since all the driver's and  memory management, etc. are run in user-mode servers (just programs really..?) If malicious code finds a hole in one of those servers the entire kernel doesn't crash only that single server.

While I feel that I am pretty good with computers I do not and do not claim to know the deep down technical way that many things work in computers so the explanations of the how these OSes work and how the kernels work are difficult for me. 
In simple terms what are the disadvantages + advantages of the microkernel, monolithic kernel, "hyrbid kernel"??

I am currently starting to learn a variety of different things with computers like how to program, etc. and I a currently a novice in areas as advanced as this.

Thank you

---

### Post by karellen on 2007-03-07
Since the operating system provides an hardware abstraction layer, and since it must provide resource sharing, every access to the hardware from user programs should be done through the operating system. To enforce this in a secure way, and prevent malicious or buggy applications to mess up with the hardware, a protection is needed at the hardware level.

Hardware must provide at least two execution levels:

Kernel mode
    In this mode, the software has access to all the instructions and every piece of hardware. 
User mode
    In this mode, the software is restricted and cannot execute some instructions, and is denied access to some hardware (like some area of the main memory, or direct access to the IDE bus). 

So, we define two spaces at software level:

Kernel space
    Code running in the kernel mode is said to be inside the kernel space. 
User space
    Every other programs, running in user mode, is said to be in user space. 

Monolithic kernel based systems

This is the traditional design of Unix systems. Every part which is to be accessed by most programs which cannot be put in a library is in the kernel space:

    * Device drivers
    * Scheduler
    * Memory handling
    * File systems
    * Network stacks

Many system calls are provided to applications (more than 250 for Linux 2.4), to allow them to access all those services.

This design has several flaws and limitations:

    * Coding in kernel space is hard, since you cannot use common libraries (like a full-featured libc), debugging is harder (it's hard to use a source-level debugger like gdb), rebooting the computer is often needed, ... Remember this is not just a problem of convenience to the developer : as debugging is harder, as difficulties are stronger, it is likely that code is ``buggier''.
    * Bugs in one part of the kernel have strong side effects, since every function in the kernel has all the privileges, a bug in one function can corrupt data structure of another, totally unrelated part of the kernel, or of any running program.
    * Kernels often become very huge (more than 100 MB of source code for Linux 2.6), and difficult to maintain.
    * The presence of strong side effects makes the whole kernel less modular (remember the VM issues of Linux 2.4, some people suggested to make the VM modular, allowing the system administrator to chose one VM at compile time, but the impact of the VM over the other parts of the code was so huge that the idea was dropped). And since kernel code runs with all the privileges at hardware level, only the system administrator can be allowed to load a module inside the kernel space.

Micro-kernel based systems

Principles

Only parts which really require to be in a privileged mode are in kernel space :

    * IPC (Inter-Process Communication, see below)
    * Basic scheduler, or scheduling primitives
    * Basic memory handling
    * Basic I/O primitives

Many critical parts are now running in user space :

    * The complete scheduler
    * Memory handling
    * File systems
    * Network stacks

That reminds me of the famous flame-war between Andy Tanenbaum and Linus Torvalds regarding monolithic kernels/micro-kernels :)...

---

### Post by billdotson on 2007-03-07
so are monolithic kernels faster but harder to maintain, while microkernels are a bit slower and easier to maintain?

or are there noticeable, and practical differences between the two that I do not have enough knowledge to totally understand at the moment?

---

### Post by Bragador on 2007-03-07
Personally I'd say the quality/price ration is bad.

Also with vista, you have that extra DRM problem.

---

### Post by karellen on 2007-03-07
imo monolithic kernels are more reliabe and robust :)

---

### Post by Yossarian on 2007-03-07
I heard the Windows kernel was actually not bad, and was not responsible for Windows' problems.

Here's a few things I can think of:

Windows' memory management is sort of flakey, which is why performance sucks after long uptimes. 

Windows uses a pretty old filesystem (NTFS) that will often store bits of files everywhere, causing your disk to become fragmented.   

Windows allows any type of file to run as a program, so long as it has .exe at the end of its name.  This makes social engineering easier as you can just trick someone into clicking what they think is a photo, and it will actually run a program.  Unix forces you to make a file executable with chmod first.

Windows' software installer is sloppy.  Most programs provide their own install and uninstall programs, which will sometimes leave junk behind after you uninstall.  Contrast this with APT, which uses one program to uninstall, upgrade, and remove everything.  This isn't entirely Windows' fault, just that alot of Windows developers are sloppy.  I think there is some sort of Windows installer built in, it just in general isn't used as well as it should.

Internet Explorer is an awful browser, and they made it impossible to uninstall.  Its feature-poor and full of holes, and it used to run inside the kernel, although it might not be anymore.  Probably the worst problem with Windows.  Same goes for Outlook Express/ Windows Mail.

Windows is high maintainence.  Performance degrades over time.  Back in the Windows 98 era, gamers I knew used to reinstall over six to twelve months to get the best performance. XP isn't nearly as bad, though.

---

### Post by NotPhil on 2007-03-07
> **billdotson said:**
> ... What things does Windows does so poorly that would drive you to a different OS?... what is really that bad about Windows and why do people bash it so often?
MS Windows certainly has its fans, but there are many valid reasons to dislike it. Most of them boil down to Microsoft's policies and Microsoft's coding.

You can see how Microsoft's policies affect other software developers, computer manufacturers, and computer users by looking at the legal complaints made against MS, and the courts' findings of facts in those cases. Generally, MS is so frightened of any sort of competition that it bullies equipment manufacturers in attempts to prevent them from installing other OSes on their products, tries to weld its own application software (like audio-video players and Web browsers) onto its OS, to discourage consumers from choosing other applications, hides some of Windows' programming interfaces from other software developers, making it difficult for them to write applications for MS Windows, and now, with Vista, its DRM policies are also making it difficult for its customers to install the software, or play the audio-video files, they want to use on MS Windows. And the price of Windows for consumers is pretty silly. Some versions cost as much as the computers it runs on.

And Microsoft's code is surprisingly bulky. General estimates put it at almost half-a-dozen times larger than comparable code. Bloated source code means serious code-maintenance and code-revision problems, and this means bugs and security problems. Windows may not crash and freeze as often as it did in the past, but it still has a lot of problems that affect programmers and users. I know people who are frightened to change any of their personal settings in Windows because doing so has caused things to break, Windows has a very bad track record with backwards compatibility, and, as we all know, Windows has severe problems with computer security.

Of course, if some people like Windows, then some people like it. Good for them. The biggest problem with Windows is that those of us who don't like it have to go to extreme lengths to find and install something else. The reason Linux and OS X and BSD and other OSes aren't popular isn't because they're bad OSes, it's because Microsoft has a stranglehold on the personal computing market.

---

### Post by Trebuchet on 2007-03-07
> **Yossarian said:**
> Internet Explorer is an awful browser, and they made it impossible to uninstall.  Its feature-poor and full of holes, and it used to run inside the kernel, although it might not be anymore.  Probably the worst problem with Windows.  Same goes for Outlook Express/ Windows Mail.Internet Explorer 7 is a HUGE improvement over IE6 and previous versions. Had IE6 not already made me a Firefox fan, I'd be quite content to use IE7 as my browser (I didn't like Opera 9 at all). The only thing I use IE7 for now is manual Windows Update; which won't use other browsers. (Most of my Windows Updates are automatic; which don't require a browser anyway.) IE7 in Vista runs on a restricted mode (sandbox) which can no longer write to system files. It doesn't have that feature in the XP version.

Haven't tried Windows Mail yet, but my needs for a mail app are minimal. I prefer something very basic without bells and whistles of any kind; and didn't even like Thunderbird much. (I'm getting ready to try the Windows version of Evolution.)

---

### Post by Yossarian on 2007-03-07
> Originally posted by **Trebuchet**
Internet Explorer 7 is a HUGE improvement over IE6 and previous versions. Had IE6 not already made me a Firefox fan, I'd be quite content to use IE7 as my browser (I didn't like Opera 9 at all). The only thing I use IE7 for now is manual Windows Update; which won't use other browsers. (Most of my Windows Updates are automatic; which don't require a browser anyway.) IE7 in Vista runs on a restricted mode (sandbox) which can no longer write to system files. It doesn't have that feature in the XP version.

Haven't tried Windows Mail yet, but my needs for a mail app are minimal. I prefer something very basic without bells and whistles of any kind; and didn't even like Thunderbird much. (I'm getting ready to try the Windows version of Evolution.)

IE7 is better, and the sandbox is a good idea.  I was thinking of setting something up something similar on either XP or Ubuntu by making a seperate user account to browser with, and then running it with gksu -u or a scripted Run as or something.  Just for an extra layer of paranoia.

---

### Post by Trebuchet on 2007-03-07
> **Yossarian said:**
> IE7 is better, and the sandbox is a good idea.  I was thinking of setting something up something similar on either XP or Ubuntu by making a seperate user account to browser with, and then running it with gksu -u or a scripted Run as or something.  Just for an extra layer of paranoia.Not that I'm knocking paranoia (I've been accused of that myself a few times), but do you really visit websites you consider that dangerous even though you're using Linux? I mean, IE6 was full of gaping security holes but it appears IE7 is as good or possibly better than Firefox for security, at least when run in Windows.

---

### Post by some_random_noob on 2007-03-07
I haven't read anyones posts, but for me I was driven away by the way they treat customers. The technical side is bad, but not as bad as their business practises.

---

### Post by billdotson on 2007-03-07
wow.. Internet Explorer used to be tied directly into the kernel.. what a horrible idea!! even if IE is used for system updates that is a horribly bad idea!  Also code that is bulky especially in the kernel is not a good thing because as it has been stated there are bound to be bugs in it the more it has in it.

---

### Post by karellen on 2007-03-08
> **some_random_noob said:**
> I haven't read anyones posts, but for me I was driven away by the way they treat customers. The technical side is bad, but not as bad as their business practises.
agree with this ;)

---

### Post by mahy on 2007-03-08
Technically speaking, the kernel is not the major problem. There are other problems to worry about: IE entrenched deep in the system (and performing updates), susceptibility to viruses and spyware, filesystem fragmentation, stupid user rights policy, windows registry, and so on. I know many things improved with Vista, but it's still far from being on par with Linux.

---

### Post by 3rdalbum on 2007-03-08
> **billdotson said:**
> Granted Windows usually "just works", programs are generally easy to install and uninstall and there is a wide range of hardware support and software for Windows what makes Windows so bad?

1. Windows "just works" (although it doesn't really) because when you buy a computer, it is already preloaded with all the drivers for the hardware in the computer. In fact, it's already preloaded on the computer. This is nothing to do with Microsoft - it's done by OEMs (Own Equipment Manufacturers).

2. Programs being easy to install is nothing to do with Windows, and everything to do with application developers. People distributing programs for Linux could distribute Autopackages, for example, for all their programs. Windows only being available for one platform DOES help a bit, as one would never have to distribute source as the "lowest common denominator" that will run on all machines, but this is inconsequential really. And it's a downside of Windows.

3. There is only a wide range of hardware support because of 3rd-party manufacturers.

So basically, the three things you cite as being good things about Windows, are actually nothing to do with Microsoft.

---

### Post by Yossarian on 2007-03-08
> Originally posted by **3rdalbum**
1. Windows "just works" (although it doesn't really) because when you buy a computer, it is already preloaded with all the drivers for the hardware in the computer. In fact, it's already preloaded on the computer. This is nothing to do with Microsoft - it's done by OEMs (Own Equipment Manufacturers).

2. Programs being easy to install is nothing to do with Windows, and everything to do with application developers. People distributing programs for Linux could distribute Autopackages, for example, for all their programs. Windows only being available for one platform DOES help a bit, as one would never have to distribute source as the "lowest common denominator" that will run on all machines, but this is inconsequential really. And it's a downside of Windows.

3. There is only a wide range of hardware support because of 3rd-party manufacturers.

So basically, the three things you cite as being good things about Windows, are actually nothing to do with Microsoft.

More or less true, but its not at all refuting what Trebuchet said.  I think the discussion was on Windows', and not Microsoft's, merits.

---

### Post by billdotson on 2007-03-08
yes that is true.

If you take all that then yes.  But what drivers exactly are included in the OEM process?  I built my own and the local university put XP on my system so I have not actually gone through the driver process of Windows.  As far as I am aware the only drivers I need to install are automatically installed when I plug a device like an external drive or something.  Although with a videocard or a TV tuner or something like that you have to install a driver.

Although I wonder.. if Windows wasn't such a big target and the market was split 33-33-33 with Mac OS X, Windows and Linux would Linux and OS X get viruses and spyware?

btw Microsoft.. you know if there was a more even playing field for the home desktop you could spend more time on other things than combating viruses, spyware and adware..

---

### Post by NotPhil on 2007-03-08
> **billdotson said:**
> ... I wonder.. if Windows wasn't such a big target and the market was split 33-33-33 with Mac OS X, Windows and Linux would Linux and OS X get viruses and spyware?Probably, but there are reasons to believe the problem wouldn't be as severe with Linux and OS X. Both of those OSes are better designed, and in Linux' case, there are piles of hobbyists going over the source code just looking for bugs and loopholes to patch. OS X has an open source core, in Darwin, but I don't know how many hobbyists are checking its code. Still, it's based on BSD, which is, reputedly, even sturdier than Linux.

---

### Post by Trebuchet on 2007-03-08
> **3rdalbum said:**
> 1. Windows "just works" (although it doesn't really) because when you buy a computer, it is already preloaded with all the drivers for the hardware in the computer. In fact, it's already preloaded on the computer. This is nothing to do with Microsoft - it's done by OEMs (Own Equipment Manufacturers).

2. Programs being easy to install is nothing to do with Windows, and everything to do with application developers. People distributing programs for Linux could distribute Autopackages, for example, for all their programs. Windows only being available for one platform DOES help a bit, as one would never have to distribute source as the "lowest common denominator" that will run on all machines, but this is inconsequential really. And it's a downside of Windows.

3. There is only a wide range of hardware support because of 3rd-party manufacturers.

So basically, the three things you cite as being good things about Windows, are actually nothing to do with Microsoft.Those apply to the usability of Windows as an OS, not to its technical merits. Linux similarly takes negatives for things having to do with hardware, peripherals, and software that are certainly not the fault of Linux's programmers. It's certainly not their fault mainstream manufacturers are not writing drivers and software for Linux. Similarly, if someone has to use a particular Windows-compatible program for their work and that program is simply not available for Linux, then in that particular instance Linux is not as "good" as Windows. It does not mean that objectively Linux is not superior to Windows in any number of other ways.

---

### Post by Popoi on 2007-03-09
Windows is bad in everything these folks say. But one thing is good to appreciate, Direct X. OpenGL is far from Direct X drivers...

I think. I'm a bit ignorant, ok let's teach me if you want.

---

### Post by M$LOL on 2007-03-09
IMO, the Windows architecture is fatally flawed, and should have been revamped after NT4.0.

Windows is plain and simple inferior to Linux/Windows, and what annoys me is that M$ push their OS onto everyone's desktop despite it being, at best, a poorly built OS.

---

### Post by cunawarit on 2007-03-10
> **Quillz said:**
> From a technical standpoint, the Registry is really not such a great idea. It creates a single point of error. If something goes wrong there, your entire system may be compromised. While there are some advantages to a centralized concept like the Registry, the negatives outweigh the positives, I think.

The other problem is that you need the registry editor to change anything in it. You can't simply boot to the command line and edit it like you could with normal text settings files.

---

### Post by elst on 2007-03-10
The way that Linux distributions manage software gives them a lot of technical advantages over Windows. The entire system is built by the package management system (APT for Ubuntu) during installation. This means that APT can track and manage every file right from the start, to build or rebuild systems to any given configuration that the vendor or the network administrator wants, as well as safely adding individual pieces of new software. This makes it very easy to create customized varients from a single pool of packages, update or swap out specific components without affecting others, and upgrade systems to new versions. 

In contrast, Windows is a vast pile of files, many of which have been inherited from previous versions. This makes it much more difficult for Microsoft developers to safely make changes, which is one of the reasons why MS takes so long to both create new software and sometimes even issue working security updates. Vista development collapsed and had to be restarted because MS didn't have a mechanism that could efficiently track and integrate all of the components of the system that were being changed. There is talk of making Windows more modular, but the only way for Microsoft to get the manageability and rapid development of a Linux distribution now is for them to develop the equivalent of APT, and then spend many man-years reshaping Windows and their other applications into packageable components.

---

### Post by Trebuchet on 2007-03-10
I think you're right on here. It's time for Microsoft to abandon the DOS/NT lineage and move to a *nix kernel. It's the only way they'll be able to trim out all that old baggage and bring Windows into the 21st century. If they need to run old software, they can include a VM or emulator.

---

### Post by steveneddy on 2007-03-11
:-s

---

### Post by pennyminstrel on 2007-03-14
I'm not a techie and I don't understand all that stuff too well, but having started using Ubuntu on a dual boot about 6 months ago, I only occasionally boot into windows now if I want to do something quickly that I haven't yet discovered how to do in Linux, and when I do I drives me mad with it's temperamental behaviour. Same PC, all the settings set to work to the optimum and its not clogged up with masses of old files cos I hardly use it.

So I don't know what it is but there must be something working better in LInux.

---

### Post by rs3 on 2007-03-15
Frankly, I dare ask just what *isn't* "so bad" about Windows.  But this entire thread and many like it have all been done a hundred times before.

I resent having my computer taken away from me--and paying for such a service, no less.  I see Vista (in all its DRM-laden glory) as a very troubling sign of things to come, and though I've few issues with Windows XP, I can't sit idly by and wait for another myriad of updates to trickle through and quietly liberate me further of my freedoms.

Or maybe I just sound ridiculous and paranoid. :)  Moving on...

I'll be frank.  I've never, personally, had any issues with malware or viruses.  I've used Windows since 3.1 on a 386sx/16, and I was very impressed with XP upon its release.  But I've helped parents, friends, and family members through numerous Windows tribulations and I've seen what careless/casual computer use can do to the Windows operating system.

The (sad?) truth is that a vast majority of Windows users are unconcerned with the inner workings of a computer, are blissfully unaware of their operating system alternatives, and equate poor OS performance with dysfunctional or underpowered hardware.  Windows is an operating system built for pedestrian consumption, replete with all the dumbing down and obscurity necessary to guarantee a foothold in the OS market with each passing upgrade.

Why else would casual computer users--those looking to browse, compose mail, hit YouTube now and again, and catalogue music for their iPod or what-have-you--be at all compelled to shell out for another operating system and the hardware necessary to support it?  It is the squandering, the perpetuating ignorance, and the lack of true ownership that Windows fosters that I consider "so bad."

Other issues to consider: the fallacious notion of security-through-obscurity, the extent-less and self-destructive file system (though I am told NTFS can handle extents or something roughly equivalent to it, if with some registry tweaks), the EULA and its many trappings (among them, my inability to install my legal copy of XP SP2 after a "significant" hardware change to the very same computer on which it was once installed), and msstyles.  Hey, I like to be able to theme my desktop environment without having to patch uxtheme.dll or buy some third-party product...

Sorry for the verbosity.

---

### Post by Trebuchet on 2007-03-15
> **rs3 said:**
> The (sad?) truth is that a vast majority of Windows users are unconcerned with the inner workings of a computer, are blissfully unaware of their operating system alternatives, and equate poor OS performance with dysfunctional or underpowered hardware.  Windows is an operating system built for pedestrian consumption, replete with all the dumbing down and obscurity necessary to guarantee a foothold in the OS market with each passing upgrade.Most of the world's people are unconcerned, pedestrian, dumbed down, and blissfully unaware of much of anything which doesn't impact them directly.

I'm sometimes afraid that in order to go mainstream, Linux will have to increase its appeal to that audience. My suspicion is that if Linux were adopted *en masse* by the world's computer users, many of the hardcore Linux faithful would migrate to another OS. Who wants to be using the same OS as the moron next door? How would you feel elite anymore?

For some, Linux is a superior tool. For others, it's a religion.

---

### Post by billdotson on 2007-03-15
I would hardly see Linux as a religion, but I see it as a powerful OS that is very capable.  If everyone moved to Linux en masse I wouldn't mind.. I would be there to help.  That is for a fee of course.. but only if masses of people came to me everyday for help.  A few friends and family here and there.. nah.

---

### Post by Condoulo on 2007-03-15
Ok, well the way I see it, each OS has their up-sides, and their down sides. 

Linux is good when it comes to security, free software, and quite a lot of other things.

Macs also are good for quite a few things, but in my opinion, most notable for video editing.

Windows in my opinion, would be good for a business that has to use Windows-Only applications with no alternative (Sadly, there are business programs like that), or gaming. I mean thats why the xbox is so good, Microsoft systems tend to be good gaming Machines if you have the correct hardware.

---

### Post by Trebuchet on 2007-03-15
> **billdotson said:**
> I would hardly see Linux as a religion, but I see it as a powerful OS that is very capable.  If everyone moved to Linux en masse I wouldn't mind.. I would be there to help.  That is for a fee of course.. but only if masses of people came to me everyday for help.  A few friends and family here and there.. nah.There are Linux websites which spend more time bashing Windows/Microsoft than discussing Linux. That may not be religion, but it's pretty close.

---

### Post by rs3 on 2007-03-15
> **Trebuchet said:**
> There are Linux websites which spend more time bashing Windows/Microsoft than discussing Linux. That may not be religion, but it's pretty close.

Regardless of whatever you believe or advocate, such immature zeal (bashing the Other OS) serves no constructive purpose (except, perhaps, to ward off potential converts in disgust).  Indeed, it's pretty close.

> I'm sometimes afraid that in order to go mainstream, Linux will have to increase its appeal to that audience. My suspicion is that if Linux were adopted en masse by the world's computer users, many of the hardcore Linux faithful would migrate to another OS. Who wants to be using the same OS as the moron next door? How would you feel elite anymore?

I question the idea that "Linux" has to do anything of the sort in the name of market share.  It's a vague notion that assumes an entire kernel and all the distributions built upon it must be "dumbed down" for the Windows-using public.  Already, we have numerous distributions (such as the one with which this forum is primarily concerned) marketed toward the casual user, and the only barriers to ease-of-use have little to do with mass-market appeal and virtually everything to do with hardware and software vendor lock-in.

Nonetheless, "Linux" will always be collectively comprised of numerous distributions, and some will suit the elite comfortably, whereas others will cater to casual use.  And maybe the hipsters looking to be "elite" will simply push on to a BSD or Solaris variant--or whatever else is relatively obscure and challenging.

---

### Post by Trebuchet on 2007-03-15
> **rs3 said:**
> I question the idea that "Linux" has to do anything of the sort in the name of market share.  It's a vague notion that assumes an entire kernel and all the distributions built upon it must be "dumbed down" for the Windows-using public.  Already, we have numerous distributions (such as the one with which this forum is primarily concerned) marketed toward the casual user, and the only barriers to ease-of-use have little to do with mass-market appeal and virtually everything to do with hardware and software vendor lock-in.I rather like the multiple options Linux distros provides; there's something for everyone. But I'm not sure that supposed strength isn't one of its greatest weaknesses. The multiple distros make it hard to speak with a unified voice within the personal computing community, and also confuses interested non-users who hear apparently contradictory things like "Linux doesn't need a GUI at all" and "Linux's GUI is much better than Windows'" and both can be true. Decrying the fact that Windows is "dumbed down" is ignoring the fact that being dumbed down is one of its biggest selling points. Windows is perceived as relatively easy by the average computer user. Linux is still seen as an OS for geeks.

> Nonetheless, "Linux" will always be collectively comprised of numerous distributions, and some will suit the elite comfortably, whereas others will cater to casual use.  And maybe the hipsters looking to be "elite" will simply push on to a BSD or Solaris variant--or whatever else is relatively obscure and challenging.Some computer users simply prefer the road less traveled. I have to suspect that, were Linux to suddenly become as dominant as Windows is now, some of those types would be looking elsewhere.

---

### Post by rs3 on 2007-03-16
> **Trebuchet said:**
> Decrying the fact that Windows is "dumbed down" is ignoring the fact that being dumbed down is one of its biggest selling points. Windows is perceived as relatively easy by the average computer user. Linux is still seen as an OS for geeks.

Given that I fall into the latter camp (geek) I find that I'm failing to appreciate the casual user viewpoint on this matter accurately, if at all, and I realize I'm only repeating the very things I started to say.  My bad.

But!  If any distribution stands a chance of being a strong voice in the Linux community and attracting non-users to conversion, it's Ubuntu.  Unification is not going to happen in the case of Linux-based operating systems, and it's a double-edged sword, as you pointed out; the best hope Linux (collectively) has of attaining significant market share is through the presence of one friendly, well-supported distribution such as this, and, in time, I hope it is instrumental in exploding the stigma of FUD and impersonal geek culture surrounding the Linux name.

After all, the default Ubuntu desktop couldn't get much easier to use.  It's just a matter of perception and a few stumbling blocks that impede non-users (prior knowledge of another operating system getting in the way, for example) from outright acceptance...isn't it?

Maybe I'm too idealistic. :D

---

### Post by Trebuchet on 2007-03-16
I pretty much agree with all of that. Ubuntu is a very attractive distro and has excellent support; it was the friendliness of these forums that made me decide to try Ubuntu rather than go back with the distro I'd tried previously, SuSE. My only difference with many Linux fans is that I don't consider Windows XP to be a terrible OS or Bill Gates to sit at the left hand of Satan. I'm fairly happy with XP, but I like to learn new things and learning a new OS is interesting. I like Linux and hope it succeeds; I just don't think it's for everyone at this point in time.

I'd consider myself a mere pseudo-geek. I built my own system, overclock my CPU, have enough cooling fans that my tower sounds like a jet on the taxiway, tinker with the Windows registry on occasion, and have played around with Linux.

---

### Post by 23meg on 2007-03-16
[QUOTE=Trebuchet]I just don't think it's for everyone at this point in time.[/QUOTE]

Just out of curiosity, do you think *any* OS will be "for everyone" at any point in time?

---

### Post by Lord Illidan on 2007-03-16
> **23meg said:**
> Just out of curiosity, do you think *any* OS will be "for everyone" at any point in time?

If I had to chose one, it would be Linux. It's so versatile that it can run on anything from a supercomputer to a wristwatch....

---

### Post by nocturn on 2007-03-16
> **billdotson said:**
> Granted Windows usually "just works", programs are generally easy to install and uninstall and there is a wide range of hardware support and software for Windows what makes Windows so bad?
[Some problems I have noticed in Windows: isn't as easily customizable as a Linux distro, the software is mostly not free, there are the possibility of getting viruses and spyware + adware, the Windows registry is not a good idea, Windows has to be maintained by defragging harddrives, etc.]

But what makes a Linux distro or another OS a viable alternative to Windows?  What things does Windows does so poorly that would drive you to a different OS?

So overall what is really that bad about Windows and why do people bash it so often?  I use Windows XP SP2 for some things and generally it is a very stable system that requires little maintenance.  I have seen things on websites like microsuck.com that say things like the OS keeps a hidden folder of all your visited websites, etc. and all your email correspondents and stuff like that and sens it back to Microsoft but things like that seem a bit extreme and biased coming from a website called microsuck.com

Also, apart from general reasons why Windows is deemed bad what are some more technical reasons for Windows being deemed "bad".. like for instance what are things that Windows does/does not do that are inefficient or just the source code of the OS is poorly written in some way?

Technically, Windows is unstable (XP does fairly well but still not good compared to Unix-likes) and insecure.
It is very expensive software that is not of a hight quality (specially judging the price).

Secondly, Microsoft does not repect your privacy.  Windows does not copy your mails to microsoft.com, but the hidden folder (copy of IE history and cache) is true.
In addition, product activiation and WGA do send back a lot of data that MS does not need, even if you refuse to share that information: [http://nocturn.vsbnet.be/?q=node/31](http://nocturn.vsbnet.be/?q=node/31)

Next to that, Microsoft has more convitions on its record then an entire crime gang, ranging from copyright violations to the anti-trust violations.  Basicly, they are a neighbourhood bully.

---

### Post by nocturn on 2007-03-16
> **3rdalbum said:**
> 1. Windows "just works" (although it doesn't really) because when you buy a computer, it is already preloaded with all the drivers for the hardware in the computer. In fact, it's already preloaded on the computer. This is nothing to do with Microsoft - it's done by OEMs (Own Equipment Manufacturers).


Indeed, and my newly devilverd preinstalled DELL computer crashed 2 hours after arriving.  It took me 2 days to get XP to fully boot again.

An Edgy install (dual boot) on this machine took 20 minutes and it has not crashed 1 single time.

---

### Post by Trebuchet on 2007-03-16
> **23meg said:**
> Just out of curiosity, do you think *any* OS will be "for everyone" at any point in time?Technically, no. But for all practical purposes Windows already is used by everybody. Those using Macs or Linux are just deviants. ;)

More seriously, it's pretty clear that OSs are converging in function on desktops. Windows is becoming more OS X or Linux-like underneath; Linux is looking more and more like Windows on the surface. I suspect the differences are going to be minimal in the not real distant future. Of course, that won't make OS wars any less heated. Continents will be laid waste over the ideal desktop or the best resolution for icons. :D

---

### Post by elst on 2007-03-16
Most people are Linux users already - Google, Amazon, and probably their ISP and mail provider all deliver services with Open Source software on top of a Linux kernel. From that perspective, Windows is just the software that your current terminal device (the PC) runs. 

I'd agree with Trebuchet that the desktop OSes are converging - they are all trying to do  basically similar things with PC form factor machines. Linux is adaptable to more specialized devices, whilst Windows NT (XP/2003/Vista) is effectively "stuck" on only running on generously-equipped Intel-compatible PCs, which makes it of decreasing value. Attempts to shoehorn Windows to fit thin client computing and virtual machines don't quite work. And you can't run standard Windows at all on handhelds, industrial mini-PCs, or embedded systems... I'd bet that regular consumers won't consciously ditch Windows as such - they and their employers will just buy more services and appliances that happen not to run Windows code.

---

### Post by billdotson on 2007-03-16
So about the hidden folder that keeps a copy of all IE history and cache.. that is true?  There surely isn't a copy of all your emails in some hidden folder when you use Outlook is there??

I agree w/ Trebuchet.. I do not hate Windows.. although in the first few weeks I used Ubuntu I did bash Windows often.  I guess I would consider myself a pseudo-geek as I do not have the stereotypical appearance of a geek but I really like to tinker w/ computers and computer-related things.  My continuing goal is pretty much to keep learning as much about computers as I can.. even after I get my Bachelor's degree in CS.  

When i get my PC put back together I will be trying PC-BSD, Dreamlinux, Zenwalk Linux, NexentaOS, OpenSolaris, Gentoo 2007 (when it is released), and Haiku OS (when it is released).  

Linux just seemed like something cool to try and an opportunity to learn a lot/something new. After I started using Ubuntu I started to want to learn programming, and other technical things related to computers.

While I think that Linux distros, especially Ubuntu are superior to Windows in most cases.. (mostly because they are free, but also some other things like being able to customize icons, etc.) I do not hate Windows.. I use it and it works fine for me because I do the maintenance to keep it secure.  One of the biggest things why I like Ubuntu is the community forums.. I can always seem to get an answer to anything I am having problems w/ and sometimes even issues w/ Windows.

---

### Post by Trebuchet on 2007-03-16
> **elst said:**
> Most people are Linux users already - Google, Amazon, and probably their ISP and mail provider all deliver services with Open Source software on top of a Linux kernel. From that perspective, Windows is just the software that your current terminal device (the PC) runs.True, but we're really discussing desktops here. Expansion of Linux in the server field is mostly coming at the expense of Unix, not Windows.

> I'd agree with Trebuchet that the desktop OSes are converging - they are all trying to do  basically similar things with PC form factor machines. Linux is adaptable to more specialized devices, whilst Windows NT (XP/2003/Vista) is effectively "stuck" on only running on generously-equipped Intel-compatible PCs, which makes it of decreasing value. Attempts to shoehorn Windows to fit thin client computing and virtual machines don't quite work. And you can't run standard Windows at all on handhelds, industrial mini-PCs, or embedded systems... I'd bet that regular consumers won't consciously ditch Windows as such - they and their employers will just buy more services and appliances that happen not to run Windows code.All of those are things that will make Linux more attractive to servers and other specialized uses, not the desktop. For Linux to supplant Windows with average consumers, it's essentially going to have to do everything Windows does. Ultimately, it means Linux in some form is either going to have to run Windows games or come up with a HALO-like "must have" game exclusive to Linux.

I do think you're right that Linux will first expand into businesses as a desktop OS. Employers will like the idea of a secure, stable OS which employees won't be able to muck up easily (thus reducing IT expenses; which is probably a bigger expense than purchasing even Windows).

---

### Post by elst on 2007-03-16
> **Trebuchet said:**
> All of those are things that will make Linux more attractive to servers and other specialized uses, not the desktop. For Linux to supplant Windows with average consumers, it's essentially going to have to do everything Windows does.

I was really just arguing that PCs are only one way of delivering and accessing various services that make up what we think of as the desktop, and they are not particularly cost-effective or good at any individual job. People often buy other devices for facilities that they really care about, especially now that electronics are comparitively cheap. Those devices tend not to be Windows-based, and often couldn't be. Here in the UK, Windows PCs seem to be losing out as gaming devices to consoles and handhelds. By pushing the Xbox and the associated network services, MS are themselves reducing the value of Windows PCs as games machines.

So I don't see PCs running Linux wholly displacing PCs running Windows, as much as PCs generally being slowly displaced by various other kinds of computer, many of which will run Linux-based operating systems. From that point of view, one of these operating systems has a future, and the other does not ;-).

---

### Post by nenyalorien on 2007-04-18
[COLOR="DarkRed"]the fact that the risk of losing my data more than doubles on Windows as opposed to any other OS based on Unix is keeping me away from that curse of a company. aside from M$ Word and Encarta, i don't think i've ever really liked working in Windows all that much. with my experience of meltdowns happening within months of a fresh install, using Window$ is getting to be much too much of a hassle already. i don't think i can afford to lose my sanity simply because of a shabbily-written OS. :evil: [/COLOR]

---

### Post by Jhongy on 2007-04-20
Some of the technical arguments are a little hypocritical. We vilify the windows registry for being "all in one place", "one error could bring down the system", and in the next breath sing the praises of a momolithic kernel!

I think these technical arguments are besides the point. I've just posted about this in a similar thread, but in short:

- Windows and the software ecosystem around it can't be trusted, and they don't trust you.
- Open source software is more powerful, and more innovative. The GNU GPL is about treating computing as a science, and battling to widen computer frontiers in a way that will better society. Windows/Big corporations are not interested in this in the slightest
- Microsoft is removing and restricting desktop capabilities, not enhancing them. And they wrap this in marketing nonsense in a way that is ultimately very disrespectful to users
- Windows is breeding more ignorant users that are happily/unwittingly signing their rights away.
- These negative cultural aspects are mirrored positively in the FOSS community.
- On this side of the fence, there are no technology or format "lock-ins", no law suits hell bent on bringing down competitors. The developers are interested in developing, not making money from restricting access to patents.
- Most Linux distros are developing at light speed compared to Windows. But they are built on a stable foundation
- Linux is about giving power to users, not dumbing them down.

[http://ubuntuforums.org/showthread.php?t=349361&page=10](http://ubuntuforums.org/showthread.php?t=349361&page=10)

---

### Post by FuturePilot on 2007-04-20
> **billdotson said:**
>  the OS keeps a hidden folder of all your visited websites, etc. and all your email correspondents and stuff like that and sens it back to Microsoft
That's actually somewhat true. Although nothing gets sent to Microsoft, Windows does actually keep stuff like that tucked away in places you'll never find. When you delete your history from IE all you're doing is removing it from the browser. However that does not remove it from the system. With IE every website you visit gets logged.

Way back when, I did a little amateur computer forensics, and dug up every single site that had been visited.:shock:

---

