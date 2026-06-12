---
title: "Linux Depenency Hell and Packaging Question"
date: 2008-01-24
forum: The Cafe
---

### Post by Yfrwlf on 2008-01-24
If you're not going to re-invent the wheel, at least make sure that users can easily get and install those dependencies required by your program.  I believe this could be accomplished by a new, more intelligent packaging format.  Imagine clicking on a package on the net which includes either links to dependency locations elsewhere on the net, or which includes all the dependencies within the file, and having your browser hand it off to your package manager (or use a plugin) to examine and download only the dependencies that you need from the package (you could also have the option to download the whole complete set of dependencies regardless for use on other systems and/or for archiving purposes).  Then, imagine using libraries that could all happily co-exist side-by-side, perhaps in different directories, so that when a major revision comes out it gets placed in another directory (since major revisions could be the only ones that change the API).```
/usr/lib/gimp/2.0/
/usr/lib/gimp/3.0/
```You could use whatever system a program has come up with, but if programmers are smart about depenencies it seems like such a directory structure would be helpful to use.

My question is, wouldn't this pretty much make software installation on Linux a breeze?  Make a plugin or extend current package managers to be able to recognize such a format or modify current formats to have that capability and it seems to me you've solved a lot of the issues.  Any thoughts about this?  Thanks! :)

P.S.: On a side note, all package managers should be made to recognize mutiple file formats to allow DEBs and RPMs and others to compete with one another.  I'd also like to see the creation of a Linux Package file container in which any of the current formats can reside, which could serve to aleviate confusion slightly with different file names, having a single name that users could recognize, be it .LNX or .NIX or whatever.

P.S.P.S.: I know that an automatic repository URL adder format has been proposed before, but am not sure on the status of it.  However, I think it's a bandage on a bigger problem which is not having to worry about distro-specific and distro-version-specific packagees/repositories, allowing Linux to unify and duplication of effort to be greatly reduced.  "Ubuntu" should be a specific selection of packages from a repository which are supported by Cannonical.  Linux distros shouldn't have to be so segregated from one another if they don't want to be.

---

### Post by macogw on 2008-01-24
RPM's can be installed on Debian systems and vice versa.  The files inside are the same....there's a difference in compression settings, I think and maybe in some scripts in there, but that's why Alien exists.

---

### Post by Mithrilhall on 2008-01-24
I'm actually quite happy with the current state of package management (especially in the Debian based distros). Nothing make me happier than apt-get. Sure, Yum was nice when I was over on CentOS but I'll take apt-get over any other package system I've seen.

---

### Post by hyper_ch on 2008-01-24
> **Mithrilhall said:**
> but I'll take apt-get over any other package system I've seen.
APT is one of my main reasons to use debian-based distros.

---

### Post by az on 2008-01-24
Gnu/Linux is *not* binary-compatible.

The software is made to be compatible and interact at the source level.  Putting effort to make it work at all costs at the binary level is not worth it.

Binary compatibility costs a lot in development and performance.  Once you go down the road of making a stable binary interface, you are committed to that and must pay the price.

Package management is advanced enough so that users don't even have to interact with packages on either the source or package management level.  You just pick what you want to install and make it go.

If you are an "in-between" user, where you are not advanced enough to know how to avoid dependency problems at the source level, but are advanced enough to want something that is just out of the reach of your package manager, you may think that binary compatibility is a good thing.  It's not a big enough reason to do it, IMHO.

---

### Post by aysiu on 2008-01-24
> **Yfrwlf said:**
> 
My question is, wouldn't this pretty much make software installation on Linux a breeze? As far as I'm concerned, it already is a breeze. In fact, when I have to install stuff on Windows or OS X, I get annoyed that I have to fuss through CDs, activation codes, and web searches to get all the software I need to install--then there is all the unnecessary clicking and rebooting.

With Ubuntu, almost all my software needs are a Synaptic Package Manager search away. Once all the packages have been marked for installation, they can all be downloaded and installed together. There are a few packages I use that are outside the repositories, but they are (thanks to gDebi) double-click installations (Opera, for example).

---

### Post by macogw on 2008-01-24
> **az said:**
> Gnu/Linux is *not* binary-compatible.
In some cases, binaries are compatible though...I mean, the Nvidia drivers come as a .run which just holds a binary and some scripts to tell it where to go.  Even though that binary is only compiled once, it works on all distros and any 2.6.x kernel (not sure about 2.4.x)

---

### Post by forrestcupp on 2008-01-24
My main complaint isn't about apt, but about Synaptic.  If you install a package in Synaptic, it will install that package and all of its dependencies.  But if you remove that same package, it doesn't remove any of the dependencies that it installed, even if they aren't being used by anything else.

I know there are command line ways to purge all of these unused dependencies, but a lot of people use Synaptic, and I think it should be updated.

---

### Post by koenn on 2008-01-24
> In some cases, binaries are compatible though...
binaries can, in some cases be compatible with miltiple systems, but it's not a requirement, and not something that is actively sought after. 

developers write source code, and distributors compile and package it so that it's compatible with *their* distribution. Simple. Effective. 
I'm not aware of any dependency hell.

---

### Post by koenn on 2008-01-24
> **forrestcupp said:**
> My main complaint isn't about apt, but about Synaptic.  If you install a package in Synaptic, it will install that package and all of its dependencies.  But if you remove that same package, it doesn't remove any of the dependencies that it installed, even if they aren't being used by anything else.

I know there are command line ways to purge all of these unused dependencies, but a lot of people use Synaptic, and I think it should be updated.

[http://ubuntuforums.org/showthread.php?t=46547](http://ubuntuforums.org/showthread.php?t=46547) :
Synaptic also supports this now and will automatically mark unused
dependencies for removal (it ask kindly first of course before it
removes anything). It can be turned off by starting synaptic with:
# synaptic -o Synaptic::AutoRemove=false
(it will save that option on exit).

---

### Post by forrestcupp on 2008-01-24
> **koenn said:**
> [http://ubuntuforums.org/showthread.php?t=46547](http://ubuntuforums.org/showthread.php?t=46547) :
Synaptic also supports this now and will automatically mark unused
dependencies for removal (it ask kindly first of course before it
removes anything). It can be turned off by starting synaptic with:
# synaptic -o Synaptic::AutoRemove=false
(it will save that option on exit).

Well, that's from '05 and as long as I've been using it I've never seen it work like that.  Does that mean I have to install the auto-remove package, or am I just not finding that option in the menus?

---

### Post by koenn on 2008-01-24
no idea. I've heard people mention auto-remove and aptitude before,  so I did a search, and that's what came up. 
I hardly ever use synaptic, most software i need is already in a standard ubuntu desktop.

---

### Post by ycason on 2008-01-24
> **forrestcupp said:**
> Well, that's from '05 and as long as I've been using it I've never seen it work like that.  Does that mean I have to install the auto-remove package, or am I just not finding that option in the menus?

On the bottom left of the Synaptic window there should be a set of buttons.

Sections, Status, Origin...

You'll want the Status button.  The auto removable programs will be in the "Installed (Auto Removable)" section.

:popcorn:

---

### Post by jseiser on 2008-01-24
on the talk of package managers, i would say i prefer pacman.  I also like ports systems, its really nice to copy a file from one diretory, into a build directory and type makepkg, then pacman -U package and have it installed, able to be updated and removed from my package manager.  it is also really nice if you get yaourt and having the ability to compile programs posted to the aur, once again being able to update them and remove them all from the package manager.

---

### Post by M7S on 2008-01-24
I think apt and synaptic works great. Problems occur  first when you need to install something on a computer without working internet connection. Apt-zip isn't really as intuitive as apt-get. I couldn't figure it out last time when I tried. (I was under quite a bit of time pressure, though.)

---

### Post by macogw on 2008-01-24
EDIT:  I remembered wrong.  I was thinking of [this announcement](http://lists.debian.org/debian-devel-announce/2007/08/msg00000.html), which says that Debian's new apt-get will install all recommends like aptitude does. It doesn't say anything about removal.  I associated removal with it because I asked on a LUG mailing list if it would also affect removal, but nobody knew, so I guess this is a good time to actually ask a developer.

---

### Post by erfahren on 2008-01-24
From my point of view (a novice ) I think the current system works well too. In my experience (and from what I understand) if .debs are packaged correctly Gdebi will already automatically download and install any dependencies that are needed from the repos. Personally, (and I'm sure I'm not alone here) I wouldn't want an installer file downloading some dependency it needs from somewhere else on the internet. That's a security risk. (Actually, there was a forum post about that awhile back where it was said that the developers were considering(?) a system where there would be measures set to prevent the installing of packages that weren't certified. That's a little extreme, but the reasoning behind it was to prevent the type of scenario where a user gets directed to download other obscure packages.)

I *would* like to see developers be more clear when they list the dependencies that their software need and seperate what you need to compile it from what it needs to run. Oftentimes it seems that compiling instructions are written for other developers, for instance: "For the GUI you need the GTK development packages" -- huh?

Side note: I don't know if something like this exists - but is there a main log of sorts that is created by ap and /aptitude that records everting installed? I know there's the Synaptic History (which records the automatic upgrades as well - which is good), but does it record packages that are downloaded and installed by Gdebi? As I recall, when Gdebi opens a little terminal informing you that it's installing other packages, there's no way to copy and paste the information. Also - does aptitude create a log? I know that packages installed through it aren't recorded in the Synaptic history.

Anyway, I sure wouldn't want all the dependencies a program needs included with it, especially if they make them coexist with equivalent libraries (for instance) from other programs (maybe I'm misunderstanding what the OP is saying). That would create a lot of redundancy and make the entire file system more complex.

I know it would be difficult to deal with dependencies without an internet connection, but there is work being done to help with that from what I understand - see: [APTonCD](http://aptoncd.sourceforge.net/) and [this forum post](http://ubuntuforums.org/showpost.php?p=3851343&postcount=7).

There is also the "apt-file" program (available in the repos) that will make a list of all the packages in the repos and all the files they contain - so if you get a error message like that "libxyz.so" cannot be found you can use apt-file to find which package it's in - its mentioned [here](https://help.ubuntu.com/community/CompilingEasyHowTo) under "Resolving Dependencies".

In any event - the term "Dependancy Hell" is a little outdated. I heard that term when I first heard of Linux (back in the late 90's) before there were package management systems and/or before they were what they are now. 

Personally, I've *rarely* found a program for Linux on the internet that wasn't available in the repos, and more times than not, I was able to find a .deb for Ubuntu [elsewhere](http://www.getdeb.net/). It would also be up to the individual software developers to do whatever it is they needed to do on *their* end to implement a system to where you are linked to the required dependencies.

I don't know, maybe I'm misinterpreting the OP's suggestion, but the current system works great IMO, much better than I ever anticipated when I first started using Ubuntu.

-- that's just my $.02 anyway.

---

### Post by macogw on 2008-01-24
> **erfahren said:**
> 
Side note: I don't know if something like this exists - but is there a main log of sorts that is created by apt and/or aptitude that records everthing installed? I know there's the Synaptic History (which records the automatic upgrades as well - which is good), but does it record packages that are downloaded and installed by Gdebi? As I recall, when Gdebi opens a little terminal informing you that it's installing other packages, there's no way to copy and paste the information. Also - does aptitude create a log? I know that packages installed through it aren't recorded in the Synaptic history.
Aptitude has a *very* good log, which is why it's often recommended over apt-get.  It remembers whether things were manually or automatically installed, which is how it knows what to remove (and if you tell it not to remove those when it asks, it'll mark them manual so it won't ask again).

However, I don't know where said log resides.

If you want to get a complete list of the statuses of every package currently installed, deinstalled, or held, you can run ```
dpkg --get-selections
```
If you want the listing to include purged packages (but still list them all), do it like this:
```
dpkg --get-selections "*"
```
If you send that output to a text file like this:
```
dpkg --get-selections > packages.txt
```
you can feed that text file back into dpkg on another computer to make that computer automatically install/deinstall/hold those packages to match the first computer.  You do that like this:
```
sudo dpkg --set-selections < packages.txt
sudo apt-get -u dselect-upgrade
```

---

### Post by 23meg on 2008-01-24
[QUOTE=Yfrwlf]a bigger problem which is not having to worry about distro-specific and distro-version-specific packagees/repositories[/QUOTE]

The scope of this is beyond package management. No amount of producing "new" package management ideas will solve it. What you're worrying about is just the symptom of the problem; that is, if you see the current distro-centric packaging paradigm and its byproducts as inherently problematic.

---

### Post by erfahren on 2008-01-24
thank you Macogw - good to know

(I meant to say "apt and/or aptitude ..." - nothing like seeing a bunch of your own typos get quoted - lol !)

---

### Post by forrestcupp on 2008-01-24
> **ycason said:**
> On the bottom left of the Synaptic window there should be a set of buttons.

Sections, Status, Origin...

You'll want the Status button.  The auto removable programs will be in the "Installed (Auto Removable)" section.

:popcorn:

As far as I can tell, that is just a list of things that will work with auto-remove, or whatever it is.  I don't see an option to go through and remove all of the unused dependencies.

---

### Post by erfahren on 2008-01-25
> **forrestcupp said:**
> As far as I can tell, that is just a list of things that will work with auto-remove, or whatever it is.  I don't see an option to go through and remove all of the unused dependencies.
Those *are* the unused dependencies. Removing them from there would be the same as doing "sudo apt-get autoremove" in the terminal.

The problem would be though, if a package was installed maunally to resolve a dependancy of a program that the user installed by some other means (like with a .run or "make install") they would still show up there (wouldn't they?). It would be nice to have a way to create a "lock" of sorts on a package you know you need. Maybe a way to make a reminder note so you'd get a message such as: "You marked this as required for the program *foo*, are you sure you want to remove it?".

I avoid using other installers unless it's clear on how to uninstall the program if needed. If I need to compile it I like to use [url=https://help.ubuntu.com/community/CheckInstall]CheckInstall[url] to create a .deb package.

I install and uninstall programs quite often just to try them out. Now that I'm more familiar using Synaptic and aptitude I never have a problem with unused dependencies sitting around.

---

### Post by ssam on 2008-01-25
they installing multiple versions would be good. the gobolinux filesystem looks like it can do it.

currently there are a few individual packages in debian/ubuntu that can have multiple versions installed. but it would be clever if it was made to work for any package. then the backports people would not have to worry about breaking existing packages. (eg no firefox backports because lots of packages use the firefox rendering engine)

---

### Post by Yfrwlf on 2008-02-09
If you created a system of APIs from the ground up so that you could ensure binary compatibility without the need to recompile a program for every situation of every different possible kernel option turned on or off or set to different values, a system that was streamlined and as fast or nearly as fast as the compiled-from-source versions, if this system was in place at the kernel level on up, you wouldn't be forced to recompile anything, and could have both binary and source compatibility at every level throughout the OS.  Until that happens, some higher-level compatibility system will have to be relied upon, similar to how we have Java (except, faster than Java...).  I don't quite understand how binary compatibility is possible, but it is, to some degree.  For example you can go and download the Linux version of Second Life, and run it, and it Just Works.  If everything was like that, that would be great, but things, especially at lower levels like kernel drivers, weren't designed for this binary compatibility, instead these switches/flags are all thrown into the source while compiling, instead of having an API that says "this switch is on, this one is off" so that you can have binaries be intelligent and not need to be *compiled* with the switches on or off yet still be as fast and responsive as their compiled-from-source cousins.  There *has* to be a way to implement such a system, I refuse to take no for an answer.  Linux should have source *and* binary compatibility across the board.  If you don't want the binary compatibility stuff, fine, but for users that do they should be able to install/enable that functionality easily.

I'll repeat my concern: I want users to get the programs they want/need.  That's all.  There is a huge problem right now with getting anything outside the repositories.  It shouldn't matter what distro you're running, you should be able to install any program you want, and the program creator should not have to compile a binary for every distro, and users should not be force to compile from source if they don't care to and would like to use a program within minutes instead of possibly within hours depending on it's size.

> **macogw said:**
> RPM's can be installed on Debian systems and vice versa.  The files inside are the same....there's a difference in compression settings, I think and maybe in some scripts in there, but that's why Alien exists.

But it doesn't work by default.  What good is Alien when users *can't* go get an RPM and install it?  It doesn't work, try it.  Go to Sourceforge, download an "RPM", and click on it.  Witness the magic of it not working.  If Alien is going to be serious about actually supporting RPMs, then it should be installed by default or working alongside/with apt-get, or whatever it takes to get RPM and DEB files working on Ubuntu and any distros.  I don't care about having different package formats, that's fine, what I care about is being able to install the software I want and all other users doing the same thing.  That's the problem here and the only one I'm trying to address, so if your answer then is "install alien by default and make it work within the GUI" then so be it, but I think this issue is much more complex than packaging formats, it's about dependencies and resolving them easily in all situations.  When Linux users have a very difficult time sharing programs with one another, Linux will never make 1st place.

Or why can't dpkg and/or apt-get be modular and pluggable, so you can just add on support for RPM or other new packaging formats, if that's really all there is in the differences between the two systems.  That's the way it should be, and that's the way things are heading (towards modular programming) and I'd love for things to get there.  But again, it's not just a package format difference problem, it's a dependency issue too, and all current systems suck.  DEB2 may be better, but it's still DEB2.  Why not call it the Ultimate Linux Package Manager or something instead of having it based on one package format. :P

It bugs me to no end that these awesome standards exist like ODF and XML and other things, yet when it comes to Linux, developers between distros can't even get together for long enough to create a standardized, XML-based Linux Package Format.  Linux is precisely *where* such a thing is needed and should be expected.  But, again, whatever, just at least make your package systems able to understand these different formats even if you're not going to make a single standard format.  Having multiple formats is fine, just implement them please.

> **Mithrilhall said:**
> I'm actually quite happy with the current state of package management (especially in the Debian based distros). Nothing make me happier than apt-get. Sure, Yum was nice when I was over on CentOS but I'll take apt-get over any other package system I've seen.

Not talking about how easy it is to install repository packages, even though it's certainly noteworthy, but instead the problems that exist which is trying to install anything outside your distro versions repository.  There should be only one repository needed: the Linux repository.

> **az said:**
> Gnu/Linux is *not* binary-compatible.

The software is made to be compatible and interact at the source level.  Putting effort to make it work at all costs at the binary level is not worth it.

Binary compatibility costs a lot in development and performance.  Once you go down the road of making a stable binary interface, you are committed to that and must pay the price.

Package management is advanced enough so that users don't even have to interact with packages on either the source or package management level.  You just pick what you want to install and make it go.

If you are an "in-between" user, where you are not advanced enough to know how to avoid dependency problems at the source level, but are advanced enough to want something that is just out of the reach of your package manager, you may think that binary compatibility is a good thing.  It's not a big enough reason to do it, IMHO.

You're not committed to anything, you will always have the source code, so if you want to compile from source so be it.  First off, having a standardized API doesn't limit the system in any way, that's like saying OpenGL is the devil and no one should make a program that talks to it.  You're not forced to using those APIs like OpenGL (avoiding the discussion of how much of an API OGL actually is), you can make your own system that communicates with *specific programs only*, that will break if a user tries to remove those programs or use something else, but do you think your program would get widespread use?

It's like Microsoft trying to make their OS "depend" on Internet Explorer or Windows Media Player.  That's not being modular, that's not programming wisely, that's locking users in, and that's not at all what anyone wants except for companies who want something to be proprietary.

Do you honestly believe/know that binary compatibility is bad, and that the only "standards" you could ever possibly have are on the source level?  Three more responses to that, first being that as I pointed out there already are tons of standards that are for binaries (see file formats, APIs, Xorg, etc).  Secondly, if the only possible way to make installing programs across distros possible is to use source code (which it's not at all IMO and source/binary has nothing to do with dependency issues) then the solution would be to make installing programs from source a snap which will also limit the ability for anyone to make something closed-source for Linux which will also not fly (even though I prefer open of course like anyone would).  Thirdly, that's a horribly defeatist attitude.  Saying "no you can't" is always the wrong answer.  Anything is possible.  Do you think it's completely impossible to create a "platform/API/standardized system" that would allow expansion for new technologies in a non-bloated way while retaining compatibility with older technologies?  Maybe we should try to think a little harder about solutions before saying "nope, can't be done!"  Even though I hate Adobe, I don't expect them to make a version of their program for all 8432598325 Linux distributions.

As far as this compiling and dependency stuff goes, perhaps what's important here is why do you have to compile?  Why do certain flags have to be turned on or off at the source code level so that you end up with a different binary than someone else?  It seems to have been designed (and I guess it was) from the ground up to only be compatible at the source level.  Why can't programs just throw switches on or off instead after they are compiled?  If mechanisms were put in place to allow programs to be compatible on the binary level too, I'll bet such a system could be made as streamlined as the programs that are compiled from source.  Even if you couldn't make it the same or could only get really really close to the same speed, at least you'd have compatibility, which is what is needed for a computing platform.  Sending KDE 4 to a friend and expecting them to 

> **aysiu said:**
> As far as I'm concerned, it already is a breeze. In fact, when I have to install stuff on Windows or OS X, I get annoyed that I have to fuss through CDs, activation codes, and web searches to get all the software I need to install--then there is all the unnecessary clicking and rebooting.

With Ubuntu, almost all my software needs are a Synaptic Package Manager search away. Once all the packages have been marked for installation, they can all be downloaded and installed together. There are a few packages I use that are outside the repositories, but they are (thanks to gDebi) double-click installations (Opera, for example).

Again, I'm not talking about repository installations.  Like I pointed out in my original post, try installing something outside the repositories sometime, or giving a program to a friend who's on a different distro.  Good luck!

> **macogw said:**
> In some cases, binaries are compatible though...I mean, the Nvidia drivers come as a .run which just holds a binary and some scripts to tell it where to go.  Even though that binary is only compiled once, it works on all distros and any 2.6.x kernel (not sure about 2.4.x)

Actually I believe that the binary compiles the driver to some degree, which is why you need your kernel headers to be installed before you can run the driver installer.  While functional in some kind pathetic way, it's a horrible system.  Ideally it should be a package format that you run with a package manager which knows that it needs some dependencies already, and won't break when you don't have them.  Normal users aren't going to care to use the terminal installation method, but of course that should still exist when you DO need it or if you do want it.  Not to mention, you shouldn't need kernel source for installing a driver any way, it should be completely modular and pluggable.  There should be a "driver format" that can communicate with your kernel's driver API.

> **koenn said:**
> .
binaries can, in some cases be compatible with miltiple systems, but it's not a requirement, and not something that is actively sought after. 

developers write source code, and distributors compile and package it so that it's compatible with *their* distribution. Simple. Effective. 
I'm not aware of any dependency hell.

Because you're playing within the old, outdated jail cell that you're used to IMO.  There has to be a much better way than that.  A way to share programs easily between users/distros.  If that way is to automatically compile everything from source while resolving any dependency requirements all automatically so be it, better than nothing for now, but ideally you don't want installing software to take an hour depending on it's size.  I believe there is a better way, to have compatibility at the binary level, and that it's possible and practical for normal users and all without a huge loss in performance or anything like that.

> **jseiser said:**
> on the talk of package managers, i would say i prefer pacman.  I also like ports systems, its really nice to copy a file from one diretory, into a build directory and type makepkg, then pacman -U package and have it installed, able to be updated and removed from my package manager.  it is also really nice if you get yaourt and having the ability to compile programs posted to the aur, once again being able to update them and remove them all from the package manager.

That is a great system, the ability to have a package upgraded and removed/installed automatically is a pleasant experience indeed.  That's what we need for all users, regardless of distro, so that we can have true software sharing.

> **erfahren said:**
> Personally, (and I'm sure I'm not alone here) I wouldn't want an installer file downloading some dependency it needs from somewhere else on the internet. That's a security risk. (Actually, there was a forum post about that awhile back where it was said that the developers were considering(?) a system where there would be measures set to prevent the installing of packages that weren't certified. That's a little extreme, but the reasoning behind it was to prevent the type of scenario where a user gets directed to download other obscure packages.)

First off if you try to install something that's not certified, it will warn you, both in the GUI installers and in apt-get, probably even dpkg.  You can get your packages from where ever you want, it's up to you, but you should not be forced to get them from "Ubuntu repositories" and you should be able to share any Linux program with a friend, regardless of distro or especially distro version.  I'm talking about more freedom for users, and more compatibility, which is the same thing.

> **erfahren said:**
> I *would* like to see developers be more clear when they list the dependencies that their software need and seperate what you need to compile it from what it needs to run. Oftentimes it seems that compiling instructions are written for other developers, for instance: "For the GUI you need the GTK development packages" -- huh?

An automated universal system for automatic dependency resolution and even downloading, I want that too.  The package file should not only contain information on the dependencies but also where to get them from and which versions are needed, etc, even though there should be some APIs in place to greatly reduce harsh dependencies.

> **erfahren said:**
> Anyway, I sure wouldn't want all the dependencies a program needs included with it, especially if they make them coexist with equivalent libraries (for instance) from other programs (maybe I'm misunderstanding what the OP is saying). That would create a lot of redundancy and make the entire file system more complex.

That's a depenency problem.  If you had good, scalable APIs then you wouldn't have to have such strict dependencies, but that fault lies with the coders for the programs and the coders for the libraries.  This example is completely fantasy for the most part, but lets say you wanted to install Quake Wars which used OpenGL 2.0 while, say, Second Life used OpenGL 1.0.  Would you rather just not install OpenGL 1.0 and just not use the program at all?  I think I'd rather install the extra dependency so I could run the program on my computer.  Now, another option would be to compile Second Life from source, IF it was available (which it's not) so that the program could use the new version of OpenGL. Or, you could simply have mechanisms and methods of communication (APIs) in place that were scalable and would allow the program to interface properly with OpenGL 2.0 because they made OpenGL 2.0 use standard methods of communication that were all still fully functional with version 1.0 programs.  It IS possible to do all this.  You make an API, a language, that libraries and programs both use.  By doing so, you can have 50 different libraries that do the *same thing* with no problem, but not *need* all of them, they just all need to use the same *language*.  This allows there to be forking and duplication of effort in Linux where developers feel they need/want to spend their time, but it will *not* force everyone else down the road from them to change their whole program just because of it.  It's called **modularity**.

What would you do if the FTP protocol format kept changing on you?  Everyone would go ballistic, and switch to a different format, or quickly develop a standard language or method of communication.  A file format in itself is a standard.  It is an example of what I'm talking about, and all of you love them and use them and take them for granted.  I'm asking for such magic to be able to occur on all levels of the Linux system, so that the lives of developers and end users and companies all are made much, much, much simpler.  Sure, you may love using that program you installed from your repository, but someone had to compile that program for your exact version of your exact distro.  That kind of lock-in isn't acceptable, and should not occur in Linux, and you'll face that cold reality when you're suddenly faced with compiling something from source.  Asking a noob to do something like that is completely out of the question.  For Linux to take over, this problem has to be addressed, so I wish [the folks at the Linux Foundation who are working hard on this issue]("http://www.linux-foundation.org/en/Packaging") good luck as well as anyone else.

> **erfahren said:**
> In any event - the term "Dependancy Hell" is a little outdated. I heard that term when I first heard of Linux (back in the late 90's) before there were package management systems and/or before they were what they are now. 

Personally, I've *rarely* found a program for Linux on the internet that wasn't available in the repos, and more times than not, I was able to find a .deb for Ubuntu [elsewhere](http://www.getdeb.net/). It would also be up to the individual software developers to do whatever it is they needed to do on *their* end to implement a system to where you are linked to the required dependencies.

I don't know, maybe I'm misinterpreting the OP's suggestion, but the current system works great IMO, much better than I ever anticipated when I first started using Ubuntu.

-- that's just my $.02 anyway.

Thanks for your comments.  My post was to address the problem with the current system.  You simply disagree with me that it's a problem, and as long as all your friends use Ubuntu, oh and it has to be the same version of Ubuntu, and as long as the rest of the world follows suit so that all the developers out there for programs you (or your friends, or other Ubuntu users) want make a Ubuntu package of their program for your exact Ubuntu version, then I guess there won't be any problems with the current system.

Problem is, all those things aren't reality.  This thread is about addressing this problem, otherwise I wouldn't be here posting this, so for those who agree that a problem exists, we want to see it fixed. :)

> **23meg said:**
> The scope of this is beyond package management. No amount of producing "new" package management ideas will solve it. What you're worrying about is just the symptom of the problem; that is, if you see the current distro-centric packaging paradigm and its byproducts as inherently problematic.

I agree, it's about dependencies and why they exist so strongly, and why there isn't much more modularity in Linux from the ground up.  The funny thing is, binary compatibility does exist, and on some higher level you can have this even if the lower level is extremely non-modular.  Well, I guess it's not too hard to understand.  Java and VMs and other things exist upon this system, after all.  If we have to settle with a system that is layered on top of a system which is old and un-modular until the entire thing can be updated to be very modular on both binary and source levels, that's fine by me.  I certainly wouldn't mind talking about all the issues here though, so please redirect the topic to what you feel are the real issues if you wish.

While I'm at it though, at those deeper levels, having to compile kernel drivers for your specific kernel is definitely a no-no.  A system needs to be made so that binary compatibility for drivers among other things can exist, and instead of having switches made static placed into the compiler at compile time, these need to be moved into an API.  In other words, if the entire Linux system was designed to be only source-compatible from the ground up, it needs to be redesigned with binaries in mind too.

> **ssam said:**
> they installing multiple versions would be good. the gobolinux filesystem looks like it can do it.

currently there are a few individual packages in debian/ubuntu that can have multiple versions installed. but it would be clever if it was made to work for any package. then the backports people would not have to worry about breaking existing packages. (eg no firefox backports because lots of packages use the firefox rendering engine)

Exactly, and it would also have another good side effect too, which is that those libraries that didn't try to create or use some APIs would need to start doing so if they wanted to see use of their libraries continue, because it would be hell for end users to have to install 20 different versions of their one library to run different programs all because they refused to use a common, scalable language.  Part of that reason is because right now they just expect users to recompile everything, and there isn't much thought put into binary-level APIs.  That will change in Linux, and I want to see that happen as well as a completely automated system for installing/compiling sources when users have to or want to do so.  It should not be a requirement, however.  If I want to send a friend OpenOffice, a newer version, or some other program, and it's not in their repository, and I don't have the source for it, or I don't want to force them to compile it which would take hours on their slow system, they **should be able to install it**.  The ability for Linux to be installed on slower computers is nice to have, but please, don't force them to compile everything on those slow computers too.

A Linux distro should not be forced to rely upon an ecosystem of users compiling everything for it, either.  That's an extremely poor system.  It's impossible for all developers to compile their programs for every system, and to host all these binaries for every single system, or to force users to wait for hours while things compile is just insane.

Linux can do better than that.

---

### Post by Polygon on 2008-02-09
tl;dr.

that is one freakkkking long post

---

### Post by Yfrwlf on 2008-02-09
> **Polygon said:**
> tl;dr.

that is one freakkkking long post

I try my best. :)

---

### Post by koenn on 2008-02-09
> **Yfrwlf said:**
> In other words, if the entire Linux system was designed to be only source-compatible from the ground up, it needs to be redesigned with binaries in mind too.

Well, it *is* designed to be only source-compatible from the ground up. I read an interview with Torvalds once where he explains why this is so, and while I don't remember his reasoning, I do remember it made sense to me then. So if you have an issue with this, you're going to have to take this up with the guy at the source.

---

### Post by saulgoode on 2008-02-09
[http://www.mjmwired.net/kernel/Documentation/stable_api_nonsense.txt](http://www.mjmwired.net/kernel/Documentation/stable_api_nonsense.txt)

---

### Post by koenn on 2008-02-09
Quote:
Originally Posted by koenn 
.
binaries can, in some cases be compatible with miltiple systems, but it's not a requirement, and not something that is actively sought after.

developers write source code, and distributors compile and package it so that it's compatible with their distribution. Simple. Effective.
I'm not aware of any dependency hell.
> **Yfrwlf said:**
> IfBecause you're playing within the old, outdated jail cell that you're used to IMO. 
I think you're wrong about that. 
My computer does what I want and need it to do. I don't see how that makes it an old outdated jail cell. 

------
I recently installed Oracle Express rdbms and a number of their tools, all downloaded  from their website. I also installed VMware Server,  with a package from the VMware website. 
In both cases, the software installed without any trouble, even though it was not coming from the repos. 
It seems to me that devs / vendors who have their act together, have no problems delivering software that is distro-agnostic. 
So, again, I'm not aware of any dependency problem.

---

### Post by az on 2008-02-09
> **Yfrwlf said:**
> If you created a system of APIs from the ground up so that you could ensure binary compatibility without the need to recompile a program for every situation of every different possible kernel option turned on or off or set to different values, a system that was streamlined and as fast or nearly as fast as the compiled-from-source versions, if this system was in place at the kernel level on up, you wouldn't be forced to recompile anything, and could have both binary and source compatibility at every level throughout the OS.  Until that happens, some higher-level compatibility system will have to be relied upon, similar to how we have Java (except, faster than Java...).  I don't quite understand how binary compatibility is possible, but it is, to some degree.  For example you can go and download the Linux version of Second Life, and run it, and it Just Works.  If everything was like that, that would be great, but things, especially at lower levels like kernel drivers, weren't designed for this binary compatibility, instead these switches/flags are all thrown into the source while compiling, instead of having an API that says "this switch is on, this one is off" so that you can have binaries be intelligent and not need to be *compiled* with the switches on or off yet still be as fast and responsive as their compiled-from-source cousins.  There *has* to be a way to implement such a system, I refuse to take no for an answer.  Linux should have source *and* binary compatibility across the board.  If you don't want the binary compatibility stuff, fine, but for users that do they should be able to install/enable that functionality easily.



Ever heard of autopackage?  It provides run-time binary compatibility.  The catch is, every upstream developer has to buy-in and use the underlying libraries.  Never gonna happen.

Autopackage is dead.

> **Yfrwlf said:**
> 
I'll repeat my concern: I want users to get the programs they want/need.  That's all.  There is a huge problem right now with getting anything outside the repositories.  It shouldn't matter what distro you're running, you should be able to install any program you want, and the program creator should not have to compile a binary for every distro, and users should not be force to compile from source if they don't care to and would like to use a program within minutes instead of possibly within hours depending on it's size.

That method has proven to be a nightmare on every platform on which it is implementd (Solaris is dead slow, Windows is unsafe, etc...)  If you want to refuse to see that, then you can carry on this discussion by yourself.

> **Yfrwlf said:**
> 

You're not committed to anything, you will always have the source code, so if you want to compile from source so be it.  First off, having a standardized API doesn't limit the system in any way

Yes it does.  It's an every-increasing tax on developer, code and performance resources.  The API and the ABI should change as the software needs it to.  The particular distro should abstract that.

> **Yfrwlf said:**
> 
  Not to mention, you shouldn't need kernel source for installing a driver any way, it should be completely modular and pluggable.  There should be a "driver format" that can communicate with your kernel's driver API.

Every single binary-only driver that has ever been released by a third-party either doesn'T work anymore or will one day render your system completely  unstable.  Binary-only kernel drivers that work only do so for a very short period of time.  How many posts on this forum are about getting the latest binary-only graphics driver to run because the current version makes their system crash?

> **Yfrwlf said:**
> 
What would you do if the FTP protocol format kept changing on you?  Everyone would go ballistic, and switch to a different format, or quickly develop a standard language or method of communication. 


You imply that the file format would change for no other reason than to make your life difficult.  You have to realize that these sort of things don't happen without reason.  You are ignoring all the reasons why there is no binary compatibility.

---

### Post by Yfrwlf on 2008-02-11
I'm all for compatabililty in every way possible as long as it allows for improvements in the way things are done, or in other words having scalable, modular, standardized methods of communication in place that allow change, but keep everyone on the same page, so that programs don't break constantly.  I don't think I'm being arrogant by saying that everyone wants this.  It's the difference between good programs and bad ones, it's simply intelligent.  Otherwise you'd be saying standardized anything is useless and foolish and there's no point.

So if we all agree on that, we're to the next question: is binary compatability possible.  Well, sure, but how smart is it, and smart for whom?  My question is is there any way to have a solution that is, like I just mentioned, scalable, modular, and standardized, yet allows for improvment, that could work for both binaries and sources?

I'm not asking you to rehash old ways of thinking, I'm asking is it possible to create such a perfect system, or does this simply have no solution IYO?

I'm not trying to attack anyone, and it's clear that some of you feel the answer is a definite "no" and have given up on the possability of any solution.  That's fine, I guess you're done reading this thread then.

Anyone else think there could be a solution to this problem, and have any ideas?

Here's mine:
I'm still struggling with understanding how it all works, I'm trying to learn, so is the problem with binary compatability that it is based on **directly** using libraries instead of interfacing with a standardized API, so that the programs that use them have a more and more difficult time because they are restrained from improvments in technology, **or** is it because the set of standardized library packages doesn't increase fast enough, or is it both?  Any information/ideas/opinions would be lovely. :)  But getting to my actual idea for a solution, which isn't new, and I've said it many times before: APIs.  OK, so someone comes out with a new library that is totally different in terms of it's language or whatnot, but it *functions the same* as another library that, say, happens to be in the LSB.  Well, instead of the LSB adding this package into the "standardized package set" and becoming bigger and more bloated with time, why not have the libraries all use a common API, so that you can use whatever library you want, but the libraries can do the same things.  If one library does the same things better, or does more things, then have it *replace* the older library.  In this case, the library would still be compatible with older programs that used the older library, because it would still use the same API and be capable of the same things, so the program wouldn't know the difference, and the LSB "set" wouldn't become more and more bloated.

Basically I'm saying, why can't you make the interface between libraries and programs and everything be completely modular, completely lubricated, by having a common interface between everything that can easily scale to include any new technology that comes along?  Isn't there some way to convert or translate or standardize and catagorize all systems so that any programming language can use any other programming language's classes or any program could use any function or call or whatever that it wanted to because the system would contain a library of all possibilities...

Maybe what I'm saying is can libraries be broken down so that instead of being these massive things they can be sorted into a bunch of individual "books", and a program can call on any books that they want to, instead of depending on the whole specific library, and if any newer books come out they can replace the older books, or be added into the library.

Perhaps I *really* don't understand programming, and I don't claim to, but I really don't understand yet why this isn't *possible*.  Only respond if you care to.  If you don't have anything constructive, don't bother. :)  I thank everyone for their input thus far.

Dare to dream.

---

### Post by eye208 on 2008-02-11
> **az said:**
> Gnu/Linux is *not* binary-compatible.
If you talk about drivers, you are right.

If you talk about applications, you are wrong.

---

### Post by 23meg on 2008-02-11
[QUOTE=Yfrwlf]I'm still struggling with understanding how it all works, I'm trying to learn, so is the problem with binary compatability that it is based on directly using libraries instead of interfacing with a standardized API, [/QUOTE]

The correct term is ABI. Understanding what an ABI is will help you better understand why things work the way they work.

---

### Post by Yfrwlf on 2008-03-30
> **23meg said:**
> The correct term is ABI. Understanding what an ABI is will help you better understand why things work the way they work.

Thanks, and I did read up on it, and I still think there's no reason why the existing ABI can't be expanded further to make it a complete universal standardized ABI.  If you'd like to make some specific arguments why, go ahead, but I highly doubt I will never be convinced that there are any good reasons for not having a universal cooperative standard for binary installation across Linux distros because I strongly believe **doing so won't hurt anything**, since you'll always have the choice not to follow the standards, but I also strongly believe that this feature will have many benefits and will provide much, much greater freedom.  If you want to make software that is friendly to users who want to try it, you can make it conform to good standards, and if you have additional dependencies you can include all of them in your program package or whatnot.  Or, if you want, you can force your users to run around trying to track down your dependencies, it's up to you.  You can be as selfish as you want and not give a damn about those wanting an easy install to try out your program, or you can cater to them the best by providing a package that is cross-distro, and just a "Gnu/Linux program", or better yet just a Gnu program, or even better just a Linux Standard program.  Standardization allows that to happen.  Every distro allows you to TAR up files, so why can't RPMs, DEBs, or other formats be just as standard?  IMO, a program package is MUCH more important to have function than the ability to TAR. :P

Take OpenGL for example, again.  You don't have to interface with that API, you can write your own software that interfaces on a lower level, but the API is put there to try to make things easier.  There's no reason APIs can't be written to please pretty much just about everyone.  You can have lots that encompass both high and low levels of programming, and I'd guess that it's possible for them to be cross-programming language as well?

I believe it's one of the most important remaining Unix legacies to be fixed.  Fragmentation is a horrible thing, and an OS that doesn't supply a way for users to get to their apps quickly and efficiently from ANY source is a gimped OS that needs that feature to be added if it ever wishes to see mainstream.

Many of you out there may not care if it does or not.  I don't fall into that category.  I will push until I'm old and gray for a better, easier way to install apps on Linux from any source so that it can become mainstream.  Binary applications from third-parties have to be allowed on Linux if we want to see adoption rates explode.  The faster they explode, the more that benefits everyone which includes all open source projects.  There is no way developers can compile their program for every distro, and they shouldn't need to.

---

### Post by Yfrwlf on 2008-03-30
Again, I'm not the only one.

[http://kerneltrap.org/node/4006](http://kerneltrap.org/node/4006)

---

