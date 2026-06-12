---
title: "Open internal access to machine, but close it up outside network"
date: 2008-12-13
forum: Security
---

### Post by hotstovejer on 2008-12-13
Hi,

I am having a bit of a problem learning about firewalls and iptables. Here is my situation.

Internally, I want all default ports open for my other machines. I want them to be able to access my shares, printer, everything that is open by default. So, I want my subnet to be wide open. Anything on 192.168.mysubnet.X I want to have free reign.

Externally, I want to button it all up. Only allow what I need from the outside (ftp, ssh, http and vnc)

How would I go about it? I'm sure it's easy to do, no? I searched, but I rely on my friends here to help. 

Thanks!

Jeremy

---

### Post by bodhi.zazen on 2008-12-13
First, as you may know, a router will do this for you.

If you are making your own router, we need more details.

You may want to start with ufw or gufw

---

