---
title: "help setting up authoritative name server"
date: 2008-03-06
forum: Server Platforms
---

### Post by rajend3 on 2008-03-06
I am developing a DNS security tool, but in order to test it I need to set up 2 name servers, the target name server to test and another authoritative  name server that will run my application.  I am using VMware and running Ubuntu 6.06.  I do not have a registered domain name.  I have no idea of how to go about setting this up, any help would be appreciated.

---

### Post by azadpanchi on 2008-07-25
You will need a domain name.  Once you have it your registrar should have information to set it up as authoritative name servers.  Basically you choose the hostname, e.g. ns1.domain.com and ns2.domain.com, and provide them with respective IP Addresses.  I believe some may require you to have at least two ip addresses, but, most let you get away with one in case you don't have two ip addresses.

Then you can use bind to run your own name servers.  Here in an ample guide for the task:
[http://www.zaphu.com/2007/09/10/ubuntu-dns-server-guide-bind-caching-name-server-setup/](http://www.zaphu.com/2007/09/10/ubuntu-dns-server-guide-bind-caching-name-server-setup/)

---

