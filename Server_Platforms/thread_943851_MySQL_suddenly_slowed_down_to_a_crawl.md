---
title: "MySQL suddenly slowed down to a crawl"
date: 2008-10-10
forum: Server Platforms
---

### Post by Aeros84 on 2008-10-10
Hi again,

I've noticed something rather strange with my MySQL installation on my ubuntu server.

I set MySQL up as normal (apt-get install mysql-server). Everything fine up to the point that I tried to connect to the database from one of the network PC's using Navicat. Said that IP isn't allowed to access the database.

So, I commented out the following in my.cnf:

#skip-external-locking
#bind-address           = 127.0.0.1

And restarted the MySQL server. After that, I could connect from the LAN PC using Navicat, but my gosh, it's slow. Takes 5 seconds to connect, then 5 seconds to open a database, and then another 5 to 10 seconds to open a table. I never had this problem before on other servers.. did I break something somehow (can't see how, though), or what's going on here?

---

### Post by Aeros84 on 2008-10-10
Hm, actually I found the solution in the meantime. Bizarre though.

Had to add the LAN PC's IP to the /etc/hosts file. Can't remember ever having to do that before. Isn't there a way to turn off dns resolution completely?

---

