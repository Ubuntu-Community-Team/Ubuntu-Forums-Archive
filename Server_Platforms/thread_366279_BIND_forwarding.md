---
title: "BIND forwarding"
date: 2007-02-20
forum: Server Platforms
---

### Post by hachaboob on 2007-02-20
Hi,

External domain: example.com
* e.g: [www.example.com](www.example.com), mail.example.com

Internal domain: example.com
* e.g: time.example.com, server.example.com

Is there a way to setup BIND to check locally first for the name and if it doesn't exist to check the external nameservers?

I have setup a zone for example.com as a master. I tried putting my ISP's nameservers as forwarders but then it will not resolve local names at all.

---

### Post by aragorn2909 on 2007-02-20
I think your referring to a caching-only nameserver?

---

### Post by Brazen on 2007-02-21
I'm talking all from theory here as I have not yet set up BIND DNS servers here (using problematic Windows DNS servers for the time being).

I would have assumed that by default, if the cname exists on the local server it would use that before it uses the forwarders.  You MIGHT (again no personal experience here) check out dnsmasq.  I believe it is supposed to do just what you are talking about, but is much simpler, at the cost of being much less functional, than BIND.

---

### Post by hachaboob on 2007-02-21
Unfortunately I do not want to switch from using BIND for the moment. It would take too much time setting up a new firewall machine and test it.

I will have to mess around with BIND I guess. At the moment it is OK because there are not many external sites on the example.com that I have to be weary about.

If I am successful I will tell you all about it.

---

