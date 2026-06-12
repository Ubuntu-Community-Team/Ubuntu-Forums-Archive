---
title: "if all distros are based on one kernel...."
date: 2009-04-07
forum: The Cafe
---

### Post by pbpersson on 2009-04-07
If all distros are based on one kernel....

If all distros use the same KDE and Gnome.....

If all distros use the same version of Konqueror, Gedit, Dolphin, Nautilus, etc......

Then how can they be so different?

Also, let us say that Fedora is better with some hardware and Mandrake is better with others....and only Ubuntu can recognize some sound cards....how can that be?

Aren't they all supposed to be using and sharing the same GPL code?

I have seen many times in this forum where people say "no distro recognized my hardware until I tried xyz distro" and I am trying to understand this.

---

### Post by MilesRdz on 2009-04-07
They are all configured differently. 
Some have more device drivers than others.
Some have a modified versions of KDE/Gnome.
It's all about which configuration is right for you.

---

### Post by FuturePilot on 2009-04-07
Most distros (except for a few) apply their own distro specific patches to things. This could be related to distro A not working with some piece of hardware but Distro B works. Also, not ever distro uses the exact same kernel version.

---

### Post by pbpersson on 2009-04-07
But if distro A does sound cards better and distro B does WIFI better and all this stuff is FOSS, would they not incorporate the best features of each distro into each one and have two distros that are better than either one?

Does that make sense?

---

### Post by MilesRdz on 2009-04-07
Perhaps that would be easier if the developers got out of that 699 Mb budget mentality.

---

### Post by Dekkon on 2009-04-07
> **pbpersson said:**
> But if distro A does sound cards better and distro B does WIFI better and all this stuff is FOSS, would they not incorporate the best features of each distro into each one and have two distros that are better than either one?

Does that make sense?

Too bad the whole FOSS community is ignorant and doesn't want to work towards a few good options instead upon the load of unneeded choices we have today.

---

### Post by dspari1 on 2009-04-07
> **MilesRdz said:**
> Perhaps that would be easier if the developers got out of that 699 Mb budget mentality.

I disagree, that 699 Mb budget mentality is what saves us all from 100 different text editors, 20 image viewers, 5 media players, 2 office suite and useless mini games like solitaire hogging up the system. I wouldn't mind DVDs if the distros would be mindful that redundancy isn't always a good thing.

---

### Post by simtaalo on 2009-04-07
> **pbpersson said:**
> But if distro A does sound cards better and distro B does WIFI better and all this stuff is FOSS, would they not incorporate the best features of each distro into each one and have two distros that are better than either one?

Does that make sense?

because sometimes the devs of certain distro's don't send the extra device driver/whatever upstream to the kernel.

---

### Post by Barrucadu on 2009-04-07
Not all distros use KDE or GNOME, many don't.

---

### Post by samjh on 2009-04-07
> **pbpersson said:**
> But if distro A does sound cards better and distro B does WIFI better and all this stuff is FOSS, would they not incorporate the best features of each distro into each one and have two distros that are better than either one?

Does that make sense?

Yes it does, but the real-world isn't so ideal. :)

Some hardware have proprietary drivers which some distros will not include by default.  Some distros use specific flags during compilation of the kernel, or exclude some kernel modules because they cause problems or are inconsistent with the goal of the distro.

An operating system kernel is very complex.  There are many many modules, configuration options, etc.  Some don't really play well with each other.  Distros have target classes of users who are better served with some configuration options and modules than others.  It all makes each distro somewhat different from each other.  Being FOSS doesn't really solve those differences.  Being FOSS can help reduce bugs, incompatibilities, and add more options to serve specific needs, but there will always be differences, problems, and so on.

---

### Post by macogw on 2009-04-07
> **pbpersson said:**
> But if distro A does sound cards better and distro B does WIFI better and all this stuff is FOSS, would they not incorporate the best features of each distro into each one and have two distros that are better than either one?

Does that make sense?

Because it takes a lot of effort to hunt around and find and test all the patches all the others are using.  Wanna go to all the other distros and ask for copies of all their patches and what do the patches do and then test them all and then give them to Ubuntu's kernel lead and then try to convince him they won't hurt anything or conflict with each other?  And then they have to actually be integrated...  That's why patches need to be sent upstream, to Linus.  Only then do all the distros get the patches.
> **Dekkon said:**
> Too bad the whole FOSS community is ignorant and doesn't want to work towards a few good options instead upon the load of unneeded choices we have today.
Too bad the hardware manufacturers are ignorant and don't want to work toward a few high-quality models that conform to their specifications instead of creating hundreds of variations on each model number that are implemented slightly differently and thus break drivers in many different ways.

---

### Post by mips on 2009-04-07
> **pbpersson said:**
> If all distros are based on one kernel

If all distros use the same 

If all distros use the same version



You see, now that is where you are wrong. 
They don't all use the same kernel.
They don't all use the same Gnome, KDE etc
They don't all use the same version of applications.

Then there are people that apply patches to their distros.

You cannot really compare say Fedora to Ubuntu. Fedora has newer versions of most things compared to Ubuntu.

---

### Post by SnappyU on 2009-04-07
I must say I was having the same wonderment as well.  Can't we pool our resources together instead of having numerous distros doing similar things.

The numerous distros forked for various reasons, some because the key dev just couldn't party together, and sometimes due to a philo diff.

IMO, Ubuntu has so far done a good part of what you mentioned, ie piece together as much as possible the good work done by various groups and presenting a OOTB solution for end users.  It is based on Debian, supports Gnome, KDE and XFCE, like some other distros, and comes with a good starter meal of apps for most (say 80%) of new users to begin with.

Distros are to me like real estate developers.  They all use cement, iron beams, wood, glass, etc etc.  But the way they piece everything together is a bit diff.  The ease or sophistication of installation differs to suit diff users.  The built-in apps are diff as mentioned (kind like how diff condos offer diff kind of furnishing etc).

Ubuntu also support proprietary drivers while some refuses totally.  I see it as philo-hair-splitting, but some see it as pertinent to their cause; I really just want an OS that works, OSS, proprietary or otherwise.

A touchy area is the dev's sensitivity or openness to merging with other devs.  While OSS is about freedom, the individual dev's ego does get in the way at times.  I don't blame them for it, 'cos as a dev myself, I see why they feel so strongly abt their own code.  But at times, I just can't see how they can put their code ego above the overall benefit of the community.  I thought that was the pt of OSS?

To be fair, OSS is really great and I've benefitted tremendously from it.  The one gripe I have besides the one you mentioned is how OSS projects always seem to break things just when it seemed to be working.  It's like the dev guys are playing lego here and can never stay still or be content with the supercool megatron lego toy they built.  The good thing about OSS is that you can then fork so that you have a distro that is as stable as you like without joining in for the bumpy ride.  With your own distro, you can then choose when to incorporate new features or support for hw.  Ah, and that's why we have all these forking and distros because that way everyone get their flavor of ice-cream. :)

---

### Post by mips on 2009-04-07
> **SnappyU said:**
> Can't we pool our resources together instead of having numerous distros doing similar things.


NO!

I prefer choice. You would like to use Ubuntu and so would many other people. I on the other hand am not the biggest Ubuntu fan and prefer to use something else. I do not want to be restricted by the choice of the masses.

What works for some people does not work for others, thus we have choices and I would like to keep it that way.

---

### Post by m0ntels on 2009-04-07
If you give 100 different artists the same set of paints, brushes, and canvas, and tell them all to paint a pictures of a cat, they will all paint a cat using the same materials, but how many do you think would look the same if they were all working independently of each other?  They all end up with cat paintings, but none are exactly the same.  Some could be cubist, some impressionist, some pointillist, some realistic....but they are all cat paintings.  

Afterward, you could let them see each others paintings and let them paint a second cat painting.  Now they will have ideas that they like from others' paintings and can incorporate them if they choose.  But not everyone will like all other painters' ideas.

I used to not understand why all distros were so different until I spent some time with a few different ones with different roots.  I used Mint, Fedora, Mandriva, and Zenwalk for example.  Each starts with relatively the same set of building blocks, but they all arrange and use them differently.  Some choose not to use some parts at all.  They all work as Linux distros, but differently.

---

### Post by pbpersson on 2009-04-07
> **m0ntels said:**
>   I used Mint, Fedora, Mandriva, and Zenwalk for example.  Each starts with relatively the same set of building blocks, but they all arrange and use them differently.  Some choose not to use some parts at all.  They all work as Linux distros, but differently.

This is true and I can understand the concept of artistic differences.

However, as a user if I try four different distros and three do not recognize my hardware then those distros are FAILURES and WORTHLESS to me.

Also, as Joe Six Pack if I venture into LinuxLand, try two distros and neither one works I would conclude that Linux as a whole is just a joke.

I am not saying that this is good or bad, it is just a comment.

EVERYONE should send their kernel changes upstream to Linus, that is the best way to make Linux the best OS on the planet.  Shame on anyone who does not.  :(

---

### Post by mips on 2009-04-07
> **pbpersson said:**
> 
EVERYONE should send their kernel changes upstream to Linus, that is the best way to make Linux the best OS on the planet.  Shame on anyone who does not.  :(

That does not mean your changes will be incorporated into mainline...

---

### Post by simtaalo on 2009-04-07
> **mips said:**
> That does not mean your changes will be incorporated into mainline...

but if its a device driver its 99% likely to make it in.

---

### Post by m0ntels on 2009-04-07
But what if Linus does make the only distro and that makes me not like Linux anymore?  

Get away from calling everything Linux and you'll be better off understanding why there are so many.  It's like the art analogy again...I wouldn't say I don't like art after looking at only one or 2 artists' work.  Dismissing everything else based on one or 2 experiences isn't the way to do things.

If you or your hardware don't like Fedora, then don't use it.  If you don't like CentOS, don't use it. If you are simply in love with Debian, then use that.  But don't forget, Debian might not do what someone else wants, so while you love it, they think it's garbage.  For example, hibernate worked for me in Mint, but not Ubunutu.  They are 2 near identical distros, but one simple change made a world of difference.

If everyone consolidated into one distro, eventually someone else would say this stinks and make something else and we'd be back where we are now.

---

### Post by 23meg on 2009-04-07
[http://ubuntuforums.org/showthread.php?t=170434](http://ubuntuforums.org/showthread.php?t=170434)

---

### Post by SomeGuyDude on 2009-04-07
> **MilesRdz said:**
> Perhaps that would be easier if the developers got out of that 699 Mb budget mentality.

My system came from a 100MB installation CD and had no problem detecting all of my hardware. It ain't a size issue.

---

### Post by Therion on 2009-04-07
Linux itself is like a huuuge box of Lego bricks that anyone is free to use.

Individual distros are like Lego "kits" you buy to build, for instance, a spaceship or a train station.

No single "kit" will make everyone happy or fulfill every need.

---

### Post by chris200x9 on 2009-04-07
> **Therion said:**
> Linux itself is like a huuuge box of Lego bricks that anyone is free to use.

Individual distros are like Lego "kits" you buy to build, for instance, a spaceship or a train station.

No single "kit" will make everyone happy or fulfill every need.

well said

---

### Post by MaxIBoy on 2009-04-07
> **pbpersson said:**
> But if distro A does sound cards better and distro B does WIFI better and all this stuff is FOSS, would they not incorporate the best features of each distro into each one and have two distros that are better than either one?

Does that make sense?2/3 of all  the drivers you probably use are **not** FOSS. They are binary blobs compiled into the kernel or as kernel modules, released as-is from hardware companies without any source. We are gradually working toward the goal of fully-FOSS drivers, but in the meantime, some distros will stay away from the binary blobs, and some distros won't.

---

### Post by TwiceOver on 2009-04-07
My question is: Since U/K/X Ubuntu are all the same besides DE, why does my sound not work in X and hotkeys not work in K?

Still happy with good old U though.

---

### Post by init1 on 2009-04-07
> **MilesRdz said:**
> Perhaps that would be easier if the developers got out of that 699 Mb budget mentality.
699MB should be plenty. The Ubuntu CD has way more than it needs. I wouldn't mind if they removed Gnome games to make room for drivers.

---

### Post by Mehall on 2009-04-07
> **init1 said:**
> 699MB should be plenty. The Ubuntu CD has way more than it needs. I wouldn't mind if they removed Gnome games to make room for drivers.

Put it this way, Tiny Core is 10MB and has the entire kernel in it.

It will probably manage to stay under 20MB easily, and maybe under 10MB, even with new kernels with better still hardware support.

it is NOT drivers that take the space.

---

### Post by 23meg on 2009-04-07
> **MaxIBoy said:**
> 2/3 of all  the drivers you probably use are **not** FOSS.

That's an overestimation. Even a very unlucky configuration in terms of support is unlikely to need more than three or four proprietary drivers, the most likely candidates being networking and display drivers.

[QUOTE=TwiceOver]My question is: Since U/K/X Ubuntu are all the same besides DE, why does my sound not work in X and hotkeys not work in K?[/QUOTE]

Because the kernel is only one part of making hardware work, albeit the most essential one. Some distributions can lack or misconfigure the userspace tools that are needed to make your hardware that's otherwise supported by the kernel work the way it's supposed to work.

---

### Post by mamamia88 on 2009-04-07
probably the same reason it's harder to crack passwords containing numbers, letters, and symbols, as well as lowercase, and upercase numbers you can combine them in almost infinite ways and not get 2 exactly the same

---

### Post by pbpersson on 2009-04-09
I have read this thread and the connected thread and this is what I am hearing:

1.Each distribution is different
2.Each one has unique components
3.Each one is a work of art

Okay, but does it need to be that way and is that a good idea?

One hundred years ago, cars were made the same way.  Each car was unique and parts could not be exchanged between cars.  This made them very difficult to work on and very costly to repair.  At some point the competing manufacturers standardized.  This way a headlight, spark plug, or radio built for one car would work in all cars.  This was a win-win scenario for the manufactures and the customers.  Can we be as smart as the car companies?

Each distribution can still be different.  It can have its own distinctive look and feel and even unique applications that make it special.  What I am suggesting is standardized layers for basic functions.  The TCP/IP stack is a perfect example of this.  It has defined layers and precisely defined interfaces which allow those layers to interact.  This means that if you plug in a new network card, you just insert a new physical layer into the TCP/IP stack and your network interface still functions.  This is the entire reason why it is so easy to install a new network card in a PC.

In this discussion we have talked about the kernel from Linus.  Then people said another layer was hardware detection – hooking the hardware to the device drivers.  Then we have the XORG/ALSA/Pulseaudio layers and the package management layers.

Wouldn't it be great if a distribution maker could start with the Linus kernel, add the Feodora hardware detection layer, use the SUSE audio/video layer, and the Ubuntu package management layer, picking a layer from each company based on how they want their distribution to function?

By using an approach such as this, the various developers working with the various distributions would be able to POOL their resources instead of producing unique creations which cannot share parts.  Also, once they had the foundation – all devices recognized and working – they could concentrate on making the graphical interface their own unique work of art.

Are we working on a painting, a sculpture, or an operating system that NEEDS to perform certain tasks?  I don't know about anyone else, but when I try a live CD I check three things – network, sound, and video.  If those don't work, regardless of how artistic the distro appears, I fling the CD into the trash because:

1.Life is too short to spend days tinkering in an attempt to fix what should not have been broken in the first place

2.If they cannot get the BASICS right, what other larger problems are hiding beneath the surface, just waiting to jump out and surprise me?

The open source community is about working together as a global force to share our knowledge and work toward a common goal rather than competing.  Can we follow this belief to its ultimate conclusion and work together to build the best OS the world has ever seen?  If we pooled the resources of all the FOSS developers in the world in one unified project, we would literally leave Windows behind in our dust.  Do you think we are up to the challenge?

---

### Post by samjh on 2009-04-09
> **pbpersson said:**
> The open source community is about working together as a global force to share our knowledge and work toward a common goal rather than competing.No it's not.  Open source is about transparency and freedom to use, modify, and distribute software.

The "working together" thing is an unrelated concoction.

> Can we follow this belief to its ultimate conclusion and work together to build the best OS the world has ever seen?  If we pooled the resources of all the FOSS developers in the world in one unified project, we would literally leave Windows behind in our dust.  Do you think we are up to the challenge?Not really, because too much cooperation stunts competition.  Competition breeds innovation and accelerated growth.

What is needed is a balance between cooperation and competition, which is what we reasonably have at the moment.

We have very many distros, most of which are based on one of several key distributions like Debian, Fedora, Gentoo, Slackware, etc.  The developers of derivative distributions are able to assist the developers of parent distribution by contributing bug fixes, enhancements, etc.  Maintainers of distributions assist upstream developers (ie. the actual developers of FOS software) by providing patches upstream.  Organisations like the Linux Standards Base  establish standards for desktop usability, configuration management, and device drivers.

There is quite a lot of competition, but also a healthy amount of cooperation.

A major problem with over-standardisation is that it limits innovation by discouraging the use of NON-standard technology.  Standards are inherently static, and relatively slow to change in comparison with new technological developments.  If the FOSS community were to stick only to established standards, then there will be little or no opportunity for distros to experiment with multiple technologies to accomplish the same goal, and determine by strong competition, the best technology for that goal.  If you want Linux to develop quickly and improve as fast as it can, then you need to foster innovation.  Unfortunately, fostering innovation means you need to tolerate variety and non-compliance with standards.

What you suggest might sound nice on the surface, but it's a medicine worse than the disease.

---

### Post by Barrucadu on 2009-04-09
> **pbpersson said:**
> The open source community is about working together as a global force to share our knowledge and work toward a common goal rather than competing.  Can we follow this belief to its ultimate conclusion and work together to build the best OS the world has ever seen?  If we pooled the resources of all the FOSS developers in the world in one unified project, we would literally leave Windows behind in our dust.  Do you think we are up to the challenge?

You may as well ask the Emacs and Vi(m) developers why they can't just work together to create one amazing text editor. No matter how good your argument is, it'll never happen because of differences in developer opinions.
I think it's good this way. A one-size-fits-all distro would be at best a compromise, and would only satisfy a minority. What you want from your operating system sounds very different to what I want. I enjoy playing with everything to make it work, you do not. What would be the perfect solution for both of us? Everything half-configured?

---

### Post by Mehall on 2009-04-09
Agreed.

Also, Upstart will make more things standard throughout any distro that uses it, rather than having the current init.d mess (rc.d in arch)

I think it's a good idea to have *some* standards, but I think it's equally good that other distros can choose to not use them, and make their own, as this breeds the requierd competition.

---

### Post by pbpersson on 2009-04-09
> **Barrucadu said:**
> 
I think it's good this way. A one-size-fits-all distro would be at best a compromise, and would only satisfy a minority. What you want from your operating system sounds very different to what I want. I enjoy playing with everything to make it work, you do not. What would be the perfect solution for both of us? Everything half-configured?

How about just standardizing the hardware detection so it works across all distros?

I am tired of hearing people say "Your distro is great but it would not detect my hardware so I tried distro xyz and it worked but I hated everything else so I went back to Windows"

If you take a look at the posts here on the forum, you will see tons of posts where network cards, graphics cards, and sound cards are not working properly due to incorrect hardware detection - the drivers are there but people need to tinker for days or weeks to get them working.

For people such as yourself who expect the distro to be broken out of the box, I am certain that once you install the distro and it works you can delete some files so you have something broken to work on.

Then we can all be happy.  :)

---

### Post by Simian Man on 2009-04-09
> **pbpersson said:**
> If you take a look at the posts here on the forum, you will see tons of posts where network cards, graphics cards, and sound cards are not working properly due to incorrect hardware detection - the drivers are there but people need to tinker for days or weeks to get them working.

Here's one example where that would not work.  Fedora 11 is switching the default Nvidia drivers from the old nv drivers to the newer Nouveau drivers.  Nouveau is independent from Nvidia and, unlike nv, will offer 3d support.  However it is a very new project and will likely have some bumps on the way.

Ubuntu likes older, more stable software and likely won't adopt Nouveau for a while, but Fedora likes to be cutting edge so are adopting it early.  Surely there will be some Nvidia cards that will work better with one driver and some that will work better with the other (as Nouveau becomes more mature especially).  Thus Fedora will better support some graphics cards and Ubuntu will better support others.

I'm sure there are lots of other examples, but this is one that is currently happening.

---

### Post by Skripka on 2009-04-09
> **pbpersson said:**
> How about just standardizing the hardware detection so it works across all distros?


"Standardizing" linux will likely only happen shortly after the Lions win the Super Bowl.

---

### Post by Therion on 2009-04-09
> **pbpersson said:**
> How about just standardizing the hardware detection so it works across all distros?

How about you build me a rocket-ship that will take me to the moon and back?

No offense by that, I'm trying to make a point.  Do you even know what you're asking?  

You seem to want to reduce the act of building an entire operating system down to something akin to assembling a sandwich ("Just add tomato!") and it's just not that simple.





/Waiting for someone to come in and say "But.. But *Windows*...  ](*,)

---

### Post by pbpersson on 2009-04-09
> **Therion said:**
> How about you build me a rocket-ship that will take me to the moon and back?

No offense by that, I'm trying to make a point.  Do you even know what you're asking?


Here is what we have so far:

1.  Linus creates the kernel which has the device drivers
2.  There is a layer called "hardware detection" which detects the hardware on the machine and assigns the proper drivers so the hardware functions
3.  This hardware detection layer is not standardized between distros so some distros from a user perspective appear broken.
4.  This hardware detection layer which is directly above the kernel layer, if standardized across all distros, would allow all distros to work with a wider variety of hardware.

I am certain that the hardware detection layer is very complicated, my only request is that we spread it around so it is consistent and shared.

The rocket ship has already been built, it has gone to the moon and back, but we are not sharing the knowledge.

Now.....it is very possible that there is something I am missing here that will make this not feasible.  However, I have not yet heard what this is other than the story about Fedora wanting to abopt a new driver project for graphics cards.

---

### Post by Simian Man on 2009-04-09
> **pbpersson said:**
> 
Now.....it is very possible that there is something I am missing here that will make this not feasible.  However, I have not yet heard what this is other than the story about Fedora wanting to abopt a new driver project for graphics cards.

The reason is that not all distros ship all drivers.  Your part 1 assumes that the kernel is a fixed, static entity, however distros ship the subset of drivers and features that they want.

---

### Post by samjh on 2009-04-09
> **pbpersson said:**
> 1.  Linus creates the kernel which has the device driversYes, the kernel can incorporate drivers, but different distros choose to incorporate different sets of modules for drivers.  So you're almost right, but not quite.
> **pbpersson said:**
> 2.  There is a layer called "hardware detection" which detects the hardware on the machine and assigns the proper drivers so the hardware functions
3.  This hardware detection layer is not standardized between distros so some distros from a user perspective appear broken.Hardware detection is standardised via the Linux Hotplug project, which has been in the Linux kernel since 2.4.
> **pbpersson said:**
> 4.  This hardware detection layer which is directly above the kernel layer, if standardized across all distros, would allow all distros to work with a wider variety of hardware.No, it won't.  As I said, different distros incorporate different sets of driver modules for technical reasons.  It matters not that hardware is detected if the kernel cannot communicate with it due to limitations of drivers.

> **pbpersson said:**
> I am certain that the hardware detection layer is very complicated, my only request is that we spread it around so it is consistent and shared.It is consistent and it is shared.  What isn't consistent is the state of the drivers, and the versions of drivers and kernel each distro includes into their releases.

> **pbpersson said:**
> The rocket ship has already been built, it has gone to the moon and back, but we are not sharing the knowledge.It has been to the moon and back many times, but via different rocket ships which follow the same basic design but with different features.

> **pbpersson said:**
> Now.....it is very possible that there is something I am missing here that will make this not feasible.  However, I have not yet heard what this is other than the story about Fedora wanting to abopt a new driver project for graphics cards.
It is not feasible.

Different Linux distros cater for different needs.  They are also different because they carry different versions of software packages.  Despite having so much standardisation in Linux these days, some things just can't be standard without sacrificing progress.

The example cited about Fedora is quite a good one.  Fedora aims to push the envelope of FOSS progress.  Some of the technologies it incorporates into its releases are fraught with risk, but they do it anyway in order to foster innovation and accelerate growth.  Others, like Debian, take a wait-and-see approach, incorporating only the thoroughly tested technologies.  Ubuntu and OpenSUSE sit somewhere in between the two extremes.  In your model, how will you reconcile the four distros into a standardised distro without reducing innovation, remembering that even the kernel versions and device modules differ between the four?

---

### Post by pbpersson on 2009-04-10
> **samjh said:**
> 

The example cited about Fedora is quite a good one.  Fedora aims to push the envelope of FOSS progress.  Some of the technologies it incorporates into its releases are fraught with risk, but they do it anyway in order to foster innovation and accelerate growth.  Others, like Debian, take a wait-and-see approach, incorporating only the thoroughly tested technologies.  Ubuntu and OpenSUSE sit somewhere in between the two extremes. 

Thank you for explaining that.  It now makes sense to me why different distributions can handle device drivers differently even though they are all standardized to a great degree.  It sounds like they are all on the same journey but at different spots on the road.

I am herein only referring to DESKTOP distributions such as SUSE, Ubuntu, Mint, etc. that would be used by John and Jane Doe as their home OS.

This clears things up for me.

---

### Post by mips on 2009-04-10
> **pbpersson said:**
> 
I am herein only referring to DESKTOP distributions such as SUSE, Ubuntu, Mint, etc. that would be used by John and Jane Doe as their home OS.


Nice of you to define what you expect John & Jane Doe to use as their home OS. Stop trying to put things into boxes.

---

### Post by 23meg on 2009-04-10
[QUOTE=samjh]Hardware detection is standardised via the Linux Hotplug project, which has been in the Linux kernel since 2.4.[/QUOTE]

Hotplug has been obsoleted by udev in pretty much every major distribution.

---

### Post by SnappyU on 2009-04-13
I like the artist and lego analogy, if only the basic building blocks for linux distros are working like paint and lego blocks.

Things like input devices, display, wifi etc should be working by the time the distro is released.  Distros should stay and give freedom of choice, but that would be nice when the basics are working.

As it is, ubuntu, fedora, etc are all getting there, except that every one other distro release, something as basic as display, audio or input breaks and requires the user to hunt for patches and fixes.  Just imagine if the paint don't 'work' the way they are supposed to or some lego blocks don't fit?  Notice how each lego block that is supposed to be identical, is identical.

Engines are engines; tires are tires.  But each model of cars from diff makers are somewhat diff, and that kind of choice is nice.  Imagine if a new model of Honda or BMW come with a broken window or screenswiper?  You get the idea.

---

