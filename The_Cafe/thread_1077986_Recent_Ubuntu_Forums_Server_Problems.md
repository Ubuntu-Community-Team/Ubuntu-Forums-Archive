---
title: "Recent Ubuntu Forums Server Problems"
date: 2009-02-22
forum: The Cafe
---

### Post by Favux on 2009-02-22
I gather the Forum uses MySQL.  I don't know which version.  Even if it's not 5.1 I think the following blog by Michael "Monty" Widenius is interesting:

[http://monty-says.blogspot.com/2008/11/oops-we-did-it-again-mysql-51-released.html]("http://monty-says.blogspot.com/2008/11/oops-we-did-it-again-mysql-51-released.html")

---

### Post by Thirtysixway on 2009-02-22
It wasn't a mysql error that took down the forum.  I think it was more of a performance issue with thousands of users and thousands of threads, the servers couldn't handle it.

---

### Post by Favux on 2009-02-22
OK, but then what were the database corruption issues they kept referring to?  Monty does say that your chances of running into the bugs depends on how you've configured MySQL.  But some of the bugs seemed eerily familiar.

---

### Post by Thirtysixway on 2009-02-23
[http://ubuntuforums.org/showthread.php?t=1071591](http://ubuntuforums.org/showthread.php?t=1071591)

---

### Post by Favux on 2009-02-23
Hi Thirtysixway,

Sure I've been following that thread.  Maybe you missed this thread started by ubuntu-geek:

[http://ubuntuforums.org/showthread.php?t=1039481]("http://ubuntuforums.org/showthread.php?t=1039481")

Again, to my admittedly limited understanding, ubuntu-geek (who runs the forum, right?) seems to be talking about issues that could relate to the bugs Monty was discussing.

---

### Post by tubezninja on 2009-02-23
This of course assumes that UF is/was using MySQL 5.1 at the time the corruption occurred.  Maybe I missed it, but I don't think there has been a specific mention of what version of MySQL this site is in fact using.  I could be wrong though, I admit I haven't been following that discussion very well.

In any case, **would** UF be so quick to jump to 5.1?  Intrepid Ibex ships with 5.0.67.  While I don't presume that UF would by default use whatever's in the package repos, it would make sense not to go with something newer than what is deemed "stable" without a very good reason, no?

Then again, this is all just speculation.

---

### Post by matthew on 2009-02-23
We are still using the 5.0 series of MySQL.

---

### Post by Favux on 2009-02-23
Hi matthew,

Good I was hoping someone who knew would tell us.  So it's MySQL 5.0.

Hi scaredpoet,

Of course this is speculation.  The thing is that Monty's blog mentions 5.0 bugs too, not just 5.1 bugs.
> Don't expect that all critical bugs that you may have encountered in 5.0 to be fixed in 5.1. Even if we have fixed a big majority of the bugs from 5.0 some really critical ones still haven't been addressed.
> We still have 20 known and tagged crashing and wrong result bugs in 5.1 35 more if we add the known crashing bugs from 5.0 that are likely to also be present in 5.1.
and then he goes on to discuss some of the bugs.

So the speculation I guess would go something like:

Given the increase in forum use eventually the database was "stressed" enough to unmask some lurking bugs.  Or perhaps in an attempt to deal with the increased traffic a configuration change was made that unmasked, what had been to that point, a potential bug.

I hope it is just equipment and that somehow ubuntu-geek comes up with some new stuff.

Bringing "solved" back seems important to me.  And getting "thanks" and "ignore thread" back would also be good.  I know they're still planning on re-implementing some of this.

---

### Post by matthew on 2009-02-23
At this point, we are mostly convinced our problems are hardware related. We hope to have some new equipment in place soon, at which point we hope to bring back some of the features that were helpful, like thanks and marking threads solved.

---

### Post by Favux on 2009-02-23
Hi matthew,

Great!  That is good news.  I hope the installation goes smoothly and quickly.  Ubuntu-geek and the rest of the team are entitled to a break it seems to me.

---

