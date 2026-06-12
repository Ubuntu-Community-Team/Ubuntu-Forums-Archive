---
title: "Treason uncloaked!"
date: 2008-09-14
forum: Server Platforms
---

### Post by cpetercarter on 2008-09-14
When I check my server logs, I always find a number of entries like this:
 > 1 Time(s): [32267283.448000] TCP: Treason uncloaked! Peer 83.136.15.38:6595/80 shrinks window 984386883:984386884. Repaired.
What is that about?

---

### Post by schettj on 2008-09-14
Google for "Treason uncloaked!"
It's really easy. You'll like it.

Report back what you find. It's pretty much what you're asking others to do for you ;)

---

### Post by cariboo on 2008-09-14
You might want to have a look here for an explanation:

[http://lwn.net/Articles/92727/](http://lwn.net/Articles/92727/)

Jim

---

### Post by cpetercarter on 2008-09-17
Well, thanks for these replies. The answer seems to be that the "Treason uncloaked!" messages are EITHER:
caused by a router somewhere which is stripping out some information from TCP packets;
OR:
an attempt to crash or subvert the server.

The messages are therefore EITHER:
someone else's problem and nothing to worry about
OR:
my problem and I need to think whether the server is sufficiently well protected eg by adding the offending IP addresses to denyhosts.

At the moment I am simply monitoring the messages to see whether there is a consistent pattern. Anyone got any better ideas?

---

### Post by schettj on 2008-09-17
Nope. Sounds reasonable to me. I've never seen one of those messages tho, and my site gets hammered with the usual internet e1ete haxxor attacks... so I'd lean towards the first choice as way more likely.

---

