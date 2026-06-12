---
title: "How to do failover with bind9"
date: 2010-02-27
forum: Server Platforms
---

### Post by Fliggerty on 2010-02-27
Hey all,

My web host recently had an outage of nearly a week...well, for the server a few of my sites were on anyway.  I work for my web host, so I was privy to all of the details of what exactly was going on.  We believed pretty much each day that it would go back online "tomorrow," so I didn't really want to mess with the DNS and have propagation time basically cause longer downtime than needed.

My work gave me a server that they phased out of production, and I have had it in my basement running Ubunutu 9.10 on it for some time; there are several live sites on it.  All of my domains are registered through my work, and the DNS is hosted there as well.  They do not support any sort of backup DNS or failover.

I would like to actually build a name server of my own using Bind9.  I've never tackled it, but it seems like a fun project to wrap my hands around.  I have another old server, a Gateway 2700, that is not being used.  So I am thinking about setting it up with Ubuntu 9.10 as well, and Bind9.  Then I'm going to point all of my domains to it.

The real question I have is this: how can I set up failover?  I'd like this name server to also run the task of checking for response from my web host server every minute.  If it gets no response after 10 minutes or so, I'd like it to change the IP address of the domain to my local server where I have a mirror of my site.

Does anybody have an idea of how I can accomplish this, or what packages I need to acquire to do this?  Or any other suggestions ways to provide redundant DNS in my situation?

Thanks!

---

### Post by Fliggerty on 2010-03-05
No suggestions yet?

---

### Post by Bachstelze on 2010-03-05
> **Fliggerty said:**
> 
The real question I have is this: how can I set up failover?  I'd like this name server to also run the task of checking for response from my web host server every minute.  If it gets no response after 10 minutes or so, I'd like it to change the IP address of the domain to my local server where I have a mirror of my site.

One way to do that would be to have a shell script running in cron that will ping your web host's server, and if it doesn't get any answer, update the DNS configuration with the failover IP.

---

