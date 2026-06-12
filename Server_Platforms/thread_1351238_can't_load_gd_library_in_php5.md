---
title: "can't load gd library in php5"
date: 2009-12-10
forum: Server Platforms
---

### Post by fuzz500 on 2009-12-10
I can't seem to enable the gd library in a vanilla install of ubuntu 9.10 server with LAMP and SSH. Instructions on the net are trivial: apt-get install php5-gd, restart apache, and presto I'm supposed to feel the love, i.e. phpinfo should report that gd is enabled.

It's totally not working and I haven't been able to pinpoint the problem.
There was another post that said you have to enable the dotdeb.org repositories and then clean apt cache, and reinstall php5-gd ... no luck there either.

Any ideas comrades?

Fuzz

HA!
I had to issue the apt-get update command to get the latest pkg lists or whatever that does... afterwards the apt-get install php5-gd worked, after apache restart phpinfo reported gd library, and application worked.

---

