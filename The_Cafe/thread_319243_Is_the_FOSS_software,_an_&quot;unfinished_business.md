---
title: "Is the FOSS software, an &quot;unfinished business&quot;?"
date: 2006-12-15
forum: The Cafe
---

### Post by zugu on 2006-12-15
Nowadays, it seems to me as if the FOSS world is more of an unfinished business: the developers write their code, and some other people finish the job in whatever way they see fit (particularly the GNU/Linux distributions).

Most of the projects include prebuilt binaries in the "Downloads" sections of their websites. However, when I can't find one for my distribution, they say that they are building the already available packages out of pleasure, that they are no package maintainers for various distributions, and that they are not even supposed to build packages, but only the source.

I really hate this "build it yourself" attitude. I agree, the closed source world is providing binaries, because they don't want to open up the source, but even if they decide to open up their sources one day, it would be inconvenient.

I am initiating this thread out of frustration towards Debian and Ubuntu and their commitment not to release newer versions of the upstream packages for their "stable" releases, only security updates. Due to some problems, I cannot upgrade to Edgy and I'm stuck with Dapper. However, I thought that this was not a bad thing, until I saw that the edgy-backports repository does not receive software updates, like VLC 0.8.6, Firefox 2 or whatever.

Actually, I'm supposed to wait some time for some people to put up another release of the WHOLE distro, because the whole package ecosystem is FRAGILE and updating GAIM could render my OS useless. Don't get me wrong, I appreciate what these people are doing, but I think the whole approach is wrong.

I agree that the only solution to this would be something like the "each application comes with it's own libraries" approach. But no, many zealots do not agree, because they consider it encourages software bloat and makes security updates harder to implement. Let's say that package A contains all the libraries it needs in order to function regardless of what libraries are installed on the host system or not, including library B. When a security issue is discovered in library B, the "shared libraries" approach makes it easier to fix it: one just updates the specific library, whereas in the other case, each program relying on library B would need to update it. This means more HDD-space being used, and (oh, noes!) more RAM.

But guess what! Nowadays we can have humongous space on our HDDs and outrages amounts of memory for reasonable prices, so here's the fix to the problem. As for the security issue, I think each developer should watch out for vulnerability news and update their implementations of the vulnerable libraries accordingly. Theyr application, their duty.

The problem is that today a distro is not just an operating system, but an operating system plus a plethora of software designed to run specifically on it.

C'mon, people, start designing operating systems and leave the applications developing job to others!

Just my $0.02.

PS: By the way, think of Picasa. It relies on wine, yet it does not need wine to be installed on the system. Because it is bundled with it! And believe me, I had no "bloat" sensations.

---

### Post by Kindred on 2006-12-15
You are calling people zealots because they disagree with how applications should be packaged? Interesting.

I think the shared library approach is technically a better one but is not without its problems.  I'm not sure abandoning it all together is really the solution though.

---

### Post by 23meg on 2006-12-15
These may help you, as well as third party repositories and scripts all over the forums:

[http://www.ubuntuforums.org/showthread.php?t=268687](http://www.ubuntuforums.org/showthread.php?t=268687)
[http://autopackage.org/](http://autopackage.org/)
[http://klik.atekon.de/](http://klik.atekon.de/)

---

### Post by GeneralZod on 2006-12-15
> **Kindred said:**
> You are calling people zealots because they disagree with how applications should be packaged? Interesting.

What's even more interesting is that he brands them "zealots" and then goes on to ascribe to them motivations that are both rational and sensible.

---

### Post by zugu on 2006-12-15
@Kindred and GeneralZod: You should know that there are zealots arguing about anything. And if you find the term offensive, please ignore it and comment on what I had to say, of course, if you have something to say about my rant. Apart from the use of the word "zealots".

Thank you.

@23meg: thank you for the links, they could be helpful, but I did not look for an immediate solution in this thread. I just raised some questions about the logic of software packaging.

---

### Post by prizrak on 2006-12-15
OP,
That's what Windows did and I have not encountered a computer on which XP has been faster than Ubuntu. Moreover my old laptop 64MB Intel card + 512MB RAM worked fine with Beryl+AIGLX giving me the same thing that Vista is promissing. Go look at the requirements for Vista please. Using more RAM and accessing HDD often to load all those libraries is extremely bad for mobile computing as it uses battery power. Just look at Vista battery consumption it lasts about an hour less than XP/Ubuntu (they are pretty close if you don't use nVidia cards).  

If you have a problem with using outdated (OMG 6 months old!!!!) software don't use Ubuntu. There are many distros that will provide you with new software as soon as it is released. Such as Gentoo that will have the most bleeding edge software in Portage. Ubuntu and Debian made a choice and have an intended audience. Debian is an uber stable and secure Linux based OS. It was meant for people who need something basically bullet proof as opposed to recent. Ubuntu is aimed at a home/corporate user that want/needs something that is fairly recent but at the same time stable. With a 6 month release cycle it is never behind by much but is behind. 

Most Linux software comes packaged in some way (did you know you could install RPM's in Ubuntu?) and even if you can't find a package that works for you there is always compiling it yourself or using something like Klik that will basically build a package for you.

---

### Post by MetalMusicAddict on 2006-12-15
> **zugu said:**
> I really hate this "build it yourself" attitude. I agree, the closed source world is providing binaries, because they don't want to open up the source, but even if they decide to open up their sources one day, it would be inconvenient.

I would actually say they make binaries because they only have to make 1. For windows.

---

### Post by zugu on 2006-12-15
@prizrak: the problems you raise could be defeated, given that there are enough people, resources and willingness to start focusing on optimizing the packaging process. It's about rethinking the packaging system.

Yes, I know I can install rpms in Ubuntu, except that I ran into dependency hell with some *alien*ated ones.

As for Debian/Ubuntu and their intended audience, you're right, except that I'm not asking for those specific distros to rethink the design process. I'm sure their intended audience is happy with the thought of having older software. The logical conclusion is that the "new version" announcements for various popular applications are intended to developers and people who are willing to throw their system in a possible non-usable state only. Imagine a new Gnome release announcement, and then Jon Doe trying to replace his old one with it. His OS would be FUBAR.

What we actually need, are people able to see what's wrong with their favorite software, and act accordingly.

---

### Post by 23meg on 2006-12-15
[QUOTE=zugu]
@23meg: thank you for the links, they could be helpful, but I did not look for an immediate solution in this thread. I just raised some questions about the logic of software packaging.[/QUOTE]I'm aware of that; I'll avoid the discussion and just wanted to help somehow.

---

### Post by zugu on 2006-12-15
And yet another example: the VLC people won't do a build of VLC 0.8.6 for Ubuntu Dapper, cause it's not their job to do it. The Ubuntu Dapper people won't do it either, as it might break the system and/or need additional testing for which there is no time/resources.

So no VLC 0.8.6 for me and thousands of other users. The software is there, as bug-free as a stable release can be, thoroughly tested by the developers, working just fine. Yet, the only thing that keeps it from our systems is the packaging process. Isn't this ironic?

---

### Post by doobit on 2006-12-15
edit

---

### Post by Kindred on 2006-12-15
Yeah, there are many other distros that release software on a more frequent basis, if that's a big concern - Arch, Debian Unstable, Gentoo etc.  I do kind of understand where you're coming from and indeed those are my preferred choices, but like was said, Ubuntu has a different audience really.

Aren't there already ways of packaging that use these methods anyway?  if so and they're not widely used I suppose that's demand for you..

---

### Post by ZylGadis on 2006-12-15
I don't really understand your logic.

The people you keep whining against (be it developers or packagers) are not in any way obliged to provide you with anything. They do whatever they do because they like it, not because you like it (sometimes there is a transitive relationship: they do that because they like it, and they like it because users like it, but there is never a direct causal relationship).

The FLOSS ecology is so vibrant and healthy for precisely the same reason: nobody is pressuring you to do what you don't like (i.e. nobody is preventing you from doing whatever you like). So if you think something is wrong, just fix it yourself. It is not difficult, and if you are capable, people will pick your thing. In the end you'll get the warm fuzzy feeling that you did something right and you helped not only yourself, but others, too.

Putting pressure on capable people to obey **your** wishes is not something pertinent in the FLOSS world. In the end, if you are that desperate and incapable, I am sure you can pay someone to do that (whatever it is) for you.

---

### Post by DoctorMO on 2006-12-15
I agree, if you really want packages in ubuntu dapper then you have to be able to commit the time.

[QUOTE=Linux Torvalds]Linux it just works... no wait the other thing, do it yourself.[/QUOTE]

---

### Post by prizrak on 2006-12-15
> **zugu said:**
> @prizrak: the problems you raise could be defeated, given that there are enough people, resources and willingness to start focusing on optimizing the packaging process. It's about rethinking the packaging system.

Yes, I know I can install rpms in Ubuntu, except that I ran into dependency hell with some *alien*ated ones.

As for Debian/Ubuntu and their intended audience, you're right, except that I'm not asking for those specific distros to rethink the design process. I'm sure their intended audience is happy with the thought of having older software. The logical conclusion is that the "new version" announcements for various popular applications are intended to developers and people who are willing to throw their system in a possible non-usable state only. Imagine a new Gnome release announcement, and then Jon Doe trying to replace his old one with it. His OS would be FUBAR.

What we actually need, are people able to see what's wrong with their favorite software, and act accordingly.

1) Can you not find all the dependencies in Synaptic? I tend to find everything that is needed for my 3rd party software. 

2) Google for the debs alot of software has 3rd party packages and repositories. In fact chances are that the newest VLC is in Debian testing/unstable repos that generally will work with Ubuntu. 

3) Joe Doe DOES NOT install newest software, in all probability Joe Doe HAS NO CLUE that there is a new version out.

This debate has been done to death. Simple answer is: If that something that bothers you Ubuntu isn't for you. There is no problem with the way that FOSS is developed and distributed, if there was then Linux would not be running on 25% of world's servers including supercomputers. IBM and Sun would not back it and Apache would not have a a 64% market share in web servers. It all comes to your audience. 

Also look for Linux Standard Base project, it proposes a standard base for all Linux distro's to be built upon as well as a standard packaging system based on RPM.

---

### Post by Brunellus on 2006-12-15
> **prizrak said:**
> 1) Can you not find all the dependencies in Synaptic? I tend to find everything that is needed for my 3rd party software. 

2) Google for the debs alot of software has 3rd party packages and repositories. In fact chances are that the newest VLC is in Debian testing/unstable repos that generally will work with Ubuntu. 

3) Joe Doe DOES NOT install newest software, in all probability Joe Doe HAS NO CLUE that there is a new version out.

This debate has been done to death. Simple answer is: If that something that bothers you Ubuntu isn't for you. There is no problem with the way that FOSS is developed and distributed, if there was then Linux would not be running on 25% of world's servers including supercomputers. IBM and Sun would not back it and Apache would not have a a 64% market share in web servers. It all comes to your audience. 

Also look for Linux Standard Base project, it proposes a standard base for all Linux distro's to be built upon as well as a standard packaging system based on RPM.
it's also worth mentioning that RPMs that are LSB-compliant apparently seem to install just fine using the alien program.

---

### Post by lyceum on 2006-12-15
Nothing is perfect. What you say makes sense. That said, you can't expect everyone to drop everything every time something new comes out. I would say that something new comes out everyday. If you have a better way, the best way to go about making change is not to "rant" but to initiate change. Can you program? If not can you learn or pay someone else to? I would love to see a way to get the latest and greatest on Ubuntu with the click of a button. I have no idea where to begin on making it happen. 

Here are my suggestions:

Get a plan.
Present the plan.
Gain support for the plan.
Go forward with action. 

That is what the Automatix people did, and their stuff is great! Automatix2 works like Add/Remove.

---

### Post by tbroderick on 2006-12-15
> And yet another example: the VLC people won't do a build of VLC 0.8.6 for Ubuntu Dapper, cause it's not their job to do it.

 That's right. They don't have the time/resources to build and test VLC on who knows how many distro's with who knows how many different configurations.

>  The Ubuntu Dapper people won't do it either, as it might break the system and/or need additional testing for which there is no time/resources. 

Correct. It's a trade off between bleeding edge and stable. If your really want the lastest software plus Ubuntu, then I suggest using feisty or whatever the latest testing branch is.

> So no VLC 0.8.6 for me and thousands of other users. The software is there, as bug-free as a stable release can be, thoroughly tested by the developers, working just fine. Yet, the only thing that keeps it from our systems is the packaging process. Isn't this ironic?

Try building it yourself. It's not that hard.

---

### Post by jrjazzman on 2006-12-18
The leading packaging systems for Linux are broken, notwithstanding the interesting justifications in this thread.  

How could maintainers of a free operating system test all the software in the universe on their OS?  They can't, which is why the software available for a given Ubuntu release is frozen at the time of the OS release.  You want a recent version of your favorite app?  Keep re-installing the latest version of Ubuntu.  Unfortunately, much of the software in the repos is outdated by the time the Ubuntu release is final.  And alas, all this version testing and locking doesn't seem to prevent fatal flaws being distributed to tens of thousands of people which result in the linux equivalent of the BSOD.

We need more side-by-side library versions.  Yeah, it'd be nice if you only needed one version for everything, but this is practically impossible, unless you're willing to be locked into versions of applications that meet the lowest common denominator of your library versions.  The insistence on one version of a library is what necessarily dictates application LCDs, and tends to diminish the F in FOSS in a certain regard.

Most users don't want to have to compile and build software just to install it.  Often enough, what one would hope to be a five minute process can turn into a life-robbing multi-hour process.  Massive makefiles that few people understand, hunting for all kinds of libraries in order to link statically... just not a good process for users.  The difficulties that can arise during basic system maintenance is one of the areas in Linux that seems unevolved.  

The dependency features of the packaging systems seems pretty good, but the overly simplistic structure of the libraries themselves is inadequate.  One of my favorite things about Linux is its approachability and simplicity.  But I'd be willing to give up a little bit of this for improved ways of getting certain things done.

Oh, and I know that:
- nothing is perfect
- Ubuntu is free
- If I want <whatever> I should develop/compile/build it myself

---

### Post by argie on 2006-12-19
Compiling isn't as hard as people make it out to be. I just string out my commands with &&'s and go for dinner when I need to compile stuff. But the last time I needed to do that was ages ago.

If you want the latest version, it is *not* hard to compile it yourself. Go ahead and try it.

Also, if you want a binary distribution that offers the most bleeding edge binaries, you must look elsewhere. People like me are content with having a system that does everything they need, and they're more interested in it not breaking than in having <insert awesome new feature>

---

### Post by kripkenstein on 2006-12-19
> **argie said:**
> If you want the latest version, it is *not* hard to compile it yourself. Go ahead and try it.

Additionally, if you have any problems, plenty of people here on the forums will help you out.

---

### Post by prizrak on 2006-12-19
> **jrjazzman said:**
> The leading packaging systems for Linux are broken, notwithstanding the interesting justifications in this thread.  

How could maintainers of a free operating system test all the software in the universe on their OS?  They can't, which is why the software available for a given Ubuntu release is frozen at the time of the OS release.  You want a recent version of your favorite app?  Keep re-installing the latest version of Ubuntu.  Unfortunately, much of the software in the repos is outdated by the time the Ubuntu release is final.  And alas, all this version testing and locking doesn't seem to prevent fatal flaws being distributed to tens of thousands of people which result in the linux equivalent of the BSOD.

We need more side-by-side library versions.  Yeah, it'd be nice if you only needed one version for everything, but this is practically impossible, unless you're willing to be locked into versions of applications that meet the lowest common denominator of your library versions.  The insistence on one version of a library is what necessarily dictates application LCDs, and tends to diminish the F in FOSS in a certain regard.

Most users don't want to have to compile and build software just to install it.  Often enough, what one would hope to be a five minute process can turn into a life-robbing multi-hour process.  Massive makefiles that few people understand, hunting for all kinds of libraries in order to link statically... just not a good process for users.  The difficulties that can arise during basic system maintenance is one of the areas in Linux that seems unevolved.  

The dependency features of the packaging systems seems pretty good, but the overly simplistic structure of the libraries themselves is inadequate.  One of my favorite things about Linux is its approachability and simplicity.  But I'd be willing to give up a little bit of this for improved ways of getting certain things done.

Oh, and I know that:
- nothing is perfect
- Ubuntu is free
- If I want <whatever> I should develop/compile/build it myself

You make an [incorrect] assumption that many people want/know of the bleeding edge features and that they are incapable of compiling something themselves. You are also completely ignoring the multitude of other distributions that provide bleeding edge software or the numerous amounts of software that actually does come in forms of packages for different package systems and in some case distributions. 

Simple fact is that those who tend to care/want the latest and greatest will find a way to get it and comprise a very small (albeit a vocal one) portion of users. It is also a matter of fact that distributions such as Gentoo allow you for the latest and greatest software that will even be built specifically for your system. I would also like to point out that Ubuntu is not that far behind the times at each new version as we get one every 6 months. 

Binary distro's will never be able to have the latest and greatest as quickly as source based distro's can. Simply because the software has to be packaged in a way that will work with a given distribution.

---

### Post by jrjazzman on 2006-12-19
> **prizrak said:**
> You make an [incorrect] assumption that many people want/know of the bleeding edge features and that they are incapable of compiling something themselves. You are also completely ignoring the multitude of other distributions that provide bleeding edge software or the numerous amounts of software that actually does come in forms of packages for different package systems and in some case distributions. 


I think you make some good points.  I really didn't intend to quantify the number or percentage of people who want bleeding edge software.  However, it would be interesting to know, e.g., how many Dapper users wanted FF 2.0 before Edgy came out.  I always ran the latest release version of FF on Windows and didn't really consider myself bleeding edge.  

> 
Binary distro's will never be able to have the latest and greatest as quickly as source based distro's can. Simply because the software has to be packaged in a way that will work with a given distribution.

This is something I still don't understand.  I think it's safe to say that the Windows world is dominated by binary distributions, yet users are generally free to run whatever version of programs they want.  DLL Hell was solved by COM, GAC, etc., allowing for versioned deployment of libraries/components.  Now applications either keep their binaries to themselves, or they provide and request versioned libraries.  Linux has not solved this problem yet.  Thus, users live with locked versions, or go outside the system.

---

