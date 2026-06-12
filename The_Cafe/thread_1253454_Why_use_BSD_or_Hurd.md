---
title: "Why use BSD or Hurd?"
date: 2009-08-30
forum: The Cafe
---

### Post by keiichidono on 2009-08-30
Is there a technical advantage of BSD variations and GNU Hurd over the Linux Kernel that i should know about? If not, why would BSD or Hurd appeal to me?

---

### Post by hanzomon4 on 2009-08-30
BSD has a stable api(correct) but linux innovates faster. The Hurd is a lost cause but, the way I understand it, is more modular. It's like things like networking, drivers.. are not built into the kernel but act as like servers that are separated from each other. As a result if one dies or acts stupid it doesn't screw with everything else. That could be really wrong as I am not a computer coder devy person

---

### Post by keiichidono on 2009-08-30
> **hanzomon4 said:**
> BSD has a stable api(correct) but linux innovates faster. The Hurd is a lost cause but, the way I understand it, is more modular. It's like things like networking, drivers.. are not built into the kernel but act as like servers that are separated from each other. As a result if one dies or acts stupid it doesn't screw with everything else. That could be really wrong as I am not a computer coder devy person

Who needs stability when you have innovation? Sounds like Linux is better?

---

### Post by schauerlich on 2009-08-30
BSD is a whole 'nother operating system. It's not as simple as trading out kernels. I suggest wikipedia and [this article](http://www.over-yonder.net/~fullermd/rants/bsd4linux/bsd4linux1.php) as a good place to start learning if you're interested.

Hurd will never be finished, and if it is, it will suck.

EDIT:

> **CalvinB said:**
> Who needs stability when you have innovation? Sounds like Linux is better?

People who need to keep their computers running without it crashing?

---

### Post by hanzomon4 on 2009-08-30
> **CalvinB said:**
> Who needs stability when you have innovation? Sounds like Linux is better?

Well think about servers... they need stability reliability first, not that linux isn't good for servers. Nothing is really better when you compare world classes OS. It really depends on the task user.

---

### Post by keiichidono on 2009-08-30
> **EDavidBurg said:**
> BSD is a whole 'nother operating system. It's not as simple as trading out kernels. I suggest wikipedia and [this article](http://www.over-yonder.net/~fullermd/rants/bsd4linux/bsd4linux1.php) as a good place to start learning if you're interested.

Hurd will never be finished, and if it is, it will suck.

EDIT:



People who need to keep their computers running without it crashing?
Great link my friend. Explains everything very cleanly. But one thing.

> On the other hand, I have BSD systems that I installed in 1997, which have always been kept (and still are today) up with the latest kernel and the latest version of Apache and the latest Mozilla and the latest everything. With a Linux system, however, you tend to find yourself trying to keep a handful of obvious things upgraded, while others get further and further behind, until eventually you just reinstall with the latest version to bring it up to date. Those methodologies appeal to rather different kinds of admins.

This is fixed by rolling release distro's like Arch, am i not correct? I intend on using Arch soon, so the real question is, would BSD still appeal to me if I'm using Arch?

> **hanzomon4 said:**
> Well think about servers... they need stability reliability first, not that linux isn't good for servers. Nothing is really better when you compare world classes OS. It really depends on the task user.

Yeah, i was just thinking about that after i said it.

---

### Post by schauerlich on 2009-08-30
> **CalvinB said:**
> This is fixed by rolling release distro's like Arch, am i not correct? I intend on using Arch soon, so the real question is, would BSD still appeal to me if I'm using Arch?

Arch borrows a few concepts from BSD that I like - namely, installing a minimal "base" system (although the base system has a more formal definition in BSD lingo), and having a centralized /etc/rc system. Instead of a whole patchwork of symlinked daemons and config files in /etc/init, you have one file, /etc/rc.conf, to which you add any services you'd like to run on boot. Quite handy. My experience with Arch made my FreeBSD experience that much more familiar. BSD also has a linux compatibility layer (which is MUCH better than Wine; just about everything works with no performance penalty) if you're worried about software availability.

But really, what you want to try is up to you. Arch is much more familiar obviously as it is Linux based, and still operates the way you'd expect Linux to. FreeBSD is an entirely different *nix, similar in many respects, but not the same. I recommend any moderately experienced Linux user to dabble with FreeBSD. But don't go into it expecting to get an out-of-the-box desktop experience a la Ubuntu. Again, Arch is similar to FreeBSD in its design philosophy: keep the default as simple as it needs to be, and let the user go from there. Here's the parts, here's the tools, here's the documentation, now go build it.

If you're looking for a recommendation, here's mine: Try Arch. It'll give you a taste of something different. If you like it, play with it until you get bored. If you still like it, or you're ready for something just a bit more different, give FreeBSD a shot.

---

### Post by keiichidono on 2009-10-20
Arch is great, I'm just having geeky thoughts of other operating systems. I wonder if there's a resource that will give me a modern day blow by blow comparison of Linux (as an OS) to FreeBSD, and maybe even OpenSolaris. Open Solaris's cool ZFS stuff is being built with our ButterFS, FreeBSD's clean init and ports collection among other things have been taken by Arch Linux, there's no real benchmarks showing that FreeBSD is faster than any Linux (as an OS) or that Linux/OpenSolaris is faster than FreeBSD. 

I want to test FreeBSD/OpenSolaris on bare metal to make sure that I have a good perspective on where each operating system stands but at this time I don't really see any value besides peace of mind and geek cred.

---

### Post by RiceMonster on 2009-10-20
I don't think BSD is comparable to HURD, as it is actually useful, works, and has not been incomplete for 20 years.

> **CalvinB said:**
> Who needs stability when you have innovation? Sounds like Linux is better?

Because in many cases, reliability is most important.

---

### Post by slakkie on 2009-10-20
You might want to have a look here: [http://www.debian.org/ports/kfreebsd-gnu/](http://www.debian.org/ports/kfreebsd-gnu/)

Debian with a BSD kernel.

Having used FreeBSD myself for 6+ years.. It is a fun system to work on. Very very stable, although newer hardware is not always support which made me make the switch to Linux. But for servers it is a really nice OS.

It is like Gentoo with the ports collections (Gentoo kinda stole that idea from BSD), but you can also install binary packages. 

I have spent nights on getting my sound to work, compile my kernel, etc etc. Good fun :)

---

### Post by SunnyRabbiera on 2009-10-20
BSD is stable and secure, even more secure then linux.
BSD is especially great for servers because it has lots of decent stability.

---

### Post by starcannon on 2009-10-20
> **CalvinB said:**
> Is there a technical advantage of BSD variations and GNU Hurd over the Linux Kernel that i should know about? If not, why would BSD or Hurd appeal to me?
It always comes down to personal preference, correct tool for the job, and time to make it go zoom. Hurd is not really viable in my opinion, but BSD is an excellent choice for certain people doing certain tasks. I use Linux, specifically Ubuntu, because it does not require a huge initial investment of time from me to make it go. Don't forget there is also [BeOS]("http://www.haiku-os.org/") out there to pick from.

---

### Post by keiichidono on 2009-10-20
> **slakkie said:**
> You might want to have a look here: [http://www.debian.org/ports/kfreebsd-gnu/](http://www.debian.org/ports/kfreebsd-gnu/)

Debian with a BSD kernel.

Having used FreeBSD myself for 6+ years.. It is a fun system to work on. Very very stable, although newer hardware is not always support which made me make the switch to Linux. But for servers it is a really nice OS.

**It is like Gentoo **with the ports collections (Gentoo kinda stole that idea from BSD), but you can also install binary packages. 

I have spent nights on getting my sound to work, compile my kernel, etc etc. Good fun :)
Okay, I'll be sure to stay away from FreeBSD then. Thanks, this is all I needed to hear. Why didn't anyone tell me this in the first place.
> **starcannon said:**
> It always comes down to personal preference, correct tool for the job, and time to make it go zoom. Hurd is not really viable in my opinion, but BSD is an excellent choice for certain people doing certain tasks. I use Linux, specifically Ubuntu, because it does not require a huge initial investment of time from me to make it go. Don't forget there is also [BeOS]("http://www.haiku-os.org/") out there to pick from.
I'm keeping my eyes peeled while looking at Haiku. If you see my other thread in the cafe I'm think hard about it.

---

### Post by -grubby on 2009-10-20
> **CalvinB said:**
> Okay, I'll be sure to stay away from FreeBSD then.

So you're going to base your opinion of FreeBSD on a comparison somebody made in a forum post, instead of by trying it? Seriously?

---

### Post by slakkie on 2009-10-20
> **-grubby said:**
> So you're going to base your opinion of FreeBSD on a comparison somebody made in a forum post, instead of by trying it? Seriously?

Not only that, he completely overlooked the binary packages can be installed as well part. But let him, BSD will not become a lesser OS due to him not trying it :)

---

### Post by Giant Speck on 2009-10-20
> **-grubby said:**
> So you're going to base your opinion of FreeBSD on a comparison somebody made in a forum post, instead of by trying it? Seriously?

This one time, this guy told me that being social sucks, so I locked myself in the closet away from physical human contact.


I'm hungry.

---

### Post by schauerlich on 2009-10-20
> **Giant Speck said:**
> I'm hungry.

BACK IN YOUR CAGE.

You remember last time.

---

### Post by Giant Speck on 2009-10-20
> **EDavidBurg said:**
> BACK IN YOUR CAGE.

You remember last time.

I didn't escape.  I just said I was hungry.   :(

---

### Post by Hyporeal on 2009-10-20
The different technologies used in Linux, BSD, and the Hurd are interesting but not compelling to a desktop user. I like Ubuntu, but that doesn't mean that I like Linux more than BSD. It simply means that my preferred OS happens to use Linux as its kernel. If you're looking for a new OS, my advice is to try out a variety of distributions and see for yourself which one you like the most.

---

### Post by kpholmes on 2009-10-20
> **EDavidBurg said:**
> 

Hurd will never be finished, and if it is, it will suck.


HAHAHAHAHAA

> 
EDIT:



People who need to keep their computers running without it crashing?

+1, like my server

---

### Post by earthpigg on 2009-10-20
> **CalvinB said:**
> 
This is fixed by rolling release distro's like Arch, am i not correct? I intend on using Arch soon, so the real question is, would BSD still appeal to me if I'm using Arch?


Arch has nothing like the clear differentiation between it's "base" and additional installed packages that BSD has by default. this affects one when one upgrades his or her Arch system.

you can certainly configure pacman ***not*** to upgrade a certain set of packages that you choose to define as the system's "base", if you like, but it is not present by default.

perhaps next time i install Arch (if there is a next time), i will likely generate a plain-text list of packages included in the base install and make a script that tells pacman to upgrade everything *except* those packages. from there, i will add and remove things from that list as needed. 

many would consider a display manager as part of their own "Base" system that needs to be stable. so, those should/could/i-will-next-time-i-install would add GDM or their chosen display manager to the list-of-things-not-to-automatically-update. [http://wiki.archlinux.org/index.php/Gnome_2.28_Changes#Configuring_gdm_2.28](http://wiki.archlinux.org/index.php/Gnome_2.28_Changes#Configuring_gdm_2.28)

by doing that, i suppose one would have created a self-defined separation between what I consider "base-that-really-needs-to-be-stable" and "everything-else" that is kinda-sorta-similar to BSD's system.


on a somewhat unrelated note -- i hope that Ubuntu does something to keep GDM's graphical config utility in action. heck, i wouldn't object to a fork if that was what is needed. UDM :D

---

### Post by t0p on 2009-10-20
> **CalvinB said:**
> Okay, I'll be sure to stay away from FreeBSD then. Thanks, this is all I needed to hear. Why didn't anyone tell me this in the first place.

Because it's one person's opinion that no one else necessarily shares?

> **CalvinB said:**
> 
I'm keeping my eyes peeled while looking at Haiku. If you see my other thread in the cafe I'm think hard about it.

Jeez Louise!  If you really really want to know what an OS is like, install it on a partition on your computer.  Then you can decide for yourself if a particular OS is good for you or not.

You seem to be putting a bizarre amount of value on the opinions of random forum members.  If I say I think Arch is crap, will you say "OMG why didn't anyone tell me that before?" and remove it from your computer?  If I tell you Windows 95 is better than BSD, will you become a fan of appalling outdated OSes?  Try things out for yourself!  Form opinions of your own!  Use DSL for everything!

---

### Post by Mateo on 2009-10-20
to be l33t.  it's really the only reason.

---

### Post by keiichidono on 2009-10-20
I wasn't too serious about not trying out FreeBSD, I'm downloading it in a few minutes along with Fedora 12 beta. I'm too much of a geek to resist and I'll never be able to sleep if I don't try it now.

> **Hyporeal said:**
> The different technologies used in Linux, BSD, and the Hurd are interesting but not compelling to a desktop user. I like Ubuntu, but that doesn't mean that I like Linux more than BSD. It simply means that my preferred OS happens to use Linux as its kernel. If you're looking for a new OS, my advice is to try out a variety of distributions and see for yourself which one you like the most.

I like the way you say it. I mainly just want to know if FreeBSD/OpenSolaris is going to be useful for me on the desktop. I don't care if a system running FreeBSD has been running since 1954 and is the only computer keeping the internet up. I just want something as good as or better than Linux to test out. I'm not a distro-hopping person. I just like new tech.

---

### Post by slakkie on 2009-10-20
> **t0p said:**
> Because it's one person's opinion that no one else necessarily shares?


You don't have to believe me.

However:
[http://www.gentoo.org/main/en/about.xml](http://www.gentoo.org/main/en/about.xml)
> 
He was impressed. He found a BSD-style ports system.


I never used Gentoo, but what I know from it is that emerg --sync sounds a lot like cvsup -g <more params> /etc/supfile.ports and that emerge packagename is the same as cd /usr/ports/<catagory>/<sub-catagory>/packagename; make depend all install clean.

And also their emerge -Du world sounds a lot like the make world one would execute on FreeBSD. To me, it sounds like Gentoo saw what FreeBSD did and copied some of the principles. 

Another source:
[http://distrowatch.com/table.php?distribution=gentoo](http://distrowatch.com/table.php?distribution=gentoo)
> 
Portage is a true ports system in the tradition of BSD ports 


You don't have to agree with me or believe me, but just saying the obvious as an ex-BSD user. Gentoo looks a lot like BSD in that way. Compile from source via the ports. AFAIK Gentoo does not allow installation of binary packages, which BSD does offer.

BTW, since you (TS) also mentioned Hurd, you might want to have a look at Minix, which is a also a micro-kernel.

---

### Post by handy on 2009-10-20
The short answer is that BSD works.

Hurd probably never will.

I have used FreeBSD, its great.

I currently use FreeNAS which is absolutely brilliant.

---

### Post by keiichidono on 2009-10-20
> **handy said:**
> The short answer is that BSD works.

Hurd probably never will.

I have used FreeBSD, its great.

I currently use FreeNAS which is absolutely brilliant.

But WHY is FreeBSD "great"? :|

---

### Post by Bachstelze on 2009-10-20
> **slakkie said:**
> AFAIK Gentoo does not allow installation of binary packages, which BSD does offer.

It has a binary version of the biggest packages, like openoffice and firefox (and of course, the apps for which the source is not available are distributed as binary packages only).

> **CalvinB said:**
> But WHY is FreeBSD "great"? :|

Just try it out and see for yourself whether you like it or not...

---

### Post by schauerlich on 2009-10-20
> **CalvinB said:**
> But WHY is FreeBSD "great"? :|

You have three choices:

1) Google a review
2) Try it yourself and form your own opinion
3) Wait around for someone to tell you what they think

---

### Post by keiichidono on 2009-10-20
I finished trying out Fedora 12 beta, it was slow as a snail. Fedora 11 was like this too. Time to try FreeBSD while I google reviews.

---

### Post by Simian Man on 2009-10-20
> **CalvinB said:**
> I finished trying out Fedora 12 beta, it was slow as a snail. Fedora 11 was like this too. Time to try FreeBSD while I google reviews.

Keep in mind that beta versions of Fedora, unlike most distributions, ship executables with debugging symbols present which hurts performance a little bit.  So the pre-release versions will be slower than the actual release.

---

### Post by keiichidono on 2009-10-20
Fedora 11 was slow too. It was the final release. I'm making sure to use FreeBSD 7.2 and not 8.0.

---

### Post by kk0sse54 on 2009-10-20
> **CalvinB said:**
> Fedora 11 was slow too. It was the final release. I'm making sure to use FreeBSD 7.2 and not 8.0.

From what I've experienced Freebsd 8.0 is faster and to my knowledge any debugging symbols were removed with the release of RC1. It still remains a release candidate though.

---

### Post by keiichidono on 2009-10-20
> **C!oud said:**
> From what I've experienced Freebsd 8.0 is faster and to my knowledge any debugging symbols were removed with the release of RC1. It still remains a release candidate though.

Can you cite your source for the debugging symbols being removed in RC1?

---

### Post by kk0sse54 on 2009-10-20
> **CalvinB said:**
> Can you cite your source for the debugging symbols being removed in RC1?

/usr/src/UPDATING and if you really want it [http://groups.google.com/group/mailing.freebsd.current/browse_thread/thread/ecf27a12eea4b752](http://groups.google.com/group/mailing.freebsd.current/browse_thread/thread/ecf27a12eea4b752)

---

### Post by Bachstelze on 2009-10-20
> **C!oud said:**
> /usr/src/UPDATING

I still see the note about the debugging options affecting performance, nothing about them having been removed. That being said, I didn't see any difference betwwen 7 and 8, and I switched to 8 before RC1 anyway.

*EDIT: the notice is not there anymore after a source update. It was removed on Sep 30th, nine days after RC1 was released.*

---

### Post by Sporkman on 2009-10-20
> **handy said:**
> The short answer is that BSD works.


So does Ubuntu Server!

Except you don't need to spend hours reading a manual to install it. ;)

---

### Post by keiichidono on 2009-10-20
FreeBSD 8.0 it is then.

---

### Post by kk0sse54 on 2009-10-20
> **Bachstelze said:**
> I still see the note about the debugging options affecting performance, nothing about them having been removed. That being said, I didn't see any difference betwwen 7 and 8, and I switched to 8 before RC1 anyway.

*EDIT: the notice is not there anymore after a source update. It was removed on Sep 30th, nine days after RC1 was released.*

Perhaps I am wrong and I apologize if so but this here says that it was mostly removed on Sep 10 [http://svn.freebsd.org/viewvc/base?view=revision&revision=197065](http://svn.freebsd.org/viewvc/base?view=revision&revision=197065). Either way @OP just make sure it's turned off ;)

> So does Ubuntu Server!

Except you don't need to spend hours reading a manual to install it. 

Thank you for finding the need to interject such irrelevant comments in practically every thread even mentioning the word server let alone the word BSD especially in referencing quotes out of context.

---

### Post by Bachstelze on 2009-10-20
> **Sporkman said:**
> So does Ubuntu Server!

Except you don't need to spend hours reading a manual to install it. ;)

Have you ever installed FreeBSD, or are you just trying to be funny?

---

### Post by RiceMonster on 2009-10-20
> **Sporkman said:**
> So does Ubuntu Server!

Except you don't need to spend hours reading a manual to install it. ;)

God forbid anyone recommend anything other than Ubuntu for a server OS!

---

### Post by Bachstelze on 2009-10-20
> **C!oud said:**
> Perhaps I am wrong but this here says that it was mostly removed on Sep 10 [http://svn.freebsd.org/viewvc/base?view=revision&revision=197065](http://svn.freebsd.org/viewvc/base?view=revision&revision=197065). Either way @OP just make sure it's turned off ;)

I was talking about the notice in UPDATING, I haven't investigated about when the debug symbols were actually removed. That explains why I haven't seen any performance impact, though, I upgrade to 8 around the 15th.

---

### Post by DeadSuperHero on 2009-10-20
> **Sporkman said:**
> So does Ubuntu Server!

Except you don't need to spend hours reading a manual to install it. ;)

Actually, the manual is pretty much FreeBSD's equivalent to going to the UF for answers about hardware and software related issues, except it's much more accurate. 

You only read the manual WHEN you need it. You probably spent just as many hours asking questions about Ubuntu Server when you first needed to set it up.

---

### Post by Sporkman on 2009-10-20
> **Bachstelze said:**
> Have you ever installed FreeBSD, or are you just trying to be funny?

I tried it in virtual box a year or two ago - it crashed or something. I remember trying it more recently in some context, but the disk partitioner was cryptic & unusable.

---

### Post by recluce on 2009-10-20
We have been using FreeBSD in an ISP setting since about 1997 (if memory serves), initially just because the cost of Sparc machines hurt too much and SCO was a pain in the posterior even then. I believe we started out with FreeBSD 2.1 or something like that.

Today, we are still using FreeBSD for almost all server applications, but not a single desktop machine runs FreeBSD.

The reasons we like FreeBSD so much on our servers:

- Uptime can be measured in years. We had a few, low impact systems, that logged more than three years uptime before we had to do something to them

- FreeBSD behaves better under extreme I/O and memory loads

- FreeBSD has a very stringent release policy, which is bad if you need the latest hardware to work, but great for a stable server environment

- BSD incorporates a very solid security policy, which helps in an ISP environment

Mind you, the differences between, for example, Debian and FreeBSD will not be all that enormous, it is just that little extra "edge" that has kept us with FreeBSD for server applications.

On the other hand, the desktops and notebooks run a mix of Ubuntu and Windows (yikes) with an occasional Mac thrown in...

---

### Post by Bachstelze on 2009-10-20
> **Sporkman said:**
> I tried it in virtual box a year or two ago - it crashed or something. I remember trying it more recently in some context, but the disk partitioner was cryptic & unusable.

This is a weak argument. Someone coming from Windows could tell you as much about the Ubuntu Server partitioner.

---

### Post by Sporkman on 2009-10-20
> **RiceMonster said:**
> God forbid anyone recommend anything other than Ubuntu for a server OS!

I won't be censored! :D

Though, I must admit, I certainly am a minority in advocating Ubuntu Server here on the arch/BSD/Debian forums.

---

### Post by Sporkman on 2009-10-20
> **Bachstelze said:**
> This is a weak argument. Someone coming from Windows could tell you as much about the Ubuntu Server partitioner.

Sure, but had I persevered, I wouldn't have been able to proceed without looking up how to partition in the manual. Partitioning in Ubuntu is pretty straightforward when you simply want to use the whole disk.

---

### Post by handy on 2009-10-20
> **CalvinB said:**
> But WHY is FreeBSD "great"? :|

It installed easily & worked faultlessly, the ports package management system caused me no trouble.  The community though tiny in comparison to the Ubuntu community was very helpful, you just had to wait a little longer for an answer to a question on their forum than on a monster like this one.

The reason I moved on after a few months, was that I wanted to run Cedega (this was before I discovered the brilliant Codeweavers Crossover people who are SO much better than the Transgaming Cedega people) & play a particular game on that machine.

As far as the FreeBSD based FreeNAS is concerned; it is great because it is an installation that is absolutely dedicated to being the most efficient reliable, secure, easy to install & maintain (what maintenance?) NAS system (for free as well) that you can find.

FreeNAS IS absolutely brilliant!

**@CalvinB:** There is NO accounting for taste.  What suits one person is poison to someone else.  The wonder (in my mind at least) of the GNU, FOSS, Linux, BSD, Haiku, AROS & what have you world, is that it gives us so much freedom to explore, contribute, create & participate in development/usage/community, & for free as well (which is a real bonus & in the end makes it all possible).

---

### Post by handy on 2009-10-20
> **Sporkman said:**
> So does Ubuntu Server!

Except you don't need to spend hours reading a manual to install it. ;)

Install PC-BSD if FreeBSD presents an installation/experience problem.

PC-BSD is based on FreeBSD.

---

### Post by handy on 2009-10-20
> **Sporkman said:**
> I won't be censored! :D

Though, I must admit, I certainly am a minority in advocating Ubuntu Server here on the arch/BSD/Debian forums.

Ah! You are here to entertain & educate us with regard to chauvinism... :)

Good. 

As most of us need just that.

---

### Post by PurposeOfReason on 2009-10-20
> **Sporkman said:**
> Sure, but had I persevered, I wouldn't have been able to proceed without looking up how to partition in the manual. Partitioning in Ubuntu is pretty straightforward when you simply want to use the whole disk.
So is FreeBSD. Go to the partitioner and press a. Done. If you couldn't get that figured out, then you either quite before you started or really aren't observant.

---

### Post by slakkie on 2009-10-21
> **Bachstelze said:**
> It has a binary version of the biggest packages, like openoffice and firefox (and of course, the apps for which the source is not available are distributed as binary packages only).


From what I've read Gentoo only provides binary packages on installation media. I don't know Gentoo that well, so they may have changed that.

---

### Post by keiichidono on 2009-10-21
> **slakkie said:**
> From what I've read Gentoo only provides binary packages on installation media. I don't know Gentoo that well, so they may have changed that.

You've got it right. Gentoo is a source based distribution so they make you compile everything. I guess it's fun for Gentoo users.

---

### Post by handy on 2009-10-21
> **CalvinB said:**
> You've got it right. Gentoo is a source based distribution so they make you compile everything. I guess it's fun for Gentoo users.

If someone didn't enjoy it, Gentoo would not exist.

Personally I prefer my downloads to be mostly binary, but I'll leave that alone here. :)

---

### Post by gnomeuser on 2009-10-21
I ran FreeBSD (around the 5.0 beta days and beyond) for a number of years as a desktop, it feels like it has much better interactivity than Linux on my hardware and there is a solidity to the system that I like. I am not a big fan of ports, all that compiling seems counterproductive (but then again I did come from Gentoo to FreeBSD) and I kinda lack whole system updaters, precompiled kernels that will work on every setup and the things like that which I get from a Linux distro. Finally due to lacking manpower FreeBSD tends to be behind on things like HAL and now DeviceKit-* which makes the desktop a lot less useful.

FreeBSD has also managed to create some interesting appliances, FreeNAS and m0n0wall are good examples of things that work consistently well and provide a good experience. I really do enjoy when I can install something, put it in the corner and just have it do what I expect without constant babysitting.

The biggest argument for me to use BSD right now is getting away from the GPL and the FSF fanboys especially. I'm growing increasingly worried about the fundamentalism in Linux today, especially from new users who seem to deem that everything should be about defeating the great evil and not about producing great technology. The license itself is preventing adoption of technology (recent examples: zfs, dtrace, grand central dispatch) which might have been useful and which now are being duplicated in an incompatible manner (though occasionally improved, btrfs e.g.).

---

### Post by handy on 2009-10-21
> **gnomeuser said:**
> 
FreeBSD has also managed to create some interesting appliances, FreeNAS and m0n0wall are good examples of things that work consistently well and provide a good experience. I really do enjoy when I can install something, put it in the corner and just have it do what I expect without constant babysitting. 

From experience (well FreeNAS anyway) I'm with you all the way on that .

> **gnomeuser said:**
> 
The biggest argument for me to use BSD right now is getting away from the GPL and the FSF fanboys especially. I'm growing increasingly worried about the fundamentalism in Linux today, especially from new users who seem to deem that everything should be about defeating the great evil and not about producing great technology. The license itself is preventing adoption of technology (recent examples: zfs, dtrace, grand central dispatch) which might have been useful and which now are being duplicated in an incompatible manner (though occasionally improved, btrfs e.g.).

I personally love what the FSF stands for.  I understand that it only exists (& I agree with you that it is extreme) to counter the extremes of what these days we call corporate greed (the shareholder).

I also agree with you that fan-boy-ism of any kind is biased & therefore a problem.

(I think my above generalisations of your thoughts are accurate, I'm sure you will let me know if I have misinterpreted you?)

I also agree that it is nice to have somewhere else to go IF, Linux for whatever reason turns to s**t.  BSD is a great option. 

There are fortunately other options as well.


The FSF, GNU & the GPL, only exist due to the existence of closed source software.  Closed source is what created these organisations, without closed source software the FSF, GNU & the GPL would not exist. (I know, I'm repeating myself:))

The reason the above organisations can & are seen as extreme, is because they have to be as extreme as it takes to counter the opposition.

All in all, I am so grateful to these people for fighting the fight for what is basically our freedom.

As previously stated; it is nice to have another license to go to, but boy if we are *forced* to go there we will really have suffered a huge (perhaps devastating) loss. (imho)

---

### Post by kk0sse54 on 2009-10-21
> **slakkie said:**
> From what I've read Gentoo only provides binary packages on installation media. I don't know Gentoo that well, so they may have changed that.

Gentoo offers binary packages for things like Firefox and OpenOffice, both in which can take some time to compile.

---

### Post by Bachstelze on 2009-10-21
> **gnomeuser said:**
> and I kinda lack whole system updaters, precompiled kernels that will work on every setup and the things like that which I get from a Linux distro.

There is now a binary updater for FreeBSD which lets you upgrade your base system without recompiling (of course not the ports, though). Also, the GENERIC kernel which gets installed with the system supports pretty much every common setup. You have to run a very obscure device for GENERIC to not support it.

---

### Post by K.Mandla on 2009-10-21
> **EDavidBurg said:**
> You have three choices:

1) Google a review
2) Try it yourself and form your own opinion
3) Wait around for someone to tell you what they think
Speaking to No. 2, the BSDs that I have tried I found quite attractive. Not in the aesthetic sense, but in the sense that they performed exceptionally well, were easy to customize and gave me no hardware issues. Any OS that does that gets at least one gold star in my book.

And since part of the discussion is about the Hurd, I thought I would mention this, if it hasn't been linked to already. 

[http://www.debian.org/ports/hurd/](http://www.debian.org/ports/hurd/)

I'm not in the business of defending Hurd, but my impression -- last time I read about it -- was that it wasn't so much unusable. It just hadn't crossed that line of "stability on production machines" that everyone feels safer in. I might see if I can get it going, one of these days ... when I have some extra time ... :lol:

---

### Post by Sporkman on 2009-10-21
> **PurposeOfReason said:**
> So is FreeBSD. Go to the partitioner and press a. Done. If you couldn't get that figured out, then you either quite before you started or really aren't observant.

That was not at all apparent in that stage of the installation. Why don't they print "Just press 'a' if you want to partition the entire disk & move on" on the installation screen?

You know, winning the lottery is as simple as circling the correct 7 numbers on a small rectangular card. Done. ;)

---

### Post by RiceMonster on 2009-10-21
> **Sporkman said:**
> That was not at all apparent in that stage of the installation. Why don't they print "Just press 'a' if you want to partition the entire disk & move on" on the installation screen?

It's written in the handbook.

> **http://www.freebsd.org/doc/en_US.ISO8859-1/books/handbook/install-steps.html]If you want to use FreeBSD for the entire disk (which will delete all the other data on this disk when you confirm that you want sysinstall to continue later in the installation process) then you can press A, which corresponds to the Use Entire Disk option. [/quote]

[quote=Sporkman said:**
> You know, winning the lottery is as simple as circling the correct 7 numbers on a small rectangular card. Done. ;)

There isn't a handbook telling which 7 numbers to circle in the lottery

---

### Post by Sporkman on 2009-10-21
> **RiceMonster said:**
> It's written in the handbook.


Why can't they just put that on the screen? Why do I have to wade through a handbook just to do a basic install?

---

### Post by Bachstelze on 2009-10-21
> **Sporkman said:**
> Why can't they just put that on the screen? Why do I have to wade through a handbook just to do a basic install?

[img]http://img26.imageshack.us/img26/314/fbsd.png[/img]

---

### Post by Sporkman on 2009-10-21
> **Bachstelze said:**
> [img]http://img26.imageshack.us/img26/314/fbsd.png[/img]

That doesn't say that's sufficient, though - IIRC (not sure), it also talked about setting the root & swap partitions beforehand. And should you set it as bootable? Do I need to set the type or geometry?

I'm sure it seems straightforward to you, but when I see this screen, I think "I don't know what I'm doing, time to read the manual".

---

### Post by RiceMonster on 2009-10-21
> **Sporkman said:**
> I'm sure it seems straightforward to you, but when I see this screen, I think "I don't know what I'm doing, time to read the manual".

Which is very comprehensive. You're setting up a server, not your grand mother's computer. What's the problem?

---

### Post by Simian Man on 2009-10-21
> **Sporkman said:**
> That doesn't say that's sufficient, though - IIRC (not sure), it also talked about setting the root & swap partitions beforehand. And should you set it as bootable? Do I need to set the type or geometry?

I'm sure it seems straightforward to you, but when I see this screen, I think "I don't know what I'm doing, time to read the manual".

You lost man, give it up :).

---

### Post by Sporkman on 2009-10-21
> **RiceMonster said:**
> Which is very comprehensive. You're setting up a server, not your grand mother's computer. What's the problem?

Perhaps I'm spoiled by the very simple & straightforward installation process of the stable & powerful Ubuntu Server distro. ;) It wouldn't kill the freeBSD team to put a little effort into making a more intelligent & user friendly installer, IMO. Time is valuable, and if an easier installer can save users the time of doing research in the manual, then that's something.

I'll give freeBSD another try at some point.

---

### Post by bruno9779 on 2009-10-21
> **Sporkman said:**
> I won't be censored! :D

Though, I must admit, I certainly am a minority in advocating Ubuntu Server here on the arch/BSD/Debian forums.

:lolflag:

---

### Post by slakkie on 2009-10-21
> **Sporkman said:**
> That doesn't say that's sufficient, though - IIRC (not sure), it also talked about setting the root & swap partitions beforehand. And should you set it as bootable? Do I need to set the type or geometry?

I'm sure it seems straightforward to you, but when I see this screen, I think "I don't know what I'm doing, time to read the manual".

After that option you get another screen showing you the layout which you can change iirc.

---

### Post by keiichidono on 2009-10-21
Damn, FreeBSD is a deal harder to install than Arch Linux. No hand holding and they expect me to know everything. Not so bad, I'd just like something akin to the Begginers' Guide.

---

### Post by Bachstelze on 2009-10-21
> **CalvinB said:**
> Damn, FreeBSD is a deal harder to install than Arch Linux. No hand holding and they expect me to know everything.

That sums it up pretty well, actually. Before installing FreeBSD, you must have done your homework.

---

### Post by gnomeuser on 2009-10-21
> **Bachstelze said:**
> There is now a binary updater for FreeBSD which lets you upgrade your base system without recompiling (of course not the ports, though). Also, the GENERIC kernel which gets installed with the system supports pretty much every common setup. You have to run a very obscure device for GENERIC to not support it.


It's not so much that these tools aren't available but that they lack the completeness of something like yum + packagekit. I am happy to see that things are getting better though, FreeBSD is an amazing project and I have to admit being a sizable phk admirer.

---

### Post by Machnikowski on 2009-10-21
> **Sporkman said:**
> So does Ubuntu Server!

Except you don't need to spend hours reading a manual to install it. ;)

Well, if you're familiar with the workings of BSD, you don't need a manual. FreeBSD is (in a nutshell) more stable and secure than Ubuntu Server.

But, if you're a new with servers, Ubuntu or Arch may be a better choice, as they require less tweaking.

---

### Post by PurposeOfReason on 2009-10-21
> **Machnikowski said:**
> Well, if you're familiar with the workings of BSD, you don't need a manual. FreeBSD is (in a nutshell) more stable and secure than Ubuntu Server.

But, if you're a new with servers, Ubuntu or Arch may be a better choice, as they require less tweaking.
Arch on a server is just stupid IMO.

---

### Post by handy on 2009-10-21
> **PurposeOfReason said:**
> Arch on a server is just stupid IMO.

There is a different kernel & other packages available that make Arch more suitable than it would be otherwise as a server.

& there is this project dedicated to Arch as server also:

[http://arch-stable.wholebean.info/default.html](http://arch-stable.wholebean.info/default.html)

---

### Post by Sporkman on 2009-10-21
Ok, I gave the FreeBSD installation another go on an ancient Gateway laptop I had lying around.

It's only on CD1 so far, but I must say, I stand absolutely corrected - so far it's perfectly easy (and the installation screen right before the disk partitioner did indeed advise re the A + Q for using the whole disk)...

---

### Post by Sporkman on 2009-10-22
...done. Quite easy, actually, not sure why I had so much trouble previously.

Now the hard part: actually using it. For example, after logging in as myself, it wouldn't let me "su" - googled the solution, which I'll try tommorrow.

---

### Post by DeadSuperHero on 2009-10-22
> **Sporkman said:**
> ...done. Quite easy, actually, not sure why I had so much trouble previously.

Now the hard part: actually using it. For example, after logging in as myself, it wouldn't let me "su" - googled the solution, which I'll try tommorrow.

There are various things you can do, such as setting up su or sudo yourself, or just logging in as root in order to do the grunt work with configuring everything.

---

### Post by handy on 2009-10-22
I always set up sudo in Arch.

Probably because Ubuntu trained me to use it... :)

---

### Post by slakkie on 2009-10-22
> **Sporkman said:**
> ...done. Quite easy, actually, not sure why I had so much trouble previously.

Now the hard part: actually using it. For example, after logging in as myself, it wouldn't let me "su" - googled the solution, which I'll try tommorrow.

Add yourself to the wheel group.

---

### Post by earthpigg on 2009-10-22
> **handy said:**
> I always set up sudo in Arch.

Probably because Ubuntu trained me to use it... :)

ditto, except i've only installed arch once.

---

### Post by keiichidono on 2009-10-22
> **earthpigg said:**
> ditto, except i've only installed arch once.

I know, I was there.

---

### Post by handy on 2009-10-23
> **earthpigg said:**
> ditto, except i've only installed arch once.

I've set it up on more than one machine.

My initial Arch install from March 2008 is still going strong on the iMac.  Other's have come & gone on No.2. box though.

***[Edit:]**  Not because there were problems with them, just my playing around with different distros & such.*

---

### Post by andamaru on 2009-10-23
> **CalvinB said:**
> Who needs stability when you have innovation? Sounds like Linux is better?

I believe he is talking about a different kind of stability, I believe he is talking about the api

---

### Post by keiichidono on 2009-10-23
> **andamaru said:**
> I believe he is talking about a different kind of stability, I believe he is talking about the api

The API? :confused:

---

