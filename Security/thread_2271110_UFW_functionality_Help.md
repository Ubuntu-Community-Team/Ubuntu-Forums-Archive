---
title: "UFW functionality Help?"
date: 2015-03-27
forum: Security
---

### Post by smogsy on 2015-03-27
So, before you all say it Ubuntu it already "secure", well i like to make it more "secure"

Now this PC is mainly going to be Gaming/browsing only.

So what ive done so far

1. turned on UFW of course
2. edited SSH so it uses a non standard port Blocked this service with UFW through command line
3. edited Telnet port to non standard port & blocked this service with UFW through command line.

**What i want to do:**
Block all outgoing traffic, which is easy 
However, i want a way to be flagged when it blocks the X request/port without going through the logs. Maybe a Gnome Extension or somtrhing that flashes?


**So imagine this scenerio**
1. load up Steam
2. Flags it blocked X request with X port
3. i then manually add Ports through commandline
4. allow me through.

also is their any other good services to block through the firewall?

---

### Post by bardo2 on 2015-04-01
Hum, nice, that you are interested in "security" from the net. Although i am very much interested in this topic as well, and have always been, i do disagree somewhat:
You seem to be imagining security coming from a firewall. That - as far as my understanding is concerned - is only the tinyest part of it, some sort of a playground only. Most problems are coming through the Internet (port :80 IIRC) and are caused by PEBKAC. So there is never going to be a situation to relax vigilance, except maybe, while the network cable is pulled. ;-)

Still... good luck and have fun!

edit:
any port, that is NOT protected by a firewall, is SAFE, as long as nobody is listening to it. That is why i suggest you first check out, what "listeners/services" you have running. SSH for example isnt listening before you INSTALLED some sort of ssh server (a client doesnt listen).

---

