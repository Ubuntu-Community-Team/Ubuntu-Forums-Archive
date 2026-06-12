---
title: "How to sort out ONE fixed IP serving several VMs"
date: 2015-12-25
forum: Virtualisation
---

### Post by satimis on 2015-12-25
Hi all,

Host	   Ubuntu 14.04 desktop
VMs	   Ubuntu 14.04 desktop/server edition
VirtualBox

I have several websites running on VMs, each with its own domain/subdomain and internal IP address.  But I have only one Fixed IP.  Please advise how set up their static IP so that they can be evoked on Internet?

Does following document help?
VirtualBox: Configuring Static IPs for VMs
[http://coding4streetcred.com/blog/post/VirtualBox-Configuring-Static-IPs-for-VMs](http://coding4streetcred.com/blog/post/VirtualBox-Configuring-Static-IPs-for-VMs)

Thanks in advance

Regards
satimis

---

### Post by Skaperen on 2015-12-25
*how many* static IPs did you get from your internet service provider?

---

### Post by satimis on 2015-12-25
> **Skaperen said:**
> *how many* static IPs did you get from your internet service provider?
Only ONE

Regards
satimis

---

### Post by Skaperen on 2015-12-25
then you have only *one* to make the *where it gets used* decision with.  you can't run two static IPs if you only have one.

---

### Post by Skaperen on 2015-12-25
each VM needs its own IP.

---

### Post by Skaperen on 2015-12-25
if the VMs are not servers and only need to make outgoing connections, then you could use masquerading.

---

### Post by satimis on 2015-12-25
Hi all,

Thanks for your reply.  

All VMs are Apache server running WordPress.  My problem is I have only ONE Fixed IP.  I can create many internal IPs on router.

Serveral years ago I made use of Perdition

Perdition: Mail Retrieval Proxy
[http://horms.net/projects/perdition/](http://horms.net/projects/perdition/)

to setup several mail servers on VMs but served with only ONE Fixed IP.  It worked seamlessly.  All emails were delivered to their own servers.  Maybe I can dig up the respective documents on my database.  But I have no idea whether it also work on web-server?

Regards
satimis

---

### Post by MAFoElffen on 2015-12-25
:: To Mods-- This is more a Server Section question. ::

Although perdition is still in the Ubuntu Repo's for current versions of Ubuntu Server. 
```

sudo apt-get perdition

```
But that is a mail service proxy right?To others, [perdition]("http://manpages.ubuntu.com/manpages/hardy/man8/perdition.pop3.8.html") is an imap and pop proxy server service for mail servers. What you are looking for is more an http proxy like [Squid]("http://manpages.ubuntu.com/manpages/dapper/man8/squid.8.html")?

You can have a static Ip that is subnetable or you could have a single /32 IP that you can share that single IP to multiple domains via using one of many techniques-- 2 of which are port forwarding, or using a SOCKS (http proxy).

Both techniques are very usable and elegant solutions to share a single static IP. If the OP is used to perdition, (still an actively supported service), then configuring an http proxy, such as Squid, might be closer to what you are used to...

---

### Post by satimis on 2015-12-25
Hi,

I have deleted perdition already after the test.

> **MAFoElffen said:**
> 
- snip -

You can have a static Ip that is subnetable or you could have a single /32 IP that you can share that single IP to multiple domains via using one of many techniques-- 2 of which are port forwarding, or using a SOCKS (http proxy).

- snip - 

Just learn "Apache HTTP Server As Reverse-Proxy Using mod_proxy Extension" and found following article;

Building Apache for Proxying
[http://www.apachetutor.org/admin/reverseproxies](http://www.apachetutor.org/admin/reverseproxies)

I'm prepared testing it.  But my concern is whether I can created a VM running Apache for this test?  OR I have to install Apache on the host for this test?  I'm reluctant installing Apache on the host because I expect keeping it clean for running VirtualBox ONLY.  Then I'll find another PC to continue this test.

Advice would be appreciated.

Thanks

Regards
satimis

---

### Post by MAFoElffen on 2015-12-26
I don't see any reason why you couldn't do that as a guest in VM... I would try that first.

---

### Post by Skaperen on 2015-12-26
show me 3 example URLs that might be used ...

[http://example.com/](http://example.com/)
[http://example.net/](http://example.net/)
[http://example.org/](http://example.org/)

and what are their IP addresses (you can use examples) ...

192.0.2.1
198.51.100.2
203.0.113.3

oh wait!

that's 3 addresses.

better use *different ports* which is easy enough to forward if you have a decent router or you have linux, where all the traffic for your ONE IP address ends up at.

if it's *not* easy, try getting a cheap [VPS server]("https://www.cloudvps.com/") and set up a tunnel.

---

