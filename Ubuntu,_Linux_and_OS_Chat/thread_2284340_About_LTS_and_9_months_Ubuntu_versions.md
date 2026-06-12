---
title: "About LTS and 9 months Ubuntu versions?"
date: 2015-06-28
forum: Ubuntu, Linux and OS Chat
---

### Post by remmas-sido on 2015-06-28
Hello guys 
I have a question that I want to ask, usually in the LTS version community softwares which are universe and multiverse softwares (someone correct me if I'm wrong) don't get updates as long as the version is actively supported and the only way to get updates for those softwares is through Personal Package Archive, so here's my question: Do these softwares get updates in 9 non-LTS versions? or they are just like LTS releases where you will need to add a Personal Package Archive?

---

### Post by kansasnoob on 2015-06-28
It depends greatly on who maintains a specific package - some maintainers are known to update packages only when they deem the changes worthy of a package upgrade - while, at the other end of the spectrum, some maintainers are known to almost always upload the latest package available from Debian Unstable or Experimental even if it's incredibly buggy.

OTOH sometimes Canonical themselves forces flavors such as Ubuntu GNOME to hold certain packages for another cycle because the newer versions may conflict with some packages related to the Unity desktop. And since GNOME normally releases a new version only about one month prior to Ubuntu releasing a new version we're almost always one version behind on actual GNOME packages.

So there is no single answer that would be truthful in all instances. But you can always search [packages.ubuntu.com]("http://packages.ubuntu.com/") to see what versions of a specific package are available in the archive. Just for instance [look at VLC]("http://packages.ubuntu.com/search?keywords=vlc"):

[ATTACH=CONFIG]262906[/ATTACH]

Does that help at all?

---

### Post by remmas-sido on 2015-06-28
> **kansasnoob said:**
> It depends greatly on who maintains a specific package - some maintainers are known to update packages only when they deem the changes worthy of a package upgrade - while, at the other end of the spectrum, some maintainers are known to almost always upload the latest package available from Debian Unstable or Experimental even if it's incredibly buggy.

OTOH sometimes Canonical themselves forces flavors such as Ubuntu GNOME to hold certain packages for another cycle because the newer versions may conflict with some packages related to the Unity desktop. And since GNOME normally releases a new version only about one month prior to Ubuntu releasing a new version we're almost always one version behind on actual GNOME packages.

So there is no single answer that would be truthful in all instances. But you can always search [packages.ubuntu.com]("http://packages.ubuntu.com/") to see what versions of a specific package are available in the archive. Just for instance [look]("http://packages.ubuntu.com/search?keywords=vlc")[ at VLC]("http://packages.ubuntu.com/search?keywords=vlc"):

[ATTACH=CONFIG]262906[/ATTACH]

Does that help at all?

As I can see VLC is always upgraded to it latest version.

---

### Post by monkeybrain20122 on 2015-06-28
> **remmas-sido said:**
> As I can see VLC is always upgraded to it latest version.

?? The latest version of vlc is 2.2.1 and from kansasnoob's picture Trusty has 2.16 (and Precise has 2.08 which is ancient) In fact only 15.10 has 2.2.1 and it is not released yet. You can get the latest stable release on Trusty only from ppas such as [https://launchpad.net/~mc3man/+archive/ubuntu/trusty-media](https://launchpad.net/~mc3man/+archive/ubuntu/trusty-media) or compile it yourself (videolan has a ppa for vlc but it offers only unstable builds rather than the latest stable release and I think some options are disabled for unknown reasons)

---

### Post by buzzingrobot on 2015-06-29
The vast  majority of Linux programs in Ubuntu, and in any other distribution, are maintained by developers not affiliated with that distribution. Typically, then, a develop updates a piece of software for his or her own reasons on his or her own schedule. When any given distribution adds that update to its repositories is a different decision.

The attraction of an LTS release is that it remains stable over the long term. Users tend to think of "stable" as meaning crash-free and bug-free.  That's accurate, but it also refers to the unchanging nature of the package versions in a distribution release, i.e., their stabililty. That's the particular kind of stability that's important to enterprise users and that's why they choose distributions like RHEL, Debian Stable, and Canonical's LTS releases. (Reduction of bugs is the result of applying bug fixes to fixed version of packages over time, rather than introducing unknown changes inherent in new versions.)

Ordinary users need to decide if they value access to the most recent packages more than the promise of stability an LTS provides. However, no Ubuntu release can actually be considered cutting edge. The non-LTS Unity releases typically avoid using components from the most recent Gnome release.

---

