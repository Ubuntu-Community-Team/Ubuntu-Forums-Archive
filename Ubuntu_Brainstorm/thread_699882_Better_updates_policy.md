---
title: "Better updates policy"
date: 2008-02-17
forum: Ubuntu Brainstorm
---

### Post by DizzyTech on 2008-02-17
We need a better updates policy.  By this, I mean Ubuntu's policy on providing updated packages (e.g., Firefox 0.0.0.x bugfixes between releases) and larger upgrades between releases (e.g. ALSA 0.0.x) needs to be fixed.

If it's broken**right** now, it might be fixed in the next release.  Maybe not; toss in a bug and it might be looked at.  If you just got a new laptop, and a new updates comes out to fix it (like ALSA), you're mostly SOL for the next six months.  I propose that an updates team is created (or enlarged if too small, or liberated if tied to another group) for the **sole** purpose (now and forever) of providing updates to the current supported edition of Ubuntu while the next edition is being worked on.

We also need to have less strict boundaries on packaging for releases.  It should be possible to have xOrg 1.5 or Kernel 2.6.26 (no typo) in Hardy Heron before Insatiable Impala is released.  There should be less red tape defining versions of software included in versions of Ubuntu.  I understand the concept of pre-release freezes, but post-release updates should not be out of the question.  One problem I've noticed with Ubuntu is that we try to be as cutting-edge as possible, but limit as much as possible between releases at the same time.  I'm not going to point the proverbial finger at the other guys - whoever they may be - but they definitely have their respective advantages as far as packing go.

Just bouncing ideas...

---

### Post by Fbot1 on 2008-02-17
Ya, this is by far the most annoying part of Ubuntu.

---

### Post by jken146 on 2008-02-17
It's always a trade-off between stability and having the latest versions of software.  Also you have to bear in mind that the Ubuntu devs are mostly dedicated to working on the next release, as we have a 6 month cycle.  This allows Ubuntu releases  to be rather cutting-edge at first, then pretty static until the next release.  That's how this distro works.  IMHO the Ubuntu way is very good indeed.

Other distros have different ways of doing things.  Arch, for example, has a rolling release system, which keeps you very up to date.  It's not exactly a distro for the faint-hearted (read the manual), but if you're prepared to give it a shot, I recommend it to those who want something less static than Ubuntu.

---

### Post by Fbot1 on 2008-02-17
> **jken146 said:**
> It's always a trade-off between stability and having the latest versions of software.  Also you have to bear in mind that the Ubuntu devs are mostly dedicated to working on the next release, as we have a 6 month cycle.  This allows Ubuntu releases  to be rather cutting-edge at first, then pretty static until the next release.  That's how this distro works.  IMHO the Ubuntu way is very good indeed.

Other distros have different ways of doing things.  Arch, for example, has a rolling release system, which keeps you very up to date.  It's not exactly a distro for the faint-hearted (read the manual), but if you're prepared to give it a shot, I recommend it to those who want something less static than Ubuntu.

But sometimes they past up perfectly stable software.

---

### Post by DizzyTech on 2008-02-17
@jken146:  I understand that.  I very much do.  I want each release to be as fricking awesome as possible.  However, if my laptop's sound doesn't work when Gutsy comes out, I don't want to be screwed for six months.  No offense, but Ubuntu has always been static due to version freezes (and I don't mean via things like SVN).  Every Ubuntu release is immediately out of date as far as things go.

We all try and push it off, saying that we're sacrificing an acceptable amount of bloody fingers on bleeding edges for stability, but we're not.  By not updating, we're locking ourselves into a cycle of crappiness.  Just look at Gutsy and its kernel, or Flash, or ALSA, or Firefox.  None of them have been updated in the repositories (well, I'll give them ALSA, but they were doing it anyway) since Gutsy RC, which I ran months ago.

I'm not even talking about rolling releases, although a hybrid model could help us out a lot (e.g., releases like Gutsy and Hardy, but with lots of updated packages in between).  In a perfect world, a past release (e.g., Gutsy) would have the maximum updated packages in everything.  The idea of upgrading to the new release is not bugfixes, but for big, new stuff.  Old releases should have software at their newest verisons allowed in their release line (Firefox 2.0.0.x, Kernel 2.6.23.xx).

EDIT:  @Fbot1:  Exactly.

---

### Post by steeleyuk on 2008-02-18
Firefox (and other software) usually gets updated when security fixes are released. But feature only updates are very rarely included (there was one related to Vista updates a few months back which Ubuntu never updated to).

I still think the current model is better in terms of stability. By the time a version of Ubuntu is released, the development team is pretty much working on Alpha 1 of the next release. With your suggestion, that will mean having to do the new development work plus support the current release with testing, packaging and bug fixing...

The only other thing to do if you want the latest and greatest is to compile the software yourself. At least you in the knowledge can fix any problems that might occur and take responsilbity for anything that goes wrong on your computer.

---

### Post by DizzyTech on 2008-02-18
That makes sense.  I understand exactly what you're saying.  The model we use was great at first, but it's been defeated with a lack of stability in some releases.  I'm not asking the development team to take on another job.  We need a seperate team to do this.  For a professional operating system, that's how it should be.

---

### Post by arkara on 2008-02-18
what i want to say is that ubuntu has a very nice distro but for example some packages should be updated in every release and most of all in lts.
for example openoffice and gimp are some apps that have new features and bugfixes all the time and should be really updated.
in general the 'frame' should be kept stable and the some programs should be updated more frequently.

---

### Post by Fbot1 on 2008-02-18
> **DizzyTech said:**
> ...We need a seperate team to do this...

Even just one guy would be nice.

---

### Post by lexen on 2008-02-18
I totally agree, but the question is where are these people coming from?  I have been trying to figure how to package Ubuntu .deb files for a while now, but I can't figure it out.  What we need is a way to get people like me (enthusiastic but ignorant) working for Ubuntu.  

   If someone out there could either make a really good tutorial for packaging .deb, possibly including videos or make a better program for doing a majority of the work for you.  I downloaded DebianPackageMaker, but I couldn't get it to work.  The program ran, but the output didn't work.  It also didn't let me select which version of Ubuntu I wanted this for, or even that it was for Ubuntu, so I think that is why the output wouldn't run.  If we could work together, maybe we could fix that problem and really get something done.

   Is there anyone reading this that can make industry standard .deb files for Ubuntu that could help the rest of us out, or at least send us in the right direction?  The official Ubuntu documentation is okay, but it is a little hard to follow.



Thanks,
Lexen

---

### Post by jpittack on 2008-02-18
Ask for a backport.

---

### Post by 23meg on 2008-02-18
[QUOTE=lexen]I totally agree, but the question is where are these people coming from? [/quote]

Very good question that strikes the problem at the core.

[quote=lexen]I have been trying to figure how to package Ubuntu .deb files for a while now, but I can't figure it out. What we need is a way to get people like me (enthusiastic but ignorant) working for Ubuntu.[/QUOTE]

You should follow the ongoing [Ubuntu Developer Week]("http://ubuntuforums.org/showthread.php?t=693734"), check out the [packaging guide]("https://wiki.ubuntu.com/PackagingGuide"), and [ask for a mentor]("https://wiki.ubuntu.com/MOTU/Mentoring") if you're looking to contribute as a MOTU in the future. A lot of effort is being made to attract new developers; you may find the [MOTU logs]("http://ubuntuforums.org/showthread.php?t=691331") kept by some prospective ones interesting. There's also [a forum]("http://ubuntuforums.org/forumdisplay.php?f=44") for packaging related issues.

---

### Post by jdong on 2008-02-19
As a member of the MOTU SRU team and the lead of the Backports team, I have to say "wait 6 months" is the **LAST** thing I want to tell someone requesting a fix to their favorite software.

The bottom line is, **broken software should be, and will be, fixed** and this philosophy has recently been solidifying in terms of black and white words on the wiki ([https://wiki.ubuntu.com/StableReleaseUpdates](https://wiki.ubuntu.com/StableReleaseUpdates)). If you read the criteria for such updates, they are getting broader and more generous.

However, we will not blindly accept new versions of things into a released version of Ubuntu, with the sole exception that the current version is so completely and utterly broken that it couldn't get any worse.

For the most part, we'd like to see small fixes picked from upstream, or another distribution that solely address the problem at hand, without introducing any other unnecessary changes...

If you notice nowadays, often times things like Firefox and core GNOME packages will get updated to the upstream's latest point releases as those projects already adopt a bugfixes-only policy.

Of course, we are always open to suggestions and improvements. We want to see Ubuntu software working as much as you do, but at the same time when next big digg/slashdot article features the latest Ubuntu breakage from overzealous updates.... the blame finger has got to be pointed at someone :)


EDIT: I should also add, Backports is now going to be better too (I hereby coin the term Backports 2.0) now that our very own Scott Kitterman is a core developer -- this means that I can more easily get in source-change backports and just about everything that won't uproot the entire repository will be fair game for backporting :)

---

