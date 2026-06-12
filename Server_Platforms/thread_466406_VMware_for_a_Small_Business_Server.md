---
title: "VMware for a Small Business Server?"
date: 2007-06-06
forum: Server Platforms
---

### Post by FluffyElmo on 2007-06-06
I'm about to set up a small business server, low traffic but with a lot of services (gateway, e-mail, web, printer sharing, etc...). I'll take notes as I go to see if I can add anything to the homeserver project. 

One thing that has been bothering me is that I've seen posts recommending using VMware to divide the services into separate virtual servers and am wondering if this is really worth it? It seems like it would make things more complicated, and a standard Ubuntu server is secure enough?

I don't mean to start a flame war or anything, just genuinely curious if this is the way to go...

---

### Post by apocalypsefalcon on 2007-06-06
i would probably use it, especially to separate the private services from the more public ones.

---

### Post by Chayak on 2007-06-07
VMware is good for isolating various servers.  It's more or less a standard practice in many datacenters now as most servers are hardy used at all.  I use our VMware systems daily for both windows and linux.  Even with everything else just having vmware for backups as you can copy the entire VM system by backing up the folders they're stored in and reguardless of the system you can easily restore them.

---

### Post by craigp84 on 2007-06-07
> It's more or less a standard practice in many datacenters now

This is wrong. This is what vmware would have you believe, but this is *not* the common situation. While virtualisation is used to some extent in large businesses, it is not a primary solution for most.

> having vmware for backups as you can copy the entire VM system by backing up the folders they're stored in

No, that wouldn't work, the disk files are moving targets. There is however a snapshot feature which generates a file which you can just copy.

Just in the same way there is a snapshot feature of any enterprise OS (Linux, Solaris, AIX, HP-UX...) disk / lvm subsystem. Actually solaris is a slight exception, but for the purposes of this, it's not that important.

Snapshotting an entire system is wasteful. Disks are certainly cheap, but the time required to perform the backup is not.

> i would probably use it, especially to separate the private services from the more public ones.

Why? It's a waste of resource (lose compute, memory etc.) with a percieved increase in security. It should be noted that this percieved increase in security has yet to be proven in any meaningful way.

Well thought out architecture, sensible configuration, proper auditing and effective firewalling contain the risk in your public facing services.

Virtualisation does *nothing* to protect a service. Invest your time and money in protecting a service, before trying to contain a breach in it.

> It seems like it would make things more complicated

FluffyElmo hit the nail on the head with this one. Where previously you had one host to configure, maintain, backup, monitor etc. - now you have 5 or 8 or 10 or whatever.

All that being said, obviously there is no golden rule with this (otherwise there would never be debates on it). Look at your possible solutions, how much do they cost, what performance loss will you get with virtualisation etc. etc. and see what makes most sense in your sitiuation.

Hope this helps,

-c

p.s. virtualisation very much is in fashion just now, everywhere you look people are ranting about how it "halfed my leccy bill in the datacentre" or "enhanced my security" blaa blaa blaa - what i'm saying is, that it's wise to remember that soon (as with all technology) this will pass; where does that leave your setup?

---

### Post by Chayak on 2007-06-07
Actually it is becoming a standard practice and yes backups do work by just copying the VM machine's directory.  I can even quickly make a clone of a machine by copying in and starting it up with the virtual network adaptor turned off to reconfigure the machine identity and IP and then bring the virtual adaptor back up and I have a fully functional clone from a template that took me a fraction of the time to deploy.  I can also take that folder and run that VM on any machine with VMware installed.

It's true, yes, that you shouldn't go over your capabilities.  If you already have multiple servers it's great to consolidate machines that are barely used.  You shouldn't virtualize high use servers like databases.  It's also good if you just don't have the extra hardware for another server

---

