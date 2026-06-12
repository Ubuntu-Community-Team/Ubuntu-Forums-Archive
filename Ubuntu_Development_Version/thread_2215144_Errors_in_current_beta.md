---
title: "Errors in current beta?"
date: 2014-04-05
forum: Ubuntu Development Version
---

### Post by NoBugs! on 2014-04-05
Greetings all,

I was looking here: [https://errors.ubuntu.com/](https://errors.ubuntu.com/) and there seems to be a good number of errors on the new version - I'm curious if this is usual for a new LTS release? I'm excited about the new features, especially nvidia+intel optimus support, but I wonder if this number of errors is usual? And anyone know if this bug has a solution in 14.04? [https://bugs.launchpad.net/ubuntu/+source/indicator-appmenu/+bug/1005174](https://bugs.launchpad.net/ubuntu/+source/indicator-appmenu/+bug/1005174)

I've previously used the betas on my everyday machines, with rarely a small problem or two, but are these errors ones that will likely cause serious problems in current betas?

---

### Post by Sophont on 2014-04-05
> **NoBugs! said:**
> Greetings all,

I was looking here: [https://errors.ubuntu.com/](https://errors.ubuntu.com/) and there seems to be a good number of errors on the new version - I'm curious if this is usual for a new LTS release? I'm excited about the new features, especially nvidia+intel optimus support, but I wonder if this number of errors is usual? And anyone know if this bug has a solution in 14.04? [https://bugs.launchpad.net/ubuntu/+source/indicator-appmenu/+bug/1005174](https://bugs.launchpad.net/ubuntu/+source/indicator-appmenu/+bug/1005174)

I've previously used the betas on my everyday machines, with rarely a small problem or two, but are these errors ones that will likely cause serious problems in current betas?

Any large software project has a zillion defects at any time.
The most critical with the most widespread effcts will be dealt with in time for release (and some shortly after).
But it will never be bug free.

You'd be shocked if you could see the number of known defects in all the software products (MS Office, Mac OSX, etc... doesn't matter - all software is riddled with - mostly small - defects).
OTOH most of these defects will only show under unusual circumstances or affect only a small percentage of users.

LTS releases are not special in that they are particularly bug free. You are promised a longer support time - that's all.

---

### Post by buzzingrobot on 2014-04-05
Add in the fact that users report all sorts of things to the Linux bugzilla's that aren't really bugs. Plus, bugs that can't be duplicated, bug reports that lack information, etc. Just trying to read and evaluate incoming new reports can be a major resource issue.

That's why the LTS concept exists: Release something, fix bugs and patch security risks, try hard to avoid introducing other changes, and over time the number of bugs lurking in the release decreases.

---

### Post by NoBugs! on 2014-04-05
Thanks, I know there is no 100% bug-free software - I was just seeing the 14.04 line was double the others - and from what I understand, that is where the "program crashed, click send-report" go to, when they don't report them to launchpad?

---

### Post by grahammechanical on 2014-04-05
I used to work as a safety officer in a high street store of a major UK retailer. We were told to encourage employees to report any kind of accident no matter how trivial. One year the company directors noticed that our company had many more reported accidents than a rival company and the directors, in their great wisdom, assumed it meant that our company was less safe than the rival company. What it actually meant was that the rival company was not so diligent in reporting accidents.

As part of my health and safety training I once had to give a presentation on Accident reporting. I choose as my theme: "Look beyond the statistics." Let us do a little bit of it now.

Over the last two years a lot of effort has been put into Ubuntu Quality Assurance to make even the development branch of Ubuntu stable. Part of this effort is to increase the number of testers and the range of test cases. It is better to detect bugs during the development phase rather than after the version has been released. The more bugs we can find during the development phase the more bugs get squashed during the development phase.

The development Branch comes with a Crash reporting utility enabled by default. It also is being refined.

And what is more, those statistics for 14.04 will also include Ubuntu Touch bugs. A lot of development work has been done over the last year on Ubuntu for phones and tablets. So, we should expect an increase in the number of bugs for 13.10 and 14.04 when compared to 12.04/12.10. And that is exactly what we do see.

Now, it all depends on how we look at these statistics. You see trouble and failure. I see a massive effort to identify bugs before release day. And remember, although some of us have been running Trusty Tahr since the start of the development cycle many more people starting using the next release of Ubuntu when the beta images are released. Do we not see spikes in the number of bugs reported in line with the Beta images being released?

Regards.

---

