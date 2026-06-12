---
title: "Dekko crashes as soon as it opens"
date: 2017-01-01
forum: Ubuntu Phone and Tablet
---

### Post by Roland_G86 on 2017-01-01
I bought a BQ E5 maybe a year ago, a demo, just before they went on sale worldwide. At first Dekko was working, and I added some accounts to it.  Then one day, maybe six months or more ago, it started crashing as soon as it starts.  I waited hoping an upgrade might help, but the last update I did on Dec 17 didn't help.  I've tried uninstalling it and then reinstalling, but no luck there either.

I love the phone otherwise, mainly flawless (except for the battery charge indicator) but I can't really show it off to anyone if the main mail client doesn't work.

Anyone else having this problem?  Any suggestions on what to do?

Thanks!
Roland

---

### Post by woody2707-3 on 2017-01-01
Have had same issue too. Normally for me closing and restarting Dekko has fixed the problem after a couple of attempts. Annoying I know also has happened on tablet and mx 4. You might want to check out the bug reports to see if one has been filed.

---

### Post by lapor2 on 2017-01-01
Dekko 1.0 should land soon ([launchpad]("https://launchpad.net/dekko/+milestone/1.0-beta")). That should fix a lot of bugs.
I think that Dan is waiting for snap version of Ubuntu touch. Or maybe not...

---

### Post by Roland_G86 on 2017-01-08
Thanks for the replies.  I found this posted on the launchpad site, from a few days ago

> The Dekko project will no longer be releasing or supporting click packages for Ubuntu Touch, with focus now being on snap packages and following the future of the platform.

> Over the next week I will be going through the current bug list and closing any bugs related to the current Ubuntu Touch version as there will be no active development going forward.

[https://launchpad.net/dekko/+announcements](https://launchpad.net/dekko/+announcements)

So I think that solves my questions.

---

### Post by krusty8 on 2017-01-10
You can try deleting dekkos files using ubuntu touch tweak tool or from commandline. 

Off of the top of my head something like ./cache/dekko ./local/share/dekko and ./config/dekko or similar

---

