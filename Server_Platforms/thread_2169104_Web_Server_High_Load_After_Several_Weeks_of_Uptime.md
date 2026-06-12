---
title: "Web Server High Load After Several Weeks of Uptime"
date: 2013-08-20
forum: Server Platforms
---

### Post by ScatterBrain on 2013-08-20
I've got an Ubuntu 12.04 server (a VM running on a vmWare ESXi 4 host if that matters) running a pretty bland LAMP stack which hosts my website, a Wordpress blog.  I keep it up to date - both with Ubuntu patches and Wordpress patches.  It doesn't use a great deal of plugins and is using a stock theme.  Beyond that,  I write on it and post photos and link to YouTube videos.  Pretty mundane, boring stuff.

This morning when I tried to access my site, the browser just timed out.  When I checked via SSH, which was a very frustrating, slow process, the server was under a very heavy load (in excess of 8.0 according to top).  But I couldn't find ANYTHING hogging resources.  Top didn't show a single process using more than 4% of CPU time  - mySQL and Apache were swapping back and forth.  Still not enough to cause the load and sluggishness I was seeing.  Combined CPU use was like less than 6 or 7%.  The machine is sitting idle most of the time (Very light traffic.  6k visitors in a 24 hour period, better than half of these being crawlers.)

I checked the other two virtual machines on that host and they were using less CPU and resources than my server.  Suffice to say the host was handling the load just fine.  Yet my server was unresponsive to the point where I rebooted it to get the site back online.

I have fail2ban on the machine. I also run ufw, blocking all but the needed ports (apache, dns, ssh).  Yesterday, fail2ban blocked 6 addresses for SSH attempts...ufw is blocking some things, but that's its job.  Beyond that, I'm not seeing any real concerns.

I'd be willing to call this a fluke except it's happened before - several times now.  Not like clockwork, but about 14 days of uptime is what it takes to get the machine into this state.  I can find nothing wrong, nor can I see an active attack.  It just goes bonkers.

So I'm wondering if anyone else has seen this and what I can do to stop it.

---

### Post by CharlesA on 2013-08-20
Does the load go down if you stop the mysql and apache services?

I seem to recall hearing similar things by other people running on ESXi, but I cannot recall where I saw them off the top of my head.

---

### Post by ScatterBrain on 2013-08-21
> **CharlesA said:**
> Does the load go down if you stop the mysql and apache services?
To be honest, accessing the machine was so painfully slow that I simply rebooted the machine, so I can't answer this.  When it happens again, I'll try that before simply falling into the "windows mentality" and reboot it.


> **CharlesA said:**
> I seem to recall hearing similar things by other people running on ESXi, but I cannot recall where I saw them off the top of my head.
If you happen to locate this, I'd be interested in reading it.

---

### Post by tgalati4 on 2013-08-21
How much RAM do you have allocated for the VM?  It sounds like a resource in ESXi4 is running out after a long period of time.  I'm not familiar with the monitoring tools in ESXi4, so you will have to do some more digging.

If this is the free version of ESXi4, perhaps there are some limitations over the enterprise version?  Any purple screens of death?

---

### Post by ScatterBrain on 2013-08-27
> **tgalati4 said:**
> How much RAM do you have allocated for the VM?  It sounds like a resource in ESXi4 is running out after a long period of time.  I'm not familiar with the monitoring tools in ESXi4, so you will have to do some more digging.

If this is the free version of ESXi4, perhaps there are some limitations over the enterprise version?  Any purple screens of death?

I had 2GB of RAM, but have bumped that to 4GB as part of a "let's see if this fixes it" type solution.  The machine isn't dead just woefully slow - SSH won't connect, console is like molasses.

When I've looked at the performance charts (which are only for an hour or two) of ESXi, the host seems to be doing fine and the VM is too - with slightly elevated virtual CPU usage (like 20% vs 6%), no high NIC traffic, not filling RAM, datastore usage is normal.  It's very, very odd.

No, I've not seen any screens of death - purple or otherwise.

It's been nearly 2 weeks now and so far, so good.  I've updated it once since I wrote the initial post, everything is a-ok at the moment.

---

