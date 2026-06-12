---
title: "Problems with ddclient and apache"
date: 2009-11-28
forum: Server Platforms
---

### Post by cardsfan12 on 2009-11-28
I have a Ubuntu 9.04 box I use for IRC and internet browsing. I'd like to host files on it, so I can access them from school. However, for now I'm not worrying about hosting files, I just want to be able to see the website from outside my network.

I have Verizon DSL, so I'm using DynDns and ddclient. Everything seems to be working fine there, as my IP is updating on the DynDns web page. 

I'm hosting the server with apache. I got it installed fine, and yesterday I could see the server at [http://localhost/](http://localhost/) from anywhere inside my network. I don't know what changed, but today I can only see [http://localhost/](http://localhost/) from the ubuntu box.

My question is  twofold:

How do I make ddclient and apache work together so that I can access the server from the internet?

How do I deal with port forwarding? As far as I can tell, Verizon blocks outgoing TCP 80, so is there a way around that?

---

