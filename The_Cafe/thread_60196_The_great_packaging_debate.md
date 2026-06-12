---
title: "The great packaging debate"
date: 2005-08-26
forum: The Cafe
---

### Post by npaladin2000 on 2005-08-26
First, I know the chances of Ubuntu switching package management is zero unless Debian does, and Debian ain't gonna. :D

With that out of the way, there's a bit of excitement going on in the area of package management these days.  It's no longer the old APT vs. RPM debate with APT the clear winner.  APT-RPM has been around for a bit, though it'd no longer supported.  Yum has matured well, though no frontend has come really come out on top as "THE" frontend like Synaptic has for APT (Kyum is one of the best, but it's KDE, gnome-yum is pretty good, Yumex is desktop neutral I believe, but well short in function and still maturing, Gyum seems to be history). 

URPMI is still hanging around but I never hear much about it.  Maybe because of this guy and his SmartPM project? [http://smartpm.org/](http://smartpm.org/)  Looks like a really interesting development, but I haven't tried it out yet.  The concept is pretty good, and might even start to unify package management a bit in Linux (While not a unified packaging system, at least it would be a unified frontent, which is a start).

Then there's things like Emerge, which is a pretty decent way of handling source packages, and slapt-get, which is a slavish Slackware clone of apt-get. :)

Now, I realize that talking about packaging is right about on the same level as arguing vim vs. emacs (where I don't care since I use Nano) or one religion versus another (again, don't care...3rd party religion too, heh). But I'm gutsy. :)

Anyway, so what's your stance on where packaging in Linux is going?  with stuff like slapt-get and emerge and pacman coming out, is it fragmenting even more than before?  Will SmartPM have a chance at starting to unify packagemenagement a bit?  Am I smoking something really illegal? And, if so, do you want some?  O:)

---

### Post by az on 2005-08-26
When I first learned that you downloaded stuff directly from a repository when you installed things in Debian I felt funny about it.  Then I learned what it meant to package something for debian.  I read up on the Debian Developer process and the high standards that they meet.

I read up about how strongly they beleive in free-libre software.  I read the mailing lists and quickly realized that they mostly all have brains the size of a planet.  They are pretty much the perfectionists of an already highly sophisticated world of software.

A .deb is so much more than just a package which contains files and scripts.  It is a distillation of the very thing that makes free software so powerful - a distributed matchmaking of the best (wo)man for the job to the piece of software for which they are responsible.

That's all I have to say about that.

---

### Post by Gnobody on 2005-08-26
We don't need unification of package managment systems, what we need is all distributions to have an online repository of software that it is up-to-date and contains everything the user ever needs.  Who cares if packages are compatible when downloading your software through a web browser is obsolete?  In a few years, will the average user even need to manually submit themselves to dependancy hell?  

For the rare occurrence that you need a commercial game or suite, (that comes on old fashion optical media or from a website)  I'd recommend publishers use autopackage or something like installshield.

Ubuntu should expand it's universe more and with a greater emphasize on backports, especially as Ubuntu itself matures.

Linux <> Windows or Mac OS 
Management of your software can be much EASIER because it is all free and released under similar licenses so it makes things that are impossible in the old closed source world, possible!

---

### Post by Gnobody on 2005-08-26
I would like to see the Redhat world improve their software management situation.  Apt4rpm is the best solution for rpm distros, yet it is neglected big time.  The Fedora/SUSE/Mandriva philosophy is to bundle everything you need on the installation media (making it harder to obtain for new users) and to lightly use a half-broken package managment system like yum, or urpmi.  I have used Mandrake and Fedora in the past, this is not a bash against them but I really wish they'd become more Debianish!

---

### Post by John Nilsson on 2005-08-26
The only thing I can see that has the chance to be a deb replacement is conary.

I haven't looked at RPM for a while but I hear it hasn't improved much. Portage is WAY to cenralized. Autopackage and those other new things are really just for third parties. I think the future is that the Distro will manages system stuff with whatever fits the bill. I sense the possibility that Mr Suttleworth will push for either a deb/baz hybrid or conary in the near future though.

Applications will have their own way of dealing with it. Look at eclipse or azureus. I have booth installed in ~/opt letting their inclided package managment do what it does best.

---

### Post by drizek on 2005-08-26
smartpm was made by the same guy that devlopes(d) synaptic AFAIK, and it wipes the floor with apt as far as im concerned. 

i used to have smartpm installed in mepis, but i would use synaptic by default because it is more stable/tested for now at least. however, whenever synaptic started giving me crap, i would load up smartpm and it would do wantever i told it to without a fight. it is better at solving depends and "impossible" situations. a lot of the problems people are having apt-getting to breezy or even errors when installing hoary from a cd are a result of apt.

that aside, smart has the capability of being **THE** linux package manager. not only is it more advanced than the current solutions, it supports both deb's and rpm's. it also supports installing foo.deb from your desktop, you dont _have_ to download something off of a repository. right now, we need kpackage+kynaptic and gnome-app-install+synaptic+ubuntuupdatenotifiersystemtraythingy. smart has the capability of doing all of that with just one app.

---

### Post by GeneralZod on 2005-08-27
[QUOTE=John Nilsson]

Portage is WAY to cenralized. Autopackage and those other new things are really just for third parties. [/QUOTE]

Interesting - I consider the centrality (if that's even a word :)) to be one of its greatest strengths.

Actually, I have a quick question about packaging - if two versions of libraries contain exactly the same functions, interfaces and constants (i.e. only the actual implementation has been changed), can a package compiled against the earlier version work with the newer version, and vice-versa? I ask because I've had a few failed package installed because the version of, say, libc is very slightly behind ("Very slightly" as in x.y.z-ubuntu13 vs x.y.z-ubuntu21).  I'm surprised that such a mature and fundamental library would change so radically with a sub-minor-point release as to no longer be compatible with the old version, so I'm guessing there's something more complex at work here. 

Can anyone in the know elaborate on this? Would a more sophisticated dynamic linker improve matters....?

Cheers!

---

### Post by slux on 2005-08-27
The problem with contemporary package management is that it means a huge amount of duplicated work and as the amount of free software grows, so does the work. 20 different distributions all go through hoops to package the same things and *none* of them has everything.

That's not to say I don't like the system but I see that as a big issue that needs to be solved somehow.

[Conary](http://wiki.conary.com/) which was already mentioned seems quite interesting in that it distributes the package sources and reduces packaging work (also fixes the problem of always having to download whole packages when little has changed) but it does not seem to solve this particular problem. Anyone used it? What's it like in daily use?

For the work duplication problem the mots often offered solution these days seems to be [AutoPackage](http://www.autopackage.org/). I understand it has some bad flaws at least from a distribution package maintainer's view but it's still an enlightening experience to try an autopackage on a random distribution, see it find some of it's dependencies, install the remaining by itself and have a working application as a result.

SmartPM looks interesting but doesn't really seem to bring anything actually new to the table according to the blurb.

---

### Post by weasel fierce on 2005-08-27
Personally, I think the apt-get / debian way is rather neat and straightforward.

---

### Post by John Nilsson on 2005-08-27
[QUOTE=slux]The problem with contemporary package management is that it means a huge amount of duplicated work and as the amount of free software grows, so does the work. 20 different distributions all go through hoops to package the same things and *none* of them has everything.

That's not to say I don't like the system but I see that as a big issue that needs to be solved somehow.

[Conary](http://wiki.conary.com/) which was already mentioned seems quite interesting in that it distributes the package sources and reduces packaging work (also fixes the problem of always having to download whole packages when little has changed) but it does not seem to solve this particular problem. Anyone used it? What's it like in daily use?

For the work duplication problem the mots often offered solution these days seems to be [AutoPackage](http://www.autopackage.org/). I understand it has some bad flaws at least from a distribution package maintainer's view but it's still an enlightening experience to try an autopackage on a random distribution, see it find some of it's dependencies, install the remaining by itself and have a working application as a result.

SmartPM looks interesting but doesn't really seem to bring anything actually new to the table according to the blurb.[/QUOTE]
 The problem is that for dependency resolution to function you must have a controlled namespace so you can state things like, package A depends on B, package C and D provides B in a way compatible with A. This is as yet an unsolved problem to handle on a global scale. I don't think IANA is the way to go. Mabey an RDF network...

Mabey dependencies should be stated in a more detailed way. I.e. package A need symbols x,y and z from the system lib, and a service that implements RFC###,### and ### together with org.freedsektop.someStandard



On top of that you must have controll over what the packe installs and where so you can handle it in a way suitable for your Distro. Conary goes a long way to provide this as everything in the package (or trove as they call it) is tagged with a somewhat semantic meaning.

---

### Post by mhearn on 2005-08-31
[QUOTE=John Nilsson]The problem is that for dependency resolution to function you must have a controlled namespace so you can state things like, package A depends on B, package C and D provides B in a way compatible with A. This is as yet an unsolved problem to handle on a global scale. I don't think IANA is the way to go. Mabey an RDF network...

Mabey dependencies should be stated in a more detailed way. I.e. package A need symbols x,y and z from the system lib, and a service that implements RFC###,### and ### together with org.freedsektop.someStandard



On top of that you must have controll over what the packe installs and where so you can handle it in a way suitable for your Distro. Conary goes a long way to provide this as everything in the package (or trove as they call it) is tagged with a somewhat semantic meaning.[/QUOTE]
 A better way would be to eliminate dependencies entirely. For now, autopackage leverages DNS to provide its namespace.

---

### Post by John Nilsson on 2005-08-31
Eliminate dependencies... how? why?

---

### Post by az on 2005-08-31
[QUOTE=GeneralZod]Interesting - I consider the centrality (if that's even a word :)) to be one of its greatest strengths.

Actually, I have a quick question about packaging - if two versions of libraries contain exactly the same functions, interfaces and constants (i.e. only the actual implementation has been changed), can a package compiled against the earlier version work with the newer version, and vice-versa? I ask because I've had a few failed package installed because the version of, say, libc is very slightly behind ("Very slightly" as in x.y.z-ubuntu13 vs x.y.z-ubuntu21).  I'm surprised that such a mature and fundamental library would change so radically with a sub-minor-point release as to no longer be compatible with the old version, so I'm guessing there's something more complex at work here. 

Can anyone in the know elaborate on this? Would a more sophisticated dynamic linker improve matters....?

Cheers![/QUOTE]

Let's say I make libfoo, a library that does "foo"

A year later, I find a better way to do "foo" since "foo" now use HAL instead of devfs (stay with me).  Since it is "foo" but it is different, I call it "libfoo2.0"

In february, I add a few functions to libfoo2.0.  I call it libfoo2.1

Everything I can do with libfoo2, I can do with libfoo2.1  I can even do more with libfoo2.1, but not with libfoo2.0

So, my friend started to write an application in January and her package depends on libfoo2 >2.0.  It can work with libfoo2.0 and libfoo 2.1.

My other friend started work on his project in February and uses the new functions I made in February.  His application depends on libfoo2.1, and will not run with libfoo2.0.

Does that answer your question?  I could go on, but I think less is more, at this point.

---

### Post by npaladin2000 on 2005-09-01
[QUOTE=mhearn]A better way would be to eliminate dependencies entirely. For now, autopackage leverages DNS to provide its namespace.[/QUOTE]

Sorry, but eliminating dependencies is a:
[I]
[B][SIZE=7]REALLY DUMB IDEA!!!![/SIZE]
[/B][/I]

Dependencies are what keep Linux apps so much smaller than their Windows equivalents....shared libraries and such.  Most windows applications componentize, sure, but they're not often shared...the DLLs are specific to each application, so basically each app ends up being one large, monolithic, statically-linked block.  

Dependencies are fine if handled properly, and if programs are written intelligently (that is, to not depend on a library that is TOO old...keep up with your libraries).  APT, Yum, URPMI, and SmartPM can handle resolving dependencies fine; this isn't the days of dependency-hell anymore....well, unless you use certain distros. :)

---

### Post by GeneralZod on 2005-09-01
[QUOTE=azz]Let's say I make libfoo, a library that does "foo"

A year later, I find a better way to do "foo" since "foo" now use HAL instead of devfs (stay with me).  Since it is "foo" but it is different, I call it "libfoo2.0"

In february, I add a few functions to libfoo2.0.  I call it libfoo2.1

Everything I can do with libfoo2, I can do with libfoo2.1  I can even do more with libfoo2.1, but not with libfoo2.0

So, my friend started to write an application in January and her package depends on libfoo2 >2.0.  It can work with libfoo2.0 and libfoo 2.1.

My other friend started work on his project in February and uses the new functions I made in February.  His application depends on libfoo2.1, and will not run with libfoo2.0.

Does that answer your question?  I could go on, but I think less is more, at this point.[/QUOTE]

Thanks for the response, but that's not quite what I was asking :) I've seen a few packages that apparently have a very strict dependency on a specific version of a library, even though earlier or later libraries almost certainly present the same interface.  The example I'm most interested in is libc which, as mentioned, has a few packages requiring a very specific version that it is ever-so-slightly higher than that provided with Ubuntu.

Now, given that the newer library is so incrementally ahead of the one provided with Ubuntu (it's not even a minor point release higher!) I can't imagine that the API could have changed, so am wondering why the old package can't be used instead? Granted, it may not work as well as the newer version (perhaps the newer version contains a few optimisations not found in the old), but to simply not work at all? It seems odd to me.  So either the packaging was unreasonably strict about what versions of the library it could use, or libraries that have identical APIs can't be used in place of each other.  

I was basically just wondering why so many packages are insisting on this very specific version of libc which I can't get :)

---

### Post by poofyhairguy on 2005-09-01
[QUOTE=slux]The problem with contemporary package management is that it means a huge amount of duplicated work and as the amount of free software grows, so does the work. 20 different distributions all go through hoops to package the same things and *none* of them has everything.

That's not to say I don't like the system but I see that as a big issue that needs to be solved somehow.[/QUOTE]

I fix it a lot myself. My tool is called Alien. I like to convert those Mandrake RPMs to the dark side!

---

### Post by neighborlee on 2005-09-02
[QUOTE=drizek]smartpm was made by the same guy that devlopes(d) synaptic AFAIK, and it wipes the floor with apt as far as im concerned. 

i used to have smartpm installed in mepis, but i would use synaptic by default because it is more stable/tested for now at least. however, whenever synaptic started giving me crap, i would load up smartpm and it would do wantever i told it to without a fight. it is better at solving depends and "impossible" situations. a lot of the problems people are having apt-getting to breezy or even errors when installing hoary from a cd are a result of apt.

that aside, smart has the capability of being **THE** linux package manager. not only is it more advanced than the current solutions, it supports both deb's and rpm's. it also supports installing foo.deb from your desktop, you dont _have_ to download something off of a repository. right now, we need kpackage+kynaptic and gnome-app-install+synaptic+ubuntuupdatenotifiersystemtraythingy. smart has the capability of doing all of that with just one app.[/QUOTE]

I read the website for smartpm and I agree with your assessment 100%, and the linux world would be wise to consider it head on, because it can replace what is otherwise 'broken' in both camps and that includes ALL distros that utilise apt and rpm...;-)

cheers
nl

---

### Post by f76 on 2005-09-14
I might sound like the village idiot but couldnt a list be maintained of what versions of a library that a program does not work with? That way an installer/the program could fetch an older version of a lib if necessary and keep a parallel copy...? 

But i guess the you would run into problems when u have two copys running at the same time... See, I am an idiot.

---

### Post by bob_c_b on 2005-09-14
Havng spent all my formative Linux years in RPM based distros I originally thougt URPMI was the best it could get, but I feel apt is far better and the Synaptic front-end is about as simple to understand as it gets. I'm all for a "better" solution, but with my current experience I now understand why Debian is so respected.

---

### Post by gflores on 2005-09-14
Someone made the claim that the days of dependency-hell is no more. Is this accurate? I've read about many people having problems with dependencies (including someone in this thread).

---

### Post by John Nilsson on 2005-09-15
[QUOTE=gflores]Someone made the claim that the days of dependency-hell is no more. Is this accurate? I've read about many people having problems with dependencies (including someone in this thread).[/QUOTE]
 I've had very much "dependency-hell" using ubuntu. Mainly when I tried to upgrade to breezy, but only using hoary-backport puts introduces a few problems.

The strange thing is that while using Gentoo I never had theese kind of problems. I haven't studied the issue, but I think that portage is inferior to apt in dependency resolution features...

---

### Post by MrBrownstone3g on 2005-09-19
I believe that people think one packaging method fits all and unfortunatly it doesn't.
APT and RPM are perfect for the control of distrobutions and their core components. 
They aren't that easy to use for the end user especially those who have migrated from a non *nix OS.  I think that application packages should be supplied in Autopackage format or even a desktop agnostic version Klix, from the the KDE project.

Another interesting *nix packaging method could be a port of the PBI installer from the PC BSD project when it becomes stable and performance and stability can compared fairly to the older technology such as APT/DPKG or the BSD ports system.

---

### Post by poofyhairguy on 2005-09-19
[QUOTE=MrBrownstone3g]  I think that application packages should be supplied in Autopackage format or even a desktop agnostic version Klix, from the the KDE project.[/QUOTE]

I have a good counterpoint to that:

Autopackage and Klik are basically beta projects right now. Apt-get is a "enterprise" class product. I don't think anything should switch over till the technology is ready.

---

### Post by bsussman on 2005-09-19
[QUOTE=gflores]Someone made the claim that the days of dependency-hell is no more. Is this accurate? I've read about many people having problems with dependencies (including someone in this thread).[/QUOTE]

In a non-trivial system (anything useful) dependency management is both necessary and difficult.

What makes it work is coordinated release mannagement, allowing projects that share code (libs, open apps, etc) to plan releases so that you do not get deadlocks and mismatches.

I think the linux community has been pretty good about this, but it ain't easy.

BTW, I really like Synaptic/APT/dpkg (dpkg being the packager, apt the dependency engine and Synaptic the Gooey interface). The division of function is nice, the operation smooth and as long as the maintainers know what their stuff depends on, us users will continue to enjoy life without 'doesthisworkwiththat' hell.

---

### Post by Kuolio on 2005-09-19
I like portage and apt to be the best. I use them both quite often, as my desktop-pc has gentoo and my lappy runs ubuntu flavored linux. But you gotta keep it in mind that not every packagemanaging system is for everyone, i.e. portage is not for beginning linuxusers who are afraid of cli, and that's just fine because it has never been meant to be for that kind of people. That's why gentoo uses it, as it is very efficient and great when used correctly, has trillions of options, and atracts the "enthusiast" audience wich is the "market segment" of Gentoo. They realy don't like to atract new linux users, as they like to keep it as "the (educating) enthusiast distribution".

Apt falls somewhere in between of "enthusiast" and "beginners" as the ease-of-use is concidered (when used from cli), and makes a great effort of being very beginner friendly with Synaptic-GUI.

Hmm, and what else is there that i know of.. well, rpm's are very bad and i dont recommend anyone to use them, I have had so many bad experiences with dependencys with distros relying on .rpm packages. Conary I have briefly tested, and it seemed promising, same as arch-linuxes Packman. Packam especially was kinda fun, and I'm thinking maybe doing a testmachine just to get to play with it.

---

### Post by jdong on 2005-09-19
[QUOTE=GeneralZod]Interesting - I consider the centrality (if that's even a word :)) to be one of its greatest strengths.

Actually, I have a quick question about packaging - if two versions of libraries contain exactly the same functions, interfaces and constants (i.e. only the actual implementation has been changed), can a package compiled against the earlier version work with the newer version, and vice-versa? I ask because I've had a few failed package installed because the version of, say, libc is very slightly behind ("Very slightly" as in x.y.z-ubuntu13 vs x.y.z-ubuntu21).  I'm surprised that such a mature and fundamental library would change so radically with a sub-minor-point release as to no longer be compatible with the old version, so I'm guessing there's something more complex at work here. 

Can anyone in the know elaborate on this? Would a more sophisticated dynamic linker improve matters....?

Cheers![/QUOTE]

Umm, no, not usually. You're asking two completely different questions in one:

First of all: Is there always a common denominator with library versions and compatibility? **NO -- there isn't**. There are a large number of reasons for compatibility breakage, and any nature source change can cause issues.

Second: You're surprised of 'radical' changes to mature libraries: No, not radical changes... that's simply the way things work. Explanations get long and hairy, but just know that any changes to the exported ABI will cause breakage.

Would a more sophisticated ld improve matters? Well, umm, I don't feel too qualified to answer that. I can say that some languages (Python, CIL based) that use an intermediate language have much better compatibility, provided that source code level changes are compatible.


Of course, you can take the PC-BSD approach and statically link everything together. This means Windows-style enormous executables for the smallest of programs, poor loading times, and lack of management when it comes to library updates.

---

### Post by John Nilsson on 2005-09-19
I think the field of package managers are a bit confused at the moment. There are so many problems that people try to solve under the same name, 'package managment'.

Here is a short list of what I think the current requirements is.

1. Update management.
1.1 Know when updates are availible.
1.2 Be able to differentiat between kinds of updates. E.g, stable/unstable, security-fix,  critical bug patches.

2. Dependency managment
2.2 Resolve library symbol dependencies
2.3 Resolve system service dependencies
2.4 Resolve intrapackage deps (what src gave what bin in what way?)

3. Installation managment
3.1 Keep track of installed files for later uninstallation
3.2 Keep track of diffs between original files and local changes
3.3 Downloads


This fairly trivial and naive list (most package mangment systems handle much more complex cases than this) allredy exposes a lack of features in nearly all systems.

Conary is the only one that does 2.4, Portage and conary is rather alone in the 3.2 case. None provides a nice integration with apps with their own package mangment, like firefox extensions, eclipse and azureus, ruby gems, cpan or php pear

What strikes me as most odd is that absolutley noone provies an easy way of installing a local branch of a projects CVS HEAD. This is after all OSS...

No "package managment" is an unsolved problem and I very much doubt that msi-files are the right thing...

---

### Post by GeneralZod on 2005-09-20
[QUOTE=jdong]Interesting Stuff[/QUOTE]

Thanks for the info :) I'm wondering why an implementation-level (i.e. not interface-level; not changing the signature of any exposed functions, etc) change would affect the ABI so.  

Hopefully we'll see a gradual switch to using high-level languages like Ruby for end-user apps, with the key libraries either written in these languages or, if they need the performance, written in C with Ruby/ Python/ Blah bindings.  Then if one of the key libraries is upgraded, it should Just Work if the library itself is written in Ruby etc, or will at most just need the bindings updated.

---

### Post by Knome_fan on 2005-09-20
First off, as smart has been mentioned several times already, Gustavo Niemeyer, the main developer of smart, is now working for Canonical:
[http://www.livejournal.com/users/gniemeyer/11415.html](http://www.livejournal.com/users/gniemeyer/11415.html)

About dependancy-hell:
In my experience this really isn't a problem anymore, if you stay with the "normal" way of installing stuff on your distro. Problems start if you want to install things that aren't provided for your distro, or if you start to wildly add repositories that aren't meant to work with your distro, e.g. if you stay with the official ubuntu repos and backports you won't run into problems, if you add repos meant for debian, you probably will.

There is however an other problem that hasn't really been addressed here yet:
There is no easy way for developers to package their software in a way that makes it usable for most users. 
This of course does also hold true for development versions, as John Nilsson mentioned, which is a problem as these versions do need testing, artwork, translations, etc.

I think autopackage and klik are two ways to address this problem.
Btw., there's an intersting article by Kurt Pfeifle about klik and what it could mean for development:
[http://dot.kde.org/1126867980/](http://dot.kde.org/1126867980/)

---

