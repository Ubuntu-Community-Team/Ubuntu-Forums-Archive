---
title: "Setting up DynDNS"
date: 2010-04-21
forum: Server Platforms
---

### Post by 1serveyou on 2010-04-21
Hey everyone, I'm trying to setup DynDNS for my server and I can't seem to get it to work from a "website"(servername.homeip.net), but if I use putty while I'm still on my network and type in the same thing it works. I'm not sure exactly what I'm doing wrong. Thanks in advance!

Also, I'm using comcast, which from doing some research blocks port 80, how would I change this so I can connect to my file server?

---

### Post by volkswagner on 2010-04-22
If your ISP blocks port 80, you will need url/port redirection.  noip.com has this feature, I'm not sure about Dyndns.com though.

From the sounds of things, it seems your blocked port 80 is stopping the apache site, but perhaps using putty allows use because the port for putty is not blocked.

---

### Post by iissmart on 2010-04-22
If you have a router, you probably have to set up port forwarding. Normally you would just open port 80 and set it to your servers internal IP, but in this case you should open a different port like port 81, and have the router forward that to port 80 and the servers IP. Then you would just type [http://servername.homeip.net:81](http://servername.homeip.net:81) from outside the network to get access to it.

---

