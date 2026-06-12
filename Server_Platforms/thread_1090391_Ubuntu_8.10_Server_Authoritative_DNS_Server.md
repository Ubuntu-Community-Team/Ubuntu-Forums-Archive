---
title: "Ubuntu 8.10 Server: Authoritative DNS Server"
date: 2009-03-08
forum: Server Platforms
---

### Post by o891 on 2009-03-08
Hi Guys,

I am looking for a few tips. I have been reading everything I can find about DNS Servers, but I am unsure about how to go on from here.

I am setting up a Ubuntu 8.10 Server on VMWare on Mac OS X 15.6, in preparation to doing an actual install on an HP Server. The server will only host about 4-5 different sites, using about 10-12 different domains.

So far everything has gone very well (thanks to the amazing Ubuntu community I must say), everything is working perfectly (Apache2, mysqld, php5, ssh, vsftpd, openssh, etc, etc).

I have the Virtual Machine with a bridged internet connection, and all the port forwarding if setup up with the routers NAT.

Now I was getting into the whole DNS thing. After a few hours of reading I think that I have a pretty good idea of how the system should work. But when it comes to setting it up, I am not getting very far.

Here is what I would like to do: I would like to have on my server whatever is required for people to be able to get to the content of the server (www, mail, ftp, etc) by using the domains (ex: [www.example.com](www.example.com)). [EDIT: Without something like EasyDNS or DynDNS.]

So, so far I thought that I would be able to setup a primary nameserver on my server and then a secondary nameserver on the domains' registrars servers (the latter is no problem, I have checked that). Am I missing something? If not, maybe someone could point me towards a guide that addresses exactly this issue or maybe a sample zone file for an actual internet - not intranet  - DNS Server, as I can't find a good tutorial/guide about this. All I am finding are pretty basic, mostly intranet tutorials, that don't really explain the whole actual internet side of the setup.

Thanks for any help!!

Oliver

---

### Post by hyper_ch on 2009-03-08
do you have a static IP?

---

### Post by o891 on 2009-03-08
Well, my provider rarely ever changes my ip, so I suppose you could call it static, but it's not really! I could get a static ip, if I needed to...

---

### Post by hyper_ch on 2009-03-08
if you don't have a static ip then use [http://www.everydns.net](http://www.everydns.net) as nameserver host. There you can then set the according nameserver entries and for your linux box you can download a perl (or python) script and let that run like once every hour. It will update the IP with everydns.

The only problem is, that if your IP changes the server may not be reached for like 1 h.

The other option is to get a static ip.

---

### Post by o891 on 2009-03-09
Well I can get a static IP through my university, so I suppose that fixes that problem. But where do I go from here?

I think I kinda know how to setup the zone files for my DNS server. But how do all the other DNS servers out there know that the nameservers for my domains are at 84.20.xx.xx? Is it from the information found when doing a whois query?

When I do an whois query for mit.edu I get this:

```

Name Servers:
STRAWB.MIT.EDU 18.71.0.151
W20NS.MIT.EDU 18.70.0.160
BITSY.MIT.EDU 18.72.0.3

```

But the registrar where all my domains are registered now (1und1, Germany) only lets me enter FQDNs for the nameservers (not IPs)?

So where do I register the IP addresses of the servers that the DNSs of other people query to to get the IPs of my domains?

Thanks!

---

### Post by hyper_ch on 2009-03-09
well, you have to tell your registrar where you registered the domains what your nameserver IP(s) are. some accept just one nameserver, others require two, others require two in different subnets.

I'd still say use everydns.net to manage the zone files for your server.

---

### Post by o891 on 2009-03-10
Thanks for the info!

What if I dont want to use DynDNS? I suppose that I could just point the registrar to my static IP, right? The problem is that my registrar doesnt accept IPs as nameservers, if I enter an IP it says that  that is not a valid nameserver. It just accepts FQDNs. Do you know what the problem might be? My registrar is 1und1 in Germany.

They allow IP forwarding, but not setting nameservers with IPs...

Thanks

---

### Post by hyper_ch on 2009-03-10
you need to create nameserver entries at your registrar. not sure if 1&1 allows that..

---

