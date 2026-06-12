---
title: "Tracking Bandwidth for Users"
date: 2008-03-25
forum: Server Platforms
---

### Post by utahcon on 2008-03-25
**Background:** I run a very small hosting company. We are currently under 10 users, but we hope to grow quickly. We have had some really good advertising via word-of-mouth.

We are running Ubuntu 7.10 Server Edition, and currently have the Xampp Stack. I am very open to rebuilding the stack with "real" installs of the software if I must.

Currently has Apache, PHP, ProFTPd, MySQL, CVS pserver all running for the clients.

**Problem:** I would like to be able to limit my accounts to a set limit of storage space (disk quotas) and bandwidth (incoming and outgoing). 

I think I know how to do disk quotas, but the problem I am having is the bandwidth.

I have read all sorts of things regarding this that range from installing and using webalizer, to installing ntop, and other apps.

I was wondering if there is a command line process that is tested and law in the hosting world, that I should take a look at. 

What are you using on your systems?

Thanks!

---

### Post by Gen2ly on 2008-03-25
I don't run a server, so I won't be able to help you but I seem to recall running across some information here today that might be able to help:

[http://cb.vu/unixtoolbox.xhtml](http://cb.vu/unixtoolbox.xhtml)

Networking is toward the buttom.

---

### Post by utahcon on 2008-03-25
I can't believe this, I left out details. Sorry.

More on the problem.

I have 1 IP for all my clients thus far. I know things would be simple with multiple IPs (one for each site), but it isn't an option yet. 

So the configuration is all Vhosts on HTTP/FTP/CVS etc.

Thanks for the link Dirk, lots of good info there, I think. :D

---

