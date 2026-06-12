---
title: "Apache only using one core"
date: 2009-08-04
forum: Server Platforms
---

### Post by mrsteveman1 on 2009-08-04
Server is a Xeon with 4 cores, running Ubuntu 8.04.3, and apache 2.2.8 running in prefork mode.

In htop all apache processes sit on the 1st core, causing http requests to grind to a halt when that core is being utilized for other things, even if other cores are available. In other words, it is not spreading the load across all the cores at all. 

It is not running in the worker threaded mode, but these are still separate processes and they should be able to run on other cores.

The only thing i can think of would be that this apache version came from the virtualmin people and they did something to it. For some reason virtualmin required apache to be replaced with their own version, perhaps because of suexec.

I may rip that virtualmin crap out tonight anyway, but perhaps someone else has had this problem before.

Any ideas?

---

### Post by mrsteveman1 on 2009-08-04
Ripped out virtualmin and all the apache packages it wanted to use, and it seems to work fine now with the stock apache build from ubuntu.  

I don't know if the suexec stuff is the only difference but our server can now handle a fair bit of load, before it was crawling just because of one core being 100%, nothing loaded etc.

---

