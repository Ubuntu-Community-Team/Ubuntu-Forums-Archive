---
title: "Server programs not accessible (ports?)"
date: 2009-09-11
forum: Server Platforms
---

### Post by Creek on 2009-09-11
Hi.

I have a server running Ubuntu server 9.04.
I use it for www/mail/samba and so on.

I have recently set up a ventrilo and cod4 server, which are not installed through apt-get, but manually.
I can access these applications within my home network (192.168.1.xxx) but I cannot connect from an outer network.
I have opened the correct ports (TCP 3874 for vent, UDP 28960 for cod4) in my smoothwall (which I never had a problem with).

I checked the ports through a port checker ([http://www.canyouseeme.org/](http://www.canyouseeme.org/)) and it says that my ports are open and can find my services.

So, I turned to the OS and *iptables* but  it is running as default (accept all chains), so it shouldn't block anything.

Other ports are working (25 smtp, 80 www, 22 ssh), but when it comes to custom ports, it doesn't.


Anyone have an idea what I should try next?

Any help is appreciated.

---

### Post by grantemsley on 2009-09-11
So it works from the LAN on another computer, but not from the internet?

That means the machine is configured properly (unless you are using two network cards).  The issue has to be with your router/firewall or ISP.

---

