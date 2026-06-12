---
title: "Can I use hashlimit and connlimit at same time?"
date: 2013-12-11
forum: Security
---

### Post by bissagars on 2013-12-11
Hello, 

I'm seeking help to prevent my server from some DoS attacks, I'm linux novice and during search I found to many things like connlimit, hashlimit, hitcount.

I wonder do I have to use only 1 module or I can still use all the modules connlimit, haslimit and hitcount at the same time?

I hope to find some help as I'm really confusing :/

---

### Post by CharlesA on 2013-12-11
You can load as many modules are you need. I've used conn limit and hitcount at the same time before and it has been fine.

I do not know what hashlimit is, though.

---

