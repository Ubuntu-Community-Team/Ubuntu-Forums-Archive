---
title: "Good, multi-functional linux/BSD router software"
date: 2006-06-08
forum: Server Platforms
---

### Post by robinl on 2006-06-08
Hi all I recently got an unused celery 733mhz 64mb ram machine and am planning to use it as a router for my lan. I need the basic things like NAT, Firewall and also ability to count bandwidth used with each MAC address individually and limit their speed if they're using too much. Web-based config is preferred but ssh should be fine. Is there any software packages that can do these? Thanks

---

### Post by dk_pa on 2006-06-08
This looks like it's up your alley. 

[http://www.m0n0.ch/wall/](http://www.m0n0.ch/wall/)

I use it and like it a lot.

---

### Post by mat1t on 2006-06-08
or an alternative to m0n0wall is pfSense. It's based on m0n0wall, but has a few extra features. The beta's I've found to be quite stable so far.

[http://www.pfsense.com](http://www.pfsense.com)

---

### Post by carlbowden on 2006-06-08
Truly,

m0n0 wall (as above) is a remarkably well writing project, the releases are VERY stable, the interface is logical and stright forward.

I have used it for public facing hosting networks for years. I have not been let down once.

very highly recommended.

---

### Post by robinl on 2006-06-09
Thanks for the suggestion but I cannot seem to find the ability to limit speeds on both of them. Is it there? Also can I install Squid on the machine? Thanks.

---

### Post by mat1t on 2006-06-09
[QUOTE=robinl]Thanks for the suggestion but I cannot seem to find the ability to limit speeds on both of them. Is it there? Also can I install Squid on the machine? Thanks.[/QUOTE]

Squid is installable on pfSense, but I haven't been able to get it working yet. Other people have though. I think this is the part to point out that it's beta. All of the core functionality works, but some of the plugins have some problems.

---

### Post by dk_pa on 2006-06-09
Looks like you could try the beta

> 06/05/2006 - Beta version 1.23b1 released
This beta version includes improvements to the captive portal (per-user bandwidth limitation, different MAC formatting styles) and fixes to 3rd party extension and anti-spoof rule handling.

Also, you could look at the listing over at Distrowatch.

[http://distrowatch.com/dwres.php?resource=firewalls](http://distrowatch.com/dwres.php?resource=firewalls)

I've used m0n0wall, redWall and Coyote Linux.  Redwall could be the worst experience I've ever had with Linux.  I used Coyote Linux (runs off a floppy disk and some memory) for a box at my old job and it worked great.  It doesn't have bells and whistles tho.

---

### Post by Iowan on 2006-06-09
[http://forums.freesco.org/support/]("http://forums.freesco.org/support/") 
Here's another single-floppy router/OS you might check.  I've been using it for years (on a '486). There's an additional package site at:  [http://freescosoft.org/]("http://freescosoft.org/")

---

### Post by houstonbofh on 2006-06-12
I am very active on the m0n0wall lists.  What you need can be done.  Look at traffic shaping and captive portal for per user bandwidth monitoring.  (Use MAC for username, and hardcode the password, and there is no login)  Get on the list, and post this same question.  You may be slightly memory light is you need to extend the stock image, however.

As to pfsence, it is a friendly fork.  Many people develop for both.  FreeNAS is another fork.  All look alike, and are very easy to intuitively configure.

---

