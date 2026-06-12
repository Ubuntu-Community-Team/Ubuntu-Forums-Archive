---
title: "Server setup questions"
date: 2008-06-09
forum: Server Platforms
---

### Post by beckols on 2008-06-09
Here's the deal, I live in a fraternity house and I've recently become the sysadmin.  I want to improve the infrastructure over the summer while no one is here.  Currently, there are two servers running old versions of red hat (not sure what version) and they are Pentium II's with like 98 MB of RAM and tiny hard drives.  I'm working on getting new hardware, but for now I just want to figure out the software setup I'm going to use. Right now they only are used as a gateway/firewall with a small samba file share. The reason there are two is because the previous sysadmin did manual load balancing by switching users back and forth between the two servers (by the way we have two dsl lines).

Ok, so I want to knock it down to one computer.
* It will run Ubuntu 8.04 server
* It needs to act as a gateway/firewall
* I would like it to be a proxy server for faster web browsing
* It needs to have a small Samba share
* It needs to have load balancing

I don't necessarily need step-by-step instructions, I can figure some things out on my own.  I just would like to know if 1) this setup is efficient, 2) what software is best, 3) maybe some links to similar server setups.

Even any general advice on managing a network with ubuntu server would be appreciated as this is my first time administrating a network with this many users.

Thanks in advance for any help.

---

### Post by ilrudie on 2008-06-09
Sounds like you are basically trying to build an appliance.  Not to knock Ubuntu but for this you might want to look at a lighter Linux distro or a BSD solution perhaps.  Thats just my thoughts but I have not played much with Ubuntu Server.  Others might have more relevant experience.

---

### Post by beckols on 2008-06-09
Well, I'd really like to use ubuntu server.  I'm not completely opposed to using something else, but ubuntu is the only linux I've used.

---

### Post by andremzenun on 2008-06-09
Hello,

Well I have used debian based distros for many years now and they are very good to manage (apt) and very stable!

I few months ago I started to use ubuntu server 8.04 and so far no problems!

I think ubuntu can do all you need! You'll need to find some resources on internet to do what you want, as this one:

[http://lartc.org/howto/lartc.rpdb.multiple-links.html](http://lartc.org/howto/lartc.rpdb.multiple-links.html)

This will teach you how to setup multiple internet providers with load balancing (50% - 50%) using the iproute tool!

Well I think for the file sharing (samba) and proxy (squid) are not that hard to setup! For these two are a lot of step-by-step on google! ;)

---

### Post by beckols on 2008-06-09
Thanks! That link is very helpful. And I had been looking at squid as well, and I'm assuming that would be my best option for proxy.

---

### Post by andremzenun on 2008-06-09
No problem!
I think squid is the most used web proxy!
In Guatemala I know a big internet provider that use squid and
so far no problem! ;)

---

