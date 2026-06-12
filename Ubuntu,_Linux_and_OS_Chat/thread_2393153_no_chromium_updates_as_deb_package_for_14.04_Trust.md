---
title: "no chromium updates as deb package for 14.04 Trusty - press info"
date: 2018-05-30
forum: Ubuntu, Linux and OS Chat
---

### Post by arapaho on 2018-05-30
Updates for chromium as deb package for 14.04 has ended.
[URL="https://linux.slashdot.org/story/18/05/18/1654208/canonical-shares-desktop-plans-for-ubuntu-1810"]
https://linux.slashdot.org/story/18/05/18/1654208/canonical-shares-desktop-plans-for-ubuntu-1810[/URL]

> [COLOR=#363636][FONT=Arial]Chromium as a snap 
Chromium is becoming very hard to build on older releases of Ubuntu as it uses a number of features of modern C++ compilers. Snaps can help us solve a lot of those problems and so we propose to ship Chromium only as a snap from 18.10 onwards, and also to retire Chromium as a deb in Trusty. If you're still running Trusty you can get the latest Chromium as a snap right now.[/FONT][/COLOR]

I don't require support. I still use 14.04 and was searching for reasons why chromium is outdated and found this press news and decided to share this info for other who might look for this information.

---

### Post by Perfect Storm on 2018-05-30
Thread moved to Ubuntu, Linux and OS Chat.

---

### Post by PaulW2U on 2018-05-30
Further details can be found in the following two threads on the Ubuntu Community Hub:

[Chromium updates on trusty]("https://community.ubuntu.com/t/chromium-updates-on-trusty/5905")
[Intent to provide chromium as a snap only]("https://community.ubuntu.com/t/intent-to-provide-chromium-as-a-snap-only/5987")

This affects **everyone** that uses Chromium not just Trusty users. ;)

---

### Post by PaulW2U on 2018-09-14
Now in testing: [Please test chromium snap as a replacement for the deb]("https://discourse.ubuntu.com/t/please-test-chromium-snap-as-a-replacement-for-the-deb/7978").

I've been using the snap version of Chromium since late August and have only come across a handful of problems that still need to be resolved. The change from Chromium being provided by deb package to snap can't be far away now even though it doesn't seem likely to be the default in Ubuntu 18.10 as the Phoronix article suggested: [https://linux.slashdot.org/story/18/05/18/1654208/canonical-shares-desktop-plans-for-ubuntu-1810](https://linux.slashdot.org/story/18/05/18/1654208/canonical-shares-desktop-plans-for-ubuntu-1810).

---

### Post by PaulW2U on 2019-06-14
The date when the Chromium browser will be provided as only a snap rather than a deb package is getting very much closer now.

The official call for testing of the transition can be found at: [https://discourse.ubuntu.com/t/call-for-testing-chromium-browser-deb-to-snap-transition/11179](https://discourse.ubuntu.com/t/call-for-testing-chromium-browser-deb-to-snap-transition/11179)

Providing Chromium as a snap is now the default in the current development release (Ubuntu 19.10) and once any initial problems have been resolved the transition to a snap will be rolled out to the 'disco' and then 'bionic' and 'xenial' releases.

---

### Post by PaulW2U on 2019-10-10
[Chromium in Ubuntu – deb to snap transition]("Chromium in Ubuntu – deb to snap transition") is I guess the official announcement of what **will** affect any Chromium user that installs or upgrades to Ubuntu 19.10 which is due for release next week. All Ubuntu [flavours]("https://wiki.ubuntu.com/UbuntuFlavors") are similarly affected.

As someone who has been testing the Chromium snap for sometime I will admit that there will are still a [few issues]("https://bugs.launchpad.net/ubuntu/+source/chromium-browser/+bugs?field.tag=snap") that need resolving but for me those issues are minor. Hopefully everything will be resolved before the next LTS release in April 2020.

The blog posts says:
> Once 19.10 is released, we will carefully consider extending the transition to other stable releases, starting with 19.04. This won’t happen until all the important known issues are addressed, of course.
Please report any issues that you find after of course first checking the list of [known issues]("https://bugs.launchpad.net/ubuntu/+source/chromium-browser/+bugs?field.tag=snap").

---

### Post by cruzer001 on 2019-10-10
Chromium .deb package and all other deb packages

[https://pkgs.org/download/chromium-browser](https://pkgs.org/download/chromium-browser)

---

### Post by PaulW2U on 2019-10-10
I added to this thread, which has been running for over a year now, to draw attention to the fact that for Ubuntu **19.10** Chromium will only be offered as a snap and that **eventually** this will affect **all** supported releases of Ubuntu.

Sorry cruzer001, what were you trying to point out?

---

### Post by cruzer001 on 2019-10-10
What this thread was about "14.04"  NOT SNAPS

---

### Post by PaulW2U on 2019-10-10
But I did point out in post #3 that **every** release would be affected not just 14.04.

---

### Post by uRock on 2019-10-10
> **PaulW2U said:**
> [Chromium in Ubuntu – deb to snap transition]("Chromium in Ubuntu – deb to snap transition") is I guess the official announcement of what **will** affect any Chromium user that installs or upgrades to Ubuntu 19.10 which is due for release next week. All Ubuntu [flavours]("https://wiki.ubuntu.com/UbuntuFlavors") are similarly affected.

As someone who has been testing the Chromium snap for sometime I will admit that there will are still a [few issues]("https://bugs.launchpad.net/ubuntu/+source/chromium-browser/+bugs?field.tag=snap") that need resolving but for me those issues are minor. Hopefully everything will be resolved before the next LTS release in April 2020.

The blog posts says:

Please report any issues that you find after of course first checking the list of [known issues]("https://bugs.launchpad.net/ubuntu/+source/chromium-browser/+bugs?field.tag=snap").

Thanks for sharing this. Though the original title does state 14.04, it is also talking about the end of deb package support for Chromium.

---

### Post by PaulW2U on 2019-10-10
> **uRock said:**
> Thanks for sharing this.
No problem and thanks for your comment.

I probably should have started a new thread but mistakenly thought that by changing the title of the post then the title of the thread would also be changed when viewing new posts/threads. Still learning after 9+ years.  :)

---

### Post by TheFu on 2019-10-10
Goodby Chromium. You will be missed.
I miss 10.04 more and more every day.  That was the last Ubuntu that "felt" right, sadly.

Snaps should be optional, IMHO.  Not everyone has 50G of storage and 16G of RAM and doesn't want to read data from flash drives or /tmp/.

---

