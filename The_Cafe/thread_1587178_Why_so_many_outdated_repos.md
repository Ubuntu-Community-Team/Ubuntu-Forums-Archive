---
title: "Why so many outdated repos?"
date: 2010-10-03
forum: The Cafe
---

### Post by ki4jgt on 2010-10-03
I was just wondering how all these repos get out dated. I mean, FBreader has already fixed a lot of issues which the Ubuntu repos still have and have had for the last three releases. Yet, the users have to add FBreader's repos themselves to get these fixes. In the last distro Moovida wasn't current and wouldn't work with my computer. I don't know if it is now or not, but how do the repos work, that is if it's not top secret classified LOL

---

### Post by Paqman on 2010-10-03
> **ki4jgt said:**
> I was just wondering how all these repos get out dated.

Depends on who is responsible for the package. Generally speaking though, it's up to the devs to push their stuff to the repos.

---

### Post by aG93IGRvIGkgdWJ1bnR1Pw== on 2010-10-03
Because Ubuntu only upgrades their repos when a new version of Ubuntu is released, every 6 months. So most of the packages tend fo be 6 months out of date. If you don't like that, switch to a rolling release distro.

---

### Post by Tibuda on 2010-10-03
> **aG93IGRvIGkgdWJ1bnR1Pw== said:**
> Because Ubuntu only upgrades their repos when a new version of Ubuntu is released, every 6 months. So most of the packages tend fo be 6 months out of date. If you don't like that, switch to a rolling release distro.

This.

The most popular of those rolling-relase distors are Debian (testing and unstable) and ArchLinux. They are not as easy to install as Ubuntu, they are not harder than installing a minimal Ubuntu system. Some derivatives are easier like Chakra, ArchBang, Aptosid (formerly Sidux), and LinuxMint Debian Edition.

---

### Post by Spice Weasel on 2010-10-03
You need to check out:

[LIST]
[*]Fedora
[*]Debian Testing
[*]Aptosid
[*]Arch Linux
[*]PCLinuxOS
[*]Sabayon
[/LIST]

---

### Post by koenn on 2010-10-03
> **Paqman said:**
> Generally speaking though, it's up to the devs to push their stuff to the repos.

you sure ? 
i'd have thought the package maintainer tracks the development of the software he packages ....

---

### Post by Paqman on 2010-10-03
> **koenn said:**
> you sure ? 
i'd have thought the package maintainer tracks the development of the software he packages ....

A lot of the packages in Universe don't have a dedicated maintainer.

---

### Post by koenn on 2010-10-03
aren't those just (rebuilds of) Debian packages ?

---

### Post by cariboo on 2010-10-03
There are a lot of packages in the repositories that are umaintianed, they are included when a snapshot of the Debian unstable repositories is taken at the start of a new development cycle. Once the snapshot is taken, that is what we get unless a package has been updated before the feature freeze.

If a package scores highly in the [popularity contest]("http://http://popcon.ubuntu.com/by_inst"), it stays in the repositories, if it's popularity drops off, eventually it will be dropped

---

### Post by linux-hack on 2010-10-03
> **Spice Weasel said:**
> You need to check out:

[LIST]
[*]Fedora
[*]Debian Testing
[*]Aptosid
[*]Arch Linux
[*]PCLinuxOS
[*]Sabayon
[/LIST]

+ CentOS
+ OpenSUSE
+ FreeBSD
+ OpenBSD

---

### Post by del_diablo on 2010-10-03
> **cariboo907 said:**
> There are a lot of packages in the repositories that are umaintianed, they are included when a snapshot of the Debian unstable repositories is taken at the start of a new development cycle. Once the snapshot is taken, that is what we get unless a package has been updated before the feature freeze.

If a package scores highly in the [popularity contest]("http://http://popcon.ubuntu.com/by_inst"), it stays in the repositories, if it's popularity drops off, eventually it will be dropped

A bit better question:
Package is broken, bug reports are filed for Ubuntu, and there are forum threads.
Why does not a newer patched version arrive in the repos then, so that the problem gets fixed?

---

### Post by 23meg on 2010-10-03
> **del_diablo said:**
> A bit better question:
Package is broken, bug reports are filed for Ubuntu, and there are forum threads.
Why does not a newer patched version arrive in the repos then, so that the problem gets fixed?

If there's a known and tested fix, that usually happens either because the fix doesn't comply with the [stable release update criteria]("https://wiki.ubuntu.com/StableReleaseUpdates"), or in the case of Universe packages, there's nobody interested in and/or available for doing the work to prepare and upload a SRU.

---

### Post by 23meg on 2010-10-03
> **cariboo907 said:**
> There are a lot of packages in the repositories that are umaintianed, they are included when a snapshot of the Debian unstable repositories is taken at the start of a new development cycle. Once the snapshot is taken, that is what we get unless a package has been updated before the feature freeze.

By "unmaintained" you probably mean "not maintained by a particular person or group in Ubuntu".

If something is unmaintained upstream, it will usually be dropped from Debian, and consequently from Ubuntu, unless the Debian maintainer wants to take up the maintenance work. If the Debian maintainer drops a package, or is unreachable, it goes orphaned and is dropped from Debian, and again, from Ubuntu during the first semi-automated Debian sync period at the start of the development cycle, unless it's there's extraordinary need or demand for it in Ubuntu.

> **cariboo907 said:**
> If a package scores highly in the [popularity contest]("http://http://popcon.ubuntu.com/by_inst"), it stays in the repositories, if it's popularity drops off, eventually it will be dropped

Popcon data is not a binding rule on whether a package should stay in the archive, either in Ubuntu or in Debian. It's only looked at by maintainers on a per-package basis when evaluating whether it should be dropped, and it's just one data point, not a rule. A maintainer can decide to continue to maintain an unpopular package, and popular packages can be dropped for various reasons.

---

### Post by cariboo on 2010-10-03
I should have said not updated instead of unmaintained, there was a package I was trying to get dropped from the repositories because it hasn't been updated in 5 years, but there is still a Debian maintainer who does bug fixes. I was pointed to the the popularity contest data as one of the main reason why that particular package wouldn't be dropped.

---

### Post by ki4jgt on 2010-10-03
Well, like I said, FBreader has been missing the same upgrade since 9.04. The FBreader's repos program allows you to search for books and download them online, but the Ubuntu repos have yet to add this feature and the last I checked, fbreader was included with UNR.

---

### Post by cariboo on 2010-10-03
> **ki4jgt said:**
> Well, like I said, FBreader has been missing the same upgrade since 9.04. The FBreader's repos program allows you to search for books and download them online, but the Ubuntu repos have yet to add this feature and the last I checked, fbreader was included with UNR.

The UNR/UNE uses the same repositories as the regular versions. FBreader v. 0.10.7dfsg-3ubuntu1 is in the [maverick]("http://packages.ubuntu.com/search?keywords=fbreader&searchon=names&suite=maverick&section=all") repositories

---

### Post by forrestcupp on 2010-10-03
If you fill out a bug report to let them know that it needs to be updated, it will up the chances that it will get updated. ;)

That's one easy way that non-programmers can "give back".

---

### Post by snowpine on 2010-10-03
Ubuntu repos are "dated" not "outdated".

10.04 is the April 2010 repo
9.10 is the Oct 2009 repo
9.04 is the April 2009 repo
etc.

It is that simple, no top secret classified. :)

---

### Post by beew on 2010-10-04
> **snowpine said:**
> Ubuntu repos are "dated" not "outdated".



Same thing. I install almost all my non system softwares through PPAs. "Stability" means having the same old bugs for 3 years so you get to know them real well.:P

---

### Post by del_diablo on 2010-10-04
> **mgunes said:**
> If there's a known and tested fix, that usually happens either because the fix doesn't comply with the [stable release update criteria]("https://wiki.ubuntu.com/StableReleaseUpdates"), or in the case of Universe packages, there's nobody interested in and/or available for doing the work to prepare and upload a SRU.

In practical context this does mean that it will never get fixed.
That is my interpretation of it.
The exception might be a core part of GNOME, perhaps supercritical kernel bugs?

---

### Post by 23meg on 2010-10-04
> **del_diablo said:**
> In practical context this does mean that it will never get fixed.

No. As I said, it depends foremost on the severity of the bug, and the people available / interested in delivering the fix.

> **del_diablo said:**
> That is my interpretation of it.
The exception might be a core part of GNOME, perhaps supercritical kernel bugs?

Both the kernel and GNOME are part of the "main" component, which Canonical and the Ubuntu development community guarantee security and other critical operational updates for. Packages from the Universe component don't come with such a guarantee, thus updates are made available by the community on a best-effort basis.

See [http://www.ubuntu.com/project/about-ubuntu/components](http://www.ubuntu.com/project/about-ubuntu/components) for more information.

---

### Post by ssam on 2010-10-04
> **del_diablo said:**
> In practical context this does mean that it will never get fixed.
That is my interpretation of it.
The exception might be a core part of GNOME, perhaps supercritical kernel bugs?

no.

it just takes someone to find the patch that fixes the issue. check that it applies to the ubuntu version. make a debdiff that updates the changelog. file a stable release update report/bug. and get a few people to confirm that it fixes the issue and does not break anything. you don't need to be a programmer (but it helps) or an ubuntu dev to do this. have a read of the SRU wiki page.

there have been occasions in the past where an updated package in the stable ubuntu has broken things, so the level of testing required increased.

for getting a whole new version you generally just need to file a bug before the freeze (so too late for 10.10, but you'll be able to do it for 11.04 soon)

---

### Post by LowSky on 2010-10-04
> **beew said:**
> Same thing. I install almost all my non system softwares through PPAs. "Stability" means having the same old bugs for 3 years so you get to know them real well.:P

I use PPAs as much as possible for important software that Ubuntu falls beyond quickly or doesn't apply fixes for. MythTV, ALSA, and Nvidia come to mind right now.

---

### Post by del_diablo on 2010-10-04
> **ssam said:**
> for getting a whole new version you generally just need to file a bug before the freeze (so too late for 10.10, but you'll be able to do it for 11.04 soon)

Which again means: I am correct.
So if there is a package that just needs a new version to fix a MAJOR bug that snuck in with the freeze on 10.10, then it won't be fixed for that version.

mgunes: "Community best effort" tends to translate to "will never get fixed, but there is a PPA hidden somewhere for those who care."

---

### Post by snowpine on 2010-10-04
Del Diablo, you misunderstand how bug fixes work in most Linux distros (including Ubuntu).

Let's say you create an application called "deldiablo" (doesn't matter what this application does for purposes of our discussion). Ubuntu 10.10 releases October 2010 with version deldiablo-1.1-1 in its repositories.

In November 2010, a major bug is discovered and you release deldiablo-1.2 with the bug fix (and maybe a couple of new features). 

Does Ubuntu "backport" deldiablo-1.2 to the 10.10 repos? No! But they do take the code that fixes the bug, and they "patch" the version in the repositories as deldiablo-1.1-2 (for example).

In other words, you never get new features through regular updates. But you DO get bug fixes and security patches. Once an application has been ported to Ubuntu (or any other distro), the version numbers might not line up any more with the "upstream" release.

This comes up all the time in very stable distros like Red Hat (which has a 10-year support cycle). Red Hat currently uses kernel 2.6.18. This is a very old kernel, and you might assume that Red Hat users will have very unstable systems since they are missing out on all the bug fixes in kernels 2.6.19 through 2.6.35. But this is not true at all! The Red Hat kernel stays at 2.6.18 and is patched with the bug fix. I think they have published close to 200 kernel revisions to 2.6.18!

If you want to use a lot of PPAs, that is OK with me. I will mention that, based on my extensive experience on these forums, a large percentage of help requests are PPA-related. It is true that PPAs sometimes correct bugs, but they can also introduce new bugs. Those who stick to the official repositories seem to experience fewer update problems over the long term, in my observations.

---

### Post by beew on 2010-10-04
> Those who stick to the official repositories seem to experience fewer update problems over the long term, in my observations.

Sure, this sounds like the abstinence school of safe sex. :)

But if they stick to the official repo but still want feature updates (so instead of using version 1.* of program X in Ubuntu 8.04 while version 5.* is now avaliable) they would have to upgrade the whole system. This is a lot more risky.

---

### Post by 23meg on 2010-10-04
> **del_diablo said:**
> Which again means: I am correct.
So if there is a package that just needs a new version to fix a MAJOR bug that snuck in with the freeze on 10.10, then it won't be fixed for that version.

You seem to want to reach an absolute conclusion, but it really depends a lot on the nature of the bug, and the invasiveness of the patch. 

If it's a bug with a great distribution-wide impact in that it makes the system unusable for a significant amount of users, it will usually get fixed in the development branch no matter what. But if the impact is not deemed the possible risk of inadvertent damage so late in the cycle, the fix can be postponed to a SRU, since without proper testing, fixing one bug can easily introduce others.

> **del_diablo said:**
> mgunes: "Community best effort" tends to translate to "will never get fixed, but there is a PPA hidden somewhere for those who care."

You can translate it as you like, but that effort is undertaken by volunteers who are not paid, otherwise compensated or obligated to do the work that they do. As ssam said, anyone can submit a debdiff or prepare a branch to get a fix in; you don't need to be a developer or a member of any specific group, and if the patch is already out there it doesn't take a lot of technical work. If there's a specific fix which you think should be applied to a Universe package, and nobody is taking it up, consider having a go at [doing it yourself]("https://wiki.ubuntu.com/PackagingGuide/Complete#Creating a Debdiff").

---

### Post by koenn on 2010-10-04
> **beew said:**
> Sure, this sounds like the abstinence school of safe sex. :)

More like serial monogamy. 
Or: if you got a good thing going, dont f*ck around

I have a system that works. What do PPA's have to offer me that I don't already have ?

---

### Post by beew on 2010-10-04
> If it's a bug with a great distribution-wide impact in that it makes the system unusable for a significant amount of users, it will usually get fixed in the development branch no matter what. But if the impact is not deemed the possible risk of inadvertent damage so late in the cycle, the fix can be postponed to a SRU, since without proper testing, fixing one bug can easily introduce others.

But what if the program does not have wide distribution impact but it is important to some users? I am sure they won't take comfort in the wisdom that "when you fix one bug there is a theoretical risk that you will introduce others so do nothing". Medicine may have side effects, but few people would think as a* matter of principle* that they therefore shouldn't see a doctor unless it is life threatening.

---

### Post by beew on 2010-10-04
> **koenn said:**
> More like serial monogamy. 
Or: if you got a good thing going, dont f*ck around

I have a system that works. What do PPA's have to offer me that I don't already have ?

Yeah, but have potentially very messy break ups every 6 months. :)

---

### Post by snowpine on 2010-10-04
> **beew said:**
> Sure, this sounds like the abstinence school of safe sex. :)

A strange analogy. A better analogy is: your car leaves the factory with a certain list of parts that have all been tested to work well together. Some people hot-rod their cars by installing non-factory-tested replacement parts. If you are a good mechanic, then maybe your car performs better :) but if you are an average-at-best mechanic, there is an increased risk your car will break down :( (and good luck cashing in on your factory warranty).

> **beew said:**
> But if they stick to the official repo but still want feature updates (so instead of using version 1.* of program X in Ubuntu 8.04 while version 5.* is now avaliable) they would have to upgrade the whole system. This is a lot more risky.

If you stay current with Ubuntu releases, then you are typically using applications that are between 0 and 6 months old. Surely that is "new enough" for most users. 

I am not going to argue the fact that 8.04 (the April 2008 release) uses older applications. Of course it does.

---

### Post by 23meg on 2010-10-04
> **beew said:**
> But what if the program does not have wide distribution impact but it is important to some users? 

If you're talking about Universe packages, which such a package most likely is, then the possibility of introducing significant distribution-wide damage by fixing a bug in it is usually pretty low already (unless it depends on libraries in main which also need to be updated), so it can be fixed in place. In the case of freezes, the [MOTU Release Team]("https://launchpad.net/~motu-release") would be responsible from evaluating the eligibility of the fix.

> **beew said:**
> I am sure they won't take comfort in the wisdom that "when you fix one bug there is a theoretical risk that you will introduce others so do nothing". Medicine may have side effects, but few people would think as a* matter of principle* that they therefore shouldn't see a doctor unless it is life threatening.

It takes quite a leap of logic to go from "deliver the fix once the freeze is over and it's properly tested", to "do nothing". 

And to extend the medical metaphor, except in immediately life-threatening cases, few doctors would operate on a patient right away, without tests, consultation and possibly medication.

---

### Post by koenn on 2010-10-04
> **beew said:**
> Yeah, but have potentially very messy break ups every 6 months. :)

as someone pointed out already ; upgrades tend to be a lot messier for systems that run software/pathches from PPAs. 

If you're using PPAs to get some sort of "rolling release", you've picked the wrong distro, and you better have  an other computer standing by for when this one breaks.  


oh, and I do LTS. Fresh eye candy and higher version numbers are not a high priority to  me. So only have to deal with upgrades every few years, thank you.

---

### Post by beew on 2010-10-04
I think it comes down to a fundamental difference in philosophy. 

Some of us use computers basically to run softwares rather than to admire the OS, so it seems pointless to have a "stable" and secure system at the cost of not being able to run up to date softwares (with new features that enhance usability as well as bug fixes)

This is particularly relevant when we use mostly if not exclusively open source softwares as OSS typically have different developmental philosophy and cycles from commercial softwares. Commercial releases tend to be more polished, stable and have longer release cycles (you don't want to dish out a lot of $ to upgrade unless you have to) On the other hand OSS,-especially smaller ones that don't have "distribution wide impacts",--are more like projects in the making. They may be rough at the edges, more buggy at any one point and lack some crucial functionality, these drawbacks are remedied through community feed backs, a lot of beta releases and frequent updates. So if you use the commercial software model to manage open source apps you will probably miss out on a lot of necessary enhancements and not just the frills.

At least to me it seems upside down to tailor one's software need based on the OS.

---

### Post by beew on 2010-10-04
> **koenn said:**
> as someone pointed out already ; upgrades tend to be a lot messier for systems that run software/pathches from PPAs. 


I don't know about this. I just did an experiment upgrading Lucid to Maverick with a fresh installation of Lucid. Well there was no PPAs, only a Nvidia card and it was enough to break it completely. Now Maverick is a beta and the machine is also quite old, but the experience is not good.

Even if you don't have any PPAs chances are you may have a few proprietary drivers and it can cause problems. Well, unless you take the approach to only use open source drivers regardless how crappy the result is.

---

### Post by MasterNetra on 2010-10-04
If you want to keep your apps up to date in Ubuntu adding the getdeb repos is your best bet they may not turn Ubuntu to a rolling release but with your apps kept up to date, it will be the next best thing.

---

### Post by koenn on 2010-10-04
> **beew said:**
> I think it comes down to a fundamental difference in philosophy. 

Some of us use computers basically to run softwares rather than to admire the OS, ... 

Some of us use computers basically to do real work, rather than to feel good about having all te latest versions ...


The rest of you post isn't too bad, you're beginning to make sense. Too bad you had to ruin it with this snide remark.

---

### Post by beew on 2010-10-04
snowpine

> If you stay current with Ubuntu releases, then you are typically using applications that are between 0 and 6 months old. Surely that is "new enough" for most users.

First of all I am using a LTS (lucid) so I can run into a situation of being stuck with 3 year old softwares down the road if I don't use PPAs.

Now is 0 -6 months "new enough"? It depends on the software. There is a thread in the education forum where some guy couldn't run a mathematical software because of a fatal bug and the fixed version is availiable only in a PPA and Maverick's repo. Well maybe Octave doesn't have "distribution wide impact" and who cares about math? But if you need it you are in a bind. 

Another example, when I installed Lucid back in June the document viewer (evince) was basically a piece of crap, it was extremely slow in even opening simple PDFs and rendered pictures very poorly so I basically gave up on it and installed Foxit instead. A few months later I was playing with Maverick and I was shocked to discover how fast it is now and how polished the rendering has become. I realized that by using Lucid's repos I have missed out on a whole bunch of upgrades in just a few months and these are not just frills, they go to the core of usability. So I have raid the Maverick repo to install the newest version in my Lucid box and use it as my default instead of Foxit. 

I happily took the risk because it is a truly impressive improvement,--and there was a problem when a library got upgraded but I have fixed it.

---

### Post by beew on 2010-10-04
> **koenn said:**
> Some of us use computers basically to do real work, rather than to feel good about having all te latest versions ...


Yeah tell the guy who uses Octave to do real work while the repo version crashes immediately after it starts, or people for whom openoffice took a minute to start because they only have version 2X in the Ubuntu repo (that was exactly the situation not too long ago so the web was full of tutorials for installing OO.O3 from PPAs)

---

### Post by snowpine on 2010-10-04
> **beew said:**
> First of all I am using a LTS (lucid) so I can run into a situation of being stuck with 3 year old softwares down the road if I don't use PPAs.

I think your choice of the word "stuck" gets to the heart of the matter. :) 

First of all, if you *choose* to use an older Ubuntu release, *you will not get the new features* of the current release. This is so obvious I see no point in arguing it.

Second, Ubuntu provides a stable, timed-release, non-rolling repository of software as a *starting point* for building your own ideal system. **You are not "stuck" with the default software that Ubuntu provides** and I think this is the point that gets missed in these recurring discussions. 

"Open source" means that **you** have final say over what goes on your computer, **you are never "stuck"**!

---

### Post by beew on 2010-10-04
> **snowpine said:**
> 

"Open source" means that **you** have final say over what goes on your computer, **you are never "stuck"**!

Exactly, short of switching to a rolling release or writing my own apps the best way to get unstuck is to use a lot of PPAs, which some people here disapprove because it may compromise "stability" (which is really a tautology, as I learn that in Ubuntu talk "stability" means doesn't change, rather than the commonly understood meaning that "your system doesn't crash". They are related but not but not the same concept. :))

---

### Post by koenn on 2010-10-04
> **beew said:**
> Yeah tell the guy who uses Octave to do real work while the repo version crashes immediately after it starts, or people for whom openoffice took a minute to start because they only have version 2X in the Ubuntu repo (that was exactly the situation not too long ago so the web was full of tutorials for installing OO.O3 from PPAs)

If my work depended on the speed with which an office suite loads, or on the availability of something like Octave, I'd have tested those extensively before committing to them or to the OS they run on.

---

### Post by snowpine on 2010-10-04
> **beew said:**
> Exactly, short of switching to a rolling release or writing my own apps the best way to get unstuck is to use a lot of PPAs, which some people here disapprove because it may compromise "stability" (which is really a tautology, as I learn that in Ubuntu talk "stability" means doesn't change, rather than the commonly understood meaning that "your system doesn't crash". They are related but not but not the same concept. :))

I think we basically agree with each other then. :)

If you re-read my post #25, I do not disapprove of PPAs at all, merely observing that many ubuntuforums support requests are PPA-related. I see these help requests every single day: for example the user has added a PPA for the wrong release, or created "malformed syntax" in /etc/apt/sources.list, or failed to import the GPG key, or the PPA is no longer being maintained, etc.

It is also worth clarifying that PPAs are the **not** only way to get newer applications. "I do not personally use PPAs" does not automatically imply "I don't know how to install the 'upstream' applications of my choice." ;)

---

### Post by koenn on 2010-10-04
> **beew said:**
> Exactly, short of switching to a rolling release or writing my own apps the best way to get unstuck is to use a lot of PPAs, which some people here disapprove because it may compromise "stability" (which is really a tautology, as I learn that in Ubuntu talk "stability" means doesn't change, rather than the commonly understood meaning that "your system doesn't crash". They are related but not but not the same concept. :))

PPA's have a their role in providing patches/updates/ software versions that are not (yet) in the main release. We (or at least, I) are not despising PPA's as such, but the fact that you'd make them the norm (according to some of your comments throughout this thread) , with complete disregard of Ubuntu's change management processes. These exist, o.a., to avoid regression bugs and to minimize the risk of introducing new bugs. 



As for stability, we usualy use the adjective, 'stable', and the noun that goes with it actually matters. You're confusing a stable system with a stable release. Note that Ubuntu talks about LTS **release** - meaning that changes to it are managed, in a known and documented way, to make it behave predictably. 
In the real world, this is a good thing. If I'd have to recover a system from scratch, I like to know that if I reinstall the same release, I'll end up with a working system again, identical to the system I had before. 



Now, there is, imo, room for improvement in ubuntu's release cycle and on its the concept of a monolitic operating system, and PPA's are an interesting experiment in that respect.

But if your use cases require a rolling release distro, why arent' you using a rolling release distro ?

---

### Post by beew on 2010-10-04
> **koenn said:**
> 
But if your use cases require a rolling release distro, why arent' you using a rolling release distro ?

I am going to checkout Debian testing when I get around to, but I still like Ubuntu for its ease of use, the big and helpful community support and the wide availability of software. I do like Ubuntu in many ways, except for the outdated repos, but I have managed to keep my system updated by using PPAs. You are right that it is the norm for me and it has been working great.

> In the real world, this is a good thing. If I'd have to recover a system from scratch, I like to know that if I reinstall the same release, I'll end up with a working system again, identical to the system I had before.

Depends on what you do in the real world. In one of my jobs they use Windows XP, Office2003 and Firefox 3.5. The only things that are updated are some stat software that we actually use for work (but only those that require license renewals, for those that only ask for one time payment there hasn't been updates even if they are freely available) It is completely predictable but it would be a travesty if I run my own system like that.

---

### Post by del_diablo on 2010-10-04
> **mgunes said:**
> You seem to want to reach an absolute conclusion, but it really depends a lot on the nature of the bug, and the invasiveness of the patch. 

I do want to reach a absolute conclusion.
The main reason is that I am sick of tired of people not saying what things actually means. Or implying things are "working" when the actual questionnaires is questioning that.
Lets say major parts of the Kubuntu desktop is broken(has happened), and it would be solved by just upgrading the version number a bit.
I assume it is not even a universe package, which means that it should not have those bugs unfixed.

> If it's a bug with a _great distribution-wide impact_ in that it makes the system unusable for a significant amount of users, it will _usually_ get fixed in the development branch no matter what.

What can qualify for "great distrowide impact"?
I can only think of broken Firefox.
Flash, but that is again suppose to be broken.
Major GNOME components(which will never happen since it is the launch desktop, but it will be patched if something large enough slips trough).


> You can translate it as you like, but that effort is undertaken by volunteers who are not paid, otherwise compensated or obligated to do the work that they do. As ssam said, anyone can submit a debdiff or prepare a branch to get a fix in; you don't need to be a developer or a member of any specific group, and if the patch is already out there it doesn't take a lot of technical work. If there's a specific fix which you think should be applied to a Universe package, and nobody is taking it up, consider having a go at [doing it yourself]("https://wiki.ubuntu.com/PackagingGuide/Complete#Creating a Debdiff").

:P First argument is a strawman, due the nature of the project.
And yes, it could get patched like that, but when is that actually the case of actually happening? What happens is that a PPA is created, and the bug remains in the vanilla package.

Seriously, stop beating around the bush: The repozitary freeze over is Ubuntu's problem, and the project will have to find a way to fix it sooner or later.
Most applications do not suffer from it, as nothing tends to happen.
A few get new functionality, but that tends to not be significant.
But lets say THE GAME gets a new version after a few days of the new Ubuntu is out, THE GAME will be broken because its a online game, and thus: PPA's, which again ridicules the idea of having a working system.
PPA is suppose to be for stuff like Xorg Edgers, extremely weird stuff.
The moment a PPA gets used for "hey guyz, lets fix that 1 broken app", its broken.
And will be broken until its fixed.

---

### Post by snowpine on 2010-10-04
Del Diablo, respectfully, I think you are addressing your frustration in the wrong direction. ;) It sounds like the **real** problem here is not so much Ubuntu's 6-month cycle, but rather the number of serious bugs that end up in final Ubuntu releases. I would have to agree with you about that problem (though I disagree with your proposed solution). :)

My suggestion to you is learn about how different Linux distros handle releases, updates, and bug fixes. For example you might feel inspired to install a "rolling release" distro (like Arch) as a dual boot with Ubuntu. Use both for a couple of years and then you will have a good feel for the pros and cons of each method.

---

### Post by PhilGil on 2010-10-04
Just for the record, Debian Testing isn't a rolling release in the same sense as Arch. It works like this: After a stable release of Debian, Testing behaves like a rolling release. However, a few months before a new Stable release, Testing is "frozen" and behaves like a stable release -- only bug fixes are accepted; no new packages are added. Once the new Stable is released, a crap-ton of new/updated packages are dumped into Testing.

Right now, Debian Testing is frozen, so you won't be seeing anything but bug fixes for the next few months. The real rolling release in the Debian family is Unstable (Debian Sid) and its derivatives.

---

### Post by del_diablo on 2010-10-04
*rolleyes*
Non-ubuntu distro summary:
*Archlinux(due the setup its light and good, the disadvantage is that a lot of things are broken by default, but you are suppose to edit their configs by hand and fix it, but its quite good when its finally configured correctly)
*Fedora(package managent system does still have a few minor gripes around, but its neglishable. The 1 year cycle is superior to Ubuntu's, and there is a lot more patches going on under the hood. The disadvantage is more or less that some features get officially backported, and then abonded later on)
*Debian(more or less Archlinux, but it works, and the repos is several times larger. Got a stable rolling version, for those who want that)

Sorry to break it to you, but what is not ubuntu tends to get in proper fixes, in a different way. Ubuntu's only real advantage is the high markedshare, which means it will always get the needed .debs and the support.
Meanwhile lets wait for the Linux desktop to gain markedshare, so that "fixes" to obvious problems suddenly will become a issue.

---

### Post by 23meg on 2010-10-04
> **del_diablo said:**
> I do want to reach a absolute conclusion.
The main reason is that I am sick of tired of people not saying what things actually means. Or implying things are "working" when the actual questionnaires is questioning that.

OK, so here's your absolute conclusion: 

[list][*]Will every bug be fixed in Ubuntu before release? -> No.
[*]Will every bug be fixed *after* release? -> No.
[*]Will every bug fix be delivered immediately, regardless of impact, available workforce and potential of regressions? -> No. [/list]

Those are the extremely original, so far unheard of conclusions we can reach with the black-or-white logic that you demand. Anything more sophisticated and you need to look into the fine details of the matter, which you don't seem to have any interest in.

> **del_diablo said:**
> Lets say major parts of the Kubuntu desktop is broken(has happened), and it would be solved by just upgrading the version number a bit.
I assume it is not even a universe package, which means that it should not have those bugs unfixed.

Can you cite the specific case where that happened?

> **del_diablo said:**
> What can qualify for "great distrowide impact"?

The SRU policy wiki page I linked to earlier explains that in detail.

> **del_diablo said:**
> :P First argument is a strawman, due the nature of the project.

Why is it a straw man? Is Universe not taken care of by volunteers? 

> **del_diablo said:**
> And yes, it could get patched like that, but when is that actually the case of actually happening? 

[This]("https://bugs.launchpad.net/ubuntu/+bugs?field.searchtext=&orderby=-importance&field.status%3Alist=FIXRELEASED&assignee_option=any&field.assignee=&field.bug_reporter=&field.bug_supervisor=&field.bug_commenter=&field.subscriber=&field.component=3&field.component-empty-marker=1&field.tag=&field.tags_combinator=ANY&field.status_upstream-empty-marker=1&field.has_cve.used=&field.omit_dupes.used=&field.omit_dupes=on&field.affects_me.used=&field.has_no_package.used=&field.has_patch.used=&field.has_branches.used=&field.has_branches=on&field.has_no_branches.used=&field.has_no_branches=on&search=Search") is the list of 32427 fixed Universe bugs. I don't have a definitive metric at hand as to how many were SRUs, since [http://qa.ubuntuwire.com/sru/](http://qa.ubuntuwire.com/sru/) is temporarily out of order, but you should be able to figure out roughly by doing a search.

> **del_diablo said:**
> What happens is that a PPA is created, and the bug remains in the vanilla package.

How many cases of that happening can you point to? Surely if a fix is not eligible for a SRU, and someone is willing to do the packaging and create a PPA, it can be a way to deliver a fix, and can be resorted to at times, but when you speak of it as if it were the norm, that's simply inaccurate.

> **del_diablo said:**
> Seriously, stop beating around the bush: The repozitary freeze over is Ubuntu's problem, and the project will have to find a way to fix it sooner or later.

When you have a fixed conclusion in mind before even starting a discussion, every argument to the contrary is "beating around the bush", isn't it? For future reference, this is a great way to make people feel discussing with you was a waste of time.

---

### Post by del_diablo on 2010-10-04
> OK, so here's your absolute conclusion:

I disagree that is the conclusion. That is only the mere fact affecting about everything.
What I want people to realize is:
*There is a problem
*It is not been attempted to be solved yet, at the base of the problem
But again, only a miniscule % of people actually browse parts of the forum, which means debatting it is kind of a moot point. So the a fact could have been "don't bother to debate anything, not enough people get aware anyhow", but thats no fun is it :popcorn:

> Can you cite the specific case where that happened?

Not specific enough to be of help.
On the top of my head I can think of users complaining about last minutes pull on KDE, that essentially "broke" quite a bit of the desktop.
The closest thing I got to a source is more a bit of user complaint: [http://www.diskusjon.no/index.php?showtopic=401300&view=findpost&p=16254865](http://www.diskusjon.no/index.php?showtopic=401300&view=findpost&p=16254865)

> **mgunes said:**
> Why is it a straw man? Is Universe not taken care of by volunteers? 

The entire argument reallies on a twisted version of "Don't like it? Leave."
The actual argument that should be put forth should be: "Don't upstream and patch it yourself? Then enjoy.", which i find you to be sorely lacking.
[IMG]http://imgs.xkcd.com/comics/duty_calls.png[/IMG]
 

> How many cases of that happening can you point to? Surely if a fix is not eligible for a SRU, and someone is willing to do the packaging and create a PPA, it can be a way to deliver a fix, and can be resorted to at times, but when you speak of it as if it were the norm, that's simply inaccurate.

If the rate of getting PPA's to fix random issues is higher than actual patch rate, than the PPA is the norm in this comparison.
Simple broken debate logic.

> When you have a fixed conclusion in mind before even starting a discussion, every argument to the contrary is "beating around the bush", isn't it? For future reference, this is a great way to make people feel discussing with you was a waste of time.

It depends.
When a person debating starts deliberately ignoring points made, or refuse to acknowledge or to be able to acknowledge that the bush is a bit more complex, that is when a debate slows down.
Also, people define "the bush" differently, and that again is reflected in every used expression.
To  be honest, the actual conclusion regardless is: "Its broken, lets hope the project fixes it". 
The degree of brokenness varies, but is it there? If yes, its broken.
I can think of a few topics more that is more or less this constant, but its usually technology related. A debate on how to fix it would be interesting, but from what few times I have seen that in recursing, it usually dies of by proposing rolling.

My personal opinion on how they should fix it? I don't have one, I rather want to be amazed of their design choice if they actually fix it.

---

