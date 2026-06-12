---
title: "Which is the safest Linux Server Platform?"
date: 2009-10-21
forum: Server Platforms
---

### Post by WitchCraft on 2009-10-21
I wanted to know which Linux/Unix server platfrom is the safest.

Anybody has a good reason or stats on which distro is safest ?
Is FreeBSD saver than Linux (assuming both are correctly configured)?

Are there any tools like chroot jails, address space randomizers or intrusion detection systems that should be installed ?

Any programs/services that should definitely not be installed ?
Which webserver (properly configured) is the safest (with reasonable performance) ?

---

### Post by Iowan on 2009-10-21
OpenBSD (not Linux) is supposed to be designed around security. There are a couple of Linux distros that are security-minded as well, but I don't have the names available.  
Avoid services that transmit unencrypted passwords... FTP comes to mind (although there are secure versions).

---

### Post by cdenley on 2009-10-21
I think OpenBSD has the reputation for being "most secure".
[http://www.openbsd.org/](http://www.openbsd.org/)
Any stats you find comparing security will be too subjective to be useful, in my opinion. In addition to their aggressive code auditing, they claim to have a more secure-by-default configuration. I believe the project being based in Canada allows them to distribute/export their OS with strong cryptography which is not allowed for other OS's.

Really, any common Linux server distribution which is properly configured should provide more-than-adequate security. I guess when comparing Linux distro's, you can look into their default SELinux or Apparmor configuration.

---

### Post by WitchCraft on 2009-10-21
I ran OpenBSD before. The only thing I remember is that it was really hard to install. No superprobe, no autoconfiguration of xorg server etc.

Now I think about setting up a command line server, and I think probably it would be worth to do so, because I can work from a remote computer via sshfs for everything.

But is OpenBSD really secure? Of course there is the core operating system which is secure, but there are other programs that run on top, like sshfs, lighthttp, mono etc., and I don't think the secure applies to OpenBSD + server programs.

---

### Post by nsche on 2009-10-21
OpenBSD is as secure as you want it to be.  If you do not think sshfs, lighthttp, mono etc. are secure enough do not run them.  Run more secure alternatives if they exist.  If you want to provide some services from a server you have to have service providers each of which has their own security characteristics. If you want it to be really secure do not install a networking card in it.

---

### Post by baceman007 on 2009-10-21
I'm going to give one of those annoying knowledge answers. Yes there are some distros that focus on security, and OpenBSD is supposed to be great for security, but the most secure system is one that is being administered by an efficient admin that reviews their logs, keeps the system patched, etc. 
So what I'm saying is that a system you're familiar with, and understand, or are willing to learn to understand like good old Ubuntu, should serve you just as well. No security is absolute, and threats always evolve over time.

---

### Post by wojox on 2009-10-21
> **baceman007 said:**
> I'm going to give one of those annoying knowledge answers. Yes there are some distros that focus on security, and OpenBSD is supposed to be great for security, but the most secure system is one that is being administered by an efficient admin that reviews their logs, keeps the system patched, etc. 
So what I'm saying is that a system you're familiar with, and understand, or are willing to learn to understand like good old Ubuntu, should serve you just as well. No security is absolute, and threats always evolve over time.

+1 Couldn't of said it better.

---

### Post by cdenley on 2009-10-21
Forgetting about xorg and any graphics interface would probably be more of a security advantage than picking a more security-focused OS like OpenBSD. Depending on the configuration an Ubuntu server can be more secure than an OpenBSD server. I suggest choosing the linux distro you like best, then configuring it so it is secure.

---

### Post by HermanAB on 2009-10-21
Linux is Linux is Linux...

Take your pick, it is the same difference.

---

### Post by johnycage on 2009-10-22
> **HermanAB said:**
> Linux is Linux is Linux...

Take your pick, it is the same difference.
It's the linux, so it depends how you configure it. You can tweak it to make it more secure. :P

---

### Post by windependence on 2009-10-23
> **HermanAB said:**
> Linux is Linux is Linux...

Take your pick, it is the same difference.

Exactly, and BSD is NOT Linux. Linux is NOT an operating system. It's a kernel. The kernel is bundled with software to form a distribution. This is the fundamental difference between Linux and BSD. BSD IS an operating system in every sense of the word. All the applications made to run on the BSDs are audited by the development team. The ports collection is made to run on each flavor of BSD and will only run on that flavor. The applications do not run on Linux or Unix or any other OS, they are coded just for that form of BSD. This is one reason it is so secure out of the box.

That being said, a bad administrator can open huge holes in BSD or any other OS as has been stated. Loading a GUI package on any OS can and does open security holes and is not necessary on a server. Each application you load on the OS provides potential security holes and must be properly secured just as anything else you run on the server.

My opinion? If I wanted security, I would run OpenBSD, but then I am an admitted BSD junkie. Two remote holes in ten years does say something about the OS in my mind though. 

You can't really blame Linux, as it is impossible to control security when the applications have no central development point. I'm not saying that is bad, just that it promotes a bit more confusion and disorganization than applications that are specifically written for a given OS.

-Tim

---

### Post by cdenley on 2009-10-23
Two remote holes in the **default** install. They do have an impressive security record, but this can be a little misleading since I don't think their default install has any servers. How many remote security flaws has Linux had in the last 10 years which can be exploited without any listening processes?

I think Linux IS an OS, the same as any BSD flavor. The difference is Linux has many different distributions using the same kernel, so they are all the same OS, while each BSD flavor has their own unique kernel, which makes them their own OS. There is nothing inherent with BSD's port system which makes it more secure, unless maybe since they have to port linux software to run on their BSD flavor, they are forced to review and rewrite code. They may do more code auditing (OpenBSD in particular), but there is no reason a Linux distribution couldn't audit the code for their packages just as much.

---

### Post by dragos2 on 2009-10-23
There is no rule. Some are safer because are less targeted.

---

### Post by Dragonbite on 2009-10-23
> **WitchCraft said:**
> I wanted to know which Linux/Unix server platfrom is the safest.

Anybody has a good reason or stats on which distro is safest ?
Is FreeBSD saver than Linux (assuming both are correctly configured)?

Are there any tools like chroot jails, address space randomizers or intrusion detection systems that should be installed ?

Any programs/services that should definitely not be installed ?
Which webserver (properly configured) is the safest (with reasonable performance) ?

The safest system depends on the administrator.

Otherwise I generally think of CentOS (which is really Red Hat) with SELinux installed is supposed to be a very secure system plus it has the familiarity of Linux and support of a Linux community.

---

### Post by openfly on 2009-10-23
The single "safest" linux distro is either Gentoo on Alpha or PS2 Linux.

The argument is as follows.

No one writes their exploits for 128bit MIPSel.  ( PS2 Arch )

And finding executable memory on Big endian, plus writing shellcode for alpha... makes a gentoo alpha build an unlikely target.

I say gentoo, because finding executable memory locations and timing patterns in say... rpms or binary debs can make portability of malicious code go from obscenely difficult and time consuming to lol easy.

script kiddies simply wouldn't target you.  And those that could, probably wouldn't care to.

So that's my suggestion.

---

### Post by MisfitI38 on 2009-10-23
All things being equal and in the hands of a capable admin, OpenBSD is certainly the most secure, period.

Having established that, I always say that the best OS for a server is the one you are most familiar with... unless you have time to learn OpenBSD. ;)

---

### Post by windependence on 2009-10-23
> **cdenley said:**
> Two remote holes in the **default** install. They do have an impressive security record, but this can be a little misleading since I don't think their default install has any servers. How many remote security flaws has Linux had in the last 10 years which can be exploited without any listening processes?

I think Linux IS an OS, the same as any BSD flavor. The difference is Linux has many different distributions using the same kernel, so they are all the same OS, while each BSD flavor has their own unique kernel, which makes them their own OS. There is nothing inherent with BSD's port system which makes it more secure, unless maybe since they have to port linux software to run on their BSD flavor, they are forced to review and rewrite code. They may do more code auditing (OpenBSD in particular), but there is no reason a Linux distribution couldn't audit the code for their packages just as much.

You're missing the fundamental difference here. In BSD, the applications are part of the OS. That is a HUGE difference. There's one code base. All the apps are written for BSD and the code is audited (especially with OpenBSD) and is known to be secure. I'm not bashing Linux, just pointing out that Linux is just a kernel, not an OS. 

[http://pupeno.com/blog/linux-is-not-an-operating-system/](http://pupeno.com/blog/linux-is-not-an-operating-system/)

[http://www.tech-no-media.com/2009/07/linux-is-not-operating-system.html](http://www.tech-no-media.com/2009/07/linux-is-not-operating-system.html)

[http://www.nuxified.org/article/linux_not_os](http://www.nuxified.org/article/linux_not_os)

The comments section on the article directly above this compares and contrasts the BSD way vs. the Linux way.

And finally, right from gnu.org:
[http://www.gnu.org/gnu/linux-and-gnu.html](http://www.gnu.org/gnu/linux-and-gnu.html)

Again, I'm not saying Linux is bad in any way, just that for security, the complete OS design is much better.

-Tim

---

### Post by Vegan on 2009-10-23
Security is almost completely independent on the distribution, but rather on how skilled the administrator is.

I use a Linksys box and it has a firewall that I use.

Next I only open ports for specific services. HTTP and FTP and NTP are the only ones I pen.

My web server etc are safe, however my forums are constantly attacked by spammers. The spam problem is where I put most of my intellect into.

---

### Post by windependence on 2009-10-23
This has nothing to do with what I just posted. We have already established that the admin has everything to do with security.

-Tim

---

### Post by cdenley on 2009-10-24
> **windependence said:**
> You're missing the fundamental difference here. In BSD, the applications are part of the OS. That is a HUGE difference. There's one code base. All the apps are written for BSD and the code is audited (especially with OpenBSD) and is known to be secure. I'm not bashing Linux, just pointing out that Linux is just a kernel, not an OS.

Linux is just as much an OS as any BSD. The BSD's are also "just kernels". Linux distributions have their own code base the same as BSD's. Ubuntu's entire repo is built from source the same as *BSD's ports. They aren't written "for BSD", they are simply compiled for BSD. There may occasionally be a patch specifically to make it compile on BSD, but Linux distributions often have their own patches as well. BSD and Linux applications are all compiled from the same source. Applications are not re-written for BSD, as you seem to suggest. Linux distros can audit the code just as much if they choose. The BSD port system is not inherently more secure.

---

### Post by MisfitI38 on 2009-10-24
> **cdenley said:**
> Linux is just as much an OS as any BSD. The BSD's are also "just kernels". ..

You are 100% wrong, unfortunately.

---

### Post by cdenley on 2009-10-24
> **MisfitI38 said:**
> You are 100% wrong, unfortunately.

Well then, please explain.

---

### Post by Sporkman on 2009-10-24
> **MisfitI38 said:**
> You are 100% wrong, unfortunately.

Is Ubuntu an OS?

---

### Post by MisfitI38 on 2009-10-24
OpenBSD is a complete system, the entirety of which is developed within a single source repository and kept in sync. It is not a "Kernel plus utilities" that can be upgraded separately from each other. 
The failure to keep a system (kernel, userspace utilities, and applications) in complete synchronicity invariably results in security liabilities. 
Because of its comparatively 'schizoid' development model, there is no GNU/Linux system that can compare to OpenBSD's code and security audit process.

---

### Post by cdenley on 2009-10-24
> **MisfitI38 said:**
> OpenBSD is a complete system, the entirety of which is developed within a single source repository and kept in sync. It is not a "Kernel plus utilities" that can be upgraded separately from each other. 
The failure to keep a system (kernel, userspace utilities, and applications) in complete synchronicity invariably results in security liabilities. 
Because of its comparatively 'schizoid' development model, there is no GNU/Linux system that can compare to OpenBSD's code and security audit process.

The ports system is a single source repository just like ubuntu's repository. They are both the same software sources with patches from the port/package maintainer. Regardless of the "development model" or auditing practices done by any given Linux distribution or BSD flavor, they are both OS's. OpenBSD may audit the code in their source repository more than any other BSD flavor or Linux distro, but that doesn't mean Linux isn't an OS.

Also, you can upgrade an individual application "separately from each other" in any BSD just like you can in any Linux distro.
[http://www.openbsd.org/faq/faq15.html#PkgUpdate](http://www.openbsd.org/faq/faq15.html#PkgUpdate)

---

### Post by cdenley on 2009-10-24
> **Sporkman said:**
> Is Ubuntu an OS?

I think technically, Ubuntu is a Linux distribution. Linux is an OS. Not that it really matters.

On a side note, is Darwin BSD an OS? If so, what is Mac OSX?

---

### Post by MisfitI38 on 2009-10-24
> **cdenley said:**
> The ports system is a single source repository just like ubuntu's repository. They are both the same software sources with patches from the port/package maintainer. Regardless of the "development model" or auditing practices done by any given Linux distribution or BSD flavor, they are both OS's. OpenBSD may audit the code in their source repository more than any other BSD flavor or Linux distro, but that doesn't mean Linux isn't an OS.

Also, you can upgrade an individual application "separately from each other" in any BSD just like you can in any Linux distro.
[http://www.openbsd.org/faq/faq15.html#PkgUpdate](http://www.openbsd.org/faq/faq15.html#PkgUpdate)

Who is talking about ports? A port is an application to be *ported* to a different platform. Ports has nothing to do with this discussion and is a completely different entity.
OpenBSD is a complete OS which is developed within 1 single source repository. Do not confuse this with the availability of a ports tree.
A GNU/Linux distribution is the amalgamation of hundreds, (for a small lightweight system) or thousands (for a more bloated distro) of apps, userspace utilities and the kernel, developed within countless repos worldwide under the direction of countless projects. Just because they are gathered together into a single distro's repo does not mean it can be compared to the stringent oversight, quality control or code auditing of a BSD system.
The GNU/Linux schizoid development model is certainly more conducive to rapid development, but it is NOT comparable to the code correctness of OpenBSD. It just isn't.

---

### Post by windependence on 2009-10-26
> **cdenley said:**
> Linux is just as much an OS as any BSD. The BSD's are also "just kernels". Linux distributions have their own code base the same as BSD's. Ubuntu's entire repo is built from source the same as *BSD's ports. They aren't written "for BSD", they are simply compiled for BSD. There may occasionally be a patch specifically to make it compile on BSD, but Linux distributions often have their own patches as well. BSD and Linux applications are all compiled from the same source. Applications are not re-written for BSD, as you seem to suggest. Linux distros can audit the code just as much if they choose. The BSD port system is not inherently more secure.

Have you even read any of the articles I posted? Particularly the on from gnu.org? I think it's safe to say if GNU thinks Linux is a kernel and not an OS, it probably is. You may not like it, but as you grow in the 'nix world, you will find there are things even better than Linux. Things that have been around a lot longer and have been time tested and proven in the Unix world. 

Linux is great, but it is not BSD, and BSD is not a Linux distro. There is much on the web about the history of both. You may want to read about the differences and why one is an OS and one is simply a kernel with applications commonly bundled with it.

-Tim

---

### Post by Dragonbite on 2009-10-26
> **MisfitI38 said:**
> Who is talking about ports? A port is an application to be *ported* to a different platform. Ports has nothing to do with this discussion and is a completely different entity.
OpenBSD is a complete OS which is developed within 1 single source repository. Do not confuse this with the availability of a ports tree.
A GNU/Linux distribution is the amalgamation of hundreds, (for a small lightweight system) or thousands (for a more bloated distro) of apps, userspace utilities and the kernel, developed within countless repos worldwide under the direction of countless projects. Just because they are gathered together into a single distro's repo does not mean it can be compared to the stringent oversight, quality control or code auditing of a BSD system.
The GNU/Linux schizoid development model is certainly more conducive to rapid development, but it is NOT comparable to the code correctness of OpenBSD. It just isn't.

Does OpenBSD, FreeBSD, NetBSD, PC-BSD and other BSD flavors share the same repository and/or their applications compatible with each other? 

If so, then that would make a difference but if not then I don't see how BSD is all that much different from Linux and the individual distros which "massage" the applications for their particular systems.

That's not to say that BSD doesn't have more stringent repo's quality control. Unfortunately that is all up to the individual people and if you get a few losers managing the repo's, or a Linux Distro gets some people who really know what their doing then this advantage could be compromised.

I'm curious, though, how BSD handles things like codecs and proprietary applications like Flash and Java.

---

### Post by gnuisancev3 on 2009-10-26
> **WitchCraft said:**
> I wanted to know which Linux/Unix server platfrom is the safest.

Anybody has a good reason or stats on which distro is safest ?
Is FreeBSD saver than Linux (assuming both are correctly configured)?

Are there any tools like chroot jails, address space randomizers or intrusion detection systems that should be installed ?

Any programs/services that should definitely not be installed ?
Which webserver (properly configured) is the safest (with reasonable performance) ?

OpenBSD, Redhat, or Debian.  IMO.

But in the end it really matters how you have it configured.  I recommend reading through the NSA's Guide to Securing a Red Hat Linux box.  It's pretty applicable across distros. 

[http://www.nsa.gov/ia/_files/os/redhat/rhel5-guide-i731.pdf](http://www.nsa.gov/ia/_files/os/redhat/rhel5-guide-i731.pdf)

---

### Post by gnuisancev3 on 2009-10-26
> **cdenley said:**
> I think technically, Ubuntu is a Linux distribution. Linux is an OS. Not that it really matters.

On a side note, is Darwin BSD an OS? If so, what is Mac OSX?

Linux is a Kernel.  

Ubuntu would be a distribution, yes, but technically its an OS.  An OS being a kernel and a collection of tools that reside on top of that. 

Mac OS X is an OS.  I don't know what Darwin BSD is, but i'm guessing that's the kernel OS X runs off of.

---

### Post by cdenley on 2009-10-26
> **gnuisancev3 said:**
> Linux is a Kernel.  

Ubuntu would be a distribution, yes, but technically its an OS.  An OS being a kernel and a collection of tools that reside on top of that. 

Mac OS X is an OS.  I don't know what Darwin BSD is, but i'm guessing that's the kernel OS X runs off of.

Except everyone here seems to be suggesting BSD's are more than kernels. I'm pretty sure, however, that almost everything besides the *BSD kernel is a collection of software which is not specific to that kernel, just like Linux, so I still fail to see how any BSD is MORE of an OS. BSD or Linux, they are all just kernels with a collection of tools most of which aren't unique to that BSD/distro/kernel, as well as a repository of open-source applications. I already said OpenBSD has the best security, and I'm not trying to defend Linux when I doubt your claim that BSD is more of an OS.

Mac OS X is basically a GUI and graphical applications which run on Darwin BSD. You can have a fully functioning system with only Darwin BSD and not Mac OS X, though it isn't very common. Mac OS X, on the other hand, couldn't function without Darwin BSD, but I guess Darwin BSD is a component of Mac OS X. Are they both an OS?

---

### Post by MisfitI38 on 2009-10-26
> **cdenley said:**
> Except everyone here seems to be suggesting BSD's are more than kernels. I'm pretty sure, however, that almost everything besides the *BSD kernel is a collection of software which is not specific to that kernel, just like Linux, so I still fail to see how any BSD is MORE of an OS. BSD or Linux, they are all just kernels with a collection of tools most of which aren't unique to that BSD/distro/kernel....

This is the error; Assuming that BSD is a kernel with a collection of tools which are not unique to that BSD.

In fact, as I mentioned above, *BSD *is not* developed with a 'kernel plus utilities' model; The whole operating system is coded by *one team and in one revision control system.* There is nothing to 'collect' as you have inferred.

Hopefully this can clear things up. This is taken from FreeBSD's documentation, yet the same can be said of the other BSD variants: 
>   There is only *one* team responsible for organising and managing the development of FreeBSD; the FreeBSD Core Team. Since there's one team, there's only one version of FreeBSD, not a bunch of distributions with a common kernel but with differing tools and applications (GNU/Linux). There's no fragmentation and competing groups in the FreeBSD community, although there are different BSD operating systems, but they have been created for different purposes in mind: OpenBSD: security, NetBSD: portability, DragonFlyBSD: scalability and cluster computing.
*FreeBSD is developed as a complete operating system. The kernel, device drivers, libraries, compilers, user-land applications and utilities are all developed in the same source code revision tracking system (CVS), unlike GNU/Linux where the kernel, user-land utilities and applications are developed separately and packaged together by other groups/developers as GNU/Linux distributions. *


---

### Post by Dragonbite on 2009-10-26
> **MisfitI38 said:**
> This is the error; Assuming that BSD is a kernel with a collection of tools which are not unique to that BSD.

In fact, as I mentioned above, *BSD *is not* developed with a 'kernel plus utilities' model; The whole operating system is coded by *one team and in one revision control system.* There is nothing to 'collect' as you have inferred.

Hopefully this can clear things up. This is taken from FreeBSD's documentation, yet the same can be said of the other BSD variants:

It sounds like FreeBSD develops its kernel and some utilities on its own and doesn't share its kernel with anybody else so the kernel is not compatible with OpenBSD, NetBSD, etc. For intent and purpose, the only thing FreeBSD shares with the other *BSD is the name and maybe some coding and licensing.

And then on top of FreeBSD, each application (like Gnome, KDE, OpenOffice.org, Gimp, etc.) has to be ported over to the FreeBSD kernel (OS) specifically instead of a common BSD kernel like Linux uses.

So instead of the list of operating systems being; Windows, Linux, Solaris, BSD and OS X

A more proper list would be; Windows, Linux, Solaris, FreeBSD, OpenBSD, NetBSD and OS X

So that means the *BSD team codes the KDE or Gnome environment, Gimp, OpenOffice.org, etc. themselves? 

According to the quote, there are not a lot of "distributions", but there are other BSD systems based off of, or are alternative versions of specific BSD systems. From the [[COLOR="Blue"]Distrowatch list of BSD systems[/COLOR]]("http://distrowatch.com/search.php?category=BSD&origin=All&basedon=All&desktop=All&architecture=All&status=Active") (snipped for size):

> DragonFly is an operating system and environment designed to be the logical continuation of the FreeBSD-4.x OS series. 

m0n0wall is based on a bare-bones version of FreeBSD, along with a web server (thttpd), PHP and a few other utilities. 

MidnightBSD is a FreeBSD derived operating system. ... MidnightBSD was forked from FreeBSD 6.1 beta. 

MirOS is an operating system based on OpenBSD and synchronised with the ongoing development of its parent. 

PC-BSD has as its goals to be an easy-to-install-and-use desktop operating system, based on FreeBSD. 

pfSense is a m0n0wall-derived operating system. 

Sorry, I'm just trying to understand this all.

---

### Post by openfly on 2009-10-26
BSD stands for berkeley systems distribution or something to that effect.  Basically way back in the day Berkeley rewrote bell labs unix which would later become system v.  Then there were 2 branches of unix... the system v branch and the bsd branch...

BSD became the defacto standard in unix.  The design and implementation of 4.3 / 4.4 BSD being the most simple intro to BSD standards... BUT ultimately DOD Spec for UNIX was first applied to BSD.  In fact, posix standards owe a lot of what they are to the BSD spec.

So, when something is a BSD... it simply means they conform to BSD design principles.  Though originally it meant it's of the family of unixes that branched from BSD unix as opposed to system v.  

FreeBSD deviated far away from netbsd ( the oldest of the BSDs, a direct descendant of BSD ( from berkeley )) and openbsd ( a port of netbsd... ubuntu:debian::openbsd:netbsd ).  FreeBSD borrowed heavily from BSDi who was a commercial vendor producing an enterprise ready BSD.  As a result they advanced very quickly and ended up taking off on their own path while net and open bsd trundled along ever so slowly towards their own goals.

Imagine if you will that ubuntu began their own linux kernel tree and releasing their own version of the kernel cherry picking what they wanted from lkml and then rolling in their own features... 

advance 10 years... you have ubuntu linux and ... linux tm.  two very different kernels but both linux.  

Kinda analogous.

---

### Post by windependence on 2009-10-27
The point I think nobody gets is that you cannot run a port from OpenBSD on FreeBSD the way you can with a Linux distro. Every single *BSD has it's own set of applications, tools, and utilities that ONLY run on that OS. This is the fundamental difference and is what makes it so much easier to control security. The development teams have total control over the code that goes in their OS including all the apps, etc.

-Tim

---

### Post by openfly on 2009-10-27
> **windependence said:**
> The point I think nobody gets is that you cannot run a port from OpenBSD on FreeBSD the way you can with a Linux distro. Every single *BSD has it's own set of applications, tools, and utilities that ONLY run on that OS. This is the fundamental difference and is what makes it so much easier to control security. The development teams have total control over the code that goes in their OS including all the apps, etc.

-Tim

Not entirely true... openbsd and netbsd are very very similar.  most stuff is portable between them without interaction.

And freebsd has a linux compat mode.  So you can run elf binaries in it.

And your suggestion that any of this relates to security is absurd.

---

### Post by Dragonbite on 2009-10-27
> **openfly said:**
> Not entirely true... openbsd and netbsd are very very similar.  most stuff is portable between them without interaction.

And freebsd has a linux compat mode.  So you can run elf binaries in it.

And your suggestion that any of this relates to security is absurd.

Most stuff is portable, but not everything. Ultimately this is talking about pretty low-down stuff, not general applications right?  Gnome doesn't count, does it?

Is a "Linux compat mode" similar to Wine in Linux except running elf binaries instead of Windows dll's?

Oh, I am getting so confused!  :)

---

### Post by openfly on 2009-10-27
> **Dragonbite said:**
> Most stuff is portable, but not everything. Ultimately this is talking about pretty low-down stuff, not general applications right?  Gnome doesn't count, does it?


Every linux has it's own set of tools.  =P

I mean NetBSD and OpenBSD really aren't very different on a kernel level.  They are like brothers that hate each other but copy from each other every chance they get.

FreeBSD is a whole nother story because they've been on their own development arch for so long, they are something different from Open and NetBSD for sure.  But technically they are all forks of NetBSD.

---

### Post by openfly on 2009-10-27
> **gnuisancev3 said:**
> Linux is a Kernel.  
Mac OS X is an OS.  I don't know what Darwin BSD is, but i'm guessing that's the kernel OS X runs off of.

Darwin is an OS.  It's the Free/Open Source version of OSX.  It lacks large swathes of functionality such as Aqua.  It is BSD based, and branched from FreeBSD, but very different.  I would not call Darwin a BSD, since it does not conform to BSD design standards, though it is a branch.  I wouldn't even call it a UNIX.  It's a unix like, bsd like, thing...  

I mean if you wanted my honest opinion I'd call it a hacked up bsd kernel with as many good ideas as horrendously bad ones.

---

### Post by rnodal on 2009-10-27
> **MisfitI38 said:**
> OpenBSD is a complete system, the entirety of which is developed within a single source repository and kept in sync. It is not a "Kernel plus utilities" that can be upgraded separately from each other. 
The failure to keep a system (kernel, userspace utilities, and applications) in complete synchronicity invariably results in security liabilities. 
Because of its comparatively 'schizoid' development model, there is no GNU/Linux system that can compare to OpenBSD's code and security audit process.

So according to your logic, if there is an update to OpenSSH then you have to wait until the next release of OpenBSD to have your OpenSSH updated because you cannot upgrade the utilities separate from the kernel?

-r

---

### Post by Dragonbite on 2009-10-27
> **rnodal said:**
> So according to your logic, if there is an update to OpenSSH then you have to wait until the next release of OpenBSD to have your OpenSSH updated because you cannot upgrade the utilities separate from the kernel?

-r

I think the applications they are refering to are lower-level than that since OpenSSH can be installed or not installed.

Maybe the Package Management system is something they are referring to?  I dunno.

---

### Post by rnodal on 2009-10-27
> **Dragonbite said:**
> I think the applications they are refering to are lower-level than that since OpenSSH can be installed or not installed.

Maybe the Package Management system is something they are referring to?  I dunno.

Well the point that I was trying to make was that, I doubt that if there is a security problem in one of the so called "utilities" that you cannot update that utility because you cannot upgrade them separately from the kernel.

-r

---

### Post by MisfitI38 on 2009-10-27
> **rnodal said:**
> So according to your logic, if there is an update to OpenSSH then you have to wait until the next release of OpenBSD to have your OpenSSH updated because you cannot upgrade the utilities separate from the kernel?

-r

If there is a *security* update to openSSH, it will be fixed in [OpenBSD current]("http://www.openbsd.org/anoncvs.html") and [the patch branch.]("http://www.openbsd.org/stable.html") Arbitrarily updating openSSH (or any other package) is a potential security/stability issue because the audited source base would then become compromised. This would be compounded by other such updates which would un-sync the system. The goal is to have pristine, and perfectly audited code, (utilizing cryptography where appropriate) for the base system. This is why I am basically repeating myself. GNU/Linux distros are 'schizoid' cherry-picked kernel+utilities, whereas OpenBSD is a complete, perpetually audited OS developed in a single source repo-- not to be confused with ports.
Remember, *everything* in a GNU/Linux system is an add-on.

More security explanations [here]("http://www.openbsd.org/security.html") and [here.]("http://www.openbsd.org/crypto.html")

---

### Post by rnodal on 2009-10-27
> **MisfitI38 said:**
> If there is a *security* update to openSSH, it will be fixed in [OpenBSD current]("http://www.openbsd.org/anoncvs.html") and [the patch branch.]("http://www.openbsd.org/stable.html") Arbitrarily updating openSSH (or any other package) is a potential security/stability issue because the audited source base would then become compromised. This would be compounded by other such updates which would un-sync the system. The goal is to have pristine, and perfectly audited code, (utilizing cryptography where appropriate) for the base system. This is why I am basically repeating myself. GNU/Linux distros are 'schizoid' cherry-picked kernel+utilities, whereas OpenBSD is a complete, perpetually audited OS developed in a single source repo-- not to be confused with ports.
Remember, *everything* in a GNU/Linux system is an add-on.

More security explanations [here]("http://www.openbsd.org/security.html") and [here.]("http://www.openbsd.org/crypto.html")

That still does not answer my question. If I install OpenBSD and two days later someone finds a security problem in OpenSSH or maybe the kernel. 

How do I get the fixed version of the software? Or I just seat around and wait for the next stable release?

-r

---

### Post by windependence on 2009-10-27
The BSD developers will release a patch for the application. The patch will have been audited just like any other code going into the OS. If you decide to update an application on your own, you would have to compile it from source assuming the source would compile on the OS, and this would be highly unsupported.

-Tim

---

### Post by windependence on 2009-10-27
> **openfly said:**
> Not entirely true... openbsd and netbsd are very very similar.  most stuff is portable between them without interaction.

And freebsd has a linux compat mode.  So you can run elf binaries in it.

And your suggestion that any of this relates to security is absurd.

Agreed, but you would have to agree running one OS's ports on the other OS is not officially supported although possible. 

What side of this are you on anyway. It most certainly relates to security in many many ways. See Misfit's post above for why. I'll give you an analogy. Linux is like baking a cake without a recipe, you just throw in whatever you feel would be good and it turns out half decent, but it's not consistent each time it's put together. *BSD uses a recipe that comes out with the same end result each and every release.

-Tim

---

### Post by WitchCraft on 2009-11-02
Interesting contributions, but actually, I asked which is the safest **_LINUX_** PLATFORM.

I know that OpenBSD is considered "safest by default", but when you use software like apache, it all boils down to 'which distro implements security updates fastest IN GENERAL' regarding the operating system and the server daemons.

---

### Post by MisfitI38 on 2009-11-02
> **WitchCraft said:**
> I wanted to know which Linux/Unix server platfrom is the safest...

?

---

### Post by will81 on 2009-11-02
I've only skim-read this thread, so apologies if somebody's already said it, but have a look at Bastille Linux.  It's a script you run on, I think, any flavour of Linux that locks things down, explaining exactly what it's doing and why.  Very educational and functional.

---

### Post by WitchCraft on 2009-11-13
> **will81 said:**
> I've only skim-read this thread, so apologies if somebody's already said it, but have a look at Bastille Linux.  It's a script you run on, I think, any flavour of Linux that locks things down, explaining exactly what it's doing and why.  Very educational and functional.

I have already installed bastille, but that doesn't help if packages aren't updated fast enough.

Anybody knows which Linux distro has the fastest updates?

---

### Post by the_guv on 2009-11-13
not necessarily safer but, if you go ubuntu, will be less hassle to go with a long term support edition (currently hardy Heron 8.04)

but really, it's how you set up your iptables (firewall) that matters, and things like your ssh.  keep unnecessary ports closed.  here's handy ..


[LIST]
[*][COLOR=DeepSkyBlue][Harden the Secure Shell (SSH) & Create a Firewall]("http://www.guvnr.com/web/web-dev/harden-ssh-create-firewall/")[/COLOR]
[/LIST]

.. and bear in mind, today is Friday the 13th :P

---

### Post by WitchCraft on 2009-11-13
> **the_guv said:**
> 
.. and bear in mind, today is Friday the 13th :P


:lolflag:

---

