---
title: "get the ubuntu firefox 1.0.7 fixed -help w. bug report"
date: 2006-03-05
forum: Server Platforms
---

### Post by towsonu2003 on 2006-03-05
We have the 1.0.7 firefox in ubuntu, and it has known vulnerabilities. There was a thread previously about this as well. 

I reported this as a bug[1] in ubuntu, bug no one seems to be interested. Now, I am absolutely not experienced with bugzillas. When there is no replies from the maintainers about a newly reported bug, I just assume they don't care about that specific bug. 

So I need some help:
1. People[2] to post / subscribe to this *bug report* so it gets attention[3]
or
2. Someone letting me know that not getting any input from maintainers doesn't mean they don't care ;)

I decided to post this because I saw that slackware updated their firefox to 1.5.0.1. This is significant, because the guy had a baby and still found time to update his distro... Here is his advisory: [http://www.slackware.com/security/viewer.php?l=slackware-security&y=2006&m=slackware-security.332581](http://www.slackware.com/security/viewer.php?l=slackware-security&y=2006&m=slackware-security.332581) which cites this as well: [http://www.mozilla.org/projects/security/known-vulnerabilities.html#firefox1.5.0.1](http://www.mozilla.org/projects/security/known-vulnerabilities.html#firefox1.5.0.1)

We have a bunch of developers and a billionaire sponsor. I'd prefer getting the update as well ;)

[1]**Bug** report here: [https://launchpad.net/distros/ubuntu/+bug/32083](https://launchpad.net/distros/ubuntu/+bug/32083)

[2]Preferably some experienced users in order to give convincing arguments. It seems I failed to do so. 

[3]Don't "digg" it though ;) :Pp

Thanks.

---

### Post by towsonu2003 on 2006-03-06
anyone out there? too early to bump? everyone busy at work?

---

### Post by hod139 on 2006-03-06
I'll subscribe to this thread if you think it will help, but I'm fairly certain the maintainers don't read this.  I too would like an official version of firefox 1.5 for breezy, but I'm not going to hold my breath.

---

### Post by towsonu2003 on 2006-03-06
[QUOTE=hod139]I'll subscribe to this thread if you think it will help, but I'm fairly certain the maintainers don't read this.  I too would like an official version of firefox 1.5 for breezy, but I'm not going to hold my breath.[/QUOTE]
sorry for the confusion: I meant the bug report... link is now in the first post. :)

---

### Post by hod139 on 2006-03-06
I suppose I should have figured that out on my own :)
Anyway, I subscribed to the bug, but I still have my doubts of a breezy package.

---

### Post by towsonu2003 on 2006-03-07
last bump-

> I still have my doubts of a breezy package me too, but according to their update guidelines, they have to update it. at least patch the current firefox 1.0.7 so that it is in the security state of 1.5.0.1 (patching 1.0.7 is gonna be harder than updating it to 1.5.0.1).

---

### Post by bobdave on 2006-03-12
If Dapper is delayed by six weeks ([https://lists.ubuntu.com/archives/ubuntu-art/2006-March/000734.html]("https://lists.ubuntu.com/archives/ubuntu-art/2006-March/000734.html")), patching or upgrading Firefox will become even more important.

---

### Post by towsonu2003 on 2006-03-12
the anomaly here is that, they are supposed to update Breezy security issues regardless of Dapper. Breezy is maintained for 6 months after Dapper is released if I am correct. Hence, they need to fix fx regardless of what they are doing with dapper. 

Is this how they are maintaining other packages as well??? if so, we're not using a secure distro...

---

### Post by ssam on 2006-03-12
the debian (and therefor ubuntu) way of doing things is to patch current verion rather to replace with a new version.

the ubuntu firefox 1.0.7 should contain newer patches. see [http://packages.ubuntu.com/changelogs/pool/main/f/firefox/firefox_1.0.7-0ubuntu20/changelog](http://packages.ubuntu.com/changelogs/pool/main/f/firefox/firefox_1.0.7-0ubuntu20/changelog)

if there are specific vunerablities not mentioned in that change log then file a bug.

---

### Post by towsonu2003 on 2006-03-12
[QUOTE=ssam]the debian (and therefor ubuntu) way of doing things is to patch current verion rather to replace with a new version.

the ubuntu firefox 1.0.7 should contain newer patches. see [http://packages.ubuntu.com/changelogs/pool/main/f/firefox/firefox_1.0.7-0ubuntu20/changelog](http://packages.ubuntu.com/changelogs/pool/main/f/firefox/firefox_1.0.7-0ubuntu20/changelog)

if there are specific vunerablities not mentioned in that change log then file a bug.[/QUOTE]
Bug is already filed. pls see 1st post. According to the changelog, the last update was done on >  firefox  (1.0.7-0ubuntu20) breezy; urgency=low

   * Recompile everything -fno-strict-aliasing.  See 17276.

 -- Ian Jackson <iwj@ubuntu.com>  Mon, **10 Oct 2005** 11:22:37 +0100 
Following are the bugs affecting 1.0 & 1.5 and fixed after that date with 1.5.0.1 release:
[http://www.mozilla.org/security/announce/mfsa2006-05.html](http://www.mozilla.org/security/announce/mfsa2006-05.html) (critical)
[http://www.mozilla.org/security/announce/mfsa2006-03.html](http://www.mozilla.org/security/announce/mfsa2006-03.html)
[http://www.mozilla.org/security/announce/mfsa2006-01.html](http://www.mozilla.org/security/announce/mfsa2006-01.html) (moderate)

edit: added this specific info to the bug.

---

### Post by bobdave on 2006-03-12
It'd be helpful if we could get some sort of official comment about this.

Interestingly, I don't think that there are new Fx packages for sarge, either.

---

### Post by hod139 on 2006-03-15
Looks like the devs are finally looking at your bug report!  Doesn't look like they are going to port 1.5 to breezy though, instead opting to make a 1.0.8.  As long as the hole is patched, that is fine with me.

---

### Post by towsonu2003 on 2006-03-15
as long as they close the holes -> I'm fine. I would think making a patch is harder but, well, I guess it's not <= I'm no programmer.

---

### Post by towsonu2003 on 2006-04-19
finally fixed with 1.0.8, see [http://www.ubuntu.com/usn/usn-271-1](http://www.ubuntu.com/usn/usn-271-1)

now the exciting part: let's see if upgrading breaks our 1.5.x installs ;)

---

### Post by RavenOfOdin on 2006-04-19
I know its breaking something, because I get the message:

"unable to make backup link of /usr/sbin/update mozilla-firefox chrome during install"
Please restart any running Firefoxes, or you will experience problems.

What's going on?

---

