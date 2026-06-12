---
title: "Home DNS server?"
date: 2009-12-07
forum: Server Platforms
---

### Post by SlugSlug on 2009-12-07
My ISP's DNS is pretty poor, I was using  opendns and then I thought would it be possible / worth while having my own DNS server..??

---

### Post by ratcheer on 2009-12-07
If you can figure out how to configure it, the package is bind9. If you have ever run Treewalk in Windows, it does the same thing.

Tim

---

### Post by redmk2 on 2009-12-07
> **ratcheer said:**
> If you can figure out how to configure it, the package is bind9. If you have ever run Treewalk in Windows, it does the same thing.

TimBind9 is *the* DNS server standard.  It can be very complex to configure.

Treewalk is more like DNSMasq.  DNSMasq is easy to install.  It is great for small networks.  You can read about it [**_[COLOR="DarkSlateGray"]here[/COLOR]_**]("http://www.thekelleys.org.uk/dnsmasq/doc.html").  The config files has all the documentation and can be seen [**_[COLOR="DarkSlateGray"]here[/COLOR]_**]("http://www.thekelleys.org.uk/dnsmasq/docs/dnsmasq.conf.example")

---

### Post by memilanuk on 2009-12-07
Another good source for a basic dnsmasq setup: [the Ubuntu Community Documentation]("https://help.ubuntu.com/community/Dnsmasq") has a page on it.  Works well, and much simpler to setup than bind.

Didn't notice at first that you already tried OpenDNS... I'm kind of surprised that didn't help?

---

### Post by SlugSlug on 2009-12-07
opendns does work, I just thought I maybe able to set up my own dns, quick readup on bind9, stated I need to input my ISP DNS address,  is this the case? 

I was thinking I could make my PC do all the DNS storing / syncing (so if I enter [www.google.com](www.google.com) my PC looks at it's own records and knows the IP)
but not really sure how the whole thing works.

---

### Post by AlanR8 on 2009-12-07
Could be another issue that makes domain name resolution slow, posted elsewhere in this forum but here it is again.

Open, as sudo, /etc/nsswitch.conf 

Find the line that reads:

> hosts:  files mdns4_minimal [NOTFOUND=return] wins dns mdns4

Edit it to read:

> hosts:  files mdns4_minimal [NOTFOUND=return] dns mdns4

In other words, get rid of the entry for "wins"

Worked a treat for me when I noticed there was an unacceptable delay in resolving names on the Web.

You might also want to try the new Google service for DNS resolution. In your router software, Primary DNS Server 8.8.8.8 and Secondary 8.8.4.4

Changed from OpenDNS to Google over the weekend and all works well!

---

### Post by redmk2 on 2009-12-07
> **SlugSlug said:**
> opendns does work, I just thought I maybe able to set up my own dns, quick readup on bind9, stated I need to input my ISP DNS address,  is this the case? 

I was thinking I could make my PC do all the DNS storing / syncing (so if I enter [www.google.com](www.google.com) my PC looks at it's own records and knows the IP)
but not really sure how the whole thing works.

What you are talking about is a caching non-authoritative DNS server.  In other words it stores all of your successful DNS searches.  The DNS from OpenDNS or Google is something different. 

OpenDNS (or Google) is authoritative and pulls info from the root domains (.com, .net, .edu, etc).  The DNSmasq server is your local cache of the returned information.

Keep in mind that the information is dynamic (e.g. it has a TTL factor)  Today's information is not the same as yesterday's and it won't be the same tomorrow.

---

### Post by Iowan on 2009-12-07
As a side benefit - DNSmasq can act as DHCP/DNS server - tying the two together so DHCP clients can be referenced by name instead of IP

---

### Post by jamieleshaw on 2009-12-07
I wrote this how-to might beable to help.
[http://jamieleshaw.wordpress.com/2009/11/28/howtosetup-a-home-domain-name-serverdns-with-bind9/]("http://jamieleshaw.wordpress.com/2009/11/28/howtosetup-a-home-domain-name-serverdns-with-bind9/")

---

### Post by hazza96 on 2009-12-13
I combine a dnsmasq server *with* OpenDNS. Here's how I have my setup.

**/etc/resolv.conf**
```

domain localdomain
search localdomain
nameserver=127.0.0.1

```

**/etc/dnsmasq.conf** (eth1 is my external interface)
```

domain-needed
bogus-priv
filterwin2k
except-interface=eth1
resolv-file=/etc/resolv.openDNS
log-queries
log-facility=/var/log/dnsmasq

```

**/etc/resolv.openDNS**
```

search localdomain
nameserver 208.67.222.222
nameserver 208.67.220.220

```

The server uses itself to look up addresses, dnsmasq is configured to use a different resolv file than the default.

So whether the query comes from the network or the server dnsmasq will be doing all the work and using OpenDNS to resolve it, then it will cache the result.

I added the logging facility recently... some interesting things have popped up.

---

### Post by BkkBonanza on 2009-12-14
That last post is the way to go. Use dnsmasq and stay away from bind9. 
You don't need authoritative DNS  - you need a DNS cache which is one function of dnsmasq.

> I added the logging facility recently... some interesting things have popped up.

I bet. Lots of ad server / spam ware type stuff no doubt.

---

### Post by SlugSlug on 2009-12-14
> **hazza96 said:**
> I combine a dnsmasq server *with* OpenDNS. Here's how I have my setup.

**/etc/resolv.conf**
```

domain localdomain
search localdomain
nameserver=127.0.0.1

```**/etc/dnsmasq.conf** (eth1 is my external interface)
```

domain-needed
bogus-priv
filterwin2k
except-interface=eth1
resolv-file=/etc/resolv.openDNS
log-queries
log-facility=/var/log/dnsmasq

```**/etc/resolv.openDNS**
```

search localdomain
nameserver 208.67.222.222
nameserver 208.67.220.220

```The server uses itself to look up addresses, dnsmasq is configured to use a different resolv file than the default.

So whether the query comes from the network or the server dnsmasq will be doing all the work and using OpenDNS to resolve it, then it will cache the result.

I added the logging facility recently... some interesting things have popped up.




Nice I have just copied you and dig [www.bbc.co.uk](www.bbc.co.uk) after the first hit = 0ms

thanks!

:popcorn:

---

### Post by SlugSlug on 2009-12-14
hummm spoke to soon??  I seem to be getting 'Page not found' then a refresh or two gets me the page some times the page is not fully loaded untill a refresh too..

---

### Post by Xiuh on 2009-12-14
I think all questions have been pretty much answered for this thread, but it caught my eye. I just setup Bind9 with a local forward zone and dhcp3 to write dynamic records. I thought it was a nightmare. You'll see tons of guides out there, usually doing the same thing in lots of different ways. If I would of read this thread I think I would of saved myself lots of grief. Instead I became so confused and paranoid about the slightest issues with my dns I ended up going through most of the bind documentation....only to do what I had done before in a slightly different way :P

---

### Post by SlugSlug on 2009-12-14
> **SlugSlug said:**
> hummm spoke to soon??  I seem to be getting 'Page not found' then a refresh or two gets me the page some times the page is not fully loaded untill a refresh too..


this seems to have fixed by removing the '=' out of resolv.conf and having it as a space 

(or maybe it was because I rebooted)

---

