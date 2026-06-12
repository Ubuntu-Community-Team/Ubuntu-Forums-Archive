---
title: "SSH limit users from same IP"
date: 2006-06-15
forum: Server Platforms
---

### Post by CrustyDOD on 2006-06-15
Hey

How would i limit a user from accessing SSH? I have server and on it it runs ssh which is opened for two IP's only. One is mine and the other one is my colleges IP. This guy works in a magazine company and they all have the same IP outside their network. Now i don't want all computers in that company to have access to SSH but only colleges computer. Can this be done in anyway?

Something like: he puts some key on his PC which allows only him to connect to SSH. And by connect i don't mean login but connect to ssh!

---

### Post by gavagai on 2006-06-15
You may look into port-knocking.  [http://en.wikipedia.org/wiki/Port_knocking](http://en.wikipedia.org/wiki/Port_knocking) 

Unless you have special reason to be paranoid, I wouldn't bother making it any more restricted.

---

