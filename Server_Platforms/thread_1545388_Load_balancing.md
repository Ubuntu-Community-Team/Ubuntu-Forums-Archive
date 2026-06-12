---
title: "Load balancing"
date: 2010-08-03
forum: Server Platforms
---

### Post by StolerTech on 2010-08-03
Hi,

I have a 10.04 32-bit virtual ubuntu server. I am trying to figure out how to setup load balancing. Here is how I planned out to do it, I need direction for what software I should use.

--Internet(1.2.3.4)
--Router
---Load Balancing Server (192.168.1.30), port 80, public as in port forwarded
           Load balancer sends traffic to either web server
---Web Server 1 (192.168.1.100)
---Web Server 2 (192.168.1.101)

I heard I should use rsync to keep the files concurrent, at this point rsync is the least of my worries. I need to know what load balancer I should use I have tried and failed with crossroads(xr), and balance.

I can't seem to find a modern tutorial for either system. I looked at linux virtual server but that is like 5 years ahead of my current knowledge.

If anyone could point me in the right direction I would be so happy :)

---

### Post by StolerTech on 2010-08-03
Bump

---

### Post by tgalati4 on 2010-08-04
Why don't you install phoronix-test-suite on one of the servers and perform some webserving benchmarks then post the results.

sudo apt-get install phoronix-test-suite

What type of pages are you serving and why do you need 2 servers in the first place?

You say you are running a virtual server.  How is it configured?  

What type of hardware are you running?

---

### Post by Jakob Lundberg on 2010-08-04
Maybe HAProxy is what you are looking for.
[http://haproxy.1wt.eu/](http://haproxy.1wt.eu/)

---

