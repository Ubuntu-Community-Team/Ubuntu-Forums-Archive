---
title: "Cannot access web site from external browser"
date: 2007-01-30
forum: Server Platforms
---

### Post by ajcooper on 2007-01-30
I have Ubuntu 6.10 setup with Apache and have a small website hosted.  My modem/router is set up to direct traffic for port 80 to the ubuntu box.  I can access the website from inside my network, but not from outside.  Interestingly, I have webmin (port 10000) and slimserver (port 9000) set up and both of these can be accessed externally (using a url from dyndns.org).  Is there anything else I need to configure on the apache/ubuntu side to allow access?

---

### Post by MJN on 2007-01-31
Perhaps your ISP blocks port 80?
 
Try changing the port (in both your Apache config and router port forwarding, or just the router if it support port translation) and see if that helps.
 
Mathew

---

### Post by punx45 on 2007-01-31
I use DynDNS and host a site just for giggles.

for one thing, if you have Verizon DSL, i know they block port 80 (and i dont think i could even get anything going on 8080 either.) so if that is the case you are pretty much as far as you can go, which sucks.  do you have ssh or any other low port services that you are able to connect to?

otherwise, double check your server config files (which vary somewhat between apache 1 and 2) and make sure the refrences to ServerName point to your DynDNS hostname and not the server's IP (local or from the ISP).   im gona do a quick browse of my httpd.conf and see if there are any other suggestions i can make.

---

### Post by ajcooper on 2007-02-01
Thanks for the replies.  It was down to my ISP blocking port 80.  Fortunately they're a good ISP and let you toggle the blocking yourself.

I will be looking at ServerName however as well as it will only be local at the moment.

---

