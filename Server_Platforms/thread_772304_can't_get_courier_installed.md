---
title: "can't get courier installed"
date: 2008-04-28
forum: Server Platforms
---

### Post by t8sht3r on 2008-04-28
We have Ubuntu 8.04, Hardy Heron, installed (server edition).  I want to get POP3 working so I decided to go with courier.  Everywhere I've looked, the way to get courier is "apt-get install courier-pop", etc.  Each time I try to do this, or install any other package listed for courier, I get something like this:

$ sudo apt-get install courier-pop
Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Couldn't find package courier-pop

Can someone just tell me the package names I need to get courier running?

thx

---

### Post by eric_stewart on 2008-04-29
> **t8sht3r said:**
> We have Ubuntu 8.04, Hardy Heron, installed (server edition).  I want to get POP3 working so I decided to go with courier.  Everywhere I've looked, the way to get courier is "apt-get install courier-pop", etc.  Each time I try to do this, or install any other package listed for courier, I get something like this:

$ sudo apt-get install courier-pop
Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Couldn't find package courier-pop

Can someone just tell me the package names I need to get courier running?

thx
courier-imap
courier-imap-ssl
courier-pop
courier-pop-ssl
courier-authdaemon
courier-docs
courier-base
courier-mta
courier-mta-ssl
courier-webadmin
....
So, "courier-pop" looks OK.  You might want to make sure that you have your repositories up-to-date *and* all the ones you need.  I don't know offhand which repository courier's packages are in, but you can't install a package with apt-get unless it's there.

/Eric
webmaster
Net Tiki!  [http://www.NetTiki.com](http://www.NetTiki.com)

---

