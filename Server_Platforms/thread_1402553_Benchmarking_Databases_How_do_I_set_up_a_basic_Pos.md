---
title: "Benchmarking Databases: How do I set up a basic PostgreSQL database?"
date: 2010-02-09
forum: Server Platforms
---

### Post by tom66 on 2010-02-09
Basically, for a little project I am doing, I am comparing the speed, performance, and reliability of various database systems. At the moment I am only comparing open source systems but I may try to compare the closed source systems as well. To do this, I set up servers/clients on my local computer with root permissions (because security is not important in this local test-bed) with a single database called 'BenchmarkDB'. 

I've already managed to get MySQL (just installed mysql-server-5.0 and started the service then logged in as 'root') and SQLite3 (not really a 'server', was ready out-of-the-box) to work as I want. But PostgreSQL always complains about either the server not running (when it is), or not having permissions, or it can't find the config file... (this is just a vanilla apt-get install) 

How do I set up a basic single-user installation of PostgreSQL? I'm sure there must be some way, or at least an easier way of doing what I want. All the docs I've read mention, when an error is encountered, to "contact your server administrator". But I am my administrator, so that doesn't help me. So can someone point me to an easy tutorial? (By the way, I've tried the one on their website. No luck. More server administrators to contact.)

---

