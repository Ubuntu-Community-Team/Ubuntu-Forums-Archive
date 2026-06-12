---
title: "Is Ubuntu very buggy compared to Debian?"
date: 2014-01-15
forum: Ubuntu, Linux and OS Chat
---

### Post by Dáire Fagan on 2014-01-15
Hi

The time has come for me to fresh install three OS, the main of which I was intending to be Ubuntu. I was browsing YouTube videos and came across a lot of people comparing Ubuntu to Debian, which I know Ubuntu is based upon, and saying that they found every version of Ubuntu a bugfest whereas Debian is completely rock solid stable - although with slightly older software because of this. Much blame was attributed to Canonical allegedly insisting a new version is released every 6 months - ready or not. Thinking on it, I have encountered a lot of bugs in Ubuntu over many releases, even using LTS, and I am tempted by the idea of an OS with no bugs at all. That said, I very much enjoy support community Ubuntu offers, and I am also very much aware most linux guides outside of Ubuntuforums still seem to explain how to do things in Ubuntu rather than any other version of linux.

Just thought I would ask for the community's thoughts on this matter, and if any of you are running Ubuntu where you encounter absolutely no bugs, and everything just works?

For the included poll I am very much aware results from a Ubuntu website might be ever so slightly biased so please only vote if you have experience with both OS :P

---

### Post by tgalati4 on 2014-01-15
Every 6 months or so, Ubuntu is completely pulled apart (like a race car after a crash) and reassembled.  Sometimes the pieces don't fit.  Sometimes pieces are left over.  Sometimes the car won't start.  Usually the bugs are minor and are fixed quickly.  Sometimes a completely new framework is introduced which causes some problems.  Anyone remember *pulseaudio* when it was first introduced.

---

### Post by monkeybrain20122 on 2014-01-15
Which Debian? It is definitely not buggy comparing to Debian sid. SID is the buggiest distro ever for packaging bugs alone and it is not for end users.

 It may be more buggy comparing to debian stable but you have to compare orange with orange, there are trade offs for newer software.I lose my appetite right the way just by looking at how old and outdated things are in Debian stable. It is indeed rock solid, as in fossil. :) I would happily trade some "stability" for freshness.

P.S. I have put Ubuntu on numerous machines.Wouldn't say absolutely no bug, but all very minor and there are bugs with all OSes.

---

### Post by lykwydchykyn on 2014-01-15
I experience more bugs in Ubuntu, most often in the first couple months after the release.  It's not the worst experience I've ever had in a distro, not by far.
I've never had to regret putting Debian Stable on a server, though I can't say the same about Ubuntu LTS.  Debian isn't "bug-free", though; nothing is.

---

### Post by Jason_Gibson on 2014-01-15
Ubuntu pulls from Debian sid and whatever testing happens to be at the time. So naturally it will be a bit more buggy. There is a reason Debian stable is just that... stable. The software is old and well tested to all work together. I moved to Ubuntu from Debian stable for that reason, software is old and won't be updated for another year at minimum. They are using the 3.2 kernel. I don't know how fast kernel versions come out but we are at 3.12 I think now, and 3.2 released in stable in may of 2013 I believe. They are way behind. But again stable.

---

### Post by buzzingrobot on 2014-01-15
It's not possible to answer this in a meaningful way. Debian and Ubuntu take different approaches to meet different needs.

The way to reduce the number of bugs is to stop changing the code *except* for bug fixes. Do that and you will have fewer bugs. And, older software.

Ubuntu's non-LTS releases change more frequently than Debian Stable, which does not follow a fixed release schedule. By the time a Stable is released, no changes have been accepted for some time.

So, if you compare an Ubuntu LTS in month 59 to a Debian Stable in month one, you will see something different than if you compare a non-LTS on release day to a Stable that's one month from being superceded. 

In Debian-speak, "Stable" refers to the lack of change to the collection of software packages that make up the release. It isn't an assertion about the stability of any given piece of software.

---

### Post by monkeybrain20122 on 2014-01-15
> **buzzingrobot said:**
> 

In Debian-speak, "Stable" refers to the lack of change to the collection of software packages that make up the release. It isn't an assertion about the stability of any given piece of software.

Exactly. In Debian speak 'stability' has no implication for better performance, more reliable etc. It simply means 'never change'.  As software bugs tend to be fixed in new releases, being 'stable' in Debian speak doesn't even mean less buggy.  If something is already broken then Debian 'stability' simply means predictably broken.

---

### Post by lykwydchykyn on 2014-01-16
> **monkeybrain20122 said:**
> Exactly. In Debian speak 'stability' has no implication for better performance, more reliable etc. It simply means 'never change'.  As software bugs tend to be fixed in new releases, being 'stable' in Debian speak doesn't even mean less buggy.  If something is already broken then Debian 'stability' simply means predictably broken.

That may be true in a sense; but you can't dismiss the fact that Debian stable is released when *quality goals* are met (specificially, RC bugs are all closed), rather than releasing on an arbitrary date.  It isn't uncommon for Debian to just pull software from a release if it's non-critical and too buggy at release time.

---

### Post by buzzingrobot on 2014-01-16
> **lykwydchykyn said:**
> That may be true in a sense; but you can't dismiss the fact that Debian stable is released when *quality goals* are met (specificially, RC bugs are all closed), rather than releasing on an arbitrary date.  It isn't uncommon for Debian to just pull software from a release if it's non-critical and too buggy at release time.


Of course, the trade off is that you eventually release with reliable but less-than-current packages. This pleases people who do not want the features in the newer releases and displeases people who want those features and are willing to risk the bugs or who would not encounter them in the first place. 

Releasing to a fixed schedule no-matter-what seems unnecessarily rigid. 

Fedora has a release schedule, but famously is always delaying releases to fix problems. Bugs are ranked, more or less, as release blockers, nice-to-have fixes, and, in a sense, unfixable.  Eventually, a decision is made to annoint an RC as the release, with any remaining serious bugs listed on a "Common Bugs" page for that release.

I've always thought that's a reasonable approach.  Unless a distribution has some kind of obligation to meet a set release date, what's the compulsion to meet it at all costs?

---

### Post by monkeybrain20122 on 2014-01-16
> **buzzingrobot said:**
> Of course, the trade off is that you eventually release with reliable but less-than-current packages. This pleases people who do not want the features in the newer releases and displeases people who want those features and are willing to risk the bugs or who would not encounter them in the first place. 

Releasing to a fixed schedule no-matter-what seems unnecessarily rigid. 

Fedora has a release schedule, but famously is always delaying releases to fix problems. Bugs are ranked, more or less, as release blockers, nice-to-have fixes, and, in a sense, unfixable.  Eventually, a decision is made to annoint an RC as the release, with any remaining serious bugs listed on a "Common Bugs" page for that release.

I've always thought that's a reasonable approach.  Unless a distribution has some kind of obligation to meet a set release date, what's the compulsion to meet it at all costs?

Yeah, Fedora is very impressive in terms of being able to offer the latest yet at the same time very stable. There is no real 'freeze" as things get ongoing version updates after release (even kernel) so while it is a fixed release it is almost like rolling in terms of freshness (much more up to date out of the box than fake rolling releases like Debian testing or LMDE)

My take on Debian 'stability' is like: instead of taking a bus to the airport and fly to China let's do it the Marco Polo way. Buses and flights are complex things and therefore buggy. Don't believe me? Read the papers, there are plane crashes and highway accidents from time to time.

So the question of whether Ubuntu (or Arch or Fedora) is more buggy than Debian stable (which OP didn't specify) is not a meaningful question. It is comparing apple with orange. At best it doesn't take into account the context.

---

### Post by WBHyAz8 on 2014-01-16
Usually, whenever i install Ubuntu (specificly Lubuntu), It starts having errors and bugs after about two weeks of it running. But thats understandable, because i use the latest-greatest repository builds.

---

### Post by RichardET on 2014-01-16
> **dusf said:**
> Hi

The time has come for me to fresh install three OS, the main of which I was intending to be Ubuntu. I was browsing YouTube videos and came across a lot of people comparing Ubuntu to Debian, which I know Ubuntu is based upon, and saying that they found every version of Ubuntu a bugfest whereas Debian is completely rock solid stable - although with slightly older software because of this. Much blame was attributed to Canonical allegedly insisting a new version is released every 6 months - ready or not. Thinking on it, I have encountered a lot of bugs in Ubuntu over many releases, even using LTS, and I am tempted by the idea of an OS with no bugs at all. That said, I very much enjoy support community Ubuntu offers, and I am also very much aware most linux guides outside of Ubuntuforums still seem to explain how to do things in Ubuntu rather than any other version of linux.

Just thought I would ask for the community's thoughts on this matter, and if any of you are running Ubuntu where you encounter absolutely no bugs, and everything just works?

For the included poll I am very much aware results from a Ubuntu website might be ever so slightly biased so please only vote if you have experience with both OS :P


I don't believe for one second the notion Debian is "rock solid".  My old SPARC 64 works fine with OpenBSD and pretty much is a brick using Debian.
Ubuntu seems fine to me.

---

### Post by msdn70 on 2014-01-25
Hi

I'm totally new to Linux world, your above discussion is very interesting to me.
I have a question here.. Is it necessary if Debian have a bug this bug transferred to Ubuntu automatically (as Ubuntu built upon Debian)? 
If the answer is yes! then we can't compare both Debian and Ubuntu. but we can compare distros only.

Do you agree with me?

---

### Post by QIII on 2014-01-25
Hi!

No it is not necessarily the case that if there is a bug in Debian it will also be present in Ubuntu.  However, since many distros use many of the same packages, it is possible that a bug in a package may show up across a number of distros. But that is not even necessarily true, since distros are free to modify packages they include.

Ubuntu is *based *on Debian but it is not exactly *built *on Debian.  Ubuntu has many components that are not included in Debian and vice versa.

---

### Post by robin7 on 2014-01-26
One of the reasons that I stick with LTS releases of Ubuntu is that the LTS releases are built from *Debian Testing*, rather than from *Debian "Sid"* (Unstable), which the non-LTS releases are derived from.

But because of the changes that Ubuntu makes, I find Ubuntu much easier to install and configure, and it seems to smooth out an otherwise bumpy ride.  

Another practice I have come to adopt is using an LTS release all the way to the end of it's life rather than grabbing the newest LTS edition as soon as it is released.  This provides time for the bugs to be discovered and worked out long before my version reaches it's end of support.  

But that's just me, being the technophobe I have become since I started using Linux.  I take great comfort in Ubuntu LTS' stability and reliability from several months after release to it's end-of-life.

---

### Post by buzzingrobot on 2014-01-26
Deciding if X or Y has more bugs requires identifying and counting all the bugs in both, and that's impossible. Personally, I have never found the non-LTS Ubuntu releases to be any less reliable than the LTS releases, so it's useful to me to get the improvements in the non-LTS versions.  I'm not running a business where downtime costs money, though. 

(That said, it has been a long, long time since I have had *any* Linux distribution crash and just stop running. Most bugs I see in Ubuntu are only apparent  because Apport brings them to my attention. And, frankly, most of those seem to be compiz crashing and restarting.)  

It's useful to remember that Debian uses "Stable" in reference to the lack of change to package versions.  If a package moves from Sid to Testing to Stable without any changes, it will be as buggy in Stable as it was in Sid. 

A deliberate focus by developers to find and fix bugs is useful.  But, bugs are best found when software is used on  a wide variety of hardware in curcumstance nevers fully envisioned by developers by users of all kinds of skill levels. That's how LTS releases, whether Ubuntu's or Red Hat's, deal with bugs:  First, an effort to reduce bugs during the development and testing process, and then elimination of bugs reported by users after release.

Distributions are most likely to try to fix bugs in software that they contribute.  Bugs in software from upstream, e.g. Debian is upstream to Ubuntu and the developers of a Debian package are that package's upstream for Debian, are often pushed back upstream so they can be fixed for all distributions that package that software.

---

