---
title: "&quot;Secure by default&quot; ... ?"
date: 2007-03-24
forum: Server Platforms
---

### Post by Wardazo on 2007-03-24
Hi

I'm confused about Ubuntu's default security.

Ubuntu is "secure by default", that is to say it comes with no open ports out of the box. 

So why would someone want to install a firewall?

OK I can understand that you might want to consolidate all the control over ports in one application. But lets say you are running only a web server (port 80 only). You want tcp and udp... you open incoming and out going for both those types of traffic.

Why install a firewall? What more does this give you?

I'm obviously missing something but I don't like installing a security application without knowing why.

Thanks

Ward

---

### Post by kidders on 2007-03-24
Hi there,

> **Wardazo said:**
> So why would someone want to install a firewall?Firewalls allow you to route packets to hosts (or ports) they were not originally destined for, selectively admit, reject or drop traffic using a *huge* variety of criteria, and a range of other useful (often essential) things.

> **Wardazo said:**
> Why install a firewall? What more does this give you?Other than the above, running a firewall guards against accidentally opening ports to the outside world (eg a careless reconfiguration of something like Samba), and can protect your computer from low-level attacks designed to cause overflows or stack errors.

Other possible uses for firewalls include traffic shaping and accounting.

---

### Post by Frosty Cold Drink on 2007-03-24
A properly configured system doesn't need a firewall. But really... how many systems are 100% properly configured? ;)

---

### Post by homli on 2007-03-28
In short, for the same reason you may want a deadbolt even when the doorknob on your front door has it's own lock.  Multiple layers of protection.

---

### Post by Brazen on 2007-03-28
I always setup my firewall (I say "setup", not "install" because the netfilter firewall is already part of the kernel) for the 2 reasons already mentioned: **kidders:** "guards against accidentally opening ports to the outside world", and **homli:** "Multiple layers of protection."

I also have a functionality reason for setting up the firewall.  For instance on our MySQL server, MySQL needs to be accessed by 3 servers, so I want to ONLY allow access from those 3 servers.  Doing this within MySQL is not possible (or not easy anyway, although you can restrict user accounts to certain IP addresses, but that still leaves the daemon open), but it is a snap to only allow the MySQL port open through the firewall to just those 3 servers.

---

