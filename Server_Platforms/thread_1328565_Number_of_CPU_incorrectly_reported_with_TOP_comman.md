---
title: "Number of CPU incorrectly reported with TOP command"
date: 2009-11-16
forum: Server Platforms
---

### Post by wjrhee77 on 2009-11-16
From what I've been reading, it seems like my cpu is being over utilized.  But I just don't see that happening with this servers's usage.  Could I get some of your inputs?

I am running Ubuntu 7.10 Server edition on a Dell PowerEdge 2950 server with Dual Core Xeon® 5110 CPU.

The problem is when I run "top" command, it shows something like "load average: 8.16, 8.11, 8.18".

From my understanding, since this is a dual-core CPU system, load average of 2.00 means being "100% utilized".  
If it was that much overloaded, I would expect the server to halt.
Even with cpu 100% idle, load average is 8.00.
Is this load average of 8.00+ wrong or should I be looking to upgrade.
Just dont know what's going on here.

This server is being used as apache/mysql server.
Mysql server has about 50 to 80 concurrent connections throughout the day with apache getting 10,000 hits per day(about 40 visits per day).

Thanks for your opinion.

---

### Post by dca on 2009-11-16
You should try doing a fresh install (I know that'd be a pain in the rear) to Ubuntu 8.04LTS 64-bit and test...
 
This article helped me:
 
[http://www.linuxjournal.com/article/9001](http://www.linuxjournal.com/article/9001)

---

### Post by wjrhee77 on 2009-11-16
I'm leaning more toward top reporting being off.
Yes, it would be a major pain since this is a live server.

I've been wanting to upgrade to 8.04 LTS for awhile now, and separating the apache with mysql since in-house app and few sites will be using this mysql.

As you mentioned, I think it's time to go 64 bit with some decent cpu juice.  It should be more enjoyable then trying to fix "top".
;)

Thanks.

By the way, that's a great picture of u.

---

