---
title: "Wrong assigned Natty upgrade announcement"
date: 2011-04-29
forum: The Cafe
---

### Post by Jallu59 on 2011-04-29
Hey

This is to developers.

Why do ordinary Maverick users get an ad/announcement of Natty release-upgrade although they have no privileges to execute it ?

This behavior also break the convention that users without admin rights do not get update announcements at all, which is in my opinion a good practice, that should be continued. This Natty update ad is very annoying with senior and other less technically oriented users, who are not capable neither interested in system administration.

It not even wise to have an release update to untechnical users until two months after the release, when all major update bugs have been detected.

No I do get tens of calls from confused users of the computers under my supervision. Not good.

Yours

Jari J. Lehtinen
an elder PC-pro from Turku, Finland

---

### Post by Sef on 2011-04-29
Moved to the Community Cafe.

You can set it to not show the upgrade releases.

Applications > Ubuntu Software Center > Updates > Release upgrade > Never

---

### Post by Jallu59 on 2011-04-29
was I  using wrong words ? So far it has been that only administrators  have received announcements of available updates. But this announcement breaks this "rule" because it is shown ti every user, also to those who do not have enough privileges and what's more remarkable not enough computer skills to understand the whole thing.

So please NO update information to unprivileged users PLEASE.

May I  present an example: My daughters 84 year old mother-in-law uses Xubuntu which is tailored for her having only large icons of browser(Firefox) and f-spot on her desktop. She has got absolutely no skills for administration. Apparently the popping Natty ad-window makes her totally confused. I am now just waiting for a frustrated call.

Yours Jallu59

---

### Post by grahammechanical on 2011-04-30
Yes. I know what you are talking about. I got an advert yesterday giving me the option to upgrade there and then. But I like to update after midnight as it does not add to my ISP download limit. Also, Downloads are very slow for the first few days after a distribution release. So, I wonder what the point of it was. I also wondered how it was done and if I could expect other unsolicited adverts.

Regards.

---

### Post by 3rdalbum on 2011-04-30
> **Jallu59 said:**
> It not even wise to have an release update to untechnical users until two months after the release, when all major update bugs have been detected.

Well, firstly, how do you expect a copy of Ubuntu to differentiate between technical and non-technical users, to display a release announcement?

And secondly, how are you going to detect bugs if you're telling people not to use the software?

And thirdly, they release the software when they've fixed all critical bugs that they know about.

Fourthly, that's why I suggest people get pre-release versions of Ubuntu whenever they can possibly help test - it makes the actual release better.

---

### Post by Throne777 on 2011-04-30
> **3rdalbum said:**
> Well, firstly, how do you expect a copy of Ubuntu to differentiate between technical and non-technical users, to display a release announcement?

Check to see if the user is running Conky? :p

---

### Post by koenn on 2011-04-30
> **3rdalbum said:**
> Well, firstly, how do you expect a copy of Ubuntu to differentiate between technical and non-technical users, to display a release announcement?

that was answered in the OP:
don't display the release announcement to unprivileged users, i.e. users that can't sudo to eleveted "admin" or "root" privileges that are required to actually execute an upgrade.

The answer to the rest of your questions follows from that : on any PC, there'll be at least 1 account with sysadmin rights - he'll get notified and do the upgrade (or not).

The part you're not seeing that there can be more than one account/user on a computer - if I's set up accounts on my PC for all family members, those would be accounts that can _not_ do a release upgrade. 
That's elementary system administration.

---

### Post by Lucradia on 2011-04-30
> **Throne777 said:**
> Check to see if the user is running Conky? :p

+1 to that. I never run conky, so I'd rather use upgrade manager to show it :V

Also, Ubuntu fixed the issue of having really old releases show the newest release, as it pulled way too many packages at once (some old packages had to be re-installed over re-installs of upgrades because the packages require you to install versions in sequence.)

Thus, old releases will only show the next version up (IE: 8.04 > 8.10 and further)

---

### Post by santaslittlehelper on 2011-04-30
Sounds like a very valid bug/feature request that I would like to see too maybe go report at /launchpad.net/ubuntu/.

---

