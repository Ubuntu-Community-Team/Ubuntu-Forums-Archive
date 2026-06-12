---
title: "Database alternatives for LAMP"
date: 2007-12-27
forum: Server Platforms
---

### Post by Chayak on 2007-12-27
I know MySQL is installed by default on LAMP installs but in the past day or so researching various databases and how they work in the system I found out some interesting little tidbits.

MySQL keeps a process running and stores it's index in memory.  The result?  The larger your database the more memory you are going to need.  A low to medium volume webserver doesn't really need that.

SQLite only accesses the database when it's called and doesn't stay resident in memory.  True it may not be as fast but if you are running on older hardware it would be good to look at.  It works well even on medium volume sites.

When does the trade off occur where the advantages of SQLite is lost? I honestly don't know but for low volume sites it should work very well and doesn't require any configuration and services.  If your site is getting the volume that you're going to move the web and database servers to separate machines then MySQL or another option is needed.  The good news is that SQLite databases can be imported fairly easily into MySQL

Why am I mentioning this?

I was playing around with putting a wiki on a usb thumbdrive to keep my notes on and organized.  SQLite is the best option for that and during my research I discovered it's a pretty robust little program.  I know databases are boring and I've had thoughts of gnawing off a limb to escape from lectures involving them but you can't deny they're important as they're the backbone of dynamic websites, and not to mention these forums too :) Though I'm guessing they're running a fairly robust database setup behind it.

---

