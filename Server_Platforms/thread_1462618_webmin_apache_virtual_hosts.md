---
title: "webmin apache virtual hosts"
date: 2010-04-25
forum: Server Platforms
---

### Post by teaker1s on 2010-04-25
I've previously run a server over a static ip for just one website without problems.

Reading Several tutorials it appeared that it was possible to point several websites to a static ip, using virtual hosts to port each site to the correct folder.

I have full access to change DNS server settings on name server
(hosted by lcn)

I'm struggling at the moment, I'm getting apache randomly serving default web page(the one for un-handled sites) and the two other websites on virtual hosts.Other times it says site unavailable.

[http://httpd.apache.org/docs/2.0/vhosts/examples.html](http://httpd.apache.org/docs/2.0/vhosts/examples.html)
Has anyone come across this behaviour before and any suggestions how to cure it 
I've reinstalled server with 9.10,latest webmin from webmin site and after hours of searching I'm still stuck.

thanks

---

### Post by halvors on 2010-04-26
Hi!

I use virtualmin GPL on my server, only add a domain and it works.

Remember for setup multiplie domains you need to do follow in DNS:

mydomain1 A xxx.xxx.xxx.xxx
mydomain2 A xxx.xxx.xxx.xxx

Your server will automaticly choose the right apache folder.

Halvor.

---

### Post by teaker1s on 2010-04-26
Thanks,thought I was going mad. 
After hours of checking and re-checking various dns tutorials and following to the letter several webmin or apache tutorials.
The answer turned out to be DNS hosts end, not sure what they did
(settings stayed the same) but it is reliably resolving domains. 

Thank you for your assistance I will bear your post in mind if I get any other issues

---

