---
title: "Unify package management (rpm, deb, emerge, whatever)"
date: 2008-01-04
forum: Ubuntu Brainstorm
---

### Post by mangar on 2008-01-04
IMHO, there's no technical reason to have multiple formats of package management systems (since they all solve the same problems), and it will  help create a broader foundation for the linux distros (in addition to the LSB).

proposal: 
create a metapackage manager, with legacy backends to existing package managers (deb, rpm, emerge, whatever) - unlike autopackge or smart package management, that, together with the LSB, will allow some measure of interoperability between different distros.

---

### Post by Auria on 2008-01-04
Would be damn cool, but just wait and see the flame war that will arise here and will uinderstand why it is not possible :(

---

### Post by stokedfish on 2008-01-04
Big fat **YES**!

---

### Post by smartboyathome on 2008-01-04
This will never happen, since people like different things, and each package format is a little different and bring something different to the table.

---

### Post by Bou on 2008-01-05
So, what's the practical difference between a .deb package and an .rpm?

---

### Post by 23meg on 2008-01-05
[QUOTE=mangar]proposal:
create a metapackage manager, with legacy backends to existing package managers (deb, rpm, emerge, whatever)[/QUOTE]

It exists: it's called PackageKit, and will probably be integrated into Ubuntu in Hardy+1. But the interoperability part is beyond the scope of package management.

LSB 4.0 is also set to introduce a cross-format package API: 

[http://www.linux.com/articles/59502](http://www.linux.com/articles/59502)

[QUOTE=smartboyathome]
This will never happen, since people like different things, and each package format is a little different and bring something different to the table.[/QUOTE]

It's already happening.

---

### Post by xelapond on 2008-01-06
Correct me if I am wrong, but isn't this what [Alien]("http://http://kitenet.net/~joey/code/alien/") Tries to do?  It works, so maybe just writing a GUI for it would be easier.

---

### Post by maybeway36 on 2008-01-06
Adding a new package format will only add another package format. The way to go is making .deb packages work on Red Hat/Mandriva/etc. and rpm packages work on Debian/Ubuntu. In other words, an alien GUI.

---

### Post by 23meg on 2008-01-06
[QUOTE=maybeway36]The way to go is making .deb packages work on Red Hat/Mandriva/etc. and rpm packages work on Debian/Ubuntu. In other words, an alien GUI.[/QUOTE]

That's the typical "symptomatic treatment" approach that will just not work. The problem isn't that RPMs are hard to install on a Debian system; it's that there are multiple packaging formats, filesystem policies, packaging policies and lots of software, which don't have a well established common ground. Unless you establish that common ground and adhere to it, tacking on GUIs to alien package formats won't help; if anything, it can deepen the problem.

---

### Post by Auria on 2008-01-06
That standarisation attempt is a great idea. We need to see how far it goes though

I think at some point Linux will need to split in 2 groups, one for open-source fanatics that wish to remain a small niche, the other group that want sto make linux spdead as much as possible. It saddens me that people of the first group may slow down the adoption of features that would help linux spread in the name of totally unrealistic ideals

---

### Post by jacksaff on 2008-01-07
The problem isn't different package formats - it's very easy to install .rpms on .deb systems and vice-versa using alien. Rather it is that each distro has different versions of various libraries, different default locations for files, their own sets of default packages and so on. Until all this sort of stuff gets standardised to a degree in LSB 4 the solutions will all require some compromises. Things like klik and zero install work very well cross-platform but give up some of the benefits of apt-like package management.
I'd like to see all open source code repositories unified in one huge distributed repo - something like conary maybe. Every distro could patch and package from the same source code. This would make it easier for all distros to help upstream coders as there would be one place to send your patches to (and one place for upstream to communicate with). Plus, if some sort of standardisation finally does occur there will already be one 'place' holding all the code and from which whichever format wins can build it's packages.

---

### Post by lexen on 2008-01-07
What a few people are skipping around, but no one has really said is:  We should integrate alien into synaptic.  Is that an easy fix, or does it create more problems?  I think this discussion should involve the synaptic people.

I have to ask, because synaptic can install from source, doesn't that mean it could just compile the program that could work on any version of linux?  Is there different source code from one distro to another?  I never really understood why programs don't work from one OS to another.  I would really like it if someone could explain that to me.

---

### Post by 23meg on 2008-01-07
[QUOTE=lexen]We should integrate alien into synaptic. Is that an easy fix, or does it create more problems?[/QUOTE]

See post #9.

[QUOTE=lexen]because synaptic can install from source[/QUOTE]

It can't.

[QUOTE=lexen]Is there different source code from one distro to another?[/QUOTE]

Yes, distros apply their own patches to some software, but the majority of the code is common.

---

### Post by lexen on 2008-01-07
Synaptic cant install from source?  Then why do a lot of repositories say deb-src at the beginning?  I thought that stood for Debian Source, but maybe I am off base.

---

### Post by smartboyathome on 2008-01-07
It does stand for that, but those are used with the command line, not with Synaptic itself. Synaptic installs from precompiled binaries for your system. The source packages are used with the command apt-get source.

---

### Post by lexen on 2008-01-07
So synaptic doesn't directly compile the source, but it can with an external program?  If that's the case then the end result is the same

---

### Post by Steveway on 2008-01-07
No. You download the source with that command and then you can compile it like you compile every program.
Also apt-get build-dep <programname> will fetch required libs and programs for compilation.

---

### Post by Jan-Nik on 2008-01-10
autopackage is already a good package for all distributions. Why not improve it instead of creating a new package format? For example integrate it into the package system (e.g. apt-get) via PackageKit.

btw: What does Gah. mean?

---

### Post by smartboyathome on 2008-01-10
I find that autopackage installs stuff - even when you already have it - if it isn't in the place autopackage expects.

---

### Post by zetetic on 2008-01-10
> **Auria said:**
> That standarisation attempt is a great idea. We need to see how far it goes though

I think at some point Linux will need to split in 2 groups, one for open-source fanatics that wish to remain a small niche, the other group that want sto make linux spdead as much as possible. It saddens me that people of the first group may slow down the adoption of features that would help linux spread in the name of totally unrealistic ideals

Please read something before posting silly comments: linux wouldn't exist and wouldn't be so powerful if it weren't the "open source fanatics".

It it weren't the "open source fanatics", linux, it it exists (witch I doubt), would be just another windows.

It's the "proprietary fanatics" like you who give Ubuntu a bad name.

And one last thing: go read something about the differences between "open source software" and "free software"...

If you just want a free (as in free beer) windows, then please just use windows and leave as alone. We don't need people like you.

---

### Post by BigD77 on 2008-01-10
Forgive me for being a noob here, but my problem is that there are programs that I would like to try, but can't because they use RPM.  

A radio automation software called Rivendell looks nice, has features that I like, but it uses RPM.  Can that be loaded into Ubuntu?  If so, how?

[http://www.rivendellaudio.org/](http://www.rivendellaudio.org/) 

It also has .tar archives as well.  Will that work?

[http://www.rivendellaudio.org/rivendell/download.shtml](http://www.rivendellaudio.org/rivendell/download.shtml)

---

### Post by voteforpedro36 on 2008-01-10
It will never happen. I could be wrong, but for some reason I don't doubt myself here.

Compile from source, if you really want something unified.

---

### Post by smartboyathome on 2008-01-11
> **BigD77 said:**
> Forgive me for being a noob here, but my problem is that there are programs that I would like to try, but can't because they use RPM.  

A radio automation software called Rivendell looks nice, has features that I like, but it uses RPM.  Can that be loaded into Ubuntu?  If so, how?

[http://www.rivendellaudio.org/](http://www.rivendellaudio.org/) 

It also has .tar archives as well.  Will that work?

[http://www.rivendellaudio.org/rivendell/download.shtml](http://www.rivendellaudio.org/rivendell/download.shtml)

You can alien the package (make sure alien is installed through synaptic). Once it  is installed, run:

```
sudo alien -i pathto.rpm package.deb
```

---

### Post by ryanVickers on 2008-01-11
I have to say we MUST standardize on ONE format across the board!!  every package or installer needs to be the same, they could call it <package>.ulp or something for universal linux package ;)

---

### Post by smartboyathome on 2008-01-11
ryannVickers, even if a universal package format was made and implimented on OpenSUSE, Ubuntu, and Fedora, there would still be distros that could take it out and replace it with their own, meaning that the package format would not be "universal". I would say the only universal package is going to be the .bin packages and tarballs.

---

### Post by ryanVickers on 2008-01-11
unfortunately, your probably right... I guess thats the one thing windows has got on is, all window's can use an exe or msi

---

### Post by BigD77 on 2008-01-11
> **smartboyathome said:**
> You can alien the package (make sure alien is installed through synaptic). Once it  is installed, run:

```
sudo alien -i pathto.rpm package.deb
```


Thanks.  Is alien part of the add/delete repository?

---

### Post by smartboyathome on 2008-01-11
I don't know, but if you search with synaptic for alien it should be close to the top.

---

### Post by Jan-Nik on 2008-01-12
> **smartboyathome said:**
> I find that autopackage installs stuff - even when you already have it - if it isn't in the place autopackage expects.

That could be solved with [PackageKit](http://packagekit.org) and the developers are already thinking about this.

> I have to say we MUST standardize on ONE format across the board!! every package or installer needs to be the same, they could call it <package>.ulp or something for universal linux package 
There's already autopackage, it only needs improvements :)

---

### Post by coolen on 2008-01-14
> **smartboyathome said:**
> ryannVickers, even if a universal package format was made and implimented on OpenSUSE, Ubuntu, and Fedora, there would still be distros that could take it out and replace it with their own, meaning that the package format would not be "universal". I would say the only universal package is going to be the .bin packages and tarballs.

I don't see that as a problem. Interoperability is in the best interests of everyone: it makes it easier (in the long run) for individual distros, users, and developers.


As for the idea, it is a fantastic one. I can't wait for the day this becomes standard. It'll be a great day for Linux in general, and it will make Linux development much more attractive. You could see more ISVs providing their software for Linux, since they only have to package it once.

The one thing it'd need is the ability to require a license of some kind.

---

### Post by lexen on 2008-01-14
I think the question here, that has already been asked, is can synaptic ever have the ability to install tar files?  A lot of people say no, but the things they say seem so trivial.  The fact that you need to put information in while installing from source could easily be automated.  A pop up window could ask you unique questions and it could automate all information that it already knows the answer to.  

If you had the ability to install from source using synaptic, then all you would have to do is have a repository that contained tar files and make it so it prefers to install from deb files, but if one isn't available or if it is obsolete, then it uses source.

Is there any reason why that couldn't happen?

---

### Post by smartboyathome on 2008-01-14
Yes, and as said before, because the user would have to MANUALLY LOOK THROUGH the ./configure file to find all the dependancies and put them in the file. There is no way a normal user would be able to do it (heck, I would rather compile it manually). Also, there are repos that have source files, but people still have to package it with the required info (see former reason).

---

### Post by 23meg on 2008-01-14
Source tarballs are just source; think of them as raw substance. Source debs are packaged from this substance by distribution developers to work properly in and make sense in the distribution, which means **they contain info as to what exact packages in the distribution contain their build dependencies**. Binary debs (that you download and install via Synaptic, etc.) are built from these source debs.

---

### Post by LaserJock on 2008-01-14
OK, so I'd like to throw in a few thoughts here on a few different aspects of this thread.

1) add alien support to Synaptic

This is a really a bad thing to do and would never be done in Debian or Ubuntu. Simply put, .rpms are not .debs and **cannot** be reliably converted without manual work. It works sometimes for simple applications/packages but I have yet to see it create anything that would meet the packaging standards of Ubuntu. Particular problems are dependency handling and maintainer scripts. Debian-based packaging makes extensive use of pre-/post- install/removal scripts and alien will not give you those because RPMs don't use them. I've used alien myself a few times and have also had to remake packages from scratch after doing so. So, as a last resort alien can be ok (if you know how to build from a source tarball you're generally better off doing so) but it can't be used for official packaging.

2) add a "build from tar.gz" functionality/app

I've seen this suggested quite a few times around the forums and can tell you that this is also not a good idea. There is simply **no** way to automate software building with a high enough success rate to make if feasible. The problem is, sure you can build many apps by running ./configure && make && sudo make install, but there are lots and lots (and an increasing amount from what I can see) of applications that do not use a standard autotools build setup. Off the top of my head there is python distutils, cmake, scons, a plain old makefile, ./install.sh scripts, and sometimes no real build system at all. Now, if you are going to build a program that will "easily build software without having to know anything" you will literally be swamped with bug reports/support requests because building software **requires** people who can read up on dependencies, steps to build, figure out any build problems, etc.

3) we need a packaging format to rule them all or as the thread title says unify them

First of all, I think unifying them all on the same machine just is asking for a mess. The Debian packaging format is very stable and well  tested/optimized but it also doesn't deal well when things happen "outside" of itself. Note that PackageKit is not attempting to unify packaging formats, only the UI used to install software.

Trying to build any sort of automation to create packages or convert between packaging formats is, IMO, going to fail as far as trying to run a distro off of. The different packaging formats were built to address somewhat different things. If you consider that the Debian Policy manual, which all Debian and Ubuntu official packages must adhere to, is 152 pages long and often requires human judgment, you can see why I'm a bit skeptical.

I think that to really make any significant headway towards having some semblance of consistency and ease-of-use, software authors and some standards body will have to figure out a standard way of delivering software in Linux. Distros are too invested in the packaging formats they've invented/inherited to revolutionize build systems.

-LaserJock

---

### Post by coolen on 2008-01-15
I like the idea of PackageKit, particularly the possibility of letting unpriveleged users install/remove software (I made this suggestion a while back for dpkg).

Also, rather than creating one all-ruling format, keeping our individual packages is a good idea: I think this diversity helps Linux. I don't want to see Linux turn into a single distro: The Linux OS. Our current division is good for innovation: one distro decides to go with some sparkly new tech, and the others have to keep up, and go one better. Healthy competition at its best.

However, this package manager API would be invaluable for getting major players' support. Who knows, you might even be able to get Apple to ship a Linux version of iTunes (not that I'd ever use it, but it would make obsolete a full 80% of the requests on these forums).

---

### Post by Jan-Nik on 2008-01-15
> I like the idea of PackageKit, particularly the possibility of letting unpriveleged users install/remove software (I made this suggestion a while back for dpkg).
That's already possible with autopackage, which makes it a good format for the distribution of 3rd party applications.

> Also, rather than creating one all-ruling format, keeping our individual packages is a good idea: I think this diversity helps Linux. I don't want to see Linux turn into a single distro: The Linux OS. Our current division is good for innovation: one distro decides to go with some sparkly new tech, and the others have to keep up, and go one better. Healthy competition at its best.
If autopackage would be THE package for 3rd party applications, there will still be rpm, deb and co, because autopackage isn't a replacement. It fits in the gap, the lack of a "linux-installer" working on all distributions.

> However, this package manager API would be invaluable for getting major players' support. Who knows, you might even be able to get Apple to ship a Linux version of iTunes (not that I'd ever use it, but it would make obsolete a full 80% of the requests on these forums).
They could already use an existing technology: autopackage!

> 
The one thing it'd need is the ability to require a license of some kind.
There shouldn't be any license displayed during the installation process: [http://autopackage.org/faq.html#6_2](http://autopackage.org/faq.html#6_2)

---

### Post by coolen on 2008-01-15
Does autopackage integrate with the native package manager? For example, will I be able to remove a package installed with autopackage through Synaptic?

As for the license display issue, I'll accept the UI vision tactic. However, the inability to display a EULA will probably be a turn-off for proprietary vendors.

---

### Post by smartboyathome on 2008-01-15
> **coolen said:**
> Does autopackage integrate with the native package manager? For example, will I be able to remove a package installed with autopackage through Synaptic?

Nope, it doesn't even handle dependancies real well and sometimes installs other versions of packages over the ones already installed. It reminds me of Windows' EXEs, really. :(

---

### Post by lexen on 2008-01-15
LaserJock and smartboyathome, you guys seem to really know what you are talking about and you both think this is a bad idea.  I agree that there are a lot of problems, but consider what we would gain from this.  You could still have binary packages that would install quickly and work better, but for those of us that cannot install from source would have access to a wider verity of programs.

I will ask you guys this question, if there was not a problem of dependencies, would we be able to have a source compiler integrated with synaptic?

If that is the only problem, then I think we can work something out.  Consider this, what if we had a repository with source code, and the repository itself had a list of dependencies for all of the programs in it?  It seems like a lot of work, but it is a lot easier to write what dependencies a program needs then it is to compile every program in a binary form for every distro you want to support.

Besides dependencies, what problems are we up against.

---

### Post by 23meg on 2008-01-15
[QUOTE=lexen]I will ask you guys this question, if there was not a problem of dependencies, would we be able to have a source compiler integrated with synaptic?[/QUOTE]

We can have it now. Synaptic is a frontend to APT, and with APT you can already use *apt-get source* to grab and build from source packages **that are already packaged in the source repositories**.

[QUOTE=lexen]Consider this, what if we had a repository with source code, and the repository itself had a list of dependencies for all of the programs in it?[/QUOTE]

You're describing the deb-src repositories, which exist. As I said in post #33, binary packages get built from the source packages in these repositories.

[QUOTE=lexen]Besides dependencies, what problems are we up against.[/QUOTE]

None. You're asking for something that already exists, because you're looking for the problem in the wrong place. As said in post #33, in order to have properly packaged binary debs that can constitute the default installation and be added to it, you also need to have properly packaged source debs. And they exist, and you can use them. But of course, the content you get won't be different than the binary packages you can already install from the repositories.

In order for the "raw substance" to be usable the same way as the packaged product, it needs to be processed (read: packaged properly). There's no standardized way of getting straight from a random source tarball provided by an independent developer to a proper Debian/Ubuntu package. It involves manual labor and judgment, and that's the (incredible) job that the Debian maintainers and MOTU do.

---

### Post by Jan-Nik on 2008-01-15
> **coolen said:**
> Does autopackage integrate with the native package manager? For example, will I be able to remove a package installed with autopackage through Synaptic?
Not yet, but this will change when PackageKit is supported.

> As for the license display issue, I'll accept the UI vision tactic. However, the inability to display a EULA will probably be a turn-off for proprietary vendors.
You can display an EULA. And you should do it for every user, when he runs the program for the first time.

> Nope, it doesn't even handle dependancies real well and sometimes installs other versions of packages over the ones already installed.
Well, this will change with PackageKit, too. PackageKit is the layer over every package management system and autopackage can use it to install dependencies. If Hardy+1 gets PackageKit by default, it should also ship a new version of autopackage which uses PackageKit. With this improvement autopackage IS the unified package format we are talking about.

> It reminds me of Windows' EXEs, really.
It's more like Windows' MSI.

---

### Post by coolen on 2008-01-16
If  autopackage will use PakcageKit to install dependancies, why can't vendors just use PackageKit?

---

### Post by 23meg on 2008-01-16
[QUOTE=Jan-Nik]Well, this will change with PackageKit, too. PackageKit is the layer over every package management system and autopackage can use it to install dependencies.[/QUOTE]

Can you cite a source for this? How will an independently made package be made to know what packages contain its dependencies? How does PackageKit help in this regard?

[QUOTE=coolen]If autopackage will use PakcageKit to install dependancies, why can't vendors just use PackageKit?[/QUOTE]

PackageKit is just a frontend that's meant to unify the installation method across distros, while keeping each distro's package management backend.

---

### Post by Jan-Nik on 2008-01-16
> **23meg said:**
> Can you cite a source for this? How will an independently made package be made to know what packages contain its dependencies? How does PackageKit help in this regard?
You can search a package which contains a specific file (e.g. a shared library) with PackageKit. Unfortunately this doesn't work with all backends at the moment (including apt).

---

### Post by 23meg on 2008-01-16
[QUOTE=Jan-Nik]You can search a package which contains a specific file (e.g. a shared library) with PackageKit.[/QUOTE]

You can also do that with dpkg/APT themselves (*apt-file* or *dpkg -S*).

---

### Post by Jan-Nik on 2008-01-16
> **23meg said:**
> You can also do that with dpkg/APT themselves (*apt-file* or *dpkg -S*).

Not in openSUSE.

---

### Post by coolen on 2008-01-16
I know it's a frontend. My point is, why should ISVs settle on yet another package format, with every distro still supporting their own, rather than just use PackageKit to interface with the native package manager? Why have two package managers trying to run the one system?

PackageKit is so attractive because it gives everyone what they want: it gives ISVs a single format to use for Linux packaging, and it allows all the different distros to maintain their own sense of individuality without having stray software running loose on the system.

---

### Post by Jan-Nik on 2008-01-17
> PackageKit is so attractive because it gives everyone what they want: it gives ISVs a single format to use for Linux packaging

Which one? PackageKit isn't a package format, so it doesn't gives ISVs a single format. This is the part where autopackage comes in.

---

### Post by maybeway36 on 2008-01-17
With autopackage and PackageKit, could one vendor ditribute a program that installs and runs on (say) Ubuntu, Debian, Fedora, and Mandriva?

---

### Post by Jan-Nik on 2008-01-17
> **maybeway36 said:**
> With autopackage and PackageKit, could one vendor ditribute a program that installs and runs on (say) Ubuntu, Debian, Fedora, and Mandriva?

He could do it with autopackage alone, but with PackageKit, his package can have dependencies which would be solved by the package manager of the distribution.

---

### Post by lexen on 2008-01-17
I emailed the guys at synaptic to see what they had to say.  Here is what I emailed to them:

> Hello and thank you for reading my email.

A discussion is taking place in the Ubuntu forums about how to instate a universal program medium.  You can view the discussion here.  One of the questions that arose was, is it possible to automate the process of installing a program from source?  The three questions I have for you are:


Is it possible to ever integrate a source code compiler into synaptic?
Are there any plans to do so?

What would it take?



Thanks,
Lexen 

Here is what they said back:

> What would be the reason to install from source rather than to use
pre-build packages?

> The three questions I have for you are:
> Is it possible to ever integrate a source code compiler into synaptic?

It would be possible, but its a problem from a UI standpoint. There is
e.g. the issue of displaying a progress dialog while it compiles. Then
there is the scope. Is this about ubuntu source packages or about any
source code?

> Are there any plans to do so?

Not currently.

> What would it take?

That depends very much on what you plan to do :) If its about the
equivalent of "apt-get source --build foo" then its not that hard
(also I wonder what the use-case is).

Cheers,
 Michael

He thinks it can be done, but he doesn't see the point.  What do all of you think about this?

---

### Post by 23meg on 2008-01-17
> Is this about ubuntu source packages or about any source code?

The critical difference me and others have been trying to describe.

It would be trivial to make Synaptic build from Ubuntu source packages, but there's no real use case for it. It would not be possible, **and** wouldn't make sense, to make it build any source package.

[QUOTE=Jan-Nik]You can search a package which contains a specific file (e.g. a shared library) with PackageKit. Unfortunately this doesn't work with all backends at the moment (including apt).[/QUOTE]

I haven't been able to find any info about PackageKit's Autopackage backend; not even proof that it exists. Again, can you please cite the source?

---

### Post by mangar on 2008-01-17
@lexen
possible use case for automating compilation for source:
batch compilation of packages in order to check the effect of compiler optimization, allowing synaptic to be used as front end for gentoo's packages,.

---

### Post by DrMega on 2008-01-17
> **23meg said:**
> It would not be possible, **and** wouldn't make sense, to make it build any source package.

I disagree. I'm not particularly knowledgeable about Linux yet but I am learning, and I have built a number of apps from source that were meant for any distro. In some cases it was straightforward, in others it was a real nightmare. The one thing that they all had in common was that most of the work I had to do was tedious but not complicated, and the various errors and warning I saw during failed attempts (leading up to the successful build) provided me with the info I need to fix the error/warning.

I think it would be about impossible to write an app that would work for EVERY source package, but if it work for 80% of packages, and did most of the donkey work in the other 20% I think it would be really useful.

---

### Post by 23meg on 2008-01-17
[QUOTE=DrMega]I think it would be about impossible to write an app that would work for EVERY source package, but if it work for 80% of packages, and did most of the donkey work in the other 20% I think it would be really useful.[/QUOTE]

*Some* application (optional) that can, with some luck, compile n% of source tarballs automatically can make sense (and probably exists already). Integrating this into a default application such as Synaptic doesn't.

Synaptic works with repositories, not with individual packages. The use case of compiling a source package includes obtaining it manually and working on it locally, so Synaptic isn't the suitable app. 

And the main point of having applications packaged in repositories and providing elaborate frontends to users to install/uninstall from them is the comfort of knowing that once the user installs an application, it will 

[list=1][*]work (have compiled with the default toolchain, perform as expected)
[*]not interfere with other applications and libraries installed 
[*]integrate seamlessly into and make sense in the environment (install menu shortcuts, set necessary options in related software, prefer certain libraries or backends, etc.)[/list]
This is most of what distro packaging is about, and its scope goes beyond package management and installation methods. You cannot guarantee any of the above with a hypothetical Synaptic that installs from any source package in the wild. Thus, you lose the whole point.

---

### Post by DrMega on 2008-01-17
23meg

You are right. I'd missed the point that we had moved onto Synaptic specifically. It certainly would not make sense to have Synaptic (which is an excellent tool) deal with compilation from source.

What I meant was that in addition to Synaptic, and tucked away out of sight somewhere (but easy to find), it would be great if there was a tool to help the user build from source if they wanted to do so. I am a developer on Windows, but am still learning Linux. If I ever get time, I might try to develop such a tool myself. It would be a great learning exercise if nothing else.

---

### Post by Jan-Nik on 2008-01-17
> **23meg said:**
> I haven't been able to find any info about PackageKit's Autopackage backend; not even proof that it exists. Again, can you please cite the source?

As I said: "Not yet, but this will change when PackageKit is supported."
So there isn't a PackageKit integration. I  wanted to say: "With this improvement autopackage WOULD BE the unified package format we are talking about." It was a mistake because of my bad English.

All I wanted to say: Why create a new unified package format? Better improve autopackage instead.

---

### Post by vishnumrao on 2008-01-28
Awesome Idea. My vote is yes. Standarisation will help companies release commercial versions of their products in one form for all the linux users. 

Right now if you visit the java or adobe flash  or limewire sites, they have to offer the .rpm or .deb files or the .tar.gz files, for users of different linux distros. How bout just creating one common package medium, maybe .lin (lin for linux, my suggestion)

---

### Post by coolen on 2008-01-28
PackageKit will allow compaines to release a single version for any participating distro, once it's complete.

When comparing this to autopackage, they'd both provide the same thing, except that PackageKit can do it and still keep it within the system. The package manager would be aware of the installed software, and able to remove it.

They're both decent solutions, but PackageKit seems to be what the people in charge are going with, and is the direction LSB is taking.

Why have two package managers trying to handle a single system when you can just as easily have one?

---

### Post by Jan-Nik on 2008-01-28
> **coolen said:**
> PackageKit will allow compaines to release a single version for any participating distro, once it's complete.

When comparing this to autopackage, they'd both provide the same thing, except that PackageKit can do it and still keep it within the system. The package manager would be aware of the installed software, and able to remove it.

They're both decent solutions, but PackageKit seems to be what the people in charge are going with, and is the direction LSB is taking.

Why have two package managers trying to handle a single system when you can just as easily have one?

No, PackageKit is not a package format! Also it isn't possible to install rpms on an apt system with PackageKit.

---

### Post by Jan-Nik on 2008-01-28
> **vishnumrao said:**
> Right now if you visit the java or adobe flash  or limewire sites, they have to offer the .rpm or .deb files or the .tar.gz files, for users of different linux distros.
This is already possible with autopackage.

> How bout just creating one common package medium, maybe .lin (lin for linux, my suggestion)

The autopackage developers are trying to do this.

---

### Post by KillerKiwi on 2008-02-10
Klik2 does some thing like this using the zeroinstall format

Klik2 then downloads an rpm/deb and makes it executable on any distro with the klik2 client.. meaning the packager only has to create his package for one distro

The klik file never messes with your base install as it only creates one file on your system.. deleting that file 'uninstalls' the application

see [http://code.google.com/p/klikclient/](http://code.google.com/p/klikclient/)

---

### Post by coolen on 2008-02-10
> **Jan-Nik said:**
> No, PackageKit is not a package format! Also it isn't possible to install rpms on an apt system with PackageKit.

I never said it was a package format. It's a package manager interface. It will allow ISVs to create an installer that deposits their program on a system and lets the package manager know about it. That way, you can use tools like Synaptic to remove it if need be.

It won't let you use RPMs on a Debian-based system, true. However, that's not what we're trying to do (and, unless I'm very much mistaken, neither will AutoPackage). We want to present ISVs with a nice, standard way to package their programs for a Linux system. If that just so happens to play nicely with the existing system, without introducing a superfluous second package manager, then great!

---

### Post by Jan-Nik on 2008-02-11
> **coolen said:**
> I never said it was a package format. It's a package manager interface. It will allow ISVs to create an installer that deposits their program on a system and lets the package manager know about it. That way, you can use tools like Synaptic to remove it if need be.
I don't think installers, like Windows' ones are the right way. And if they create an installer, user needs to make it executable. Also downloading the installer code everytime costs traffic.

> It won't let you use RPMs on a Debian-based system, true. However, that's not what we're trying to do (and, unless I'm very much mistaken, neither will AutoPackage). We want to present ISVs with a nice, standard way to package their programs for a Linux system. If that just so happens to play nicely with the existing system, without introducing a superfluous second package manager, then great!
Really, I don't think every ISV should create it's own installer (the situation on windows actually before .msi)! The work should be done within the autopackage project and then included into the distros.

---

### Post by coolen on 2008-02-11
As it stands, writing one's own installer is the most attractive option. Saves you having to repackage for all those different formats. This way, they can do that, and still play nice with the package manager.

Also, I fail to see how downloading installer code is worse than installing a package when it comes to traffic.

---

### Post by Jan-Nik on 2008-02-11
It's a nice discussion!

I think there are many mistakes in my posts, because it's difficult for me to describe all this in English. Sorry for that.

> **coolen said:**
> As it stands, writing one's own installer is the most attractive option. Saves you having to repackage for all those different formats. This way, they can do that, and still play nice with the package manager.
Maybe it's the most attractive option, but i think it will lead to bugs: For example if there's a bug in one installer, the ISV has to fix this (or wait for the creator of the installer to fix the bug and then recreate the installer). It's better if there's one code base which reads a package format.
I think the best way would be to create this package format which has a support code that uses PackageKit. And the easiest way to this is to improve autopackage so that it makes use of PackageKit.

By the way: Does PackageKit really support such an integration with the package manager? AFAIK it's only a wrapper and doesn't have any bonus features.

"How does PackageKit handle dependencies?

PackageKit does not do dependency resolution. This problem has already been solved by the backend systems and we don't really want to re-invent the wheel.

PackageKit does not have the fine-grained API to do everything. For instance, synaptic should still use libapt as can do much more than can be provided by PackageKit. " ( [http://www.packagekit.org/pk-faq.html](http://www.packagekit.org/pk-faq.html) )

As I understand it, Synaptic will never recognize any installed package except debs.

> Also, I fail to see how downloading installer code is worse than installing a package when it comes to traffic.
If you download an installer for an program, the GUI of the installer will be downloaded with every single program. If you download a package, the code to guide you through the installation process will be already on your disc (or downloaded only one time, the current solution of autopackage).

---

### Post by smartboyathome on 2008-02-11
If there isn't a wrapper for autopackage which detects dependancies from other distros using rpm/deb/whatever, then I don't see any advantage to it, even with the packagekit integration of it. It will still sometimes install extra code even though the code is already there, and still has a good potential to break packages if you are installing an autopackage on an older system.

---

### Post by Jan-Nik on 2008-02-11
> **smartboyathome said:**
> If there isn't a wrapper for autopackage which detects dependancies from other distros using rpm/deb/whatever, then I don't see any advantage to it, even with the packagekit integration of it. It will still sometimes install extra code even though the code is already there, and still has a good potential to break packages if you are installing an autopackage on an older system.
Well, but these are problems a self-created installer has too. IMHO if someone wants to create an installer which uses PackageKit, he should add this feature to autopackage instead.

I think it's a good idea to start implemnting such a wrapper. Does someone has an idea how to implement this? The name of a package can be different on each distribution, what would be the easiest way to solve this?

---

### Post by smartboyathome on 2008-02-11
Have it compile it for your distro. That is the only way I can see it working.

---

### Post by coolen on 2008-03-09
Sorry about my latew reply. I didn't get any emails about this.

Synaptic, as I understand it, will recognise programs installed using PackageKit (as will tools for other supported package managers). As I understand it, PackageKit allows you to install your programs using scripts/executables, and let PackageKit know what you're doing. PackageKit will, in turn, let the native package manager know.

The end result is that you get a package that will work on every supported distro (and eventually, this should be all Linux distros), and which can later be handled natively. You can remove the program normally.

AutoPackage, to me, seems to be another package manager. That's great, but it's not a solution. If you want to address deficiencies in APT, do it in APT. AutoPackage would still need to make its way into every distro, and it probably won't, since it will be viewed as a competing packaging system.

---

### Post by raul_ on 2008-03-09
IMHO, that's the same as creating an unified distro. Different distros install packages in different places, have different architectures, different dependencies, etc etc.

Plus, the unified format is SOURCE CODE :p

---

### Post by Jan-Nik on 2008-03-09
> **coolen said:**
> Synaptic, as I understand it, will recognise programs installed using PackageKit (as will tools for other supported package managers).
PackageKit uses apt to install packages, so synaptic will of course recognize them.

> As I understand it, PackageKit allows you to install your programs using scripts/executables, and let PackageKit know what you're doing. PackageKit will, in turn, let the native package manager know.
I don't think so. According to [http://www.packagekit.org/pk-intro.html](http://www.packagekit.org/pk-intro.html) PackageKit is just a abstraction layer over the package manager, it can't install anything by itself.

> The end result is that you get a package that will work on every supported distro (and eventually, this should be all Linux distros), and which can later be handled natively. You can remove the program normally.
I don't think that's possible with PackageKit.

> AutoPackage, to me, seems to be another package manager.
Yes, but it's distribution neutral and should only be used for third party applications and not for something like GNOME, or the kernel itself.

> AutoPackage would still need to make its way into every distro, and it probably won't, since it will be viewed as a competing packaging system.
Hm.. it would be nice, but you can install autopackages on distros that doesn't ship it, because the .package file downloads the support code if it's missing.
Autopackage ist not a normal package manager: [http://autopackage.org/faq.html#1_2](http://autopackage.org/faq.html#1_2)


edit: I don't think it's possible with PackageKit to let apt know that you installed something.

---

### Post by dirk_s on 2008-03-12
> **maybeway36 said:**
> Adding a new package format will only add another package format. The way to go is making .deb packages work on Red Hat/Mandriva/etc. and rpm packages work on Debian/Ubuntu. In other words, an alien GUI.
SIGNED!! :guitar:
That's exactly what I think and wish for. The FAQ of the Smart packagage manager says something in the sense that smart can replace the native package manager but is unable to integrate non-native packages into the native package management - despite the "better resolver" this i's IMHO not much more than a different front-end to the native package management. The alien system tries to convert packages from one system to another - but how good is it at that? I mean, now, today. Already good enough to reliably integrate a package of .rpm origin on an Ubuntu system?



Btw: Is there ANY package system that allows me to install two different versions of the same software in different locations, say, a full Java version 1.5 under /usr/... and Java Version 1.6 under /opt/... or /usr/local/...? Sometimes I need that. 

A few hours ago I learned that the DEB format is not capable to allow that, while RPM theorerically could, but I never heard that any distribution supports that... wait... I have heard of something similar, where every package is installed in its own "private" path, but I forgot what distro/package management that was. Only thing I remember is that they had/have their very own&unique package management.

Well, right now the only solution to the 2-version problem seems to be: Install from source, compile by yourself. That is: .tgz and maybe emerge/ebuild, I don't know enough about Gentoo.

I'm not so much into standards here - none of the well-known and widely used Distros have any reason to ditch their package format in favor of a new one, be it a meta format or a real one. What is really needed is a good conversion system. Where, of course, building from source offers the most possibilities, by far.

---

### Post by coolen on 2008-03-12
The distro you're thinking of is GoboLinux. It uses a custom filesystem that's more intuitive, installing each program to its own directory, thus allowing for multiple versions of a single program. The filesystem is, essentially, the package manager (drop a program in, it's installed, delete it, it's removed).

GoboLinux is not a beginner's distro. Despite its more user-friendly filesystem, it requires a fair amount of Linux experience to work with it. It's more a proof of concept itself, in the hopes that others might develop a user friendly distro around it.

However, you won't see Ubuntu, or any other major distro, adopting the Gobo style packaging scheme. For good reason, I believe.

---

### Post by coolen on 2008-03-12
> **Jan-Nik said:**
> I don't think so. According to [http://www.packagekit.org/pk-intro.html](http://www.packagekit.org/pk-intro.html) PackageKit is just a abstraction layer over the package manager, it can't install anything by itself.

I didn't say that. The installer installs the files, and let's PackageKit know what it's doing. PackageKit, in turn, lets the package manager know, so it can update its own database. That's the whole point of PackageKit: to let the ISVs do their thing while the system keeps doing its thing.

My main problem with Autopackage is that it's just giving us something we already have, and hoping for widespread adoption. Why don't we convince Fedora and openSUSE to use APT? That'd solve our problems, too!

PackageKit will allow the distros what they want (one package manager, being the one they've invested in) while giving the ISVs what they need (a single method of neatly installing and distributing programs for Linux).

---

### Post by vikasmk on 2008-03-12
i think it's a great idea . as to its feasibility , I have no idea:lolflag:

---

### Post by 23meg on 2008-03-12
[QUOTE=dirk_s]
Btw: Is there ANY package system that allows me to install two different versions of the same software in different locations, say, a full Java version 1.5 under /usr/... and Java Version 1.6 under /opt/... or /usr/local/...? Sometimes I need that.[/QUOTE]

Just about every packaging system lets you do this. In Debian based distros you use update-alternatives to choose which version will provide the functionality.

---

### Post by smartboyathome on 2008-03-12
> **coolen said:**
> The distro you're thinking of is GoboLinux. It uses a custom filesystem that's more intuitive, installing each program to its own directory, thus allowing for multiple versions of a single program. The filesystem is, essentially, the package manager (drop a program in, it's installed, delete it, it's removed).

GoboLinux is not a beginner's distro. Despite its more user-friendly filesystem, it requires a fair amount of Linux experience to work with it. It's more a proof of concept itself, in the hopes that others might develop a user friendly distro around it.

However, you won't see Ubuntu, or any other major distro, adopting the Gobo style packaging scheme. For good reason, I believe.

That may be a good reason for you, but maybe not for others, though that is a discussion for another thread.

Also, OpenSUSE and Fedora have put a lot of work into RPM, I doubt they would turn back now and give to APT. Same with Debian.

---

### Post by Shin_Gouki2501 on 2008-03-12
to put "a lot" of work into some diffrent things doesnt mean you can not find a common standard to use in future.
Open Source Community should make benefit of its "openess".

---

### Post by raul_ on 2008-03-12
> **Shin_Gouki2501 said:**
> to put "a lot" of work into some diffrent things doesnt mean you can not find a **common standard** to use in future.
Open Source Community should make benefit of its "openess".

i'll say it again:** source code?**

---

### Post by dirk_s on 2008-03-13
> **coolen said:**
> The distro you're thinking of is GoboLinux. It uses a custom filesystem that's more intuitive, installing each program to its own directory, thus allowing for multiple versions of a single program. The filesystem is, essentially, the package manager (drop a program in, it's installed, delete it, it's removed).
You're right, that's it. I've heard of it some time ago but never tried because I thought it is prone for creating a chaos. Maybe I should give the Live-CD a try once in a while.

> **coolen said:**
> GoboLinux is not a beginner's distro. Despite its more user-friendly filesystem, it requires a fair amount of Linux experience to work with it. It's more a proof of concept itself, in the hopes that others might develop a user friendly distro around it.
That's not a problem, I'm not a linux newbie. 
During mad minutes I even thought of creating my own distro, with a new package manager that can read&install RPM, DEB and source packages :p When reason kicks in I realize that I wouldn't find enough time to lift such a project. And the package manager without an interesting distro around it would be nothing.

There is a sort of "business rule" to it: To achieve total world domination of your package management, you must "force" a major amount of people to use it. To create that "force", it must be remarkably better than your competitors. That's not easy... The easiest way to get there would be to be able to do ALL your competitors can do with *their* package management (so hat the replacement is a drop-in-and-finished) plus having some advantages that the users really want. :D

> **coolen said:**
> However, you won't see Ubuntu, or any other major distro, adopting the Gobo style packaging scheme. For good reason, I believe.
Exactly - same goes for all other major distros. The only way for another/different package management to "take them over" would be if the new system could fully replace the original package management WHITHOUT any need to change a bit of the native packages, PLUS would add the ability to use other distro's packages, too, like native ones, that is, auto-converting them on the fly and taking care of all dependency stuff. Then the migration from the native package management would be done in less then a second. And - let them use their RPM/DEB/TGZ or whatever they please - I can read all of them, if they cannot read mine, that's not my problem.

About installing different versions of the same software onto one system:
> **23meg said:**
> Just about every packaging system lets you do this. In Debian based distros you use update-alternatives to choose which version will provide the functionality.
Really? I wasn't aware of that. Yesterday I saw a note somewhere that the Debian system is incapable of that, of course now I cannot find it again. Also, the SUSE system does not. And they use RPM... (If you let it have its way, Yast even replaces kernel source packages, completely removing the old version, leaving no trace.)

The GoboLinux would solve that problem but I'm not not fully convinced - what about disk space? I should give it a try to learn more.


Addenum, I forgot:
There's a [featured story on distrowatch]("http://distrowatch.com/weekly.php?issue=20080310#feature") about Sabayon (Gentoo-based) developing a new package manager :D Well of course, since they (and Gentoo) are installing from source, their chances are best :)

---

### Post by 23meg on 2008-03-13
[QUOTE=dirk_s]Really? I wasn't aware of that.[/QUOTE]

Type ```
sudo update-alternatives --list java
``` to see the available Java versions you have installed, and```
sudo update-alternatives --set java /path/of/whichever/version/you/want 
``` to choose the one to use. It's all done with symlinks, and it's been available for ages.

Specifically for Java, you can also use *update-java-alternatives*.

---

### Post by coolen on 2008-03-13
> **smartboyathome said:**
> That may be a good reason for you, but maybe not for others, though that is a discussion for another thread.

Also, OpenSUSE and Fedora have put a lot of work into RPM, I doubt they would turn back now and give to APT. Same with Debian.

Yes, it is, but it's been done to death. No amount of user discussion will setlle thatr one, obviously. If you want to see it happen, discuss it with a developer. Tell them all about your single use case, the massive amounts of effort it would require and the horrible compatibility that would ensue. I'm sure they'll love it.

---

### Post by Joeb454 on 2008-03-13
It also partly takes away the freedom of choice that Linux users have.

I like APT, but I don't particularly like Yum/RPM etc.

---

### Post by smartboyathome on 2008-03-13
> **coolen said:**
> Yes, it is, but it's been done to death. No amount of user discussion will setlle thatr one, obviously. If you want to see it happen, discuss it with a developer. Tell them all about your single use case, the massive amounts of effort it would require and the horrible compatibility that would ensue. I'm sure they'll love it.

Like I keep saying, there will be NO COMPATIBILITY ISSUES! It uses hidden symlinks to make it compatible with all linux programs. If I were you, I would read up a little more on it.

And in the long run it will also help, I will post this in the other thread designated for this topic.

---

### Post by bone2006 on 2008-04-15
Sounds good........
How do we start to contribute money and who is going to start development?  If we all want it.....................has to start somewhere

---

### Post by Jan-Nik on 2008-04-15
> **bone2006 said:**
> Sounds good........
How do we start to contribute money and who is going to start development?  If we all want it.....................has to start somewhere

Several projects are already there:

[http://www.packagekit.org/](http://www.packagekit.org/)
[http://autopackage.org/](http://autopackage.org/)
[http://klik.atekon.de/](http://klik.atekon.de/)
[http://0install.net/](http://0install.net/)

Development has already started :)

---

### Post by tbrminsanity on 2008-04-18
> **Joeb454 said:**
> It also partly takes away the freedom of choice that Linux users have.

I like APT, but I don't particularly like Yum/RPM etc.

Having one package manager will not take away freedom of choice from Linux users.  It will open up programs that were not available before because it was too much a pain in the @$$ to install since they didn't have it in your package.

---

### Post by coolen on 2008-04-18
> **Joeb454 said:**
> It also partly takes away the freedom of choice that Linux users have.

I like APT, but I don't particularly like Yum/RPM etc.

The direction the LSB is taking is PackageKit (or something that sounds a great deal like it). This provides package installers with the common functionality, without requiring them to commit to any one package format, nor you to try to adapt the package/switch systems to install it.

So, for the end user, it enables greater choice. It no longer matters if a software package is provided in my format, so I can choose whichever system best suits me.

---

### Post by Jan-Nik on 2008-04-18
> **coolen said:**
> The direction the LSB is taking is PackageKit (or something that sounds a great deal like it). This provides package installers with the common functionality
Which functionality?

---

### Post by smartboyathome on 2008-04-18
> **coolen said:**
> The direction the LSB is taking is PackageKit (or something that sounds a great deal like it). This provides package installers with the common functionality, without requiring them to commit to any one package format, nor you to try to adapt the package/switch systems to install it.

So, for the end user, it enables greater choice. It no longer matters if a software package is provided in my format, so I can choose whichever system best suits me.

That is not what PackageKit is doing. It is just creating a unified frontend for all the major package formats out there. It does not try to allow the installation of different packages from different package formats.

---

### Post by tbrminsanity on 2008-04-18
Just for my own information, what are the major challenges of having only one package system for all distros?  Is it the different filesystem layouts (/usr/bin vs /usr/lib/bin) or is there something more?

If the only hurdle is where a program should be installed then the only remaining difficulty would be universal adoption (it is funny how attitudes seem to bugger everything up in the end).

---

### Post by Jan-Nik on 2008-04-18
> **tbrminsanity said:**
> Just for my own information, what are the major challenges of having only one package system for all distros?  Is it the different filesystem layouts (/usr/bin vs /usr/lib/bin) or is there something more?

More: Binary compatibility, dependencies, etc.
One package system for all distros, that's never going to happen (and it's also not necessary).

---

### Post by tbrminsanity on 2008-04-18
> **Jan-Nik said:**
> More: Binary compatibility, dependencies, etc.
One package system for all distros, that's never going to happen (and it's also not necessary).

Shouldn't all Linux programs be binary compatible.  That just seems wrong if they aren't.  As for dependencies, I see what you mean.  It will get very messy trying to convert all the current packages over to a new system if the dependencies have different names (like RHEL and Ubuntu).

I think it is improbable but not impossible though.

---

### Post by smartboyathome on 2008-04-18
> **tbrminsanity said:**
> Shouldn't all Linux programs be binary compatible.  That just seems wrong if they aren't.  As for dependencies, I see what you mean.  It will get very messy trying to convert all the current packages over to a new system if the dependencies have different names (like RHEL and Ubuntu).

I think it is improbable but not impossible though.

No, because source by its nature looks for certain files to determine if a program is installed. The package management would have to be built into the terminal, which would be less than practical.

---

### Post by tbrminsanity on 2008-04-19
> **smartboyathome said:**
> No, because source by its nature looks for certain files to determine if a program is installed. The package management would have to be built into the terminal, which would be less than practical.

I thought most of the package managers are built into the terminal and just have a GUI frontend.  APT for example has many GUI frontends, but just one terminal backend.

---

### Post by smartboyathome on 2008-04-19
> **tbrminsanity said:**
> I thought most of the package managers are built into the terminal and just have a GUI frontend.  APT for example has many GUI frontends, but just one terminal backend.

I meant a whole new format would have to be built to handle them all, sorry for not being so clear.

---

### Post by coolen on 2008-04-19
> **smartboyathome said:**
> That is not what PackageKit is doing. It is just creating a unified frontend for all the major package formats out there. It does not try to allow the installation of different packages from different package formats.

That's not what I said. This is why I said that ISVs don't have to commit to one system. It's won't allow Ubuntu users to install RPMs, but it will allow users of both systems to install a program from the same package.

---

### Post by coolen on 2008-04-19
> **Jan-Nik said:**
> Which functionality?

[http://www.packagekit.org/pk-faq.html](http://www.packagekit.org/pk-faq.html)

---

### Post by smartboyathome on 2008-04-19
> **coolen said:**
> That's not what I said. This is why I said that ISVs don't have to commit to one system. It's won't allow Ubuntu users to install RPMs, but it will allow users of both systems to install a program from the same package.

It doesn't, some packages are compatible between ie Debian and Ubuntu, but some aren't, and the packages which can be installed on both systems will remain the same, as it is only a frontend. It won't allow users of ie Fedora and Ubuntu to install the same package from the deb or RPM of the package.

I hope I am understanding you.

---

### Post by coolen on 2008-04-19
> **smartboyathome said:**
> It doesn't, some packages are compatible between ie Debian and Ubuntu, but some aren't, and the packages which can be installed on both systems will remain the same, as it is only a frontend. It won't allow users of ie Fedora and Ubuntu to install the same package from the deb or RPM of the package.

I hope I am understanding you.

You're not understanding me. That may be my fault.

At the moment, for the most part, each distro uses their own package management solutions. We in the Debian world have APT, the Red Hat children have RPM, newer distros use Cornary, and older ones use source-based packages.

For the most part, these are incompatible with one another. You can use tools like Alien for some compatibility, but it's not a reliable solution.

The LSB is going to use, I believe, PackageKit, to solve this problem. At the moment, ISVs must either make their own installers, or package their programs for as many of these systems as they can. When PackageKit becomes usable and is implemented across the board (as an LSB standard, it would be), ISVs can use their own installer scripts, and use PackageKit to register their application with the local package manager.

Thus, if Nero released their programs for Linux in this format, I could download the package and install it on Ubuntu, then take that same package with me to my brother's machine running Fedora, and install it there, while the same package would serve my sister who uses Gentoo.

---

### Post by PurposeOfReason on 2008-04-19
*.tar.gz

Gettin' back to my roots.

[SIZE="-1"]*.pkg.tar.gz is really where it's at.[/SIZE] ;)

---

### Post by smartboyathome on 2008-04-19
> **coolen said:**
> You're not understanding me. That may be my fault.

At the moment, for the most part, each distro uses their own package management solutions. We in the Debian world have APT, the Red Hat children have RPM, newer distros use Cornary, and older ones use source-based packages.

For the most part, these are incompatible with one another. You can use tools like Alien for some compatibility, but it's not a reliable solution.

The LSB is going to use, I believe, PackageKit, to solve this problem. At the moment, ISVs must either make their own installers, or package their programs for as many of these systems as they can. When PackageKit becomes usable and is implemented across the board (as an LSB standard, it would be), ISVs can use their own installer scripts, and use PackageKit to register their application with the local package manager.

Thus, if Nero released their programs for Linux in this format, I could download the package and install it on Ubuntu, then take that same package with me to my brother's machine running Fedora, and install it there, while the same package would serve my sister who uses Gentoo.

Ok, so how would Packagekit handle the different dependancies? That is where I see it screwing up, because different distros give their packages different names to their programs.

---

### Post by coolen on 2008-04-19
As I understand it, the LSB will define a standard. Installers need only verify that a system is LSB compliant (and which version it complies to), then, as long as it's been designed for that version of an LSB compliant system, it will work.

I think there'll be some more general dependancy management, too. You won't specify individual packages, but you'll specify modules which must be installed, for example, QT.

There may also be an effort to standardise pakcgae naming across distros.

---

### Post by kklimonda on 2008-04-20
You are talking about two things - there is PackageKit and there (or will be in the future) is LSB4. The later indeed is trying to solve the problem of 3rd party packages but it's not what PackageKit does. at least not exactly.
Yes, PK hides underlying package format from developer and delivers an API for him to install required packages. So a developer can install a package which provides libfoo.so.1 without knowing anything about underlying system.
But PK won't do anything that it's backends (apt, yum, smart etc.) can't. So it won't install custom-made package from vendor's page unless it's already added to a repository PK knows about.
I could imagine some application (autopackage2, Klik3, whatever) which takes custom package, installs it's dependencies via PK and then unpacks application itself into $HOME or / but in my opinion it's a really, really bad idea and it isn't the way we should go.

---

### Post by tbrminsanity on 2008-04-21
Is there an unix standard where programs should be installed to?  If so would it be possible to just create a new package manager that had legacy checks for dependencies, and installed to the unix standard?

I find the biggest problem I have right now when I work between RHEL and Ubuntu is knowing where to find stuff on the HD.  The other option is a tool to run first that reconfigures the system to an unix standard before installing new packages.  This would mean the first time you load the new package software it would take a very long time on beefy systems and you wouldn't be able to go back to the original package system.

---

### Post by smartboyathome on 2008-04-21
> **tbrminsanity said:**
> Is there an unix standard where programs should be installed to?  If so would it be possible to just create a new package manager that had legacy checks for dependencies, and installed to the unix standard?

I find the biggest problem I have right now when I work between RHEL and Ubuntu is knowing where to find stuff on the HD.  The other option is a tool to run first that reconfigures the system to an unix standard before installing new packages.  This would mean the first time you load the new package software it would take a very long time on beefy systems and you wouldn't be able to go back to the original package system.

I think compiling from source IS the unix standard. Also, this sounds like it would require the same amount of hassle as going to Gobolinux's file system, with not much more gain. :(

---

### Post by coolen on 2008-04-21
> **kklimonda said:**
> You are talking about two things - there is PackageKit and there (or will be in the future) is LSB4. The later indeed is trying to solve the problem of 3rd party packages but it's not what PackageKit does. at least not exactly.
Yes, PK hides underlying package format from developer and delivers an API for him to install required packages. So a developer can install a package which provides libfoo.so.1 without knowing anything about underlying system.
But PK won't do anything that it's backends (apt, yum, smart etc.) can't. So it won't install custom-made package from vendor's page unless it's already added to a repository PK knows about.
I could imagine some application (autopackage2, Klik3, whatever) which takes custom package, installs it's dependencies via PK and then unpacks application itself into $HOME or / but in my opinion it's a really, really bad idea and it isn't the way we should go.

Uhh, yeah, I am. My bad. I can't remember where I got the impression that PackageKit was the LSB4 packaging system, but it became fairly rooted, and now I've gone and said a lot of very incorrect things :lolflag:

Just pretend I was talking about the LSB spec all along and I stand by everything I meant to say. Although PackageKit should still be fairly awesome (new codecs could be handled upstream in Totem, for example).

To the post above regarding package naming difficulties, PackageKit can be asked to install the package that provides any given file, so this wouldn't be an issue for cross-distro compatibility.

Again, my apologies for my confusion. I swear I was linked to the PK website from an artcile about the LSB spec, but I can't find it again.

---

### Post by tbrminsanity on 2008-04-21
> **smartboyathome said:**
> I think compiling from source IS the unix standard. Also, this sounds like it would require the same amount of hassle as going to Gobolinux's file system, with not much more gain. :(

Your probably right.  Maybe it would just be easier to make the tools that convert other packages to deb format.  Like alien.

---

### Post by smartboyathome on 2008-04-21
> **tbrminsanity said:**
> Your probably right.  Maybe it would just be easier to make the tools that convert other packages to deb format.  Like alien.

Those also have risks. There is no guarentee that the deb package will find all the libraries in the right place or that it will be able to make a clean deb package. It may not even be able to install because there is a dependancy missing/not named correctly for the package to work. Too many risks of breakage with alien, imo.

---

### Post by tbrminsanity on 2008-04-21
> **smartboyathome said:**
> Those also have risks. There is no guarentee that the deb package will find all the libraries in the right place or that it will be able to make a clean deb package. It may not even be able to install because there is a dependancy missing/not named correctly for the package to work. Too many risks of breakage with alien, imo.

With time it should improve.  I think any app that leads towards interoperability between different distros is a good app.  I think the time to sit down and choose one package system for all Linux distros was about 10 years ago and we are suffering for it now.

---

### Post by dryder on 2008-04-21
Aren't most non-Ubuntu packages/programs available in source code as well as some limited different distro flavours?
 
If that is the case, as I believe it often is, why not simply compile from source? I guess, as linux becomes more 'user friendly', via a gui so things like where to put libraries, what symlinks need creating, etc can be input by the user?

Then, the version of linux could perform its 'special requirements' as required.

Things would be more 'universal' and companies more inclined to write for linux.

How else are we going to get packages to work on all versions? Such as a printer driver or a backup power supply etc.

When I worked on UNIX mainframes, all were different. But all compiled from source - and there was only one source program.
David

---

### Post by coolen on 2008-04-22
First, and most obvious, that would require companies to release source code for their products. While we want to encourage this, it would be a mistake to demand it in any way.

Also, compiling from source can take longer, and introduces build depednacies.

It would certainly be possible to create a GUI for compiling source code. You could fetch build dependancies as required, too, and possibly remove them after the fact. This would be great, especially if you could put it in a .deb and have dpkg handle it, but it's not a universal solution.

---

### Post by elpichi on 2008-04-22
I think this is a great idea, branching towards universal compatibility with other distros would atract many users with fear of change in distro, i find debian package management very efficient compared to others, but they all have their pros and cons, specially emerge with its ebuilds.

---

### Post by tbrminsanity on 2008-04-22
> **elpichi said:**
> I think this is a great idea, branching towards universal compatibility with other distros would atract many users with fear of change in distro, i find debian package management very efficient compared to others, but they all have their pros and cons, specially emerge with its ebuilds.

I have to agree with you.  Deb packages are by far the best linux packages I've worked with.  They just work for me.  I use RPM packages on my work computer (RHEL) and it is always hit or miss if something will install.  Most cases I just install from source as I know that will work.

---

### Post by dryder on 2008-04-22
> First, and most obvious, that would require companies to release source code for their products. While we want to encourage this, it would be a mistake to demand it in any way.
For drivers etc this is not really an issue, I think, and would increase, say, printer useage and the commercial value of drivers is very small - indeed, some programmers write their own.

For programs, well, to an extent alien already converts by using parameters in the file provide in the rpm package. A 'universal' package then may not be the source code if that is too much giving away secrets but a (distro) non-specific compilation that a gui/distro could then have the required variants put in manually (gui) or automatically (new-alien) to create the deb or whatever.

> Also, compiling from source can take longer, and introduces build depednacies.
Not really of any significance - does it matter if converting it to your distro (rpm, deb, etc) takes a litle longer? Once converted it is simply installed like any other package. Getting the build dependancies is what this method does.
Running from source code of course would be a hell of a lot faster but not universal.

If the community really wants linux to seriously compete but maintan distro uniqueness, this really is the only way to go. Getting programs in deb, rpm etc is too much work for the manufacturers. Source or compiled code that each distro can create its own package from is easier - once they are convinced linux is not a bunch of geek type systems but to be taken as another useful market. Then it would be Windows, Mac, Linux - not Windows, Mac, linux this, linux that etc.

David

---

### Post by tbrminsanity on 2008-04-23
> **dryder said:**
> For drivers etc this is not really an issue, I think, and would increase, say, printer useage and the commercial value of drivers is very small - indeed, some programmers write their own.

For programs, well, to an extent alien already converts by using parameters in the file provide in the rpm package. A 'universal' package then may not be the source code if that is too much giving away secrets but a (distro) non-specific compilation that a gui/distro could then have the required variants put in manually (gui) or automatically (new-alien) to create the deb or whatever.


Not really of any significance - does it matter if converting it to your distro (rpm, deb, etc) takes a litle longer? Once converted it is simply installed like any other package. Getting the build dependancies is what this method does.
Running from source code of course would be a hell of a lot faster but not universal.

If the community really wants linux to seriously compete but maintan distro uniqueness, this really is the only way to go. Getting programs in deb, rpm etc is too much work for the manufacturers. Source or compiled code that each distro can create its own package from is easier - once they are convinced linux is not a bunch of geek type systems but to be taken as another useful market. Then it would be Windows, Mac, Linux - not Windows, Mac, linux this, linux that etc.

David

I agree.  Linux needs a unified front.  It is awesome to have different distros that offer packages tailored for specific needs, but the basics need to be standardized.  

If a difference can exist without causing incomparability then great have those differences (example running KDE vs Gnome vs XFCE), but when I have to hunt down my distro's version of a program online, that is when I get pissed off.

---

### Post by qamelian on 2008-04-23
> **tbrminsanity said:**
> I agree.  Linux needs a unified front.  It is awesome to have different distros that offer packages tailored for specific needs, but the basics need to be standardized.  

If a difference can exist without causing incomparability then great have those differences (example running KDE vs Gnome vs XFCE), but when I have to hunt down my distro's version of a program online, that is when I get pissed off.
For the most part, the basics are standardized. Most of the time, variances exist for valid technical or logistical reasons. The real problem is that new users refuse to learn the standards and expect Linux to adapt to them rather than being willing to learn the necessary skills and fundamentals of the OS.

---

### Post by smartboyathome on 2008-04-23
This is not about adapting, it is about making a standard package management format. I still think that Gobohide/Gobolinux would take care of this if it were adopted into the kernel (the easiest way). Other ways are just more complicated imo.

---

### Post by qamelian on 2008-04-23
> **smartboyathome said:**
> This is not about adapting, it is about making a standard package management format. I still think that Gobohide/Gobolinux would take care of this if it were adopted into the kernel (the easiest way). Other ways are just more complicated imo.
It is about adapting. The "standard" on *nix-type systems is to compile from source. Package management systems are never going to be standardized around one type because that is counter-intuitive to the open-source ecosystem in which there is always someone who thinks they can do it better. Sometimes they are right; sometimes not. 

I don't believe Gobohide/Gobolinux are the solution either. Obfuscation is never a good substitute for actually learning the fundamentals. I was a newbie once myself, and I know it is not that difficult, if you are willing to accept responsibility for learning a new skill-set rather than expecting the set to be molded over to match your expectations. In many fields that is referred to as "lowering the bar" and always produces negative results despite the best intentions.

---

### Post by smartboyathome on 2008-04-23
No, Gobohide puts all the program files in one directory. This allows for the package manager to see every program's files, thus allowing for unification of package managers and compiling from source.

---

### Post by qamelian on 2008-04-23
> **smartboyathome said:**
> No, Gobohide puts all the program files in one directory. This allows for the package manager to see every program's files, thus allowing for unification of package managers and compiling from source.
I know what it does; I've used it. It was the single worst Linux experience I've had in 11 years of being a Linux user. Putting all the programs in one folder is not a good idea and is completely in opposition with the existing standards. There is already an appropriate place for any software, regardless of whether it is part of the base distribution, something you build/install locally on your workstation and applications provided by third parties. The standard is extremely well documented and not at all difficult to learn. If people would expend half as much energy to actually learn the standards that already exist as they spend trying to change that standard into something completely unnecessary, they would be much better off.

---

### Post by dryder on 2008-04-23
qamelian,
> For the most part, the basics are standardized. Most of the time, variances exist for valid technical or logistical reasons. The real problem is that new users refuse to learn the standards and expect Linux to adapt to them rather than being willing to learn the necessary skills and fundamentals of the OS
Not really. How far back in the package process do you want to go? This argument would do away with packages altogether and leave it up to you to compile from source: no alien, no /.configure no easy install of a deb (or whatever) package.

I am only addressing a package management system that would be the same  package for all distros. The management for a particular distro would then do the rest either (semi-)manually via a gui or by 'new-alien'. One program = one package = let the distro do the work according to its (variant and technical, etc.), needs.

I find it rather offensive when you say 'new users refuse to learn ...' and some of the comments in your post before this one I'm writing. If you want a command line only linux, then go back to it. But I bet you use the windows front-end Ubuntu provides. And Writer. And Calc and so on and so forth. My days of writing programs either in binary, assembler, fortran, are long over - I want the control, yes, but not for the sake of it. And a lot of new people try very hard for the better than Windows system and stick with it. Some learn more slowly than others. Condescending, belittling attitudes do not go down well.

David

---

### Post by qamelian on 2008-04-23
> **dryder said:**
> qamelian,

Not really. How far back in the package process do you want to go? This argument would do away with packages altogether and leave it up to you to compile from source: no alien, no /.configure no easy install of a deb (or whatever) package.

I am only addressing a package management system that would be the same  package for all distros. The management for a particular distro would then do the rest either (semi-)manually via a gui or by 'new-alien'. One program = one package = let the distro do the work according to its (variant and technical, etc.), needs.

I find it rather offensive when you say 'new users refuse to learn ...' and some of the comments in your post before this one I'm writing. If you want a command line only linux, then go back to it. But I bet you use the windows front-end Ubuntu provides. And Writer. And Calc and so on and so forth. My days of writing programs either in binary, assembler, fortran, are long over - I want the control, yes, but not for the sake of it. And a lot of new people try very hard for the better than Windows system and stick with it. Some learn more slowly than others. Condescending, belittling attitudes do not go down well.

David
Be offended if you like. No where did I indicate that we needed to or should go back to a command line only Linux, so please do not put words in my mouth as that offends me in kind. If you don't believe that a very large contingent of new Linux users refuse to learn, I suggest you spend a little more time browsing the forums and you will very quickly find post after post after post in which people want to change the existing standards rather than learn them. As a long-time Linux user who has taken the time to learn my way around Linux, I find it extremely offensive when other users would rather have things fixed that just are not broken. I have always been willing to help, or at least make the attempt, anyone I can on this and other forums. 

My attitude is hardly condescending and if you interpret it that way, again I take offense. I do not expect a new user to know everything by rote, but I do expect users to take some responsibility for their own computing experience and that include being willing to learn when they choose to change computing environments. When a user expects the world to change on their whim rather than taking the time and effort to learn why some things are as they are, and why those things work, I simply find this inexplicable. I first moved to Windows after 13 years as an Atari ST user. Did I expect Windows to work like the environment that I knew intimately? No, I did not. Did I expect that I would be required to learn a substantially different skill-set? You betcha. To expect otherwise is simply being unreasonable.

There are plenty of things in Linux that can and should be changed, but there are plenty of things that should be left as they are and learned as they are. The benefits are worth it. Of course, if a user never takes the time to learn, they never understand the benefits either.

---

### Post by dryder on 2008-04-23
qamelian,

It is not about changing things that aren't broken or about learning - it is about making more drivers, software etc.available to all distros requiring only one item to then be handled by all flavours.

Some things are written for specific distros and will not convert. Example: Eaton Powerware UPS linux package.

David

---

### Post by qamelian on 2008-04-23
> **dryder said:**
> qamelian,

It is not about changing things that aren't broken or about learning - it is about making more drivers, software etc.available to all distros requiring only one item to then be handled by all flavours.

Some things are written for specific distros and will not convert. Example: Eaton Powerware UPS linux package.

David
Can you be more specific regarding your example? As far as I can tell, the Powerware stuff can be compiled on pretty much any *nix.

I'm not trying to be argumentative, about this, Dryder, but I think that some of the opinions expressed by some contributors to this thread are extremely short-sighted. I'm involved in technical and functional support as my profession and, aside from simply helping my clients resolve problems, I also use each support call as a opportunity to help them learn in order to avoid problems in the first place and to give them an edge in trouble-shooting their own issues. I have also taught many seminars over the years relating to basic to intermediate OS topics to application specific courses. Based on almost 20 years of dealing with these same arguments on one platform or another, I stand by everything I have said. I have seen plenty of real-world evidence to back me up and none thus far to convince me I'm wrong. I've been proven wrong about many things in my life, but my opinions on the importance of learning the fundamentals, including being able to compile from source, ...well, I stand firm on those.

---

### Post by smartboyathome on 2008-04-23
> **qamelian said:**
> I know what it does; I've used it. It was the single worst Linux experience I've had in 11 years of being a Linux user. Putting all the programs in one folder is not a good idea and is completely in opposition with the existing standards. There is already an appropriate place for any software, regardless of whether it is part of the base distribution, something you build/install locally on your workstation and applications provided by third parties. The standard is extremely well documented and not at all difficult to learn. If people would expend half as much energy to actually learn the standards that already exist as they spend trying to change that standard into something completely unnecessary, they would be much better off.

I have learned it. I just think that Gobolinux is taking a step in the right direction when it comes to the filesystem.

---

### Post by qamelian on 2008-04-23
> **smartboyathome said:**
> I have learned it. I just think that Gobolinux is taking a step in the right direction when it comes to the filesystem.
We'll have to agree to disagree. Like I said, obfuscation never helps anyone. 

I think the Gobolinux root might initially ease adoption for some users, but if they attempt to user another distro later they will have problems adjusting. The exact same problems they have now, in fact, with the additional confusion of having started out with Gobo. When I was testing Gobolinux, my group of test users was broken down into two groups. One started with Gobolinux, the other started with Debian. At the end of two weeks, the groups "traded" distros. The group that started with Debian made the transition to Gobollinux with virtually no problems, but found the Gobohide system initially confusing. The group that started on Gobolinux and later moved to Debian was completely bewildered and of the 6 members of the group, only one gained any degree of comfort with Debian. 

For me, the best test of the experience was the number of members of the "Debian First" group who have since elected to make the move to Linux. Four out of the six. Of the Gobolinux group, not one even considers linux usable due to the difficulty they had in transitioning from Gobo to Debian. They didn't start out learning fundamentals; the Debian group did. For the record, only one member of each group is involved in the tech business. Remaining members of each group were all what might be loosely termed "typical end-users". This certainly was not an exhaustive or conclusive test due to the small size of the test groups, but I would expect the results to be similar even in a larger group.

---

### Post by dryder on 2008-04-23
qamelian,

It is some time since I contacted Eaton re the linux software. The rpm does not, I should say 'did not' as it is some time since I changed UPS because of it, convert to an installable debian package. This was confirmed by Powerware themselves and they were not prepared to help. Nor were there linux/Ubuntu experts who could get it to work. This was a package problem, not alien or /.configure or anything that could reasonably be understood by users.

I was trying to give just one example.

From your post you have built an amount of knowledge of linux that would far exceed that which would or should be reasonably required of users. That gives you the edge - a good edge - but not a realistic day-to-day 'reasonable to expect to learn' for users.

All I am suggesting is that to make more things available, to give writers more ease to write, create one standard package and let the distros do the necessary. I have said all along 'by gui or by 'new-alien' ', that latter still leaving the command line interface for those who want it.

But may I point out, that whilst a lot of help is given in forums few explain what their commands do - hence users copy and paste and don't learn. Some say 'RTFM" - great - which manual? A great deal of help is meant very genuinely but is often very wrong. Yes, that's a good reason to learn - explaining is teaching. But I am deviating from packages and handling them. And your help is, I'm sure, very gratefully received - and that is not patronising.

David

---

### Post by qamelian on 2008-04-23
> **dryder said:**
> qamelian,

It is some time since I contacted Eaton re the linux software. The rpm does not, I should say 'did not' as it is some time since I changed UPS because of it, convert to an installable debian package. This was confirmed by Powerware themselves and they were not prepared to help. Nor were there linux/Ubuntu experts who could get it to work. This was a package problem, not alien or /.configure or anything that could reasonably be understood by users.
Fair enough. I've encountered the odd package problem, but I've never run into one yet that was unresolvable. Usually the problem is not so much the packaging as much as the way the package was built. 
> 
I was trying to give just one example.

From your post you have built an amount of knowledge of linux that would far exceed that which would or should be reasonably required of users. That gives you the edge - a good edge - but not a realistic day-to-day 'reasonable to expect to learn' for users.

Come on now. I was one of those new users myself once. I remember my first distro didn't even default to a desktop. You needed to install XFree86 on your own. It took me three days of trolling the web to get a working desktop with fvwm and sound through OSS. Up to that point, the closest I had ever got to anything *nix-related was using emacs on my Atari ST. The difference is that I fully expected that I would need to learn a lot and I made the commitment to learn. Any user who is not prepared to make the same commitment is going to be very frustrated because they will continuously run into things that behave in ways that are strange and unexpected to them. 

> All I am suggesting is that to make more things available, to give writers more ease to write, create one standard package and let the distros do the necessary. I have said all along 'by gui or by 'new-alien' ', that latter still leaving the command line interface for those who want it.
This is a great idea in theory, but as I said previously, there will always be someone who will reinvent the wheel because they believe there way is better. By extension, there will always be users/developers who follow suit. Love it or hate it, this is fundamental to the F/OSS world. The same thing happens in Windows with various vendors providing the own installers. The only real different being that they almost all follow the the same basic principles for the front-end. 

It's also important to note that for any package system to be universal, many other factors need to be universal as well. I've encountered packages that failed to work because they required a specific version of gcc to compile successfully and would not work on distros that were standardized on a slighty older version of the compiler. 
> 
But may I point out, that whilst a lot of help is given in forums few explain what their commands do - hence users copy and paste and don't learn. Some say 'RTFM" - great - which manual? A great deal of help is meant very genuinely but is often very wrong. Yes, that's a good reason to learn - explaining is teaching. But I am deviating from packages and handling them. And your help is, I'm sure, very gratefully received - and that is not patronising.

David
I have to agree that the "copy & paste" with no clear explanation is definitely not the right way to help resolve a problem. When I provide support to my clients, whether on-site, via phone, or through remote administration, I always make it a point (unless prevented by the specific circumstances) to explain every step of what I am doing to resolve the issue and my reason for taking that step. This has a calming effect on some times panicky users  and also allows those users to learn ways in which they can help themselves to avoid similar problems in the future. That little bit of extra effort and time expenditure benefits everyone.

I have to admit though: I get very frustrated when I see suggestions (or in some cases almost commandments!) to change things that, for me, are part of the fundamental charm and beauty of Linux specifically and *nix in general. More often than not, the suggestions are to implement some feature that drove me away from Windows into the "arms" of Linux to begin with! :rolleyes:

Anyway, it's getting late here and I need to crash so I can deal with the onslaught again tomorrow.

---

### Post by nonoitall on 2008-04-24
Wow, I have just read over this whole thread and found it to be quite informative.  I can appreciate that there are many experienced Linux users here who find current solutions to be adequate for their needs, but I have to agree with some of the others when I say a unified method for installing and distributing software would really make Linux more attractive.  I've been using Linux off-and-on for over three years now, and have been a programmer for over five.  Over the years, I've learned a lot, and expended considerable time and energy toward learning how to use Linux, but still have never moved beyond dual-booting.  Part of the problem is definitely the lack of a standard for installing and distributing software.

Call me lazy, but I come from the Windows world, and I do not like having to think when I find a program that I want to install.  I want to acquire the software, install the software, and use the software.  I *don't mind* if I have to learn a new method for doing this on Linux, but I want that method to work.  Source code is neat, but it has the obvious problems:
[LIST]
[*]It can take hours of resolving dependencies to install a single piece of software.
[*]There's no real standard for building/installing software.  ./configure && make && make install often work, but the software developer might decide to do things differently, in which case I have to take the time to read and learn his instructions - just to install a program, driver or library.
[*]There's no real standard for removing software.  checkinstall can be kind of handy here, but I still need to spend extra time to enter in the right information so that the package is built correctly.
[*]It can take a very long time to compile some software.
[*]Closed-source software obviously can't be distributed this way.
[/LIST]
So, source code is not going to be the fix-all solution that wins me over.  Let's move on to package managers.  They solve a lot of the problems from the previous method.  Dependencies can be taken care of automatically (at least a good majority of the time).  There *is* a standard method for installing software - it varies from package manager to package manager, but it's not nearly as bad as source code where the method can change depending on what piece of software you're installing.  There *is* a standard for removing software, like above.  And since the software is distributed in binary form, there's no problems with a lengthy compilation or closed-source distribution.  Package managers have done a very good job of addressing the issues inherent to source code distribution.  In fact, from the end-users perspective, they're just about perfect.  But, there is still one problem:

There is no unified format or set of policies for packages.  I can't put some software I've written into a DEB and expect everyone, or even a majority of Linux users to be able to install it.  Even users who run distros that use that package format might have problems, as some Debian packages do not work in Ubuntu, and vice versa.  And that's to say nothing about RPM users, or others who use different package management entirely.

So, as a developer, it's more trouble than it's worth for me to try and build all the packages that it will take to cover all the bases.  Some charitable organizations and disto developers attempt to solve this problem by featuring thousands of pieces of custom-built software in their repositories.  But, even the most complete repositories can't possibly keep up with all the development going on out there, leading to lots of software being outdated, or even completely unavailable.

No offense intended towards anyone, but, IMHO, this is organized confusion.  On Windows, I go to the developer's site, download their software (they maintain the binary themselves, since, well, they only need one for it to work on every Windows machine), and install it.  Microsoft doesn't need to maintain builds of every piece of software that their OS's users could possibly want.  (Even with their resources, I doubt they could.)

A new package manager is not likely to be the answer.  There needs to be a way for software developers to build a single package and have it work for *everyone* (so long as its dependencies are installed, of course).  There are three ways this could happen.  (1) All the distros could agree on a unified package format/policy and discard the others.  (Very unlikely.)  (2) A single package format that could be trivially and automatically converted to the destination's native package type.  (I'm not sure how feasible that is.)  Or, (3) do things the Windows way - throw away the package managers, more or less, and have each software package include its own installer/uninstaller.  Say what bad things you want about the last method, it works for a vast majority of developers and end-users.

Whatever the solution may be, *everyone* needs to use it for it to work.  Otherwise, we're right back where we started.  I'm not demanding anything - I'm just saying where I think the problem is and what I think it would take to fix it.

---

### Post by corn13read on 2008-04-24
sure do it but base it off of apt!

---

### Post by smartboyathome on 2008-04-24
> **corn13read said:**
> sure do it but base it off of apt!

What about the people who like RPM? Would it be fair just to throw that aside for what you like? :(

---

### Post by dryder on 2008-04-24
qamelian,

Where I'm coming from in this debate has nothing to do with learning, level of knowledge or anything else along that line.

I'm being realistic in realizing that drivers, backup programs, commercial software (not everything that is for linux can be free) will not be written in all flavours of linux manufacturers and developers just won't do it and no amount of knowledge will change that. And some will not be open source as too much investment is tied up in it.

Therefore, let there there be one linux basic standard for all to write to - but then let the distros do the distro specific work. I am suggesting by a user choice of gui interface, automatically or by command line.

That is not re-inventing the wheel nor is it fixing something in linux that isn't broken. But what is broken (if it ever existed) is the availability of software that can then, as it should, be made installable by the distro. None of the distro's features, preferences etc. are changed and would still result in rpm, deb or whatever packages but we might, hopefully, increase the willingness of developers to write for linux.

It has nothing to do with what you, I or Joe Bloggs prefers. Only about more software and drivers, etc.

David

---

### Post by qamelian on 2008-04-24
> **dryder said:**
> qamelian,

Where I'm coming from in this debate has nothing to do with learning, level of knowledge or anything else along that line.

I'm being realistic in realizing that drivers, backup programs, commercial software (not everything that is for linux can be free) will not be written in all flavours of linux manufacturers and developers just won't do it and no amount of knowledge will change that. And some will not be open source as too much investment is tied up in it.

Therefore, let there there be one linux basic standard for all to write to - but then let the distros do the distro specific work. I am suggesting by a user choice of gui interface, automatically or by command line.

That is not re-inventing the wheel nor is it fixing something in linux that isn't broken. But what is broken (if it ever existed) is the availability of software that can then, as it should, be made installable by the distro. None of the distro's features, preferences etc. are changed and would still result in rpm, deb or whatever packages but we might, hopefully, increase the willingness of developers to write for linux.

It has nothing to do with what you, I or Joe Bloggs prefers. Only about more software and drivers, etc.

David
Well, I'm afraid I can't agree with you. Obviously your experience with Linux has been different from mine, because based on what I have seen in the past 10-11 years of using Linux and teaching others how to use it, it has everything to do with learning and the willingness to do so. 

There are already standards that are adhered to by virtually every sizable distro I have used. There are times, however, when a technical decision needs to be made that might require straying from the existing standards somewhat to acchieve other goals within the distro. This is and always has been true for virtually every OS ever designed. 

I'm afraid I just will not bother to address any other points in this discussion, because it is apparent that continuing is a recipe for frustration. I stand by my statement that there are technical issues that will always prevent what people are asking for in this thread from ever occuring. The only way What you are looking for will ever occur is if literally every technical difference between distros is eliminated, at which point much of the choice we currently have available would be gone forever.

Colour me gone and all the best.

---

### Post by yanom on 2009-02-18
What if Synaptic could access rpm and portage repositories? And then remember what it installed package x with so it uninstalls with the same tool.

Has anyone gotten portage to work on ubuntu?

---

