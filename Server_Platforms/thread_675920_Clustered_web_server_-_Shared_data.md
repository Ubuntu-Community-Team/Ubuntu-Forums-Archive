---
title: "Clustered web server - Shared data"
date: 2008-01-23
forum: Server Platforms
---

### Post by CheShA on 2008-01-23
I want to make a clustered LAMP server, running as a back end behind our load balancers.  The plan is to have the servers connected to a single LUN on our SAN and share the data that way using GFS.  The question I have is... Just how much data can I share?

The first idea was just to share  /home and /var but I realise this comes with its problems - e.g. after adding packages to one server , apt/dpkg would think they were already installed on the other server. 

I have figured out that I can share /etc by having a seperate /localetc  and using symlinks for anything that needs to be specific (e.g. /etc/hostname) **, and /home goes without saying, but how to share the best parts of /var... and what ARE the shareable parts of /var?  Should I also share /usr? /usr/local? In fact, should I share everything except the bare bones needed to get booted and then get the SAN connected -  /boot and select parts of /etc? Thinking about it, this sounds like the best option - what do you think?  Would having GFS transaction locking on most of the file system cause a noticeable issue with disk I/O throughput?  Has anyone got any pearls of wisdom they can bestow from experience?

Thanks  :popcorn:

**Edit: AHA! A better idea, i could have a Union FS  and have the main body writeable with any local specific configs in /etc layered over the top.  Sweet.

---

### Post by dpiddy on 2008-02-24
Another route to try would be to use a configuration management tool such as [Bcfg2]("http://trac.mcs.anl.gov/projects/bcfg2/") or [Puppet]("http://reductivelabs.com/projects/puppet/") to get all the machines to the same state. Then just mount your shared data via GFS. It's what I do for shared Samba storage; might be easier for you.

---

