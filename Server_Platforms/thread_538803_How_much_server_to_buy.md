---
title: "How much server to buy?"
date: 2007-08-30
forum: Server Platforms
---

### Post by jay0316 on 2007-08-30
We are putting in a request for a web server that will run ubuntu. We are only using it as a web server.   The IT dept. talked with Dell and gave them our sites' statistics and they suggested a $3,000 server.  It sounded like it was over kill for what we would be using it for.  I wanted to run this by you to see what you think and see what we should be looking for in a server.

Our 5 sites total to about:
1,100 MB Bandwidth roughly per week
1.4 GB of disk space
19,000 page views per week
6,100 visitors per week
68,000 hits per week

Here are a few specs from the server Dell suggested:
2- Dual Core 1.8Ghz AMD Opteron 2210 Processors
4GB of RAM
2- 250GB Hard Drives
     3yr Standard Support

This sounds like overkill to me.  Do we really need this much?  What should we be looking for?

Thanks a lot!

---

### Post by Wiebelhaus on 2007-08-30
> **jay0316 said:**
> We are putting in a request for a web server that will run ubuntu. We are only using it as a web server.   The IT dept. talked with Dell and gave them our sites' statistics and they suggested a $3,000 server.  It sounded like it was over kill for what we would be using it for.  I wanted to run this by you to see what you think and see what we should be looking for in a server.

Our 5 sites total to about:
1,100 MB Bandwidth roughly per week
1.4 GB of disk space
19,000 page views per week
6,100 visitors per week
68,000 hits per week

Here are a few specs from the server Dell suggested:
2- Dual Core 1.8Ghz AMD Opteron 2210 Processors
4GB of RAM
2- 250GB Hard Drives
     ***_[SIZE="4"]3yr Standard Support[/SIZE]_***

This sounds like overkill to me.  Do we really need this much?  What should we be looking for?

Thanks a lot!

Have you looked at an itemized list of what all of this costs? I bet the support is outrageous , if your the support , you could probably build that without much headache.

---

### Post by jay0316 on 2007-08-30
Yeah, that is one of the costs we are looking at.  I'm not sure if the IT department will budge on it, but the cost for support is HIGH.

Here are the items that added to the cost

3yr support - $679
2- 250gb hard drives - $200
4GB RAM- $519
Processors were included in the base cost of $1,200

These items seemed to really drive up the cost.  The nice thing is we'll be saving $800 by not getting windows on it!

Based on the stats I gave above do you see any downsizing we could do on hard drive and ram. Our sites only take up a little over a 1GB.  The smallest we can go with a RAID is 80GB, which seems like that would be more than enough.  Does two 80GB drives sound like plenty or do we need more?

Also RAM.  Do we need 4GB based on those stats? 

We are going to talk to IT about the 3yr support, but that will be there call in the end.  I've always heard that buying the support is just lining their pockets with cash.

Thanks.

---

### Post by Wiebelhaus on 2007-08-30
The support is allot less than I thought it would be , you don't want to buy anything new right now without as much ram as you can possibly afford , nothing less than 2 gigs personal computer / 4gigs server , the hard drives have a good price , is that a raid configuration? is that raid 1 (Mirroring)?

---

### Post by jay0316 on 2007-08-30
Yes, it is a RAID configuration.  There is a RAID controller.  I assumed that it would be mirroring, isn't that what RAID does?

Thanks.

---

### Post by Wiebelhaus on 2007-08-30
> **jay0316 said:**
> Yes, it is a RAID configuration.  There is a RAID controller.  I assumed that it would be mirroring, isn't that what RAID does?

Thanks.

That's raid one mirroring , there are many [raid configuration options]("http://en.wikipedia.org/wiki/RAID") I personally for a server would go with raid 3 or higher , but we may be getting into over kill in your situation talking about anything higher than 1 , but on the other hand, that may be something to broach with support , it may not cost that much more.

---

### Post by Wiebelhaus on 2007-08-30
by the way mate , that thing is going to be hella fast , What OS?

---

### Post by wirelessmonkey on 2007-08-30
IMO, so long as you are doing backups to another machine, this spec is adequate for ~5years for a production webserver.  You could probably find another vendor for a little cheaper, but the 3 year support in an enterprise environment can save you bookoo $$, and is absolutely worthwhile.

---

### Post by jay0316 on 2007-08-30
Thanks for the replies.

> by the way mate , that thing is going to be hella fast , What OS?   LOL!

The OS is going to be the Ubuntu Server Edition. Are the processors overkill?

We don't think we'll have any issues with just having 1 RAID.  Is it that likely we'll have 2 drives fail on us?  You seen our specs.  They aren't out of this world.

---

### Post by Viruk on 2007-08-30
We go RAID5 on all our servers, although there is good protection in RAID1 and you double your read speed (in theory anyway - there is an overhead) but get no performance boost on write operations. 

IMO your choice should be RAID 1 or 5. It depends on your requirements - just don't get RAID0 in a server if its mission critical :p
Bear in mind that you will need another drive in that spec of machine to achieve RAID5.

> Yes, it is a RAID configuration. There is a RAID controller. I assumed that it would be mirroring, isn't that what RAID does?
There are quite a few RAID configurations. If you need any information on RAID have a look at:
[http://en.wikipedia.org/wiki/RAID](http://en.wikipedia.org/wiki/RAID)
[http://www.webopedia.com/TERM/R/RAID.html](http://www.webopedia.com/TERM/R/RAID.html)
[http://www.acnc.com/04_00.html](http://www.acnc.com/04_00.html)

---

### Post by ssam on 2007-08-31
are you serving static or dynamic pages? are you running a database for dynamic content?

if it is static that sounds like overkill. you might want enough ram to run the OS and apache, and then some spare so that your most viewed pages/files can be cached into RAM.

maybe you could find a spare computer and do some benchmarking.

apache has a tool called ab for benchmarking.

---

