---
title: "Why bother posting bug reports?"
date: 2006-08-24
forum: The Cafe
---

### Post by christian.convey on 2006-08-24
The number of bugs already in the tracker is way, way beyond what Ubuntu's developers can deal with in the next 5 years.

Many of the bugs I've filed months ago haven't even been triaged yet.

Is there really a point in filing any non-super-critical bug?  At the moment, the bug tracker seems like a well-intentioned version of /dev/null.

---

### Post by x64Jimbo on 2006-08-24
The tracker, no matter how far behind it may be, is necessary because those bugs will need fixing one of these days, and if there isn't a record of it, the devs might not ever know about it. /dev/null deletes its inputs right away, but at least the tracker keeps all of its inputs in a database.

---

### Post by curuxz on 2006-08-24
I think this threads title makes the top 10 most retarded comments of 2006 shorlist.

I mean come on! have you an idea how open source development works, without the bug reports, no matter how many, the devs are practicaly blind to how software works in the real world.

Please everybody continue submitting bug reports its the only way we can improve is if we tell the devs where the problems are they have enough on their plate without wasting time testing stuff them selfs!

---

### Post by win_zik on 2006-08-24
> **curuxz said:**
> I think this threads title makes the top 10 most retarded comments of 2006 shorlist.

If you read beyond the title it's pretty clear that the OP is frustrated with the way bugs are handled by the Ubuntu devs and not questioning the usefulness of bugs in general.

---

### Post by christian.convey on 2006-08-24
> I think this threads title makes the top 10 most retarded comments of 2006 shorlist. Thanks for sharing.  Now on to more substantive discussion...

> have you an idea how open source development works Yes, I have some idea, thanks for asking.

Here's my point:  It's obviously worth submitting a bug report if there's a 1:5 chance that it will help get the bug fixed.  But what about when there's a 1:500 change it will get fixed?  Or 1:1000?

There's something about Ubuntu's process right now that makes submitting non-critical bugs commonly pointless.  Perhaps the problem is that we're filing bugs into Ubuntu's bug database rather than the package maintainers' databases directly - I'm not sure.

But when only a tiny fraction of the bugs I've submitted have even ***been triaged*** after several months, it's time to question to point of even filing them.  

If you file a bug in Malone and no one triages it, did it make a sound?

---

### Post by aysiu on 2006-08-24
I think you should leave it up to the developers to decide what they have time to get around to.

If you file it and they don't get around to it for months or a year even... then so be it. But if you don't file it, there's no way they will ever get to it.

So in the case of your hypothetical bug that won't be fixed for a long time or maybe never, would you rather have a 2% chance it'll get fixed or 0%. If you file it, it'll be 2% (or maybe more), but if you don't file it, it'll be 0%.

I think the bug reporting system sounds great in theory, but every bug report I've filed has:

1. Been ignored
2. Been deemed undoable or undesirable
3. Been labeled as not able to be reproduced
4. Been labeled a wishlist item

---

### Post by Virogenesis on 2006-08-24
Well alot of bugs, won't be just ubuntu bugs they will appear in other distros and this allows other distros to use ubuntu's fantastic community to improve their own. 

So yes, bugs should be reported no matter what BUT expect a list that some will take abit longer than others.

---

### Post by christian.convey on 2006-08-24
>  would you rather have a 2% chance it'll get fixed or 0%. I think you've come to the kernel of the issue:
Do I want to spend 10 minutes filing a report with a 2% change of payoff, or 0 minutes filing a report with 0% change of payoff?

It's a risk/reward problem, and there's no one obvious answer in our case.

As an interesting aside, if we *stop* posting bugs for a while, there's a possibility that the developers will reduce the # of untriaged bugs.  That means that subsequently posted bugs will likely have a > 2% change of being dealt with.  I'm guessing this because of the current high rate at which reporting is outpacing triaging/fixing.

My suspicion, however, is that most bugs we file these days will eventually be thrown in the trash without ever having been looked at.  The developers will say, "That bug was filed with a 2-year-old version of the software?  I'm not looking at it - I've already got enough bugs filed against the current version of the software."

---

### Post by Virogenesis on 2006-08-24
Don't treat it as a ubuntu thing bugs get fixed in other distos then appear in ubuntu aswell so bugs affecting mepis will get sorted and will appear back in ubuntu.

---

### Post by aysiu on 2006-08-24
If 10 minutes is too much of your time to not necessarily get a result, then don't file one.

That doesn't mean that the community as a whole will stop filing bug reports, though. It means *you* will stop filing them.

I'm a bit frustrated that the developers have deliberately chosen not to fix the bugs I've reported, but I'm glad I took the time to file them anyway, just on the off chance that they might fix them. That's my choice.

---

### Post by Jucato on 2006-08-24
I'm more frustrated on how to file a bug report properly than it about it not being read. I mean, one of the ways for users to contribute to the development of a distro or open source project is by filing bug reports. But how can regular users, who wish to make bug reports because they want to help but can't code, easily file these reports? It would be probably nice if they would post a sort of guide to help people file proper bug reports, like what to include, etc.

Also, the number of bug reports have prompted developers to ask/look for a new kind of "job", one who's sole purpose it to triage bug reports. Maybe that's another area where users can help. But then, again, they would have to understand how bug reports work...

---

### Post by aysiu on 2006-08-24
I'm with you on that Fenyx. LordHunter317 scolded me on one of my *sudo* bug reports saying that I was filing it on the wrong package and didn't know what I was talking about.

Well, the end-user often *doesn't* know what she's talking about! All she sees an error whenever she does X, Y, and Z. She doesn't know what package it relates to. She doesn't know what's causing the error. That's why she's filing the bug report.

Yes, there needs to be a much easier system for filing bug reports. How do you get that, though?

---

### Post by Miguel on 2006-08-24
> **aysiu said:**
> 
Well, the end-user often *doesn't* know what she's talking about! All she sees an error whenever she does X, Y, and Z. She doesn't know what package it relates to. She doesn't know what's causing the error. That's why she's filing the bug report.

Yes, there needs to be a much easier system for filing bug reports. How do you get that, though?

Dear Aysiu,

You really nailed this one. It's the classical communication problem between the not-technically-skilled user and the technicall programmer. It's like having a psychologist describing me a weird behaviour he had while solving Schrodinger's equation (I'm a physicist). Sometimes, that behaviour "is not a bug, it's a feature!" (tm). Sometimes, they don't speak the same language, and get nowhere. However, don't despair. It's also likely that both end up understanding each other and so the bug can get fixed :).

If you really need your bug to be fully examined, install debian etch and file bugs. It's just a different philosophy. Personally, I'd say I've had mixed luck, though I've never been ignored. Most of the time, it was already filed (I tend to do some nice search before filling anything).

I'll start my last but one paragraph by stating the things a free software user can do to feel better with what he has recieved. He can code. He can write docs. He can translate. He can fill bugs. He can help users. He can do nothing. Seeing as the spanish translation is almost full, and that I have enough work with writing articles, I fill bugs and try to help some users.

Two curious bugs: dapper-updates' cups (1.2.2) is still nerfed (running as cupsys, not reading shadow, etc). However, the web interface (have a look at [http://localhost:631](http://localhost:631) ) doesn't warn you that you can't make changes. Another one is with cfdisk, a partition editing utility (CLI). As stated, I have it in spanish. It obviously asks for confirmation. Well, the spanish confirmation is "sí", not "si" (note the i). This program won't let me put "í", either typing or copy-pasting, thus rendering it unusable. Will I report them? Yes, but let me have my dinner first 8) 

Have a nice night,

Miguel

---

### Post by aysiu on 2006-08-24
I write docs, mostly.

I try to file bug reports, but apparently I don't know enough about Ubuntu to do so properly.

---

### Post by Miguel on 2006-08-24
> **aysiu said:**
> 
I try to file bug reports, but apparently I don't know enough about Ubuntu to do so properly.

It might be that the idea of perfect software the developers have does not coincide with yours. You know, I would have never supressed the "lock screen after X time" from the screensaver. It happens.

BTW: One of the reasons for filling bugs to your distro is organizing them properly to re-send the bugs to the original package coders. Or at least that's what I read somewhere else.

---

### Post by bailout on 2006-08-24
I would agree that the bug reporting system is difficult to use and confusing for most people. As has been said, whether making it more accessable would actually be an improvement or not is debateable as there already seem to be more bugs than the developers can cope with.

---

### Post by Jucato on 2006-08-24
> **bailout said:**
> I would agree that the bug reporting system is difficult to use and confusing for most people. As has been said, whether making it more accessable would actually be an improvement or not is debateable as there already seem to be more bugs than the developers can cope with.

Making bug reporting more accessible and understandable to non-technical people also involves making the bug search/query tool also accessible, understandable, and efficient. For example (in bugs.kde.org), you can't use 3 letter words for search keywords. Then how will I search for CSS, KJS, Ark, etc.? Or in Launchpad, how do you find a bug, without knowing either the bug report # or the product name? But I guess this ultimately has to do with the bug tracker like Malone or Bugzilla.

What does improving the bug search/query system have to do with what bailout said? Well, if the search system was improved, it could lessen the amount of duplicate bug reports. It will the developer's job easier, too, when looking for bugs, because all the info and confirmation from other users will be found in just one spot, and not have "This is a duplicate of bug ####" links.


@Miguel: True, users can contribute to the development of a distro in more ways than one: coding, documentation, bug reporting, artwork, translation, offering help. But all of these, except for bug reporting and artwork, requires you to really, really know the system first (except for offering help, but it does require you to know what you are doing). I've also seen articles lately about how bug reporting is one good way for non-coding users to help developers. But until bug reporting is made easier for these non-coders, we're gonna have lots of improperly filed bugs, duplicate bugs, or no bug reports at all.

---

### Post by TheRingmaster on 2006-08-24
I have a solution for all of this. Lets find more developers fast!

---

