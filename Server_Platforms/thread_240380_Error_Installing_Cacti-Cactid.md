---
title: "Error Installing Cacti-Cactid"
date: 2006-08-20
forum: Server Platforms
---

### Post by rincewind1013 on 2006-08-20
Hi,
I'm trying to install cacti-cactid and am getting an error during the post install process,

Setting up cacti-cactid (0.8.6g-1build1) ...
dpkg: error processing cacti-cactid (--configure):
 subprocess post-installation script returned error exit status 10
Errors were encountered while processing:
 cacti-cactid
E: Sub-process /usr/bin/dpkg returned an error code (1)

I found an older thread complaining of the same problem, but the "solution" was since dapper was in pre-release it was a wait and see situation. Dapper has been out for some time, and I'm still having the same problem

How do I install cactid?

---

### Post by Kurdt on 2006-08-20
I also got the same issue with cacti-catid, after asking in cacti forum and do A LOT of search and a lot of things, i gave up...

Try to ask in cacti forum too. :) I think the package is broken or sort of.

---

### Post by Chrissss on 2006-08-22
I've got the same problem

Package cacti
* dapper (web): Frontend to rrdtool for monitoring systems and services [universe]** 0.8.6h-1ubuntu3**: all

Package cacti-cactid
* dapper (web): Multi-Threading poller for cacti [universe] **0.8.6g-1build1**: amd64 i386 powerpc

Looks like cacti-cactid has the wrong version. It's also here

[http://forums.cacti.net/about12475.html](http://forums.cacti.net/about12475.html)

and here's the bug report

[https://launchpad.net/distros/ubuntu/+source/cacti-cactid/+bug/40219](https://launchpad.net/distros/ubuntu/+source/cacti-cactid/+bug/40219)

---

### Post by Linuturk on 2007-03-02
I can second this problem.

---

