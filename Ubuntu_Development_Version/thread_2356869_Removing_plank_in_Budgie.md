---
title: "Removing plank in Budgie"
date: 2017-03-27
forum: Ubuntu Development Version
---

### Post by lysander6662 on 2017-03-27
One of the things that stops me from moving over to Budgie [apart from the current bugs] in the plank. When I first used it I liked it but after a few minutes I find it very irritating. I much prefer the Solus version of Budgie without it. Is there a way to disable it in 17.04? I couldn't find it.

---

### Post by #&amp;thj^% on 2017-03-27
GNOME Tweak Tool

---

### Post by lysander6662 on 2017-03-27
Thanks. I'm surprised there's no option to remove it without the tweak tool. OK, thanks, I'll try that.

---

### Post by fthx on 2017-03-27
just type S-T-A (or whatever works in your language) in GS overview bar, there is a startup apps launcher without starting tweak tool.

---

### Post by lysander6662 on 2017-03-27
Didn't even know that existed in Ubuntu standard. It lists Variety even though I'm sure I uninstalled it [and Caffeine which never starts automatically, it has to be manually done]. I'll try that as well, thanks.

---

### Post by ajgreeny on 2017-03-27
I did not stick with my VM of budgie as I didn't like the DE at all, but why could you simply not run command **sudo apt remove plank**?

If you don't like it and will not use it, why not remove it; or does it take with it a load of dependencies that you do need?

---

### Post by lysander6662 on 2017-03-27
I'm still a newbie to Ubuntu [been using it for about six weeks now] so there's still a lot to learn. I could just remove it via the command, yes. Still, it's good to know there are quite a few options to do so.

---

### Post by davidmohammed on 2017-03-28
its even easier than that - from the menu - run startup applications and untick "budgie-plank"

---

### Post by lysander6662 on 2017-03-28
Excellent, thanks David [I think this point was mentioned above by fthx]. Any plans to integrate such an option into Raven?

---

### Post by davidmohammed on 2017-03-28
For 17.10 we'll be looking at whether it is possible for users to choose their default layout on first logon.

Something like "classic budgie" - no plank topbar, icon-tasklist, clock on rightside
vs "ubuntu budgie" - as current.

think that is possible to implement - need to investigate further.

---

### Post by lysander6662 on 2017-03-28
Yep, that sounds great. Having tried Solus yesterday again, I think it would be good to have the choice, especially since there's a strong focus on customisation.

---

