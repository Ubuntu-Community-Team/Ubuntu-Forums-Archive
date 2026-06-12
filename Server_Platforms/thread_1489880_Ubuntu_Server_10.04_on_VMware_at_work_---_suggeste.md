---
title: "Ubuntu Server 10.04 on VMware at work --- suggested specs?"
date: 2010-05-21
forum: Server Platforms
---

### Post by r0b0-tr0n on 2010-05-21
Hi all.  ):P

I found out yesterday that the data center in our  traditionally Microsoft-centric organization will let me set up a Linux  box.  =D>

So  I'm looking at Ubuntu Server 10.04.  Our servers all run via VMware, so  I'm debating whether to use the JeOS edition or not.

I can ask  my admin for basically whatever I like in terms of specs, within  reason.  The key questions being number of virtual processors, amount of  RAM, and number of hard drives & space on each.

This box, if  it all works out, will function as a web & db server, running  probably at most 10 sites, the busiest of which by far gets around 50k  visits, 175k pageviews per month.

This job is currently handled  by two Windows boxes, web (1 processor, 4 GB of RAM, three drives  25GB, 50GB, 50GB) and db (same specs).  I don't mind running Apache and  MySQL together for now.  HD space has never been an issue, really.

The  worst they can say is no, so I might as well as ask for dual procs and  at least 8 GB RAM, right?  Yeah, I'm probably overthinking here, but I'm  trying to take my time and get things right the first time.  Any  thoughts or suggestions?

In any event, hello to everyone, and  thanks!  :)

---

### Post by arrrghhh on 2010-05-21
Welcome to the forums.

Obviously the beefier the hardware, the better.  However, the specs of your current Windows system sounds fine.  The RAM is going to probably be more important than the processor for your setup.  Dual quad-core or even more is overkill, but hey if they'll get it for ya why not?

A single quad-core would probably be sufficient, with I'd say at least 4GB of RAM.

Be careful of the stupid new landscape system - I spooled up an Ubuntu server here for testing, and the information security department was all over me because the server kept trying to phone home.  Very annoying, and actually kind of appalling that Canonical would do such a thing - but they're obviously just trying to increase profits.  Which, I can understand... I just don't appreciate my server phoning home without even asking.

---

### Post by robvas on 2010-05-21
They probably won't give you dual processors, they actually shouldn't for performance reasons in a VM environment. 

I have 6-8 Linux VM's running at any given time at work, along with 4 Windows VM's (they're the ones actually doing the work ;))

512MB is fine for a 10.04 desktop VM, so I'm sure 1-2GB would be plenty for a server, depending on how much RAM your database uses.

---

### Post by r0b0-tr0n on 2010-05-24
Thanks for the feedback guys, I appreciate it!\\:D/

---

