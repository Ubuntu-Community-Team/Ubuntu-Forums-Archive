---
title: "Why do you think dependencies are superior (with a catch)"
date: 2009-03-29
forum: The Cafe
---

### Post by shadoweva00 on 2009-03-29
To me it seems dependencies are the root of 99% of user problems not related to hardware.

If you took arguments that the average user didn't care about and would never need to know, there is no support for them whatsoever. If you can't talk about how shared and dynamic libraries work, how it saves what is probably less than a gigabyte, and can only talk about how the competitors of Mac and Windows require applications to ship with what you call dependencies, or security issues, how can you possibly defend them?

If the average user just wants it to work, and ubuntu wants to compete with Windows and Mac, why don't we have self contained  install files as well? PCBSD has already done this, so it could be used as a model. They've literally already thought through the issues and finished the system.

Sorry, but it just defies reason that you're still hanging onto dependencies as better when they have such huge downsides that you must be ignoring. (server costs, people seeking help needing to use command lines, 3rd party packages that need renamed/merged dependencies. It's always ends up being a dependency problem)

Can you possibly defend them if you aren't thinking about technical details and only in terms of usability? I'm sure you can't, but let's see. To me it's just such a no brainer question, but if the Linux community keeps standing behind them for only technical reasons, they'll be keeping Desktop Linux from ever being a serious competitor.

(Anyone who mentions dll hell, shared/dynamic libraries, and security issues fails. Only usability issues are valid arguments here. (PCBSD found chroot jails fixed security problems))

---

### Post by MaxIBoy on 2009-03-29
> **shadoweva00 said:**
> (Anyone who mentions dll hell, shared/dynamic libraries, and security issues fails. Only usability issues are valid arguments here. (PCBSD found chroot jails fixed security problems))I don't believe that gravity exists. Please do not try to dissuade me by allowing objects with mass to fall. If you attempt to prove the existence of gravity by dropping heavy objects, you fail, because that is obviously not a valid method of proving it.



While you're at it, prove to me that I cannot fly. If you try to prove that I cannot fly by throwing me off a cliff and watching me drop like a brick, you fail, because that is obviously an overused and tiresome piece of so-called "evidence."

---

### Post by Skripka on 2009-03-29
> **MaxIBoy said:**
> I don't believe that gravity exists. Please do not try to dissuade me by allowing objects with mass to fall. If you attempt to prove the existence of gravity by dropping heavy objects, you fail, because that is obviously not a valid method of proving it.



While you're at it, prove to me that I cannot fly. If you try to prove that I cannot fly by throwing me off a cliff and watching me drop like a brick, you fail, because that is obviously an overused and tiresome piece of so-called "evidence."

I giggled.

---

### Post by shadoweva00 on 2009-03-29
> **MaxIBoy said:**
> I don't believe that gravity exists. Please do not try to dissuade me by allowing objects with mass to fall. If you attempt to prove the existence of gravity by dropping heavy objects, you fail, because that is obviously not a valid method of proving it.



While you're at it, prove to me that I cannot fly. If you try to prove that I cannot fly by throwing me off a cliff and watching me drop like a brick, you fail, because that is obviously an overused and tiresome piece of so-called "evidence."

See, if you just admitted that self contained installers like those of windows, mac, and PCBSD make the system "just work" far more than dependencies ever will, Ubuntu can be a much better competitor.

---

### Post by bakedbeans4life on 2009-03-29
> **shadoweva00 said:**
> To me it seems dependencies are the root of 99% of user problems not related to hardware.

If you took arguments that the average user didn't care about and would never need to know, there is no support for them whatsoever. If you can't talk about how shared and dynamic libraries work, how it saves what is probably less than a gigabyte, and can only talk about how the competitors of Mac and Windows require applications to ship with what you call dependencies, or security issues, how can you possibly defend them?

If the average user just wants it to work, and ubuntu wants to compete with Windows and Mac, why don't we have self contained  install files as well? PCBSD has already done this, so it could be used as a model. They've literally already thought through the issues and finished the system.

Sorry, but it just defies reason that you're still hanging onto dependencies as better when they have such huge downsides that you must be ignoring. (server costs, people seeking help needing to use command lines, 3rd party packages that need renamed/merged dependencies. It's always ends up being a dependency problem)

Can you possibly defend them if you aren't thinking about technical details and only in terms of usability? I'm sure you can't, but let's see. To me it's just such a no brainer question, but if the Linux community keeps standing behind them for only technical reasons, they'll be keeping Desktop Linux from ever being a serious competitor.

(Anyone who mentions dll hell, shared/dynamic libraries, and security issues fails. Only usability issues are valid arguments here. (PCBSD found chroot jails fixed security problems))

So each application should be installed with it's own libraries, even though those libraries may be duplicated on the same system. Sort of sounds like you want Windows to me.

[www.microsoft.com](www.microsoft.com)

Be prepared, they may want your credit card details. Amongst other things.

---

### Post by smartboyathome on 2009-03-29
> **shadoweva00 said:**
> See, if you just admitted that self contained installers like those of windows, mac, and PCBSD make the system "just work" far more than dependencies ever will, Ubuntu can be a much better competitor.

What would happen if you installed two programs which relied on two different versions of the same library which was located in the same place? The one with the dependence on the older library would probably break, because the newer copy would be installed.

---

### Post by MaxIBoy on 2009-03-29
DLL Hell, shared libraries, and security holes are all usability issues, which is why I think the OP's question cannot be answered in any meaningful way. It's like trying to define the word "vehicle" without mentioning transportation or movement.

In other words, "Objection! Assumes organ not in evidence!"

---

### Post by shadoweva00 on 2009-03-29
> **smartboyathome said:**
> What would happen if you installed two programs which relied on two different versions of the same library which was located in the same place? The one with the dependence on the older library would probably break, because the newer copy would be installed.

No, it would be like Mac and PCBSD. Each application get's it's own folder and anything that the OS doesn't provide (X, dhcp, etc...) would be bundled there. Every program just works, you don't need to download extra dependencies, the distro maintainers don't need to host huge repositories and pay for bandwidth, power costs for the servers hosting the repository...

---

### Post by smartboyathome on 2009-03-29
> **shadoweva00 said:**
> No, it would be like Mac and PCBSD. Each application get's it's own folder and anything that the OS doesn't provide (X, dhcp, etc...) would be bundled there. Every program just works, you don't need to download extra dependencies, the distro maintainers don't need to host huge repositories and pay for bandwidth, power costs for the servers hosting the repository...

So, basically you would have to compile most of Linux for each package? The way you describe, since Linux has many dependancies, something like BASH would have to be included with every app, along with GCC, Glibc, etc. That would give you a huge package for each file, and would actually waste space imo.

---

### Post by MaxIBoy on 2009-03-29
> **shadoweva00 said:**
> No, it would be like Mac and PCBSD. Each application get's it's own folder and anything that the OS doesn't provide (X, dhcp, etc...)What the hell are you smoking? X, Dhcp, and so on, should **not** be provided! Nothing should be provided! Don't you know how annoying dependencies are? Every program should come with its own window system, Internet code, graphics drivers, and so on. Heck, every program should come with its own operating system! It's totally worth the effort, just to avoid dependencies! Even if you had to specifically design your program to accommodate every other combination of programs that the user might run at the same time. Totally worth the trouble. And we can't compromise on this, either. If just one little feature was provided, that would be a dependency, and dependencies are bad for usability.> ...would be bundled there. Every program just works, you don't need to download extra dependencies, the distro maintainers don't need to host huge repositories and pay for bandwidth, power costs for the servers hosting the repository...Sounds good to me! [Here's your computer]("http://cgi.ebay.com/Compaq-Portable-Computer-101709-Model-Still-Working_W0QQitemZ180341195624QQcmdZViewItemQQptZLaptops_Nov05?hash=item180341195624&_trksid=p3286.c0.m14&_trkparms=72%3A1234%7C66%3A2%7C65%3A12%7C39%3A1%7C240%3A1318%7C301%3A0%7C293%3A2%7C294%3A50") (minus the pesky "hard drive" dependency,) now get programming!

---

### Post by Paqman on 2009-03-29
> **shadoweva00 said:**
> To me it seems dependencies are the root of 99% of user problems not related to hardware.


Can't say i've *ever* had any dependency problems with a package i've got from a repo. The only time it's an issue is if you're rolling your own apps, at which point you can't really moan about usability, since you're deliberately straying off the path of least resistance.

---

### Post by lykwydchykyn on 2009-03-29
I think it's unfortunate that so many people on these forums are way more capable of designing a better OS than the ubuntu developers.  I mean, if Linux was only open source maybe those folks could take a crack at creating their own Linux and demonstrating how much better their design for it is than Ubuntu's.  But no, too bad it's not and we have to suffer with Canonical's missteps.  

And if only us Ubuntu USERS would admit these folks are right, Ubuntu would be so much better.  But we won't, pig-headed jerks that we are.  So, that's it then.

---

### Post by shadoweva00 on 2009-03-29
> **smartboyathome said:**
> So, basically you would have to compile most of Linux for each package? The way you describe, since Linux has many dependancies, something like BASH would have to be included with every app, along with GCC, Glibc, etc. That would give you a huge package for each file, and would actually waste space imo.
 Your missing a lot of key facts, firefox would only require cairo, gtk, and would be the same size as the windows binary. Everything would practically be the same size as the windows binary equivalents. PCBSD implemented a working system, and comments like this prove you didn't bother looking at it. Sure it wastes a little space, But gives 1000 times more usability than our work a rounds for dependencies and it's hardly any space to begin with.

---

### Post by cardinals_fan on 2009-03-29
> **shadoweva00 said:**
> 
If you took arguments that the average user didn't care about and would never need to know, there is no support for them whatsoever. If you can't talk about how shared and dynamic libraries work, how it saves what is probably less than a gigabyte, and can only talk about how the competitors of Mac and Windows require applications to ship with what you call dependencies, or security issues, how can you possibly defend them?
You know, those "average users" don't care about the difference between their processor and their RAM.  So why not combine the two into one master component?  No complaining about technical details - they don't care.
> **shadoweva00 said:**
> 
If the average user just wants it to work, and ubuntu wants to compete with Windows and Mac, why don't we have self contained  install files as well? PCBSD has already done this, so it could be used as a model. They've literally already thought through the issues and finished the system.
All my experiences with PBIs have been disastrous.  I'd be interested to hear why you like that approach.
> **shadoweva00 said:**
> 
Can you possibly defend them if you aren't thinking about technical details and only in terms of usability? I'm sure you can't, but let's see. To me it's just such a no brainer question, but if the Linux community keeps standing behind them for only technical reasons, they'll be keeping Desktop Linux from ever being a serious competitor.

If nobody thought about technical details, you would be writing this on a papyrus scroll with the blood of an antelope.
> **shadoweva00 said:**
> See, if you just admitted that self contained installers like those of windows, mac, and PCBSD make the system "just work" far more than dependencies ever will, Ubuntu can be a much better competitor.
But I don't admit that.  
> **shadoweva00 said:**
> No, it would be like Mac and PCBSD. Each application get's it's own folder and anything that the OS doesn't provide (X, dhcp, etc...) would be bundled there. Every program just works, you don't need to download extra dependencies, the distro maintainers don't need to host huge repositories and pay for bandwidth, power costs for the servers hosting the repository...
*sigh*

You don't get out of downloading dependencies by putting them with the apps.  In fact, that would require far more hosting because every single app would need all of its dependencies as well.

The only problem with the current system is the way certain systems (Debian and all derivatives, SliTaz, and others) trim out development headers and otherwise adulterate their packages.  Slackware's package manager doesn't even resolve dependencies, but it's rarely an issue because the packages come with everything they are supposed to.

Anyway, it's good to have you back.  This should be every bit as enjoyable as our last discussion.

---

### Post by shadoweva00 on 2009-03-29
> **lykwydchykyn said:**
> I think it's unfortunate that so many people on these forums are way more capable of designing a better OS than the ubuntu developers.  I mean, if Linux was only open source maybe those folks could take a crack at creating their own Linux and demonstrating how much better their design for it is than Ubuntu's.  But no, too bad it's not and we have to suffer with Canonical's missteps.  

And if only us Ubuntu USERS would admit these folks are right, Ubuntu would be so much better.  But we won't, pig-headed jerks that we are.  So, that's it then.

Proving that the community hates people? Everyone must be programmers willing to take months of their time to fix a product they believe to be broken in the first place. If you don't listen to complaints or suggestions, you're the biggest problem with Desktop Linux ever. That's right, you're really just proving the community is the biggest problem with Desktop Linux by not properly responding to any criticism, no matter how valid.

---

### Post by shadoweva00 on 2009-03-29
> **cardinals_fan said:**
> You don't get out of downloading dependencies by putting them with the apps.  In fact, that would require far more hosting because every single app would need all of its dependencies as well.

But it's the software makers that have to deal with it, not the distro maintainers.

---

### Post by bakedbeans4life on 2009-03-29
> **shadoweva00 said:**
> Your missing a lot of key facts, firefox would only require cairo, gtk, and would be the same size as the windows binary. Everything would practically be the same size as the windows binary equivalents. PCBSD implemented a working system, and comments like this prove you didn't bother looking at it. Sure it wastes a little space, But gives 1000 times more usability than our work a rounds for dependencies and it's hardly any space to begin with.

So why don't you go with a PC-BSD system? If it scratches your itches, fair enough. Why post here?

---

### Post by shadoweva00 on 2009-03-29
> **bakedbeans4life said:**
> So why don't you go with a PC-BSD system? If it scratches your itches, fair enough. Why post here?

Hardware compatibility is low, It doesn't really matter whether Linux copies PBI or the OSX's dmg, it just needs to pick something.

P.S. I'd rather laugh as the community makes Desktop Linux crash and burn. Some of the posts in this very thread have proved that's where it's going.

---

### Post by shadoweva00 on 2009-03-29
> **MaxIBoy said:**
> DLL Hell, shared libraries, and security holes are all usability issues, which is why I think the OP's question cannot be answered in any meaningful way. It's like trying to define the word "vehicle" without mentioning transportation or movement.

In other words, "Objection! Assumes organ not in evidence!"

Users don't care about shared libraries, nor do they ever affect usability. DLL is from bad programmers, an OS can't protect you from that. This is all about what affects the user.

---

### Post by MaxIBoy on 2009-03-29
> **shadoweva00 said:**
> Proving that the community hates people? Everyone must be programmers willing to take months of their time to fix a product they believe to be broken in the first place. If you don't listen to complaints or suggestions, you're the biggest problem with Desktop Linux ever. That's right, you're really just proving the community is the biggest problem with Desktop Linux by not properly responding to any criticism, no matter how valid.Proving that users hate programmers? "Damn them all, working hard for little or no pay on software I use every day! Let's make life hell for programmers! That'll teach them a lesson!"

---

### Post by BuffaloX on 2009-03-29
I have much sympathy for OPs suggestion, but wouldn't it require stable API?
I know there has been talk about making part of Linux API stable, but I'm not aware of it being actually decided.

Wouldn't it be possible to just include needed "fixed" libraries in your package / installer, and use local libraries instead of system libraries?
Of course running the risk of making obsolete unsupported calls from same libraries.

For people such as myself, it's weird not to have a stable API, I've been used to that for 30 years now. The Linux way is very different, and takes a lot of getting used to.

---

### Post by simtaalo on 2009-03-29
> **shadoweva00 said:**
> P.S. I'd rather laugh as the community makes Desktop Linux crash and burn. Some of the posts in this very thread have proved that's where it's going.

seems to be doing fine on my system.

don't get how it could crash and burn either.

---

### Post by lykwydchykyn on 2009-03-29
> **shadoweva00 said:**
> Proving that the community hates people? Everyone must be programmers willing to take months of their time to fix a product they believe to be broken in the first place. If you don't listen to complaints or suggestions, you're the biggest problem with Desktop Linux ever. That's right, you're really just proving the community is the biggest problem with Desktop Linux by not properly responding to any criticism, no matter how valid.

Yep, I AM THE BIGGEST PROBLEM WITH DESKTOP LINUX EVER.  It's true.  How could I not see it before?  Despite the fact that I (and I'm willing to bet, everyone else in this thread) have NO SAY WHATSOEVER over the future of Linux development, my refusal to concede to every criticism of Linux is destroying it.  

And shame on me for suggesting someone else could make a distro that does this sort of thing.  It's much more realistic to expect a major existing distro to scrap its entire architecture and adopt this one.

---

### Post by damis648 on 2009-03-29
> **shadoweva00 said:**
> To me it seems dependencies are the root of 99% of user problems not related to hardware.

Where in hell are you getting this statistic from? I have only once ever had a serious dependency problem, and that was my fault.

Also, since every Linux distro comes with different tools, how could software makers know what to include in their applications, because some distros could have it and some wouldn't?

---

### Post by Skripka on 2009-03-29
> **lykwydchykyn said:**
> Yep, I AM THE BIGGEST PROBLEM WITH DESKTOP LINUX EVER.  It's true.  How could I not see it before?  Despite the fact that I (and I'm willing to bet, everyone else in this thread) have NO SAY WHATSOEVER over the future of Linux development, my refusal to concede to every criticism of Linux is destroying it.  

And shame on me for suggesting someone else could make a distro that does this sort of thing.  It's much more realistic to expect a major existing distro to scrap its entire architecture and adopt this one.

Why DO you/me/we Hate Linux So Much?

---

### Post by bakedbeans4life on 2009-03-29
> **shadoweva00 said:**
> Hardware compatibility is low, It doesn't really matter whether Linux copies PBI or the OSX's dmg, it just needs to pick something.

P.S. I'd rather laugh as the community makes Desktop Linux crash and burn. Some of the posts in this very thread have proved that's where it's going.

So I was correct in my initial assessment, you want Windows.

[www.microsoft.com/](www.microsoft.com/)

---

### Post by loell on 2009-03-29
> **shadoweva00 said:**
> Your missing a lot of key facts, firefox would only require cairo, gtk, and would be the same size as the windows binary. **Everything would practically be the same size as the windows binary **

needs compeling proof. ;)

---

### Post by shadoweva00 on 2009-03-29
> **Skripka said:**
> Why DO you/me/we Hate Linux So Much?

Because you've become the enforcers of the status quo, and completely killed off any chance that it will change and become better like open source is supposed to. By agreeing with other people that dependencies are the best way to do things, not doing objective comparisons to other systems, and not admitting faults, you are now the enforcers of a status quo for Desktop Linux. All changes that could make it possibly better are now killed of by your community because you think it's the best way to do things. Things like market share and usability are irrelevant next to small technical details the average use should never know of, Even though this kind of thinking is the most hypocritical thing to ubuntu bug #1. The ignorance and immaturity goes all the way to the top of each distro. Essentially you've all made the idea of open source becoming better the biggest lie of all because you're always standing in the way of it.

---

### Post by BuffaloX on 2009-03-29
Please could some of you guys be just a little bit more constructive.

We all fully get the advantage of size for shared dependencies.
Admittedly they are better both for size and efficiency.

But not for ease of installing programs.

But the other day I wanted to try Bluefish unstable, but couldn't install it, although it had .deb installers, because my repositories didn't meet a dependency. I know it's not a big deal, I could just install this library too, and if needed even compile it.

The OP wants and suggests a method to make programs as easy to install as in windows. Don't bash him so hard, many want this.

Synaptix beats any Windows installer by light-years, but when things are not in Synaptix, installation of programs is not so great.

Including dependencies in packages, would make all installations a one click operation.

---

### Post by Skripka on 2009-03-29
> **shadoweva00 said:**
> Because you've become the enforcers of the status quo, and completely killed off any chance that it will change and become better like open source is supposed to. By agreeing with other people that dependencies are the best way to do things, not doing objective comparisons to other systems, and not admitting faults, you are now the enforcers of a status quo for Desktop Linux. All changes that could make it possibly better are now killed of by your community because you think it's the best way to do things. Things like market share and usability are irrelevant next to small technical details the average use should never know of, Even though this kind of thinking is the most hypocritical thing to ubuntu bug #1. The ignorance and immaturity goes all the way to the top of each distro. Essentially you've all made the idea of open source becoming better the biggest lie of all because you're always standing in the way of it.

Here ya go:

[http://en.wikipedia.org/wiki/Rhetorical_question](http://en.wikipedia.org/wiki/Rhetorical_question)

HTH HTH HTH!!!

---

### Post by red_Marvin on 2009-03-29
If I have a toaster and a washing machine that I need to fix, and they are both put together with the same kind of screw, it makes sense to me to only buy one screwdriver of that kind, and use it to fix both machines. Note that I in that motivation haven't mentioned anything technical, like saving money, or one screwdriver taking up less space in the tool drawer than two. While I do computer programming enough to be able to see why dependencies are positive, I do not make my own screwdrivers (except maybe the kind you drink) and I just want to "use it".

It more or less boils down to a/the basic unix philosophy "one tool for the job". If you do not agree with this I believe there is no way of convincing you.

---

### Post by shadoweva00 on 2009-03-29
> **BuffaloX said:**
> Please could some of you guys be just a little bit more constructive.

We all fully get the advantage of size for shared dependencies.
Admittedly they are better both for size and efficiency.

But not for ease of installing programs.

But the other day I wanted to try Bluefish unstable, but couldn't install it, although it had .deb installers, because my repositories didn't meet a dependency. I know it's not a big deal, I could just install this library too, and if needed even compile it.

The OP wants and suggests a method to make programs as easy to install as in windows. Don't bash him so hard, many want this.

Synaptix beats any Windows installer by light-years, but when things are not in Synaptix, installation of programs is not so great.

Including dependencies in packages, would make all installations a one click operation.

Face it, you should have just reported all of them from the start, it does say this if for community building and all they've wanted to do is insult the idea itself.

---

### Post by Mr. Picklesworth on 2009-03-29
APIs are "usability issues". That won't stop any developers from using them, because without said APIs they would never get things done.

---

### Post by issih on 2009-03-29
Having only one copy of a library in the system is very useful from a security point of view. If every application that needed a shared library has its own version, potentially with each version being a different release, what happens when versions between x and y are found to contain a serious buffer overflow vulnerability.

You'd need to loop through every copy of the library on the system, checking if it was one of the compromised versions and updating it where it was broken, hoping that this update wouldn't break the application in question.

This means the OS will need to keep a list of where all copies of a given library are, at which point you stumble into the pain of things like registries and the potential disasters if these things get out of sync, or if an app doesn't register itself as installing a certain library. In the end that is every bit as clunky (and less secure) as having one version of the library on the system and having to deal with dependencies.

You can not separate the technical arguments from the usability ones. Your proposed model is inherently less secure and more vulnerable to badly coded apps compromising the system and I don't see how you could change those facts (I'm willing to be proved wrong here, but I'm not going to go googling now as it is late here). The only real benefit it has is that it makes installation simpler for the fringe cases where we cannot work with the repositories...but does so at the expense of the security model. Its just not worth the price imho.

Security IS usability, without it you simply shouldn't be using the computer, regardless of how simple it is, Microsoft has taught us that much over the years.

I'm all for some development of the packaging system to try and resolve problems more elegantly, but I don't think that this solution is going to help anyone. In any case, its really more of a problem with someone releasing badly packaged software than anything else. as there is nothing stopping a developer releasing all the necessary debs to install his software (including updated libraries) its just that sometimes they don't. In much the same way as sometimes you download windows software that won't install or uninstall or wom't start or whatever else, it is not so much a limitation of the model, but developers not using it properly.

Granted the proliferation of distros and package managers makes packaging things in a way that is universal to all linux distros almost impossible, but that is a different argument.

Realistically people just need to learn to release software via ppa's more, so that any dependencies that require libraries of a newer version than those in the repos can be easily satisfied.

End of ramble...I should sleep now

---

### Post by smartboyathome on 2009-03-29
> **shadoweva00 said:**
> Face it, you should have just reported all of them from the start, it does say this if for community building and all they've wanted to do is insult the idea itself.

You asked that we prove that dependencies are superior, we are trying to. Then you say we are all bashing. Make up your mind what you want.

And if you want this, make a new Linux packaging format which allows for this. I will give you a hint on where to get started, see [here]("http://www.linuxfromscratch.org/hints/downloads/files/pkg_unionfs.txt") and read through it.

---

### Post by MikeTheC on 2009-03-29
I totally agree with the OP. We should get rid of all shared libraries and make everything self-contained. And while we're at it, we should also [blow up the moon](http://www.petitiononline.com/156840/petition.html).

---

### Post by simtaalo on 2009-03-29
> **shadoweva00 said:**
> Things like market share and usability are irrelevant next to small technical details the average use should never know of, Even though this kind of thinking is the most hypocritical thing to ubuntu bug #1

personally i do think that market share is irrelevant especially at the cost of good practise, and yes i do think bug #1 is pretty stupid but thats just me.

i've hardly experienced problems with dependencies, i can't think of a case where it has happened to me with a deb file, and only once when compiling from source. that day i learnt the build-dep command in apt-get which sorted all that out.

the system doesn't need to change, just in the small number of cases where deb files don't install all needed dependencies they just need to be packaged better. the problem isn't the system, just some people don't package deb's that well.

---

### Post by MaxIBoy on 2009-03-29
> **issih said:**
> Having only one copy of a library in the system is very useful from a security point of view. If every application that needed a shared library has its own version, potentially with each version being a different release, what happens when versions between x and y are found to contain a serious buffer overflow vulnerability.

You'd need to loop through every copy of the library on the system, checking if it was one of the compromised versions and updating it where it was broken, hoping that this update wouldn't break the application in question.

This means the OS will need to keep a list of where all copies of a given library are, at which point you stumble into the pain of things like registries and the potential disasters if these things get out of sync, or if an app doesn't register itself as installing a certain library. In the end that is every bit as clunky (and less secure) as having one version of the library on the system and having to deal with dependencies.
Essentially, you'd be asking the OS to solve the [Halting Problem]("http://en.wikipedia.org/wiki/Halting_problem").

---

### Post by chucky chuckaluck on 2009-03-29
> **cardinals_fan said:**
> If nobody thought about technical details, you would be writing this on a papyrus scroll with the blood of an antelope.

i miss those days.

---

### Post by Skripka on 2009-03-29
> **chucky chuckaluck said:**
> i miss those days.

It needs to be posted:

[http://www.youtube.com/watch?v=R_hlMK7tCks](http://www.youtube.com/watch?v=R_hlMK7tCks)

---

### Post by Mr. Picklesworth on 2009-03-29
Heck, COMPUTERS are usability issues. We expect users to figure out that the mouse corresponds to an arrow on screen? How dumb!

Anyhow, my thought on "dependencies":


[LIST]
[*]An application does not NEED to ship with global dependencies (the Debian way). It can work the Windows way, providing its own versions of everything. Nothing is stopping it.

[*]An application does not need to exist 'all over the system', eg. with files in /usr/share /etc and /var. It can easily go into /opt, or just dump its files into one place. Nobody will complain. It is *preferred* that an application installs itself in the regular places since it encourages some nice avenues for scripting and integration.

[*]Dependencies are more than just for saving space. The idea is that applications *actually do* depend on shared components of a system. Yes, believe it or not, this is not just a tacked on layer to torment you. A Linux system is very openly modular so those components are exposed and interchangeable. Some interfaces, like gnome-app-install and PackageKit's current front end do quite nicely hiding that bother.

[*]Dependencies are awesome for developers. Package a program, say "this needs sqlite, the Mono runtime and goocanvas" and have that automagically work for users. The Windows version, on the other hand, tends to be absolutely horrible for end users since it demands they install such things themselves. Developers must hand-tune their installers to deal with the dependencies since Windows Installer alone doesn't cut it. Some developers are better at that than others.

[*]Shared libraries are important. First of all, without shared libraries we don't have an operating system but a mess of lone applications each with long load times and such bother. If every application shipped with its own GUI toolkit, the operating system vendor would never be able to change said toolkit. Ever. An obvious example of such change is that the version of GTK coming in Jaunty now has a cute little warning when the caps lock key is being pressed in a password field. Imagine if everyone shipped their own self-contained GTK to spare you the "horror" of package dependency management?
Same deal with any other API out there. We don't discriminate. Changing those shared components is about more than just adding pretty effects, too. Without that capability, individual application developers are in charge of maintaining security for every component utilized by each of their applications. That is a HORRIFYING duplication of effort and means that everyone wastes a lot of time updating stuff. (Long story short, that doesn't work in the real world). What time you are spared worrying about that rare case of broken dependencies is quickly lost worrying about updating some crypto library a hundred times.
[/LIST]

---

### Post by betrunkenaffe on 2009-03-29
So I read through your other thread and all of this one. I am definitely in favor of eliminating users ever running into dependency issues. I however disagree on the methods in order to accomplish this. That being said, we are 2 people on the internet with the same goals and different opinions, it happens.

If you REALLY feel it's important to implement your dependency solution, I recommend you look at the following links for further assistance in accomplishing this goal.

[http://www.ibm.com/developerworks/linux/library/os-lfs/](http://www.ibm.com/developerworks/linux/library/os-lfs/)
[http://www.linuxfromscratch.org/](http://www.linuxfromscratch.org/)
[http://www.informationweek.com/news/software/showArticle.jhtml?articleID=205917063](http://www.informationweek.com/news/software/showArticle.jhtml?articleID=205917063)

If you want Ubuntu to examine a move towards this, you should first start with polls, get support and then communicate to the Ubuntu developers the interest. I'm sure they'll conduct their own polls and see what users would like to see. All this being said, if the developers are not interested in this system at all, it will not be implemented. Their distribution, their choice.

Linux is about choice, you can choose to use what someone else has set up or you can choose to make your own customized package. There are always advantages to both, but you need to make that choice yourself. I choose to accept the problems that come with this distribution because I happen to really like the advantages that come with it. You may disagree, that is your choice, you can complain, that again is your choice. In the end, it isn't your choice on what this distribution will look like in 5 years.

Regarding your blatant attacks on the community, stop it, no one here is a developer, no one here is holding back anything. We all use an OS which we feel works well, would like to see improvements and are happy to see what those hardworking devs can do. If you are not happy with the community, please leave and never return. Your negativity and poison are not wanted, leave it at the door and discuss rationally.

---

### Post by wswartzendruber on 2009-03-30
Hey guys.  Gentoo user here.  We had this a**hat stop by our forums too.  He seems to be hopping around.

[http://forums.gentoo.org/viewtopic-t-750962.html](http://forums.gentoo.org/viewtopic-t-750962.html)

---

### Post by Skripka on 2009-03-30
> **wswartzendruber said:**
> Hey guys.  Gentoo user here.  We had this a**hat stop by our forums too.  He seems to be hopping around.

[http://forums.gentoo.org/viewtopic-t-750962.html](http://forums.gentoo.org/viewtopic-t-750962.html)

Yes, but our thread is better as it has more posts!
;)

---

### Post by CraigPaleo on 2009-03-30
> **Skripka said:**
> Yes, but our thread is better as it has more posts!
;)

Actually, theirs has 50 posts. :P

---

### Post by directhex on 2009-03-30
> **Mr. Picklesworth said:**
> [list][*]Dependencies are more than just for saving space. The idea is that applications *actually do* depend on shared components of a system. Yes, believe it or not, this is not just a tacked on layer to torment you. A Linux system is very openly modular so those components are exposed and interchangeable. Some interfaces, like gnome-app-install and PackageKit's current front end do quite nicely hiding that bother.

[*]Dependencies are awesome for developers. Package a program, say "this needs sqlite, the Mono runtime and goocanvas" and have that automagically work for users. The Windows version, on the other hand, tends to be absolutely horrible for end users since it demands they install such things themselves. Developers must hand-tune their installers to deal with the dependencies since Windows Installer alone doesn't cut it. Some developers are better at that than others.[/list]

Merge these points in your mind - through careful dependency management, Mono's footprint in Jaunty has shrunk

---

### Post by cardinals_fan on 2009-03-30
> **shadoweva00 said:**
> But it's the software makers that have to deal with it, not the distro maintainers.
And why on earth is this good?!  The operating system is supposed to provide a base and then get out of the user's way.  The software they use is what matters, so why would you possibly want to make it harder to write?  The whole job of a distribution is to package third party software into a usable set.  Handling dependencies and adding packages to the repositories is their job.  Third-party software developers are absolutely essential for any OS to succeed - you don't want to make it hard for them.
> **shadoweva00 said:**
> Proving that the community hates people? Everyone must be programmers willing to take months of their time to fix a product they believe to be broken in the first place. If you don't listen to complaints or suggestions, you're the biggest problem with Desktop Linux ever. That's right, you're really just proving the community is the biggest problem with Desktop Linux by not properly responding to any criticism, no matter how valid.
I listen to complaints **and** suggestions.  Just not when they have ridiculous "catches" that totally stifle the actual discussion.  See the next comment.
> **shadoweva00 said:**
> Users don't care about shared libraries, nor do they ever affect usability. DLL is from bad programmers, an OS can't protect you from that. This is all about what affects the user.
Do you know why users don't care about and don't have to worry about shared libraries?  Because someone else does it for them.  It's one thing to say "I'm a user, and I don't care about shared libraries".  That's your choice.  But trying to demand changes to an operating systems core design while loudly trumpeting that nobody cares about that core design is madness.  Somebody has to care about the technical details for everything to work.  That somebody doesn't have to be you, but you can't complain about the way things are without recognizing that they are that way for a reason.
> **shadoweva00 said:**
> Because you've become the enforcers of the status quo, and completely killed off any chance that it will change and become better like open source is supposed to. By agreeing with other people that dependencies are the best way to do things, not doing objective comparisons to other systems, and not admitting faults, you are now the enforcers of a status quo for Desktop Linux. All changes that could make it possibly better are now killed of by your community because you think it's the best way to do things. Things like market share and usability are irrelevant next to small technical details the average use should never know of, Even though this kind of thinking is the most hypocritical thing to ubuntu bug #1. The ignorance and immaturity goes all the way to the top of each distro. Essentially you've all made the idea of open source becoming better the biggest lie of all because you're always standing in the way of it.
There is nothing wrong with change.  Nor is there anything right.  The question is whether the individual change in question is *good*.  I just don't understand how what you propose is better.  If the application you want is not in the repositories, you should petition to get it added.  Otherwise, you only need to worry about dependencies if you choose to (as I do).

Security arguments are very relevant in this context.  While PC-BSD may have found that chroot jails solve security issues (I haven't done enough research on their particular solution to comment on it), the fact is that BSD systems have far more sophisticated jail systems than Linux.  This is one of the many great things about BSD.

If you are having dependency issues, have you considered that the problem may just be with that particular package and not with the system itself?

---

### Post by basenvironment on 2009-05-05
As a user, I do not want fifty copies of libX on my system to be vulnerable to a flaw. Dependencies are better because I only have one copy of libX on my system. I update one lib and I am safe instead of trying to update fifty programs in order ot be safe.

next question please...

---

### Post by lswb on 2009-05-05
> **shadoweva00 said:**
> To me it seems dependencies are the root of 99% of user problems not related to hardware.


In 4 years of using ubuntu and other debian-style distributions and installing probably a couple or few hundred programs, I can only recall 1 instance of a dependency problem affecting a program installed from a distribution repository. And of course that is a bug in the package, isn't it? I don't agree with that 99% observation. Ordinary bugs in the programs themselves are FAR more common. 

Typical users have little if any need to go outside official repositories for their software IMHO. 

Remember that if programs were statically compiled and linked, not only would their on-disk size increase, but their memory footprint would also rise substantially as each running program dragged in redundant but identical code for common functions.

---

### Post by maybeway36 on 2009-05-05
If I were distributing a commercial Linux program, I would make an X11 installer app that finds and installs known dependencies from the web based on the distribution you're running, then installs the program.

---

### Post by mobilediesel on 2009-05-05
> **shadoweva00 said:**
> See, if you just admitted that self contained installers like those of windows, mac, and PCBSD make the system "just work" far more than dependencies ever will, Ubuntu can be a much better competitor.

Yeah, that's so awesome when a Windows installer replaces a dll with an older version because few of them check existing versions.

Some of them do get around that problem by installing their "dependencies" in their own locations so you end up having 30 or 40 copies of the same dll all over the place. Then when you have programs that use more than 1 dll file, you have 30 or 40 copies of 3 or 4 dlls each.

Dependencies in Ubuntu or any version of Linux may not be perfect, but it sure is less imperfect than the Windows way.

---

### Post by basenvironment on 2009-05-05
> **lswb said:**
> I
Remember that if programs were statically compiled and linked, not only would their on-disk size increase, but their memory footprint would also rise substantially as each running program dragged in redundant but identical code for common functions.
good point

---

### Post by basenvironment on 2009-05-05
> **mobilediesel said:**
> 
Dependencies in Ubuntu or any version of Linux may not be perfect, but it sure is less imperfect than the Windows way.

too true, it sucks less... :lolflag:

---

### Post by swoll1980 on 2009-05-05
> **shadoweva00 said:**
> 

(Anyone who mentions dll hell, shared/dynamic libraries, and security issues fails. Only usability issues are valid arguments here. 

Correct me if I'm wrong here, but if I were in dll hell, wouldn't I be having usability issues. You can't separate technical aspects, from usability ones. If a system isn't technically sound, it won't be very usable. Will it? Stricly from a usability stand point, I don't see what is so god damned hard about sudo apt-get install/remove whatever.

---

### Post by basenvironment on 2009-05-05
I think the OP figured he would have to be proven 'right' if he ruled out any technical basis of discussion....sadly even that did not work...

---

### Post by happysmileman on 2009-05-05
Personally I don't want to have to install a new copy of KDElibs/Qt every time I install a KDE app.
But maybe that's just me being stupid for thinking of technical reasons, like not wanting to spend hours downloading, or not wanting every application I install to take up at least twice as much space (for smaller apps maybe several dozen times as much as it does using the horrible way it's done now).

I guess I just don't care about usability.

Oh and the reason Mac and Windows (not sure about PC-BSD) can do this is because they come with a full DE, WM and their own GUI toolkit, which a majority of programs use, individual apps generally just pull in one or two dependencies so they bundle them, partially because it's not worth the hassle for just one or two, partially because there is no package manager for Windows.

Whereas on Linux you can't expect KDE/Qt to be installed for any KDE/Qt app to use, nor can you expect Gnome/GTK to be installed for any Gnome/GTK app to use, I'd prefer not to have several dozen copies of these (large) libraries on my system, along with even more copies of all the X libraries.

> Can you possibly defend them if you aren't thinking about technical details and only in terms of usability?
Could you possibly use a computer if no-one ever thought of technical details, only usability? What about a car? Television? Radio?

If you don't want technical answers then don't ask a technical question.

---

### Post by happysmileman on 2009-05-05
Double Post

---

### Post by zakany on 2009-05-05
> **red_Marvin said:**
> If I have a toaster and a washing machine that I need to fix, and they are both put together with the same kind of screw, it makes sense to me to only buy one screwdriver of that kind, and use it to fix both machines.

Fiberboard furniture all uses the same Allen wrench, but you get one in every box.

---

### Post by swoll1980 on 2009-05-05
> **zakany said:**
> Fiberboard furniture all uses the same Allen wrench, but you get one in every box.

It only needs one tool though. Bad analogy. If every program had only one dependency it wouldn't be a problem to include it. Imagine if you had 40 cars, and you were forced to keep a  toolbox for each car, even though a lot of them were duplicates. Wouldn't it make sense if you could use the same tools for more than one car? I don't go out, and get a new wrench every time I need to unfasten a 5/8 nut.

---

### Post by basenvironment on 2009-05-05
> **zakany said:**
> Fiberboard furniture all uses the same Allen wrench, but you get one in every box.
....but they don't need to do so, since you already have what you need

---

### Post by happysmileman on 2009-05-05
> **zakany said:**
> Fiberboard furniture all uses the same Allen wrench, but you get one in every box.

Because maybe this is your first piece of furniture or you lost the other ones.

With software the package manager knows for certain whether you already have the tool or not, which is different.

---

### Post by mkvnmtr on 2009-05-05
Was this thread a joke? If so it has succeeded. It is very funny.

---

### Post by piousp on 2009-05-05
1) Dont feed the troll
2) On the other hand, we need to *make* this thread longer than gentoo's :lolflag:

---

### Post by basenvironment on 2009-05-05
oh okay...

---

### Post by piousp on 2009-05-05
I know, i know....

---

