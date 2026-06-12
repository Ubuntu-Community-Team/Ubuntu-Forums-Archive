---
title: "Setting-Up Production Cloud Environment -- Looking for Appliance-like Reliability"
date: 2012-08-08
forum: Ubuntu Cloud and Juju
---

### Post by Luce on 2012-08-08
Hello.  I'm new to the cloud environment and was once a bit of techie but have been in Management too long to even think I know where to begin.  To make matters worse our previous full-time tech is no longer with us and has left our servers in an unreliable state.  

The servers consist of numerous front-end machines (~ 10-15) connected to 3 database servers (running PostgreSQL).  There are numerous flavors of Linux in play.

The primary front-end machines are new dual 16 core AMD based machines with ~96G RAM, Quad GigE, connectors.  The database machines are new dual Xeon 5690 machines spinning 24 2TB drives each (configured in RAID 6 with numerous hot spares). There is a separate machine for monitoring functions.

We use a development, staging and production environment and also a "demo" environment to showcase stable new products and features to special customers and investors.

Our goal is to have all machines running under a properly architected standardized OS environment that is rock solid and where machines can be added and removed easily with no drama and no risk, with automatic failover, proper load balancing and where the system automatically brings up additional VMs as required.  (Presently we run numerous VMs but where each one must be brought up manually).  

As a bit of an aside, the previous company I was involved with was also running Linux based servers with large database RAIDed machines (40 disks) and where the reliability was fantastic  -- except for their scheduled cleaning and the occasional upgrades and drive failures the system never went down and has been in service for over 8 years.  This system was/is appliance reliable but difficult to upgrade to handle more load (luckily the load never exceeded the hardware).

We've been researching the latest solutions and it appears that the latest release of Ubuntu Cloud has the capabilities we want. It also looks like it is now possible to use the MAAS technology to fully automate the process.  The challenge is in creating and maintaining the proper charms.

Does anyone know where we can find a great (experienced, honest, mature and success focused) person to help set this up for us under a fixed contract or part-time employment arrangement that could grow into a full time arrangement?

PS: We have sent an email to Canonical Tech Support (for more information regarding the $9,000 set-you-up plan), but have not heard back from them as of this writing.  In any event, we are looking for a long-term relationship with the right person.

---

### Post by dragonfly41 on 2012-08-08
I'm also experimenting with deploying to cloud in a small  way and I found this ..

[http://scalr.net/tour/](http://scalr.net/tour/)

[http://wiki.scalr.net/display/docs/About](http://wiki.scalr.net/display/docs/About)

which I've bookmarked for when I'm ready to use it.

However scalr.net might help you with your admin problem.

...

p.s.

I've just read some more tips here ...

[https://news.ycombinator.com/item?id=4181348](https://news.ycombinator.com/item?id=4181348)

...

---

