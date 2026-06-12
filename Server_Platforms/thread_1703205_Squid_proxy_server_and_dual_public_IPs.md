---
title: "Squid proxy server and dual public IPs"
date: 2011-03-09
forum: Server Platforms
---

### Post by markosjal on 2011-03-09
I have set up Squid and webmin on Ubuntu 10.04 64 bit and seek assistance with the following

I have one NIC and 2 Public IPs from 2 different countries. When I assign both IPs to Ubuntu and use the IP on the virtual adapter eth0:0 all traffic shows as if it originates from the IP on eth0. I was hoping that if a person connects from x.x.x.x that squid would limit their data to originating from x.x.x.x, instead however it always shows y.y.y.y to all sites. Is this a routing issue? Need I configure some routing? Squid is configured to use 0.0.0.0 or any IP address.

Alternately, I could specify the proxy by root domain for instance all connections to /from .ca extensions come and go from x.x.x.x while all connections to/from .com extensions come and go from y.y.y.y



I want to add some security and have tried to follow several tutorials with no success. I understand there is some built in security in Squid as well as some 3rd party security. I want that all users MUST use usernames and passwords. What is the easiest way too do this based on current releases? I think that much of the information out there is outdated and does not apply to current releases.



How can I limit bandwidth? I want to limit bandwidth to a level that supports a basic Netflix stream and I believe this to be just under 2 Mb/s.


Thanks in advance

---

### Post by Demented ZA on 2011-03-09
Uhm, I've never done exactly what you are trying to do now, but I'm approaching that situation.

I recently set up a system with two internet connections on Ubuntu 10.10 64-bit, using shorewall as firewall and Webmin for an alternate means of access than ssh.

Out of my experience, I'd say what you are trying to do is not a Squid related aspect, but rather routing as you mentioned.

Shorewall does basic load balancing, and is more than good enough for the needs of most. Shorewall basically works with zones, all adapters with a public ip will be your 'net' zone, and local adapters will be your "loc' zone with the firewall 'fw' in between. You generally create rules and policies between zones and not adapters. Makes it a lot easier to understand, and thus very powerfull. Aslo works like a charm with Webmin.

Basically squid should only listen on your internal interfaces. As for fetching and caching content, squid will get its information from whatever shorewall descerns at the time.

I can help you with the two interface system, but as for squid, I'm only just getting started on it.

I also want to have my users log in with a username and password, and even made a post about it: [**Squid allow or deny browsing for around 15 users.**]("http://ubuntuforums.org/showthread.php?t=1701221")

I would approach this as two seperate problems.
[]("http://ubuntuforums.org/showthread.php?t=1701221")

---

