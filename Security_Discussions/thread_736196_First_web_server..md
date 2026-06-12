---
title: "First web server."
date: 2008-03-26
forum: Security Discussions
---

### Post by Montollio on 2008-03-26
I am about to launch and ecommerce site. I am concerned about the server itself being secure. Can anyone give me a good link with step by step instructions on how to secure it properly? I am not a total newb but close to it. Any help would be appreciated.

---

### Post by CheShA on 2008-03-26
Woah there buddy! It sounds like you might be trying to run before you can walk.  If you're processing money on an ecommerce site, you will will be a very tasty target for hackers.  There is a lot goes into building and securing a public web server including the network configuration, firewall configuration (like filtering inbound packets for "bogons" and such like), apache configuration, SSL, etc etc etc.  There is no "step by step guide" for n00bs to building a secure server - to use a cliche:  "security is a journey, not a destination" and on top of that, each situation is unique.

If you're "close to" being a newb, I'd suggest you rethink this, buy a couple of books about a) linux webservers and b) linux security (bastionisation)  and get to know your stuff before you start thinking about building an ecommerce server and asking people to hand over credit card details.

---

