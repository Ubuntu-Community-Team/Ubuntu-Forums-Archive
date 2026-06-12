---
title: "Why does Ubuntu have so much trouble upgrading smoothly?"
date: 2019-04-30
forum: Ubuntu, Linux and OS Chat
---

### Post by Tadaen_Sylvermane on 2019-04-30
Preface by saying I love Ubuntu. Every computer in my home that can be Ubuntu, is.

We see it all the time. "Fresh install better than upgrade", "Tried upgrade and now system won't boot", or any of a million other things that have the same thing in common... An upgrade that usually failed somehow.

Why is this? What makes Ubuntu so different from Debian, Fedora, CentOS / Red Hat that it is such a problem to upgrade? Why do their upgrades go smoothly 99% of the time but with Ubuntu you have better odds of winning the lottery than a successful upgrade?

Is it PPAs?
Is it simply less tested software?
A less tested upgrade process?
Can anything be done about this?

I just have so much trouble with the idea of believing that Ubuntu is used by many major corporations and that they reinstall every time their is a new LTS on however many thousand servers they have instead of upgrading. It doesn't make any sense. And if they are upgrading smoothly... Why do their upgrades go so well and the average user fails miserably so often? What is different?

---

### Post by crip720 on 2019-04-30
Think the average user probably adds so much stuff to the system over time, that an upgrade has trouble.  Most corporations probably have basically the same system at upgrade as when installed, plus some people who know what they are doing.  Would be nice if there were any stats on problems with upgrade.

---

### Post by poorguy on 2019-04-30
> **crip720 said:**
> Think the average user probably adds so much stuff to the system over time, that an upgrade has trouble.
Could have something to do with it moving older software packages tied to an older kernel and migrating over to a newer kernel.

Seems I read that PPAs and any software packages related to the PPAs should be removed before attempting to do an upgrade.

---

### Post by Frogs Hair on 2019-04-30
Single version upgrades such as (18.04-18.10)  have always worked well on my two computers, but I have not ever tried any LTS upgrades (16.04-18.04).
If it weren't for testing or curiosity about new features I would stick to LTS releases and perform a clean installation when released. PPAs, though automatically disabled can cause problems due to dependencies included with the software that may conflict with official upgrades.

---

### Post by #&amp;thj^% on 2019-04-30
I came straight from 16.04 to 18.04 to 19.04 on this drive.
I always PPA purge first, update and upgrade, then use "sed" 
Smooth as Cheesecake.:)

---

### Post by Geoffrey_Arndt on 2019-04-30
Comparing "home" or consumer users with "Corporate" or company users is faulty.  For example, how many home users have the policies & practices corporations do such as ITL's (Integration Test Labs), ACL's  (access control lists), etc, etc, etc.    Also, they do not "change" the computing environment for the latest and greatest software (we used Office 97 for TEN years before upgrading) . . .

---

### Post by Rubi1200 on 2019-04-30
If you look around at some of the better known Windows forums, tenforums for example, you will find just as many threads about failed updates/upgrades.

I think a lot depends on how much tinkering went on before the upgrade; adding PPAs, customizing desktop environments, tweaking system settings etc.

In general, I always recommend backing up data and then doing a clean install.

---

### Post by Shibblet on 2019-05-01
My only issues come from PPA's that have not been updated as of yet.

For example:  Grub-Customizer PPA does have a Disco Dingo (19.04) version, but Ubuntu-Cleaner only has a Cosmic Cuttlefish (18.10) version (yet).  So, Ubuntu-Cleaner does not get updated.  And you'll get some errors from APT when trying to update or upgrade, because there is no current version of that particular PPA in the system.  

I normally just take out the non-updated PPA's and wait until they are updated.  But there may be a better way to do it that I am not aware of.

The system, however, updates just fine.

---

### Post by mikewhatever on 2019-05-01
Unlike the OP, I won't make groundless claims about avarage users. Upgrades work very well for me, also, I don't see "all the time" ...all this stuff the OP very carelessly claims "we see". 
All in all, the topic is reminicent of the "Why do you beat your wife?" kind of question, the answer to witch is "I've never beaten my wife" followed by a few choice expletives.

---

### Post by Tadaen_Sylvermane on 2019-05-01
Doesn't take much searching to find a large number of those threads. And yes "we see" them all the time. And they are almost always responded to by telling the OP of that thread they should have re-installed instead of upgraded. Maybe I am wrong to compare enterprise users to home users. Just makes the point though. If it works so well, what causes the threads to keep coming every release. For example, I've seen recently about an app called ppa-purge. And it makes sense, remove all external and everything should be fine. Why isn't that mentioned on any of the official docs?

My own anecdotal experience tells me upgrades are a crap shoot. On my server out of 5 attempts, I've rolled back my lvm snapshots 4 times. The last time the upgrade worked but I had other issues that required me to revert to 16.04 to keep Kodi running correctly with MythTV. I've only attempted a couple desktop upgrades, both of which were successful. Even combined that is less than a 50% success rate though. That is terrifying. Multiply it out and it's a real problem.

*EDIT* editing my post as it was out of line.

I don't see how you can't see the regular and consistent threads people post about upgrades gone south. They are so common it's ridiculous. I almost avoid the section because the only constant in the whole forum is "should have done a fresh install". It's rare from my own reading that anyone has any solutions most of the time other than that. Is one of the reasons I left Windows. Got tired of the fresh install nonsense. It should be able to be fixed, not given up on and dumped every time.

---

### Post by QIII on 2019-05-01
The problem with concluding that Ubuntu has "so much trouble upgrading smoothly" is that we never see the threads that *are never started* when updates go perfectly smoothly and without a hitch.  People don't complain when things go right.  We can have no earthly idea what the ratio of failures to attempts may be.

Jumping to any conclusion based on 100 or 300 posts is invalid.  That may represent one percent of attempts.  It may represent 50 percent.  We don't know.  Given the millions of users of *buntu, I favor the notion that this represents a small fraction of users.  But I can't state that categorically.

You have fallen into two simultaneous logical fallacies, I think:

"Argumentum ad ignorantiam":  The argument from ignorance in that you don't know the number of smooth upgrades and, lacking that information, you assume the number to be small because you don't know about them.  ("UFOs can't be definitively proven to be real, so they must not exist")

You compound that fallacy with a Hasty Generalization:  You see complaints, so you conclude that many, most or all attempts end in failure.  ("All Indians walk in single file.  At least the one I saw did.")

---

### Post by DuckHook on 2019-05-01
> **QIII said:**
> The problem with concluding that Ubuntu has "so much trouble upgrading smoothly" is that we never see the threads that *are never started* when updates go perfectly smoothly and without a hitch.  People don't complain when things go right.  We can have no earthly idea what the ratio of failures to attempts may be.

Jumping to any conclusion based on 100 or 300 posts is invalid.  That may represent one percent of attempts.  It may represent 50 percent.  We don't know.  Given the millions of users of *buntu, I favor the notion that this represents a small fraction of users.  But I can't state that categorically.

You have fallen into two simultaneous logical fallacies, I think:

"Argumentum ad ignorantiam":  The argument from ignorance in that you don't know the number of smooth upgrades and, lacking that information, you assume the number to be small because you don't know about them.  ("UFOs can't be definitively proven to be real, so they must not exist")

You compound that fallacy with a Hasty Generalization:  You see complaints, so you conclude that many, most or all attempts end in failure.  ("All Indians walk in single file.  At least the one I saw did.")

&#8593;&#8593;&#8593;  …a heart-felt \\:D/ from me.  &#8593;&#8593;&#8593;

---

### Post by Shibblet on 2019-05-02
> **QIII said:**
> The problem with concluding that Ubuntu has "so much trouble upgrading smoothly" is that we never see the threads that *are never started* when updates go perfectly smoothly and without a hitch.  People don't complain when things go right.  We can have no earthly idea what the ratio of failures to attempts may be.

Jumping to any conclusion based on 100 or 300 posts is invalid.  That may represent one percent of attempts.  It may represent 50 percent.  We don't know.  Given the millions of users of *buntu, I favor the notion that this represents a small fraction of users.  But I can't state that categorically.

You have fallen into two simultaneous logical fallacies, I think:

"Argumentum ad ignorantiam":  The argument from ignorance in that you don't know the number of smooth upgrades and, lacking that information, you assume the number to be small because you don't know about them.  ("UFOs can't be definitively proven to be real, so they must not exist")

You compound that fallacy with a Hasty Generalization:  You see complaints, so you conclude that many, most or all attempts end in failure.  ("All Indians walk in single file.  At least the one I saw did.")

[IMG]https://media.makeameme.org/created/i-find-your-mye9ue.jpg[/IMG]

---

### Post by him610 on 2019-05-03
Do not agree that upgrades are problematic.
My spouse's laptop came with Ubuntu LTS 12.04 when we bought it several years ago. Since then, it has been upgraded to LTS 14.04 then to LTS 16.04 with no issues whatsoever; however, I intend to complete a new installation on spouse's laptop with Xubuntu 18.04 in the near future after backing up all personal and data files.

---

### Post by PaulW2U on 2019-05-03
> **him610 said:**
> Do not agree that upgrades are problematic.
I agree with your disagreement. :)

At the time of the 18.04 release I had three ageing or inferior laptops running Xubuntu 16.04 or 17.10. I upgraded each of them to Xubuntu 18·04 but while one failed dismally the other two were successful. So I installed Xubuntu 18.04 afresh on to the one on which the upgrade failed but I still had problems with suspending. A hardware specific problem?

Cutting a long story short, the two oldest laptops are now in the process of being disposed of. The third is in daily use and shows no signs of the upgrade not being 100% successful. :D

---

### Post by Tadaen_Sylvermane on 2019-05-04
> **QIII said:**
> The problem with concluding that Ubuntu has "so much trouble upgrading smoothly" is that we never see the threads that *are never started* when updates go perfectly smoothly and without a hitch.  People don't complain when things go right.  We can have no earthly idea what the ratio of failures to attempts may be.

Jumping to any conclusion based on 100 or 300 posts is invalid.  That may represent one percent of attempts.  It may represent 50 percent.  We don't know.  Given the millions of users of *buntu, I favor the notion that this represents a small fraction of users.  But I can't state that categorically.

You have fallen into two simultaneous logical fallacies, I think:

"Argumentum ad ignorantiam":  The argument from ignorance in that you don't know the number of smooth upgrades and, lacking that information, you assume the number to be small because you don't know about them.  ("UFOs can't be definitively proven to be real, so they must not exist")

You compound that fallacy with a Hasty Generalization:  You see complaints, so you conclude that many, most or all attempts end in failure.  ("All Indians walk in single file.  At least the one I saw did.")

Didn't even consider that honestly. Just see so many, why would someone report something did what it was supposed to do. My apologies for not thinking this thought all the way through to all. I guess I let my own experiences dictate what is happening to everyone else. Maybe I am doing something wrong. I'll need to do some testing. Appreciate the responses both for and against. Opens my mind a bit. Can't believe I never even thought from that perspective.

---

### Post by monkeybrain20122 on 2019-05-04
> **Rubi1200 said:**
> 
I think a lot depends on how much tinkering went on before the upgrade; adding PPAs, customizing desktop environments, tweaking system settings etc.


Agreed, the less tinkering the more likely for a smooth upgrade but then the less reason to "upgrade". People usually think they would rather "upgrade" than clean install because they have custom settings, but "upgrade" is more likely to fail because of those custom settings. So there is really no point to "upgrade", clean install is a lot faster comparing to "upgrade" on a pristine system(where "upgrade" likely works)

---

### Post by mrdc76 on 2019-05-06
> **QIII said:**
> The problem with concluding that Ubuntu has "so much trouble upgrading smoothly" is that we never see the threads that *are never started* when updates go perfectly smoothly and without a hitch.  People don't complain when things go right.  We can have no earthly idea what the ratio of failures to attempts may be.


People also have problems with clean installs. Those threads appear every once in a while.

---

### Post by Daveski17 on 2019-05-06
I upgraded from Trusty to Xenial with no issues. Before I upgraded almost everyone I asked opined that I needed a fresh install as if it was gospel or something. It would be interesting to know just how many successful upgrades on average there really are.

---

### Post by drvshrm on 2019-05-07
I upgraded my ubuntu 16.04 to 18.04 and didn't faced any problem in upgrading...Also not seeing any major change in performance till now...But I too suggest a fresh install instead of upgrading not because of any performance issues but because of my mind set...

---

### Post by Frogs Hair on 2019-05-07
Info based on 66% of known 18.04 users only. 80/20 clean installation vs upgrade. There is no data on installation or upgrade issues. 

 [https://www.ubuntu.com/desktop/statistics#configuration](https://www.ubuntu.com/desktop/statistics#configuration)

---

### Post by mastablasta on 2019-05-08
well you basically can't upgrade Kubuntu 14.04 to 16.04. the bug is known for at least 3 years and solution is to disable upgrade message or do a backup and reinstall. no one was bothered to fix it. i imagine the thinking in Ubunto is somewhat similar. it will work most of the time so they obviously don't bother too much with testing it.

personally i had mixed experience. sometimes it went straight, sometimes it broke. i don't have many PPA and they are now disabled on upgrade anyway. i am not sure why the upgrade would actually stop or break. i mean it just overwrites the old data with new data, removes some items no longer supported, probably resets some settings (or leave them as they are) and that's it. it went like that on server (very smooth). i am not sure why there is so many issues on desktop. why so often it stops in the middle. moreover i am note sure why at least you can't do a successful upgrade with a live cd at hand. boot live, overwrite data, remove the not needed data-* and reboot.

windows upgrades are relatively smooth (not counting the latest bugs). At least when they find the problem they stop the uprgade until they resolve it. i remember back in the days i did 95 to 98 to XP with no issues. and they were all "customised" a lot more than linux.

---

### Post by crip720 on 2019-05-17
I have an old P4 laptop with a cyberblade graphics.  12.04 worked very well on it, but anything after did not.  When 16.04 came out, figured would try again.  Seemed like every 16.04 I put in to try worked, but the LTS lubuntu(LXDE?) I was using since 12.04 would not.  Don't think any OS maker can have every option for every computer in their installers/upgraders.

---

### Post by kevhilton on 2019-05-26
I can't say I've had a large problem with Ubuntu Updates -- I've updated on install from 14.04 to 16.04 to 18.04 and things seems to work.  I don't install anything from a PPA so maybe that counts for something. I dislike upgrades as much as the next person, however if you go into the process knowing there will be problems -- and wait until the 1 point release after a LTS upgrade -- usually you'll find what you want in terms of information on how to solve the problems.  In actuality however rolling release distributions for home use -- like Arch -- seem a lot less problematic since there truly isn't a major upgrade cycle (I'm not saying there isn't problem with the rolling release cycle just saying for a home user and small server user like me -- the problems are less).  I suppose rolling release however is much less supported in corporate world however.

---

