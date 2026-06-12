---
title: "Why is upgrading so complicated?"
date: 2016-11-16
forum: Ubuntu, Linux and OS Chat
---

### Post by Stilian_Zagorov on 2016-11-16
I actually kinda know (or at least I think I know) why, but why don't users get any sort of warning before updating? I have not heard a single person report a successful update. Why is it so simple? Shouldn't there at least be a red warning saying that there is a high chance of failure? (If there is, I didn't see it) 

I understand that Ubuntu is not optimized to run on this and that machine, and it is difficult to install in the first place. The average user will know that a fresh install is better. But what if you're not the average person? What if you're me, or someone's grandma? We will see the prompt prompting us to upgrade, and upgrade. 

I think you can tell why I'm so pissed.

---

### Post by Stilian_Zagorov on 2016-11-16
The title pretty much says it all

(I saw a post that said "Poll: something about Ubuntu upgrades" but it didn't have a poll, so I made one :))

I'm wondering because I recently upgraded incorrectly and Ubuntu is now booting in emergency mode, with no solution (yet).

(I don't know what I did wrong, but the link doesn't do anything on click. Copy/paste if you want to vote :/)
Poll: http://www.strawpoll.me/11664872

---

### Post by coffeecat on 2016-11-16
> **Stilian_Zagorov said:**
> I have not heard a single person report a successful update.

Here you go. Assuming you mean an upgrade - that is, an upgrade from one release to a newer one - I have upgraded Ubuntu systems many times without experiencing problems. So sorry to break your record, but now you have heard of a single person!

Frankly, I believe all this stuff about upgrades causing breakages is grossly overstated. One of the reasons why you are much more likely to hear about broken upgrades rather than uneventful ones, is that people tend to post on forums such as this for help when they encounter problems. They don't post when everything works OK. Strange as it may seem, it's an unusual day when someone posts something like, "Help! I upgraded my Ubuntu system today and nothing went wrong. It's working perfectly. What shall I do?" 

I'd be prepared to bet good money that many of the disastrous upgrades that are mentioned are mostly down to breakage caused by the use of multiple 3rd party repositories, and/or unwise over-tinkering with the nuts and bolts of the system. Many years experience on this forum has taught me that posters often:

[list=1][*]Generalise from the particular.
[*]Fail to mention important facts when asking for help - such as the non-standard way they have modified their system.
[/list]

So, point 1 leads to an attitude that can be summed up as "an upgrade failed for me, therefore all upgrades won't work." And point 2 suggests that such posters also fail to acknowledge that their non-standard modifications may be responsible for the problems they encounter.

---

### Post by QIII on 2016-11-16
Modern Linux distros are rarely difficult to install.  Ubuntu is rarely difficult to upgrade.

In addition to the above, difficulties with upgrades arise primarily and specifically because:

1.  PPAs, non-standard repositories or backports are not de-activated immediately prior to the upgrade.
2.  Proprietary drivers are not uninstalled immediately prior to the upgrade.

---

### Post by ian-weisser on 2016-11-16
coffecat and QIII are right.

I have upgraded many machines for over a decade.
NEVER had a problem with daily upgrades on ANY machine.
Had ONE problem on ONE machine with ONE release-upgrade, years ago...and it was entirely my own fault, left non-Ubuntu software installed.
A second problem long ago was due to coincidental hardware failure - also not Ubuntu's fault.

Thanks to all the testers, including the testers here in the forums, who ensure all those upgrades work well.

---

### Post by Habitual on 2016-11-16
Yes.

---

### Post by Bashing-om on 2016-11-16
Yes.

I have been using - and installing for others - ubuntu for more years than I care to think about .
I do observe the pre-cautions and pre-conditions each and every time I do an upgrade .. and I have never ever had a bad experience - hardware permitting.

saying that ^
[INDENT][INDENT][INDENT]still not even going to cross my fingers the next upgrade
[/INDENT][/INDENT][/INDENT]

---

### Post by oldos2er on 2016-11-16
Yes, many times.

---

### Post by bearlake on 2016-11-16
I have done many upgrades over the years usually to U+1 as well as testing from one version to another.

Never had troubles that I remember.

---

### Post by him610 on 2016-11-16
Yes. Earlier this year, upgraded three different machines from LTS 14.04 to LTS 16.04. One of the machines had previously been upgraded from LTS 12.04 to LTS 14.04. No problems noted. The whole process went smoothly.

A backup of one's important files is recommended before commencing any upgrade.

---

### Post by him610 on 2016-11-16
There is a current poll that asks that very question. You can view the comments of the responders in the link...

[https://ubuntuforums.org/showthread.php?t=2343457]("https://ubuntuforums.org/showthread.php?t=2343457")

---

### Post by QIII on 2016-11-16
Good catch.  Merged.

---

### Post by cariboo on 2016-11-17
The only time I had a problem upgrading was due to a flaky wireless connection. the fix was fairly simple, I just ran:

```
sudo apt-get -f install
```

It took a long time, but eventually the upgrade succeeded.

---

### Post by mastablasta on 2016-11-17
i had it once and as i remember it was this as well:

> **cariboo said:**
> The only time I had a problem upgrading was due to a flaky wireless connection. 



otherwise i did a couple of upgrade and they were fine. the only issue is not to do much with upgrade as it has with drivers. some stuff stopped working/performing as it did before. this would happen in windows and other OS as well. in fact windows will tell you how everything is compatible and that you should really go ahead with the upgrade to improve performance but then after the upgrade is done you might find things such as printers and webcam etc. not working.

---

### Post by Stilian_Zagorov on 2016-12-06
Well,  this was unexpected.  I never read anywhere that you have to delete 3rd party stuff before upgrading.  It makes sense noe,  but if wasn't obvious to me.  one good thing out of this post,  I'll know the next time.  Thanks for all the replies,  I guess :P

---

### Post by ian-weisser on 2016-12-06
[Here is]("https://wiki.debian.org/DontBreakDebian") one place to read it for all Debian and Ubuntu systems.
Much good advice on that particular page.

---

### Post by Geoffrey_Arndt on 2016-12-07
Also upgraded multiple time with zero issues.   But I also disabled all weird 3rd party sources (PPA's), and have "all Intel" systems.    A basic "vanilla" system is actually easy to upgrade.   Also, Stilian, a quick google search would have made it clear what to do.   

Having said that, a one Liner in the appropriate desktop space similar to "Attn all Newbies!!!   Before upgrading, remove proprietary drivers, deactivate (uncheck) all PPA's and make sure _your current system is FULLY updated_ before starting the upgrade to Ubuntu xxxxx.   We have to use the principle of KISS better (keep it simple seniorita . . . !)

---

### Post by Sableyes on 2016-12-09
Have not had a failed upgrade since 2007/2008 time. Pretty sure since then it has been click  button to upgrade and click yes. Not complex at all. I have a current hard drive that has been upgraded though all 6 month releases from 12.04 - 16.04.

The only thing I have had an issue with is degrading of bluetooth audio support in Linux in general and the ATI driver blargh going onto the 16.04 release. Neither issue is a upgrade issue.

---

