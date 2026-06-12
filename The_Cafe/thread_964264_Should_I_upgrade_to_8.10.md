---
title: "Should I upgrade to 8.10?"
date: 2008-10-30
forum: The Cafe
---

### Post by tigrezno on 2008-10-30
This is the question I'm already asking myself after reading some things:

[LIST]
[*]The upgrade will not be presented by default because 8.10 is not a Long Term Support (LTS) release.
[*]Nvidia not supported by latest Xorg
[*]Will it break like my last update?
[/LIST]

What is the real deal about leaving the LTS release?
Will nvidia release a good driver soon? (i'm a gamer)
What about the update? Will it work? my last update (7.10 -> 8.04) was a total failure and had to reinstall from cdrom.

Thanks in advance.

---

### Post by pirattrev on 2008-10-30
Here's the line of questioning: 

**Question 1**
Does your current version work, or not work?  

**Question 2**
Are you not happy or dissatisfied with your current set up?

**Question 3**
Do you feel completely sure that an upgrade will make your computer more satisfactory?

**Key:**
no, no, no --> don't upgrade
yes, no, no --> proceed to look into _possible_ upgrade
no, yes, no --> look into how you could make your computer "work"
no, no, yes --> upgrade
yes, yes, no --> don't upgrade
no, yes, yes --> upgrade
yes, no, yes --> upgrade
yes, yes, yes --> upgrade

hope this helped

---

### Post by FuturePilot on 2008-10-30
> What is the real deal about leaving the LTS release?
The special thing about LTS is that it's just supported longer than the normal releases. (3 years on the desktop, 5 on the server)

> Nvidia not supported by latest Xorg
> Will nvidia release a good driver soon? (i'm a gamer)

This was only for the Legacy driver. However Nvidia has released an updated driver as of yesterday. We're just waiting for it to get approved to go into the repos. If you don't use the Legacy driver you don't have to worry about this at all.

> What about the update? Will it work? my last update (7.10 -> 8.04) was a total failure and had to reinstall from cdrom.
That all depends. I couldn't say it would completely blow up and I couldn't say it would go perfectly. Though I've always done the upgrade and never had a problem. You can always do a fresh install if you not sure, or just stay with Hardy for now. It's really up to you.

---

### Post by tigrezno on 2008-10-30
> **pirattrev said:**
> Here's the line of questioning: 

**Question 1**
Does your current version work, or not work?  

**Question 2**
Are you not happy or dissatisfied with your current set up?

**Question 3**
Do you feel completely sure that an upgrade will make your computer more satisfactory?

**Key:**
no, no, no --> don't upgrade
yes, no, no --> proceed to look into _possible_ upgrade
no, yes, no --> look into how you could make your computer "work"
no, no, yes --> upgrade
yes, yes, no --> don't upgrade
no, yes, yes --> upgrade
yes, no, yes --> upgrade
yes, yes, yes --> upgrade

hope this helped

lol nice post, but you haven't replied to what I've asked, sorry :)
my current system works, but I wanted to know the real implications of upgrading and leaving a LTS release like 8.04.

will 8.04 be frozen? (only security updates) or what?

---

### Post by pirattrev on 2008-10-30
> **tigrezno said:**
> lol nice post, but you haven't replied to what I've asked, sorry :)
my current system works, but I wanted to know the real implications of upgrading and leaving a LTS release like 8.04.

will 8.04 be frozen? (only security updates) or what?

the truth is, I wouldn't.  LTS's are well cared for, have well supported repos and people just tend to produce upgrades and improvements for them more and better on non-LTS releases. If you know that Xorg doesn't support nvidia that right there is enough for me to say stick it out. If you know what you're doing and you feel it's absolutely necessary to play with all the new gizmos, go for 8.10, otherwise you may be looking at hours lost and time spent trying to even make it work.  Security updates, graphics and everything will be more likely to crash and more likely to just not work period [not that they will, it's just more likely]. The LTS are basically surefire to function and act as a good reliable OS, but 8.10 [and the other non-LTS releases will always be more prone to problems]. New software and cooler stuff will come much quicker to the non-LTS releases, but that comes at the cost of it not working [plus non-LTS stuff can for the majority run on the LTS (as long as certain things are updated properly)]. That's my take on it. Hope that helps.

---

### Post by tigrezno on 2008-10-30
> **pirattrev said:**
> the truth is, I wouldn't.  LTS's are well cared for, have well supported repos and people just tend to produce upgrades and improvements for them more and better on non-LTS releases. If you know that Xorg doesn't support nvidia that right there is enough for me to say stick it out. If you know what you're doing and you feel it's absolutely necessary to play with all the new gizmos, go for 8.10, otherwise you may be looking at hours lost and time spent trying to even make it work.  Security updates, graphics and everything will be more likely to crash and more likely to just not work period [not that they will, it's just more likely]. The LTS are basically surefire to function and act as a good reliable OS, but 8.10 [and the other non-LTS releases will always be more prone to problems]. New software and cooler stuff will come much quicker to the non-LTS releases, but that comes at the cost of it not working [plus non-LTS stuff can for the majority run on the LTS (as long as certain things are updated properly)]. That's my take on it. Hope that helps.

yes, you've helped hehe I won't be upgrading for now.

so i've guessed that new features are included in 8.10 as "unstable" and will be released to 8.04 when they are really stable, isn't it?

---

### Post by FuturePilot on 2008-10-30
> **tigrezno said:**
> 
so i've guessed that new features are included in 8.10 as "unstable" and will be released to 8.04 when they are really stable, isn't it?
No, when each version is released the repos are frozen. Only security updates and major bug fixes are released.

---

### Post by pirattrev on 2008-10-30
> **tigrezno said:**
> yes, you've helped hehe I won't be upgrading for now.

so i've guessed that new features are included in 8.10 as "unstable" and will be released to 8.04 when they are really stable, isn't it?

yeah, basically.  The whole ubuntu "process" is trial-and-error.  Stuff gets thrown into the mix for the alpha, the more refined goes into beta, and what comes out of that is the gamma, non-LTS, release. Then once, that release has run it's course [ie non-LTS 1] the stuff gets thrown into the alpha release of the non-LTS 2, along with some other new stuff, which gets tested and refined until the new product is the non-LTS 2 gamma.  This process happens over and over again, until finally it reaches the LTS [delta, as I like to call it] release where the surest of the sure to work stuff is thrown all together (after being alpha'd and beta'd) into a release that is guaranteed to be long lasting and suported. Meanwhile, the non-LTS1 is already underway, testing the new goodies to be tested and refined all over again.

**Chart**
&#945;&#947; --> &#946;&#947; --> &#947; --> &#945;&#916; --> &#946;&#916; --> &#916; --> &#945;&#949; --> &#946;&#949; --> &#949; --> &#945;&#950; --> &#946;&#950; --> &#950; [repeat]
**Key**
&#945; - alpha
&#946; - beta
&#947; - gamma
&#916; - delta
&#949; - epsilon
&#950; - zeta

---

### Post by tigrezno on 2008-10-31
ok, thanks for the support.

I'll play with 8.04 for now :)

---

