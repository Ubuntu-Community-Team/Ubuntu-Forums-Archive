---
title: "make all web services ssl"
date: 2006-12-21
forum: Server Platforms
---

### Post by kjacks on 2006-12-21
I want to access all the web based interfaces on my server using https://  

I just installed openssl and webmin, so I can acceess webmin using https://  But how do I change the way I've been logging into other services I have like SWAT, phpmyadmin, Torrentflux that I've always just used http://

I'm running Ubuntu 6.10
and there's a total noob behind the drivers seat.

---

### Post by kidders on 2006-12-22
Hi there,

Web applications won't necessarily behave themselves over SSL, especially if you don't warn them all individually that that's what you're planning to do. You could try using mod_rewrite to force https, but as I mentioned, you *might* wind up with odd behaviour.

The biggest problem you're likely to have is that SSL and virtual hosting don't get along. (If you're familiar with the protocols, the reason for this will be obvious to you.) This means you won't be able to run phpmyadmin.yourhost.com, swat.yourhost.com, www.yourhost.com, etc. all on the same host on port 443 at the same time. Of course, if that's not what you're already doing (over unsecured http), then you can ignore this little wrinkle.

---

