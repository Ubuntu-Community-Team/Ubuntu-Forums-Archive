---
title: "Why is Ubuntu not in Debian Core Consortium"
date: 2005-07-22
forum: The Cafe
---

### Post by eewald on 2005-07-22
check this article: 
[http://www.eweek.com/article2/0,1895,1839578,00.asp](http://www.eweek.com/article2/0,1895,1839578,00.asp)

is see no debian-based ubuntu on this list, why isn't canonical participating?

---

### Post by kanem on 2005-08-06
I'm surprised there isn't more talk about this in these forums.

Just my opinion, but It seems that 
1) a consortium like this would move slowly.
2) Ubuntu could always make itself compatible with the consortium if and when it wants to.

Here's [an update on the Debian Consortium](http://www.eweek.com/article2/0,1895,1844684,00.asp).

Quoth the article:
> The DCCA (Debian Common Core Alliance) is an apt name. Sources within the Alliance said that "there will be a single set of packages, bit-identical to Debian Sarge in most if not all cases, that the participating distributions will share."

"So, there will be a tangible Debian Common Core that you can download, that you can base a distribution on, and that you can certify to if you are an ISV[independent software vendor] or an IHV [independent hardware vendor]." That seems all well and good, and if Ubuntu wanted to, they could also use this common core. However, this common core could have outdated things. If this consortium had existed a year ago and Ubuntu had joined, we would all still be using xfree. Also:

> The single largest player in the Debian Linux universe that won't be working with the alliance will be Ubuntu.

DCCA sources said that the Ubuntu Foundation and co-founder Mark Shuttleworth were approached about joining the Alliance, but the group expressed no interest in joining.

One DCCA supporter was upset by Shuttleworth's decision. "Rather than sit on the sidelines criticizing Debian, he should join with the others in the DCC alliance and help support and move Debian to a good place." Isn't it great when people try to tell a developer or philanthropist how they should volunteer their time or money?:rolleyes:

Anyway, I think this consortium is a good thing. But distros should still feel free to do what they want.

---

### Post by poofyhairguy on 2005-08-06
[QUOTE=eewald]
is see no debian-based ubuntu on this list, why isn't canonical participating?[/QUOTE]

PLEASE don't quote me on this, but I have the best answer I have found.

Prodigy Debian is a Debian spinoff created by Ian Murdock, the Debian founder (the last half of "debian" is his name). The Core Consortium is kinda dominated by the ideas and interests of Prodigy. To "work with" the consortium Ubuntu would have to adopt many parts of Prodigy the Ubuntu developers don't want. Things they feel are inferior.

This is kinda why Ubuntu does not follow the LSB- that is dominated by Red Hat ideas and concepts that Ubuntu doesn't want.

Plus Ubuntu kinda knows its the "big new thing" in the Debian world now, so it wants to lead not follow. In a few years the Consortium might be little more than something Ian uses to bash Ubuntu (he likes to bash Ubuntu, I say out of jealousy for getting the success he wanted Prodigy to have).

Thats the best I can tell.

---

### Post by az on 2005-08-06
"I'm surprised there isn't more talk about this in these forums."

Actually, that article is old news and mostly irrelevant.  So six guys had a meeting about standardizing their commercial offshoots of debian.  Big deal.

Debian developers deal with each other's projects and integrate them together on the source code level.  That is the common interface that they use together.  Striving to reach binary compatibility is of debateable importance.

This sort of project is of interest to a marginal group of companies that harvest the packages that are grown by debian.  Ubuntu is not about that.  In a way, Ubuntu is more about cultivating and making the soil better than just focusing on the crop.

---

### Post by az on 2005-08-06
"Prodigy Debian is a Debian spinoff created by Ian Murdock, the Debian founder (the last half of "debian" is his name). "

That's Progeny.  Like offspring.


"Things they feel are inferior."

Actually, just in another direction, I think.


"This is kinda why Ubuntu does not follow the LSB- that is dominated by Red Hat ideas and concepts that Ubuntu doesn't want."

dora@dora:~$ apt-cache show lsb
Package: lsb
Priority: extra
Section: misc
Installed-Size: 188
Maintainer: Chris Lawrence <lawrencc@debian.org>
Architecture: i386
Version: 2.0-1ubuntu2
Provides: lsb-core-noarch, lsb-core-ia32
Depends: lsb-base, lsb-release, xlibmesa3-gl | libgl1, xlibs, libz1, exim4 | mail-transport-agent, at, bc, binutils, bsdmainutils, cpio, cron, file, libc6-dev | libc-dev, locales, lpr, m4, make, man-db, mawk | gawk, ncurses-term, passwd, patch, pax, procps, psmisc, rsync, alien (>= 8.36), python (>> 2.2.2), debconf (>= 0.5) | debconf-2.0
Conflicts: python (>> 2.5), libutahglx1
Filename: pool/main/l/lsb/lsb_2.0-1ubuntu2_i386.deb
Size: 26554
MD5sum: a31e7f29d1e48a91373ca3e1b6ab36a5
Description: Linux Standard Base 2.0 core support package
 The Linux Standard Base ([http://www.linuxbase.org/](http://www.linuxbase.org/)) is a standard
 core system that third-party applications written for Linux can
 depend upon.
 .
 This package provides an implementation of version 2.0 of the Linux
 Standard Base for Debian on the Intel x86, Intel ia64 (Itanium), IBM
 S390, and PowerPC 32-bit architectures with the Linux kernel.  Future
 revisions of the specification and this package may support the LSB
 on additional architectures and kernels.
 .
 The intent of this package is to provide a best current practice way
 of installing and running LSB packages on Debian GNU/Linux.  Its
 presence does not imply that we believe that Debian fully complies
 with the Linux Standard Base, and should not be construed as a
 statement that Debian is LSB-compliant.
Bugs: mailto:ubuntu-users@lists.ubuntu.com
Origin: Ubuntu
Task: ubuntu-desktop

---

### Post by poofyhairguy on 2005-08-06
[QUOTE=azz]
Actually, just in another direction, I think.[/QUOTE]

Thats why I didn't want to be quoted.

> 
 The intent of this package is to provide a best current practice way
 of installing and running LSB packages on Debian GNU/Linux.  Its
 presence does not imply that we believe that Debian fully complies
 with the Linux Standard Base, and should not be construed as a
 statement that Debian is LSB-compliant.


Confused I am.

---

### Post by macgyver2 on 2005-08-06
Did anyone else find this to be a pretty darn funny pun...or am I just really tired?

[QUOTE=The article]The DCCA (Debian Common Core Alliance) is an apt name.[/QUOTE]
:):):)

---

### Post by TravisNewman on 2005-08-06
*L* Yeah I noticed that. I don't know if that was intentional or not ;)

---

### Post by npaladin2000 on 2005-08-07
That core consortium looks more like it's oriented toward creating an enterprise server standard.  And the core packages that they want to use are out of Sarge.  Problem in, in several ways, Sarge is already outdated.

It would be a mistake for Ubuntu to just hop in....Ubuntu is not an enterprise server distro; it's an enthusiast/desktop distro. Enterprise distros are like Debian, Red hat Enterprise Server, and SUSE/Novell Enterprise server: They give up using the latest/greatest thing for stability and the same software version has a MUCH longer life there.  That simply wouldn't work with Ubuntu, which stays close to current stuff with it's shorter 6 month release cycle.

Bascially Ubuntu is to Debian like Fedora is to RHEL and SUSE Pro is to Novell Enterprise Server: a testing ground for the more recent software that may eventually end up in the big server distro, while also serving as an excellent desktop OS due to it's number of current features.  Debian should really be treating Ubuntu in this way: as an extension of their testing/unstable classification. 

Honestly, it might be a mistake for Knoppix, Xandros, Linspire, and MEPIS to be involved too.  They may have a LOT of difficulty getting more current apps working with  the "common core" depending on the decided age of it. They're all desktop distros too, and using KDE 3.4 and GNOME 2.8 for the next year or so wouldn't sit well with their users most likely.  They probably just feel threatened by Ubuntu and are looking for a bandwagon to jump on. We'll have to see how this plays out, and exactly what these "core" pieces are.

---

### Post by Burgundavia on 2005-08-07
It is a mistake to consider Ubuntu just a hobbyist distro. Ubuntu is not Suse and Fedora Core. It is aimed at the 95% of computer users, your mom, dad, sister and cousin. With the enterprise release, it is also aimed at your family at work, either on the desktop or the server.

Corey

---

### Post by Knome_fan on 2005-08-07
> **npaladin2000]
It would be a mistake for Ubuntu to just hop in....Ubuntu is not an enterprise server distro said:**
> 
Nope.
> Ubuntu is a complete Linux-based operating system, freely available with both community and professional support.
[...]
Ubuntu is suitable for both desktop and server use.
 
[http://www.ubuntulinux.org/](http://www.ubuntulinux.org/)

[QUOTE=npaladin2000]
Enterprise distros are like Debian, Red hat Enterprise Server, and SUSE/Novell Enterprise server: They give up using the latest/greatest thing for stability and the same software version has a MUCH longer life there.  That simply wouldn't work with Ubuntu, which stays close to current stuff with it's shorter 6 month release cycle.

Nope.
> One driving factor behind the creation of the Foundation was the need to ensure that an Ubuntu release can be deployed on servers, which demand much slower release and upgrade cycles. "In order to support the use of free software on database and other servers, we will be offering security support for the Ubuntu base and major server components for a full five years", said Matt Zimmerman, CTO of the Ubuntu project.
[...]
The extended service support for Ubuntu version 6.04 will remain free of charge, under the same terms as the support currently provided to every release of Ubuntu. The extended service support program will only apply to designated releases of Ubuntu. Other releases, which will still be made on the current six-month cycle, will continue to receive the current commitment of 18 months free security and critical updates support.
 
[http://www.ubuntulinux.org/UbuntuFoundation](http://www.ubuntulinux.org/UbuntuFoundation)

[QUOTE=npaladin2000]
Bascially Ubuntu is to Debian like Fedora is to RHEL and SUSE Pro is to Novell Enterprise Server: a testing ground for the more recent software that may eventually end up in the big server distro, while also serving as an excellent desktop OS due to it's number of current features.  Debian should really be treating Ubuntu in this way: as an extension of their testing/unstable classification. 
[/quote]
As should have become obvious by now, this is not the case.

@azz:
Get a grip. There's no need to put down other projects just because you like Ubuntu.

---

### Post by az on 2005-08-07
"Get a grip. There's no need to put down other projects just because you like Ubuntu."

That I like Ubuntu has little bearing on what I criticise and what I priase.

---

### Post by Knome_fan on 2005-08-07
[QUOTE=azz]"Get a grip. There's no need to put down other projects just because you like Ubuntu."

That I like Ubuntu has little bearing on what I criticise and what I priase.[/QUOTE]

Let's just say, that's not the impression I get.

---

### Post by az on 2005-08-07
[QUOTE=Knome_fan]Let's just say, that's not the impression I get.[/QUOTE]

That's too bad.  Well, I still like *you*, though.

---

### Post by Knome_fan on 2005-08-07
[QUOTE=azz]That's too bad.[/QUOTE]
It is, isn't it?
Anyway, my point was that I would appreciate it if you as a mod would stop badvoicing other projects.
Wether or not my assumption that you did it because you liked Ubuntu is right or not is pretty immaterial to this point.

---

### Post by az on 2005-08-07
I said "marginal".  Oooooh!  What a strong insult!

A moderator can edit, move, delete or close posts and threads.  Are you saying that I use that privilege to railroad my opinion?  Surely not.

The fact that I spend my time helping the forums maintain a certain stardard by deleting swear words and spam does not preclude my expressing my opinion.  If you think I violate the code of conduct, take it up with my boss.

---

### Post by Knome_fan on 2005-08-07
[QUOTE=azz]I said "marginal".  Oooooh!  What a strong insult!
[/quote]
> This sort of project is of interest to a marginal group of companies that harvest the packages that are grown by debian. Ubuntu is not about that. In a way, Ubuntu is more about cultivating and making the soil better than just focusing on the crop. 
But I'll admit it. Wether it's an insult or just plain dumb is of course up for debate.

[QUOTE=azz]
A moderator can edit, move, delete or close posts and threads.  Are you saying that I use that privilege to railroad my opinion?  Surely not.
[/quote]
Not in this case, nope. 

[QUOTE=azz]
The fact that I spend my time helping the forums maintain a certain stardard by deleting swear words and spam does not preclude my expressing my opinion.  If you think I violate the code of conduct, take it up with my boss.[/QUOTE]
Feel free to express your opinion, I don't have any problem with that. But perhaps the next time around you should chose to do so in an informed, non-insulting and grown up way.

---

### Post by Stormy Eyes on 2005-08-07
[QUOTE=eewald]is see no debian-based ubuntu on this list, why isn't canonical participating?[/QUOTE]

Why should they? Committees are a waste of time when one wants to move quickly and get things done.

---

### Post by TravisNewman on 2005-08-07
Knome fan, you quote npaladin2000 about the 6 month release cycle, then say "nope" then quote an official doc saying that the 6 month release cycles are sticking around. I'm not sure what your "nope" was for, coult you elaborate?

Criticism of anything is welcome from anyone, including mods. You don't think mods should be able to speak freely about their opinions? I know you have criticized many projects yourself Knome fan, and there's nothing wrong with that. What we don't allow is bashing, which is a totally different story.

---

### Post by Knome_fan on 2005-08-07
[QUOTE=panickedthumb]Knome fan, you quote npaladin2000 about the 6 month release cycle, then say "nope" then quote an official doc saying that the 6 month release cycles are sticking around. I'm not sure what your "nope" was for, coult you elaborate?
[/quote]
Sure.
I was responding to him claiming Ubuntu wasn't an enterprise solution, which isn't true as Ubuntu is at least in the process of becoming one. Hence the five year security updates for designated releases that will only get updated every 18 months.

[QUOTE=panickedthumb]
Criticism of anything is welcome from anyone, including mods. You don't think mods should be able to speak freely about their opinions? I know you have criticized many projects yourself Knome fan, and there's nothing wrong with that. What we don't allow is bashing, which is a totally different story.[/QUOTE]
Again, I don't know how often I'm supposed to repeat it, I don't have any problem with mods critizising something, however we seem to disagree about what the difference between criticism and bashing is, as azz response comes at least very damned close to the latter imho.

---

### Post by TravisNewman on 2005-08-07
[QUOTE=Knome_fan]Sure.
I was responding to him claiming Ubuntu wasn't an enterprise solution, which isn't true as Ubuntu is at least in the process of becoming one. Hence the five year security updates for designated releases that will only get updated every 18 months.[/quote]

Right on, understood. Thanks.


> Again, I don't know how often I'm supposed to repeat it, I don't have any problem with mods critizising something, however we seem to disagree about what the difference between criticism and bashing is, as azz response comes at least very damned close to the latter imho.

Perhaps it would make things more clear if azz states why he feels that way?

---

### Post by Knome_fan on 2005-08-07
[QUOTE=panickedthumb]
Perhaps it would make things more clear if azz states why he feels that way?[/QUOTE]
This would be better than simply stating it.

However I get the impression it's not really clear why I reacted how I reacted, so let me try to clear this up.
First off, I don't have any problem with Ubuntu not joing this consortium. Though I personally think it is an interesting idea that doesn't mean it has to fit into the plans of Ubuntu.

Contrary to what azz seems to believe I don't have a problem with him calling the involved marginal, though I think putting your perceived opponent down this way is simply childish.

What I do have a problem with is him claiming that the companies and distributions involved simply "harvest the packages that are grown by debian." Whereas Ubuntu, in glaring contrast to those apparently "evil" companies is "cultivating and making the soil better than just focusing on the crop."

Now first off all, I don't really see how one can come to such a conclusion.
And finally, the irony is not lost on me that it is Ubuntu that is most often accussed nowadays of just harvesting the packages that are grown by debian.
I find this line of attack dumb and unfair in the case of Ubuntu and I don't really see why bashing others in the same way should make me like it more.

---

### Post by npaladin2000 on 2005-08-07
[QUOTE=Knome_fan]Sure.
I was responding to him claiming Ubuntu wasn't an enterprise solution, which isn't true as Ubuntu is at least in the process of becoming one. Hence the five year security updates for designated releases that will only get updated every 18 months.[/QUOTE]

Actually, the 6 month release cycle is what makes Ubuntu more of a desktop distro, not the length of time that you can get security updates.  As a rule desktop/hobbyist distros are updated much more frequently than enterprise server distros.  Kinda like how testing gets updated more than stable in Debian. ;) 

Companies don't want to see new versions of their enterprise server come out every 6 months and have to continually make the decision on whether or not to upgrade.  The 5 year security updates help...but remember, Windows 95 got 5 years of security updates.  Doesn't make it an enterprise server OS. ;)

---

### Post by az on 2005-08-07
I thought I was clear.


"Contrary to what azz seems to believe I don't have a problem with him calling the involved marginal, though I think putting your perceived opponent down this way is simply childish."

Opponent?  I said they are in a differnet direction.  In what way does that imply a fight?


"What I do have a problem with is him claiming that the companies and distributions involved simply "harvest the packages that are grown by debian." Whereas Ubuntu, in glaring contrast to those apparently "evil" companies is "cultivating and making the soil better than just focusing on the crop."

Now first off all, I don't really see how one can come to such a conclusion.
And finally, the irony is not lost on me that it is Ubuntu that is most often accussed nowadays of just harvesting the packages that are grown by debian.
I find this line of attack dumb and unfair in the case of Ubuntu and I don't really see why bashing others in the same way should make me like it more."

You are being clever, but you are wrong.  The few debian developers who have had complaints about Ubuntu have complained about the way in which the patches were reintegrated into debian.  This is a completely different involvement than organisations which stand by, tapping their feet complaining that the Sarge release is taking too long and this is causing them to lose their customers.

Contrast this to the philosophy of not charging for Ubuntu as well as pouring ressources into building tools such as launchpad to make it easier to recruit and involve more developers to open source.   Ubuntu is about furthering free software a lot more than about building a distro atop debian packages.


Ubuntu is destinct from Progeny in fundamental ways.

---

### Post by Knome_fan on 2005-08-07
[QUOTE=npaladin2000]Actually, the 6 month release cycle is what makes Ubuntu more of a desktop distro, not the length of time that you can get security updates.  As a rule desktop/hobbyist distros are updated much more frequently than enterprise server distros.  Kinda like how testing gets updated more than stable in Debian. ;) 

Companies don't want to see new versions of their enterprise server come out every 6 months and have to continually make the decision on whether or not to upgrade.  The 5 year security updates help...but remember, Windows 95 got 5 years of security updates.  Doesn't make it an enterprise server OS. ;)[/QUOTE]
Apparently I wasn't really clear, but from what I understand Ubuntu will offer an enterprise release that will only be updated every 18 months and will get security updates for 5 years. The 6 months release cycle will stay though for the "normal" desktop release.

---

### Post by npaladin2000 on 2005-08-07
[QUOTE=Knome_fan]Apparently I wasn't really clear, but from what I understand Ubuntu will offer an enterprise release that will only be updated every 18 months and will get security updates for 5 years. The 6 months release cycle will stay though for the "normal" desktop release.[/QUOTE]


Hmm...then for the enterprise release it would make sense to be paqrt of the DCC.  But only for that.  Maybe the reason Ubuntu isn't involved yet is because the enterprise distro isn't ready yet?

Then again, maybe Debian, Ian, and company are having a hissy fit because of Ubuntu's popularity and figure keeping it out is a way to take it down a notch.  Who knows?

---

### Post by Knome_fan on 2005-08-07
[QUOTE=azz]I thought I was clear.


"Contrary to what azz seems to believe I don't have a problem with him calling the involved marginal, though I think putting your perceived opponent down this way is simply childish."

Opponent?  I said they are in a differnet direction.  In what way does that imply a fight?
[/quote]
The way you took them on seems to suggest that you consider them opponents in some weird way.

[QUOTE=azz]
This is a completely different involvement than organisations which stand by, tapping their feet complaining that the Sarge release is taking too long and this is causing them to lose their customers.
[/QUOTE]
Ah, now I get it. This is what you think of as well funded critic not fud and bashing. Amazing, to say the least...

---

### Post by Knome_fan on 2005-08-07
[QUOTE=npaladin2000]Hmm...then for the enterprise release it would make sense to be paqrt of the DCC.  But only for that.  Maybe the reason Ubuntu isn't involved yet is because the enterprise distro isn't ready yet?
[/quote]
AFAIK they were approached and said they are not interested. This is purely speculation, but I get the impression canonical is currently in the process of building its own infrastructure, just take the foundation or launchpad as an example and so don't really see any benefit from joining this effort. Maybe they are also afraid that on the contrary, joining it would limit their flexibility.

[QUOTE=npaladin2000]
Then again, maybe Debian, Ian, and company are having a hissy fit because of Ubuntu's popularity and figure keeping it out is a way to take it down a notch.  Who knows?[/QUOTE]
As I said, from what I gathered reading stuff on the web they were asked to join. But I think you might be right about Ian not being the biggest fan of Ubuntu. (that is, he wrote some pretty silly stuff about Ubuntu)

---

### Post by az on 2005-08-07
[QUOTE=Knome_fan]
Ah, now I get it. This is what you think of as well funded critic not fud and bashing. Amazing, to say the least...[/QUOTE]

There should be an ammendment to the Code of conduct prohibiting the use of the word "FUD".  People who trow it around are usually proven ignorant.  It should be right up there with the word featured in this Ian Murdock weblog:
[http://ianmurdock.com/?p=168](http://ianmurdock.com/?p=168)

---

### Post by Knome_fan on 2005-08-08
[QUOTE=azz]There should be an ammendment to the Code of conduct prohibiting the use of the word "FUD".  People who trow it around are usually proven ignorant.  It should be right up there with the word featured in this Ian Murdock weblog:
[http://ianmurdock.com/?p=168](http://ianmurdock.com/?p=168)[/QUOTE]
LOL, how did I know that instead of answering you would start whining about me using the word FUD? But while I agree that the word is used way to often this doesn't mean that it doesn't apply here, does it?

Anyway, I'm really getting tired of this. 
If you think that spreading unsubstantiated FUD about other projects and bashing and insulting other projects is the right way to behave as a moderator there probably isn't anything I can do about it.

Anyway, you are merely embarassing yourself here, though it's of course unfortunate that someone who's happily trolling along is a moderator of the official Ubuntu forums, but I fear we'll have to live with that.

---

### Post by blakamin on 2005-08-08
[QUOTE=Knome_fan]
Anyway, you are merely embarassing yourself here, though it's of course unfortunate that someone who's happily trolling along is a moderator of the official Ubuntu forums, but I fear we'll have to live with that.[/QUOTE]
FWIW, I think that that last sentence is more trolling than anything else thats been said in this thread

---

### Post by Knome_fan on 2005-08-08
[QUOTE=blakamin]FWIW, I think that that last sentence is more trolling than anything else thats been said in this thread[/QUOTE]
Thanks.  :grin:

---

### Post by KiwiNZ on 2005-08-08
For obvious reasons I am locking this thread

---

### Post by poofyhairguy on 2005-08-10
So this thread doesn't end crappy like it did, I'm unlocking it because I found the biggest thing that Ubuntu doesn't like about the DCC. This:

[http://componentizedlinux.org/](http://componentizedlinux.org/)

> 
 What Is Componentized Linux?

Componentized Linux is a new way of constructing Linux distributions, built bottom-up as a set of interchangeable parts that closely track their counterpart "upstream" open-source projects, rather than top-down as a monolithic, difficult-to-change whole. The result is a platform for building specialized Linux distributions that provides developers with a set of reusable building blocks, called components, that can be easily assembled into a wide variety of configurations and customized as necessary. 

I don't blame the Ubuntu developers for not wanting that....

---

