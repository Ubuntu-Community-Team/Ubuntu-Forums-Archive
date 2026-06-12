---
title: "Installing &quot;stuff&quot;"
date: 2007-05-09
forum: The Cafe
---

### Post by clash on 2007-05-09
Apologies if this has being done to death already or in the wrong forum but ...

One of the main issues i heard from john doe and gill bates is that installing software on Linux is a hassle. Que the "This APT has Super Cow Powers" parade and rant on. 

The problem with this:
[INDENT][LIST]
[*]Not all software is in the repository
[*]Software in the apt repos is fairly "release" dependent. i.e > version 1.x of software y is your only option. If you need version 2.x then tough luck.
[*]Installing software thats not in the repos, while usually fairly trivial can still be a pain in the penguin. i.e > software x needs libxyz-1.0 while the software i'm now installing needs libxyz-1.1. So now i need the same library installed twice.
[*]Installing debs isn't usually much better. Dependency hell etc is NOT a thing of the past.
[/LIST]
[/INDENT]

We absolutely *need* to start packaging software the "windows" way. Its not pretty, its not efficient but it works and thats what new users want. 

apt should be just for the kernel, the desktop environment etc and its required libraries, device drivers, some basic small list of applications and so forth. 

We need the "Download one file for application and clickity click next next finish" crap. Yes i'm aware of bitrock installer etc but the problem is they aren't widely used. 

Ok .. time to listen to 100 good reasons why i'm wrong, 10 reasons why i suck and 2 reasons why i'm almost right. 

fire ahead :)

---

### Post by slimdog360 on 2007-05-09
1. your avatar is terrible
2. I dont like your sig

---

### Post by TheTruth34 on 2007-05-09
> **slimdog360 said:**
> 1. your avatar is terrible
2. I dont like your sig
lol

---

### Post by karellen on 2007-05-09
> **slimdog360 said:**
> 1. your avatar is terrible
2. I dont like your sig

double :lolflag:

---

### Post by ssam on 2007-05-09
if someone makes a deb file properly then you can download it and double click it to install.

I have done this before to distribute a simple python program ([Lybniz]("http://lybniz2.sourceforge.net/")). The deb contains a list of dependencies, and if you dont have them they get automatically install from the ubuntu repositories. this worked in a range of ubuntu versions i tested, and should also work on debian. (the package is now in debian and the ubuntu universe)

[Get Deb]("http://www.getdeb.net/") does this with a range of packages.

click and run will be available on ubuntu (and other distros) soon. i am not sure what technology they will be using to deliver packages, but that does not matter for the end user.

---

### Post by clash on 2007-05-09
> **ssam said:**
> if someone makes a deb file properly then you can download it and double click it to install.

I have done this before to distribute a simple python program ([Lybniz]("http://lybniz2.sourceforge.net/")). The deb contains a list of dependencies, and if you dont have them they get automatically install from the ubuntu repositories. this worked in a range of ubuntu versions i tested, and should also work on debian. (the package is now in debian and the ubuntu universe)

[Get Deb]("http://www.getdeb.net/") does this with a range of packages.

click and run will be available on ubuntu (and other distros) soon. i am not sure what technology they will be using to deliver packages, but that does not matter for the end user.

Tóuche

---

### Post by hartz on 2007-05-09
The people who need version 2.0 instead of 1.x which is in the repos will either:
1) Be Linux-literate-enough to install it manually.
2) Be willing to wait a few weeks for 2.0 to come out as a deb

You claim that dependency hell is not over.  Back up that claim with some data.  Even if version 2.0 of special software above needs a special library, then ~100% of the time, the new library version will already be in deb repos with its dependencies linked.

What software (besides the latest unstable versions of packages) is not in the repos?

P.S. You should de-register as a Linux user. <grin>

P.P.S Ditto what the others said. <grin>

---

### Post by forrestcupp on 2007-05-09
> **hartz3 said:**
> 

What software (besides the latest unstable versions of packages) is not in the repos?


I agree with everyone that things are getting pretty easy to install, and CNR should even add to that.  But there *are* many programs that are not in the repos.  One big one is Cinelerra.  It's the only free offering for professional video editing available for Linux.  Why they never added this to the repos is a mystery to me.  People who think everything is in the repos are limited by the scope of their needs and knowledge.  There are lots of things not in there.

---

### Post by prizrak on 2007-05-09
clash,
Ya know homes, in all my years with computers I have yet to see a "normal" user who is even aware that applications come in versions, much less bother with installing newer ones. There is a limited number of power users who care about such things and those can figure out how to install them if they need them that much. Or go with a distro that uses a different release style. To make matters more interesting there are a bunch of 3rd party repositories that you can quite easily add. It's all done in GUI and only needs a copy paste of the URL and in some cases into terminal to grab the GPG key (not even necessary from my experience). This not only ensures that you will have all the necessary dependancies but also that anytime there is update available you will get the latest. 

>         * Not all software is in the repository
What you fail to realize is that anyone new to Linux isn't going to know about that software. Take an average E-mail/web/youtube/IM user from Windows, plop him/her down in front of a Linux system, explain that Firefox == internet, Thunderbird/Evolution == e-mail, Pidgin == IM and I doubt they will say something like "Man I don't want Firefox I want Galeon" they won't ask you why you don't have Emacs installed. In short this world would be 100% new to them and they will use w/e software is installed regardless of how good/bad it is. 

Only the veterans know and have software preferences, those have enough knowledge to get stuff from the outside of repos.

---

### Post by prizrak on 2007-05-09
> **forrestcupp said:**
> I agree with everyone that things are getting pretty easy to install, and CNR should even add to that.  But there *are* many programs that are not in the repos.  One big one is Cinelerra.  It's the only free offering for professional video editing available for Linux.  Why they never added this to the repos is a mystery to me.  People who think everything is in the repos are limited by the scope of their needs and knowledge.  There are lots of things not in there.

Such is human nature. However people who talk about something not being in the repositories are also "limited" by their knowledge and scope of their needs. Cinelerra might be critical to you but really doesn't matter to me. If we are advocating for "average" (wtf is that?) user then Ubuntu and it's repositories provide enough choices.

---

### Post by TheMono on 2007-05-09
Cinelerra is in an awkward phase... Too good to be simple and usable for the home user, too bad to be fully functional and competent for the professional. So I don't mind it not being in the repositories yet.

I ditto what everyone has said defending apt here, especially the reference to getdeb. It is a fantastic resource.

---

### Post by kragen on 2007-05-09
If you want one file which you just click, that means you need to package it up in some way - under windows there is only really one way of doing this - make yourself an installer. Under linux there are loads of different ways however - aside from providing source, you could make an installer, provide a deb, provide a RPM etc... Factor in packaging up these files for different archetectures and it just starts becoming a pain for the developers to maintain, so they just leave it to the distros to package it up, and then it might even get put into an official repository, plus any distro-specific bugs will get fixed.

Besides, windows-style installation doesn't work - the few projects I've found providing a binary installer have generally been the ones giving me the most hassle. Under windows there usually isn't an issue of dependencies - the vast majority of the files needed are provided with windows, and the rest are usually packaged with the product - sometimes as a separate installed (ala direct X). Under linux that's never the case.

---

### Post by Mateo on 2007-05-09
This guy's absolutely 100% correct in everything he says, and it's sick that some of you are bashing him for it.  Take off your fanboy glasses for crying out loud.

---

### Post by Mateo on 2007-05-09
> **ssam said:**
> if someone makes a deb file properly then you can download it and double click it to install.

Making debs is ridiculously difficult.  Try finding a step-by-step guide to making them.  You can't, because you can't do it in steps because it's too difficult.  Every guide I've ever seen tries to explain how they are made up, because instructions won't work due to the complexity of it all.

---

### Post by M7S on 2007-05-09
I would like to see the person who is smart enough to learn how to use Cinerella but not smart enough to learn how to install it.

---

### Post by M7S on 2007-05-09
> **Mateo said:**
> This guy's absolutely 100% correct in everything he says, and it's sick that some of you are bashing him for it.  Take off your fanboy glasses for crying out loud.
Could you, please, point out some programs that are missing in the repositories that new "normal" users might want/need?

---

### Post by ssam on 2007-05-09
> **Mateo said:**
> Making debs is ridiculously difficult.  Try finding a step-by-step guide to making them.  You can't, because you can't do it in steps because it's too difficult.  Every guide I've ever seen tries to explain how they are made up, because instructions won't work due to the complexity of it all.

if you can write software then packaging is not to difficult. its not meant to be easy enough for an end user to do.

the docs on it are a bit of a mess. there are the debian docs [http://www.debian.org/doc/maint-guide/](http://www.debian.org/doc/maint-guide/) the ubuntu wiki has [https://wiki.ubuntu.com/MOTU/Packages/Packaging/Tips](https://wiki.ubuntu.com/MOTU/Packages/Packaging/Tips)

there also have been ubuntu open week sessions on packaging see [https://wiki.ubuntu.com/UbuntuOpenWeek](https://wiki.ubuntu.com/UbuntuOpenWeek)

if you are not able do this you can make requests to the masters of the universe (the people who maintain the universe repo), or the get deb people. getdeb.net is also asking for donations currently. i bet if you offered a donation to fund the packaging of a certain app they would be interested.

---

### Post by Mateo on 2007-05-09
> **ssam said:**
> if you can write software then packaging is not to difficult. its not meant to be easy enough for an end user to do.

the docs on it are a bit of a mess. there are the debian docs [http://www.debian.org/doc/maint-guide/](http://www.debian.org/doc/maint-guide/) the ubuntu wiki has [https://wiki.ubuntu.com/MOTU/Packages/Packaging/Tips](https://wiki.ubuntu.com/MOTU/Packages/Packaging/Tips)

there also have been ubuntu open week sessions on packaging see [https://wiki.ubuntu.com/UbuntuOpenWeek](https://wiki.ubuntu.com/UbuntuOpenWeek)

if you are not able do this you can make requests to the masters of the universe (the people who maintain the universe repo), or the get deb people. getdeb.net is also asking for donations currently. i bet if you offered a donation to fund the packaging of a certain app they would be interested.

i would never support the repo people because they are religious fundamentalists who won't add software to the repos except when there is a new release of ubuntu.

---

### Post by Mateo on 2007-05-09
> **M7S said:**
> Could you, please, point out some programs that are missing in the repositories that new "normal" users might want/need?

I run across software all the time that's not in the repositories.  I mean, just go look at the request list and there are hundreds of software.  If you really need something specific, how about practically every game that exists for linux.  ;)

---

### Post by Mateo on 2007-05-09
> **hartz3 said:**
> 2) Be willing to wait a few weeks for 2.0 to come out as a deb.

That's simply not true.  Only the very most popular pieces of software are added a "few weeks" after release.  Most take **forever**.  Rtorrent in about 4 or 5 versions behind in the repositories, it hasn't been changed since October.  Hellanzb is 3 versions behind and has **major bugs** in the repository version.

---

### Post by H.E. Pennypacker on 2007-05-09
clash and Mateo are right on, but of course, only a few people pay attention to what they're saying.  I wish more people were like clash, Mateo, and I/and me (can't remember which one is proper).  Hmm...maybe in a few years we'll gather enough steam to put out of business all those who want to keep Linux where it is today.

We're a minority today, but hopefully that will change.  

Clash has been rebuked already, and I hope he can put up with it.  At least he knew what he was going to get.  Fortunately, I don't care about being attacked on the Internet. 

Mateo, preach, my friend.  You are right on, and don't let the majority get to you.

---

### Post by H.E. Pennypacker on 2007-05-09
> Making debs is ridiculously difficult. 

Tell me about it.  You know how long it took me to create my first deb?  Several hours.  I guess there's some humor in it, but in the end, it is not funny.  I want to encourage the use of debs, and the deb creation process is enough to deter me from my worthwhile efforts.

The guides are about twenty pages long, and require the use of a billion documents.  You have to open this, and then open that, and you have to do some of the work using the terminal (if I remember correctly - see, you can't even memorize the process, because there are too many steps).

> I run across software all the time that's not in the repositories

You can say that again.  This happens to me all the time.  For example, the repo version of ndiswrapper was  acting up, and apparently there is a bug in it.  Someone told me compile the latest version (available from the ndiswrapper website), and sure enough, he was right.  The latest version solved the bug, it seems, and it was not available in the repos.

> That's simply not true. 

Yup.  Many things are not updated in a few weeks.  It has been a few weeks, and the latest and most stable version of ndiswrapper has not been added to the repos, as an example.  I wonder why, because the latest version is necessary for many of us (probably not all of us).

---

### Post by ssam on 2007-05-09
> **Mateo said:**
> i would never support the repo people because they won't add software to the repos except when there is a new release of ubuntu.

thats part of the ubuntu policy that is inherited from debian. it is not held to religiously, there have been a small number of exceptions. see [https://wiki.ubuntu.com/StableReleaseUpdates](https://wiki.ubuntu.com/StableReleaseUpdates)

there is the backports repository 
[https://help.ubuntu.com/community/UbuntuBackports](https://help.ubuntu.com/community/UbuntuBackports)

you can make your own personal backports quite simply with [prevu]("http://ubuntuforums.org/showthread.php?t=268647")

if you strongly disagree with the stable release policy then ubuntu may not be the distribution for you. maybe you would prefer a dristo that had rolling updates all the time. i know gentoo and debain testing and unstable do this, there are probably more.

---

### Post by prizrak on 2007-05-09
> **H.E. Pennypacker said:**
> clash and Mateo are right on, but of course, only a few people pay attention to what they're saying.  I wish more people were like clash, Mateo, and I/and me (can't remember which one is proper).  Hmm...maybe in a few years we'll gather enough steam to put out of business all those who want to keep Linux where it is today.

We're a minority today, but hopefully that will change.  

Clash has been rebuked already, and I hope he can put up with it.  At least he knew what he was going to get.  Fortunately, I don't care about being attacked on the Internet. 

Mateo, preach, my friend.  You are right on, and don't let the majority get to you.

You seem to equate Ubuntu with Linux which is simply not true. Ubuntu does it this way, Gentoo does it another way. RedHat does it a third way so I really don't see what the problem is.

---

### Post by Lord Illidan on 2007-05-09
What about .autopackage?

---

### Post by pmj on 2007-05-09
> **ssam said:**
> if you strongly disagree with the stable release policy then ubuntu may not be the distribution for you. maybe you would prefer a dristo that had rolling updates all the time. i know gentoo and debain testing and unstable do this, there are probably more.

Why should he look elsewhere? We are comparing Ubuntu to Windows here, and there is to my knowledge no distribution in existence that does what Windows does; namely, to have a stable base (the operating system) with software on top of that of any version you desire. It's MUCH easier to stay up to date with all your favorite applications on Windows than on Linux (no matter the distro), and you don't have to run a beta quality operating system to do it either.

Of course there's no easy answer to how to achieve this, but it is a problem that must be solved. Saying that anyone that wants a specific version of a program will know how to install it on their own is not only shifting the responsibility in an unfair way, it's in most cases false. I doubt 99% of the people on this forum have the skills required to, say, upgrade gstreamer, something that is required if you want to watch certain files with it as a huge bug was fixed only last week. Yeah, have fun waiting 6 months for that one.

---

### Post by forrestcupp on 2007-05-09
> **TheMono said:**
> Cinelerra is in an awkward phase... Too good to be simple and usable for the home user, too bad to be fully functional and competent for the professional. So I don't mind it not being in the repositories yet.

Yeah, and every other video editing option is too pitiful and featureless to use.  So what do I do?  I use Cinelerra.

---

### Post by bonzodog on 2007-05-09
If you want a distro that has a more up to date rolling repo, try Arch Linux.

However, Arch shys away from the GUI method of installing things,as sometimes the latest versions require building manually, so Arch has an automated package builder that runs off the command line.

The simple truth of it is, there is FAR too much software out there for linux to package everything and keep it up to date. All Linux software is released as source then it's up to each individual distro to package and maintain it. 

Clash's idea is closer to the way Mac OSX works - all dependent libs are in the one package. That way, the prog just runs from it's source dir, and installs entirely in one directory alone. In some ways this does make sense, however, Linux cannot use it as Apple have managed to patent the idea.

Even windows has dependency hell - some progs do rely on dll's that are in the root tree, and occasionally, you will find yourself not installing one program but installing two or three, as the dll's are not with the package, and not necessarily installed on the windows system.

The other reason this works so well on mac is because it's just one platform, and most progs go through Apples hands for packaging, so they can make sure all software works out of the box.

Linux however is very spread out, and the nature of open source means that no one program author is going to package it himself. 

Clashes Idea would require that ALL distros started using the same package manager and format, which is never going to happen due to the three core parent distros using very different trees and ways of doing things. 

At the core of this, it comes down to the fact that after the Linux kernel was released, 3 different people came up with different ways to attach to the GNU toolset to it, and thus was born the 3 Core "Parent" distros - they are Debian, Slackware, and Redhat.

The battles of the Slackware and Debian Communities can be traced back to the earliest days of Linux. Redhat Just went and sat in a proverbial corner, didn't get involved and quietly developed their own thing. They developed RPM (Redhat Package Manager), Debian developed the entire idea of using repos using APT with deb files, and Patrick Volkerding at Slackware decided that vanilla unpatched software was the true path, and kept the .tgz format for binary packages as well as source code packages.
 
In My opinion, to sum up, the current repo system is the best we can hope for, but there needs to be a community repo where people who build their own packages can  upload to, and thus provide much more upto date versions of packages when requested. Zenwalk Linux has this system in place, a community repo, which is maintained by a couple of people who test everything before letting it out into the wild.

---

### Post by Mateo on 2007-05-09
Thank you for aknowledging that a problem exists bonzodog, something most of the people here were unwilling to do (because of fanboyism).

 I think getdeb is a good service, but the Ubuntu people should be the people who are sending the packages to them.  If they insist of their fundamentalist approach (which is not user-friendly) with the repos, then they should be putting heavy resources into helping projects like getdeb.

I'd like to see a list of all of the new software added to feisty.  Anyone have a list?

---

### Post by prizrak on 2007-05-09
> **pmj said:**
> Why should he look elsewhere? We are comparing Ubuntu to Windows here, and there is to my knowledge no distribution in existence that does what Windows does; namely, to have a stable base (the operating system) with software on top of that of any version you desire. It's MUCH easier to stay up to date with all your favorite applications on Windows than on Linux (no matter the distro), and you don't have to run a beta quality operating system to do it either.

Of course there's no easy answer to how to achieve this, but it is a problem that must be solved. Saying that anyone that wants a specific version of a program will know how to install it on their own is not only shifting the responsibility in an unfair way, it's in most cases false. I doubt 99% of the people on this forum have the skills required to, say, upgrade gstreamer, something that is required if you want to watch certain files with it as a huge bug was fixed only last week. Yeah, have fun waiting 6 months for that one.
For one the word Linux has been used quite extensively as opposed to Ubuntu. For two rolling up a package is the software distributor's responsibility not distro maintainers'. I have installed NetBeans + JDK pack numerous times and it was always flawless. It would go into the /opt directory with all the stuff it needs. Quite a few projects maintain repositories with their software making it extremely simple to not only install but also keep up with your favorite programs. If whoever made the software doesn't feel like providing a working .deb that is really their problem. Ubuntu is LSB certified it's easy enough to make sure the dependancies are met. 

Since you mentioned Windows. In Windows pretty much all programs come with all of their dependancies save for the most basic ones. This is why the software tends to be much bigger than Linux alternatives. This was in response to .dll hell in 95 and 98. Shared libraries is a much better idea of course but if the ISV wants to make sure their software works they can include all the libraries in the package and have it install them all just for that program's use to not break existing dependancies. 

You are also bitching about it without really doing any research. For one developers aren't here they won't read it. For two the LSB project aims to provide a common base for all Linux distro's to remedy the "problem" you are talking about. In fact the LSB specs even called for an LSB package manager but it never really caught on. 

Whether it's a problem or not is debatable but it is not up to Linux distro's to deal with. I find it interesting that when an installer doesn't work on Windows people complain about the retard who couldn't get the installer correctly but when it comes to Linux it's the end of the world all of a sudden and Linux needs to deal with it ASAP.

---

### Post by prizrak on 2007-05-09
> **bonzodog said:**
> If you want a distro that has a more up to date rolling repo, try Arch Linux.

However, Arch shys away from the GUI method of installing things,as sometimes the latest versions require building manually, so Arch has an automated package builder that runs off the command line.

The simple truth of it is, there is FAR too much software out there for linux to package everything and keep it up to date. All Linux software is released as source then it's up to each individual distro to package and maintain it. 

Clash's idea is closer to the way Mac OSX works - all dependent libs are in the one package. That way, the prog just runs from it's source dir, and installs entirely in one directory alone. In some ways this does make sense, however, Linux cannot use it as Apple have managed to patent the idea.

Even windows has dependency hell - some progs do rely on dll's that are in the root tree, and occasionally, you will find yourself not installing one program but installing two or three, as the dll's are not with the package, and not necessarily installed on the windows system.

The other reason this works so well on mac is because it's just one platform, and most progs go through Apples hands for packaging, so they can make sure all software works out of the box.

Linux however is very spread out, and the nature of open source means that no one program author is going to package it himself. 

Clashes Idea would require that ALL distros started using the same package manager and format, which is never going to happen due to the three core parent distros using very different trees and ways of doing things. 

At the core of this, it comes down to the fact that after the Linux kernel was released, 3 different people came up with different ways to attach to the GNU toolset to it, and thus was born the 3 Core "Parent" distros - they are Debian, Slackware, and Redhat.

The battles of the Slackware and Debian Communities can be traced back to the earliest days of Linux. Redhat Just went and sat in a proverbial corner, didn't get involved and quietly developed their own thing. They developed RPM (Redhat Package Manager), Debian developed the entire idea of using repos using APT with deb files, and Patrick Volkerding at Slackware decided that vanilla unpatched software was the true path, and kept the .tgz format for binary packages as well as source code packages.
 
In My opinion, to sum up, the current repo system is the best we can hope for, but there needs to be a community repo where people who build their own packages can  upload to, and thus provide much more upto date versions of packages when requested. Zenwalk Linux has this system in place, a community repo, which is maintained by a couple of people who test everything before letting it out into the wild.

Isn't that what multi/universe is for?

---

### Post by Adamant1988 on 2007-05-09
I've heard a lot of good things about PC-BSD's .pbi installer format.  But it DOES recreate the errors that Windows has (wasted space, etc.)

---

### Post by prizrak on 2007-05-09
> If they insist of their fundamentalist approach (which is not user-friendly) with the repos,
Interesting how Valve doesn't seem to think so. MS also seems to think that repo approach is pretty good.... The repo approach is a great one, Ubuntu repos just don't happen to have all possible software available. You don't seem to acknowledge the fact that there are many different repo's out there. Alot of projects are going with that approach instead of/in addition to distributing regular packages.

---

### Post by Adamant1988 on 2007-05-09
Repos are a WONDERFUL idea, really.  Having that entire library of software at your fingertips is VERY nice, however, I think Gentoo and Arch have the basic idea right as they seem to have extremely inclusive software repos.  Perhaps something like the AUR for Ubuntu would work?

---

### Post by mech7 on 2007-05-09
> **Adamant1988 said:**
> Repos are a WONDERFUL idea, really.  Having that entire library of software at your fingertips is VERY nice, however, I think Gentoo and Arch have the basic idea right as they seem to have extremely inclusive software repos.  Perhaps something like the AUR for Ubuntu would work?

The idea is nice but the execution not... it is impossible to have all software in it, it is not possible to have the latest software in it :( Good example pidigin everybody wants to install it but it is and won't be in the repository..

---

### Post by Adamant1988 on 2007-05-09
> **mech7 said:**
> The idea is nice but the execution not... it is impossible to have all software in it, it is not possible to have the latest software in it :( Good example pidigin everybody wants to install it but it is and won't be in the repository..

I'm fairly certain that pidgin 2.0 was available in Gentoo's repos the day of release.  Probably the AUR (Arch User Repo) too.

---

### Post by Mateo on 2007-05-09
> **prizrak said:**
> Interesting how Valve doesn't seem to think so. MS also seems to think that repo approach is pretty good.... The repo approach is a great one, Ubuntu repos just don't happen to have all possible software available. You don't seem to acknowledge the fact that there are many different repo's out there. Alot of projects are going with that approach instead of/in addition to distributing regular packages.

Misquoted me.  I didn't say repositories were a bad idea, I said the releasing new software only every 6 months is a bad idea.  **People want new software**.  They want new software much more than they want you to fix the bug where gedit's save button is misspelled on the third wednesday of each month if the tide is up and you're using the liveCD.

---

### Post by ssam on 2007-05-09
> **Mateo said:**
> Thank you for aknowledging that a problem exists bonzodog, something most of the people here were unwilling to do (because of fanboyism).

 I think getdeb is a good service, but the Ubuntu people should be the people who are sending the packages to them.  If they insist of their fundamentalist approach (which is not user-friendly) with the repos, then they should be putting heavy resources into helping projects like getdeb.

I'd like to see a list of all of the new software added to feisty.  Anyone have a list?

i am not sure where there is a list of new packages, but you can look for which packages are in which ubuntu version at packages.ubuntu.com. or if you are nifty on the command line you could get apt to give you a list of all available packages, on a computer running edgy and then feisty and compare them.

ubuntu is run on a finite amount of money by a small group of core developers. it has a governance structure, see [http://www.ubuntu.com/community/processes/governance](http://www.ubuntu.com/community/processes/governance) .

everybody has a different set of things that they think ubuntu needs:
winmodem support
bleeding edge 3d desktops
drivers for their computer
mp3 by default
translations to their language
the latest security features
faster boot
certain games
etc

as mark shuttleworth pays the bills he can guide the priorities (though people are encouraged to join in and do what they want)

if you want there to be more people packaging things for ubuntu, you can help out, pay someone to do it, or try to persuade mark that this is a bigger priority. or you can find a linux distribution that has the same priorities as you (several have been suggested). or use windows if that does everything you need

basically if you want to change ubuntu then change it. if you don't then goes elsewhere. another thread on the forum won't make much difference

---

### Post by Mateo on 2007-05-09
> **ssam said:**
> i am not sure where there is a list of new packages, but you can look for which packages are in which ubuntu version at packages.ubuntu.com. or if you are nifty on the command line you could get apt to give you a list of all available packages, on a computer running edgy and then feisty and compare them.

ubuntu is run on a finite amount of money by a small group of core developers. it has a governance structure, see [http://www.ubuntu.com/community/processes/governance](http://www.ubuntu.com/community/processes/governance) .

everybody has a different set of things that they think ubuntu needs:
winmodem support
bleeding edge 3d desktops
drivers for their computer
mp3 by default
translations to their language
the latest security features
faster boot
certain games
etc

as mark shuttleworth pays the bills he can guide the priorities (though people are encouraged to join in and do what they want)

if you want there to be more people packaging things for ubuntu, you can help out, pay someone to do it, or try to persuade mark that this is a bigger priority. or you can find a linux distribution that has the same priorities as you (several have been suggested). or use windows if that does everything you need

basically if you want to change ubuntu then change it. if you don't then goes elsewhere. another thread on the forum won't make much difference

Please stop telling other (strangers) what to do, it's very rude.

This is what you should be watching out for folks.  A lot of people (affected with fanboyism) get worked up when someone criticizes something they like, and instead of trying to find ways to fix these valid criticisms they instead try to silence the critics.  Ubuntu will not take the next step forward by covering its ears singing "la la la la, la la la la, I can't hear you, la la la la".

---

### Post by Adamant1988 on 2007-05-09
I think the current situation is good, repo-wise.  

The reason Ubuntu's repos are locked down for 6 months is to prevent stability issues, which is understandable.  I'm more inclined to like the PC-BSD style installer, but it DOES create the same issues that Windows has...

---

### Post by karellen on 2007-05-09
> **Mateo said:**
> Please stop telling other (strangers) what to do, it's very rude.

This is what you should be watching out for folks.  A lot of people (affected with fanboyism) get worked up when someone criticizes something they like, and instead of trying to find ways to fix these valid criticisms they instead try to silence the critics.  Ubuntu will not take the next step forward by covering its ears singing "la la la la, la la la la, I can't hear you, la la la la".

how do you find ways to fix the things that you don't like or feel are not right in ubuntu?

---

### Post by pmj on 2007-05-10
> **prizrak said:**
> For one the word Linux has been used quite extensively as opposed to Ubuntu. For two rolling up a package is the software distributor's responsibility not distro maintainers'. I have installed NetBeans + JDK pack numerous times and it was always flawless. It would go into the /opt directory with all the stuff it needs. Quite a few projects maintain repositories with their software making it extremely simple to not only install but also keep up with your favorite programs. If whoever made the software doesn't feel like providing a working .deb that is really their problem. Ubuntu is LSB certified it's easy enough to make sure the dependancies are met. 

Since you mentioned Windows. In Windows pretty much all programs come with all of their dependancies save for the most basic ones. This is why the software tends to be much bigger than Linux alternatives. This was in response to .dll hell in 95 and 98. Shared libraries is a much better idea of course but if the ISV wants to make sure their software works they can include all the libraries in the package and have it install them all just for that program's use to not break existing dependancies. 

You are also bitching about it without really doing any research. For one developers aren't here they won't read it. For two the LSB project aims to provide a common base for all Linux distro's to remedy the "problem" you are talking about. In fact the LSB specs even called for an LSB package manager but it never really caught on. 

Whether it's a problem or not is debatable but it is not up to Linux distro's to deal with. I find it interesting that when an installer doesn't work on Windows people complain about the retard who couldn't get the installer correctly but when it comes to Linux it's the end of the world all of a sudden and Linux needs to deal with it ASAP.

Did you really read my post before you hit the quote button and started ranting back? First of all, while the OP doesn't mention Ubuntu, he does mention repositories and deb files, and he does so on Ubuntu Forums. If you think he was talking about another distro (Slackware perhaps?), please present your argument.

And since I mentioned Windows? The first post mentions Windows! I am aware that programs come bundled with many of their dependencies to avoid the dependency problems we have with Linux. And yes, I think this is a good idea at times. I am perfectly aware of the benefits of our current system, but also of the obvious drawbacks. Like I said, and you ignored, this system makes it a pain for users to install software that isn't in a repository. Even experienced users will have trouble with some softare (did you try upgrading gstreamer yet?), but again, this isn't something we should have to do. This is something that should work. I don't claim to know how to solve this problem, how to keep the best of both worlds, but I do believe that it must happen.

So you find it interesting, based on an assumption, that I haven't done any research, so I would have learned that LSB exists on paper but isn't used and thus isn't doing anything to help here? I find your way of thinking interesting. Also, I'm not trying to talk to any developers here. I'm merely posting on an internet forum, not expecting to be heard by anyone except regular people with too much time on their hands.

---

### Post by macogw on 2007-05-10
> **Mateo said:**
> i would never support the repo people because they are religious fundamentalists who won't add software to the repos except when there is a new release of ubuntu.

Enable the backports repo in Synaptic

---

### Post by prizrak on 2007-05-10
> The idea is nice but the execution not... it is impossible to have all software in it, it is not possible to have the latest software in it  Good example pidigin everybody wants to install it but it is and won't be in the repository..
Reply With Quote
There is a very good reason for it. Pidgin does not introduce anything that is a must have over Beta6.0. 
> Misquoted me. I didn't say repositories were a bad idea, I said the releasing new software only every 6 months is a bad idea. People want new software. They want new software much more than they want you to fix the bug where gedit's save button is misspelled on the third wednesday of each month if the tide is up and you're using the liveCD.
Sorry I misunderstood what you were saying. The thing is that people like YOU want new software, not ALL or even MAJORITY of people want it. I've mentioned this before I know a huge number of people who not only don't care about the latest and greatest but aren't even aware of it comming out. 

Perhaps there is a problem with major bug fixes not getting in. This IS a real problem and something that should be brought up to the developers attention. 

It has been noted before, every distro has it's own way of doing things. Debian comes out with new stuff every couple of years (was it 3 between releases last time?). Ubuntu is every 6 months and Arch and Gentoo have a rolling release style. The reasoning has been explained by Canonical many times and I find it quite reasonable. 

To be honest I see no problem with a 6 month release style, however if you do think it's a problem there is a solution. I suggest you start your own software repository, get people involved, package all the latest and greatest software you can find and put it in there. You can even talk to Canonical and ask them to put your repo as one of the options in the GUI. 
> A lot of people (affected with fanboyism) get worked up when someone criticizes something they like, and instead of trying to find ways to fix these valid criticisms they instead try to silence the critics. Ubuntu will not take the next step forward by covering its ears singing "la la la la, la la la la, I can't hear you, la la la la".
Calling people who don't agree with you fanboys is pretty rude as well as childish. You are of the opinion that there is a problem others are of a differing opinion and have suggest possible ways for you to solve that problem. No one is TELLING you what to do, they are suggestions.
> So you find it interesting, based on an assumption, that I haven't done any research, so I would have learned that LSB exists on paper but isn't used and thus isn't doing anything to help here? I find your way of thinking interesting. Also, I'm not trying to talk to any developers here. I'm merely posting on an internet forum, not expecting to be heard by anyone except regular people with too much time on their hands.
LSB exists on paper rather than in reality because for one the process is pretty slow and for two there isn't enough backing. If you are serious about making things easier get involved with LSB and advocate it, try to convince distros and application developers that they should be using it. The reason things are hard to install is not because Ubuntu (or any Linux) is intentionally making things hard to install. It is up to the application developers to package their software if they do it correctly then it won't be too difficult. 

You've been heard by regular people with too much time on their hands, we have responded, you didn't like the responses. What can I say such is life. If you are looking to make a difference you want to be talking to the devs. If you just wanna shoot the breeze that's fine too, that's why we got the cafe.

---

### Post by karellen on 2007-05-10
it seems to me that prizrak synthetized pretty well what was the discussion all about...
:)

---

### Post by Adamant1988 on 2007-05-10
Does anyone else feel that this argument may not be worth the merit we're giving it?  How long is it before all of our applications are cross-platform 'web apps' the run from the desktop?  I venture to say it won't be long at all before we start seeing web applications taking over... Think of how awesome that's going to be... 

All you'll need installed is the basic dependency of the webapp, maybe silverlight from mono?  Maybe JavaFX (which is very nice) and you can run anything written for those... beautiful thought...

---------------

As for having the latest and greatest, there is a mentality in the world. When a shiny new version of something is finally at a stable release (thunderbird 2.0, etc.) people will want that.  Many times these new versions offer significant features, increased performance, etc.  In the case of pidgin, it's just a more slick UI.  But it is an issue that a lot of people want the latest complete releases of applications, and they want a repo-system that grows and expands.  I know I would love to see a few new games every so often, etc. 

The issue with this of course, is that it doesn't jive well with the stable attitude which is "Don't add anything unless you absolutely HAVE to" and that the repos should not be touched once frozen.  Windows DOES meet this need of users very well though, because Windows releases a platform that only changes every few years.  Applications are then written for that platform, and dependencies included in the package.  The opposite is true for Linux distributions, where the operating system is pulled together for the applications.

---

### Post by hartz on 2007-05-10
> **forrestcupp said:**
> I agree with everyone that things are getting pretty easy to install, and CNR should even add to that.  But there *are* many programs that are not in the repos.  One big one is Cinelerra.  It's the only free offering for professional video editing available for Linux.  Why they never added this to the repos is a mystery to me.  People who think everything is in the repos are limited by the scope of their needs and knowledge.  There are lots of things not in there.

Yes, there are a few thing not in the repo's, but Cinelerra is not one of them.  See [http://cvs.cinelerra.org/getting_cinelerra.php](http://cvs.cinelerra.org/getting_cinelerra.php)

---

### Post by aysiu on 2007-05-10
> **clash said:**
> Apologies if this has being done to death already or in the wrong forum but ... Check out these two threads:
[Unified Package Manager (Autopackage and other ideas)](http://ubuntuforums.org/showthread.php?t=388305&highlight=autopackage)
[ Idea: Standardized Linux Installer](http://ubuntuforums.org/showthread.php?t=412762&highlight=autopackage)

**My personal take on it:**
* It wouldn't be a terrible thing to have .deb files outside the repositories that also included the necessary dependencies--mainly for offline users. It sucks if your Ubuntu computer doesn't have a working internet connection, and you have to download a .deb from another computer, track down all the dependencies, and then bring it over to your Ubuntu computer to install.

* If you can somehow convince all developers of Linux software to make something like a setup.exe for Linux, couldn't you also just convince them to make a .deb? I mean, it requires the same amount of effort, and at least a .deb fits into the scheme of things and can easily be incorporated into the existing repositories. And if you can't convince everybody to do it... well, then, you're stuck in the same situation we're in now--some people have things packaged "properly" for Ubuntu... other people don't.

* What would be a great idea would be a Synaptic Package Manager plugin that allowed you to search pretty much all available Linux software (maybe including whatever's listed on sourceforge.net). If it's not available in the repos, Synaptic lets you know and asks if you want to compile it from source and then compiles it from source for you, automatically downloading and installing all the necessary dependencies. Then, to the end user, it wouldn't matter if something was in the repositories or not.

* I happen to like package management. I'm a simple user with simple needs, and I don't think I'm alone in that. As Ubuntu gets more and more popular, people will package more and more programs for Ubuntu. Even a couple of years ago, most commercial applications had .rpm files only. Now, I'm seeing more and more not only .deb files, but .deb files specifically for Ubuntu. As your userbase grows, your support grows as well.

But there's something comforting for users like me in knowing there's an easy access point for all software, and I don't have to troll around the internet looking for software--it's all in one place. If Ubuntu moved to a more setup.exe model without centralized package management, I'd just move to another Linux distro.

* By the way, to those who want this, you can probably find something out there for you that already exists. I don't know why you're targeting Ubuntu specifically. GoboLinux and Gentoo might be looking into. Or even ReactOS.

---

### Post by super breadfish on 2007-05-10
> **clash said:**
> We absolutely *need* to start packaging software the "windows" way. Its not pretty, its not efficient but it works and thats what new users want. 

No, we absolutely don't. The users you are talking about don't care about doing things the "Windows" way, all they want is to use their computer. All they need is for things to be explained and they'll go on their way.

I don't really understand this attitude. Since having started using Linus I've seen countless people saying "Linux should have exes like Windows", "Linux should drop the CLI" or "XYZ should be more like it is in Windows", but these all seem to come from those who already use Linux. All the new users say is "How do I do this?".
New users don't expect Linux to bend around them, they just want to get going with Linux in the way Linux is.
Many people say that the pen is mightier than the sword, so perhaps the focus should move away from destroying the way Linux is to writing about the way Linux is and giving new users a chance to learn the "Linux" way.

---

### Post by karellen on 2007-05-10
people that say linux should behave like windows (.exe-s, similar default theme, copied features etc) don't want in fact linux. all they want is a free of charge version of windows

---

### Post by wersdaluv on 2007-05-10
> **clash said:**
> We need the "Download one file for application and clickity click next next finish" crap. Yes i'm aware of bitrock installer etc but the problem is they aren't widely used.

I believe that your point really makes sense. They can say that a user can compile and all that, but having all applications available for you to install easily makes sense.

---

### Post by salsafyren on 2007-05-10
I agree with Mateo.

However, people saying that we must make Ubuntu debs are not understanding the issue. You are only thinking of debs for your own distro, why not be all inclusive instead of this Ubuntu only thinking?

Support a project like autopackage or zeroinstall. Zeroinstall is nicer I think, because you can run multiple versions, something which autopackage doesn't support.

To the people saying "You want Linux to be Windows" when people want software that isn't in the repositories: you are basically clueless.

I want two things: repositories and a distro-neutral packages at the same time. Maybe this is unrealistic, but let's then be fair: call it a resource problem, not something else!

---

### Post by clash on 2007-05-10
I think the main problem is that software management on Linux is WAY too complicated. 

How to fix it ...

---

### Post by aysiu on 2007-05-10
> **clash said:**
> I think the main problem is that software management on Linux is WAY too complicated. 

How to fix it ...
Actually, software management in Linux is quite easy. The problem is that not every software developer creates a package for those management systems.

And it's a relatively small problem, as the repos have a plethora of software.

There are some obscure programs that people get upset about, but such is the nature of ex-Windows power users.

---

### Post by salsafyren on 2007-05-10
> **aysiu said:**
> 
There are some obscure programs that people get upset about, but such is the nature of ex-Windows power users.

Yeah, it is NOT only ex-Windows power users who say those things.

Ian Murdock who founded Debian says the same thing.

---

### Post by aysiu on 2007-05-10
I suppose Ian Murdock is just an average user with average computing needs (web browser, email, music, photos, word processing).

---

### Post by prizrak on 2007-05-10
> However, people saying that we must make Ubuntu debs are not understanding the issue. You are only thinking of debs for your own distro, why not be all inclusive instead of this Ubuntu only thinking?

We are Ubuntu users after all, if we were Gentoo users we wouldn't even have that problem. The simple truth is that in any niche there can only be a handful of "leaders". The more Linux develops into a mainstream OS the more you will see that a couple of "main" distros will be used by the vast majority and the rest will only have a modest userbase. Right now on the desktop side of things the main ones are Ubuntu (including Kubunut, Xubuntu and so on), SuSE (open or otherwise), Mandriva (though I think they are dying out) and Fedora. So if you want your software to be on the desktop then you need to keep these in mind. When it comes to FLOSS anyone interested is free to package it, so if it's something worthwile it will be done for other distros. 
> I want two things: repositories and a distro-neutral packages at the same time
There is a distro neutral package, it usually comes with a .tgz extension, we call it source. It's simply impossible to make anything distro neutral without going the Windows/OS X way. You will pretty much have to include all of the dependancies to make sure it all works. This negates many strengths of the OS. If you ever used OpenOffice on Windows you might be aware of the quickstarter. What it does is keep a bunch of OO stuff in the memory so that when you start Writer (or anything else) it only needs to load the specific files to that application. Same idea with Linux and shared libraries. Most of GTK stuff loads up pretty quickly if you are in Gnome, because the libraries are already sitting in memory. It also enables tiny files for applications since they only need to include the actual application code. It's not a perfect approach by any means but that is why something like LSB would be great if it were to take off the ground.

---

### Post by Adamant1988 on 2007-05-10
[quote=adamant1988]1 package == a program.

That is how it SHOULD be, no matter what you're using. These packages should have their dependencies met (or at least the uncommon ones) automatically. Perhaps if there were a way to make a '.deb group package' format and teach the system how to read these. Maybe call it .uai (Ubuntu App Installer ).

If you find a way to download and group all of the dependencies that a file needs, and put them together, and have the package only install dependencies that are needed (because this would go right through package manager anyway) this would give a distinct .exe style effect (one throat to choke for a single program) while maintaining the lean-ness of Ubuntu...

[/quote]

I put this in Aysiu's thread but I think this portion fits here as well.  The basic idea of this is a mini 1-shot repo that is guaranteed to have what you need for an app to run. :)

---

### Post by zugu on 2007-05-10
The current state of Ubuntu made me wipe it out of my HDD and install Windows again. Sadly for me, the only distributions that seem to do the things my way are Gentoo and Arch and they're too difficult and unstable for me to use.

The current software packaging policy is something I *fundamentally* disagree with. The developers view on the issue is obviously the opposite.

There's no point in arguing about it. It's been debated over and over with no results. Only time will tell who's right on this.

LATER EDIT: yes, I know my signature is useless now, I just forgot to change it.

---

### Post by salsafyren on 2007-05-10
> **aysiu said:**
> I suppose Ian Murdock is just an average user with average computing needs (web browser, email, music, photos, word processing).

Is the level of discussion getting this low?

Also, please leave sarcasm / irony of out of your posts. It does not translate nicely to written language.

---

### Post by Adamant1988 on 2007-05-10
> **zugu said:**
> The current state of Ubuntu made me wipe it out of my HDD and install Windows again. Sadly for me, the only distributions that seem to do the things my way are Gentoo and Arch and they're too difficult and unstable for me to use.

The current software packaging policy is something I *fundamentally* disagree with. The developers view on the issue is obviously the opposite.

There's no point in arguing about it. It's been debated over and over with no results. Only time will tell who's right on this.
Or maybe time will produce an alternative.  It's quite possible to think that time is going to make system specific applications useless and irrelevant.  pseudo web-apps are where it's at, Web Apps that live on your desktop.

---

### Post by salsafyren on 2007-05-10
> **Adamant1988 said:**
> Or maybe time will produce an alternative.  It's quite possible to think that time is going to make system specific applications useless and irrelevant.  pseudo web-apps are where it's at, Web Apps that live on your desktop.

Maybe we need some sort of Silverlight / Apollo alternative?

It could be nice to have a 100% open source cross-platform web / desktop framework available. Currently none exists.

---

### Post by zugu on 2007-05-10
If web apps are the answer, then I'm in for a long, long wait.

---

### Post by Adamant1988 on 2007-05-10
> **salsafyren said:**
> Maybe we need some sort of Silverlight / Apollo alternative?

It could be nice to have a 100% open source cross-platform web / desktop framework available. Currently none exists.

What I saw of JavaFX looks like it could very well do that.  I downloaded what appeared to be a single Java file and it ran in it's own window on my desktop.

> **zugu said:**
> If web apps are the answer, then I'm in for a long, long wait.

I think it may very well become that Windows becomes the offline OS, where it's functionality is at it's best when you have no net connection (no viruses, no spyware, you get it) but Linux will be the OS to have if you're online and rolling.

---

### Post by aysiu on 2007-05-10
I'll say it in a straightforward manner then: the creator of Debian is not a normal user with normal computing needs. Better?

---

### Post by salsafyren on 2007-05-10
> **aysiu said:**
> I'll say it in a straightforward manner then: the creator of Debian is not a normal user with normal computing needs. Better?

Much better, aysiu :-)

---

### Post by aysiu on 2007-05-10
Awesome.

Don't get me wrong. I recognize the repositories system has its limitations, especially with the userbase Ubuntu currently has, but it is not as tragic as some people make it sound.

I would love to see a "download and compile other programs outside the repositories" plugin for Synaptic, as I said before. I just think it's more of an "it'd be nice to have" feature than a "we will suffer without it" feature. Actually, it's probably somewhere in between, seeing as how at least a handful of users *are* suffering without it.

---

### Post by salsafyren on 2007-05-10
> **Adamant1988 said:**
> What I saw of JavaFX looks like it could very well do that.  I downloaded what appeared to be a single Java file and it ran in it's own window on my desktop..

JavaFX looks cool and usable. It could help deliver those cross-platform applications that so many have talked about.

---

### Post by prizrak on 2007-05-10
> **aysiu said:**
> Awesome.

Don't get me wrong. I recognize the repositories system has its limitations, especially with the userbase Ubuntu currently has, but it is not as tragic as some people make it sound.

I would love to see a "download and compile other programs outside the repositories" plugin for Synaptic, as I said before. I just think it's more of an "it'd be nice to have" feature than a "we will suffer without it" feature. Actually, it's probably somewhere in between, seeing as how at least a handful of users *are* suffering without it.

I'm not sure if it's possible or at least it's possible that the time/effort spend on it would just not be worth it. It might be the reason behind us never actually getting an easy compile program and instead getting packages. 

Time is another problem, it takes quite a bit of time to compile something compared to a simple install. 

I think there is a good reason behind a basically unanimous decision of the Linux community to come up with some form of a package rather than an automated compiler. Then again for an odd application your way may work pretty well. 

Another thought is that maybe we should have a better communication line with MOTU.

> JavaFX looks cool and usable. It could help deliver those cross-platform applications that so many have talked about.
Well maybe there is your answer, develop everything in Java, no need to install just click the .jar and it runs.

---

### Post by honkytonkwillie on 2007-05-11
> **M7S said:**
> Could you, please, point out some programs that are missing in the repositories that new "normal" users might want/need?

IPodder comes to mind.  Azureus too.

---

### Post by macogw on 2007-05-11
> **prizrak said:**
> I'm not sure if it's possible or at least it's possible that the time/effort spend on it would just not be worth it. It might be the reason behind us never actually getting an easy compile program and instead getting packages. 

Time is another problem, it takes quite a bit of time to compile something compared to a simple install. 

I think there is a good reason behind a basically unanimous decision of the Linux community to come up with some form of a package rather than an automated compiler. Then again for an odd application your way may work pretty well. 

Another thought is that maybe we should have a better communication line with MOTU.


Well maybe there is your answer, develop everything in Java, no need to install just click the .jar and it runs.
Well if it could somehow figure out what checks ./configure ran and get the -dev.debs of those first, then if it installed with Checkinstall, Synaptic would be able to figure out uninstallation

---

### Post by aysiu on 2007-05-11
> **honkytonkwillie said:**
> IPodder comes to mind.  Azureus too.
Azureus is in the repositories:
[http://packages.ubuntu.com/feisty/net/azureus](http://packages.ubuntu.com/feisty/net/azureus)

And I don't think "normal users" use iPodder. From [iPodder.org](http://www.ipodder.org/whatIsIpodder): > First of all, it's still in development, and may not live up to all expectations. But it does work and hundreds of thousands of people are using it every day. If we're optimistic and assume that "hundreds of thousands" means 900,000, that's still only about 0.15% of [the computing population](http://www.intel.com/research/exploratory/papr/extending_the_reach.htm)--hardly an application "normal users" would install.

In any case, a .deb for iPodder can be found [here](http://www.yomix.org/debian/sarge/ipodder_2.1.9-2_all.deb). Just download it to your desktop, double-click it, and let gDebi do the rest.

I still don't see why this is such a big deal.

---

### Post by pmj on 2007-05-11
Compiling software is often only a solution as long as the source code is older than the base system/what's in the official repos. It's *really* difficult to stay up to date with many programs a year after your version of Ubuntu was released because the programs will depend on so much that isn't available in the right versions in the repos, and if you were to try to upgrade them on your own you'd risk breaking all kinds of things. That's just one of the reasons why automatic fetching and compling of random source code is impossible. Random code; that's another.

One problem with deb files is that they're often pretty much tied to your specific version of Ubuntu, again because of dependencies. A Windows developer (yes, we are comparing Linux to Windows in this thread) doesn't have to create a new installer every 6 months. He doesn't have to constantly create new installers for all of the top distros either.

---

### Post by honkytonkwillie on 2007-05-11
> **aysiu said:**
> 
In any case, a .deb for iPodder can be found [here](http://www.yomix.org/debian/sarge/ipodder_2.1.9-2_all.deb). Just download it to your desktop, double-click it, and let gDebi do the rest.

Thanks a bunch.  That worked.  Far too easily, I might add.

---

### Post by zugu on 2007-05-11
> **pmj said:**
> Compiling software is often only a solution as long as the source code is older than the base system/what's in the official repos. It's *really* difficult to stay up to date with many programs a year after your version of Ubuntu was released because the programs will depend on so much that isn't available in the right versions in the repos, and if you were to try to upgrade them on your own you'd risk breaking all kinds of things. That's just one of the reasons why automatic fetching and compling of random source code is impossible. Random code; that's another.

One problem with deb files is that they're often pretty much tied to your specific version of Ubuntu, again because of dependencies. A Windows developer (yes, we are comparing Linux to Windows in this thread) doesn't have to create a new installer every 6 months. He doesn't have to constantly create new installers for all of the top distros either.

I completely agree with you. A deb approach is hardly solving anything. Imagine Ubuntu becomes THE Linux distro, much like Google is THE search engine right now. Imagine that all Linux developers package their software in deb format. In this hypothetical situation, deb + apt-get become the de facto standard. One would expect no more hassles and no more packaging mess. Yet we would still have time based releases, feature freezes and general incompatibility between two versions of the same operating system.

So how is this a solution?

What we really need is an operating system that can easily be used for at least a couple of years and that can provide/support the latest software. New version of Firefox? Just uninstall the old one and install the newer version. Time based releases are very good in an enterprise environment, but a desktop user should be able to install whatever he/she wants.

I hate this software "lock-in". What if Windows wholly embraced this time-based release model, with newer software only available to those who pay for the upgrade?

Fortunately, Ubuntu is *still* free of charge.

---

### Post by Snargledorf on 2007-05-11
Ok in a way you are right...I for one know that when i first started using Linux installing anything that wasn't in synaptic for me was a pain. But at the same time we do have .deb packages which have an installer in Ubuntu. But I do feel that if Linux wants to get more users there should be a standard installer for programs.

---

### Post by prizrak on 2007-05-11
> **honkytonkwillie said:**
> IPodder comes to mind.  Azureus too.

Dunnio about IPodder but Azureus is just SOOOO hard to install.......

---

### Post by prizrak on 2007-05-11
> One problem with deb files is that they're often pretty much tied to your specific version of Ubuntu, again because of dependencies. A Windows developer (yes, we are comparing Linux to Windows in this thread) doesn't have to create a new installer every 6 months. He doesn't have to constantly create new installers for all of the top distros either.
As long as it doesn't require NEWER libraries than what you currently have it won't be a problem. There is no need for repackaging something that was compiled for Edgy for Feisty it will still work on Feisty. So a new package only needs to be created with a new release of the software itself and that's pretty much inevitable. 
> **zugu said:**
> I completely agree with you. A deb approach is hardly solving anything. Imagine Ubuntu becomes THE Linux distro, much like Google is THE search engine right now. Imagine that all Linux developers package their software in deb format. In this hypothetical situation, deb + apt-get become the de facto standard. One would expect no more hassles and no more packaging mess. Yet we would still have time based releases, feature freezes and general incompatibility between two versions of the same operating system.

So how is this a solution?

What we really need is an operating system that can easily be used for at least a couple of years and that can provide/support the latest software. New version of Firefox? Just uninstall the old one and install the newer version. Time based releases are very good in an enterprise environment, but a desktop user should be able to install whatever he/she wants.

I hate this software "lock-in". What if Windows wholly embraced this time-based release model, with newer software only available to those who pay for the upgrade?

Fortunately, Ubuntu is *still* free of charge.
If Ubuntu becomes THE Linux distro then more people will work on it. There will be more people to maintain the repositories that will in turn lead to more software in those repositories. Not to mention that all the devs will be interested in getting their software into those repositories and will work with MOTU to that end.

---

### Post by aysiu on 2007-05-11
> **prizrak said:**
> As long as it doesn't require NEWER libraries than what you currently have it won't be a problem. There is no need for repackaging something that was compiled for Edgy for Feisty it will still work on Feisty. And that's essentially what Opera did. Its Feisty package *is* its Edgy package.

---

### Post by zugu on 2007-05-11
> **prizrak said:**
> If Ubuntu becomes THE Linux distro then more people will work on it. There will be more people to maintain the repositories that will in turn lead to more software in those repositories. Not to mention that all the devs will be interested in getting their software into those repositories and will work with MOTU to that end.

I'm sorry but I really don't know why you bothered to reply to me, since your proved nothing and my criticism is still valid. Lots of software in the repositories does not compensate for the flaws in the time-based release model. The only thing that would help is a change in policy, as to accept newer software and new functionality in the repositories. And such a change is not planned to happen.

---

### Post by prizrak on 2007-05-11
> **zugu said:**
> I'm sorry but I really don't know why you bothered to reply to me, since your proved nothing and my criticism is still valid. Lots of software in the repositories does not compensate for the flaws in the time-based release model. The only thing that would help is a change in policy, as to accept newer software and new functionality in the repositories. And such a change is not planned to happen.

Backports......

---

### Post by zugu on 2007-05-17
You mean the "oh, so empty" backports repositories? The ones with draconian policies? We both know they're hardly a solution to anything.

Please read again the statements I made in this thread before hurrying to reply.

---

### Post by salsafyren on 2007-05-17
> **zugu said:**
> I completely agree with you. A deb approach is hardly solving anything. Imagine Ubuntu becomes THE Linux distro, much like Google is THE search engine right now. Imagine that all Linux developers package their software in deb format. In this hypothetical situation, deb + apt-get become the de facto standard. One would expect no more hassles and no more packaging mess. Yet we would still have time based releases, feature freezes and general incompatibility between two versions of the same operating system.

So how is this a solution?

What we really need is an operating system that can easily be used for at least a couple of years and that can provide/support the latest software. New version of Firefox? Just uninstall the old one and install the newer version. Time based releases are very good in an enterprise environment, but a desktop user should be able to install whatever he/she wants.

I hate this software "lock-in". What if Windows wholly embraced this time-based release model, with newer software only available to those who pay for the upgrade?

Fortunately, Ubuntu is *still* free of charge.

You are absolutely right. Debs are not a solution.

We need a distro-neutral package now, and Ubuntu should push it, not merely import Debian Sid.

Maybe a new "distro" will pop up that will solve our problems and leave Ubuntu in the dust.

---

### Post by pmj on 2007-05-17
> **salsafyren said:**
> You are absolutely right. Debs are not a solution.

We need a distro-neutral package now, and Ubuntu should push it, not merely import Debian Sid.

Maybe a new "distro" will pop up that will solve our problems and leave Ubuntu in the dust.

I hope you're not suggesting we stop using our current repository system? I think both could coexist quite happily, as they solve different "problems". Debs in our repositories makes it easy to install your system and any software you want. If your needs aren't fully met by this, however, there should be an alternative available.

Now that I think about it, are so many people dead against this because they think we want to scrap repositories altogether? You should probably think again; we want more options, not less.

---

### Post by salsafyren on 2007-05-17
> **pmj said:**
> I hope you're not suggesting we stop using our current repository system? I think both could coexist quite happily, as they solve different "problems". Debs in our repositories makes it easy to install your system and any software you want. If your needs aren't fully met by this, however, there should be an alternative available.

Now that I think about it, are so many people dead against this because they think we want to scrap repositories altogether? You should probably think again; we want more options, not less.

I want both: repositories and a distro-neutral package format that all the distros agree on.

If people assume that if you are for distro-neutral packages and thus against repositories, that's their assumption.

---

### Post by compwiz18 on 2007-05-17
I think that there should be a common index file in source archives that defines the dependencies and the steps required to compile and install said source.  Because I know that the Linux community will never pick just one type of package, be it deb, rpm, or something else, the least that could be done is to make it simpler.  You download a source archive (maybe will a special extension?), double click it, and your choice of package manager kicks in, reads the index file, resolves the dependencies, compiles and installs the program.

Linux is all about choice.  Windows not so much.

That's why it is hard to install software that isn't in the repositories on Linux - because there are too many ways to do one thing.  Generally, the less choice people have, the better they do (see [http://video.google.com/videoplay?docid=6127548813950043200](http://video.google.com/videoplay?docid=6127548813950043200) - very interesting documentary on this subject)

And at the beginning of this thread, whoever said that the docs on how to create debs are pretty bad, +1 for them - it took me longer to make the deb then it did to learn Python.

---

### Post by zugu on 2007-05-17
Actually we can have both distro neutral packages and repositories if we discard the current definition of the word "repository" and replace it with one that encompasses the whole Linux software ecosystem.

By analogy, all software ever written for Windows IS a giant, decentralized repository.

---

### Post by prizrak on 2007-05-17
> **zugu said:**
> You mean the "oh, so empty" backports repositories? The ones with draconian policies? We both know they're hardly a solution to anything.

Please read again the statements I made in this thread before hurrying to reply.

There is a simple solution for this:
Rather than argue with me, I don't really care about your perceived problem as I have no trouble installing 3rd party software, I suggest that you get a group of like minded people and organize a repository of your own. You can put all the stuff you want in there and update it as often as you'd like. If you talk to Canonical you might even get your repository into the default sources.list. Well perhaps it would need to be enabled in software sources with a little warning but hey it's a solution.

---

### Post by zugu on 2007-05-17
> **prizrak said:**
> There is a simple solution for this:
Rather than argue with me, I don't really care about your perceived problem as I have no trouble installing 3rd party software, I suggest that you get a group of like minded people and organize a repository of your own. You can put all the stuff you want in there and update it as often as you'd like. If you talk to Canonical you might even get your repository into the default sources.list. Well perhaps it would need to be enabled in software sources with a little warning but hey it's a solution.

I am not arguing with anyone, I am just trying to make a point. I do not understand your defensive stance, since I just asked you to read my posts more carefully, nothing more. I can assure you that 'my' problem is very, very real; if you don't have it, it doesn't mean others don't, or that it doesn't exist.

Please, do not provide me with the standard, "if-you-don't-like-it-modify-yourself" rebuttal. It's been done before. Not everyone is a programmer / developer / package maintainer. Since Ubuntu is marketed as an easy to use Linux "for human beings", it's ridiculous to ask plain users to create debs, maintain repositories and such.

So I ask you again to participate in a constructive manner to the discussion and stop providing stock reasonings and recommendations. If nothing in this thread applies to you, you could as well restrain from posting. Thank you.

---

### Post by forrestcupp on 2007-05-17
> **prizrak said:**
> There is a simple solution for this:
I suggest that you get a group of like minded people and organize a repository of your own. You can put all the stuff you want in there and update it as often as you'd like. 

We don't want *more* work, we want less.  What is wrong with the idea of having a distro-neutral packaging system?  Each project team can compile and package their own project into this system.  Then any Linux user could install from it.  This way you don't have one person trying to package thousands of apps, each one will be packaged by its own developers.

> **salsafyren said:**
> We need a distro-neutral package now, and Ubuntu should push it, not merely import Debian Sid.

Maybe a new "distro" will pop up that will solve our problems and leave Ubuntu in the dust.

Linspire to the rescue with Click-n-Run.

---

### Post by prizrak on 2007-05-17
> **zugu said:**
> I am not arguing with anyone, I am just trying to make a point. I do not understand your defensive stance, since I just asked you to read my posts more carefully, nothing more. I can assure you that 'my' problem is very, very real; if you don't have it, it doesn't mean others don't, or that it doesn't exist.

Please, do not provide me with the standard, "if-you-don't-like-it-modify-yourself" rebuttal. It's been done before. Not everyone is a programmer / developer / package maintainer. Since Ubuntu is marketed as an easy to use Linux "for human beings", it's ridiculous to ask plain users to create debs, maintain repositories and such.

So I ask you again to participate in a constructive manner to the discussion and stop providing stock reasonings and recommendations. If nothing in this thread applies to you, you could as well restrain from posting. Thank you.

1) It is Ubuntu policy to not provide anything other than security updates for stable releases. This isn't something that is unlikely to ever change.

2) Ubuntu developers/package maintainers don't have unlimited time and resources to include every single piece of software out there. Remember that all of the software in repositories has to be tested at least as far as it satisfying dependancies. Even then new software gets added and there is a very impressive selection. 

3) You don't have to be a programmer/developer/package maintainer to make a difference. Since as you say it's a problem for alot of people, it is possible to get all those people together and pay those with necessary knowledge to create and maintain such a repository. There are also plenty of people who would volunteer their skills if they felt the cause was good. 

> We don't want more work, we want less. What is wrong with the idea of having a distro-neutral packaging system? Each project team can compile and package their own project into this system. Then any Linux user could install from it. This way you don't have one person trying to package thousands of apps, each one will be packaged by its own developers.

Nothing is wrong with the IDEA of a universal package. There are some things wrong with the implementation. There isn't even a need to create a new packaging system as long as all distro's adopt it as the standard any of the current packaging methods can be used. However it wouldn't have the effect you are hoping it would. Packages are compiled against a certain set of libraries. So a Feisty package cannot possibly work on Edgy or Dapper. Moreover a Debian Sid package is unlikely to work on Ubuntu at all. Now take into account other popular distros such as RedHat or SuSE. They don't just have different libraries but also different kernels. So even with that one universal package you are going to have to create a bunch of different packages in order for them to work in different versions/distros. Is it really all that different from making a .deb for Feisty and an .rpm for RedHat?

---

### Post by forrestcupp on 2007-05-17
> **prizrak said:**
> 
Nothing is wrong with the IDEA of a universal package. There are some things wrong with the implementation. There isn't even a need to create a new packaging system as long as all distro's adopt it as the standard any of the current packaging methods can be used. However it wouldn't have the effect you are hoping it would. Packages are compiled against a certain set of libraries. So a Feisty package cannot possibly work on Edgy or Dapper. Moreover a Debian Sid package is unlikely to work on Ubuntu at all. Now take into account other popular distros such as RedHat or SuSE. They don't just have different libraries but also different kernels. So even with that one universal package you are going to have to create a bunch of different packages in order for them to work in different versions/distros. Is it really all that different from making a .deb for Feisty and an .rpm for RedHat?

Good points.  I guess the closest thing we have that would work is Portage because it just compiles everything for you.  Too bad it's sooo slow.

But there has to be an easier way for some things.  Like, for instance, the game Sauerbraten.  You download a tar.gz file.  Untar it to a directory.  It already has all of the binaries and content, and you just run the game, no matter what distro you're using.  Or .run files.  Have you seen those?  You just run them, and they install something no matter what the distro.

---

### Post by aysiu on 2007-05-17
There are a bunch of precompiled binaries (Firefox, Thunderbird, Google Earth, Songbird, FirstClass Client, etc.) out there. I don't really like them, mainly because they come as .tar.gz files, and they usually confuse new users, who wonder where to install them to.

As Ubuntu becomes more and more popular (it's looking to be *the* home user distro if things keep going the way they are... don't know about corporate or server, though), more and more software packaging will be in a Ubuntu-compatible .deb format, which would be easier for new users--download the .deb files, double-click it, and then let gDebi install it for you.

And, as more and mroe software developers package Ubuntu-compatible .deb files, it'll be easier and easier to fill the Multiverse repositories with popular non-free software.

---

### Post by prizrak on 2007-05-17
> **forrestcupp said:**
> Good points.  I guess the closest thing we have that would work is Portage because it just compiles everything for you.  Too bad it's sooo slow.

But there has to be an easier way for some things.  Like, for instance, the game Sauerbraten.  You download a tar.gz file.  Untar it to a directory.  It already has all of the binaries and content, and you just run the game, no matter what distro you're using.  Or .run files.  Have you seen those?  You just run them, and they install something no matter what the distro.

This is basically OS X/Windows approach and does work for certain things but not others. For instance a Gnome application is generally going to depend on Gnome libs, those libs in turn depend on other libs and so on and so forth. Some of the smaller stuff can be installed this way. Some of the stuff that uses unique libraries and simply talks to the systems on some level can work like that but there is plenty of stuff out there that would pretty much have to come as it's own distro. 

Portage is simultaneously the best and the worst possible way of installing software. It's great because it will compile everything for your system and will pull whatever new stuff is necessary. It sux horribly specifically because it compiles EVERYTHING and pulls down all the new stuff. It may (and in many cases does) lead to some serious system instability. Obviously when it comes to GUI environments it takes way too long to really be useful unless you have more than one system or are going away for the weekend ;) 

I really do think that community supported repositories would be the best way to handle software in Ubuntu as they can provide things that official repositories either can't or won't for one reason or another.

---

