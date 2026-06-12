---
title: "Linus comments on Con's departure and why Ingo's patch was chosen"
date: 2007-07-28
forum: The Cafe
---

### Post by matthew on 2007-07-28
From: [http://kerneltrap.org/node/14008](http://kerneltrap.org/node/14008)

[quote=Linus Torvalds]Con wass fixated on one thing, and one thing only, and wasn't interested 
in anythign else - and attacked people who complained. Compare that to 
Ingo, who saw that what Con's scheduler did was good, and tried to solve 
the problems of people who complained.

The ck mailing list is/was also apparently filled with people who all had 
the same issues, which is seriously the *wrong* thing to do. It means that 
any "consensus" coming out of that kind of private list is totally 
worthless, because the people you ask are already in agreement - you have 
a so-called "selection bias", and they just reinforce their own opinions.

Which is why I don't trust mailing lists with a narrow topic. They are 
_useless_. If you cannot get many different people from _different_ areas 
to test your patches, and cannot see the big picture, the end result won't 
likely be very interesting to others, will it?

The fact is, _any_ scheduler is going to have issues. I will bet you 
almost any amount of money that people are going to complain about Ingo's 
scheduler when 2.6.23 is released. That's not the issue: the issue is that 
the exact same thing would have happened with CK too.

So if you are going to have issues with the scheduler, which one do you 
pick: the one where the maintainer has shown that he can maintain 
schedulers for years, can can address problems from _different_ areas of 
life? Or the one where the maintainer argues against people who report 
problems, and is fixated on one single load?

That's really what it boils down to. I was actually planning to merge CK 
for a while. The _code_ didn't faze me.[/quote]The whole page is more interesting, but this was the most poignant point. I don't know Con Kolivas, Ingo Molnar or Linus Torvalds, and I'm not up to speed on anything but the basics of the controversy over kernel schedulers, so I can't comment at all on the dispute.

I can say that I have made choices in the past based on similar criteria, and will do so in the future. I'll take working with the guy who can take criticism and can work with others over the one who responds to comments or complaints with attacks.

---

### Post by nrs on 2007-07-28
[http://lkml.org/lkml/2007/7/28/29](http://lkml.org/lkml/2007/7/28/29)

---

### Post by DaveAK on 2007-07-28
Looks like a good old fashioned pissing match.

---

