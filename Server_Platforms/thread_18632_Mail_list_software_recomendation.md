---
title: "Mail list software recomendation"
date: 2005-03-07
forum: Server Platforms
---

### Post by rvetrovec on 2005-03-07
Greetings all

i;m setting up a mail server and i'm looking for, from your point of view, the best mail list software. The utilitie it's for a university to advice the students about news on campus

Any recomendations?

Greetings

---

### Post by Jad on 2005-03-08
sure thing its Mailman!

---

### Post by meyerm on 2005-03-10
Depends on how big it will be and how complicated your setup is.

We use mailman here (university) and host a few tens lists. Some with special configurations. It's quite often that mailman takes our mailserver down (not crashing but sucking too much ressources or keeping mails in an endless loop and packing it into another mail until it gets too big (bug in the spamrules) ).

A bigger problem is that we found several really trivial bugs in the software - they will only show if you must play around with your hostname. Well, short: the software isn't sooo well tested. Before I set up a mailman list at work, I will have another look on other list managers. We'll see...

But if it is a small setup (few lists, only a hundred users or so (of course you can get thousands of users, but the hardware need goes up far too fast) and no special needs) then mailman is quite nice. Thanks to its web interface, you can let your users configure their lists. You just need to say "I want a list with that name", and even that with a web frontend if you want. But there are also CLI programs. So, from this point of view it is the best ML manager I found so far.

---

