---
title: "Samba 3.0.25 package for Dapper to get inotify support?"
date: 2007-06-26
forum: Server Platforms
---

### Post by XenonofArcticus on 2007-06-26
I'm running Dapper 6.06 on my file server because I want the LTS support. I recently learned about a issue in Samba (change notify being inefficient and therefore disabled or very slow) that has been solved in the newest kernels (2.6.13) and Samba (23.0.25) with the inotify subsystem:

[http://www.linuxjournal.com/article/8478](http://www.linuxjournal.com/article/8478)
[http://lwn.net/Articles/234312/](http://lwn.net/Articles/234312/)

My kernel is new enough, but Dapper only has Samba 3.0.22-1. I'd like to get this fix on my server, but I've had bad juju in the past when I tried to go outside of pre-made packages and build my own Samba. Invariably I end up compiling something slightly differently than the package maintainer did, and bad things happen.

I'm wondering if anyone has built a Samba 3.0.25 package for Dapper, and if so, could I get a copy of it for my use? If I have to compile it locally I will, but I'm trying to stay straight on the package-managed path on this server for ease of maintenance.

---

