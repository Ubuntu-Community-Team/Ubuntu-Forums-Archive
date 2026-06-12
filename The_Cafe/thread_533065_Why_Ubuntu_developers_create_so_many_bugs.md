---
title: "Why Ubuntu developers create so many bugs?"
date: 2007-08-23
forum: The Cafe
---

### Post by nfm on 2007-08-23
Here's something I'm trying to understand, it may perhaps affect other distros. From where are all of the bugs coming from, I mean, when we have a stable kernel 2.6.22.5, why no use it as a original and stop modifying it and creating new bugs. Why do developers modify stable packages and create extra bugs that don't exist in the first place?

Why are packages modified first place? Otherthing that bugs me is that some packages are terribly out-of-date, such as coreutils or gcc.
What is the philosophy behind all of this?

---

### Post by tageiru on 2007-08-23
> **nfm said:**
> From where are all of the bugs coming from, I mean, when we have a stable kernel 2.6.22.5, why no use it as a original and stop modifying it and creating new bugs.

:D

> **nfm said:**
> Why do developers modify stable packages and create extra bugs that don't exist in the first place?

They are fixing bugs. Upstreams definition of stable does not always correspond to end user stability. Linux is a good example as the developers have said that stabilization should be done by distributors. Distributors are also integrating software from an insane amount of sources. Sometimes there are conflicts between packages which upstream are not aware of, and they need to be fixed.

> **nfm said:**
> Why are packages modified first place? Otherthing that bugs me is that some packages are terribly out-of-date, such as coreutils or gcc.
What is the philosophy behind all of this?

They are trying to maintain some level of sanity. Running the latest from upstream would be an unpredictable ride.

---

### Post by katasuka on 2007-08-23
its called implementing new features and new support.

with new features and new hardware support etc... comes bugs. humans arent perfect and make mistakes. it happens. this is why there are testers. of course since humans arent perfect, some bugs will be missed and end up in a "stable release". however, with ubuntu, at least important bugs are fixed fairly soon after finding them

---

### Post by FyreBrand on 2007-08-23
> **nfm said:**
> Here's something I'm trying to understand, it may perhaps affect other distros. From where are all of the bugs coming from, I mean, when we have a stable kernel 2.6.22.5, why no use it as a original and stop modifying it and creating new bugs. Why do developers modify stable packages and create extra bugs that don't exist in the first place?No one goes to work in the morning and says to the team, "hey what bugs can we introduce today?"

When new features or bug fixes are implemented developers and teams try to anticipate the impact and consequences of that.  There is internal and external (such as development releases) testing to try and see what unanticipated consequences are.  In a very complicated code project it is impossible to try out every configuration setting in every environment with every single use case.  This is why there is a bug tracker where users can provide feedback on stuff that doesn't work.

> Why are packages modified first place? Otherthing that bugs me is that some packages are terribly out-of-date, such as coreutils or gcc.
What is the philosophy behind all of this?You've answered your own question here.  Why do packages change? Why update the kernel and modules?  Because packages get terribly out of date with hard ware, features, and users wants/needs.  If you wonder why packages change it's because they get out of date.  Get it?

By the way this process of updating the "out of date" often introduces the bugs.  You could really say that bugs are the fault of end users not being satisfied with working code.  If users never needed applications to be updated then new bugs would likely never be introduced.

---

### Post by ironfistchamp on 2007-08-23
Wow the title just screams flamebait.

Anyway modifying code is always going to have unpredictable affects. No matter how much you try to squash bugs, some are going to slip through the net.

---

### Post by forrestcupp on 2007-08-23
> **nfm said:**
> when we have a stable kernel 2.6.22.5, why no use it as a original and stop modifying it and creating new bugs.
> Otherthing that bugs me is that some packages are terribly out-of-date, such as coreutils or gcc.

Ha, ha.  Make up your mind.  You contradict yourself in a very small post.:lolflag:

---

### Post by PriceChild on 2007-08-23
I think a good selection of reasons have been given already.
The big one imo being that in fixing one thing, other unforseen problems can easily appear.

If you would like to contribute, please see [http://www.ubuntu.com/community/participate/developerzone](http://www.ubuntu.com/community/participate/developerzone)

Thread Closed in line with the UbuntuForums.Org Code of Conduct, section 1, part 3:
> If the thread is flame-bait (appears to be intended to start an argument or is likely to cause an argument rather than enhance discussion), it will be locked or removed without notice. Individual flame-bait may be deleted or edited at the moderators' discretion. Any users who continue to post in this manner or engage in other questionable practices, like trolling (posting in an attempt to engage people in arguments) may be subject to more serious sanctions.

---

