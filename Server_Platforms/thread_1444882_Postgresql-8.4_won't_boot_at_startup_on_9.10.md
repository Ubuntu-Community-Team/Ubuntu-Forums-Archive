---
title: "Postgresql-8.4 won't boot at startup on 9.10"
date: 2010-04-01
forum: Server Platforms
---

### Post by jordandcarter on 2010-04-01
I have just moved to rackspacecloud and created a Ubuntu 9.10 server.  Moved everything over all fine (7-10 wordpress sites).  Now I have a couple rails apps that need to move over and run on postgresql 8.4.

I installed postgresql via sudo apt-get as per usual.  Usually at this point the postgresql server starts up and I can forget about it.  But no luck.  I booted it by running /etc/init.d/postgresql-8.4 start.  When I run that command it boots fine, I can connect via psql no trouble.

I rebooted the machine to see what happened.  After boot, apache and mysql started just fine, wp sites came up nicely no trouble.  postgresql wouldn't start up.

I have tried installing from source, I have tried using different /etc/init.d/postgresql-8.4 scripts.  I have no idea what to do.

I have downgraded to upstart to 0.6.3-10.  I have apt-get updated, upgraded.  I have Googled.  I have pushed and pulled.

Usually with any linux issue in the past I have been able to find a solution on the net or work it out myself.  This one stumps me to no end.

The other irritating part is that while I wait to work out this issue I am still paying for my old server running my Rails apps.

Anybody have any clues? Solutions? Experience? Cheers!

---

### Post by BobVila on 2010-04-02
Someone might have more related experience, but if you don't get any direct help, check /var/log/messages and post any postgresql related errors; they'll probably help get this resolved more quickly.

---

