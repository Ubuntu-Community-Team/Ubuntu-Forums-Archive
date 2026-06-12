---
title: "Is the Knowledge Required to Report Ubuntu Bugs Poorly Communicated?"
date: 2011-11-01
forum: The Cafe
---

### Post by nutznboltz on 2011-11-01
**Is the Knowledge Required to Report Ubuntu Bugs too Complex and Obscure and Poorly Communicated?**

[This bug report, LP: #795717]("https://bugs.launchpad.net/bugs/795717") is emblematic of the perils of using crowd-sourced QA the way that Canonical does.  The QA team, gdahlman, failed to write the the mandatory comment about testing causing Canonical to revert the patch. I can't hold it against gdahlman.  What if he got sick or his mom died or something?  My point is there are plenty of good reasons your crowd-sourced QA team might go AWOL even after reporting a valid bug report with a reproducible test case.

What if gdahlman simply could not comprehend that the patch would not be included if he didn't just scribble "I tested the kernel in natty-proposed" into the ticket?  Is it that reporting Ubuntu bugs requires knowing internal procedures that Canonical follows but fails to communicate to the community especially to crucial members of that community who they feel need to do some work for them?

I have taken over being the QA team for LP: #795717 after my having made a long series of discoveries about why my "virsh" commands lock up caused me to arrive at it.

This is the second time I have become the QA team of someone else's Ubuntu Linux kernel bug.  The previous time was for [LP: #579276]("https://bugs.launchpad.net/bugs/579276") where I wasn't the first one to fully understand the bug, I was the first one who understood the bug PLUS spoke "Canonicalese", the magical language the makes you able to get Canonical to respond to a bug report by doing something about it instead of closing it as "invalid".

In a related question, why can't Canonical test something that only requires a single VM host computer, their own OS, Ubuntu and a FOSS VM RHEL-compatible guest?  Why are they dependent on using crowd-sourced QA when the bug is reproducible and only requires one commodity PC and some FOSS?

---

### Post by coffeecat on 2011-11-01
Not a General Support question.

*Thread moved to **The Community Cafe**.*

---

### Post by aysiu on 2011-11-01
Over the years, Ubuntu has made it easier and easier to report bugs--having reports be GUI-driven and/or automatic.

But you're right about the follow-up on bugs. That is currently not user-friendly at all for non-developers (I'm one, for example, and having been using Ubuntu for over six years). And there are a lot of valid bugs that get closed prematurely as invalid or "won't fix."

If it's a matter of communication, Ubuntu needs to step it up and make it so that regular power users (not necessarily other developers or programmers) can communicate to Ubuntu the issues they're having with releases and pre-releases.

And if it's a matter of person power, they just need to focus on a certain select number of models and make sure those work well. Better to have 99% or 100% support for five models of laptop, for example, than to have 70% support for eighty models of laptop.

---

### Post by CharlesA on 2011-11-01
I've reported a few bugs and they have either gotten ignored or listed as "fixed" or "works as intended"

Haven't run into anything recently, but the one that I had issues with was due to mountall failing to mount a device and causing the boot to hang while it was waiting for you to hit "s" without displaying anything to TTY1 (you had to switch to TTY7 to see the error).

No one decided if it was a problem with mountall (which it was) or with Plymouth. Quite annoying since the only workaround for it was to add "nobootwait" to fstab.

---

### Post by nutznboltz on 2011-11-02
It would be nice if there were video presentations of what has to be done to follow through on a bug submission correctly.

At this point my advice to aspiring bug submitters is to take time examining the successful and unsuccessful bug reports filed by others first before trying it yourself.  Plus going to LoCo meetings and asking for demonstrations of [http://bugs.launchpad.net/](http://bugs.launchpad.net/)

---

### Post by sffvba[e0rt on 2011-11-02
I would love to see it being easier to make good quality bug-reports.  That doesn't mean it is possible however (somethings in life are just inherently harder than others, and sometimes what is easy for one isn't so easy for another).


404

---

### Post by nutznboltz on 2011-11-02
> **not found said:**
> I would love to see it being easier to make good quality bug-reports.  That doesn't mean it is possible however (somethings in life are just inherently harder than others, and sometimes what is easy for one isn't so easy for another).

Show me that an effort has been made to communicate.  Then I will believe it may not be possible.  When no concerted effort has been made jumping to the conclusion that nothing can be done is not useful.

---

### Post by sffvba[e0rt on 2011-11-02
> **nutznboltz said:**
> Show me that an effort has been made to communicate.  Then I will believe it may not be possible.  When no concerted effort has been made jumping to the conclusion that nothing can be done is not useful.

I think you misunderstand... I am sorry if the post came over as negative and rejecting what your saying, I am all for making it easier, just pointing out that it isn't necessarily easy.

I am all for trying and I think that this is a very good project for the Ubuntu Beginners Team to undertake (or at least assist with).  I would love to see not only a video etc. making it easier but the whole reporting application can be revamped to guide anyone through a step by step process to make sure a high quality bug is reported (more helping than the current one, it should even have functionality to tie in directly with launchpad and even be the interface when and if anything more is ever needed after the initial report etc.)


404

---

### Post by Elfy on 2011-11-02
> **not found said:**
> I am all for trying and I think that this is a very good project for the Ubuntu Beginners Team to undertake (or at least assist with)

[http://ubuntuforums.org/showthread.php?t=1011078](http://ubuntuforums.org/showthread.php?t=1011078)

---

### Post by grahammechanical on 2011-11-02
I consider myself as an ordinary Ubuntu user. I think that there should be a sharp definition of what is a bug and what is not a bug.

Something not working the way a person thinks it should work or wants it to work is not a bug in my opinion. For example, the missing Visual Effects tab in the Appearance utility is not bug.

In some ways it is too easy to report a bug (anyone can do it) and I think that it can cause a kind of information overload. So, that real bugs may get missed by being marked as invalid. There has to be some kind of selection. And that should start with the reporting of bugs that are indeed bugs and not include things that are simply user irritants.

May be I am miss reading the situation.

Regards.

---

### Post by sffvba[e0rt on 2011-11-02
> **forestpiskie said:**
> [http://ubuntuforums.org/showthread.php?t=1011078](http://ubuntuforums.org/showthread.php?t=1011078)

Thank you sir :)


404

---

### Post by nutznboltz on 2011-11-08
Seems something happened: Ubuntu Developer Summit (UDS) Day #2 included this:
> **[Improve community kernel SRU testing (link)](http://summit.ubuntu.com/uds-p/meeting/19297/hardware-p-cert-sru-community/)**

2011-11-01 12:00..13:00 in antigua-2

SRU testing is about validating that package updates don't introduce problems on stable releases. The testing includes regression testing performed by the QA team, security testing by the Security team, certification testing by the Certification team and verification by the Kernel team. There is also some testing performed by the Ubuntu community coordinated by the QA team, but this is mostly achieved on a best effort basis. The purpose of this blueprint is to increase community participation and include their successful testing rather than just bug reports. The current process for getting community participation is by commenting on the bugs fixed by the SRU when the package is building for the proposed archive. The comment describes how to enable this archive where the package will be ready in a few hours and then asks the subscribers to please test with feedback. Another process specific for kernel packages is for development releases to be announced on voices.canonical.com and proposed kernels may also be announced eventually. As can be seen from the pending SRU reports, this has not resulted in much participation and the responsibility then falls upon the QA team. The first objective is to increase community participation for proposed kernels. The most significant value is to increase the probability that verification testing is performed by someone in the community within a reasonable delay. As a side effect, another value is to relieve the QA team from some testing which can otherwise result in additional delays. The SRU release team would benefit from having more people testing with minimal delays to push a new kernel from proposed to updates. The second objective is to include successful testing from the community rather than just bug reports. This will enable the SRU release team to also consider the number of people having tested the proposed kernels in addition to their existing reports. This should result in greater confidence before pushing a new kernel from proposed to updates. This is the story to achieve both these objectives: 1. A kernel is added to the proposed archive, so the user is notified that a new kernel is available; 2. The user opens Update Manager where she is informed that the kernel can be tested after rebooting; 3. After booting for the first time with a proposed kernel, Checkbox prompts the user to run the SRU suite; 4. If a test fails, Apport is invoked and tags the bug with "regression-proposed" for the current reports; 5. After testing, all test results are submitted to Launchpad where additional reports can be generated. 

HT @JustMeAmber for [this tweet](https://twitter.com/#!/JustMeAmber/status/131402286009303040).

But this isn't just a Kernel SRU problem, look at this grub2 bug that I converted into an SRU request this morning:
[https://bugs.launchpad.net/bugs/563895](https://bugs.launchpad.net/bugs/563895)
> fred (ubuntu-launchpad-lk2) wrote on 2011-09-10: 	#18

not having a fix for this in "LTS" after more than a year makes me sad

wasted 3 hours of my life on this earlier this year - bug is known, confirmed and fixed - why not push a new grub version for lucid?

> Benaiah (dougie-hobson) wrote on 2011-10-28: 	#19

I am also wondering why a bug fix is not being pushed to lucid. I know that with LTS versions you do the whole feature freeze thing and only release security updates and I think bug fixes. This is not a feature addition, it is a bug that needs to be fixed. Is this not possible?

The fact that yesterday there was another incident in my data center that could have been prevented if someone had done an SRU of a fix a year ago to 10.04 LTS shows not enough people know how to do an SRU.

UPDATED:

I didn't get a response in 24 hours to my attempt to convert LP: 563895 into an SRU request so I did what usually works when that fails: I opened a new bug using "ubuntu-bug".

[https://bugs.launchpad.net/bugs/888069](https://bugs.launchpad.net/bugs/888069)

---

### Post by nutznboltz on 2011-11-11
*burp*

---

### Post by VanillaMozilla on 2011-11-11
> **nutznboltz said:**
> **Is the Knowledge Required to Report Ubuntu Bugs too Complex and Obscure and Poorly Communicated?**
You, sir, are a master of understatement.

---

### Post by nutznboltz on 2011-11-16
> **VanillaMozilla said:**
> You, sir, are a master of understatement.

I was trying to put it nicely.

Meanwhile, read comment #15 in [LP: #692691](https://bugs.launchpad.net/ubuntu/+source/grub/+bug/692691/comments/15).  Note that LP: #692691 is all about Canonical sitting on yet another bug report that has a patch provided because no one did the SRU request.  Me, I had forgotten the bug existed since our OpsCode chef puts the corrected script into our servers.  I didn't remember until I got mail about it today when mail about Comment #15 arrived.

Also, interesting dates in the life of [LP: #563895](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/563895)
* March 21, 2010 - Reported as Debian [#574863](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=574863)
* April 4, 2010 (elapsed 14 days) Reported as LP: #563895
* June 2, 2010 (elapsed 73 days) Fix committed into Debian and Debian bug closed.
* July 5, 2010 (elapsed 106 days) Fix committed in Ubuntu 10.10 (Maverick)
* September 10, 2011 (538 days) Complaint (not by me) in LP #563895 using the words "not having a fix for this in "LTS" after more than a year makes me sad"
* November 8, 2011 (597 days) I convert bug into SRU request with debdiff of patch and PPA with patched grub2 packages.
* November 14, 2011 (604 days) by submitting [this question](http://askubuntu.com/questions/79347/what-is-the-policy-for-updating-grub-pc-in-lts) I am able to get someone to acknowledge that this bug needs work.
* November 15, 2011 (605 days) I post this list about LP: #563895

Does 605 days without putting one little patch into LTS seem right? 

But the amount of time is only an indication that the SRU process needs some advocacy or educational work.  If more people understood the exact steps required to do an SRU request none of this would have happened.

---

### Post by nutznboltz on 2011-11-16
Regarding [http://bugs.launchpad.net/](http://bugs.launchpad.net/) as it pertains to this issue:

On the surface it appears to be one thing while in actuality it is something else.

Almost anyone who encounters it thinks "this is a web site where I can write about what is wrong with some software and it will get fixed."

In reality nothing could be further from the truth.

That truth is "this is a web site where if one uses a complex communication protocol it is possible to get bugs fixed."

The fact that there is that gap between appearances and actuality is the crux of the issue.  Lauchpad should be altered to make the truth much easier to see.  Too many people get slighted by the "why didn't my bug get fixed I posted to this web site" concept that would not be in their minds if the web site didn't have the gap.

---

### Post by castrojo on 2011-11-16
> **nutznboltz said:**
> 
Does 605 days without putting one little patch into LTS seem right? 

In cases like this you can always post on the ubuntu-devel mailing list if something is going completely out of whack like this.

---

### Post by nutznboltz on 2011-11-16
> **castrojo said:**
> In cases like this you can always post on the ubuntu-devel mailing list if something is going completely out of whack like this.

You are missing my real point.

The current workflow goes:

1. somebody smart enough to provide a needed patch encounters the public-facing [http://bugs.launchpad.net/](http://bugs.launchpad.net/) and opens a bug with the patch.

2. Because that highly-visible public-face web site lack as much as a link to a FAQ file with a question like

Q: Why didn't my patch get accepted?
A: You need to do ....

they feel slighted.

How hard would it be to get in front of this workflow to switch it to something better?

---

### Post by Lucradia on 2011-11-16
It's hard to report a bug for ubuntu for an application that can't use apport, because the program doesn't have appropriate logs.

---

### Post by dholbach on 2011-11-16
The preferred way to get suggested changes reviewed and included in Ubuntu is [http://developer.ubuntu.com/packaging/html/fixing-a-bug.html](http://developer.ubuntu.com/packaging/html/fixing-a-bug.html) (merge proposal using bzr). If you follow this process, it will automatically land in the review queue. Also do (since a few months now) bugs with patches with a changelog entry also get put into the review queue straight away.

I realise there's still a backlog of patches in LP, but that's mainly due to old and broken patches and the problem of not having patch statuses in LP.

There's a team trying to help clean up the backlog. So if you're interested check out [https://wiki.ubuntu.com/ReviewersTeam/ReviewGuide](https://wiki.ubuntu.com/ReviewersTeam/ReviewGuide)

---

### Post by nutznboltz on 2011-11-16
> **dholbach said:**
> The preferred way to get suggested changes reviewed and included in Ubuntu is [http://developer.ubuntu.com/packaging/html/fixing-a-bug.html](http://developer.ubuntu.com/packaging/html/fixing-a-bug.html) (merge proposal using bzr).

Thanks, is this process used for patching stable Ubuntu releases or just the development branch?  

UPDATE: never mind I found [this](http://developer.ubuntu.com/packaging/html/security-and-stable-release-updates.html).

BTW did you notice [no one has ever tweeted](http://topsy.com/developer.ubuntu.com/packaging/html/security-and-stable-release-updates.html) that link?

---

### Post by nutznboltz on 2011-12-08
A recent news article about this:
> [b][The rules of the game (link)](http://www.h-online.com/open/features/The-rules-of-the-game-a-conversation-with-Dave-Neary-1382692.html)
A conversation with Dave Neary
by Richard Hillesley[/b]

Richard Hillesley talked with Dave Neary about his experience working with open source communities and companies, and discovered that the important thing is not so much what the rules are, but that everyone knows what they are. ...

---

