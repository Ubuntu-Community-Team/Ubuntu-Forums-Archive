---
title: "Any general rules of thumb on securing a stock Ubuntu 8.04 Server?"
date: 2008-07-11
forum: Server Platforms
---

### Post by samalex on 2008-07-11
Hi Everyone,

I've installed Ubuntu Server at home many times for a home-based server, but I'm about to install one for the Internet and have some questions.

My main question is whether or not there's some general practice tasks for making a stock Ubuntu server secure, or more secure I should say since outta the bocks it's probably more secure than many other OS'es :)  This box will mainly be a web and mail server with web being Apache (plus MySQL and PHP of curse) and mail being Zimbra.  Outside of that I hope to offer SSH accounts to a select few and possibly Usenet (non-anonymous) to a few technical newsgroups since many ISP's have dropped Usenet.

Outside of the realm of common security since, is there anything technically I should do to make such a box more secure?  I know the more holes I poke in it the more unsecured it'll be, but outside of WWW and incoming mail all other services will be running on a nonstandard port and nothing (except WWW) will allow anonymous connections.  

Anyway, just thought I'd ask...

Thanks --

Sam Alex

---

### Post by cdenley on 2008-07-11
I would be most concerned with the php scripts you put on the web. Sloppy php code can be a big security hole. If you are really paranoid, you can chroot apache. I never tried it.

[https://wiki.ubuntu.com/ModChroot](https://wiki.ubuntu.com/ModChroot)

---

### Post by ixus_123 on 2008-07-11
Disable root login for SSH conections and make sure you have strong passwords usign uppercase, lowercase, symbols and numbers.

I think it's also worth installing fail2ban or similar - these will block an IP for a period of time after a 3 failed login attempts.
Usually these are bots and will give up and move on if you lock them out for 5 minutes or so.

---

### Post by ibutho on 2008-07-11
Configure some firewalls rules using shorewall or any other iptables frontend (ufw should do, but I've never used it).

---

