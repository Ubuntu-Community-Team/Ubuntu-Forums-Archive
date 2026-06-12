---
title: "Deep Freeze &amp; Net Nanny alternative?"
date: 2009-09-16
forum: Security
---

### Post by Marti68 on 2009-09-16
Thanks for your help on this one.  I'm new to Ubuntu and the whole open source field.

I have been tasked with building a completely secure web access station for a young person's home.  The base OS is intended to be 9.04/10 Ubuntu.  Can you suggest Open Source alternatives to Deep Freeze & Net Nanny?  These two app's would appear to be the basis of a solid system with security as the prime concern.

Unfortunately, netnanny.com suggests that only Microsoft is compatible.  Is the Open Source model compatible with software that requires a maintained database and updates?


Thanks again.  Love the whole community thing Ubuntu promotes.
Marti

---

### Post by i.r.id10t on 2009-09-17
I'm using a locked down kiosk user, a read-only firefox profile, and a local install of squid.  Firefox has the localhost squid as its proxy server.  I'm blocking all hosts and then allowing by whitelist.  Would that work for you?

---

### Post by phillw on 2009-09-17
Another possible way is to use WOT (Web Of Trust) - It is both fire-fox & IE (Yeuch !! - lol) Aware and can be set to caution / block on 4 different parameters.

I use it to 'baby-sit' a lad of 10 yr old who lives about 100 miles away !! - If WOT doesn't like the site - he cannot access it.  

Pretty cool :-)

[http://www.mywot.com/](http://www.mywot.com/)

You can also block un-rated sites.

Hope that is of help, and, welcome to Ubuntu - we're all here to help & share our knowledge & experiences.

Regards,


Phill.
P.S. - I think WOT should be a MUST for using Firefox - you'll look at the results of searches in a whole new light, as it ranks them for you, as well

---

### Post by __p1n__ on 2009-09-17
Wait for 'Clean Feed' to be rolled out and set your primary/secondary/tertiary DNS addresses to point to Australian name servers.

---

### Post by Marti68 on 2009-09-17
Thanks Guys :c)

Ideas I hadn't even considered and will investigate this weekend.  The kids may not thank you but those of us who have used the web certainly will.

---

### Post by __p1n__ on 2009-09-18
> **i.r.id10t said:**
> I'm using a locked down kiosk user, a read-only firefox profile, and a local install of squid.  Firefox has the localhost squid as its proxy server.  I'm blocking all hosts and then allowing by whitelist.  Would that work for you?

This is actually the most secure suggestion on this thread imho.

With respect to replacing net nanny and deep freeze I would suggest that kmahjongg does just about as good a job in terms of actual security which means of course that it does nothing.  Deep Freeze is not a bad idea but it doesn't prevent anything from modifying the running o/s.

---

### Post by i.r.id10t on 2009-09-18
> **__p1n__ said:**
> This is actually the most secure suggestion on this thread imho.

With respect to replacing net nanny and deep freeze I would suggest that kmahjongg does just about as good a job in terms of actual security which means of course that it does nothing.  Deep Freeze is not a bad idea but it doesn't prevent anything from modifying the running o/s.

Of course, none of this protects from booting with a livecd and going - if thats a worry, you'll want to set up a transparent proxy using iptables and squid.  And that still won't block using a SSH tunnel or VPN.

---

### Post by Marti68 on 2009-09-21
> **i.r.id10t said:**
> Of course, none of this protects from booting with a livecd and going - if thats a worry, you'll want to set up a transparent proxy using iptables and squid. And that still won't block using a SSH tunnel or VPN.
 
Good point and I plan to disconnect the CD and lock the case (I may need to recconect it so it'll stay in place).  USB ports are another area of risk; I'll need two for the mouse and KB.

---

### Post by syga on 2009-09-27
I use OpenDNS.
It has online parental controls. It works for me...

[http://www.opendns.com/](http://www.opendns.com/)

---

### Post by Marti68 on 2009-10-12
Thank you :KS
That does look to be the most workable solution for me.  Some excellent suggestions here but a limit to how many new skills I can learn for one project and still produce a result someone else can  support.

---

