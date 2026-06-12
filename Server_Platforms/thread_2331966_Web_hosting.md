---
title: "Web hosting"
date: 2016-07-27
forum: Server Platforms
---

### Post by neil37 on 2016-07-27
HI, 

I'm running ubuntu 14 lts minimal and I've set up  LAMP.
I was wondering what the best and easiest approach would be to add a domain name?
From what I've been looking at ideally I'd need 2 DNS servers but these appear to be hosted on separate vps hosts.
One vps for each DNS.  Is it not possible to host DNS servers on the same server?
It's just for a few sites and personal use. 

Thanks

---

### Post by howefield on 2016-07-27
Thread moved to the "*Server Platforms*" forum, probably a better fit.

---

### Post by neil37 on 2016-07-27
> **howefield said:**
> Thread moved to the "*Server Platforms*" forum, probably a better fit.

ok thank you.

---

### Post by Habitual on 2016-07-27
Separate vps for each DNS on **differing sub-nets** is suggested.
You only have one (or will have.)

One is fine.

I highly suggest that the "ns1" (nameserver1 or the "first" nameserver) be **your host**.

---

### Post by neil37 on 2016-07-28
Thanks for your post.

I've been looking at digitalocean.com to  help me get as far as installing SSH, LAMP and ensuring other areas of  the system are secure.
I'm quite a novice at this and was wondering  if anyone knows of a web page that will detailed instructions on how to  get this done?

So using a domain name I pay for. There is no way to just have the domain point straight to the VPS ?

---

### Post by volkswagner on 2016-07-28
> **neil37 said:**
> 
...
So using a domain name I pay for. There is no way to just have the domain point straight to the VPS ?

The simplest method is to use the DNS service provided by your registrar. Most providers have DNS management. Create an A record pointing to the IP address of your VPS.

Try searching 'DNS setup "GoDaddy"' or whatever the name is for your registrar.

---

### Post by Habitual on 2016-07-29
Neil:
An "A Record" on the internet is a very key concept.
It is like the "telephone number" of where your domain.tld "lives".
Typically as volkswagner pointed out, is the public ip assigned to your VPS.

The [https://www.digitalocean.com/community/tutorial](https://www.digitalocean.com/community/tutorial) is "good stuff" in my book.

I have to keep it simple with telephone number analogies, my apologies.

---

### Post by SeijiSensei on 2016-07-29
All my domains are hosted at [directnic.com]("http://directnic.com").  I have two virtual servers that I rent from [Linode]("http://www.linode.com").  One is in New Jersey, the other in California.  Both of these run BIND to provide name service for the domains I maintain.  All my domains at directnic are configured to use my two name servers (via the "IN NS" record).  One of the servers runs Apache, et. al., and offers publicly available services like websites and inbound mail.  The other mostly processes the mail and offers no other publicly-visible services besides DNS.  This arrangement corresponds with [IETF best practices for DNS server location]("https://tools.ietf.org/html/rfc2182"), at least two servers that are geographically and topologically separated for redundancy.

---

