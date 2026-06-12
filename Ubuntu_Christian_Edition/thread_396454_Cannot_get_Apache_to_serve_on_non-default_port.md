---
title: "Cannot get Apache to serve on non-default port"
date: 2007-03-29
forum: Ubuntu Christian Edition
---

### Post by Cyclops_ on 2007-03-29
Hey, all...

So, I'm trying to serve http from my system.  I'm running CE, and as of now I can serve on port 80 just fine.

The problem is when I try to serve on another port (which is not already taken, of course).
Let's say I'm trying to serve on 8088, for example.

So I put:  
```
Listen 8088
```into my ports.conf and restart Apache (after setting up a simple VirtualHost).  All appears to go well, but I'm getting nothing when I try to get there.  It just spins and gives me a white screen.

Here's what I have for the VirtualHost (and I also did an "a2ensite" for it): 

```
NameVirtualHost *:8088
<VirtualHost *:8088>
    DocumentRoot /var/www
</VirtualHost>
```(Just to keep it simple)

I made sure that the router is forwarding the ports, and we are on cableone cable internet, so I'm pretty sure the modem is too.

when i do this: 

```
nmap -p80,8088 $HOSTNAME
```

 i get this:

```
80/tcp    open http
8088/tcp open unknown

```firehol is set up to accept server http

What could I be missing?

Thanks for any help :)

---

