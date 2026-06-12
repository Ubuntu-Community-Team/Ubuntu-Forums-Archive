---
title: "ownCloud caution"
date: 2014-10-23
forum: Ubuntu, Linux and OS Chat
---

### Post by vasa1 on 2014-10-23
I just came across [this]("https://lists.ubuntu.com/archives/ubuntu-devel/2014-October/038522.html") which is a request to remove ownCloud software from "universe".> On behalf of the ownCloud project ([www.owncloud.org](www.owncloud.org)) I’m requesting that  “ownCloud server" is removed from the Ubuntu packages: [http://packages.ubuntu.com/trusty/owncloud](http://packages.ubuntu.com/trusty/owncloud) (including all versions) - Let’s hope that this is finally the right ML for this kind of request.

These packaged versions are all vulnerable to multiple critical security bugs and no security fixes have been backported, for a reference of security bugs please visit [http://owncloud.org/security/advisories/](http://owncloud.org/security/advisories/)
Those security bugs allows an unauthenticated attacker to gain complete control about the web server process.

---

### Post by mastablasta on 2014-10-23
I used OpenSUSE repo to install it. as I understand they only support versions 6 and 7
version 6.0.1 is obsolete. it should be 6.0.2 or 6.0.3 if it was already released.

edit: by the way - still no Ubuntu One private server?! :(

---

### Post by grahammechanical on 2014-10-23
The exchange of emails was interesting. It led to this

[https://bugs.launchpad.net/ubuntu/+source/owncloud/+bug/1384355](https://bugs.launchpad.net/ubuntu/+source/owncloud/+bug/1384355)

---

### Post by CharlesA on 2014-10-23
Glad I've been manually installing owncloud on my boxes. Granted, I use Debian, but having it sitting in the Universe repository with no outside support seems foolish.

---

### Post by Irihapeti on 2014-10-23
I couldn't get the Ubuntu repo version to work, anyway. I just downloaded the tar.gz file from the OwnCloud website and installed that.

I sometimes wonder what it would take for some of the devs to see something as a major issue. Maybe a close friend/family member getting hacked, otherwise it doesn't seem important.

---

### Post by coffeecat on 2014-10-24
This uncovers a wider issue, which was mentioned in this article:

[http://news.softpedia.com/news/ownCloud-Asks-Canonical-to-Remove-Their-Software-From-Ubuntu-Repos-Sparks-Fly-462906.shtml](http://news.softpedia.com/news/ownCloud-Asks-Canonical-to-Remove-Their-Software-From-Ubuntu-Repos-Sparks-Fly-462906.shtml)

> One of the big issues with the Ubuntu repositories, in particular "universe," is that they’re full of old and unmaintained versions. This is a repository where anyone care be a maintainer and it's mainly used for applications that are not supported officially.

What happens is that a user becomes a maintainer for a particular package, which basically means that he updates that package on a regular basis, or at least he should. Stuff happens, the packages are no longer maintained, and Ubuntu users get to use some really old versions. .

Perhaps they should say that it is a specific problem with the Universe (perhaps Multiverse too?) repository, where it sometimes happens that the maintainer loses interest and wanders off. I wonder if this episode might get Canonical to consider whether there should be some regular spring-cleaning in the Universe repo.

---

### Post by mastablasta on 2014-10-24
but if they do the spring cleaning, then they can't boast over 30.000 packages...

the fact is there is too much old stuff in repo. and then saying to users they can safely install this old unpatched software is irresponsible.

---

### Post by vasa1 on 2014-10-24
> **coffeecat said:**
> This uncovers a wider issue, which was mentioned in this article:

[http://news.softpedia.com/news/ownCloud-Asks-Canonical-to-Remove-Their-Software-From-Ubuntu-Repos-Sparks-Fly-462906.shtml](http://news.softpedia.com/news/ownCloud-Asks-Canonical-to-Remove-Their-Software-From-Ubuntu-Repos-Sparks-Fly-462906.shtml)...
That's where I got the mailing list link from. But I thought it prudent not to cite the Softpedia article.

---

### Post by CharlesA on 2014-10-24
> **coffeecat said:**
> 
Perhaps they should say that it is a specific problem with the Universe (perhaps Multiverse too?) repository, where it sometimes happens that the maintainer loses interest and wanders off. I wonder if this episode might get Canonical to consider whether there should be some regular spring-cleaning in the Universe repo.

That's one of the reasons I only backport stuff for myself, which in my case is ZNC on Debian Wheezy (which isn't in the backports repo), but don't push it out or try to get it into backports. I thought about it for a time, but it seems like too much work for little or no reward.

There should be a purge of all packages that are no longer maintained, but I doubt that is ever going to happen.

---

### Post by vasa1 on 2014-11-08
Lots of comments here: [http://lwn.net/Articles/619483/#Comments](http://lwn.net/Articles/619483/#Comments)

---

