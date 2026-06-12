---
title: "Why the update to LibreOffice 4.3.3?"
date: 2014-11-06
forum: Ubuntu, Linux and OS Chat
---

### Post by vasa1 on 2014-11-06
I got updates today which included updates to the components of LibreOffice I have on my system:> Start-Date: 2014-11-06  06:36:39
Commandline: apt-get dist-upgrade
Upgrade: libreoffice-base-core:amd64 (4.3.2-0ubuntu1, 4.3.3-0ubuntu1), ure:amd64 (4.3.2-0ubuntu1, 4.3.3-0ubuntu1), libreoffice-writer:amd64 (4.3.2-0ubuntu1, 4.3.3-0ubuntu1), uno-libs3:amd64 (4.3.2-0ubuntu1, 4.3.3-0ubuntu1), fonts-opensymbol:amd64 (102.6+LibO4.3.2-0ubuntu1, 102.6+LibO4.3.3-0ubuntu1), libreoffice-core:amd64 (4.3.2-0ubuntu1, 4.3.3-0ubuntu1), command-not-found:amd64 (0.3ubuntu15, 0.3ubuntu15.1), python3-commandnotfound:amd64 (0.3ubuntu15, 0.3ubuntu15.1), libreoffice-style-human:amd64 (4.3.2-0ubuntu1, 4.3.3-0ubuntu1), libreoffice-help-en-us:amd64 (4.3.2-0ubuntu1, 4.3.3-0ubuntu1), command-not-found-data:amd64 (0.3ubuntu15, 0.3ubuntu15.1), python3-uno:amd64 (4.3.2-0ubuntu1, 4.3.3-0ubuntu1), libreoffice-common:amd64 (4.3.2-0ubuntu1, 4.3.3-0ubuntu1), libreoffice-gtk:amd64 (4.3.2-0ubuntu1, 4.3.3-0ubuntu1), libreoffice-style-galaxy:amd64 (4.3.2-0ubuntu1, 4.3.3-0ubuntu1), libreoffice-calc:amd64 (4.3.2-0ubuntu1, 4.3.3-0ubuntu1)
End-Date: 2014-11-06  06:38:34I'm just wondering why. I Had the impression that only "security" updates or very serious bug fixes would be pushed out during the life of each release.

[OMG Ubuntu!]("http://www.omgubuntu.co.uk/2014/10/libreoffice-4-3-3-released-62-bug-fixes") describes it this way:> LibreOffice 4.3.3, the third minor update in the 4.3.x series and the first since the September release of 4.3.2, comes packed with plenty of stability and performance fixes, but no major new features to sing of.(I know I can hold LibreOffice packages.)

---

### Post by ian-weisser on 2014-11-06
> **vasa1 said:**
> I Had the impression that only "security" updates or very serious bug fixes would be pushed out during the life of each release.

It is a security update.

First,lets look at the changelogs.
- There's nothing (yet) at changelogs.ubuntu.com. Since the update is less than 24 hours old, that's not a surprise.

Next, let's look at Launchpad for the changelog.
- Here's the changelog at [https://launchpad.net/ubuntu/+source/libreoffice:](https://launchpad.net/ubuntu/+source/libreoffice:)
```
libreoffice (1:4.3.3-0ubuntu1) utopic-security; urgency=medium
  * new upstream release
 -- Bjoern Michaelsen <email address hidden>   Tue, 04 Nov 2014 16:36:09 +0100
```
It looks like an ordinary new release...until you notice that it's uploaded to utopic-security (not -backports or -updates), and that it has a medium urgency.

Since it's a security update of some kind, let's look at the Ubuntu Security Team.
- Aha. There it is with full details: [http://www.ubuntu.com/usn/usn-2398-1/](http://www.ubuntu.com/usn/usn-2398-1/)

Finally, let's look at an upstream announcement: [https://www.libreoffice.org/about-us/security/advisories/CVE-2014-3693/](https://www.libreoffice.org/about-us/security/advisories/CVE-2014-3693/)

Note the dates. The vulnerability was discovered (but not disclosed) in May 2014. When it was disclosed, the update was packaged and pushed within hours - the upload time is (before adjusting for time zones) before the diclosure.
Good Job, Ubuntu Security Team and LibreOffice Team!

---

### Post by vasa1 on 2014-11-06
Alles klar! Thanks for the detailed explanation :)

---

### Post by mastablasta on 2014-11-06
versioning: major.minor.security

---

### Post by pfeiffep on 2014-11-06
OK now I'm perplexed. I just performed a software update (via gui) then checked LO version and I'm still running 4.2.7.2.

Certainly this is not an extremely important consideration for me, I'm just trying to understand the overall differences between software updater, apt-get, and aptitude.

---

### Post by vasa1 on 2014-11-06
> **pfeiffep said:**
> OK now I'm perplexed. I just performed a software update (via gui) then checked LO version and I'm still running 4.2.7.2.

Certainly this is not an extremely important consideration for me, I'm just trying to understand the overall differences between software updater, apt-get, and aptitude.
I'm not sure but I think you're on the equivalent of a "stable" version of LibreOffice aka "Still" versus one with more experimental features titled "Fresh" (somewhat like a beta even though they claim it's "production-ready"). So you'll keep getting updates to LibreOffice 4.**2** as long as it's supported.

The important thing is that you got the update today> All users are recommended to upgrade to LibreOffice 4.2.7 or 4.3.3.from ian-weisser's CVE link: [https://www.libreoffice.org/about-us/security/advisories/CVE-2014-3693/](https://www.libreoffice.org/about-us/security/advisories/CVE-2014-3693/)

---

### Post by vasa1 on 2014-11-06
If you want to know more about *fresh* versus *still*:
[http://ask.libreoffice.org/en/question/32301/what-is-the-difference-in-libre-fresh-or-libre-stable/](http://ask.libreoffice.org/en/question/32301/what-is-the-difference-in-libre-fresh-or-libre-stable/)
[http://standardsandfreedom.net/index.php/2014/08/01/libreoffice-4-3/](http://standardsandfreedom.net/index.php/2014/08/01/libreoffice-4-3/) (the section titled *Spring Water*)

---

### Post by pfeiffep on 2014-11-06
@vasa1 + @ian-weisser  Thank you both!

---

### Post by ian-weisser on 2014-11-06
> **pfeiffep said:**
> OK now I'm perplexed. I just performed a software update (via gui) then checked LO version and I'm still running 4.2.7.2.

Software Updater uses [phased updates]("https://wiki.ubuntu.com/PhasedUpdates"). The update will show up in a day or two.
apt-get does not use phased updates. The update will show up immediately.

---

### Post by vasa1 on 2014-11-06
@pfeiffep, where did you LibreOffice from? Was it a ppa or a direct download from [www.libreoffice.org](www.libreoffice.org) or from the software center? And what version of Ubuntu are you on?

And what do the last few lines of /var/log/apt/history.log look like?

---

### Post by mastablasta on 2014-11-07
I too had 4.2.soemthign but wasn't 7 on windows and it didn't prompt for update. trying to update it caused it to say there are no updates. strange. so I just went to libre office page and downloaded the new version.

---

### Post by pfeiffep on 2014-11-07
> **vasa1 said:**
> @pfeiffep, where did you LibreOffice from? Was it a ppa or a direct download from [www.libreoffice.org]("http://www.libreoffice.org") or from the software center? And what version of Ubuntu are you on?

And what do the last few lines of /var/log/apt/history.log look like?
LO installed during Ubuntu 14.04.1 installation which I updated immediately updated; after initial install accepted all upgrades when offered by 'Software Updater'

```
Start-Date: 2014-11-06  12:25:28
<snip>
libreoffice-common:amd64 (4.2.6.3-0ubuntu1, 4.2.7-0ubuntu1), gir1.2-ebookcontacts-1.2:amd64 (3.10.4-0ubuntu1.3, 3.10.4-0ubuntu1.5), libreoffice-gtk:amd64 (4.2.6.3-0ubuntu1, 4.2.7-0ubuntu1), 
libecal-1.2-16:amd64 (3.10.4-0ubuntu1.3, 3.10.4-0ubuntu1.5), libebook-1.2-14:amd64 (3.10.4-0ubuntu1.3, 3.10.4-0ubuntu1.5), evolution-data-server:amd64 (3.10.4-0ubuntu1.3, 3.10.4-0ubuntu1.5), 
libedataserver-1.2-18:amd64 (3.10.4-0ubuntu1.3, 3.10.4-0ubuntu1.5), poppler-utils:amd64 (0.24.5-2ubuntu4, 0.24.5-2ubuntu4.1), libedata-cal-1.2-23:amd64 (3.10.4-0ubuntu1.3, 3.10.4-0ubuntu1.5), 
libreoffice-math:amd64 (4.2.6.3-0ubuntu1, 4.2.7-0ubuntu1), libreoffice-calc:amd64 (4.2.6.3-0ubuntu1, 4.2.7-0ubuntu1)
End-Date: 2014-11-06  12:27:05

```

---

### Post by vasa1 on 2014-11-07
> **pfeiffep said:**
> LO installed during Ubuntu 14.04.1 installation which I updated immediately updated; after initial install accepted all upgrades when offered by 'Software Updater'
...
So I think things are working just fine for you because you're on 14.04. Your code showed **4.2.6.3-0ubuntu1, 4.2.7-0ubuntu1** indicating that you've got the security update. I think you'll remain with 4.2.n as long as LibreOffice supports it.

---

### Post by ssam on 2014-11-09
Be careful. Even though these are meant to be bug fix releases there is a change to how sorting works in spreadsheets that can break old documents. [https://bugs.freedesktop.org/show_bug.cgi?id=81633](https://bugs.freedesktop.org/show_bug.cgi?id=81633)

---

### Post by vasa1 on 2014-11-09
> **ssam said:**
> Be careful. Even though these are meant to be bug fix releases there is a change to how sorting works in spreadsheets that can break old documents. [https://bugs.freedesktop.org/show_bug.cgi?id=81633](https://bugs.freedesktop.org/show_bug.cgi?id=81633)
Very interesting bug. I use Calc a lot but I've been always been wary of sorting content containing formulas which I think is what the bug is about. I'll have to read that bug carefully.

I do agree with some of the posters that LibreOffice is moving a bit too fast with introducing new features. I may even uninstall 4.3 (aka *fresh*) and install 4.2 (aka *still*).

---

