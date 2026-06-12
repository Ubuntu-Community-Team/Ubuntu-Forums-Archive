---
title: "Linux As A Firewall"
date: 2012-08-27
forum: Virtualisation
---

### Post by th1bill on 2012-08-27
I know, from experience, that Linux Servers are used in many commercial settings as a firewall for Windows computers. So coomes my question, I seldom use any Windows apps today but am setting up one for a friend in business and I need to know in placing it inside Vbox on an Ubuntu unit makes it safer?

Thanks for any and all replies in advance.

---

### Post by TheFu on 2012-08-27
Nope, not by itself.

There are lots of guides to create 
* a secure network
* a locked down Linux
* a locked down MS-Windows
* a router
* a firewall
* an IPS/IDS

You can  do these things inside virtual machines if you like, but some things like firewalls and routers are best inside dedicated hardware.  Sure, you could build them inside a VM and it might be more secure than without them, but the ability to make a tiny mistake and not have any security exists.

Every OS should run a firewall, even if there's a network-based firewall.  Whenever possible a network firewall should be used too.

---

### Post by CharlesA on 2012-08-28
TheFu pretty much covered it.

A VM is as safe or as vulnerable as a physical machine. Lock it down if you want to limit the risk.

---

### Post by Lars Noodén on 2012-08-28
There is one big advantage to running such an insecure system inside a virtual machine: [snapshots](http://www.virtualbox.org/manual/ch01.html#snapshots).  You can roll back to a known good snapshot and have a fresh start any time you want it.  It could even be every time.  That's a huge advantage over having it on a regular machine and having to wipe and reinstall (thus removing 3rd party apps, too) each time a clean slate is needed.

---

