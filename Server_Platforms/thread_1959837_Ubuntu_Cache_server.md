---
title: "Ubuntu Cache server"
date: 2012-04-16
forum: Server Platforms
---

### Post by darknoobie on 2012-04-16
Good morning,
I was thinking bout setting up a cache server for our company. We currently have a program that pulls information from ms sql server 2008. Some of the users are on a remote site and it takes near 1 hour to load the application. Would a cache server work for us by caching most of the data on there end?

---

### Post by Lars Noodén on 2012-04-16
You're probably better off upgrading that remote application to MySQL or Postgreql.

What kind of cache are you thinking of?  If it is a web cache your main two choices are [Varnish](https://www.varnish-cache.org/) and [Squid](http://www.squid-cache.org/).

---

