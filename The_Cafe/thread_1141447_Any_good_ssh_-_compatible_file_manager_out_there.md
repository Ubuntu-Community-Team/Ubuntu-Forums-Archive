---
title: "Any good ssh - compatible file manager out there?"
date: 2009-04-28
forum: The Cafe
---

### Post by vexorian on 2009-04-28
I used to use konqueror, why not nautilus if I use ubuntu? Well, for once nautilus cannot connect through ssh to the one site I administer, which is lame and all, but it is the truth as well.

After the hardy->jaunty upgrade, nautilus still can't connect to that site, what's worse is that konqueror got screwed up:
* start up time increased.
* starting icons like the useful "network folders" one gone, now konqueror pretends to be just a web browser...
* theme is a little slow.
* To find the network folders part I got to do tons of hacks, first I turn konqueror into a file browser by adding a /home  to the address bar this finally makes the "network folders" icon appear in the "Go" menu.

So, is there a correctly integrated, drap and drop and associations-friendly, graphical file browser compatible with ssh out there?

Edit: Just approached this by making me a custom launcher that starts "konqueror remote:/"

---

### Post by GrouchoMarx on 2009-04-28
Have you tried sshfs? [http://fuse.sourceforge.net/sshfs.html]("http://fuse.sourceforge.net/sshfs.html")

It allows you to mount shares locally via ssh. Then you can use whatever file browser you like best. sshfs is in the Ubuntu repos.

---

