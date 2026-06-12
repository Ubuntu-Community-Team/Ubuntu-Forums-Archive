---
title: "replicated web servers"
date: 2010-02-25
forum: Server Platforms
---

### Post by ki100 on 2010-02-25
Hi all,
this my first post in this forum!!

I need a suggestion...

I have to phisical servers HP and I need to replicate them each other....
I use Ubuntu 9.10 on every server...

That is : the server A has its own ip address and hosts a web server with apache,mysql,etc. and I would want the the second server is a perfect copy of A, maybe with another ip address, so if a failure occurs and one of the servers is down, the other takes its place and the web server customers don't realize anything...

I know a company that implemented this solution....

What technology could I use to create this structure ?

Is there some software appliance on linux that I could use ?

I heard about GlusterFS...It could be useful for me....
Thanks for every suggestion...

---

### Post by BobVila on 2010-02-25
I currently do the web part of this with a pair of plone servers running in an HA configuration serving pages to four apache web servers set up as reverse proxies.

No experience with HA mysql, I'm afraid. I'll be interested to see how people do that.

---

