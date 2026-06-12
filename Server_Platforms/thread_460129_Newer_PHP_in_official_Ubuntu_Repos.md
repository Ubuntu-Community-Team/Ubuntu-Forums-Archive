---
title: "Newer PHP in official Ubuntu Repos?"
date: 2007-05-31
forum: Server Platforms
---

### Post by brainyron on 2007-05-31
The 6.06 LTS repos still only have PHP 5.1.2.  Since the current version at the time of this writing is 5.2.2, I'm beginning to wonder if any effort is made to keep the packages in the LTS repos up to date, or if the LTS solely means that they support what came with it and nothing more.  This would be a major PHP upgrade, fixing a number of security flaws as well as numerous other bugs.  I guess what I'm wondering is, will there be any updated packages, particularly php, in the dapper repos, or are we on our own if we want/need anything newer than what's provided?  If we're just on our own for this stuff, what's the point of using LTS?

---

### Post by hellmet on 2007-06-01
I cannot confirm this, as I'm not from Dev. But, from past experience, PHP might be upgraded to the latest stable version, unless its known to have problems with Dapper, like Firefox.

---

### Post by TheMono on 2007-06-01
You have enabled the dapper-backports, right?

---

### Post by jtc on 2007-06-01
Actually, the current version in LTS right now is 5.1.2-1ubuntu3.8. That is not entirely the same thing as the vanilla 5.1.2, but the original 5.1.2 together with recent security patches.

That is the way things are done in Ubuntu. You don't get any new features with your updates, simply security (and sometimes stability) patches. Hence the version number.

---

