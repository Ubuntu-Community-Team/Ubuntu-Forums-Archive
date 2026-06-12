---
title: "Ubuntu regression test suit"
date: 2009-01-06
forum: Ubuntu Brainstorm
---

### Post by celafon on 2009-01-06
I am using Ubuntu since 2006. I am perfectly happy about it but there is one thing that worries me. It is the regressions that happen a lot after system upgrades.

How many times did you find that your piece of hardware no longer works the way it used to? I had such situations several times and it was always a frustrating experience...

Now I know that not everything could be avoided but there should be something done in order to perform a regression test for a new version of distro before deploying.

I am not talking here about the tests that sometimes do exist in the software packages. These obviously should be done as well. But I would like to see something that tries to check that there are no regressions in regard to system scripts and configuration.

Maybe we could build a kind of simulative environment for this purpose. I am sure that something could be done in order to add some checking to this process.

I have found a brainstorm idea for this already so I thought I try to find more supporters. Maybe this could spark some ideas around this general idea of how this could be achieved.

See [http://brainstorm.ubuntu.com/idea/15137/](http://brainstorm.ubuntu.com/idea/15137/)

BTW: Do you know any examples of the distro that tries to enforce such testing? I wonder if anyone tried to do this...

---

### Post by SeanHodges on 2009-01-06
A good idea in theory, and a great one for individual software/driver projects, but unfortunately this it is just not possible to build an effective regression suite for a whole distribution. There is far too much hardware out there in the wild, and all too often the problems stem from certain *combinations* of hardware as well.

Like most distributions, Ubuntu relies on a public testing phase to iron out regressions. The process is not faultless, but is far more effective than any regression suite would be. It can always use more testers though, this IMO is where people should concentrate their efforts. Check out [http://www.ubuntu.com/testing](http://www.ubuntu.com/testing).

---

### Post by gnomeuser on 2009-01-06
This Jaunty blueprint might be relavant:

[https://blueprints.launchpad.net/ubuntu/+spec/qa-jaunty-regression-tracker](https://blueprints.launchpad.net/ubuntu/+spec/qa-jaunty-regression-tracker)

---

### Post by UbuWu on 2009-01-06
There is some automated testing going on:

[https://wiki.ubuntu.com/Testing/Automation](https://wiki.ubuntu.com/Testing/Automation)

There is also a tracker for regressions, but it is still new and not used much yet:

[http://qa.ubuntu.com/reports/regression/regression_tracker.html](http://qa.ubuntu.com/reports/regression/regression_tracker.html)

---

### Post by marshall.robert on 2009-01-06
Sorry if this is inappropriate; but what about software? I have often found that a script or setup breaks after upgrading. In one particular case of mine, a while back now, i had a conversion script to convert video files into a format compatible with my portable mp4 player that was very quick, but after an upgrade it totally broke....

---

### Post by gnomeuser on 2009-01-06
> **marshall.robert said:**
> Sorry if this is inappropriate; but what about software? I have often found that a script or setup breaks after upgrading. In one particular case of mine, a while back now, i had a conversion script to convert video files into a format compatible with my portable mp4 player that was very quick, but after an upgrade it totally broke....

API stability is not ensured between versions. You also have no assurances that things actually stay using the same parameters or names between releases. It might be a bug though, at any rate it would be a good project to document such changes as they happen on the wiki e.g.

---

### Post by celafon on 2009-01-31
> **UbuWu said:**
> There is some automated testing going on:

[https://wiki.ubuntu.com/Testing/Automation](https://wiki.ubuntu.com/Testing/Automation)

There is also a tracker for regressions, but it is still new and not used much yet:

[http://qa.ubuntu.com/reports/regression/regression_tracker.html](http://qa.ubuntu.com/reports/regression/regression_tracker.html)
It looks that this is what I have been thinking of.

When it is stable (if ever) it could be a wise move to include it on the live cd, so the features could be tested and we get some feedback. Nice :)

---

### Post by mario_zama on 2009-01-31
I really encourage you to use the live cd for the upgrading version and test your hardware/software before entering the proces of upgrade. It's easier to take out the cd and report any problems than doing a rollback.

Your great, Ubuntu.

---

### Post by Slug71 on 2009-02-01
That is pretty much why i made this idea.

[[IMG]http://brainstorm.ubuntu.com/idea/16814/image/1/[/IMG]](http://brainstorm.ubuntu.com/idea/16814/)

---

