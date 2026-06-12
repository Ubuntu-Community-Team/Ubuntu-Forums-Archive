---
title: "OpenVPN Question"
date: 2010-09-17
forum: Security
---

### Post by spynappels on 2010-09-17
Hi Guys,

I've set up numerous OpenVPN instances on servers, both as server and client configurations.

Now I've been asked to look at running both a client and a server instance on one machine. I think it should be possible, but I just wanted to check that this is in fact possible.

I'd presume it is simply a matter of placing 2 conf files in the /etc/openvpn/ directory, 1 server and 1 client conf, and making sure the correct Certs and keys are in place, but is there anything else to watch out for?

---

### Post by The Cog on 2010-09-17
I think that should be all. 

If you're planning to do routing between the two remote VPN ends, acting as a mid-point then you will have rather more work to do. In brief:
* You would have to enable IP forwarding on this PC. There is a line to uncomment in /etc/sysctl.conf to enable this. 
* You will also have to arrange for the end systems to know that your PC can be used as a route to get to the other end systems. Probably easiest is editing the "routing" entries in the OpenVPN config files, but it may take some thinking about.
* You may also want to use iptables to filter what devices and protocols can use your PC as a through route.

---

### Post by spynappels on 2010-09-17
Thanks for that, I'll not be wanting any sort of communication between the two VPN subnets at all, one will be for remote administration and the other will be for access to a web-app from client computers.

---

