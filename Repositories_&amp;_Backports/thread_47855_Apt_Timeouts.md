---
title: "Apt Timeouts"
date: 2005-07-10
forum: Repositories &amp; Backports
---

### Post by SauRoN on 2005-07-10
First, this is my very person post!

Now on to the problem.

I've running Kubuntu on my machine, which was working perfectly fine when I was still using 56K.

Recently however I switched to DSL, and now for some or other reason APT isn't working.

It keeps on timing out to every repository I've tried.

The worst part is, that I can browse absolutely fine, even directly to the repositories via HTTP.

Someone on #Kubuntu recommended that it might be related to DNS problems because of the (1.0.0.0) after the timeouts, but surely if I'm browsing fine that can't be it.

Worst case, is that it's erratic because it worked once last night and I managed to do a complete upgrade to the latest version without issues.

Plz Help!

---

### Post by SauRoN on 2005-07-10
[QUOTE=SauRoN]First, this is my very person post!

Now on to the problem.

I've running Kubuntu on my machine, which was working perfectly fine when I was still using 56K.

Recently however I switched to DSL, and now for some or other reason APT isn't working.

It keeps on timing out to every repository I've tried.

The worst part is, that I can browse absolutely fine, even directly to the repositories via HTTP.

Someone on #Kubuntu recommended that it might be related to DNS problems because of the (1.0.0.0) after the timeouts, but surely if I'm browsing fine that can't be it.

Worst case, is that it's erratic because it worked once last night and I managed to do a complete upgrade to the latest version without issues.

Plz Help![/QUOTE]
 Okay, this is really weird.

It seems that if I make changes to the sources.list then it suddenly works, or at least some of them.

Also, if/when I actually can ping the services (after it failed to connect) then it suddenly works on the next try.

---

