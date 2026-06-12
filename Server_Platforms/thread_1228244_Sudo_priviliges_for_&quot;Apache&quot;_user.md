---
title: "Sudo priviliges for &quot;Apache&quot; user"
date: 2009-07-31
forum: Server Platforms
---

### Post by TheDelChop on 2009-07-31
Guys,

Installing Apache on my slice, and am trying to do my best to make it secure as possible.  I've been reading about things and I've come across something I think is a great idea:

Even though its the root who will start apache, its better if I have another user (apache) actually take over once the server has started.

My only question is this:  Do I need to give the user "apache" sudo rights?  My initial assumption is no, since that would defeat the purpose of not having "root" serve the hits to my site, but will "apache" need to have sudo rights at any time?

Thanks,

Joe

---

### Post by samosamo on 2009-07-31
Absolutely not. Where did you get this idea...?

---

### Post by TheDelChop on 2009-08-01
From my own noob brain. :) Ty for confirming that it wasn't a good idea.

---

