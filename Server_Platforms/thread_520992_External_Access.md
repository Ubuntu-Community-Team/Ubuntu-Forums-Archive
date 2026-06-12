---
title: "External Access"
date: 2007-08-08
forum: Server Platforms
---

### Post by Cr4ig on 2007-08-08
I've been an Ubuntu user for a while now, but just recently got in to the server side of things and I have a few questions. I was able to set up my server with Apache, proftp, Mysql, etc, and I can access everything fine from my other computers on my local network, but I'm not sure how to access it from and external source. 

How do I see if my server is setup for external access(which I assume it is, I just can't figure out how) and how do I access it?  (if there's already been a post about this can you post a link?) Thanks. ;)

---

### Post by foxylad on 2007-08-08
This depends on the router that connects your network to the internet.

Usually these are set up by default to reject any internet->network connections, for security, so you'll have to figure out how to open inbound ports for the services you want available (SSH, HTTP and HTTPS).

Different router do it differently, but look for DMZ settings or ways to expose an external port to an internal port on a particular machine.

---

### Post by Cr4ig on 2007-08-08
Hey thanks. I thought it might be something simple like that. #-o

---

