---
title: "bug, dapper, and fixed as wontfix"
date: 2006-03-20
forum: The Cafe
---

### Post by towsonu2003 on 2006-03-20
this is basically a rant from someone (me) unhappy that Breezy isn't getting much attention any more. Also, a question for more experienced Linux users. 

Basically, here is the bug I filed: [https://launchpad.net/distros/ubuntu/+source/ooqstart/+bug/33425](https://launchpad.net/distros/ubuntu/+source/ooqstart/+bug/33425)

The bug was closed as "fix released". But I didn't get any fix (patch or something), so I changed its status back ("unconfirmed"). Then I got this (which closed the bug as "fix released" again):
[quote=dev]
breezy won't get a fix, the fixed is released in the current dapper development version.
[/quote]

So, Dapper isn't released yet, but breezy bug gets closed bc it's fixed in Dapper? Even if dapper was released, isn't Breezy supposed to be supported by devs for another 4-6 months? :confused: 

from my POV, when this happens, bug is closed as "won't fix" so the bug statistics will show how many Breezy bugs are fixed and how many are abandoned. At worst, bug would be labeled as "in progress" until Dapper is officially released. But, of course, I have no experience to discuss this with a dev, especially not in a bug report (which, I guess, isn't the place to discuss these things anyway). 

In brief, I won't be able to upgrade to Dapper for a while. Does this mean my Breezy will be abandoned and its bugs will not be fixed (except, maybe security bugs, though suspicious) although it is supposed to have more support time left (4-6 months)? :confused:

---

### Post by poofyhairguy on 2006-03-20
[QUOTE=towsonu2003]
So, Dapper isn't released yet, but breezy bug gets closed bc it's fixed in Dapper? [/QUOTE]

Yes. No more development will be done on Breezy.

> 
Even if dapper was released, isn't Breezy supposed to be supported by devs for another 4-6 months? 

Yes, but supported means "will fix any security issues we find" not "we will fix bugs."

I think you are very close to fully understanding what the Ubuntu development model is like!

---

### Post by briancurtin on 2006-03-20
same thing happens with SuSE, and pretty much everything ever. they dont do dev work on old versions, just security fixes basically. a week after 10.0 came out, i filed a 9.3 bug and went on and helped them figure out what the problem was and such, and was told "ok we just made the patch and fixed it, go upgrade to 10.0 to get it"

---

### Post by towsonu2003 on 2006-03-20
[QUOTE=poofyhairguy]
I think you are very close to fully understanding what the Ubuntu development model is like![/QUOTE]
so bug fixes are part of 'development'? that's weird
[quote=briancurtin]same thing happens with SuSE, and pretty much everything ever. they dont do dev work on old versions, just security fixes basically. a week after 10.0 came out, i filed a 9.3 bug and went on and helped them figure out what the problem was and such, and was told "ok we just made the patch and fixed it, go upgrade to 10.0 to get it"[/quote]
that's not only weird but mean -well, there's too much to learn...


PS. no offense, trying to make sense of this while ranting at the same time ;)

---

### Post by poofyhairguy on 2006-03-20
[QUOTE=towsonu2003]so bug fixes are part of 'development'? 
[/QUOTE]

Yes. I'll try to explain the best I can.

The Ubuntu developers (well....actually more like Mark) don't see the Ubuntu releases as seperate entities. They are all one in a way.

I must use an example. Its not like Warty is Windows 98 and Breezy is XP. Its more like Hoary was XP SP1, Breezy was XP SP2, and Dapper will be whatever the last version of XP will be.

Thats why Mark is making such a big deal about Dapper- in many ways in the first "real" release and he plans to support it for so long. All the Ubuntus up to now have been building up to Dapper.

---

### Post by klahjn on 2006-03-20
I understand both sides of this argument.  On the one hand, the user is happy with thier configuration on the system they have, so they really don't want to upgrade and possibly bork thier system to get a fix that should work.  On the other hand, i think the devs release the new version and are working on that, so they don't really want to go back and re-fix it in the old version for the fact that it wastes time doing double the work, when the time they used could be better spent on the newest release.  to them, it would be like making internet explorer 7 work on windows 3.11.  drastic comparison, but mostly accurate.

---

### Post by towsonu2003 on 2006-03-20
@poofyhairguy: ok, this is weird, but also make sense somehow. 

thanks for the explanation :)

PS. is this true for other linux distros (as in "Slackware 10 is the developed version of 7, not a new "release" release")?

---

### Post by poofyhairguy on 2006-03-20
[QUOTE=towsonu2003]@poofyhairguy: ok, this is weird, but also make sense somehow. 

thanks for the explanation :)[/QUOTE]

It could be explained better, but I tried my best.

> 
PS. is this true for other linux distros (as in "Slackware 10 is the developed version of 7, not a new "release" release")?

Hmm....I think it only applies to distros that freeze development at points. But I don't know that much about non Ubuntu distros, so I won't say for sure.

---

### Post by bugmenot on 2006-03-20
Seeing that the fix involved a new version of OpenOffice, I can see why things like this will only go into the next release.

And as others already have mentioned, support largely means security fixes, not bug fixes, though I'm sure there are cases where serious bugs are fixed after a release. (For example, hal integration in KDE was borked for breezy and this was fixed).

P.S.:
As older versions still get security fixes and as dapper will also mainly get security and not bug fixes, just like any other ubuntu version, your analogy with the service packs doesn't really make too much sense.

---

### Post by poofyhairguy on 2006-03-20
[QUOTE=bugmenot] your analogy with the service packs doesn't really make too much sense.[/QUOTE]

True. I will admit it was not the best way to explain it.

---

### Post by imagine on 2006-03-20
Umm, some Windows patches indeed require a certain service pack level, but not all do and not always the latest service pack has to be installed. So the analogy wasn't that bad.

---

### Post by towsonu2003 on 2006-03-20
I don't really care about the analogy as long as it serves the need. ubuntu is under constant development, regardless of the name. It's a weird concept, and it requires absolute perfection and polish of dist-upgrade, but I can live with it. ;)

---

