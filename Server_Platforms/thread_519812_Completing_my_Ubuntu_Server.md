---
title: "Completing my Ubuntu Server"
date: 2007-08-07
forum: Server Platforms
---

### Post by Khao on 2007-08-07
Hi everyone!
I just installed a ubuntu server on my old desktop pc that was lying around in my room. It works nicely and has all the features I'm been working with on other servers.
Right now it has 
Apache
Php
Mysql
PhpMyAdmin
proFTPD
WebMin

Now I'm looking for ways to fully host domains on my server, nothing really big, just for personnal use but I don't really know what to use and how it works. I'm not sure if I REALLY need bind9 because my computer isn't too powerful and I want to keep only the necessary things on it. I also need a mail server but I have no idea which one to get.

Any help appreciated! Thanks

---

### Post by foxylad on 2007-08-07
> **Khao said:**
> Now I'm looking for ways to fully host domains on my server, nothing really big, just for personnal use but I don't really know what to use and how it works. I'm not sure if I REALLY need bind9 because my computer isn't too powerful and I want to keep only the necessary things on it. I also need a mail server but I have no idea which one to get.


Postfix is the best mail server for your purposes. Personally I gave up running a DNS server years ago - they are difficult to set up and maintain, and most domain name registrars are happy to provide DNS for no extra charge. And you can mess about with domains on your internal network by hacking your hosts file, to point a particular domain to an internal server for testing, for instance.

---

