---
title: "Never submitted a backport request before and have some questions.."
date: 2012-12-16
forum: Requests
---

### Post by romandas on 2012-12-16
So, I note that this forum is titled 'requests', and thought it would be the place to submit a backport request for Precise. However, I did see the wiki page ([https://wiki.ubuntu.com/UbuntuBackports](https://wiki.ubuntu.com/UbuntuBackports)) which mentions filing a backport as a bug via ubuntu-dev-tools.

So, I'm willing to do that, but the page goes on to say that a bunch of testing is required, and it seems to imply that I must do all this testing myself before the backport request will even be considered.

Now, I'm not one to shirk away from doing work.. but that seems like a pretty steep learning curve for wanting to request a backport. Is that intentional?

In particular, I'd like to request that git be backported to Precise from Quantal or Raring, due to a reported bug with https syncing and github for older versions of git (see [https://help.github.com/articles/https-cloning-errors]("https://help.github.com/articles/https-cloning-errors") for details), which seems like a legitimate reason to request it, but I'm frankly not sure I'm up to the task of doing all the testing. Am I screwed then, or have I just misread the wiki?

---

### Post by Cheesehead on 2012-12-16
The testing is pretty, though the first time can be a bit time-consuming:

Install VirtualBox
Install 12.04 in Virtualbox
Download the 12.10 deb of git
Install the deb in your 12.04 system

Does it run?
Is the bug fixed?
Does it introduce any new problems?

Done.

Now, when you do the backport bug, you can truthfully say you tested it.

---

