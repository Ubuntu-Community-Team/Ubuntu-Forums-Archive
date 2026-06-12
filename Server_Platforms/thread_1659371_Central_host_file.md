---
title: "Central host file"
date: 2011-01-03
forum: Server Platforms
---

### Post by pjkilp on 2011-01-03
We have an Ubuntu server that is a DNS forwarder (no zones) for our internal machines to the internet. Instead of using host files on individual machines to block some websites which has been suggested on some sites, could the DNS server be configured to do the same thing (resolve specified web site requests to a crap address) so we only have to do it once and not change /etc/host files on several machines? We can't use a proxy because of some of the software and our router has no place to block.

---

### Post by SeijiSensei on 2011-01-04
> **pjkilp said:**
> Could the DNS server be configured to do the same thing (resolve specified web site requests to a crap address) so we only have to do it once and not change /etc/host files on several machines?

You'd need to create zone files for each domain you wish to block.  You'd have to make sure that these files only block what you want to block, websites I'd imagine, but have proper addresses for records like MX if you need to send mail to those domains.

Frankly, I think it's a lot easier to drop a Linux box between the internal network and the router and use [Squid in transparent proxy mode]("http://www.deckle.co.za/squid-users-guide/Transparent_Caching/Proxy") to filter HTTP requests.

---

### Post by pjkilp on 2011-01-04
Thanks. I have heard about squid while researching this. I thought I would give a quick check if there was a DNS way, but I will look into squid more.

Thanks

pk

---

### Post by HermanAB on 2011-01-04
Yes, that is exactly what a Real-Time Black List is.  E.g. Spamcop and Spamhaus.

Here is how to make your own with BIND:
[http://www.kloth.net/internet/dnsbl-howto.php](http://www.kloth.net/internet/dnsbl-howto.php)

---

