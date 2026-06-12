---
title: "IT license and asset management tool....."
date: 2012-09-14
forum: Server Platforms
---

### Post by ragtag on 2012-09-14
I'm looking for a good tool for managing our commercial software licenses. Things like license expiratin notification, serial number registration, installation notes, prices and possibly budgeting. 

If it can handle other IT assets too (hardware etc), that would be great, but it's not a must.

Preferably something that can run on a web server, so that it can be accessed from Linux, Windows and OSX.

Any suggestions? 

Or should I just roll my own.  :guitar:

---

### Post by Habitual on 2012-09-14
this may help narrow down the choice(s)...
[Call Center, Bug Tracking and Project Management Tools for Linux]("http://linas.org/linux/pm.html")
an exhaustive list, for sure, but dated 2002. :(

Subscribed with interest...

---

### Post by mespork on 2012-09-14
We use glpi, it will do all your asset and software tracking:

[http://www.glpi-project.org/spip.php?lang=en](http://www.glpi-project.org/spip.php?lang=en)

It also has a nice help desk ticketing interface.

---

### Post by ragtag on 2012-09-17
So far I haven't found anything that's exactly what I'm looking for.

glpi covers a lot of the same ground as Redmine, which we use for issue tracking....and could work.

Kwok does cover a lot of what I want, but is a Java/Tomcat web app, which for some reason makes me uncomfortable with it. :)
[http://www.kwoksys.com/index.php](http://www.kwoksys.com/index.php)

I checked out things like Glom and Kexi, to quickly set up a system manually, but neither seems to have a stable web UI yet.

So far I haven't really found anything that's a perfect fit. I will probably just wind up either hacking Redmine to do it, or make a simple php/mysql page to do it.

---

