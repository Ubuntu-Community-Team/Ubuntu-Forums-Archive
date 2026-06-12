---
title: "No compiling tools?"
date: 2005-10-23
forum: The Cafe
---

### Post by Sleeper Service on 2005-10-23
Is it a definite decision of Ubuntu to include (in a default install) no tools for compiling software?

I understand that the distro is pitched at Linux newcomers, but I'd have thought that things like gcc and make are standard linux tools?

---

### Post by poofyhairguy on 2005-10-23
[QUOTE=Sleeper Service]Is it a definite decision of Ubuntu to include (in a default install) no tools for compiling software?

I understand that the distro is pitched at Linux newcomers, but I'd have thought that things like gcc and make are standard linux tools?[/QUOTE]

Its easy to add:

> sudo apt-get install build-essential

and yes the fact they don't come by default probably won't change. Ubuntu is aimed at end users, not for developers or people that need to install the latest program from a tar file they day it comes out.

---

### Post by GeneralZod on 2005-10-23
It can also be argued that the omission of GCC et al offers an additional layer of security, albeit a small one.

---

### Post by Burgundavia on 2005-10-23
Every piece of code you install by default causes potential security problems.GCC and assoicated tools introduce higher risk because they allow the building of programs.

Now, how many people actually build stuff on their systems? Not the vast majority of computer users.

Corey

---

### Post by brentoboy on 2005-10-23
[QUOTE=Burgundavia]

Now, how many people actually build stuff on their systems? Not the vast majority of computer users.

[/QUOTE]

How many operating systems have software publishers who distribute packages as source as the universal package type (tar.gz).

Without a compiler, you dont have linux :)

While i'm ranting, it would be nice if the default compiler added when you get build-essential would have been the one that was used to compile the kernel. And CC was already set to use that one, rather than a new one that cant be used to successfully compile a kernel module. </rant>

[QUOTE=GeneralZod]It can also be argued that the omission of GCC et al offers an additional layer of security, albeit a small one.[/QUOTE]

certainly, synaptic is a larger target for security hole, than the compiler - you have to act as root in order to do anything bad with a compiler, with synaptic, you are root just to open it and start working.

---

### Post by Brunellus on 2005-10-23
apt-get/aptitude/synaptic requires you to be root, as well.  

I agree, however, that a compiler and build-essential should be in the default install.

---

### Post by malv on 2005-10-23
[QUOTE=...
Without a compiler, you dont have linux :)
[/QUOTE]
[-X 
couldn't have said it better!
=D> \\:D/

---

### Post by BWF89 on 2005-10-23
[QUOTE=Burgundavia]Now, how many people actually build stuff on their systems? Not the vast majority of computer users.[/QUOTE]
When I use useing Fedora that's how I installed Firefox.

---

### Post by Orunitia on 2005-10-23
[QUOTE=Burgundavia]Now, how many people actually build stuff on their systems? Not the vast majority of computer users.

Corey[/QUOTE]

The vast majority of computer users also use windows, and never have any reason to compile anything.

---

### Post by xequence on 2005-10-23
[QUOTE=Burgundavia]Every piece of code you install by default causes potential security problems.GCC and assoicated tools introduce higher risk because they allow the building of programs.

Now, how many people actually build stuff on their systems? Not the vast majority of computer users.

Corey[/QUOTE]


No, but a vast majority of linux users do. Most of the stuff avalable for download in linux is in .tar.gz which needs to be compiled.

Also, for everything ive ever needed to compile, more then build essential was needed. Like the x window system headers and more...

---

### Post by brentoboy on 2005-10-23
[QUOTE=Orunitia]The vast majority of computer users also use windows, and never have any reason to compile anything.[/QUOTE]

Even newbies will sooner or later (probably within the first few weeks) see some howto that lets them do something cool that requires a compiler.  Linux is a source based OS not a binary based one.  That is why every distro has its own package system.  They are all "easy" replacements for source compile - the "official" linux packaging system.

If we loose source distribution / compiling, we will eventually find ourselves on a closed platform.

---

### Post by GeneralZod on 2005-10-23
[QUOTE=brentoboy]
If we loose source distribution / compiling, we will eventually find ourselves on a closed platform.[/QUOTE]

Dude, the build-essentials package is *right there* on the CD, and takes all of 10 seconds to install!  Honestly, as a programmer, I don't see how this is even an issue :confused: 

Also, Ubuntu is Debian-based and Debian has a reputation as being highly committed to Free Software - ferociously so, in fact.  There may be some minor obstacles raised to installing GCC, but the odds of Ubuntu becoming a "closed platform" are, frankly, zero.

Also, about your earlier point regarding the security of Synaptic vs GCC - Synaptic, while it does indeed run as root, is *extremely* hard to exploit - it's basically a GUI wrapper around a set of very well-tested command-line tools which opens up no ports and which interacts only with sources that are by default trustworthy.  

The removal of GCC makes trojans and root-kits harder to write - there are several instances of root-kits that require a working compiler on the host in order to install themselves due to the lack of binary compatibility between distros.  This is the "extra layer of security" that was referred to by myself and Burgundavia.

Perhaps you could expand on your concerns a little more...?

---

### Post by ssam on 2005-10-23
it is easy to install build-essential if you need it.

if you nerdy enough that you want to compile something, then you can easily run an apt-get install.

ubuntu currently fits on a single cd, thats cool. of course there is a lot left out, but it is easy to get. some people would say it not linux if it does not have emacs, latex, kde, etc

if there is something you want to install that it not in the universe why don't you become a [MOTU]("https://wiki.ubuntu.com/MOTU"), and fix it?

apple ship one button mice to force developers to make simple user interfaces, power users can easily buy a 28 button mouse if they need it. how about we try to make ubuntu fully useable with out having to compile stuff (synaptic, add-applications and update-notifier do a very good jobs at this)

if you feel strongly about linux being source based why dont you run linux from scratch/gentoo?

sam

---

### Post by brentoboy on 2005-10-23
[QUOTE=GeneralZod]
Perhaps you could expand on your concerns a little more...?
[/QUOTE]

if I must.

[QUOTE=GeneralZod]
Dude, the build-essentials package is *right there* on the CD, and takes all of 10 seconds to install!  Honestly, as a programmer, I don't see how this is even an issue :confused: 
[/QUOTE]

In order to build the nvidia driver:
I have to add build essential, then, I have to go get gcc 3.4 (becuase it isnt essential i guess) and g++ 3.4, and find the kernel headers (not essential either)... and then set CC to be correct, and export it.

[QUOTE=GeneralZod]
Also, Ubuntu is Debian-based and Debian has a reputation as being highly committed to Free Software - ferociously so, in fact.  There may be some minor obstacles raised to installing GCC, but the odds of Ubuntu becoming a "closed platform" are, frankly, zero.
[/QUOTE]

Not so much ubuntu itself closing up, just packages.  There is lots of incentive to write binary only software, and compile it for each of the major distros and distribute it in rpm, deb, and ... whathaveyou but if a package is distributed in binary form only, you really don't know what its doing.

[QUOTE=GeneralZod]
Also, about your earlier point regarding the security of Synaptic vs GCC - Synaptic, while it does indeed run as root, is *extremely* hard to exploit - it's basically a GUI wrapper around a set of very well-tested command-line tools which opens up no ports and which interacts only with sources that are by default trustworthy.  
[/QUOTE]

All I have to do to exploit synaptic is offer you an alternative repostory - with win32 codecs and other illegal stuff, and tell you this is THE place to get all the stuff the govenment wants to keep you away from...  Then tell you to make sure and set my repo to top priority on your system (so it wont accidentally download the "wimpy" codecs instead)  Then, offer a few packages that do whatever I want them to do as part of my illegal offereing, and post some stuff on forums inviting people to my party.  I would own your systems after that.  and if my trojans were any good, you wouldnt even know it.

[QUOTE=GeneralZod]
The removal of GCC makes trojans and root-kits harder to write - there are several instances of root-kits that require a working compiler on the host in order to install themselves due to the lack of binary compatibility between distros.  This is the "extra layer of security" that was referred to by myself and Burgundavia.
[/QUOTE]

GCC gets very heavy security audits on a regular bases.  Serious webservers running gentoo and other source distros in order to squeeze every last ounce out of their PCs depend on it.  It is a universal security need for all linux distros, so it gets noticed when their is a problem.

I'm not saying we should abandon deb and go to tarballs - that sucks, what i'm saying is you could make compiling programs a root only thing if you want in order to highten security, but... (I'll say it again) ...

Without a compiler, you dont have linux.

There are some simple "universal" linux utilities (like cp, ls, tar, ifconfig, ... and make) that shouldnt be missing.  Call me old fashoned.

(Oh, I almost forgot, no newbie ever cried because he had a compiler pre-installed - so the "nice for newbies" card doesnt work here)

P.S. I love ubuntu. but that doesnt mean I leave my desktop brown.
:)

---

### Post by UbuWu on 2005-10-23
[QUOTE=brentoboy]
Not so much ubuntu itself closing up, just packages.  There is lots of incentive to write binary only software, and compile it for each of the major distros and distribute it in rpm, deb, and ... whathaveyou but if a package is distributed in binary form only, you really don't know what its doing.
[/QUOTE]

It isn't distributed in binary form only, you can easily apt-get the source as well for every program in the main and universe repository. It is just that the average user won't want to do that.

---

### Post by UbuWu on 2005-10-23
[QUOTE=brentoboy]
All I have to do to exploit synaptic is offer you an alternative repostory [/QUOTE]

And to exploit you compiling programs, all it takes is let you download an alternative source package, which is far more easy to get users to do if they have to get programs from different websites instead of a centralized repository. While in theory it is safe because you can inspect the source code and see what it does, you won't be able to check all the source code for security of most programs anyway, it is just way to much code.

---

### Post by UbuWu on 2005-10-23
[QUOTE=brentoboy]
In order to build the nvidia driver:
[/QUOTE]

I hope you know you can get the nvidia driver from the repositories?

---

### Post by brentoboy on 2005-10-23
[QUOTE=UbuWu]And to exploit you compiling programs, all it takes is let you download an alternative source package, which is far more easy to get users to do if they have to get programs from different websites instead of a centralized repository. While in theory it is safe because you can inspect the source code and see what it does, you won't be able to check all the source code for security of most programs anyway, it is just way to much code.[/QUOTE]

its the ablity to inspect the code that makes it hard to deny that your program is malicious

---

### Post by brentoboy on 2005-10-23
[QUOTE=UbuWu]It isn't distributed in binary form only, you can easily apt-get the source as well for every program in the main and universe repository. It is just that the average user won't want to do that.[/QUOTE]

I whole heartedly agree that deb and repostitories are way better than compiliing packages for installation.  If I had to compile every package I added, I'd go back to windows.

But, compilers are part of linux.

I'm not looking for an argument here, i'm simply voting.
If it was a democracy, I'd vote that a compiler is an essential command like grep or ls or ln.  Now that I cast my vote, i'll live happily within the community regardless of the end result, becuase I can make do.

---

### Post by majikstreet on 2005-10-23
[QUOTE=ssam]it is easy to install build-essential if you need it.

if you nerdy enough that you want to compile something, then you can easily run an apt-get install.

ubuntu currently fits on a single cd, thats cool. of course there is a lot left out, but it is easy to get. some people would say it not linux if it does not have emacs, latex, kde, etc

if there is something you want to install that it not in the universe why don't you become a [MOTU]("https://wiki.ubuntu.com/MOTU"), and fix it?

apple ship one button mice to force developers to make simple user interfaces, power users can easily buy a 28 button mouse if they need it. how about we try to make ubuntu fully useable with out having to compile stuff (synaptic, add-applications and update-notifier do a very good jobs at this)

if you feel strongly about linux being source based why dont you run linux from scratch/gentoo?

sam[/QUOTE]
Nerdiness has nothing to do with compiling programs! I'm a full-blown nerd and I have barely ever compiled a program, mainly because I am too impatient!

---

### Post by GeneralZod on 2005-10-24
[QUOTE=brentoboy]
In order to build the nvidia driver:
I have to add build essential, then, I have to go get gcc 3.4 (becuase it isnt essential i guess) and g++ 3.4, and find the kernel headers (not essential either)... and then set CC to be correct, and export it.
[/QUOTE]

Aha - is this the source of your concerns?

Hoary to Breezy marked the transition from GCC 3.xx to GCC 4.xx, which produce incompatible binaries.  It was too late for the kernel to be compiled with 4.xx (it either simply didn't compile, or wasn't stable enough), but *every other package* was compiled with 4.xx.  Thus, build-essentials, which again is right there on the CD, contains everything you need to compile apps *except* for kernel modules and the kernel itself.  Come Dapper, I'd be very surprised if this split was still there, so build-essentials will give you *everything you need* to compile stuff, except possibly the kernel headers - I'm not sure why these aren't included on the CD, though, as they only take up a MB.  I'd agree that the kernel headers should be there :)

> 
If it was a democracy, I'd vote that a compiler is an essential command like grep or ls or ln. Now that I cast my vote, i'll live happily within the community regardless of the end result, becuase I can make do.


This is what we keep coming back to, and what I simply don't get - anyone who has the install CD and a working CD reader can install the complete compiler suite, with make, gcc, gdb etc in 10 seconds flat.  Why is the fact that it is not included in the default install even an issue?

---

### Post by Sleeper Service on 2005-10-24
[QUOTE=GeneralZod]Why is the fact that it is not included in the default install even an issue?[/QUOTE]
For me, it wasn't so much an Issue as a question.  I'd always thought of make as being a fundamental linux command.

Like brentoboy, I'd put my vote on compiling tools to be available by default - if only to echo the basic open-source proposition: that we can inspect source code, modify and re-build it.

But I didn't know about the build-essentials, so that'll keep me quite happy if I'm a minority.

All the best :)

---

### Post by brentoboy on 2005-10-24
[QUOTE=GeneralZod]Aha - is this the source of your concerns?

Hoary to Breezy marked the transition from GCC 3.xx to GCC 4.xx, which produce incompatible binaries.  It was too late for the kernel to be compiled with 4.xx (it either simply didn't compile, or wasn't stable enough), but *every other package* was compiled with 4.xx.  Thus, build-essentials, which again is right there on the CD, contains everything you need to compile apps *except* for kernel modules and the kernel itself.  Come Dapper, I'd be very surprised if this split was still there, so build-essentials will give you *everything you need* to compile stuff, except possibly the kernel headers - I'm not sure why these aren't included on the CD, though, as they only take up a MB.  I'd agree that the kernel headers should be there :)
[/QUOTE]

I've been painfully aware of all of that wonderful information for quite some time now, but none of the details make the end result any less anoying.

I cope. and quite happily might I add.  Ubuntu does wonders for the linux community, and I am a happy ubuntu-er

But, alas, that doesnt make a kernel compiled with 3.4 and the default compiler 4.0 any more intuitive. And it doesnt mean that a built in compiler wouldnt make things just a little better (for me).

Let it go man, let it go.  My opinion isnt based on lack of knowledge, or lack of seeing the big picture, its based on personal experience.  Its my opinion, and I like it.

---

### Post by GeneralZod on 2005-10-24
[QUOTE=brentoboy]
Let it go man, let it go.  My opinion isnt based on lack of knowledge, or lack of seeing the big picture, its based on personal experience.  Its my opinion, and I like it.[/QUOTE]

Fair enough - I guess we'll have to agree to disagree on this one :)

---

### Post by poofyhairguy on 2005-10-24
[QUOTE=Sleeper Service]For me, it wasn't so much an Issue as a question.  I'd always thought of make as being a fundamental linux command.
[/QUOTE]

Thats just the thing. Ubuntu wanted to bring new ideas to the table- such as you don't need to compile your own code to enjoy Linux!

---

### Post by BWF89 on 2005-10-24
[QUOTE=ssam]apple ship one button mice to force developers to make simple user interfaces, power users can easily buy a 28 button mouse if they need it. how about we try to make ubuntu fully useable with out having to compile stuff (synaptic, add-applications and update-notifier do a very good jobs at this[/QUOTE]
That's not a good arguement. The majority of people hate Apple's 1 button mouses. Me included.

---

### Post by Stormy Eyes on 2005-10-24
[QUOTE=Burgundavia]Now, how many people actually build stuff on their systems?[/QUOTE]

**Yo!**

Of course, I'm content to apt-get the tools I need. It's not like GVim comes installed by default, after all. :)

---

### Post by cowlip on 2005-10-24
Of course I have to for some programs or applets.  It's not fun, but doing ./configure after ./configure isn't fun either.  I wish more developers would use autopackage for this type of thing, but that's another story. In the end, I hope ubuntu will make it easier to get the required dev packages, because as I said, it's pretty hard right now.

---

### Post by BoyOfDestiny on 2005-10-25
Actually I don't mind it's not included by default (it is good to know build-essential exists though). One thing though, even with the compiler you will most likely have to fire up synpatic or apt-get and download some of the dependencies.

I was actually getting annoyed since I couldn't compile vice 1.07 and the repository had and older version with some copyrighted files removed (the kernal, yes it's kernal for the c64 :) ) Also the package doesn't mention where to put the file either once you procure the kernal image (legally of course, not just googling ;) ).

Anyway point of the rant? Ubuntu is great. Some apps I want to be up to date, but I don't want to add strange repos...

90% of what I wanted I compiled successfully (and made debs for)... but a few I'm just not sure what's keeping it from happening (gcc or dependency or what...)

What would be neat if there was something like emerge that could be used, just for those 10 apps/plugins I like to keep up to date...

Here are my debs with source:
[http://www.safaribans.com/gpl/](http://www.safaribans.com/gpl/)

Funnily enough 4 packages are out of date, time to download them, untar, ./configure, make, checkinstall, repeat... :)

---

### Post by Sleeper Service on 2005-11-01
[QUOTE=poofyhairguy]Thats just the thing. Ubuntu wanted to bring new ideas to the table- such as you don't need to compile your own code to enjoy Linux![/QUOTE]
That is somewhat twisting what I said in a different direction.

Ubuntu are very much committed to the GPL, open-source and freedom.  Nobody is arguing that make(etc.) should replace dpkg(etc.), but without tools for inspecting, re-writing and compiling software, there's little benefit in open-source.

It's accepted that beginners will not be bothered with all this, and so to save disk space (though how much, really?!) build tools can be left off the default install.  I've got no major problem with this - especially now I realise the tools are included on the CD, just not installed.

But the inclusion of these tools *is* important, even if they're not installed by default.  They are important for the open-source proposition to be meaningful.

---

### Post by poofyhairguy on 2005-11-01
[QUOTE=Sleeper Service]
But the inclusion of these tools *is* important, even if they're not installed by default.  They are important for the open-source proposition to be meaningful.[/QUOTE]

Agreed . Yay for build-essential. I'm just glad the tools are not installed by default.

---

### Post by victorche on 2005-11-08
Excuse me for taking part in the philosophy war here... But as you can see in this file:
[http://releases.ubuntu.com/kubuntu/breezy/kubuntu-5.10-install-i386.list](http://releases.ubuntu.com/kubuntu/breezy/kubuntu-5.10-install-i386.list)
there is a file, called /pool/main/l/linux-kernel-headers/linux-kernel-headers_2.6.11.2-0ubuntu13_i386.deb
So I think build-essential needs this one...
Correct me if I am wrong... So all the dependancies needed by build-essential are on the CD.
Or not? :???:
So you can install it even without an internet connection if you use your own CD as a repository... Right?

---

