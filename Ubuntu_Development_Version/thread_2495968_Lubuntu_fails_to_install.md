---
title: "Lubuntu fails to install"
date: 2024-03-09
forum: Ubuntu Development Version
---

### Post by VMC on 2024-03-09
Tried several different ways. All to no avail. Always fails with exception in Networkcfg/Main.py
Using todays ISO.

[https://bugs.launchpad.net/ubuntu/+source/lubuntu-meta/+bug/2054697](https://bugs.launchpad.net/ubuntu/+source/lubuntu-meta/+bug/2054697)

---

### Post by xeghepgiare on 2024-03-11
Perhaps the new version is not stable yet.
Can you try the older version?

---

### Post by guiverc on 2024-03-11
That bug has been reported & is being tracked (*a patch for it from upstream is mentioned in the bug report too*)

- [https://discourse.ubuntu.com/t/ubuntu-24-04-testing-week/43090/7](https://discourse.ubuntu.com/t/ubuntu-24-04-testing-week/43090/7)
- [https://discourse.lubuntu.me/t/ubuntu-24-04-lts-testing-week/4772](https://discourse.lubuntu.me/t/ubuntu-24-04-lts-testing-week/4772)

The *upstream patch* has been tested a number of times, and has been proven to work on a number of dailies; alas no *daily* to my knowledge has the package on it **yet** (*but we hope to fix a number of other issues too with the same FFe* including bugs that impact Kubuntu ISOs)

The issue impacts all *three* flavors that use (or will use) `calamares`, inc. Kubuntu (*Ubuntu Unity ISO still had `ubiquity` on their ISOs last I checked, but they will have `calamares` in time too*)

---

### Post by oldfred on 2024-03-15
Kubuntu calamares has Calamares bug also.
[https://bugs.launchpad.net/ubuntu/+source/calamares/+bug/2054795](https://bugs.launchpad.net/ubuntu/+source/calamares/+bug/2054795)
```
/usr/lib/x86_64-linux-gnu/calamares/modules/networkcfg/main.py so that line 158 reads like:
                os.chmod(f.fileno(), 0o600)
instead of its current state of:
                os.chmod(f, 0o600)


```

Fix is available in proposed, but stuck with other updates for now.
The fix is in 3.3.5-0ubuntu1.

Kubuntu installer graphics starts with Kubuntu, but then the rest refer to Lubuntu.

---

### Post by guiverc on 2024-03-27
This is an old thread.. but issues remain for now..

The reason for this reply is I saw a *comment* by [Erich]("https://launchpad.net/~eeickmeyer") on #ubuntu-flavors (Matrix) that I feel relates...

> Bear in mind: Ubuntu MATE's slideshow still hasn't been ported from Ubiquity because `livecd-rootfs` has had `ubuntu-desktop-provision` stuck in an unusable state for them. Also, Ubuntu Cinnamon, Ubuntu Unity, and Ubuntu Budgie all haven't had an .iso image for exactly a month now because `nemo` has been stuck in proposed. So now, there's nothing to test. Hopefully everything unsticks soon, but if there are bugs, it's not as simple as uploading a fix with the archive frozen.

Lubuntu's fix has been *stuck* for awhile now in *proposed*.  :(

I'm hoping in a day or two we'll be in a better state; as the Ubuntu Release/Foundations etc team are working hard to get the *stack* cleared as we're approaching *beta* freeze... 

Some install testing continues; eg. I've noted [LeoK]("https://launchpad.net/~leok") manually fixing the issue as reflected on the current ISO tests (*not just today too*).

[https://iso.qa.ubuntu.com/qatracker/milestones/450/builds/298366/testcases/1701/results](https://iso.qa.ubuntu.com/qatracker/milestones/450/builds/298366/testcases/1701/results)

> 
In order to test the daily ISO the &#8220;main.py&#8221; file was edited before install as a fix for bug 2054795


---

