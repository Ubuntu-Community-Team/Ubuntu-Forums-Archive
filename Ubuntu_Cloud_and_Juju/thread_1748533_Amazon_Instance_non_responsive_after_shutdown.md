---
title: "Amazon Instance non responsive after shutdown"
date: 2011-05-03
forum: Ubuntu Cloud and Juju
---

### Post by schoneschone on 2011-05-03
I'm trying ami-1aad5273 with Natty (latest release), using 64bit on M1.LARGE instance and everytime i try to shutdown it down, it can never be brought back up.  This is an EBS instance and i've tried it so many times that the latest time, i just basically launched the instance, commanded a shutdown and tried to start it again - and nothing.  Its dead.

A complete syslog is available at [http://pastebin.com/Acv87Cdr](http://pastebin.com/Acv87Cdr)

The culprit seems to be ln 11: "no instance data found in start-local"

Any ideas why that would be happening?

---

### Post by smoser on 2011-05-04
> **schoneschone said:**
> 
A complete syslog is available at [http://pastebin.com/Acv87Cdr](http://pastebin.com/Acv87Cdr)

The culprit seems to be ln 11: "no instance data found in start-local"

Any ideas why that would be happening?

I'm not really sure what you're saying.  The console  log looks to me like a partial log of a successful second boot and shutdown.  Can you give some more information on what you're doing, and what is going wrong?

You do realize that when you do a StopInstances and StartInstances, the instance will change IP addresses, right?

---

