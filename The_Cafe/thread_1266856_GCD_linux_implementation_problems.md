---
title: "GCD linux implementation problems?"
date: 2009-09-15
forum: The Cafe
---

### Post by the.dark.lord on 2009-09-15
Check this out: [http://arstechnica.com/open-source/news/2009/09/apple-opens-gcd-challenges-impede-adoption-on-linux.ars](http://arstechnica.com/open-source/news/2009/09/apple-opens-gcd-challenges-impede-adoption-on-linux.ars)

---

### Post by bodyharvester on 2009-09-15
heard about what they did a while ago

honestly, if this stuff appeared on the local news channel as much as it did here in the cafe MS would have riots from protesters demanding an end to their distasteful "tactics"

---

### Post by the.dark.lord on 2009-09-15
> **bodyharvester said:**
> heard about what they did a while ago

honestly, if this stuff appeared on the local news channel as much as it did here in the cafe MS would have riots from protesters demanding an end to their distasteful "tactics"

Too bad, only MS is seen as the bad guy. Apple manages to get away with most stuff!

---

### Post by gnomeuser on 2009-09-15
ah the GPL. Here is great technology which is clearly valuable to everyone but due to a technicality in the license text (which judging from the fact that it was specifically removed in v3 was never intended) we can't have.

That's just silly and all these unintended side effects is why these days I strongly prefer licenses of a simpler nature such as the MS-PL, MIT and BSD licenses. They are far more predictable.

I am starting to believe that the GPL and it's practically religious following these days are doing more harm than good in the strict enforcement of the letter of the license rather than the ideals of it.

---

### Post by bodyharvester on 2009-09-15
> **the.dark.lord said:**
> Too bad, only MS is seen as the bad guy. Apple manages to get away with most stuff!

its interesting you say "seen", think about how many windows users know about MS doing this sort of stuff, then think of all of us who discuss it almost every day. Also many windows users may think of GNU/Linux as the bad guy.:(

to most of the world MS is seen as the greatest thing ever. Apples hides behind its fashion label status to disguise its practices, i-n  m-y  o-p-i-n-i-o-n [for those of you who may have forgotten how to spell it ;)]

---

### Post by 3rdalbum on 2009-09-15
Shared libraries tend to be licensed under LGPL, not GPL; so how does this change the situation?

---

### Post by gnomeuser on 2009-09-15
> **3rdalbum said:**
> Shared libraries tend to be licensed under LGPL, not GPL; so how does this change the situation?

You need to include libdispatch in your application to access the GCD API.

The problem occures for applications that are GPLv2 which unfortunately is quite a few.

---

### Post by ssam on 2009-09-15
or you just write a GPL implementation.

microsoft never released the windows APIs with a GPL compatible license, but that did not stop wine.

---

