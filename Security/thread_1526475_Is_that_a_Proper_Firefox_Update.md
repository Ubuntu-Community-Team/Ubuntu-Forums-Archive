---
title: "Is that a Proper Firefox Update?"
date: 2010-07-08
forum: Security
---

### Post by wacky_sung on 2010-07-08
I have come across a repository site for firefox and got an update of firefox to version 3.6.7.Then in the Help -> About Mozilla Firefox (There is a label by "The XXX Company").The repository site is [http://ubuntuupdates.org/ppas/12](http://ubuntuupdates.org/ppas/12)  .I just pondered is that proper firefox update?

---

### Post by giarca on 2010-07-08
Yes, I think it is.
If you download firefox package directly from mozilla.com website and run it, you can read exactly the same.
I don't know the reason why that part miss in the ubuntu package.

---

### Post by wacky_sung on 2010-07-08
[IMG]http://i32.tinypic.com/2nrpv2b.png[/IMG]

The update come along with the tag of "The XXX Company" instead of mozilla.That does not seem right isn't it?Hopefully you get what i mean.

---

### Post by OpSecShellshock on 2010-07-08
According to the official Mozilla site, 3.6.6 is the current version.

Edit: well, the PPAs listed on that site seem real. Looks like one of them has a test package on it for 3.6.7. It may not be ready for normal use yet.

---

### Post by wacky_sung on 2010-07-08
Beside that, it does not seem to be at the right version as mozilla firefox daily build.

[https://launchpad.net/~ubuntu-mozilla-daily/+archive/ppa](https://launchpad.net/~ubuntu-mozilla-daily/+archive/ppa)

Show daily build = version 3.7 alpha , version 3.6.8 beta

What the other site shown is version 3.6.7.What's the difference between both sites?

---

### Post by giarca on 2010-07-08
Mozilla security ppa seems to sync with the official beta package from mozilla site:
[http://www.mozilla.com/en-US/firefox/beta/](http://www.mozilla.com/en-US/firefox/beta/)
The 3.6.7build1 was the official beta since 2-3 days ago.
I check my "about" window and I didn't notice any difference with the official mozilla package dowanloaded to try.
(check yourself, go to the link above and download the tar.bz2 file, then extract and run firefox, you can see the about page are the same)

---

### Post by wacky_sung on 2010-07-08
Thank you for showing me the link but my concern is the site( [http://ubuntuupdates.org/ppas/12](http://ubuntuupdates.org/ppas/12)) here coming with a tag "The XXX Company"  giving the user to install can also be trying to compromise their system.

---

### Post by FuturePilot on 2010-07-08
The Mozilla Security PPA is a legit PPA [https://launchpad.net/~ubuntu-mozilla-security/+archive/ppa]("https://launchpad.net/~ubuntu-mozilla-security/+archive/ppa")
It's maintained by the Ubuntu Mozilla Security Team. [https://launchpad.net/~ubuntu-mozilla-security]("https://launchpad.net/~ubuntu-mozilla-security")

> but my concern is the site( [http://ubuntuupdates.org/ppas/12](http://ubuntuupdates.org/ppas/12)) here coming with a tag "The XXX Company" giving the user to install can also be trying to compromise their system.
I'm not sure what you're talking about. I don't see anything saying that. Can you post a screenshot?

---

### Post by wacky_sung on 2010-07-08
> **FuturePilot said:**
> The Mozilla Security PPA is a legit PPA [https://launchpad.net/~ubuntu-mozilla-security/+archive/ppa]("https://launchpad.net/%7Eubuntu-mozilla-security/+archive/ppa")
It's maintained by the Ubuntu Mozilla Security Team. [https://launchpad.net/~ubuntu-mozilla-security]("https://launchpad.net/%7Eubuntu-mozilla-security")


I'm not sure what you're talking about. I don't see anything saying that. Can you post a screenshot?

Pardon me,i have actually removed it.I do not wanna take the risk again.Probably you can install it using my link and verify my statement.Appreciated for those who help / i may be wasting your time.I just wanna clarify if anyone face the same issue as what i did.

---

### Post by cariboo on 2010-07-08
The one thing to keep in mind is the [Ubuntuudates.org]("http://ubuntuupdates.org/"), is not an official repository, and not owned by Canonical, so whether you want to trust it is up to you.

---

### Post by FuturePilot on 2010-07-08
Ok, so the problem in question is "The Charlton Company". A little searching leads to [https://bugzilla.mozilla.org/show_bug.cgi?id=569057]("https://bugzilla.mozilla.org/show_bug.cgi?id=569057") and [http://sillydog.org/forum/viewtopic.php?t=8214#p59467]("http://sillydog.org/forum/viewtopic.php?t=8214#p59467")
Nothing to worry about.

> **cariboo907 said:**
> The one thing to keep in mind is the [Ubuntuudates.org]("http://ubuntuupdates.org/"), is not an official repository, and not owned by Canonical, so whether you want to trust it is up to you.

Ubuntuupdates.org is not a repository and does not host any packages.

---

### Post by wacky_sung on 2010-07-09
Thank you FuturePilot you have cleared my queries and hit the mark :p:popcorn:

---

