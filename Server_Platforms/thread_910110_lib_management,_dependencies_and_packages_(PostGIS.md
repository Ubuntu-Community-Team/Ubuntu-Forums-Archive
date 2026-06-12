---
title: "lib management, dependencies and packages (PostGIS)"
date: 2008-09-04
forum: Server Platforms
---

### Post by wbloos on 2008-09-04
Hi,

I'm looking for the perfect server OS for our purposes, because we want to buy a new server.
Before i go summing up what our purposes are, i'll limit this one to library management.
It has to be linux, because it's the platform for the coolest server side GIS software. 

Now i know some things about how gnu/linux works technically, it's the general architecture that i'd like to learn more about.
Up to now i'm somewhat familiar with Debian (our test and dev server that i manage), Ubuntu (my main laptop os, since 1,5 years now), RedHat (did the basics and  rhct course) and Fedora (on laptop and desktop, been a while).

I keep wondering why it is so hard to install libraries of different versions alongside. As far as i know, you can install all kinds of software (including their dependencies) on windows. Each app jsut has its own folder and includes it's dependencies somehow, so they won't bite ech other.
On linux on the other hand, there are PACKAGES. I once tried to install the latest version of pgAdmin (a postgresql client) on my Fedora box, but i also had an older version of PostgreSQL back-end on the machine. Turned out i had to upgrade the back-end that happened to live on my laptop to be able to upgrade the client software: *They were sharing a library*.
WHY CANT'T I  JUST HAVE BOTH VERSIONS OF THE LIB ???

Then, when i had put aside my purist principles, i found pout that GRASS GIS was also dependent on the same lib, so i could just forget upgrading.

I always thought that Debian was different. And, yes you can run different versions of PostgreSQL alongside in a very nice way, wich makes me very happy. I haven't really run into any conflicts on my Debian server yet, but i'm thinking that this is probably because i'm not so demanding at the time. Debian is not know for fast releases, but for stability. So intead of Lenny, wich will feature some pretty old software in a year, i think i would prefer Ubuntu, which is faster with releases.

So just to make sure that this server will live up to our expectations, i checked on my laptop if we can have the latest, super fast version of PostGIS (spatial extension for PostgreSQL database, awesome stuff).
I have PostgreSQL 8.1, 8.2 and 8.3 already running on my hardy laptop.
Postgres 8.1 is running version 'POSTGIS="1.1.6" GEOS="2.2.3-CAPI-1.1.1" PROJ="Rel. 4.6.0, 21 Dec 2007" USE_STATS'
Postgres 8.3 is running version 'POSTGIS="1.3.3" GEOS="2.2.3-CAPI-1.1.1" PROJ="Rel. 4.6.0, 21 Dec 2007" USE_STATS'

So it is running the latest version of PostGIS, which is good for sure, but:
WHY isn't the PostGIS in the 8.3 database running GEOS 3.0.0?? (which has latest improvements, was released December 12 2007 and is used by many other PostGIS users)
Why not install BOTH GEOS 2.2.3 -AND- GEOS 3.0.0 ??

Cheers :)
WBL

---

### Post by lmno149 on 2008-09-04
[swg credit](http://www.mybloglog.com/buzz/members/swg_credit/)[vanguard gold](http://www.mybloglog.com/buzz/members/vanguard_gold/)[wow gold](http://www.mybloglog.com/buzz/members/wow_gold/)[coh influence](http://www.myspace.com/coh_influence)[cov infamy](http://www.myspace.com/cov_infamy)

---

### Post by wbloos on 2008-09-06
come on, tell me your ideas.

is there a cure to my problem?
am i the only one that has this problem?
should this go in the stupid questions section?

---

