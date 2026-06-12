---
title: "Time for Linux to ditch shared libraries?"
date: 2010-02-19
forum: The Cafe
---

### Post by clanky on 2010-02-19
OK, so the usual argument goes something along the lines of shared libraries == less disk space / reduced bandwidth for downloads, right?

But really, who doesn't have elevteen million terabytes of disk space now and how much bandwidth are we really talking about?

Why not ditch shared libraries, make each piece of software a simple standalone download package, do away with dependency handling package managers (how much disk space does apt / yum / pacman / whatever take up?)

Thoughts?

---

### Post by GeneralZod on 2010-02-19
> **clanky said:**
> OK, so the usual argument goes something along the lines of shared libraries == less disk space / reduced bandwidth for downloads, right?


And less RAM usage, and increased security.

---

### Post by Hetor on 2010-02-19
You're funny.

---

### Post by kellemes on 2010-02-19
I don't have "elevteen million terabytes" of diskspace.

---

### Post by saulgoode on 2010-02-19
If ten thousand programs* rely upon the same library and the developers of that library modify it to either enhance it or fix a bug, then -- with static linking -- each of the ten thousand programs would need to be recompiled, redistributed, and re-installed in order for those improvements to have effect. 


* As an example, pretty much every GNU/Linux program there is gets dynamically linked to libc.so (GLIBC).

---

### Post by Barrucadu on 2010-02-19
So, your argument is basically &#8220;We all have lots of disk space so let's waste it&#8221;?

---

### Post by hessiess on 2010-02-19
This would also not be possible for legal reasons, think about the large number of LGPL libs. Any software which is statically linked to an LGPL lib is in violation of the licence, unless the program is released under the GPL.

And overall, centralised package managers make for a much easier to manage operating system. 1 command can update *everything* in one go.

---

### Post by clanky on 2010-02-19
> **Barrucadu said:**
> So, your argument is basically “We all have lots of disk space so let's waste it”?

Yeah, thanks for putting words in my mouth. 

No, my argument is that as hardware develops to the point where we no longer need to worry about saving a few kB of disk space, then the advantages of package management no longer outweigh the disadvantages.

---

### Post by clanky on 2010-02-19
> **hessiess said:**
> This would also not be possible for legal reasons, think about the large number of LGPL libs. Any software which is statically linked to an LGPL lib is in violation of the licence, unless the program is released under the GPL.

Sorry, I don't get what your saying here, how does this mean that programs have to have shared libraries?  

> **hessiess said:**
> 
And overall, centralised package managers make for a much easier to manage operating system. 1 command can update *everything* in one go.

Again, I would say that the disadvantages outweigh the advantages, look at how many times an update causes problems, if applications where "stand-alone" then they could simply be updated singly, there could even still be some kind of central register of applications installed on your system which could check for updates, but what I am talking about is getting rid a a database which manages what dependencies are installed / needed for certain applications, when you download an application you get everything which that application needs to run.

---

### Post by blueturtl on 2010-02-19
Nah. You can get other systems designed like that such as Microsoft Windows.

---

### Post by Tibuda on 2010-02-19
[http://sta.li/](http://sta.li/)

> stali (sta[tic] li[nux]) is a new new linux distribution based on a hand selected collection of the best tools for each task and **each tool being statically linked** (including some X clients such as xterm, surf, dwm, dmenu, mplayer).

It also targets binary size reduction through the avoidance of glibc and other bloated GNU libraries where possible (early experiments show that statically linked binaries are usually smaller than their dynamically linked glibc counterparts!!!). Note, this is pretty much contrary to what Ulrich Drepper reckons about static linking.

Due to the side-benefit that statically linked binaries start faster, the distribution also targets performance gains.

---

### Post by clanky on 2010-02-19
> **danielrmt said:**
> [http://sta.li/](http://sta.li/)

Interesting reading, thanks.

---

### Post by VertexPusher on 2010-02-19
> **clanky said:**
> Interesting reading, thanks.
Interesting indeed.

Each vulnerability in a base library would require StaLi users to redownload the entire distribution, because all applications would need to be relinked and redeployed.

And of course there are applications that use shared libraries as plugins. Imagine a music application statically linked with all existing LADSPA plugins. Or a video player such as Totem statically linked with all existing GStreamer plugins.

---

### Post by proxess on 2010-02-19
You've been going on about the disadvantages. What are they??

---

### Post by RiceMonster on 2010-02-19
I don't know. now if there's a bug of security hole or something in a library, every single application that uses that library has to be recompiled and updated. If you're downloading them separately. Now at this point, who's to say all the devs of each application are going to update it, and who's to say everyone using it is going to update?

Obviously the advantage would be no dependency or backwards compatibility issues, but I don't know.

---

### Post by gnomeuser on 2010-02-19
If you want better performance at a slight cost in security, you can use prelink *** warning on lucid recently this nuked my entire system. while this was a development release and I might have encountered some kind of rare accident or user error I would advice trying it on a non important system which can be recovered quickly first.

Staticly linked would not just lead to bigger binaries but also bigger updates. Not just because of the added static bindng but because for at least a class of packages we will need to update a lot of packages at once to ensure that they are using the right verion (important for things like security or stability problems).

I do not believe this is a worthwhile change, I think using prelink or a similar hybrid like system we can get part of the way. We can also just or in addition to that profile our tools and see where we can optimize.

*edit*

I should also mention that staticly linking due to the high demands on storage and bandwidth would also put a higher pressure on both Canonical but also our generous mirror sponsors. We should also consider these costs. Furthermore since the sheer size of updates is concerning developers might start trying to bundle several changes at once to limit large update churn. This would lenghten the cycle from bug to a fix is being deployed and slow down development, and in worst case can lead to users being stuck on non-functional desktops for a greater length of time and likely also due to the larger set of change an increased risk of being affected by new bugs. I suspect though that automatically created ppas and automated answers to users based on analysis of bug report symptoms would lessen this and give us a good model for overcoming this problem if we staticly link. Though the spawn of such likely multiple possibly conflicting ppas could be problematic if not managed correctly. 

I just don't think it is worth the risk, at least not till we have some real benchmarks and measurable difference to go by to determine the correct path. Right now we are just assuming that it will be faster, we don't know how much if any difference this makes nor if it is a significant improvement in the user experience.

*edit 2*
Here's an old but still valid guide on how to use [ul=http://ubuntuforums.org/showthread.php?t=1971]prelink on Ubuntu[/url]

---

### Post by hessiess on 2010-02-19
> **clanky said:**
> Sorry, I don't get what your saying here, how does this mean that programs have to have shared libraries?

If the author of the library licences it under a licence which only permits shared linking, i.e. the LGPL(under certain conditions), linking it statically would be a licence breach.

> 
Again, I would say that the disadvantages outweigh the advantages, look at how many times an update causes problems, if applications where "stand-alone" then they could simply be updated singly, there could even still be some kind of central register of applications installed on your system which could check for updates, but what I am talking about is getting rid a a database which manages what dependencies are installed / needed for certain applications, when you download an application you get everything which that application needs to run.

I have *NEVER* had an update cause any problems, even on Arch, a rolling release distro. Having a centralised management system is basically essential these days because of the shear number of individual applications. Not having a centralised system just results in the complete mess or a major pain in the ***. Keeping all of the individual applications on Windows up to date with security updates is a major pain because there is no centralised update system. As a workaround meny application developers have implemented custom update systems which just results in a overcomplicated mess.

Once you have a package management system, dependency management is not that difficult to add. Removing shared libs would not solve the problem because most of the brackeges which occur are caused by API changes. If something wont compile/run against some library version then it makes no difference if its statically or dynamically linked.

---

### Post by Psumi on 2010-02-19
> **hessiess said:**
> I have *NEVER* had an update cause any problems, even on Arch,

Not every distro can be like arch.

---

### Post by hessiess on 2010-02-19
> **Psumi said:**
> Not every distro can be like arch.

Can't remember having any problems with Ubuntu updates ether, though I always did a clean install when a new release came out.

---

### Post by RiceMonster on 2010-02-19
> **hessiess said:**
> If something wont compile/run against some library version then it makes no difference if its statically or dynamically linked.

Yes, but in this case, you don't have to worry about the API changes, because that application doesn't have to be compiled against the newer shared library.

---

### Post by toupeiro on 2010-02-19
Windows uses shared libraries, (DLL's) as well.  Having been a Windows packager before, I greatly prefer the way linux does shared libraries in combination with symbolic links as opposed to brute force upgrade a DLL version or isolating complete merge modules into an application you want to install.  That's horribly wasteful.  No offense, but this just sounds like one more post with an OP clearly having an inadequate understanding about his/her topic.  However, if the question was sincere, then No, IMO as long as you NEED libraries for a program, you might as well be able to share them.

---

### Post by Tibuda on 2010-02-19
Just a (dumb) question: can we run a very old static-compiled binary in a system full of bleeding-edge dynamic-compiled binaries/libraries?

---

### Post by undecim on 2010-02-19
You're joking, right?

---

### Post by Tibuda on 2010-02-19
> **undecim said:**
> You're joking, right?

If you are talking to me, no, I'm not.

---

### Post by Simian Man on 2010-02-19
No, dependencies are not that big of a problem compared to disk space, bandwidth and security.  What I'd like to see, however, is simplification of the way libraries are packaged.  It'd be really nice if, for example, there was a gnomelib package that included the literally dozens of libraries related to GTK and the Gnome desktop.  That'd be a nice middle ground I think.

> **hessiess said:**
> This would also not be possible for legal reasons, think about the large number of LGPL libs. Any software which is statically linked to an LGPL lib is in violation of the licence, unless the program is released under the GPL.

The program doesn't have to be GPL, just open source.  Actually all you really need is to distribute your object code so end users can relink it.

---

### Post by MisfitI38 on 2010-02-19
> **hessiess said:**
> Can't remember having any problems with Ubuntu updates ether, though I always did a clean install when a new release came out.

That's called a *reinstall*, not an update. ;)

As for shared libraries, they keep the 500+ distributions as moving targets, ensuring software vendors and gaming companies probably won't be taking a look at GNU/Linux in the near future. 

IMO, static is the way to go for a desktop system. (to paraphrase raff_king) Providing good, solid core libraries that are tightly integrated with a stable api would allow for a vendor to compile his package once, dynamically linking only against the stable core api, and then ship the rest of his dependencies himself. So $package or $game would work on all distributions and versions, not only on ubuntu xx.yy with a patch-level from dd-mm-yyyy.

In my view, there are more advantages than disadvantages for a desktop distro, and I would love to see one become popular.

---

### Post by MaxIBoy on 2010-02-19
This has been discussed to death.

**All** disadvantages of shared libraries are myths and come from lack of understanding about the topic.

It is possible to have multiple versions of the same libraries installed, and this is actually common practice. For example, I have libjpeg62 and libjpeg8 installed; some programs use one and some use the other. Generally this version number gets incremented if compatibility gets broken, thus it counts as a "separate" library which does not *replace* the original version. Otherwise, complete binary compatibility is retained. (As in, you don't need to recompile jack.)

Modern package managers do an excellent job of managing this for you so you don't need to worry about incompatible package versions. Sure, for the traditional shrink-wrapped distribution model this sucks, but the traditional shrink-wrapped distribution model sucks in many other ways as well.

Finally, if you want the performance benefits of static linking, you can try installing "prelink" (which will also relink everything for you if you update a library.) It does take up a bunch of disk space though (I found it takes up about 15-25% more on my root partition, which is why I no longer use it.)

---

