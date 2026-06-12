---
title: "Install Postgres 8.0.X on Hardy Heron?"
date: 2008-11-27
forum: Server Platforms
---

### Post by caledfwlch on 2008-11-27
I'm trying to install postgresql on Ubuntu Server 8.4. I know I can use apt-get install postgresql to do it, but it currently installs version 8.3.

I want to install version 8.0.X because I'm trying to duplicate another server as much as possible.

Is it possible to install this older version of Postgres? If so could I get a quick run through? I've also tried apt-get install postgresql-8.0 as I've seen in some places I've googled but that doesn't seem to work.

Any help is much appreciated! :mrgreen:

---

### Post by lykwydchykyn on 2008-11-27
apt-get would only work if you had a repository with 8.0 in it added to your sources.  I believe if you add a dapper universe repository you might be able to install 8.0, but I haven't tried this personally.  The other option is to download the sourcecode and compile.

---

