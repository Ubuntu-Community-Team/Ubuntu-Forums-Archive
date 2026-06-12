---
title: "suspicious update"
date: 2010-03-12
forum: Security
---

### Post by StuSchu on 2010-03-12
I'm a new Ubuntu 9.10 user.

My update manager is showing an update named "sudo".  When I look under Description -> Changes, this is listed:
[http://sudo.ws/repos/sudo/rev/88f3181692fe](http://sudo.ws/repos/sudo/rev/88f3181692fe)
CVE-2010-0426

When I googled the latter, I found [this]("http://web.nvd.nist.gov/view/vuln/detail?vulnId=CVE-2010-0426") page saying it's a virus.  Where can I find if other people have come across this before, and how would you recommend I deal with it?

Molto grazie.

---

### Post by uRock on 2010-03-12
Have you added any repositories to your sources.list?

---

### Post by viralmeme on 2010-03-12
> **StuSchu said:**
> .. My update manager is showing an update named "sudo" ..
It isn't a virus, but it could be exploited by a local user to gain elevated privilege but only if  pseudo-command is enabled ..

[http://www.linuxjournal.com/content/sudo-axes-escalation-glitch](http://www.linuxjournal.com/content/sudo-axes-escalation-glitch)

---

### Post by StuSchu on 2010-03-12
iRock- I'm way too linux-retarded to add repositories to my sources.list.  Where were you going with that question?

ymitchell- Thanks.  I won't let any shady people use my computer.

---

### Post by uRock on 2010-03-12
> **StuSchu said:**
> iRock- I'm way too linux-retarded to add repositories to my sources.list.  Where were you going with that question?

If you added a repo for being able to install some kind of mind horoscope software (some people try anything), then maybe the upgrade was from said repo, but I don't think that is the case with you.

---

### Post by pricetech on 2010-03-12
I recall sudo getting updated recently, though I couldn't tell you exactly when it was.

No sudo is not a virus.

---

### Post by mikewhatever on 2010-03-12
> **StuSchu said:**
> ...

When I googled the latter, I found [this]("http://web.nvd.nist.gov/view/vuln/detail?vulnId=CVE-2010-0426") page saying it's a virus.  Where can I find if other people have come across this before, and how would you recommend I deal with it?

Molto grazie.

The page you linked to is a Vulnerability Summary for CVE-2010-0426, not a virus. In fact, there is no such word on the page. So, the security vulnerability was discovered, and the update was served to patch it. Business as usual, nothing suspicious.

---

### Post by SoFl W on 2010-03-12
It was updated recently and I asked about it [HERE]("http://ubuntuforums.org/showthread.php?t=1418210"), I wasn't sure if I should allow the update.

---

### Post by MarkC502 on 2010-03-13
Its a program that lets a non admin run an admin command. IE sudo apt-get install aircrack-ng etc.

The page you list is a valid legit site for that utility. You are in 0% danger due to this.

Mark

---

